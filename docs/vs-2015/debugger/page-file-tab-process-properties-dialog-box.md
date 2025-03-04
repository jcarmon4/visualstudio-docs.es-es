---
title: Ficha de archivo de paginación, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192720"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la **archivo de paginación** pestaña para examinar el archivo de paginación de un proceso. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en el **archivo de paginación** pestaña:  
  
|Entrada|DESCRIPCIÓN|  
|-----------|-----------------|  
|**Bytes de archivo de paginación**|El número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos utilizado por el proceso, pero no contenidas en otros archivos. El archivo de paginación se usa por todos los procesos y la falta de espacio en el archivo de paginación puede provocar errores mientras se está ejecutando otros procesos.|  
|**Bytes de archivo de paginación máximos**|El número máximo de páginas que este proceso ha usado en el archivo de paginación.|  
|**Errores de página**|El número de errores de página por los subprocesos ejecutados en este proceso. Se produce un error de página cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo en la memoria principal. Por lo tanto, la página no se recuperará desde el disco si se encuentra en la lista en espera y, por tanto, en la memoria principal, o si lo está usando otro proceso con el que se comparte la página.|
