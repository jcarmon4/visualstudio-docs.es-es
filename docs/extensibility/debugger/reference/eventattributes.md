---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3361d27a9e0a4a1f56035c0d2af20d9fa9a9303
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337762"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Especifica los atributos del evento.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Campos
`EVENT_ASYNCHRONOUS`\
Indica que el evento es asincrónico y no se necesita ninguna respuesta al evento.

`EVENT_SYNCHRONOUS`\
Indica que el evento es sincrónico; responder por medio de [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica que se trata de un evento de detención. Se debe combinar con `EVENT_ASYNCHRONOUS` o `EVENT_SYNCHRONOUS`.

`EVENT_ASYNC_STOP`\
Indica un evento de detención asincrónica. Actualmente no hay ningún evento de este tipo. Esta marca es solo un marcador de posición.

`EVENT_SYNC_STOP`\
Indica un evento de detención sincrónica (una combinación de `EVENT_SYNCHRONOUS` y `EVENT_STOPPING`). Este valor se usa un motor de depuración (DE) cuando envía un evento de detención. La respuesta se realiza mediante una llamada a [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md), o [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica un evento que se envía de forma inmediata y sincrónicamente al IDE. Esta marca se combina con otras marcas como `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, o `EVENT_SYNC_STOP` para indicar el tipo de evento y el hecho de que se conoce el mecanismo de respuesta (si existe).

`EVENT_EXPRESSION_EVALUATION`\
El evento es el resultado de evaluación de expresiones.

## <a name="remarks"></a>Comentarios
Estos valores se pasan en el `dwAttrib` parámetro de la [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.

Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
