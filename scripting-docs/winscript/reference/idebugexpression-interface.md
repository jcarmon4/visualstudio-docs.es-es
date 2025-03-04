---
title: IDebugExpression (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1757317e9ab148b508bfed95107b5c3b3369b598
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430028"
---
# <a name="idebugexpression-interface"></a>IDebugExpression (Interfaz)
Representa una expresión evaluada de forma asincrónica. Motores de script normalmente implementan esta interfaz. Normalmente, un IDE del depurador utiliza esta interfaz para habilitar una ventana de ejecución inmediato o inspección (ventana).  
  
> [!NOTE]
> El `IDebugExpression` interfaz solo está disponible desde un marco de pila.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugExpression` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Comienza la evaluación de la expresión.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Anula la expresión.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina si la operación completada.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Devuelve el resultado de la evaluación de expresión como una cadena y el valor devuelto de la operación.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Devuelve el resultado de la evaluación de expresión como una propiedad de depuración y el valor devuelto de la operación.|