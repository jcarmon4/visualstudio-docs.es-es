---
title: 'CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fafa4782762e18f1ced8c7f929720e995986ac7a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546866"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|Identificador de comprobación|CA2231|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Un tipo de valor invalida <xref:System.Object.Equals%2A?displayProperty=fullName> pero no implementa el operador de igualdad.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

En la mayoría de los lenguajes de programación, no hay ninguna implementación predeterminada del operador de igualdad (= =) para los tipos de valor. Si el lenguaje de programación admite sobrecargas de operador, considere la posibilidad de implementar el operador de igualdad. Su comportamiento debe ser idéntico al de <xref:System.Object.Equals%2A>.

No se puede usar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, se producirá un desbordamiento de pila. Para implementar el operador de igualdad, use el método Object. Equals en su implementación de. Por ejemplo:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente el operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla. sin embargo, se recomienda proporcionar el operador de igualdad si es posible.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca2231.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (uso). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define un tipo que infringe esta regla:

[!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1046: No sobrecargar el operador Equals en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225 Las sobrecargas de operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 Invalidar Equals al sobrecargar el operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Invalidar GetHashCode al reemplazar Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Vea también

- <xref:System.Object.Equals%2A?displayProperty=fullName>