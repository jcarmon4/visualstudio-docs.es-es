---
title: Recopilar datos de simultaneidad de subprocesos y procesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568190"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Recopilar datos de simultaneidad de subprocesos y procesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El método de generación de perfiles de simultaneidad de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite recopilar datos de contención de recursos que incluyen información sobre cada evento de sincronización que hace que una función de la aplicación perfilada espere para obtener acceso a un recurso.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Puede especificar el método de generación de perfiles de simultaneidad mediante uno de los procedimientos siguientes:  
  
- En la primera página del Asistente de generación de perfiles, haga clic en **Simultaneidad**  
  
- En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Simultaneidad**.  
  
- En la barra de herramientas **Explorador de rendimiento**, en la lista **Método**, haga clic en **Simultaneidad**.  
  
## <a name="common-tasks"></a>Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** de la sesión de rendimiento. Para abrir este cuadro de diálogo:  
  
- En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.  
  
  Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** cuando genere perfiles mediante el método de simultaneidad.  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|En la página **General** , especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|-   [Cómo: Establecimiento de opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Iniciar**, especifique la aplicación que quiere iniciar si tiene varios proyectos .exe en la solución de código.|-   [Cómo: Especificación del archivo binario en inicio](../profiling/how-to-specify-the-binary-to-start.md)|  
|En la página **Interacción de capas** , agregue los datos de la llamada ADO.NET a la ejecución de la generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|-   [Cómo: Recopilación de datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzado**, especifique la versión del runtime de .NET Framework de la cual quiere generar el perfil si los módulos de aplicación utilizan varias versiones. De forma predeterminada, se genera el perfil de la primera versión cargada.|-   [Cómo: Especificación del entorno de ejecución de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
