---
title: 'CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: daaa856ccbc5915bcaad937a504ea2600a089c1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189099"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Los nombres de parámetro no deben coincidir con los nombres de miembro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|Identificador de comprobación|CA1719|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Coincide con el nombre de un miembro visible externamente, en una comparación entre mayúsculas y minúsculas, el nombre de uno de sus parámetros.

## <a name="rule-description"></a>Descripción de la regla
 Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro. Sería un diseño extraño si éstos fueran los mismos. Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre de parámetro que no coincide con el nombre del miembro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para el desarrollo nuevo, no conocidos se producen escenarios donde se debe suprimir una advertencia de esta regla. Para enviar las bibliotecas, es posible que deba suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
