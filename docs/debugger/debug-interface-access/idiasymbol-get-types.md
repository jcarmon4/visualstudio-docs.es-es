---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19642e6875e81220cb20109ce45e8dca40777a63
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786564"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Recupera una matriz de tipos específicos del compilador para este símbolo.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parámetros
 `cTypes`

[in] Tamaño del búfer para almacenar los datos.

 `pcTypes`

[out] Devuelve el número de tipos escritos, o bien, si la `types` parámetro es `NULL`, a continuación, el número total de tipos disponibles.

 `types[]`

[out] Una matriz que se va a rellenar con el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representan todos los tipos de este símbolo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)