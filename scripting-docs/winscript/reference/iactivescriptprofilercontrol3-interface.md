---
title: IActiveScriptProfilerControl3 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7b57dbf76eb5dd9eadb05eb5705cdffb76106b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992990"
---
# <a name="iactivescriptprofilercontrol3-interface"></a>IActiveScriptProfilerControl3 (Interfaz)
Proporciona un método para enumerar los objetos del montón GC asociados con un motor de scripts.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## <a name="methods"></a>Métodos  
 [IActiveScriptProfilerControl3::EnumHeap (Método)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Devuelve una interfaz ([IActiveScriptProfilerHeapEnum (interfaz)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que puede utilizarse para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.