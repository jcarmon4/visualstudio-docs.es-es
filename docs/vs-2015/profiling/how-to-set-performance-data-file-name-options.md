---
title: Procedimiento Establecer opciones de nombre de archivo de datos de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: faaa78d34c71d1f0b436b861ccb1ac4892267e9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205786"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedimiento Establecimiento de opciones de nombre de archivo de datos de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, se guarda un archivo de generación de perfiles de datos (.vsp) mediante la siguiente sintaxis:  
  
 *Path\VSP-File\YYMMDD(N)* **.vsp**  
  
 Puede cambiar cualquier parámetro de nomenclatura en la página General del cuadro de diálogo de propiedades de la sesión de rendimiento.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|||  
|-|-|  
|*Path*|El directorio que contiene el informe. La ubicación predeterminada es la carpeta de soluciones o la ubicación predeterminada de los proyectos y soluciones del usuario.|  
|*VSP-File*|El nombre del archivo de datos de generación de perfiles. El nombre predeterminado es el nombre de la solución o ejecutable del que se generan perfiles.|  
|*YYMMDD*|Una marca de fecha que muestra el año, mes y día en que se recopilaron los datos de generación de perfiles.|  
|*(N)*|Si existe más de un archivo de datos de generación de perfiles, se agrega un número incrementado al nombre de archivo entre paréntesis.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Para cambiar la sintaxis de nomenclatura de los archivos de datos de generación de perfiles de una sesión de rendimiento  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho en el nombre de la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2. Haga clic en **General**.  
  
3. En **Informe**, cambie cualquiera de las siguientes opciones:  
  
    |||  
    |-|-|  
    |**Ubicación del informe**|Especifique un directorio para almacenar los archivos de datos de generación de perfiles.|  
    |**Nombre del informe**|Especifique un nombre base para los archivos.|  
    |**Agregar nuevos informes a la sesión automáticamente**|Active la casilla para agregar automáticamente el archivo de datos a la sesión de rendimiento.|  
    |**Anexar un número incremental a informes generados**|Active la casilla para agregar un número incremental al nombre de archivo cuando exista más de un archivo con el mismo nombre. Desactive la casilla para sobrescribir un archivo existente.|  
    |**Usar una marca de tiempo para el número**|Active la casilla para agregar una fecha al nombre de archivo.|
