---
title: marker_series (Clase) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194938"
---
# <a name="markerseries-class"></a>marker_series (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Representa un canal en serie de eventos generados por un único proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|nombre|DESCRIPCIÓN|  
|----------|-----------------|  
|[marker_series::marker_series (Constructor)](../profiling/marker-series-marker-series-constructor.md)|Inicializa una nueva instancia de la clase `marker_series`.|  
|[marker_series::~marker_series (Destructor)](../profiling/marker-series-tilde-marker-series-destructor.md)|Destruye el objeto marker_series y libera todos los recursos asignados.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|nombre|DESCRIPCIÓN|  
|----------|-----------------|  
|[marker_series::is_enabled (Método)](../profiling/marker-series-is-enabled-method.md)|Determina si alguna sesión habilitó el proveedor.|  
|[marker_series::write_alert (Método)](../profiling/marker-series-write-alert-method.md)|Escribe una alerta en el archivo de seguimiento del visualizador de simultaneidad.|  
|[marker_series::write_flag (Método)](../profiling/marker-series-write-flag-method.md)|Escribe una marca en el archivo de seguimiento del visualizador de simultaneidad.|  
|[marker_series::write_message (Método)](../profiling/marker-series-write-message-method.md)|Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `marker_series`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Otras referencias  
 [diagnostic (Espacio de nombres)](../profiling/diagnostic-namespace.md)
