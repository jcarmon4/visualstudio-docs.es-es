---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbfa24733644067b3f79fc7b6e8450df2130116d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179954"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica qué información se va a recuperar sobre un contexto de la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Miembros  
 CIF_MODULEURL  
 Inicializar o usar el `bstrModuleUrl` campo de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estructura.  
  
 CIF_FUNCTION  
 Inicializar o usar el `bstrFunction` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_FUNCTIONOFFSET  
 Inicializar o usar el `posFunctionOffset` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ADDRESS  
 Inicializar o usar el `bstrAddress` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ADDRESSOFFSET  
 Inicializar o usar el `bstrAddressOffset` campo de la `CONTEXT_INFO` estructura.  
  
 CIF_ALLFIELDS  
 Inicializar o usar todos los campos de la `CONTEXT_INFO` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan a un parámetro a la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método para indicar qué campos de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estructura deben inicializarse.  
  
 Estas marcas también se usan para indicar qué campos de la `CONTEXT_INFO` estructura se usan y válido cuando se devuelve la estructura.  
  
 Estos valores se pueden combinar con una operación OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
