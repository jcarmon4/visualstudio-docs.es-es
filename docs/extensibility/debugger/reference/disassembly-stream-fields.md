---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3499ce5bfe46f3185dd5c8ca9e2ada055544c8c8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318259"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Especifica qué información se va a recuperar sobre un campo de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Campos
`DSF_ADDRESS`\
Inicializar o usar el `bstrAddress` campo.

`DSF_ADDRESSOFFSET`\
Inicializar o usar el `bstrAddressOffset` campo.

`DSF_CODEBYTES`\
Inicializar o usar el `bstrCodeBytes` campo.

`DSF_OPCODE`\
Inicializar o usar el `bstrOpCode` campo.

`DSF_OPERANDS`\
Inicializar o usar el `bstrOperands` campo.

`DSF_SYMBOL`\
Inicializar o usar el `bstrSymbol` campo.

`DSF_CODELOCATIONID`\
Inicializar o usar el `uCodeLocationId` campo.

`DSF_POSITION`\
Inicializar o usar el `posBeg` y `posEnd` campos.

`DSF_DOCUMENTURL`\
Inicializar o usar el `bstrDocumentUrl` campo.

`DSF_BYTEOFFSET`\
Inicializar o usar el `dwByteOffset` campo.

`DSF_FLAGS`\
Inicializar o usar el `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) campo.

`DSF_OPERANDS_SYMBOLS`\
Incluir nombres de símbolos en el `bstrOperands` campo.

`DSF_ALL`\
Especifica todos los campos de la secuencia de desensamblado.

## <a name="remarks"></a>Comentarios
Pasado como parámetro a la [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método para indicar qué campos de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura deben inicializarse.

Utilizado para la `dwFields` miembro de la `DisassemblyData` estructura para indicar qué campos se usan y válido cuando se devuelve la estructura.

Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
