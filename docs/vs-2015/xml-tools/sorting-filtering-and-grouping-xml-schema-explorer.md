---
title: Ordenar, filtrar y agrupar (Explorador de esquemas XML) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c13f7c710e462e1edd45acbf68fa4642d3d422
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150669"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordenar, filtrar y agrupar (Explorador de esquemas XML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describe las opciones que están disponibles a través de la **opciones de agrupación, filtrado y ordenación** menú en la barra de herramientas del explorador de esquemas XML.  
  
## <a name="filter-options"></a>Opciones de filtro:  
 Están disponibles las opciones de filtro siguientes: De forma predeterminada, el **mostrar espacios de nombres** y **mostrar archivos de esquema** opciones están seleccionadas.  
  
- **Mostrar espacios de nombres**.  
  
- **Mostrar archivos de esquema**.  
  
- **Mostrar compositores (secuencia/choice/all)** .  
  
## <a name="sorting-options"></a>Opciones de ordenación  
 Están disponibles las opciones de ordenación siguientes: El valor predeterminado es **ordenar por tipo**. Las opciones de ordenación no se aplican a archivos ni espacios de nombres.  
  
- **Ordenar por tipo**.  
  
- **Ordenar por nombre**.  
  
- **Orden de documento**.  
  
### <a name="sort-by-type"></a>Ordenar por tipo  
 Cuando el **ordenar por tipo** está seleccionada, los nodos globales se ordenan en el orden siguiente. Después, los nodos se ordenan alfabéticamente en cada grupo.  
  
1. nodos `import`.  
  
2. nodos `include`.  
  
3. nodos `redefine`.  
  
4. nodos `attribute`.  
  
5. nodos `attributeGroup`.  
  
6. nodos `complexType`.  
  
7. nodos `simpleType`.  
  
8. nodos `element`.  
  
9. nodos `group`.  
  
### <a name="sort-by-name"></a>Ordenar por Nombre  
 Cuando el **ordenar por nombre** está seleccionada, los nodos globales se ordenan en el orden siguiente:  
  
1. nodos `import` (por orden alfabético de espacios de nombres).  
  
2. nodos `include` (por orden alfabético de atributos `schemaLocation`).  
  
3. nodos `redefine` (por orden alfabético de atributos `schemaLocation`).  
  
4. Otros nodos globales por orden alfabético.  
  
### <a name="document-order"></a>Orden del documento  
 El **orden del documento** opción está disponible cuando el **mostrar archivos de esquema** está seleccionada. Cuando **orden del documento** está activada, los nodos globales se muestran en el orden en que aparecen en el archivo de esquema.  
  
## <a name="persisting-sortfilter-options"></a>Opciones de ordenación y filtrado persistentes  
 Las opciones de ordenación, filtrado y agrupación se guardan en el Registro para cada usuario, independientemente de la solución o de los archivos que estuvieran abiertos cuando se cambió la configuración.
