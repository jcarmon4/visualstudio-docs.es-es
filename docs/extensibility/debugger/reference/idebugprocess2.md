---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bea73c1bce5367d9686e835bb58dd99a83cc818
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314137"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Esta interfaz representa un proceso que se ejecuta en un puerto. Si el puerto es el puerto local, a continuación, `IDebugProcess2` representa normalmente a un proceso físico en el equipo local.

## <a name="syntax"></a>Sintaxis

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un proveedor de puerto personalizado para administrar programas como un grupo. Esta interfaz debe implementarse mediante el proveedor del puerto.

 Un motor de depuración también implementa esta interfaz si permite iniciar un programa a través de [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz se llama principalmente por el Administrador de depuración de la sesión (SDM) con el fin de interactuar con un grupo de programas identificados en este proceso.

 Llame a [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obtener esta interfaz. Esta interfaz también se devuelve mediante una llamada a `IDebugEngineLaunch2::LaunchSuspended`.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugProcess2`.

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtiene una descripción del proceso.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera los programas que se incluyen en este proceso.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtiene la instancia de este proceso se está ejecutando en un servidor de equipo.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Finaliza el proceso.|
|[Asociar](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Se asocia al proceso.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina si el SDM puede desasociar el proceso.|
|[Desasociar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desasocia al depurador del proceso.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtiene el identificador de proceso del sistema.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtiene un identificador único global para este proceso.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [EN DESUSO]|Obtiene el nombre de la sesión que está depurando el proceso.<br /><br /> [EN DESUSO. DEBE SIEMPRE SE DEVUELVE `E_NOTIMPL`.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera los subprocesos que se ejecutan en el proceso.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita el programa siguiente ejecución de código en este punto del proceso.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtiene el puerto que se ejecuta en este proceso.|

## <a name="remarks"></a>Comentarios
 Un `IDebugProcess2` contiene uno o varios [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaces.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)