---
title: 'CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8c82e7303ea4016974be04c3d8745cb2011017f0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923161"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|Identificador de comprobación|CA1013|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
Cuando las instancias de un tipo se pueden combinar mediante operaciones como suma y resta, casi siempre se debe definir la igualdad que se va `true` a devolver para dos instancias cualesquiera que tengan los mismos valores constituyentes.

No se puede usar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, se producirá un desbordamiento de pila. Para implementar el operador de igualdad, use el método Object. Equals en su implementación de. Consulte el ejemplo siguiente.

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
Para corregir una infracción de esta regla, implemente el operador de igualdad para que sea coherente con los operadores de suma y resta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla cuando la implementación predeterminada del operador de igualdad proporciona el comportamiento correcto para el tipo.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se define un`BadAddableType`tipo () que infringe esta regla. Este tipo debe implementar el operador de igualdad para que dos instancias de que tengan los mismos valores de `true` campo comprueben la igualdad. El tipo `GoodAddableType` muestra la implementación corregida. Tenga <xref:System.Object.Equals%2A> en cuenta que este tipo también implementa el operador de desigualdad e invalida para satisfacer otras reglas. Una implementación completa también implementaría <xref:System.Object.GetHashCode%2A>.

[!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se comprueba la igualdad mediante el uso de instancias de los tipos que se definieron previamente en este tema para mostrar el comportamiento predeterminado y correcto para el operador de igualdad.

[!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>Vea también

- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)