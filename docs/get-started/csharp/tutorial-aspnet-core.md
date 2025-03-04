---
title: 'Tutorial: Introducción a C# y ASP.NET Core'
titleSuffix: ''
description: Obtenga información sobre cómo crear una aplicación web ASP.NET Core en Visual Studio con C#, paso a paso.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ac544f033e8b021b7ef0a6253fbd0cb65b4450f5
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180470"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutorial: Introducción a C# y ASP.NET Core en Visual Studio

En este tutorial para el desarrollo de C# con ASP.NET Core mediante Visual Studio, creará una aplicación web de C# ASP.NET Core, realizará cambios en ella, explorará algunas características del IDE y luego ejecutará la aplicación.

## <a name="before-you-begin"></a>Antes de empezar

### <a name="install-visual-studio"></a>Instalar Visual Studio

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

### <a name="update-visual-studio"></a>Actualizar Visual Studio

Si ya ha instalado Visual Studio, asegúrese de que se está ejecutando la versión más reciente. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualización de Visual Studio a la versión más reciente](../../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Elija su tema (opcional)

En este tutorial se incluyen capturas de pantalla que utilizan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](../../ide/quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de ASP.NET Core. En el tipo de proyecto se incluyen todos los archivos de plantilla que se necesitarán para un sitio web completamente funcional, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual C#** , expanda **Web** y después seleccione **.NET Core**. En el panel central, elija **Aplicación web ASP.NET Core**. Después, asigne el nombre del archivo *MyCoreApp* y elija **Aceptar**.

   ![Plantilla de proyecto Aplicación web ASP.NET Core en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Agregar una carga de trabajo (opcional)

Si no ve la plantilla de proyecto **Aplicación web ASP.NET Core**, puede obtenerla mediante la adición de la carga de trabajo **Desarrollo de ASP.NET y web**. Puede agregar esta carga de trabajo de una de las dos formas siguientes, según las actualizaciones de Visual Studio 2017 que estén instaladas en el equipo.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Uso del cuadro de diálogo Nuevo proyecto

1. Seleccione el vínculo **Abrir el Instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**. (Según la configuración de pantalla, es posible que tenga que desplazarse para verlo).

   ![Seleccione el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../media/open-visual-studio-installer-mycoreapp.png)

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después haga clic en **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../media/tutorial-aspnet-workload.png)

   (Es posible que deba cerrar Visual Studio para continuar con la instalación de la carga de trabajo nueva).

#### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Uso de la barra del menú Herramientas

1. Cancele el cuadro de diálogo **Nuevo proyecto**. Después, en la barra de menús, elija **Herramientas** > **Obtener herramientas y características**.

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después haga clic en **Modificar**.

   (Es posible que deba cerrar Visual Studio para continuar con la instalación de la carga de trabajo nueva).

### <a name="add-a-project-template"></a>Agregar una plantilla de proyecto

1. En el cuadro de diálogo **Nueva aplicación web ASP.NET Core**, seleccione la plantilla de proyecto **Aplicación web**.

1. Compruebe que **ASP.NET Core 2.1** aparece en el menú desplegable superior. Después, elija **Aceptar**.

   ![Cuadro de diálogo Nueva aplicación web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Si no ve **ASP.NET Core 2.1** en el menú desplegable superior, asegúrese de que se ejecuta la versión más reciente de Visual Studio. Para obtener más información sobre cómo actualizar la instalación, vea la página [Actualización de Visual Studio a la versión más reciente](../../install/update-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *ASP.NET*. Seguidamente, elija **C#** en la lista de lenguajes y luego, **Windows** en la lista de plataformas.

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación web ASP.NET Core** y, luego, **Siguiente**.

   ![Seleccionar la plantilla C# para Aplicación web ASP.NET Core](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación web ASP.NET Core**, puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de ASP.NET y web**.
   >
   > ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Si se le pide que guarde su trabajo, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *MyCoreApp* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ![En la ventana "Configurar el nuevo proyecto", asigne al proyecto el nombre "MyCoreApp".](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. En la ventana **Crear una aplicación web ASP.NET Core**, compruebe que **ASP.NET Core 2.1** aparece en el menú desplegable de la parte superior. Luego, elija **Aplicación Web**, que incluye Razor Pages de ejemplo. Seguidamente, elija **Crear**.

   ![Ventana "Crear una aplicación web ASP.NET Core"](./media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Visual Studio se abre en el nuevo proyecto.

::: moniker-end

### <a name="about-your-solution"></a>Acerca de la solución

Esta solución sigue el modelo de diseño **Razor Page**. La diferencia con el modelo de diseño [Modelo-Vista-Controlador (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) es que está optimizado para incluir el modelo y el código de control dentro de la misma Razor Page.

## <a name="tour-your-solution"></a>Recorrido por la solución

 1. La plantilla de proyecto crea una solución con un solo proyecto de ASP.NET Core que se denomina _MyCoreApp_. Elija la pestaña **Explorador de soluciones** para ver el contenido.

    ![Explorador de soluciones de ASP.NET en Visual Studio para la solución Razor Pages que se denomina MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Expanda la carpeta **Páginas** y expanda *About.cshtml*.

     ![El archivo About.cshtml en el Explorador de soluciones de Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Vea el archivo **About.cshtml** en el editor de código.

     ![Visualización del archivo About.cshtml en el editor de código de Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Elija el archivo **About.cshtml.cs**.

     ![Elección del archivo About.cshtml en el editor de código de Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Vea el archivo **About.cshtml.cs** en el editor de código.

     ![Visualización del archivo About.cshtml en el editor de código de Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. El proyecto contiene una carpeta **wwwroot** que es la raíz del sitio web. Expanda la carpeta para ver su contenido.

     ![Carpeta wwwroot en el Explorador de soluciones en Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Puede colocar contenido estático del sitio &mdash;como CSS, imágenes y bibliotecas de JavaScript&mdash; directamente en las rutas de acceso que quiera.

 1. El proyecto también contiene archivos de configuración que administran la aplicación web en el entorno de ejecución. La [configuración](/aspnet/core/fundamentals/configuration) predeterminada de la aplicación se almacena en *appsettings.json*. Sin embargo, puede invalidar esta configuración mediante el uso de *appsettings.Development.json*. Expanda el archivo **appsettings.json** para ver el archivo **appsettings.Development.json**.

     ![Archivos de configuración en el Explorador de soluciones en Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Ejecutar, depurar y realizar cambios

1. Haga clic en el botón **IIS Express** del IDE para compilar y ejecutar la aplicación en modo de depuración. (O bien, presione **F5** o elija **Depurar** > **Iniciar depuración** en la barra de menús).

     ![Haga clic en el botón IIS Express de Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Si recibe un mensaje de error que indica **No se puede conectar al servidor web "IIS Express"** , cierre Visual Studio y, luego, ábralo mediante la opción **Ejecutar como administrador** que aparece si hace clic con el botón derecho o en el menú contextual. A continuación, vuelva a ejecutar la aplicación.
     >
     > También es posible que obtenga un mensaje que le pregunta si desea aceptar un certificado SSL de IIS Express. Para ver el código en un explorador web, elija **Sí** y luego, si recibe un mensaje de advertencia de seguridad de seguimiento, elija **Sí**.

1. Visual Studio inicia una ventana del explorador. Luego debería ver las páginas **Inicio**, **Acerca de** y **Contacto** en la barra de menús. (Si no es así, elija el elemento de menú "hamburguesa" para verlas).

    ![Selección del elemento de menú "hamburguesa" en la barra de menús de la aplicación web](media/csharp-aspnet-razor-browser-page.png)

1. Elija **Acerca de** en la barra de menús.

   ![Selección de Acerca de en la barra de menús de la ventana del explorador de la aplicación](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Entre otras cosas, la página **Acerca de** en el explorador representa el texto que se establece en el archivo *About.cshtml*.

   ![Ver el texto de la página Acerca de](media/csharp-aspnet-razor-browser-page-about.png)

1. Vuelva a Visual Studio y, a continuación, presione **Mayús+F5** para detener el modo de depuración. También se cierra el proyecto en la ventana del explorador.

1. En Visual Studio, elija **About.cshtml**. Luego, elimine la palabra _additional_ y, en su lugar, agregue las palabras _file and directory_.

    ![Cambio del texto en el archivo About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Elija **About.cshtml.cs**. Luego, limpie las directivas `using` que se encuentran al inicio del archivo con el siguiente método abreviado:

   Elija cualquiera de las directivas `using` atenuadas y aparecerá una bombilla [Acciones rápidas](../../ide/quick-actions.md) justo debajo del símbolo de intercalación o en el margen izquierdo. Elija la bombilla y después elija **Eliminar instrucciones Using innecesarias**.

   ![Eliminación de las instrucciones Using innecesarias en el archivo About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio elimina las directivas `using` innecesarias del archivo.

1. Luego, en el método `OnGet()`, cambie el cuerpo por el código siguiente:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Observe que aparecerán dos caracteres de subrayado ondulados en **Environment** y **String**. Los caracteres de subrayado ondulados aparecen porque estos tipos están fuera del ámbito.

   ![Errores marcados con caracteres de subrayado ondulados en el método OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Abra la barra de herramientas **Lista de errores** para ver los mismos errores en la lista. Si no ve la barra de herramientas **Lista de errores**, elija **Ver** > **Lista de errores** en la barra de menús superior.

   ![Lista de errores en Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Solucionemos este problema. En el editor de código, coloque el cursor en cualquiera de las líneas que contienen el error y elija la bombilla Acciones rápidas ubicada en el margen izquierdo. Luego, en el menú desplegable, elija **using System;** para agregar esta directiva al inicio del archivo y solucionar los errores.

   ![Incorporación de la directiva "using System;"](media/csharp-aspnet-razor-add-usings.png)

1. Presione **Ctrl**+**S** para guardar los cambios y, a continuación, presione **F5** para abrir el proyecto en el explorador web.

1. En la parte superior del sitio web, elija **Acerca de** para ver los cambios.

   ![Visualización de la página Acerca de actualizada que incluye los cambios realizados](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Cierre el explorador web, presione **Mayús**+**F5** para detener el modo de depuración y cierre Visual Studio.

## <a name="quick-answers-faq"></a>Respuestas rápidas a preguntas frecuentes

Esta es una sección rápida de P+F para destacar algunos conceptos clave.

### <a name="what-is-c"></a>¿Qué es C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) es un lenguaje de programación con seguridad de tipos y orientado a objetos que se ha diseñado para ser robusto y fácil de aprender.

### <a name="what-is-aspnet-core"></a>¿Qué es ASP.NET Core?

ASP.NET Core es un marco multiplataforma y de código abierto en el que se pueden crear aplicaciones conectadas a Internet, como por ejemplo, servicios y aplicaciones web. Las aplicaciones de ASP.NET Core se pueden ejecutar en .NET Core o .NET Framework. Puede desarrollar y ejecutar las aplicaciones multiplataforma ASP.NET Core en Windows, Mac y Linux. ASP.NET Core es código abierto en [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>¿Qué es Visual Studio?

Visual Studio es un conjunto de desarrollo integrado de herramientas de productividad para desarrolladores. Considérelo como un programa que se puede usar para crear programas y aplicaciones.

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Esperamos que haya aprendido un poco sobre C#, ASP.NET Core y el IDE de Visual Studio. Para más información acerca de cómo crear una aplicación web o un sitio web con C# y ASP.NET, continúe con los siguientes tutoriales:

> [!div class="nextstepaction"]
> [Creación de una aplicación web de páginas de Razor con ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Vea también

[Publicar una aplicación web en Azure App Service mediante Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
