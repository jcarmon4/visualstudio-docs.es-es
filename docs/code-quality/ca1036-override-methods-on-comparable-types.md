---
title: 'CA1036: Invalidar métodos en tipos comparables'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a4e04e1afdbecdc9c333ea43a52bff3123d448a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547621"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Invalidar métodos en tipos comparables

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|Identificador de comprobación|CA1036|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Un tipo implementa la <xref:System.IComparable?displayProperty=fullName> interfaz y no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que. La regla no notifica una infracción si el tipo hereda solo una implementación de la interfaz.

De forma predeterminada, esta regla solo examina los tipos públicos y protegidos, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los tipos que definen un criterio de ordenación <xref:System.IComparable> personalizado implementan la interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el criterio de ordenación correcto para dos instancias del tipo. Esta regla identifica los tipos que establecen un criterio de ordenación. Establecer un criterio de ordenación implica que no se aplica el significado ordinario de igualdad, desigualdad, menor que y mayor que. Cuando se proporciona una implementación de <xref:System.IComparable>, normalmente también se debe invalidar <xref:System.Object.Equals%2A> para que devuelva valores que sean coherentes con <xref:System.IComparable.CompareTo%2A>. Si invalida <xref:System.Object.Equals%2A> y está codificando en un lenguaje que admite sobrecargas de operador, también debe proporcionar operadores coherentes con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, <xref:System.Object.Equals%2A>invalide. Si el lenguaje de programación admite la sobrecarga de operadores, proporcione los operadores siguientes:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

En C#, los tokens que se usan para representar estos operadores son los siguientes:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de la regla CA1036 cuando la infracción está causada por operadores que faltan y el lenguaje de programación no admite la sobrecarga de operadores, como es el caso de Visual Basic. Si determina que la implementación de los operadores no tiene sentido en el contexto de la aplicación, también es seguro suprimir una advertencia de esta regla cuando se activa en operadores de igualdad distintos de op_Equality. Sin embargo, siempre debe reemplazar op_Equality y el operador = = si invalida <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="examples"></a>Ejemplos

El código siguiente contiene un tipo que implementa <xref:System.IComparable>correctamente. Los comentarios de código identifican los métodos que cumplen varias reglas que <xref:System.Object.Equals%2A> están relacionadas <xref:System.IComparable> con y la interfaz.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

El siguiente código de aplicación comprueba el comportamiento de <xref:System.IComparable> la implementación que se mostró anteriormente.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)