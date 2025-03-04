---
title: Introducción a proyectos y soluciones
ms.date: 07/22/2019
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfa9c2871a414d5ce6be6c0b64f10b3f57ca7305
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180172"
---
# <a name="learn-about-projects-and-solutions"></a>Información sobre proyectos y soluciones

En este artículo introductorio se explica qué significa crear una *solución* y un *proyecto* en Visual Studio. Una solución es un contenedor que se usa para organizar uno o más proyectos de código relacionados, por ejemplo, un proyecto de biblioteca de clases y un proyecto de prueba correspondiente. Echaremos un vistazo a las propiedades de un proyecto y a algunos de los archivos que puede contener. También se crea una referencia de un proyecto a otro.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

Se crean una solución y un proyecto desde cero como ejercicio educativo para comprender el concepto de proyecto. Cuando use Visual Studio, es probable que emplee alguna de las distintas *plantillas* de proyecto que Visual Studio ofrece al crear un nuevo proyecto.

> [!NOTE]
> No hacen falta soluciones ni proyectos para desarrollar aplicaciones en Visual Studio. Basta con abrir una carpeta que contenga código para empezar a codificar, compilar y depurar. Por ejemplo, si clona un repositorio de [GitHub](https://github.com/), podría no contener soluciones y proyectos de Visual Studio. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Soluciones y proyectos

A pesar de su nombre, una solución no es una "respuesta", sino simplemente contenedores que Visual Studio usa para organizar uno o más proyectos relacionados. Cuando se abre una solución en Visual Studio, esta carga automáticamente todos los proyectos que la solución contiene.

### <a name="create-a-solution"></a>Crear una solución

Comenzaremos nuestro periplo creando una solución vacía. Cuando se familiarice con Visual Studio, lo más probable es que no cree soluciones vacías con mucha frecuencia. Al crear un proyecto, Visual Studio crea automáticamente una solución para hospedar ese proyecto si es que no hay ya una solución abierta.

::: moniker range="vs-2017"

1. Abra Visual Studio.

1. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

   Aparece el cuadro de diálogo **Nuevo proyecto** .

1. En el panel izquierdo, expanda **Otros tipos de proyectos** y seleccione **Soluciones de Visual Studio**. En el panel central, elija la plantilla **Solución en blanco**. Ponga el nombre **QuickSolution** a la solución y luego haga clic en el botón **Aceptar**.

   ![Plantilla Solución en blanco de Visual Studio 2017](media/tutorial-projects-new-solution.png)

   La **página de inicio** se cierra y aparece una solución en el **Explorador de soluciones**, en el lado derecho de la ventana de Visual Studio. Seguramente use el **Explorador de soluciones** a menudo para examinar el contenido de los proyectos.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. En la página **Crear un proyecto nuevo**, escriba **solución en blanco** en el cuadro de búsqueda, seleccione la plantilla **Solución en blanco** y elija **Siguiente**.

   ![Plantilla Solución en blanco de Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Asígnele a la solución el nombre **QuickSolution** y elija **Crear**.

   Aparece una solución en el **Explorador de soluciones**, en el lado derecho de la ventana de Visual Studio. Seguramente use el **Explorador de soluciones** a menudo para examinar el contenido de los proyectos.

::: moniker-end

### <a name="add-a-project"></a>Agregar un proyecto

Ahora, agreguemos nuestro primer proyecto a la solución. Comenzaremos con un proyecto vacío y le agregaremos los elementos que necesitamos.

::: moniker range="vs-2017"

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución "QuickSolution"** en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo proyecto**.

   Se abre el cuadro de diálogo **Agregar nuevo proyecto** .

1. En el panel izquierdo, expanda **Visual C#** y elija **Escritorio de Windows**. Luego, en el panel central, elija la plantilla **Proyecto vacío (.NET Framework)** . Asigne el nombre **QuickDate** al proyecto y luego seleccione **Aceptar**.

   Un proyecto denominado QuickDate aparece debajo de la solución en el **Explorador de soluciones**. Actualmente solo contiene un archivo denominado *App.config*.

   > [!NOTE]
   > Si no ve **Visual C#** en el panel izquierdo del cuadro de diálogo, debe instalar la *carga de trabajo* de **desarrollo de escritorio de .NET** de Visual Studio. Visual Studio usa la instalación basada en la carga de trabajo para instalar únicamente los componentes necesarios para el tipo de desarrollo que lleva a cabo. Una manera sencilla de instalar una nueva carga de trabajo es hacer clic en el vínculo **Abrir el instalador de Visual Studio** en la esquina inferior izquierda del cuadro de diálogo **Agregar nuevo proyecto**. Una vez que se abra el Instalador de Visual Studio, elija la carga de trabajo de **desarrollo de escritorio de .NET** y luego haga clic en el botón **Modificar**.
   >
   > ![Vínculo Abrir el instalador de Visual Studio](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución "QuickSolution"** en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo proyecto**.

   Se abre un cuadro de diálogo de nombre **Agregar un nuevo proyecto**.

1. Escriba el texto **vacío** en el cuadro de búsqueda de la parte superior y luego seleccione **C#** en **Lenguaje**.

1. Seleccione la plantilla **Proyecto vacío (.NET Framework)** y luego **Siguiente**.

1. Asigne el nombre **QuickDate** al proyecto y luego seleccione **Crear**.

   Un proyecto denominado QuickDate aparece debajo de la solución en el **Explorador de soluciones**. Actualmente solo contiene un archivo denominado *App.config*.

   > [!NOTE]
   > Si no ve la plantilla **Proyecto vacío (.NET Framework)** , tiene que instalar la *carga de trabajo* **Desarrollo de escritorio de .NET** de Visual Studio. Visual Studio usa la instalación basada en la carga de trabajo para instalar únicamente los componentes necesarios para el tipo de desarrollo que lleva a cabo. Una manera fácil de instalar una nueva carga de trabajo al crear un nuevo proyecto es seleccionar el vínculo **Instalar más herramientas y características** debajo del texto que indica **¿No encuentra lo que busca?** . Una vez que se abra el Instalador de Visual Studio, elija la carga de trabajo de **desarrollo de escritorio de .NET** y luego haga clic en el botón **Modificar**.
   >
   > ![Vínculo Abrir el instalador de Visual Studio](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Agregar un elemento al proyecto

Hay un proyecto vacío. Vamos a agregar un archivo de código.

1. En el menú contextual que aparece al hacer clic con el botón derecho en el proyecto **QuickDate** del **Explorador de soluciones**, elija **Agregar** > **Nuevo elemento**.

   Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

1. Expanda **Elementos de Visual C#** y elija **Código**. En el panel central, elija la plantilla de proyecto **Clase**. Ponga el nombre **Calendar** a la clase y luego haga clic en el botón **Agregar**.

   Un archivo denominado *Calendar.cs* se agrega al proyecto. El fragmento *.cs* del final es la extensión de archivo que tienen los archivos de código de C#. El archivo aparece en la jerarquía visual del proyecto en el **Explorador de soluciones** y su contenido se abre en el editor.

1. Reemplace el contenido del archivo *Calendar.cs* por el siguiente código:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   No es necesario comprender lo que hace el código pero, si quiere, puede ejecutar el programa al presionar **Ctrl**+**F5** y ver que imprime la fecha de hoy en la ventana de la consola (o salida estándar).

## <a name="add-a-second-project"></a>Agregar un segundo proyecto

Es común que las soluciones contengan más de un proyecto y, a menudo, estos proyectos se hacen referencia entre sí. Algunos proyectos de una solución pueden ser bibliotecas de clases; otros, aplicaciones ejecutables, y otros, proyectos de prueba unitaria o sitios web.

Vamos a agregar un proyecto de prueba unitaria a la solución. Esta vez se empieza a partir de una plantilla de proyecto, así que no es necesario agregar otro archivo de código al proyecto.

1. En el menú contextual que aparece al hacer clic con el botón derecho en **Solución "QuickSolution"** en el **Explorador de soluciones**, seleccione **Agregar** > **Nuevo proyecto**.

::: moniker range="vs-2017"

2. En el panel izquierdo, expanda **Visual C#** y elija la categoría **Prueba**. En el panel central, seleccione la plantilla de proyecto **Proyecto de prueba de MSTest (.NET Core)** . Asigne el nombre **QuickTest** al proyecto y luego seleccione **Aceptar**.

   Se agregará un segundo proyecto al **Explorador de soluciones**, mientras que un archivo denominado *UnitTest1.cs* se abre en el editor.

   ![Explorador de soluciones de Visual Studio con dos proyectos](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. En el cuadro de diálogo **Agregar un nuevo proyecto**, escriba el texto **prueba unitaria** en el cuadro de búsqueda de la parte superior y luego seleccione **C#** en **Lenguaje**.

3. Seleccione la plantilla de proyecto **Proyecto de prueba de MSTest (.NET Core)** y luego **Siguiente**.

4. Asigne el nombre **QuickTest** al proyecto y luego seleccione **Crear**.

   Se agregará un segundo proyecto al **Explorador de soluciones**, mientras que un archivo denominado *UnitTest1.cs* se abre en el editor.

   ![Explorador de soluciones de Visual Studio con dos proyectos](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Agregar una referencia de proyecto

Usaremos el nuevo proyecto de prueba unitaria para probar nuestro método en el proyecto **QuickDate**, por lo que necesitamos agregar una referencia a ese proyecto. Esto crea una *dependencia de compilación* entre ambos proyectos, lo que significa que, al compilar la solución, **QuickDate** se compila antes que **QuickTest**.

1. Seleccione el nodo **Dependencias** del proyecto **QuickTest** y, en el menú contextual que aparece al hacer clic con el botón derecho, seleccione **Agregar referencia**.

   Se abre el cuadro de diálogo **Administrador de referencias**.

1. En el panel izquierdo, expanda **Proyectos** y elija **Solución**. En el panel central, active la casilla situada junto a **QuickDate** y luego seleccione **Aceptar.

   Se agrega una referencia al proyecto **QuickDate**.

   ![Explorador de soluciones de Visual Studio 2019 que muestra la referencia del proyecto](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Agregar código de prueba

1. Ahora vamos a agregar código de prueba al archivo de código de C#. Reemplace el contenido del archivo *UnitTest1.cs* por el siguiente código:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Se ve una línea ondulada de color rojo debajo de algunas partes del código. Solucionaremos este error cuando convirtamos el proyecto de prueba en un [ensamblado de confianza](/dotnet/standard/assembly/friend-assemblies) del proyecto **QuickDate**.

1. De nuevo en el proyecto **QuickDate**, abra el archivo *Calendar.cs* si aún no está abierto. Agregue la siguiente [instrucción Using](/dotnet/csharp/language-reference/keywords/using-statement) y el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a la parte superior del archivo para resolver el error del proyecto de prueba.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   El archivo de código debe tener este aspecto:

   ![Código de CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Propiedades del proyecto

La línea del archivo *Calendar.cs* que contiene el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> hace referencia al nombre de ensamblado (nombre de archivo) del proyecto **QuickTest**. El nombre del ensamblado no siempre es el mismo que el nombre del proyecto. Para averiguar el nombre del ensamblado de un proyecto, abra las propiedades del proyecto.

1. En el **Explorador de soluciones**, seleccione el proyecto **QuickTest**. En el menú contextual que se abre al hacer clic con el botón derecho, seleccione **Propiedades** o, simplemente, presione **Alt**+**ENTRAR**.

   Las *páginas de propiedades* del proyecto se abren en la pestaña **Aplicación**. Las páginas de propiedades contienen varios valores para el proyecto. Fíjese en que el nombre de ensamblado del proyecto **QuickTest** es, efectivamente, "QuickTest". Si quisiera cambiarlo, aquí es donde lo haría. Así, al compilar el proyecto de prueba, el nombre del archivo binario resultante cambiaría de *QuickTest.dll* a lo que hubiera elegido.

   ![Propiedades del proyecto](media/tutorial-projects-netcore-properties.png)

1. Examine algunas de las demás pestañas de las páginas de propiedades del proyecto, como **Compilar** y **Depurar**. Estas pestañas son diferentes para los distintos tipos de proyectos.

## <a name="next-steps"></a>Pasos siguientes

Si quiere comprobar que la prueba unitaria funciona, seleccione **Probar** > **ejecutar** > **Todas las pruebas** desde la barra de menús. Se abre una ventana denominada **Explorador de pruebas**, donde debería ver que la prueba **TestGetCurrentDate** se supera.

![Explorador de pruebas de Visual Studio que muestra una prueba correcta](media/tutorial-projects-test-explorer.png)

> [!TIP]
> Si la ventana **Explorador de pruebas** no se abre automáticamente, ábrala al elegir **Prueba** > **Windows** > **Explorador de pruebas** en la barra de menús.

## <a name="see-also"></a>Vea también

- [Crear proyectos y soluciones](../ide/creating-solutions-and-projects.md)
- [Administración de propiedades de soluciones y proyectos](../ide/managing-project-and-solution-properties.md)
- [Administración de referencias en un proyecto](../ide/managing-references-in-a-project.md)
- [Desarrollar código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Introducción al IDE de Visual Studio](../get-started/visual-studio-ide.md)
