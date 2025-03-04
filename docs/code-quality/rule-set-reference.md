---
title: Referencia del conjunto de reglas Análisis de código
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0222dab568ce421c3bd87474b956c82aab4d2683
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585242"
---
# <a name="code-analysis-rule-set-reference"></a>Referencia del conjunto de reglas Análisis de código

Al configurar el análisis heredado para proyectos de código administrado en Visual Studio, puede elegir en una lista de conjuntos de *reglas*integrados. Algunas reglas se incluyen en más de uno de los conjuntos de reglas integrados; por ejemplo, el conjunto de reglas reglas de corrección básicas incluye reglas que se encuentran en el conjunto de reglas reglas recomendadas administradas.

> [!NOTE]
> Los conjuntos de reglas de esta sección pertenecen al análisis heredado. Para obtener información sobre los conjuntos de reglas disponibles para los paquetes del analizador de código, vea [usar conjuntos de reglas con analizadores de código](analyzer-rule-sets.md).

Puede usar uno de estos conjuntos de reglas integrados, o bien puede [personalizar un conjunto de reglas](../code-quality/how-to-create-a-custom-rule-set.md) para satisfacer sus requisitos de proyecto. Si incluye varios conjuntos de reglas que contienen la misma regla en un conjunto de reglas personalizado, esa regla solo aparece una vez en el conjunto de reglas personalizado.

Los temas de esta sección describen la regla integrada conjuntos y las reglas (o advertencias) que contienen.

| Conjunto de reglas | Reglas incluidas |
| - | - |
| [Todas las reglas](all-rules-rule-set.md) | Contiene todas las reglas y C++ administradas disponibles |
| [Reglas de corrección básicas](basic-correctness-rules-rule-set-for-managed-code.md) | Incluye reglas recomendadas administradas más reglas para errores lógicos y uso del marco de trabajo |
| [Reglas de corrección extendidas](extended-correctness-rules-rule-set-for-managed-code.md) | Incluye reglas de corrección básicas (que incluyen reglas recomendadas administradas) más reglas para errores de lógica y uso del marco de trabajo. |
| [Reglas de directrices de diseño básicas](basic-design-guideline-rules-rule-set-for-managed-code.md) | Incluye reglas recomendadas administradas y reglas para garantizar que el código sea fácil de leer, comprender y mantener. |
| [Reglas de directrices de diseño extendido](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Incluye reglas de directrices de diseño básicas (que incluyen reglas recomendadas administradas) más reglas de mantenimiento que se centran en la nomenclatura |
| [Reglas de globalización](globalization-rules-rule-set-for-managed-code.md) | Incluye reglas para problemas de globalización |
| [Reglas mínimas administradas](managed-minimum-rules-rule-set-for-managed-code.md) | Incluye cuatro reglas para problemas críticos de código administrado |
| [Reglas recomendadas administradas](managed-recommended-rules-rule-set-for-managed-code.md) | Incluye reglas mínimas administradas más reglas para problemas críticos de código administrado |
| [Reglas mínimas mixtas](mixed-minimum-rules-rule-set.md) | Incluye reglas para problemas críticos en C++ el código para CLR |
| [Reglas recomendadas mixtas](mixed-recommended-rules-rule-set.md) | Incluye reglas mínimas mixtas más reglas para problemas críticos C++ en el código para CLR |
| [Reglas mínimas nativas](native-minimum-rules-rule-set.md) | Incluye reglas para problemas críticos en el código nativo |
| [Reglas recomendadas nativas](native-recommended-rules-rule-set.md) | Incluye reglas mínimas nativas más reglas para problemas críticos en código nativo. |
| [Reglas de seguridad](security-rules-rule-set-for-managed-code.md) | Incluye reglas para buscar vulnerabilidades de seguridad |