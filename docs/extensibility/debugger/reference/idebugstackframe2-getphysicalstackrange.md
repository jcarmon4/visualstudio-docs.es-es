---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cf0db9fa776116f1536ae137444160385a8b6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347713"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtiene una representación de dependiente de la máquina del intervalo de direcciones físicas asociado con un marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parámetros
`paddrMin`\
[out] Devuelve el menor dirección física asociada con este marco de pila.

`paddrMax`\
[out] Devuelve la dirección física más alta asociada con este marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La información devuelta por este método se utiliza el Administrador de depuración de la sesión (SDM) para ordenar los marcos de pila.

 Se supone que la pila de llamadas crece hacia abajo, es decir, que se han agregado nuevos marcos de pila en las direcciones de memoria cada vez más inferiores. Una arquitectura en tiempo de ejecución debe proporcionar los intervalos de pila física que coinciden con esta suposición.

## <a name="see-also"></a>Vea también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)