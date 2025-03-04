---
title: 'Tutorial: Crear un DataTable en el Diseñador de Dataset'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1126117cb1fc26c4f61bfb0f6ed0e19e86ce9323
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564927"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Tutorial: Crear un objeto DataTable en el Diseñador de Dataset

En este tutorial se explica cómo crear un <xref:System.Data.DataTable> (sin un TableAdapter) mediante el **Diseñador de Dataset**. Para obtener información sobre la creación de tablas de datos que incluyen los TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Crear una nueva aplicación de Windows Forms

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **DataTableWalkthrough**y, a continuación, elija **Aceptar**.

     El **DataTableWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**.

## <a name="add-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

2. En el panel izquierdo, seleccione **datos**, a continuación, seleccione **DataSet** en el panel central.

3. Haga clic en **Agregar**.

     Visual Studio agrega un archivo denominado **DataSet1.xsd** al proyecto y lo abre en el **Diseñador de Dataset**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Agregar una nueva DataTable al conjunto de datos

1. Arrastre un **DataTable** desde el **DataSet** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.

     Una tabla denominada **DataTable1** se agrega al conjunto de datos.

2. Haga clic en la barra de título de **DataTable1** y cámbiele el nombre `Music`.

## <a name="add-columns-to-the-datatable"></a>Agregar columnas a la DataTable

1. Haga clic en el **música** tabla. Seleccione **Agregar** y, a continuación, haga clic en **Columna**.

2. Nombre de la columna `SongID`.

3. En la ventana **Propiedades** , establezca la propiedad <xref:System.Data.DataColumn.DataType%2A> en <xref:System.Int16?displayProperty=fullName>.

4. Repita este proceso y agregue las siguientes columnas:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Establezca la clave principal para la tabla

Todas las tablas de datos deben tener una clave principal. Una clave principal identifica un registro específico en una tabla de datos.

Para establecer la clave principal, haga clic en el **IdCanción** columna y, a continuación, haga clic en **establecer clave principal**. Un icono clave aparece junto a la **IdCanción** columna.

## <a name="save-your-project"></a>Guardar el proyecto

Para guardar la **DataTableWalkthrough** proyecto, en el **archivo** menú, seleccione **guardar todo**.

## <a name="see-also"></a>Vea también

- [Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validar datos](../data-tools/validate-data-in-datasets.md)