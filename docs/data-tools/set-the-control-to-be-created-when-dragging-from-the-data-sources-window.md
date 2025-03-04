---
title: Establecer el control para crear al arrastrar desde la ventana Orígenes de datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 442a98b76efb8013d5d40607e14586299718afc3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715099"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos

Puede crear controles enlazados a datos si arrastra los elementos desde la ventana **Orígenes de datos** hasta WPF Designer o el Diseñador de Windows Forms. Cada elemento de la ventana **Orígenes de datos** tiene un control predeterminado que se crea al arrastrar el elemento hacia el diseñador. Sin embargo, puede elegir crear un control diferente.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Establecimiento de los controles que se van a crear para tablas de datos u objetos

Antes de arrastrar los elementos que representan objetos o tablas de datos a la ventana **Orígenes de datos**, puede decidir mostrar todos los datos en un control o mostrar cada columna o propiedad en un control independiente.

En este contexto, el término *objeto* hace referencia a un objeto comercial personalizado, una entidad (en un Entity Data Model) o un objeto devuelto por un servicio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Para establecer los controles que se van a crear para tablas de datos u objetos

1. Asegúrese del **WPF** diseñador o el **Windows Forms** diseñador está abierto.

2. En la ventana **Orígenes de datos**, seleccione el elemento que representa el objeto o la tabla de datos que desea establecer.

   > [!TIP]
   > Si el **orígenes de datos** ventana no está abierta, puede abrirlo seleccionando **vista** > **Other Windows** > **losorígenesdedatos**.

3. Haga clic en el menú desplegable del elemento y, a continuación, en uno de los siguientes elementos en el menú:

    - Para mostrar cada campo de datos en un control independiente, haga clic en **Detalles**. Al arrastrar el elemento de datos hacia el diseñador, se creará un control enlazado a datos diferente por cada columna o propiedad del objeto o tabla de datos primaria, junto con las etiquetas de cada control.

    - Para mostrar todos los datos en un control único, seleccione un control diferente de la lista, como **DataGrid** o **List** en una aplicación WPF o **DataGridView** en una aplicación de Windows Forms.

    La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET su proyecto tiene como destino, y si han agregado controles personalizados que compatibilidad con enlaces de datos a la **cuadro de herramientas**. Si el control que desea crear no está en la lista de controles disponibles, puede agregar el control a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Para obtener información sobre cómo crear un control personalizado de Windows Forms que se puede agregar a la lista de controles para las tablas de datos u objetos en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita datos complejos enlace](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Establecer los controles que deben crearse para las propiedades o columnas de datos

Antes de arrastrar al diseñador un elemento que representa una columna o la propiedad de un objeto en la ventana **Orígenes de datos**, puede establecer el control que se va a crear.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Para establecer los controles que se van a crear para columnas o propiedades

1. Asegúrese del **WPF** diseñador o el **Windows Forms** diseñador está abierto.

2. En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.

3. Seleccione cada columna o propiedad para la que desea establecer el control que se va a crear.

4. Haga clic en el menú desplegable de la columna o propiedad y seleccione el control que desea crear cuando el elemento se arrastre al diseñador.

     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET su proyecto tiene como destino, y qué controles personalizados que admiten enlace de datos se han agregado a la **cuadro de herramientas**. Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Para obtener información sobre cómo crear un control personalizado que se puede agregar a la lista de controles para columnas de datos o propiedades en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Si no desea crear un control para la columna o propiedad, seleccione **ninguno** en el menú desplegable. Esto es útil si desea arrastrar la tabla o el objeto principal al diseñador, pero sin incluir la columna o propiedad concreta.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)