---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39d9d9462fe1951f01927b9180fa8a99aee535be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326391"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Esta interfaz enumera los proveedores de puertos.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para representar una lista de proveedores de puertos.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llame a [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) para obtener una lista de proveedores de puertos.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IEnumDebugPortSuppliers2`.

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Recupera un número especificado de proveedores de puertos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Omite un número especificado de proveedores de puertos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtiene el número de proveedores de puertos en un enumerador.|

## <a name="remarks"></a>Comentarios
 Por lo general un motor de depuración no es necesario obtener esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)