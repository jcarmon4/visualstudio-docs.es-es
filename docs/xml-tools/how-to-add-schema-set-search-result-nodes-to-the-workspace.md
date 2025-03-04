---
title: Agregar nodos de resultados de búsqueda del conjunto de esquemas XML al área de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2718c08b36ff9ef3ca8ae06f7d511cacb8fa73c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923655"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedimiento Adición de nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo

En este tema se explica cómo agregar nodos que están resaltados en el **Explorador de esquemas XML** como resultado de una búsqueda de palabras clave en el área de trabajo.

> [!NOTE]
> Solo se pueden agregar nodos globales al [área de trabajo](../xml-tools/xml-schema-designer-workspace.md).

En este ejemplo se usa el [esquema del pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md)de ejemplo.

## <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1. Siga los pasos que [se describen en cómo: Crear y editar un archivo](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)de esquema XSD.

2. Escriba "purchaseOrder" en el cuadro de texto buscar de la barra de herramientas del [Explorador XML](../xml-tools/xml-schema-explorer.md) y haga clic en el botón Buscar.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de la búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan con TICs en la barra de desplazamiento vertical.

3. Agregue los resultados de la búsqueda al área de trabajo haciendo clic en el botón **agregar nodos resaltados al área de trabajo** en el panel de resultados de resumen.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     El `purchaseOrder` nodo y el `PurchaseOrderType` nodo aparecen junto a los demás en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.