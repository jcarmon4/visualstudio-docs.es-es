---
title: IDiaSymbol::get_sourceFileName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sourceFileName method
ms.assetid: 0f5dce88-829e-4df3-8acd-8d71076ad167
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8130fe90fe2ca8da015f174493b651d5142d2a2e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "64832335"
---
# <a name="idiasymbolgetsourcefilename"></a>IDiaSymbol::get_sourceFileName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el nombre de archivo del archivo de origen de operación de compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_sourceFileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el nombre de archivo del archivo de origen de operación de compilación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
