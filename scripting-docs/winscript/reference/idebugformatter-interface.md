---
title: IDebugFormatter (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35d1b811a017895ca40f3325bd0ac456070184f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979232"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter (Interfaz)
Permite que un lenguaje o el IDE personalice la conversión entre valores VARIANT o tipos VARTYPE y cadenas.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugFormatter` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Devuelve una cadena que representa el valor de variante especificado.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Devuelve una variante que contiene la cadena especificada.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Devuelve una cadena que representa el valor VARTYPE especificado.|