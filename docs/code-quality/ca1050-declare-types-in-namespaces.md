---
title: 'CA1050: Declarar tipos en espacios de nombres'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 869ff99243349ae01c63da0a7d9e6544761cbd39
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922498"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Declarar tipos en espacios de nombres

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|Identificador de comprobación|CA1050|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público o protegido se define fuera del ámbito de un espacio de nombres con nombre.

## <a name="rule-description"></a>Descripción de la regla
Los tipos se declaran en los espacios de nombres para evitar conflictos de nombres y como una manera de organizar los tipos relacionados en una jerarquía de objetos. Los tipos que están fuera de un espacio de nombres con nombre se encuentran en un espacio de nombres global al que no se puede hacer referencia en el código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, coloque el tipo en un espacio de nombres.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Aunque nunca tenga que suprimir una advertencia de esta regla, es seguro hacerlo cuando el ensamblado nunca se usará junto con otros ensamblados.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una biblioteca que tiene un tipo declarado incorrectamente fuera de un espacio de nombres y un tipo con el mismo nombre declarado en un espacio de nombres.

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Ejemplo
La siguiente aplicación usa la biblioteca que se definió anteriormente. Tenga en cuenta que el tipo que se declara fuera de un espacio de nombres `Test` se crea cuando el nombre no está calificado por un espacio de nombres. Tenga en cuenta también que para `Test` tener acceso `Goodspace`al tipo en, el nombre del espacio de nombres es obligatorio.

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]