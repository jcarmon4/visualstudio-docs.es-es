---
title: IDebugErrorBreakpoint2 | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9895caedebfba637eb47198c408e973e6609fcc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183962"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un error o un punto de interrupción de advertencia, como una ubicación no válida, una expresión no válida o los motivos por qué el punto de interrupción pendiente no enlazado (código no cargado todavía, y así sucesivamente).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. Esta interfaz se utiliza para notificar problemas con el enlace de un punto de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) obtiene esta interfaz. También se puede devolver esta interfaz (como parte de una lista representada por un [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) interfaz) mediante una llamada a [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugErrorBreakpoint2`.  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que produjo el error.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de errores de punto de interrupción que describe el error.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
