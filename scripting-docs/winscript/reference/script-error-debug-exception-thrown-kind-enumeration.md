---
title: Enumeración SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3be6989195eacdd4d70bd13790d55e4f6cfc769d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443648"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Enumeración SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica la clase de la excepción producida. Esta enumeración se utiliza en el [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) método.  
  
> [!IMPORTANT]
> Estas constantes se implementan mediante PDM versión 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|La excepción es una excepción de primera aparición.|  
|ETK_USER_UNHANDLED|0x00000001|La excepción no se controla en el código de usuario.|  
|ETK_UNHANDLED|0x00000002|La excepción no se controla en el código.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptErrorDebug110 (Interfaz)](../../winscript/reference/iactivescripterrordebug110-interface.md)