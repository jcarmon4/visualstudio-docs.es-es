---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346163"
---
# <a name="debugreason"></a>DEBUG_REASON
Especifica por qué se inició el proceso para la depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Campos
`DEBUG_REASON_ERROR`\
Se produjo un error no especificado (Esto se usa como una condición predeterminada cuando ninguno de los otros motivos de ajuste).

`DEBUG_REASON_USER_LAUNCHED`\
Se inició el proceso a petición del usuario.

`DEBUG_REASON_USER_ATTACHED`\
El proceso de ejecución ya se ha adjuntado a por el usuario.

`DEBUG_REASON_AUTO_ATTACHED`\
El proceso se adjunta automáticamente a cuando se inició.

`DEBUG_REASON_CAUSALITY`\
El proceso se inició debido a un *Just-In-Time* eventos de depuración (JIT).

## <a name="remarks"></a>Comentarios
Devuelve el [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
