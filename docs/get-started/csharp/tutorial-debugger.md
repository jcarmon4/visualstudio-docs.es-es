---
title: 'Tutorial: Depurar código de C#'
description: Obtenga información sobre cómo iniciar al depurador de Visual Studio, examinar el código e inspeccionar los datos.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98238aeee0662f61e8edc3b1f155dafd09e2301a
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180453"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Tutorial: Información sobre cómo depurar código de C# con Visual Studio

En este artículo se describen las características del depurador de Visual Studio en un tutorial paso a paso. Si quiere ahondar en las características del depurador, vea [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md). Normalmente, *depurar una aplicación* significa ejecutar la aplicación con el depurador activado. Al hacerlo, el depurador ofrece muchas formas de ver lo que hace el código durante la ejecución. Esto permite revisar el código y fijarse en los valores almacenados en variables, establecer inspecciones en ellas para ver cuándo cambian los valores, examinar la ruta de ejecución del código, ver si una rama de código está en funcionamiento, etc. Si esta es la primera vez que intenta depurar código, le recomendamos que lea [Depuración para principiantes sin experiencia](../../debugger/debugging-absolute-beginners.md) antes de continuar con este artículo.

Aunque la aplicación de demostración está en C#, la mayoría de las características son aplicables a C++, Visual Basic, F#, Python, JavaScript y otros lenguajes compatibles con Visual Studio (F# no admite Editar y continuar, mientras que F# y JavaScript no admiten la ventana **Automático**). Las capturas de pantalla son de código C#.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar el depurador y llegar a puntos de interrupción
> * Conocer los comandos para analizar el código en el depurador
> * Inspeccionar variables en la información sobre datos y las ventanas del depurador
> * Examinar la pila de llamadas

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"

Debe tener instalados Visual Studio 2019 y la carga de trabajo **Desarrollo de escritorio de .NET**.

::: moniker-end
::: moniker range="vs-2017"

Debe tener instalados Visual Studio 2017 y la carga de trabajo **Desarrollo de escritorio de .NET**.

::: moniker-end

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y, luego, seleccione **Modificar**.

## <a name="create-a-project"></a>Crear un proyecto

1. Abra Visual Studio.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **consola**, elija **Plantillas** y luego, **Create new Console App (.NET Framework) project** (Crear proyecto de aplicación de consola [.NET Framework]). En el cuadro de diálogo que se abre, escriba un nombre como **get-started-debugging** y luego elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#** , elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola (.NET Framework)** . Luego, escriba un nombre como **get-started-debugging** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola (.NET Framework)** , vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y, luego, seleccione **Modificar**.

    Visual Studio crea el proyecto.

1. En *Program.cs*, reemplace el código siguiente

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    con este código:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }

        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Inicio del depurador

1. Presione **F5** (**Depurar > Iniciar depuración**) o el botón **Iniciar depuración** ![Iniciar depuración](../../debugger/media/dbg-tour-start-debugging.png "Start Debugging") en la barra de herramientas de depuración.

     Al pulsar **F5**, la aplicación se inicia con el depurador activado para analizar los procesos. Como de momento no hemos hecho nada especial para examinar el código, la aplicación solo se carga y se muestra la salida de la consola.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     En este tutorial, analizaremos con más profundidad el uso de esta aplicación junto con el depurador y veremos las características del depurador.

2. Para detener el depurador, presione el botón de detención rojo ![Detener depuración](../../debugger/media/dbg-tour-stop-debugging.png "Stop Debugging").

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

1. En el bucle `foreach` de la función `Main`, establezca un punto de interrupción haciendo clic en el margen izquierdo de la línea de código siguiente:

    `shape.Draw()`

    En el lugar en el que establezca el punto de interrupción aparecerá un círculo rojo.

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código.

2. Presione **F5** o el botón **Iniciar depuración** ![Iniciar depuración](../../debugger/media/dbg-tour-start-debugging.png "Iniciar depuración"). La aplicación se iniciará y el depurador se ejecutará en la línea de código en la que haya establecido el punto de interrupción.

    ![Establecimiento y uso de los puntos de interrupción](../csharp/media/get-started-set-breakpoint.gif)

    La flecha amarilla representa la instrucción en la que el depurador se ha puesto en pausa, lo cual también suspende la ejecución de la aplicación en el mismo punto (esta instrucción todavía no se ha ejecutado).

     Si la aplicación todavía no se está ejecutando, **F5** permite iniciar el depurador, que se detendrá en el primer punto de interrupción. En caso contrario, **F5** permite continuar ejecutando la aplicación hasta el siguiente punto de interrupción.

    Los puntos de interrupción son una característica muy útil en los casos en los que conocemos la línea o la sección de código que queremos examinar con detalle.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navegación por el código en el depurador mediante comandos de varios pasos

Normalmente, aquí usamos métodos abreviados de teclado porque son una buena forma de ejecutar rápidamente la aplicación en el depurador, pero los comandos equivalentes, como los comandos de menú, se muestran entre paréntesis.

1. Mientras esté en pausa en la llamada de método `shape.Draw` en el método `Main`, presione **F11**, o bien elija **Depurar > Depurar paso a paso por instrucciones**, para avanzar en el código de la clase `Rectangle`.

     ![Uso de F11 para depurar código paso a paso por instrucciones](../csharp/media/get-started-f11.png "Depurar paso a paso por instrucciones con F11")

     F11 es el comando **Depurar paso a paso por instrucciones** y permite avanzar la ejecución de la aplicación de instrucción en instrucción. F11 es una buena forma de examinar el flujo de ejecución con más detalle. Más adelante le mostraremos otras opciones para moverse más rápido por el código. De forma predeterminada, el depurador omite el código que no es de usuario (si quiere más detalles, vea [Solo mi código](../../debugger/just-my-code.md)).

2. Presione varias veces **F10**, o bien elija **Depurar > Depurar paso a paso por procedimientos**, hasta que el depurador se detenga en la llamada de método `base.Draw` y, después, vuelva a presionar **F10**.

     ![Uso de F10 para saltar código](../csharp/media/get-started-step-over.png "Saltar con F10")

     En este caso, tenga en cuenta que el depurador no depura el método `Draw` de la clase base (`Shape`) paso a paso por instrucciones. **F10** hace avanzar el depurador sin depurar las funciones o los métodos en el código de la aplicación paso a paso por instrucciones (el código todavía se ejecuta). Al presionar **F10** en la llamada de método `base.Draw` (en vez de **F11**), se omite el código de implementación de `base.Draw` (algo que quizás no nos interese en este momento).

## <a name="navigate-code-using-run-to-click"></a>Navegación por el código con Ejecutar hasta clic

1. En el editor de código, desplácese hacia abajo y mantenga el puntero sobre el método `Console.WriteLine` de la clase `Triangle` hasta que aparezca el botón verde **Ejecutar hasta clic** ![Ejecutar hasta clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") a la izquierda. La información sobre herramientas del botón muestra "Ejecutar hasta aquí".

     ![Uso de la característica Ejecutar hasta clic](../csharp/media/get-started-run-to-click.png "Ejecutar hasta clic")

   > [!NOTE]
   > El botón **Ejecutar hasta clic** es una novedad de [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Si no ve el botón con la flecha verde, use **F11** en este ejemplo para hacer avanzar el depurador hasta el lugar correcto.

2. Haga clic en el botón **Ejecutar hasta clic** ![Ejecutar hasta clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Usar este botón es similar a establecer un punto de interrupción temporal. La característica **Ejecutar hasta clic** es útil para desplazarse rápidamente por un área visible del código de la aplicación (puede hacer clic en cualquier archivo abierto).

    El depurador avanzará hasta la implementación del método `Console.WriteLine` de la clase `Triangle`.

    Imagine que, mientras está en pausa, detecta una falta de ortografía. O que el texto "Drawing a trangle" está mal escrito. Pues lo podemos corregir aquí directamente mientras la aplicación se ejecuta en el depurador.

## <a name="edit-code-and-continue-debugging"></a>Editar código y seguir depurando

1. Haga clic en "Drawing a trangle" y corrija el texto: cambie "trangle" por "triangle".

1. Presione **F11** una vez y el depurador avanzará de nuevo.

    > [!NOTE]
    > En función del tipo de código que edite en el depurador, puede ser que vea un mensaje de advertencia. En algunos escenarios, el código tendrá que volver a compilarse para que pueda continuar.

## <a name="step-out"></a>Salida de la depuración

Supongamos que ha terminado de examinar el método `Draw` de la clase `Triangle` y quiere salir de la función, pero permanecer en el depurador. Puede hacerlo con el comando **Salir de la depuración**.

1. Presione **Mayús** + **F11** (o **Depurar > Salir de la depuración**).

     Este comando reanuda la ejecución de la aplicación (y hace avanzar el depurador) hasta que se devuelve la función actual.

     Debería volver a estar en el bucle `foreach` del método `Main`.

## <a name="restart-your-app-quickly"></a>Reiniciar la aplicación rápidamente

Haga clic en el botón **Reiniciar** ![Reiniciar aplicación](../../debugger/media/dbg-tour-restart.png "RestartApp") de la barra de herramientas de depuración (**Ctrl** + **Mayús**  +  **F5**).

El botón **Reiniciar** permite ahorrar tiempo, ya que hace que no sea necesario detener la aplicación y reiniciar el depurador. El depurador se detiene en el primer punto de interrupción que se alcanza al ejecutar el código.

El depurador se detendrá de nuevo en el punto de interrupción que haya establecido en el método `shape.Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Inspeccionar variables con información sobre datos

Las características que le permiten inspeccionar las variables son una de las más útiles del depurador y ofrecen diferentes formas de hacerlo. A menudo, para depurar un problema, debe intentar averiguar si las variables están almacenando los valores que espera que tengan en un momento determinado.

1. Mientras esté en pausa en el método `shape.Draw()`, mantenga el puntero sobre el objeto `shape` y verá su valor de propiedad predeterminado, la propiedad `Rectangle`.

1. Expanda el objeto `shape` para consultar las propiedades, como `Height`, que tiene un valor de 0.

1. Presione varias veces **F10**, o bien elija **Depurar** > **Depurar paso a paso por procedimientos**, para recorrer en iteración el bucle `foreach` una vez y pausarlo en `shape.Draw()`.

1. Vuelva a mantener el mouse sobre el objeto de forma y esta vez verá que tiene un objeto nuevo con un tipo `Triangle`.

     ![Ver información sobre datos](../csharp/media/get-started-data-tip.gif "View a Data Tip")

    A menudo, al realizar una depuración, queremos una forma rápida de comprobar los valores de las propiedades de las variables para ver si se almacenan los valores correspondientes, y las sugerencias de datos son una buena forma de verlo.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Inspeccionar variables con las ventanas Automático y Variables locales

1. Vea la ventana **Automático**, en la parte inferior del editor de código.

    Si está cerrada, ábrala mientras está en pausa en el depurador seleccionando **Depurar** > **Ventanas** > **Automático**.

1. Expanda el objeto `shapes`.

     ![Inspección de las variables en la ventana Automático](../csharp/media/get-started-autos-window.png "Ventana Automático")

    En la ventana **Automático** puede ver las variables y su valor actual. En la ventana **Automático** se muestran todas las variables que se usan en la línea actual o en la anterior. Para consultar el comportamiento específico de los lenguajes, vea la documentación.

1. A continuación, examine la ventana **Variables locales** en una pestaña situada junto a la ventana **Automático**.

    En la ventana **Variables locales** se muestran las variables que se encuentran en el [ámbito](https://www.wikipedia.org/wiki/Scope_(computer_science)) actual, es decir, en el contexto de ejecución actual.

## <a name="set-a-watch"></a>Establecer una inspección

1. En la ventana del editor de código principal, haga clic en el objeto `shapes` y elija **Agregar inspección**.

    En la parte inferior del editor de código se abre la ventana **Inspección**. Puede usar una ventana **Inspección** para especificar una variable (o una expresión) que quiera supervisar.

    Habrá establecido una inspección en el objeto `shapes` y podrá ver cómo cambia su valor conforme avance en el depurador. A diferencia de las otras ventanas de variables, en la ventana **Inspección** siempre se muestran las variables que está viendo (y se atenúan cuando están fuera del ámbito).

## <a name="examine-the-call-stack"></a>Examinar la pila de llamadas

1. Mientras esté en pausa en el bucle `foreach`, haga clic en la ventana **Pila de llamadas**, que se abrirá de forma predeterminada en el panel inferior derecho.

    Si está cerrada, ábrala mientras está en pausa en el depurador seleccionando **Depurar** > **Ventanas** > **Pila de llamadas**.

2. Presione **F11** varias veces hasta que vea que el depurador se detenga en el método `Base.Draw` para la clase `Triangle` en el editor de código. Eche un vistazo a la ventana **Pila de llamadas**.

    ![Examinar la pila de llamadas](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    En la ventana **Pila de llamadas** se muestra el orden en el que se llama a los métodos y las funciones. En la línea superior se muestra la función actual (el método `Triangle.Draw` en esta aplicación). En la segunda línea se mostrará que se ha llamado a `Triangle.Draw` desde el método `Main`, y así sucesivamente.

   > [!NOTE]
   > La ventana **Pila de llamadas** es similar a la perspectiva de depuración de algunos IDE, como Eclipse.

    La pila de llamadas es una buena forma de examinar y entender el flujo de ejecución de una aplicación.

    Puede hacer doble clic en una línea de código para ver ese código fuente. De este modo, también puede cambiar el ámbito que el depurador va a inspeccionar. Esta acción no hace avanzar el depurador.

    También puede usar los menús contextuales de la ventana **Pila de llamadas** para hacer otras cosas. Por ejemplo, puede insertar puntos de interrupción en funciones especificadas, avanzar el depurador mediante **Ejecutar hasta el cursor** y examinar el código fuente. Para obtener más información, vea [Cómo: Examinar la pila de llamadas](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Cambio del flujo de ejecución

1. Con el depurador en pausa en la llamada del método `Circle.Draw`, use el mouse para capturar la flecha amarilla (el puntero de ejecución) a la izquierda y moverla una línea hacia arriba hasta la llamada de método `Console.WriteLine`.

1. Presione **F11**.

    El depurador volverá a ejecutar el método `Console.WriteLine`, lo cual se puede consultar en la salida de la ventana de la consola.

    Al cambiar el flujo de ejecución, puede, por ejemplo, comprobar las diferentes rutas de ejecución de código o volver a ejecutar código sin tener que reiniciar el depurador.

    > [!WARNING]
    > A menudo es necesario tener cuidado con esta característica, ya que puede ser que vea una advertencia en la información en pantalla. También puede ser que reciba otras advertencias. El hecho de mover el puntero no permite revertir la aplicación a un estado anterior.

1. Presione **F5** para seguir ejecutando la aplicación.

    Enhorabuena por completar este tutorial.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a iniciar el depurador, a ejecutar el código paso a paso y a inspeccionar variables. Puede ser que le interese analizar las características del depurador con más detenimiento, así como consultar los vínculos disponibles con más información.

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../../debugger/debugger-feature-tour.md)
