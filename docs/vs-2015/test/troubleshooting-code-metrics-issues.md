---
title: Solucionar problemas de métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a02dbc4840729d5004b0815175f626fc8760711
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416968"
---
# <a name="troubleshooting-code-metrics-issues"></a>Solucionar problemas de métricas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pueden surgir algunos de los problemas siguientes al recopilar métricas del código:

- [Cambios en los cálculos de complejidad de código de Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Cambios en los cálculos de complejidad de código de Visual Studio 2010

Para la misma función, la métrica de complejidad de código calculada en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] puede ser diferente de la métrica calculada en versiones anteriores de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en las siguientes situaciones:

- La función contiene uno o varios bloques catch. En versiones anteriores de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], los bloques catch no se incluían en el cálculo. En [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], la complejidad de cada bloque catch se agrega a la complejidad de la función.

- La función contiene una instrucción switch (Select Case en VB). Las diferencias del compilador entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y versiones anteriores pueden generar código MSIL diferente para algunas instrucciones switch que contienen casos de paso explícito.

## <a name="see-also"></a>Vea también

- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
