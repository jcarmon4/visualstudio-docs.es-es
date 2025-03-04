---
title: 'CA2111: Los punteros no deben estar visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 416e45337dafd11a00e98b9adda9f16b02139f9c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921651"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Los punteros no deben estar visibles

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|Identificador de comprobación|CA2111|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un campo público o <xref:System.IntPtr?displayProperty=fullName> protegido <xref:System.UIntPtr?displayProperty=fullName> o no es de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.IntPtr>y <xref:System.UIntPtr> son tipos de puntero que se usan para tener acceso a la memoria no administrada. Si un puntero no es privado, interno o de solo lectura, el código malintencionado puede cambiar el valor del puntero, permitiendo potencialmente el acceso a ubicaciones arbitrarias en memoria o provocando errores del sistema o de la aplicación.

Si desea proteger el acceso al tipo que contiene el campo de puntero, vea [CA2112: Los tipos seguros no deben exponer](../code-quality/ca2112-secured-types-should-not-expose-fields.md)los campos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Proteja el puntero haciéndolo de solo lectura, interno o privado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla si no se basa en el valor del puntero.

## <a name="example"></a>Ejemplo
En el código siguiente se muestran punteros que infringen y satisfacen la regla. Tenga en cuenta que los punteros no privados también infringen la [regla CA1051: No declare campos](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)de instancia visibles.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>