---
title: IDebugArrayObject::GetRank | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a733baf1be2e5a249c214547b31465bb2464ed6
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "66351779"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtiene el rango de la matriz, es decir, el número de dimensiones.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parámetros
`pdwRank`\
[out] Devuelve el rango.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Use la [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) método para recuperar el tamaño de cada dimensión del objeto de matriz.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)