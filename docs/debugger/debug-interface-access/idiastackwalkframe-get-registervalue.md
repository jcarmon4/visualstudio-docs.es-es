---
title: IDiaStackWalkFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d60fa2ebefb7e1e4eefccce866a1059fdbc78a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837984"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
Recupera el valor de un registro.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_registerValue ( 
   DWORD      index,
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `index`

[in] Un valor de la [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md) enumeración que especifica el registro para obtener el valor de.

 `pRetVal`

[out] Devuelve el valor actual del registro.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)