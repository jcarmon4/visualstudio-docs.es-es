---
title: 'CA2312: Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2312
- EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing
ms.openlocfilehash: 38495a3c8d5a2efb5e5e96785cecbd6d50e9cd00
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891121"
---
# <a name="ca2312-ensure-netdatacontractserializerbinder-is-set-before-deserializing"></a>CA2312: Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar

|||
|-|-|
|TypeName|EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing|
|Identificador de comprobación|CA2312|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Se <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> llamó a un método de deserialización o se hizo <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> referencia a él y la propiedad puede ser null.

## <a name="rule-description"></a>Descripción de la regla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Esta regla busca <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> llamadas al método de deserialización o referencias <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> cuando puede ser null. Si desea impedir <xref:System.Runtime.Serialization.NetDataContractSerializer> la deserialización con independencia de la <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propiedad, deshabilite esta regla y [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)y habilite la regla [CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, use un serializador seguro en su lugar y **no permita que un atacante especifique un tipo arbitrario para**deserializar. Algunos serializadores más seguros incluyen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>: No usar <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>nunca. Si debe usar un solucionador de tipos, restrinja los tipos deserializados a una lista de espera.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET: Use TypeNameHandling. None. Si debe usar otro valor para TypeNameHandling, restrinja los tipos deserializados a una lista de espera con un ISerializationBinder personalizado.
  - Búferes de protocolo
- Convierta la prueba de alteración de los datos serializados. Después de la serialización, firme criptográficamente los datos serializados. Antes de la deserialización, valide la firma criptográfica. Proteja la clave criptográfica para que no se revele y diseñe las rotaciones de clave.
- Restrinja los tipos deserializados. Implementar un personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de deserializar <xref:System.Runtime.Serialization.NetDataContractSerializer>con, establezca <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> la propiedad en una instancia de su <xref:System.Runtime.Serialization.SerializationBinder>personalizado. En el método invalidado <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si el tipo es inesperado, inicie una excepción para detener la deserialización.
  - Asegúrese de que todas las rutas de <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> acceso de código tienen establecida la propiedad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public NetDataContractSerializer Serializer { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Serializer As NetDataContractSerializer

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Solución

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        serializer.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        serializer.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Reglas relacionadas

[CA2310: No usar deserializador no seguro NetDataContractSerializer](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)

[CA2311: No deserializar sin establecer primero NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)
