---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cef6382009d8139b8c166ce6b75a692e8e309557
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337182"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Este método inicia un proceso mediante el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parámetros
`pszMachine`\
[in] El nombre de la máquina en que se va a iniciar el proceso. Use un valor null para especificar el equipo local.

`pPort`\
[in] El [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz que representa el puerto que se ejecutará el programa.

`pszExe`\
[in] El nombre del archivo ejecutable que se iniciará.

`pszArgs`\
[in] Los argumentos para pasar al ejecutable. Puede ser un valor null si no hay ningún argumento.

`pszDir`\
[in] El nombre del directorio de trabajo usando el archivo ejecutable. Puede ser un valor null si no se requiere ningún directorio de trabajo.

`bstrEnv`\
[in] Bloque de entorno de cadenas terminadas en NULL, seguido de un terminador NULL adicional.

`pszOptions`\
[in] Las opciones para el archivo ejecutable.

`dwLaunchFlags`\
[in] Especifica el [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) para una sesión.

`hStdInput`\
[in] Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere la redirección.

`hStdOutput`\
[in] Identificador de un flujo de salida alternativos. Puede ser 0 si no se requiere la redirección.

`hStdError`\
[in] Identificador de un flujo de salida de error alternativa. Puede ser 0 si no se requiere la redirección.

`pCallback`\
[in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que recibe los eventos del depurador.

`ppDebugProcess`\
[out] Devuelve el resultado [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso iniciado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Normalmente, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] inicia un programa mediante la [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) método y, a continuación, asocia el depurador al programa suspendido. Sin embargo, hay circunstancias en que el motor de depuración es posible que deba iniciar un programa (por ejemplo, si el motor de depuración es parte de un intérprete y el programa que se está depurando es un lenguaje interpretado), en cuyo caso [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] usa el `IDebugEngineLaunch2::LaunchSuspended` (método) .

 El [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) método se llama para iniciar el proceso después de iniciar el proceso en un estado suspendido.

## <a name="see-also"></a>Vea también
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)