---
title: 'CA2219: No producir excepciones en cláusulas de excepción'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8e949e21530654882cba99a7d9fedad8b5b59b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920263"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: No producir excepciones en cláusulas de excepción

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|Identificador de comprobación|CA2219|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático, problemático|

## <a name="cause"></a>Causa
Se produce una excepción desde una `finally`cláusula, filtro o error.

## <a name="rule-description"></a>Descripción de la regla
Cuando se genera una excepción en una cláusula de excepción, aumenta considerablemente la dificultad de la depuración.

Cuando se produce una excepción en una `finally` cláusula de error o, la nueva excepción oculta la excepción activa, si está presente. Esto hace que el error original sea difícil de detectar y depurar.

Cuando se genera una excepción en una cláusula de filtro, el tiempo de ejecución detecta la excepción de forma silenciosa y hace que el filtro se evalúe como false. No hay ninguna manera de indicar la diferencia entre el filtro que se evalúa como false y una excepción que se inicia desde un filtro. Esto hace que sea difícil detectar y depurar errores en la lógica del filtro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir esta infracción de esta regla, no genere explícitamente una excepción a `finally`partir de una cláusula, filtro o error.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia para esta regla. No hay escenarios en los que una excepción generada en una cláusula de excepción proporciona una ventaja para el código de ejecución.

## <a name="related-rules"></a>Reglas relacionadas
[CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vea también
[Advertencias de diseño](../code-quality/design-warnings.md)