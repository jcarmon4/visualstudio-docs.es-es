---
title: Introducción a la edición para desarrolladores de Visual Basic
description: En esta introducción al editor de código de Visual Studio de 10 minutos de duración se describen algunas de las formas en que Visual Studio hace que escribir y comprender el código de Visual Basic (así como desplazarse por él) sea más fácil.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5ebbe6ac8ef8e6a6de99159fa8dd5169a9dcac06
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180398"
---
# <a name="learn-to-use-the-code-editor"></a>Aprender a usar el editor de código

En esta introducción de 10 minutos al editor de código, se agrega código a un archivo para ver algunas de las formas en que Visual Studio hace que escribir y comprender el código (así como desplazarse por él) sea más fácil.

::: moniker range="vs-2017"

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

En este artículo se da por hecho que ya está familiarizado con Visual Basic. Si no lo está, le aconsejamos que antes eche un vistazo a un tutorial del tipo [Introducción a Visual Basic en Visual Studio](../../get-started/visual-basic/tutorial-console.md).

> [!TIP]
> Para realizar los procedimientos de este artículo, asegúrese de que tiene la configuración de Visual Basic seleccionada en Visual Studio. Para más información sobre cómo seleccionar configuraciones del entorno de desarrollo integrado (IDE), vea [Select environment settings](visual-studio-ide.md#select-environment-settings) (Seleccionar la configuración del entorno).

## <a name="create-a-new-code-file"></a>Crear un archivo de código

Empezaremos creando un archivo y agregándole código.

::: moniker range="vs-2017"

1. Abra Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio. Presione **Esc** o haga clic en **Continuar sin código** en la ventana de inicio para abrir el entorno de desarrollo.

::: moniker-end

2. En el menú **Archivo** de la barra de menús, elija **Nuevo archivo**.

3. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija **Clase de Visual Basic** y, después, elija **Abrir**.

   Se abre un archivo nuevo en el editor con el esqueleto de una clase de Visual Basic. (Ya habrá podido observar que no es necesario crear un proyecto de Visual Studio completo para aprovechar algunas de las ventajas que ofrece el editor de código, como el resaltado de sintaxis. Lo único que se necesita es un archivo de código).

   ![Archivo de código de Visual Basic en Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Uso de fragmentos de código

Visual Studio proporciona *fragmentos de código* muy prácticos que pueden servir para generar bloques de código de uso común de forma rápida y sencilla. Existen [fragmentos de código](../../ide/code-snippets.md) disponibles para diferentes lenguajes de programación, como Visual Basic, C# y C++. Vamos a agregar el fragmento de código **Sub** de Visual Basic a nuestro archivo.

1. Coloque el cursor encima de la línea `End Class` y escriba **sub**.

   Aparece un cuadro de diálogo emergente con información sobre la palabra clave `Sub` y en el que se indica cómo insertar el fragmento de código **Sub**.

   ![IntelliSense para fragmento de código en Visual Studio](media/tutorial-intellisense-snippet.png)

1. Presione la tecla **TAB** dos veces para insertar el fragmento de código.

   El esquema del procedimiento Sub `MySub()` se agrega al archivo.

Los fragmentos de código disponibles varían según el lenguaje de programación. Para ver los fragmentos de código disponibles para Visual Basic, seleccione **Editar** > **IntelliSense** > **Insertar fragmento de código** (o presione **Ctrl**+**K**, **Ctrl**+**X**). Hay fragmentos de código de Visual Basic disponibles en las siguientes categorías:

![Lista de fragmentos de código de Visual Basic](media/tutorial-code-snippet-list.png)

Hay fragmentos de código para averiguar si existe un archivo en el equipo, para escribir en un archivo de texto, para leer un valor del Registro, para ejecutar una consulta SQL, para crear una instrucción [For Each... Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) y otras muchas tareas.

## <a name="comment-out-code"></a>Marcar código como comentario

La barra de herramientas, que es la fila de botones debajo de la barra de menús de Visual Studio, puede ayudar a mejorar la productividad mientras se codifica. Por ejemplo, puede activar o desactivar el modo de finalización de IntelliSense, aumentar o reducir una sangría o marcar como comentario código que no se quiere compilar. ([IntelliSense](../../ide/using-intellisense.md) es una ayuda de codificación que muestra una lista de métodos coincidentes, entre otras cosas). En esta sección se comenta algún código.

![Botones de barra de herramientas del editor](media/tutorial-editor-toolbar.png)

1. Pegue el siguiente código en el cuerpo del procedimiento `MySub()`.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. No usaremos la matriz `morewords`, pero puede que sí lo hagamos más adelante, así que no la eliminaremos por completo. En su lugar, lo que haremos será convertir esas líneas en comentarios. Seleccione toda la definición de `morewords` hasta la llave de cierre y, luego, seleccione el botón **Marcar como comentario las líneas seleccionadas** en la barra de herramientas. Si prefiere usar el teclado, presione **Ctrl**+**K**, **Ctrl**+**C**.

   ![Botón Marcar como comentario](media/tutorial-comment-out.png)

   El carácter de comentario de Visual Basic `'` se agrega al principio de cada línea seleccionada para marcar el código como comentario.

## <a name="collapse-code-blocks"></a>Contraer bloques de código

Puede contraer secciones de código para centrarse solo en las partes que sean de su interés. Para practicar, vamos a contraer la matriz `_words` a una línea de código. Seleccione el cuadradito gris con el signo menos que se ve en el margen de la línea `Dim _words = New String() {`. Si prefiere usar el teclado, coloque el cursor en cualquier lugar en la definición de matriz y presione **Ctrl**+**M**, **Ctrl**+**M**.

![Botón para contraer de esquematización](media/tutorial-collapse.png)

El bloque de código se contrae para mostrar únicamente la primera línea seguida de un botón de puntos suspensivos (`...`). Para expandir el bloque de código de nuevo, haga clic en el mismo cuadro gris (que ahora tiene un signo más) o presione **CTRL**+**M**, **CTRL**+**M** otra vez. Esta característica se denomina [Esquematización](../../ide/outlining.md) y es especialmente útil cuando se contraen métodos muy largos o clases enteras.

## <a name="view-symbol-definitions"></a>Ver definiciones de símbolos

Gracias al editor de Visual Studio, es muy sencillo inspeccionar la definición de un tipo, método, etc. Una forma consiste en ir al archivo que contiene la definición, por ejemplo, seleccionando **Ir a definición** en cualquier lugar donde se haga referencia al símbolo. Otra más rápida aún (y que no desplaza el enfoque del archivo en el que está trabajando) es usar [Ver la definición](../../ide/go-to-and-peek-definition.md#peek-definition). Vamos a ver la definición del tipo `String`.

1. Haga clic con el botón derecho en la palabra `String` y elija **Ver la definición** en el menú de contenido. O bien, presione **Alt**+**F12**.

   Se abrirá una ventana emergente con la definición de la clase `String`. Puede desplazarse dentro de la ventana emergente o incluso ver la definición de otro tipo desde el código inspeccionado.

   ![Ventana Ver la definición](media/tutorial-peek-definition.png)

1. Para cerrar la ventana de definición inspeccionada, seleccione el pequeño cuadro con una "x" en la esquina superior derecha de la ventana emergente.

## <a name="use-intellisense-to-complete-words"></a>Usar IntelliSense para completar palabras

[IntelliSense](../../ide/using-intellisense.md) es un recurso impagable cuando se escribe código. Así, puede mostrar información sobre los miembros disponibles de un tipo o detalles de los parámetros para las distintas sobrecargas de un método. IntelliSense puede servir también para completar una palabra después de escribir una serie de caracteres y, así, eliminar cualquier tipo de ambigüedad. Se va a agregar una línea de código para imprimir las cadenas ordenadas en la ventana de la consola, que es el lugar estándar para la salida del programa.

1. Empiece a escribir el siguiente código debajo de la variable `query`:

   ```vb
   For Each str In qu
   ```

   Verá cómo IntelliSense muestra **Información rápida** sobre el símbolo `query`.

   ![Finalización de palabras de IntelliSense en Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Presione **Tab** para insertar el resto de la palabra `query` por medio de la funcionalidad de finalización de palabras de IntelliSense.

1. Termine el bloque de código de modo que se parezca al siguiente código.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refactorizar un nombre

Nadie crea código correctamente la primera vez y una de las cosas que probablemente se tengan que cambiar es el nombre de una variable o un método. Vamos a probar la funcionalidad de [refactorización](../../ide/refactoring-in-visual-studio.md) de Visual Studio para cambiar el nombre de la variable `_words` a `words`.

1. Coloque el cursor sobre la definición de la variable `_words`, haga clic con el botón derecho y elija **Cambiar nombre** en el menú contextual.

   Se abre un cuadro de diálogo emergente **Cambiar nombre** en la parte superior derecha del editor.

1. Con la variable `_words` aún seleccionada, escriba el nombre **words**. Observe que la referencia a `words` en la consulta también cambia automáticamente de nombre. Antes de presionar **ENTRAR** o de hacer clic en **Aplicar**, active la casilla **Incluir comentarios** del cuadro emergente **Cambiar nombre**.

   ![Cambiar nombre (cuadro de diálogo)](media/tutorial-rename.png)

1. Presione **ENTRAR** o haga clic en **Aplicar**.

   Ambas instancias de `words` cambian de nombre, así como la referencia a `words` en el comentario de código.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Información sobre proyectos y soluciones](tutorial-projects-solutions.md)

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../../ide/code-snippets.md)
- [Navegación en el código](../../ide/navigating-code.md)
- [Esquematización](../../ide/outlining.md)
- [Ir a definición y Ver la definición](../../ide/go-to-and-peek-definition.md)
- [Refactorización](../../ide/refactoring-in-visual-studio.md)
- [Uso de IntelliSense](../../ide/using-intellisense.md)