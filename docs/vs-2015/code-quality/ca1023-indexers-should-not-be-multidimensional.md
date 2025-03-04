---
title: 'CA1023: Los indizadores no deben ser multidimensionales | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b9cf9cd97dd50577a466ed4d433e0e1dbd5da4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158037"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Los indizadores no deben ser multidimensionales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|Identificador de comprobación|CA1023|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido contiene un indizador público o protegido que utiliza más de un índice.

## <a name="rule-description"></a>Descripción de la regla
 Los indizadores, es decir, las propiedades indizadas, deben utilizar un índice único. Los indizadores multidimensionales pueden reducir significativamente la facilidad de uso de la biblioteca de. Si el diseño requiere varios índices, reconsidere si el tipo representa un almacén de datos lógico. Si no es así, utilice un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar el diseño para utilizar un solo entero o un índice de cadena o usar un método en lugar del indizador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla después de considerar cuidadosamente la necesidad de que el indizador no estándar.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `DayOfWeek03`, con un indizador multidimensional que infringe la regla. El indizador se puede considerar como un tipo de conversión y, por tanto, es más apropiado exponerlo como un método. El tipo se ha rediseñado en `RedesignedDayOfWeek03` para cumplir la regla.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1043: Utilizar argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
