---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e084152f6215878816739f46dc91fa322cf9c94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158443"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método evalúa la expresión de forma asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 [in] Una combinación de marcas de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeración que controlan la evaluación de expresiones.  
  
 `pExprCallback`  
 [in] Este parámetro siempre es un valor null.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Un código de error típico es:  
  
|Error|DESCRIPCIÓN|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Se está evaluando la otra expresión, y no se admite la evaluación de expresión simultáneas.|  
  
## <a name="remarks"></a>Comentarios  
 Este método debe devolver inmediatamente después de haberse iniciado la evaluación de expresiones. Cuando la expresión se evalúa correctamente, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) debe enviarse a la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) devolución de llamada de evento proporcionados a través de [adjuntar ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CExpression` objeto que implementa el [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaz.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
