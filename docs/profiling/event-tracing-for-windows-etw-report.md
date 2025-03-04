---
title: Informe Seguimiento de eventos para Windows (ETW) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13a3db996537005c0d4ec67b85c185ac2841cc0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447251"
---
# <a name="event-tracing-for-windows-etw-report"></a>Informe Seguimiento de eventos para Windows (ETW)
El informe Seguimiento de eventos para Windows (ETW) muestra los eventos ETW registrados en una sesión de rendimiento de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Los datos ETW se recopilan en un archivo binario (.*etl*).

> [!NOTE]
> No se puede mostrar informes ETW en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Para obtener información sobre cómo recopilar datos ETW mediante las Herramientas de generación de perfiles desde la interfaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Cómo: Recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Para obtener información sobre cómo recopilar datos ETW mediante las herramientas de la línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), vea [Eventos](../profiling/events-vsperfcmd.md).

- Genere el informe ETW mediante el comando **VSReport/Summary:ETW**. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).

|Columna|Descripción|
|------------|-----------------|
|**Marca de tiempo**|Identifica la hora en la que se ha producido el evento.|
|**Identificador del proceso**|Identifica el proceso que ha generado el evento.|
|**Identificador de subproceso**|Identifica el subproceso que ha generado el evento.|
|**Descripción**|Identifica el proveedor del evento.|
|**Type**|Identifica el tipo de evento.|
|**Propiedades**|Propiedades del evento. Cada evento es un par nombre-valor separado por comas e incluido entre corchetes.|