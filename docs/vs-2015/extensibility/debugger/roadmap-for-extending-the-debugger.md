---
title: Guía básica para ampliar el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695960"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guía básica para ampliar el depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta documentación proporciona información de referencia y la guía para extender la [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] del depurador con el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentación sobre depuración incluye varios escenarios representativos que muestran formas habituales para personalizar al depurador, una referencia completa y ejemplos.  
  
 El compilador y su salida determinan lo que necesita hacer para implementar la depuración en su producto. Si el compilador:  
  
- Tiene como destino el sistema operativo de Windows nativo y escribe un. Archivo PDB, puede depurar programas con el motor de depuración de código nativo (DE), que está integrado en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. No es necesario implementar un evaluador DE o una expresión. El evaluador de expresiones se escribe para conocer la sintaxis del lenguaje de programación C++.  
  
- Genera el lenguaje intermedio (MSIL) de salida, puede depurar programas con el motor de depuración de código administrado DE, que también está integrado en el Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Por lo tanto, sólo debe implementar un evaluador de expresiones. Un evaluador de expresiones de ejemplo se proporciona para usted. Para obtener más información, vea los temas siguientes:  
  
     [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Evaluación de expresiones en el modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escritura de un evaluador de expresiones de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Destinos de una propiedad de sistema operativo o algún otro entorno de tiempo de ejecución, deberá escribir su propio DE. Se proporciona un tutorial que crea un sencillo DE usar COM de ATL. Para obtener más información, vea los temas siguientes:  
  
     [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Creación de un motor de depuración mediante ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementación de un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
