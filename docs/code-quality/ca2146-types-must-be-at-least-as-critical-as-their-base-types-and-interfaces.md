---
title: 'CA2146: Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920425"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|Identificador de comprobación|CA2146|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo transparente se deriva de un tipo <xref:System.Security.SecuritySafeCriticalAttribute> que está marcado con <xref:System.Security.SecurityCriticalAttribute>o, o un tipo marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo se deriva de un tipo marcado con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada. Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad. Las infracciones de esta regla en la transparencia de nivel <xref:System.TypeLoadException> 2 dan como resultado un para el tipo derivado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir esta infracción, marque el tipo derivado o de implementación con un atributo de transparencia que sea al menos tan crítico como el tipo base o la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]