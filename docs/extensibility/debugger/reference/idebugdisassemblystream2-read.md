---
title: IDebugDisassemblyStream2::Read | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c74ed1de1d12cc7384ee8f7d27dad910c7b9c9d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310354"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lee las instrucciones a partir de la posición actual en la secuencia de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Read( 
   DWORD                     dwInstructions,
   DISASSEMBLY_STREAM_FIELDS dwFields,
   DWORD*                    pdwInstructionsRead,
   DisassemblyData*          prgDisassembly
);
```

```csharp
int Read( 
   uint                           dwInstructions,
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,
   out uint                       pdwInstructionsRead,
   DisassemblyData[]              prgDisassembly
);
```

## <a name="parameters"></a>Parámetros
`dwInstructions`\
[in] El número de instrucciones desensamblar. Este valor también es la longitud máxima de la `prgDisassembly` matriz.

`dwFields`\
[in] Una combinación de marcas de la [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) enumeración que indican qué campos de `prgDisassembly` son para rellenarlo.

`pdwInstructionsRead`\
[out] Devuelve el número de instrucciones realmente el desensamblado.

`prgDisassembly`\
[out] Una matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructuras que se rellena con el código desensamblado, una estructura por instrucción desensamblado. La longitud de la matriz viene determinado por la `dwInstructions` parámetro.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Se puede obtener el número máximo de instrucciones que están disponibles en el ámbito actual mediante una llamada a la [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) método.

 Se puede cambiar la posición actual cuando la instrucción siguiente se lee desde mediante una llamada a la [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) método.

 El `DSF_OPERANDS_SYMBOLS` marca puede agregarse a la `DSF_OPERANDS` marca en el `dwFields` parámetro para indicar que se deben usar nombres de símbolos al desensamblar las instrucciones.

## <a name="see-also"></a>Vea también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)