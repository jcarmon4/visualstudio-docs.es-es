---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23510910fe18c68107e2c497aac5913da1eae963
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310221"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Esta interfaz representa un documento de origen.

## <a name="syntax"></a>Sintaxis

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Normalmente, se implementa esta interfaz. Un motor de depuración (DE) también puede implementar esta interfaz cuando debe proporcionar el código fuente y el origen no existe en el disco.  En tales casos, podría implementar también la DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) y [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfaces, así como algunos métodos adicionales en el [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) y [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaces.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Métodos en el `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, y `IDebugActivateDocumentEvent2` interfaces devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugDocument2`.

|Método|Descripción|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtiene el nombre del documento en una de varias formas.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtiene el identificador de clase del documento.|

## <a name="remarks"></a>Comentarios
 Esta interfaz se implementa solo cuando la DE proporciona el código fuente. Por ejemplo, cuando se está depurando un script en una página HTML, la DE proporciona el código fuente porque el origen es descargado o se genera dinámicamente y no existe como un archivo de disco. Al depurar los lenguajes tradicionales, como C++, no necesita implementarse esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)