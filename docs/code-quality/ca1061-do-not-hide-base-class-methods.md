---
title: 'CA1061: No ocultar métodos de clase base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f13ac29028472384cfadbf9c397e578f6509670
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922423"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: No ocultar métodos de clase base

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|Identificador de comprobación|CA1061|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo derivado declara un método con el mismo nombre y con el mismo número de parámetros que uno de sus métodos base; uno o varios parámetros son un tipo base del parámetro correspondiente en el método base; y cualquier parámetro restante tiene tipos que son idénticos a los parámetros correspondientes en el método base.

## <a name="rule-description"></a>Descripción de la regla
Un método en un tipo base está oculto por un método con un nombre idéntico en un tipo derivado cuando la firma del parámetro del método derivado solo difiere en los tipos que se derivan de forma más débil que los tipos correspondientes de la firma del parámetro del método base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite o cambie el nombre del método o cambie la firma del parámetro para que el método no oculte el método base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un método que infringe la regla.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]