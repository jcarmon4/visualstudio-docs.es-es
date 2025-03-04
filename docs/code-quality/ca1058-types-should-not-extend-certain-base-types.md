---
title: 'CA1058: Los tipos no deben ampliar ciertos tipos base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d92194a5aa2b46a0cb65a1525bc01d9de67b86
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547358"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|Identificador de comprobación|CA1058|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un tipo extiende uno de los siguientes tipos base:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Las excepciones deben derivar de <xref:System.Exception?displayProperty=fullName> o de una de sus subclases en el <xref:System> espacio de nombres.

No cree una subclase de <xref:System.Xml.XmlDocument> si desea crear una vista XML de un modelo de objetos o un origen de datos subyacente.

### <a name="non-generic-collections"></a>Colecciones no genéricas

Use y/o extienda colecciones genéricas siempre que sea posible. No extienda colecciones no genéricas en el código, a menos que la haya enviado anteriormente.

**Ejemplos de uso incorrecto**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

**Ejemplos de uso correcto**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, derive el tipo de un tipo base diferente o una colección genérica.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla para infracciones <xref:System.ApplicationException>sobre. Es seguro suprimir una advertencia de esta regla para infracciones sobre <xref:System.Xml.XmlDocument>. Es seguro suprimir una advertencia sobre una colección no genérica si el código se liberó previamente.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).