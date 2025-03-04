---
title: 'CA1301: Evitar los aceleradores duplicados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16cd44f00db13027d737b6a6b496877075ac6fa9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922272"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar los aceleradores duplicados

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|Identificador de comprobación|CA1301|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo extiende <xref:System.Windows.Forms.Control?displayProperty=fullName> y contiene dos o más controles de nivel superior que tienen claves de acceso idénticas que se almacenan en un archivo de recursos.

## <a name="rule-description"></a>Descripción de la regla

Una tecla de acceso, también conocida como acelerador, permite el acceso mediante teclado a un control mediante la tecla **Alt** . Cuando varios controles tienen la misma clave de acceso, el comportamiento de la tecla de acceso no está bien definido. Es posible que el usuario no pueda tener acceso al control previsto mediante la tecla de acceso y que se habilite un control distinto del que está previsto.

La implementación actual de esta regla omite los elementos de menú. Sin embargo, los elementos de menú del mismo submenú no deben tener claves de acceso idénticas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, defina las claves de acceso únicas para todos los controles.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una forma mínima que contiene dos controles que tienen claves de acceso idénticas. Las claves se almacenan en un archivo de recursos, que no se muestra. Sin embargo, sus valores aparecen en las `checkBox.Text` líneas comentadas. El comportamiento de los aceleradores duplicados se puede examinar intercambiando las `checkBox.Text` líneas con sus homólogos comentados. Sin embargo, en este caso, el ejemplo no generará una advertencia de la regla.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index)