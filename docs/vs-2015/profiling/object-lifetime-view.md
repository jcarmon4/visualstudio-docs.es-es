---
title: Visa Duración del objeto| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef216c1220cbfda37da579d3ea2dfdd32837ab75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195569"
---
# <a name="object-lifetime-view"></a>Vista Duración del objeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Duración del objeto está disponible cuando se activa **Also collect .NET object lifetime data** (Recopilar también datos de duración del objeto de .NET) en las páginas de propiedades de la sesión de rendimiento.  
  
 El recolector de elementos no utilizados de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] administra la asignación y liberación de la memoria para la aplicación. Para optimizar el rendimiento del recolector de elementos no utilizados, el montón administrado se divide en tres generaciones: 0, 1 y 2. El recolector de elementos no utilizados del runtime almacena los nuevos objetos en la generación 0. Los objetos que sobreviven a las recopilaciones se promueven y almacenan en las generaciones 1 y 2.  
  
 El recolector de elementos no utilizados recupera memoria desasignando una generación completa de objetos. Para los objetos creados por la aplicación de la que se generaron perfiles, la vista Duración del objeto muestra el número y tamaño de los objetos y la generación en la que se recuperan.  
  
## <a name="general"></a>General  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Nombre de la clase**|Nombre de clase del tipo asignado.|  
|**Identificador del proceso**|El identificador del proceso de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
  
## <a name="instance-data"></a>Datos de instancia  
 Datos de instancia indica el número de objetos del tipo que se crearon en la generación de perfiles y la generación en la que se desasignaron objetos por parte del recolector de elementos no utilizados.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Instancias**|Número de asignaciones de objetos de este tipo.|  
|**Total de instancias %**|Porcentaje del número total de asignaciones que se realizaron en la generación de perfiles.|  
|**Instancias recopiladas en la generación 0**|Número de instancias del tipo que se han desasignado en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 1**|Número de instancias del tipo que se han desasignado en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 2**|Número de instancias del tipo que se han desasignado en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias activas al final**|Número de instancias del tipo que no se han desasignado hasta el final de la generación de perfiles.|  
  
## <a name="size-byte-data"></a>Tamaño (bytes) de datos  
 El tamaño (bytes) de datos indica el número de objetos del tipo que se crearon en la generación de perfiles y la cantidad de memoria que se reclamó en cada generación en la que se desasignaron los objetos.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Total de bytes asignados**|Número total de bytes de todas las instancias del tipo.|  
|**Total de bytes %**|Porcentaje del número total de bytes asignados en la generación de perfiles, que se asignaron para instancias de este tipo.|  
|**Bytes recopilados en la generación 0**|Tamaño de las instancias del tipo que se han desasignado en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 1**|Tamaño de las instancias del tipo que se han desasignado en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 2**|Tamaño de las instancias del tipo que se han desasignado en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
  
## <a name="large-object-heap-data"></a>Tamaño de montón de objetos grandes  
 El asignador de memoria de .NET administra objetos muy grandes en una ubicación que es independiente del montón administrado estándar. Los datos de montón de objeto grande indican el número y el tamaño de los objetos del tipo que se administraron en esta ubicación.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Instancias de montón de objeto grande recopiladas**|Número de instancias de este tipo que se encontraban en el montón de objeto grande y que se recopilaron en la generación de perfiles.|  
|**Bytes de montón de objeto grande recopilados**|Tamaño, en bytes, de las instancias de este tipo que se encontraban en el montón de objeto grande y que se recopilaron en la generación de perfiles.|  
  
## <a name="see-also"></a>Otras referencias  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)
