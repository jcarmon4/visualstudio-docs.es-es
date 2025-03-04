---
title: 'CA1024: Utilizar las propiedades donde corresponda'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2763d7dd167ad0027509c44b8f9d43523f03976b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547798"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizar las propiedades donde corresponda

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|Identificador de comprobación|CA1024|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un método tiene un nombre que empieza por `Get`, no toma ningún parámetro y devuelve un valor que no es una matriz.

De forma predeterminada, esta regla solo busca métodos públicos y protegidos, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

En la mayoría de los casos, las propiedades representan datos y métodos para realizar acciones. Se tiene acceso a las propiedades como campos, lo que facilita su uso. Un método es un buen candidato para convertirse en una propiedad si existe alguna de estas condiciones:

- No toma ningún argumento y devuelve la información de estado de un objeto.

- Acepta un solo argumento para establecer parte del estado de un objeto.

Las propiedades deben comportarse como si fueran campos; Si el método no puede, no se debe cambiar a una propiedad. Los métodos son mejores que las propiedades en las siguientes situaciones:

- El método realiza una operación que lleva mucho tiempo. El método es perceptiblemente más lento que el tiempo necesario para establecer u obtener el valor de un campo.

- El método realiza una conversión. El acceso a un campo no devuelve una versión convertida de los datos que almacena.

- El método get tiene un efecto secundario observable. La recuperación del valor de un campo no produce efectos secundarios.

- El orden de ejecución es importante. Establecer el valor de un campo no se basa en la aparición de otras operaciones.

- La llamada al método dos veces en sucesión crea resultados diferentes.

- El método es estático, pero devuelve un objeto que el llamador puede cambiar. Al recuperar el valor de un campo, no se permite que el autor de la llamada cambie los datos almacenados por el campo.

- El método devuelve una matriz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el método a una propiedad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla si el método cumple al menos uno de los criterios enumerados anteriormente.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Expansión de propiedades de control en el depurador

Uno de los motivos por los que los programadores evitan el uso de una propiedad es porque no quieren que el depurador lo expanda. Por ejemplo, la propiedad puede implicar la asignación de un objeto grande o la llamada a P/Invoke, pero podría no tener realmente efectos secundarios observables.

Puede impedir que el depurador expanda automáticamente las propiedades aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. En el ejemplo siguiente se muestra este atributo que se aplica a una propiedad de instancia.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp
using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]
            }
        }
    }
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente contiene varios métodos que se deben convertir en propiedades y otros que no deberían hacerlo porque no se comportan como campos.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]