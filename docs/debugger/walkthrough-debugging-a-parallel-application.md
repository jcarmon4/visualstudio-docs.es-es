---
title: Depurar una aplicación paralela | Microsoft Docs
description: Depurar con las ventanas Parallel Tasks y Parallel Stacks de Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efd3ffb81d8ef1ad69a24acc277b8f5fe10df436
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930741"
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio-c-visual-basic-c"></a>Tutorial: Depurar una aplicación paralela en Visual Studio (C#, Visual Basic, C++)

En este tutorial se muestra cómo utilizar las ventanas **Pilas paralelas** y **Tareas paralelas** para depurar una aplicación paralela. Estas ventanas ayudan a entender y comprobar el comportamiento en tiempo de ejecución del código que usa el [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) o [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime). En este tutorial se proporciona código de muestra con puntos de interrupción integrados. Una vez que el código se interrumpe, se muestra cómo utilizar las ventanas **Tareas paralelas** y **Pilas paralelas** para examinarlo.

 Se enseñan estas tareas:

- Cómo ver las pilas de llamadas de todos los subprocesos en una vista.

- Cómo ver la lista de instancias de `System.Threading.Tasks.Task` que se crean en la aplicación.

- Cómo ver las pilas de llamadas reales de las tareas en lugar de los subprocesos.

- Cómo navegar al código desde las ventanas **Tareas paralelas** y **Pilas paralelas**.

- Cómo trabajan las ventanas con la escala de tamaño mediante la agrupación, el zoom y otras características relacionadas.

## <a name="prerequisites"></a>Requisitos previos
 En este tutorial se da por supuesto que **solo mi código** está habilitado (está habilitado de forma predeterminada en las versiones más recientes de Visual Studio). En el menú **Herramientas**, haga clic en **Opciones**, expanda el nodo **Depuración**, seleccione **General** y, a continuación, seleccione **Habilitar Solo mi código (solo administrado)** . Si no configura esta característica, puede utilizar este tutorial, pero los resultados pueden diferir de las ilustraciones.

## <a name="c-sample"></a>Ejemplo de C#
 Si utiliza el ejemplo de C#, también se supone que Código externo está oculto. Para alternar si se muestra el código externo, haga clic con el botón derecho en el encabezado de tabla **Nombre** de la ventana **Pila de llamadas** y, a continuación, active o desactive **Mostrar código externo**. Si no configura esta característica, puede utilizar este tutorial, pero los resultados pueden diferir de las ilustraciones.

## <a name="c-sample"></a>Ejemplo de C++
 Si utiliza el ejemplo C++, puede omitir las referencias a Código externo de este tema. El código externo solo se aplica en el ejemplo de C#.

## <a name="illustrations"></a>Ilustraciones
 Las ilustraciones de este tema se grabaron en un equipo básico quad core que ejecuta el ejemplo de C#. Aunque puede utilizar otras configuraciones para completar este tutorial, las ilustraciones pueden diferir de lo que se muestra en su equipo.

## <a name="creating-the-sample-project"></a>Crear el proyecto de muestra
 El código de ejemplo de este tutorial es para una aplicación que no hace nada. El objetivo es entender cómo utilizar las ventanas de herramientas para depurar una aplicación paralela.

#### <a name="to-create-the-sample-project"></a>Para crear el proyecto de ejemplo

1. Abra Visual Studio y cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Tipo **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **consola** (o **c ++** ), elija **plantillas**y, a continuación:

    - Para C# o Visual Basic, elija **crear nuevo proyecto de aplicación de consola (.NET Framework)** cualquiera C# o Visual Basic. En el cuadro de diálogo que se abre, elija **Crear**.
    - Para C++, elija **crear nuevo proyecto de aplicación de consola** para C++. En el cuadro de diálogo que se abre, elija **Crear**.

    A continuación, escriba un nombre o utilice el nombre predeterminado y haga clic en **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione lo siguiente:

    - Para un C# aplicación, en **Visual C#** , elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)** .
    - Para una aplicación de Visual Basic, en **Visual Basic**, elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)** .
    - Para un C++ aplicación, en **Visual C++** , elija **Windows Desktop**,, y, a continuación, elija **aplicación de consola Windows**.

    A continuación, escriba un nombre o utilice el nombre predeterminado y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

1. Abra el archivo de código .cpp, .cs o .vb del proyecto. Elimine su contenido para crear un archivo de código vacío.

1. En el archivo de código vacío, pegue el siguiente código en el lenguaje elegido.

   [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
   [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
   [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]

1. En el menú **Archivo**, haga clic en **Guardar todo**.

1. En el menú **Compilar**, haga clic en **Recompilar solución**.

    Observe que hay cuatro llamadas a `Debugger.Break` (`DebugBreak` en el ejemplo de C++). Por tanto, no tiene que insertar puntos de interrupción; simplemente ejecutando la aplicación, el depurador se interrumpirá cuatro veces.

## <a name="using-the-parallel-stacks-window-threads-view"></a>Uso de la ventana Pilas paralelas: Vista de subprocesos
 En el menú **Depurar**, haga clic en **Iniciar depuración**. Espere a que se alcance el primer punto de interrupción.

#### <a name="to-view-the-call-stack-of-a-single-thread"></a>Para ver la pila de llamadas de un subproceso

1. En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**. Acople la ventana **Subprocesos** a la parte inferior de Visual Studio.

2. En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pila de llamadas**. Acople la ventana **Pila de llamadas** a la parte inferior de Visual Studio.

3. Haga doble clic en un subproceso en la ventana **Subprocesos** para que sea el actual. Los subprocesos actuales tienen una flecha amarilla. Al cambiar el subproceso actual, la pila de llamadas se muestra en la ventana **Pila de llamadas**.

#### <a name="to-examine-the-parallel-stacks-window"></a>Para examinar la ventana Pilas paralelas

1. En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pilas paralelas**. Asegúrese de que **Subprocesos** está seleccionado en el cuadro de la esquina superior izquierda.

     Mediante el uso de la **pilas paralelas** ventana, puede ver varias pilas de llamadas al mismo tiempo en una vista. La siguiente ilustración muestra el **pilas paralelas** ventana anterior el **pila de llamadas** ventana.

     ![Vista en la ventana Pilas paralelas de subprocesos](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")

     La pila de llamadas del subproceso principal aparece en un cuadro y las pilas de llamadas de los otros cuatro subprocesos están agrupadas en otro cuadro. Se agrupan cuatro subprocesos porque sus marcos de pila comparten los mismos contextos de método, es decir, están en los mismos métodos: `A`, `B` y `C`. Para ver los identificadores y nombres de los subprocesos que comparten el mismo cuadro, mantenga el mouse sobre el cuadro con el encabezado (**4 subprocesos**). El subproceso actual se muestra en negrita.

     ![Información sobre herramientas que muestra los nombres e identificadores de subproceso](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")

     La flecha amarilla indica el marco de pila activo del subproceso actual.

     Puede establecer cuánto detalle mostrar en los marcos de pila (**Nombres del módulo**, **Tipos de parámetros**, **Nombres de parámetros**, **Valores de parámetro**, **Números de línea** y **Desplazamientos de bytes**) haciendo clic con el botón derecho en la ventana **Pila de llamadas**.

     Un resaltado azul alrededor de un cuadro indica que el subproceso actual forma parte de ese cuadro. El subproceso actual también está indicado por el marco de pila en negrita de la información sobre herramientas. Si hace doble clic en el subproceso Main en la ventana Subprocesos, puede observar que el resaltado azul de la ventana **Pilas paralelas** se mueve de forma acorde.

     ![Subproceso principal resaltado en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Para reanudar la ejecución hasta el segundo punto de interrupción

1. Para reanudar la ejecución hasta llegar al segundo punto de interrupción, haga clic en **Continuar**, en el menú **Depurar**. La siguiente ilustración muestra el árbol de subproceso en el segundo punto de interrupción.

     ![Ventana Pilas paralelas muchas bifurcaciones](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")

     En el primer punto de interrupción, cuatro subprocesos fueron de S.A a S.B a los métodos S.C. Esa información todavía está visible en la ventana **Pilas paralelas**, pero los cuatro subprocesos han progresado más. Uno de ellos continuó a S.D y a S.E. Otro continuó hasta S.F, S.G y S.H. Los otros dos continuaron a S.I y S.J, y de allí uno fue a S.K y el otro continuó a código externo de no usuario.

     Puede desplazar el puntero del mouse sobre el encabezado del cuadro, por ejemplo, **1 subproceso** o **2 subprocesos**, para ver los identificadores de subproceso de los subprocesos. Puede desplazar el puntero del mouse sobre los marcos de pila para ver identificadores de subproceso y otros detalles del marco. El resaltado azul indica el subproceso actual y la flecha amarilla indica el marco de pila activo del subproceso actual.

     El icono de los subprocesos (interweaved líneas) indican los marcos de pila activo de los subprocesos que no. En la ventana **Pila de llamadas**, haga doble clic en S.B para intercambiar los marcos. La ventana **Pilas paralelas** indica el marco de pila del subproceso actual utilizando un icono de flecha verde y curvada.

     En la ventana **Subprocesos**, intercambie entre los subprocesos y observe que la vista en la ventana **Pilas paralelas** está actualizada.

     Puede cambiar a otro subproceso o al marco de otro subproceso, utilizando el menú contextual en la ventana **Pilas paralelas**. Por ejemplo, haga clic con el botón derecho en S.J, apunte a **Cambiar a marco** y, a continuación, haga clic en un comando.

     ![Ruta de acceso de ejecución de pilas paralelas](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")

     Haga clic con el botón derecho en S.C y apunte a **Cambiar a marco**. Uno de los comandos tiene una marca de verificación que indica el marco de pila del subproceso actual. Puede cambiar a ese marco del mismo subproceso (la flecha verde se moverá) o puede cambiar al otro subproceso (el resaltado azul también moverá). La ilustración siguiente muestra los submenús.

     ![Menú pilas con 2 opciones en C mientras actual es el J](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")

     Cuando un contexto de método está asociado solo a un marco de pila, el encabezado del cuadro muestra **1 subproceso** y puede cambiar a él haciendo doble clic. Si hace doble clic en un contexto de método que tiene más que un marco asociado, el menú se abre automáticamente. Cuando desplace el puntero del mouse sobre los contextos de método, observe el triángulo negro a la derecha. Al hacer clic en ese triángulo, también se muestra el menú contextual.

     Con aplicaciones grandes que tienen muchos subprocesos, le interesa centrarse en un subconjunto de subprocesos. La ventana **Pilas paralelas** solo puede mostrar las pilas de llamadas de los subprocesos marcados. Para marcar subprocesos, utilice el menú contextual o la primera celda de un subproceso.

     En la barra de herramientas, haga clic en el botón **Mostrar solo marcados** junto al cuadro de lista.

     ![Información sobre herramientas y la ventana pilas en paralelo](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")

     Ahora, sólo el subproceso marcado aparece en el **pilas paralelas** ventana.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Para reanudar la ejecución hasta el tercer punto de interrupción

1. Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar**, en el menú **Depurar**.

     Cuando varios subprocesos están en el mismo método pero el método no estaba al principio de la pila de llamadas, el método aparece en cuadros diferentes. Un ejemplo en el punto de interrupción actual es S.L, que tiene tres subprocesos y aparece en tres cuadros. Haga doble clic en S.L.

     ![Ruta de acceso de ejecución en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")

     Observe que S.L está en negrita en los otros dos cuadros para que pueda ver dónde más aparece. Si quiere ver qué marcos llaman a S.L y a qué marcos llama, haga clic en el botón **Alternar vista de método** en la barra de herramientas. La siguiente ilustración muestra la vista de método de la **pilas paralelas** ventana.

     ![Vista de método en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_4.png "PDW_Walkthrough_4")

     Observe cómo el diagrama se monta en el método seleccionado y lo coloca en su propio cuadro en el medio de la vista. Los destinatarios y llamadores aparecen en la parte superior e inferior. Haga clic de nuevo en el botón **Alternar vista de método** para dejar este modo.

     El menú contextual de la ventana **Pilas paralelas** también tiene los siguientes otros elementos.

    - **Presentación hexadecimal** alterna los números de la información sobre herramientas entre decimal y hexadecimal.

    - **Configuración de símbolos** abrir los cuadros de diálogo respectivos.

    - **Mostrar subprocesos en código fuente** alterna la visualización de los marcadores de subprocesos en el código fuente, que muestra la ubicación de los subprocesos en el código fuente.

    - **Mostrar código externo** muestra todos los marcos aun cuando no estén en código de usuario. Pruébelo para ver el diagrama expandirse para alojar los marcos adicionales (que pueden estar atenuados porque no tiene símbolos para ellos).

2. En la ventana **Pilas paralelas** asegúrese de que el botón **Desplazar automáticamente a marco de pila actual** de la barra de herramientas está activado.

     Si tiene diagramas grandes y pasa al punto de interrupción siguiente, tal vez le interese la vista para desplazarse de forma automática al marco de pila activo del subproceso actual, es decir, el subproceso que alcanzó primero el punto de interrupción.

3. Antes de continuar, en la ventana **Pilas paralelas**, desplácese a la izquierda y hacia abajo todo lo posible.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Para reanudar la ejecución hasta el cuarto punto de interrupción

1. Para reanudar la ejecución hasta llegar al cuarto punto de interrupción, haga clic en **Continuar** en el menú **Depurar**.

     Observe cómo la vista se desplaza automáticamente para ocupar su lugar. Alterne los subprocesos en la ventana **Subprocesos** o alterne los marcos de pila en la ventana **Pila de llamadas** y observe cómo la vista siempre se desplaza automáticamente hasta el marco correcto. Desactive la opción **Desplazar automáticamente a marco de herramienta actual** y vea la diferencia.

     La **Vista aérea** también permite ver diagramas grandes en la ventana **Pilas paralelas**. De forma predeterminada, el **vista aérea** está activado. Pero puede alternar haciendo clic en el botón situado entre las barras de desplazamiento en la esquina inferior derecha de la ventana, tal como se muestra en la siguiente ilustración.

     ![Aérea&#45;ocular vista en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")

     En la vista de pájaro, puede mover el rectángulo para hacer una rápida panorámica del diagrama.

     Otra manera de mover el diagrama en cualquier dirección es haciendo clic en un área en blanco del diagrama y arrastrando al lugar deseado.

     Para acercar y alejar, mantenga presionada la tecla CTRL mientras mueve la rueda del mouse. Alternativamente, haga clic en el botón Zoom en la barra de herramientas y utilice la herramienta Zoom.

     También puede ver las pilas en dirección descendente en lugar de ascendente haciendo clic en el menú **Herramientas**, en **Opciones**, y seleccionando o borrando la opción bajo el nodo **Depuración**.

2. Antes de continuar, en el menú **Depurar**, haga clic en **Detener depuración** para finalizar la ejecución.

## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Utilizar la ventana Tareas paralelas y la vista Tareas de la ventana Pilas paralelas
 Recomendamos completar los procedimientos anteriores antes de continuar.

#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>Para reiniciar la aplicación hasta que alcance el primer punto de interrupción

1. En el menú **Depurar**, haga clic en **Iniciar depuración** y espere hasta alcanzar el primer punto de interrupción.

2. En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**. Acople la ventana **Subprocesos** a la parte inferior de Visual Studio.

3. En el menú **Depurar**, seleccione **Ventanas** y, a continuación, haga clic en **Pila de llamadas**. Acople la ventana **Pila de llamadas** a la parte inferior de Visual Studio.

4. Haga doble clic en un subproceso de la ventana **Subprocesos** para que sea el actual. Los subprocesos actuales tienen la flecha amarilla. Al cambiar el subproceso actual, las otras ventanas se actualizan. A continuación, examinaremos las tareas.

5. En el **depurar** menú, elija **Windows**y, a continuación, haga clic en **tareas**. La siguiente ilustración muestra el **tareas** ventana.

     ![Cuatro ejecuta las tareas en la ventana tareas](../debugger/media/pdb_walkthrough_6.png "PDW_Walkthrough_6")

     Por cada tarea que se esté ejecutando, puede leer su identificador, que devuelve la propiedad del mismo nombre, el identificador y nombre del subproceso que lo ejecuta, su ubicación (desplazando el puntero del mouse para mostrar una información sobre herramientas con la pila de llamadas completa). Asimismo, en la columna **Tarea** puede ver el método que se pasó a la tarea, es decir, el punto inicial.

     Puede ordenar cualquier columna. Observe el glifo de ordenación que indica la columna y la dirección de ordenación. También puede reordenar las columnas arrastrándolas a izquierda o derecha.

     La flecha amarilla indica la tarea actual. Puede intercambiar las tareas haciendo doble clic en una tarea o utilizando el menú contextual. Al intercambiar las tareas, el subproceso subyacente pasa a ser el actual y las demás ventanas se actualizan.

     Cuando pasa manualmente de una tarea a otra, la flecha amarilla se mueve, pero una flecha blanca sigue mostrando la tarea que hizo que el depurador se interrumpiera.

#### <a name="to-resume-execution-until-the-second-breakpoint"></a>Para reanudar la ejecución hasta el segundo punto de interrupción

1. Para reanudar la ejecución hasta llegar al segundo punto de interrupción, haga clic en **Continuar**, en el menú **Depurar**.

     Anteriormente, el **estado** columna mostraba todas las tareas como activo, pero ahora dos de las tareas se bloquean. Las tareas se pueden bloquear por muchas razones diferentes. En la columna **Estado**, desplace el puntero del mouse sobre una tarea en espera para saber por qué está bloqueada. Por ejemplo, en la siguiente ilustración, la tarea 3 está esperando a la tarea 4.

     ![Dos tareas en espera en la ventana tareas](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")

     La tarea 4, a su vez, está esperando a un monitor que pertenece al subproceso asignado a la tarea 2. (Haga clic en la fila de encabezado y elija **columnas** > **asignación de subproceso** para ver el valor de asignación de subproceso de tarea 2).

     ![Tarea en espera e información sobre herramientas en la ventana tareas](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")

     Puede marcar una tarea haciendo clic en la marca de la primera columna de la **tareas** ventana.

     Puede usar las marcas para realizar el seguimiento de las tareas entre los puntos de interrupción diferentes en la misma sesión de depuración o filtrar por las tareas cuyas pilas de llamadas se muestren en la ventana **Pilas paralelas**.

     Cuando usó la ventana **Pilas paralelas** anteriormente, vio los subprocesos de la aplicación. Mire la ventana **Pilas paralelas** de nuevo, pero esta vez observe las tareas de la aplicación. Haga esto seleccionando **Tareas** en el cuadro de la izquierda superior. En la siguiente ilustración se muestra la vista Tareas.

     ![Vista en la ventana Pilas paralelas tareas](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")

     Los subprocesos que no están ejecutando tareas actualmente no se muestran en la opción Vista de tareas de la ventana **Pilas paralelas**. Asimismo, con los subprocesos que ejecutan tareas, algunos de los marcos de pila que no son pertinentes para las tareas se filtran de la parte superior e inferior de la pila.

     Ver el **tareas** ventana de nuevo. Haga clic con el botón secundario en cualquier encabezado de columna para ver un menú contextual de la columna.

     Puede utilizar el menú contextual para agregar o quitar las columnas. Por ejemplo, la columna AppDomain no está seleccionada; por consiguiente, no se muestra en la lista. Haga clic en **Primario**. La columna **Primario** aparece sin valores para las cuatro tareas.

#### <a name="to-resume-execution-until-the-third-breakpoint"></a>Para reanudar la ejecución hasta el tercer punto de interrupción

1. Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar**, en el menú **Depurar**.

     Ahora se está ejecutando una nueva tarea, la tarea 5, y la tarea 4 está en espera. Puede ver por qué desplazando el puntero del mouse sobre la tarea en espera de la ventana **Estado**. En el **primario** columna, observe que tarea 4 es el elemento primario de la tarea 5.

     Para visualizar mejor la relación de elementos primarios y secundarios, haga clic en la fila de encabezado de columna y, a continuación, haga clic en **vista de elemento primario**. Vea la ilustración siguiente:

     ![Elemento primario&#45;vista secundaria en la ventana tareas](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")

     Observe que tarea 4 y 5 están ejecutando en el mismo subproceso (mostrar la **asignación de subproceso** columna si está oculto). Esta información no se muestra en el **subprocesos** ventana; poder verlo aquí es otra ventaja de la **tareas** ventana. Para confirmar esto, vea la ventana **Pilas paralelas**. Asegúrese de que está viendo **Tareas**. Busque las tareas 4 y 5 haciendo doble clic en ellos en el **tareas** ventana. Al hacerlo, se actualiza el resaltado azul de la ventana **Pilas paralelas**. También puede buscar las tareas 4 y 5 examinando la información sobre herramientas en la ventana **Pilas paralelas**.

     ![Vista en la ventana Pilas paralelas de tareas](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")

     En la ventana **Pilas paralelas**, haga clic con el botón derecho en S.P y, a continuación, en **Ir al subproceso**. La ventana cambia a la vista de subprocesos y el marco correspondiente está a la vista. Puede ver ambas tareas en el mismo subproceso.

     ![Resalta el subproceso en la vista de subprocesos](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")

     Esta es otra ventaja de la vista de tareas de la ventana **Pilas paralelas**, comparada con la ventana **Subprocesos**.

#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>Para reanudar la ejecución hasta el cuarto punto de interrupción

1. Para reanudar la ejecución hasta llegar al tercer punto de interrupción, haga clic en **Continuar**, en el menú **Depurar**. Haga clic en el encabezado de columna **Id.** para ordenar por identificador. Vea la ilustración siguiente:

     ![Cuatro estados de tarea en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")

     Como la tarea 5 se ha completado, ya no se muestra. Si no es el caso en su equipo y no se muestra el interbloqueo, avance un paso presionando **F11**.

     Tareas 3 y 4 se están esperando mutuamente y están bloqueados. Hay también 5 nuevas tareas que son elementos secundarios de la tarea 2 y se programan ahora. Las tareas programadas son tareas que se han iniciado en código pero no se han ejecutado todavía. Por consiguiente, las columnas **Ubicación** y **Asignación de subproceso** están vacías.

     Vea la ventana **Pilas paralelas** de nuevo. El encabezado de cada cuadro tiene una información sobre herramientas que muestra los identificadores y los nombres de los subprocesos. Cambie a la vista de tareas en la ventana **Pilas paralelas**. Desplace el puntero del mouse sobre un encabezado para ver el identificador, el nombre y el estado de la tarea, como se muestra en la siguiente ilustración.

     ![Información sobre herramientas de encabezado en la ventana Pilas paralelas](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")

     Puede agrupar las tareas por columna. En el **tareas** ventana, haga clic en el **estado** encabezado de columna y, a continuación, haga clic en **Agrupar por estado**. La siguiente ilustración muestra el **tareas** ventana agrupados por estado.

     ![Tareas en la ventana tareas agrupadas](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")

     También puede agrupar por cualquier otra columna. Agrupando las tareas, se puede concentrar en un subconjunto de tareas. Cada grupo contraíble tiene un recuento de los elementos que están agrupados.

     La última característica de la **tareas** ventana Examinar es el menú contextual que aparece cuando hace clic en una tarea.

     El menú contextual muestra comandos diferentes, dependiendo del estado de la tarea. Los comandos pueden incluir **Copiar**, **Seleccionar todo**, **Presentación hexadecimal**, **Cambiar a tarea**, **Inmovilizar subproceso asignado**, **Inmovilizar todos los subprocesos excepto esto**, **Reanudar subproceso asignado** y **Marcar**.

     Puede inmovilizar el subproceso subyacente de una o varias tareas, y puede inmovilizar todos los subprocesos exceptuando el asignado. Un subproceso inmovilizado se representa en el **tareas** ventana tal y como está en el **subprocesos** ventana por un azul *pausar* icono.

## <a name="summary"></a>Resumen
 En este tutorial se han mostrado las ventanas del depurador **Tareas paralelas** y **Pilas paralelas**. Utilice estas ventanas en los proyectos reales que utilizan código multithreading. Puede examinar código paralelo escrito en C++, C# o Visual Basic.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones multiproceso](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Programación en paralelo](/dotnet/standard/parallel-programming/index)
- [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime)
- [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md)
- [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)