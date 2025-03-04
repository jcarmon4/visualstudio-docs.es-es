---
title: 'Paso 7: Agregar componentes de diálogo al formulario | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54d2b83fab24aa3c9deabc979782d9b82ea5c482
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442484"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Paso 7: adición de componentes de cuadro de diálogo al formulario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para que el programa abra archivos de imagen y para elegir un color de fondo, en este paso agregará un componente **OpenFileDialog** y un componente **ColorDialog** al formulario.  
  
 En algunos sentidos, un componente es como un control. El Cuadro de herramientas se usa para agregar un componente al formulario, y las propiedades se establecen mediante la ventana **Propiedades**. Sin embargo, a diferencia de un control, al agregar un componente al formulario no se agrega un elemento visible que el usuario puede ver. En cambio, se proporcionan determinados comportamientos que se pueden desencadenar mediante código. Un componente es lo que abre un cuadro de diálogo **Abrir archivo**.  
  
 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo")para una versión en vídeo de este tema, consulte [Tutorial 1: Crear un visor de imágenes en Visual Basic - vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205213) o [Tutorial 1: Crear un visor de imágenes en C# - vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205202). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Para agregar componentes de cuadro de diálogo al formulario  
  
1. Elija el Diseñador de Windows Forms (Form1.cs [Diseño] o Form1.vb [Diseño]) y después abra el grupo **Cuadros de diálogo** del cuadro de herramientas.  
  
    > [!NOTE]
    > El grupo **Cuadros de diálogo** del Cuadro de herramientas tiene componentes que abren automáticamente muchos cuadros de diálogo de gran utilidad y que se pueden usar para abrir y guardar archivos, examinar carpetas y elegir fuentes o colores. Use dos componentes de cuadro de diálogo en este proyecto: **OpenFileDialog** y **ColorDialog**.  
  
2. Para agregar un componente denominado **openFileDialog1** al formulario, haga doble clic en **OpenFileDialog**. Para agregar un componente denominado **colorDialog1** al formulario, haga doble clic en **ColorDialog** en el Cuadro de herramientas. (Este se utiliza en el siguiente paso del tutorial.) Debería aparecer un área en la parte inferior del Diseñador de Windows Forms (bajo el formulario del Visor de imágenes), con un icono para cada uno de los dos componentes de cuadro de diálogo agregados, tal y como se muestra en la siguiente imagen.  
  
     ![Componentes del cuadro de diálogo](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
Componentes del cuadro de diálogo  
  
3. Elija el icono **openFileDialog1** del área de la parte inferior del Diseñador de Windows Forms. Establezca dos propiedades:  
  
    - Establezca la propiedad **Filter** tal y como se indica a continuación (puede copiarlo y pegarlo):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    - Establezca la propiedad **Título** en lo siguiente: **Seleccione un archivo de imagen**  
  
         Los valores de la propiedad **Filter** especifican las clases de tipos de archivo que se mostrarán en el cuadro de diálogo **Select a picture file** (Seleccionar un archivo de imagen).  
  
    > [!NOTE]
    > Para ver un ejemplo del cuadro de diálogo **Abrir archivo** en una aplicación diferente, abra el Bloc de notas o Paint y, en la barra de menús, elija **Archivo**, **Abrir**. Observe que hay una lista desplegable de **tipo de archivo** en la parte inferior. Acabamos de usar la propiedad **Filter** del componente **OpenFileDialog** para configurarlo. Observe también que las propiedades **Title** y **Filter** están en negrita en la ventana **Propiedades**. El IDE lo hace para mostrarle todas las propiedades que han cambiado respecto de sus valores predeterminados.  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
- Para ir al siguiente paso del tutorial, vea [Paso 8: Escribir código para la presentación de un controlador de eventos de botón de imagen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
- Para volver al paso anterior del tutorial, vea [Paso 6: Nombre de los controles de botón](../ide/step-6-name-your-button-controls.md).
