---
title: 'CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 323025eb03d2a949a970659aba2357c01ed8bfab
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921757"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|Identificador de comprobación|CA1712|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Una enumeración contiene un miembro cuyo nombre comienza con el nombre de tipo de la enumeración.

## <a name="rule-description"></a>Descripción de la regla
Los nombres de los miembros de enumeración no tienen como prefijo el nombre de tipo porque se espera que las herramientas de Desarrollo proporcionen información de tipo.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo necesario para que aprenda una nueva biblioteca de software y aumenta la confianza de los clientes de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite el prefijo de nombre de tipo del miembro de enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una enumeración con un nombre incorrecto seguido de la versión corregida.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1711: Los identificadores no deben tener un sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.Enum?displayProperty=fullName>