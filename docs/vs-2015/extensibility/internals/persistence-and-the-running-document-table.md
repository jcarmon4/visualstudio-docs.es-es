---
title: Tabla de documentos de persistencia y la ejecución | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196087"
---
# <a name="persistence-and-the-running-document-table"></a>Persistencia y tabla de documentos en ejecución
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, los proyectos son completamente responsables de administrar la persistencia de sus elementos de proyecto que realizan mediante el servicio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Documentos son la unidad básica de persistencia en el entorno de Visual Studio. Los proyectos de coordinan la apertura, guardar y cambiar el nombre de los documentos con la tabla de documentos ejecución (RDT), un recurso que realiza el seguimiento del estado de todos los documentos abiertos.  
  
## <a name="managing-persistence"></a>Administrar la persistencia  
 Proyectos de control de servicio de persistencia del entorno mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaz. Mientras el entorno pide nunca directamente un documento para continuar, le pide el proyecto propietario (o jerarquía) para guardar el documento. Esto hace posible que el proyecto para guardar sus datos de elemento de proyecto en archivos locales, los archivos remotos, una base de datos, un repositorio o cualquier otro medio.  
  
 El entorno global mantiene la RDT. El entorno mantiene las entradas de todas las ventanas abiertas y documentos en el RDT, que hace posible para que puedan reciben notificaciones especiales, como cuando se cierra una solución. Además, la RDT hace posible para el entorno para realizar un seguimiento de sus nodos correspondientes en **el Explorador de soluciones**. La RDT mantiene un registro por cada objeto abierto y con persistencia, incluidos los archivos de proyecto y documentos de elemento de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
