---
title: Enlazar controles WPF a un conjunto de datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5231e37b7dd4881deaa6c85c8aa0e33d15bfcc0e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65673999"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Enlazar controles de WPF a un conjunto de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, se creará una aplicación de WPF que contiene controles enlazados a datos. Los controles se enlazan a registros de productos que se encapsulan en un conjunto de datos. También agregará botones para examinar los productos y guardar los cambios en los registros de productos.  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Crear una aplicación de WPF y un conjunto de datos que se genera a partir de los datos de la base de datos de ejemplo AdventureWorksLT.  
  
- Crear un conjunto de controles enlazados a datos arrastrando una tabla de datos desde la ventana **Orígenes de datos** a una ventana de WPF Designer.  
  
- Crear botones que naveguen hacia adelante y hacia atrás por los registros de productos.  
  
- Crear un botón que guarde los cambios que los usuarios realizan en los registros de productos en la tabla de datos y en el origen de datos subyacente.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Acceder a una instancia en ejecución de SQL Server o SQL Server Express que tenga asociada la base de datos de ejemplo AdventureWorksLT. Puede descargar la base de datos AdventureWorksLT el [sitio Web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  El conocimiento previo de los siguientes conceptos es útil, aunque no necesario, para completar el tutorial:  
  
- objetos DataSet y TableAdapter. Para obtener más información, consulte [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
- Trabajar con WPF Designer. Para obtener más información, consulte [WPF y Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Enlace a datos de WPF. Para obtener más información, consulte [Información general sobre el enlace de datos](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Crear el proyecto  
 Cree un nuevo proyecto de WPF. El proyecto mostrará registros de productos.  
  
#### <a name="to-create-the-project"></a>Para crear el proyecto  
  
1. Inicie Visual Studio.  
  
2. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3. Expanda **Visual Basic** o **Visual C#** y después seleccione **Windows**.  
  
4. Seleccione la plantilla de proyecto **Aplicación WPF**.  
  
5. En el **nombre** , escriba `AdventureWorksProductsEditor` y haga clic en **Aceptar**.  
  
     Visual Studio crea el `AdventureWorksProductsEditor` proyecto.  
  
## <a name="create-a-dataset-for-the-application"></a>Crear un conjunto de datos para la aplicación  
 Antes de crear controles enlazados a datos, debe definir un modelo de datos para la aplicación y agregarlo a la ventana **Orígenes de datos**. En este tutorial, se crea un conjunto de datos que se usará como modelo de datos.  
  
#### <a name="to-create-a-dataset"></a>Para crear un conjunto de datos  
  
1. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
     Se abre la ventana **Orígenes de datos**.  
  
2. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
     Se abrirá el **Asistente para configuración de orígenes de datos**.  
  
3. En la página **Elegir un tipo de origen de datos**, seleccione **Base de datos** y después haga clic en **Siguiente**.  
  
4. En la página **Elegir un modelo de base de datos**, seleccione **Conjunto de datos** y después haga clic en **Siguiente**.  
  
5. En la página **Elegir la conexión de datos**, seleccione una de estas opciones:  
  
    - Si hay disponible una conexión de datos a la base de datos de ejemplo AdventureWorksLT en la lista desplegable, selecciónela y haga clic en **Siguiente**.  
  
    - Haga clic en **Nueva conexión** y cree una conexión a la base de datos AdventureWorksLT.  
  
6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación**, active la casilla **Sí, guardar la conexión como** y haga clic en **Siguiente**.  
  
7. En la página **Elija los objetos de base de datos**, expanda el nodo **Tablas** y seleccione la tabla **Product (SalesLT)**.  
  
8. Haga clic en **Finalizar**.  
  
     Visual Studio agrega un nuevo archivo AdventureWorksLTDataSet.xsd al proyecto y agrega correspondiente **AdventureWorksLTDataSet** elemento a la **orígenes de datos** ventana. El archivo AdventureWorksLTDataSet.xsd define un conjunto de datos tipado llamado `AdventureWorksLTDataSet` y un TableAdapter llamado `ProductTableAdapter`. Más adelante, en este tutorial, usará `ProductTableAdapter` para rellenar con datos el conjunto de datos y guardar los cambios de nuevo en la base de datos.  
  
9. Compile el proyecto.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Editar el método de relleno predeterminado de TableAdapter  
 Para rellenar con datos el conjunto de datos, use el método `Fill` de `ProductTableAdapter`. De forma predeterminada, el método `Fill` rellena la tabla `ProductDataTable` del `AdventureWorksLTDataSet` con todas las filas de datos de la tabla Product. Puede modificar este método para que devuelva solo un subconjunto de las filas. Para este tutorial, modifique el método `Fill` para que devuelva solo las filas de productos que tengan fotos.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Para cargar filas de productos que tengan fotos  
  
1. En **el Explorador de soluciones**, haga doble clic en el archivo AdventureWorksLTDataSet.xsd.  
  
     Se abre el diseñador de DataSet.  
  
2. En el diseñador, haga clic en el **Fill,GetData()** de consulta y seleccione **configurar**.  
  
     Se abre el **Asistente para la configuración de TableAdapter**.  
  
3. En la página **Escriba una instrucción SQL**, agregue la siguiente cláusula WHERE después de la instrucción `SELECT` en el cuadro de texto.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4. Haga clic en **Finalizar**.  
  
## <a name="define-the-user-interface"></a>Definir la interfaz de usuario  
 Agregue varios botones a la ventana modificando el código XAML en WPF Designer. Más adelante en este tutorial, agregará código que permite a los usuarios desplazarse por los registros de productos y guardar cambios usando estos botones.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Para definir la interfaz de usuario de la ventana  
  
1. En **el Explorador de soluciones**, haga doble clic en MainWindow.xaml.  
  
     La ventana se abre en WPF Designer.  
  
2. En la vista [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] del diseñador, agregue el código siguiente entre las etiquetas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3. Compile el proyecto.  
  
## <a name="createdata-bound-controls"></a>Controles enlazados a crear  
 Crear controles que muestren registros de clientes, arrastrando el `Product` tabla desde el **orígenes de datos** ventana hasta WPF Designer.  
  
#### <a name="to-create-data-bound-controls"></a>Para crear controles enlazados a datos  
  
1. En la ventana **Orígenes de datos**, haga clic en el menú desplegable del nodo **Product** y seleccione **Detalles**.  
  
2. Expanda el nodo **Product**.  
  
3. En este ejemplo no se mostrarán algunos campos; por lo tanto, haga clic en el menú desplegable junto a los siguientes nodos y seleccione **Ninguno**:  
  
    - ProductCategoryID  
  
    - ProductModelID  
  
    - ThumbnailPhotoFileName  
  
    - rowguid  
  
    - ModifiedDate  
  
4. Haga clic en el menú desplegable junto al nodo **ThumbNailPhoto** y seleccione **Image**.  
  
    > [!NOTE]
    > De forma predeterminada, los elementos de la ventana **Orígenes de datos** que representan imágenes tienen sus controles predeterminados establecidos en **Ninguno**. Esto se debe a que las imágenes se almacenan como matrices de bytes en las bases de datos, y las matrices de bytes pueden contener desde una matriz de bytes simple al archivo ejecutable de una aplicación grande.  
  
5. Desde la ventana **Orígenes de datos**, arrastre el nodo **Product** a la fila de la cuadrícula situada debajo de la fila que contiene los botones.  
  
     Visual Studio genera el código XAML que define un conjunto de controles que están enlazados a los datos de la tabla **Products**. También genera el código que carga los datos. Para obtener más información sobre el XAML y el código generado, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6. En el diseñador, haga clic en el cuadro de texto junto a la etiqueta **Product ID**.  
  
7. En la ventana **Propiedades**, active la casilla junto a la propiedad **IsReadOnly**.  
  
## <a name="navigating-product-records"></a>Navegar por los registros de producto  
 Agregue código que permita a los usuarios desplazarse por los registros de productos usando los botones **\<** y **>**.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Para que los usuarios puedan navegar por los registros de productos  
  
1. En el diseñador, haga doble clic en el botón **<** en la superficie de la ventana.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `backButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2. Modifique el controlador de evento `Window_Loaded` para que `ProductViewSource`, `AdventureWorksLTDataSet` y `AdventureWorksLTDataSetProductTableAdapter` estén fuera del método y sean accesibles para todo el formulario. Declarar sólo son globales para el formulario y asígnelos dentro el `Window_Loaded` controlador de eventos similar al siguiente:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3. Agregue el código siguiente al controlador de eventos `backButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4. Vuelva al diseñador y haga doble clic en el botón **>**.  
  
5. Agregue el código siguiente al controlador de eventos `nextButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>SaveChanges para los registros de productos  
 Agregue código que permita a los usuarios guardar cambios en los registros de productos usando el botón **Guardar cambios**.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Para agregar la posibilidad de guardar cambios en los registros de productos  
  
1. En el diseñador, haga doble clic en el botón **Guardar cambios**.  
  
     Visual Studio abre el archivo de código subyacente y crea un nuevo controlador de evento `saveButton_Click` para el evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2. Agregue el código siguiente al controlador de eventos `saveButton_Click` :  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    > En este ejemplo se usa el método `Save` de `TableAdapter` para guardar los cambios. Esto es apropiado en este tutorial, porque solo se está cambiando una tabla de datos. Si tiene que guardar cambios en varias tablas de datos, puede usar también el método `UpdateAll` de `TableAdapterManager` que Visual Studio genera con el conjunto de datos. Para obtener más información, consulte [información general sobre TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Compile y ejecute la aplicación. Compruebe que puede ver y actualizar los registros de productos.  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1. Presione **F5**.  
  
     La aplicación se compila y se ejecuta. Compruebe lo siguiente:  
  
    - Los cuadros de texto muestran datos del primer registro de producto que tiene una foto. Este producto tiene el identificador 713 y el nombre **Long-Sleeve Logo Jersey, S**.  
  
    - Puede hacer clic en los botones **>** o **<** para navegar por otros registros de productos.  
  
2. En uno de los registros de productos, cambie el valor **Tamaño** y haga clic en **Guardar cambios**.  
  
3. Cierre la aplicación y presione **F5** en Visual Studio para reiniciarla.  
  
4. Navegue al registro de producto que ha cambiado y compruebe que el cambio se conserva.  
  
5. Cierre la aplicación.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Una vez completado este tutorial, puede realizar las siguientes tareas relacionadas:  
  
- Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para enlazar controles WPF a otros tipos de orígenes de datos. Para obtener más información, consulte [WPF enlazar controles a un servicio de datos WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
- Aprenda cómo usar la ventana **Orígenes de datos** en Visual Studio para mostrar datos relacionados (es decir, datos en una relación primario-secundario) en controles WPF. Para obtener más información, vea [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Herramientas de conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Información general de diseñador de Silverlight y WPF](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Información general sobre el enlace de datos](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
