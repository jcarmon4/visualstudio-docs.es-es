---
title: IEnumDebugApplicationNodes::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Reset
ms.assetid: 56ecdafe-ff11-461a-92e1-93254a49f1a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 960f980bda330eaf14cc498e8bf804649023ba39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951728"
---
# <a name="ienumdebugapplicationnodesreset"></a>IEnumDebugApplicationNodes::Reset
Restablece una secuencia de enumeración al principio.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método restablece una secuencia de enumeración al principio.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugApplicationNodes (Interfaz)](../../winscript/reference/ienumdebugapplicationnodes-interface.md)