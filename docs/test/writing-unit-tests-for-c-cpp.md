---
title: Escritura de pruebas unitarias para C/C++
description: Escriba pruebas unitarias de C++ en Visual Studio usando varios marcos de trabajo de prueba, como CTest, Boost.Test y Google Test.
ms.date: 05/06/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 6c236a8454c9710bedbf080f4d7a09cfff6a7fac
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160178"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Escribir pruebas unitarias para C/C++ en Visual Studio

Igual que con otros lenguajes, puede escribir y ejecutar pruebas unitarias de C++ en la ventana **Explorador de pruebas**. Para más información sobre cómo usar el **Explorador de pruebas**, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> C++ no admite algunas características, como Live Unit Testing, las pruebas de IU codificadas e IntelliTest.

Visual Studio incluye estos marcos de pruebas de C++ sin que sea preciso descargar nada más:

- Marco de pruebas unitarias de Microsoft para C++
- Google Test
- Boost.Test
- CTest

Además de los marcos instalados, puede escribir su propio adaptador de prueba para cualquier marco de trabajo que quiera usar en Visual Studio. Un adaptador de prueba puede integrar pruebas unitarias con la ventana **Explorador de pruebas**. En [Visual Studio Marketplace](https://marketplace.visualstudio.com) hay disponibles varios adaptadores de terceros. Para más información, vea [Instalar marcos de prueba unitaria de terceros](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 y versiones posteriores (Professional y Enterprise)**

Los proyectos de prueba unitaria de C++ admiten [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 y versiones posteriores (todas las ediciones)**

- **Google Test** se incluye como un componente predeterminado de la carga de trabajo de **Desarrollo para el escritorio con C++** . Tiene una plantilla de proyecto que se puede agregar a una solución mediante el menú contextual **Agregar nuevo proyecto** del nodo de solución en el **Explorador de soluciones**, así como opciones que se pueden configurar mediante **Herramientas** > **Opciones**. Para obtener más información, vea [Cómo: Utilizar Google Test en Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** se incluye como un componente predeterminado de la carga de trabajo de **Desarrollo para el escritorio con C++** . Se integra con el **Explorador de pruebas**, pero actualmente no tiene plantilla de proyecto, por lo que se debe configurar manualmente. Para obtener más información, vea [Cómo: Utilizar Boost.Test en Visual Studio](how-to-use-boost-test-for-cpp.md).

- La compatibilidad con **CTest** se incluye con el componente **Herramientas de CMake en C++** , que forma parte de la carga de trabajo de **Desarrollo para el escritorio con C++** . Con todo, CTest aún no está totalmente integrado con el **Explorador de pruebas**. Para obtener más información, vea [Cómo: Utilizar CTest en Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 y anterior**

Puede descargar las extensiones de los adaptadores Google Test y Boost.Test en Visual Studio Marketplace, en las páginas de [Test Adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) y [Test Adapter para Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Flujo de trabajo de prueba básico

En las siguientes secciones se explican los pasos básicos que sirven para empezar a realizar pruebas unitarias de C++. La configuración básica es muy similar en los marcos de Microsoft y Google Test. Boost.Test, por su parte, requiere que se cree un proyecto de prueba manualmente.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Creación de un proyecto de prueba en Visual Studio 2019

Hay que definir y ejecutar pruebas en uno o varios proyectos de prueba que estén en la misma solución que el código que quiere probar. Para agregar un nuevo proyecto de prueba a una solución existente, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**. Establezca el valor de **Lenguaje** en C++ y escriba "prueba" en el cuadro de búsqueda. En la siguiente ilustración se muestran los proyectos de prueba que hay disponibles cuando se instala la carga de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo para UWP**:

![Proyectos de prueba de C++ en Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Creación de un proyecto de prueba en Visual Studio 2017

Hay que definir y ejecutar pruebas en uno o varios proyectos de prueba que estén en la misma solución que el código que quiere probar. Para agregar un nuevo proyecto de prueba a una solución existente, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Agregar** > **Nuevo proyecto**. Después, en el panel izquierdo, elija **Prueba de Visual C++** y elija uno de los tipos de proyecto en el panel central. En la siguiente ilustración se muestran los proyectos de prueba que hay disponibles cuando se instala la carga de trabajo de **desarrollo para el escritorio con C++** :

![Proyectos de prueba de C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Crear referencias a otros proyectos en la solución

Para permitir que el código de prueba tenga acceso a las funciones en el proyecto que se va a probar, agregue una referencia al proyecto en el proyecto de prueba. Haga clic con el botón derecho en el nodo de proyecto de prueba en el **Explorador de soluciones** y elija **Agregar** > **Referencia**. Luego, en el cuadro de diálogo, seleccione los proyectos que quiera probar.

![Agregar referencia](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Vinculación con archivos de objeto o biblioteca

Si el código de prueba no exporta las funciones que quiere probar, puede agregar el archivo de salida .obj o .lib a las dependencias del proyecto de prueba. Vea [Para vincular las pruebas a los archivos de biblioteca u objeto](https://docs.microsoft.com/visualstudio/test/unit-testing-existing-cpp-applications-with-test-explorer?view=vs-2015#objectRef).

### <a name="add-include-directives-for-header-files"></a>Agregar directivas #include de archivos de encabezado

Después, en el archivo *.cpp* de prueba unitaria, agregue una directiva `#include` relativa a cualquier archivo de encabezado que declare los tipos y funciones que quiera probar. Escriba `#include "` y, de este modo, IntelliSense se activará para ayudarle a elegir. Repita esto mismo con los encabezados que haya.

![Agregar directivas include](media/cpp-add-includes-test-project.png)

### <a name="write-test-methods"></a>Escribir métodos de prueba

> [!NOTE]
> En esta sección se muestra la sintaxis del marco de pruebas unitarias de Microsoft para C y C++. Se documenta aquí: [Referencia de API Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Para obtener documentación sobre Google Test, vea [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Para Boost.Test, vea [Boost Test library: The unit test framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Biblioteca de Boost.Test: el marco de pruebas unitarias).

El archivo *.cpp* del proyecto de prueba tiene un método y una clase de código auxiliar definidos automáticamente para que pueda ver un ejemplo de cómo escribir código de prueba. Observe que las firmas usan las macros TEST_CLASS y TEST_METHOD, lo que hace que los métodos se puedan detectar desde la ventana **Explorador de pruebas**.

![Agregar directivas include](media/cpp-write-test-methods.png)

TEST_CLASS y TEST_METHOD forman parte del [Marco de pruebas nativo de Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). El **Explorador de pruebas** detecta métodos de prueba en otros marcos admitidos de forma similar.

Un método TEST_METHOD no devuelve ningún valor. Para obtener un resultado de prueba, use los métodos estáticos de la clase `Assert` para probar resultados reales con lo que se espera. En el siguiente ejemplo, se da por hecho que `MyClass` tiene un constructor que toma una cadena `std::string`. Podemos probar que el constructor inicializa la clase según lo previsto de este modo:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

En el ejemplo anterior, el resultado de la llamada `Assert::AreEqual` determina si la prueba se supera o no. La clase Assert contiene otros muchos métodos para comparar los resultados previstos con los reales.

Puede agregar *rasgos* para probar métodos para especificar los propietarios de la prueba, la prioridad y otro tipo de información. Así, podrá usar esos valores para ordenar y agrupar las pruebas en el **Explorador de pruebas**. Para obtener más información, consulte [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Ejecutar las pruebas

1. En el menú **Prueba**, elija **Windows** > **Explorador de pruebas**. En la siguiente ilustración se muestra un proyecto de prueba cuyas pruebas aún no se han ejecutado.

   ![Explorador de pruebas antes de ejecutar las pruebas](media/cpp-test-explorer.png)

   > [!NOTE]
   > La integración de CTest con el **Explorador de pruebas** aún no está disponible. Realice pruebas de CTest desde el menú principal de CMake.

1. Si ninguna de las pruebas está visible en la ventana, compile el proyecto de prueba haciendo clic con el botón derecho en el nodo correspondiente en el **Explorador de soluciones** y eligiendo **Compilar** o **Recompilar**.

1. En el **Explorador de pruebas**, elija **Ejecutar todas** o seleccione las pruebas concretas que quiera ejecutar. Haga clic con el botón derecho en una prueba para ver otras opciones, como la ejecución en modo de depuración con puntos de interrupción habilitados. Después de ejecutar todas las pruebas, la ventana muestra cuáles se han superado y cuáles no:

![Explorador de pruebas después de ejecutar las pruebas](media/cpp-test-explorer-passed.png)

En las pruebas no superadas, el mensaje ofrece detalles que ayudan a diagnosticar la causa. Puede hacer clic con el botón derecho en la prueba no superada y elegir **Depurar pruebas seleccionadas** para ir paso a paso por la función donde se ha producido el error.

Para más información sobre cómo usar el **Explorador de pruebas**, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](run-unit-tests-with-test-explorer.md).

Para ver procedimientos recomendados relativos a las pruebas unitarias, vea [Conceptos básicos de prueba unitaria](unit-test-basics.md).

## <a name="use-codelens"></a>Uso de CodeLens

**Visual Studio 2017 y versiones posteriores (ediciones Professional y Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) permite ver rápidamente el estado de una prueba unitaria sin salir del editor de código. Puede inicializar CodeLens para un proyecto de prueba unitaria de C++ de cualquiera de las siguientes maneras:

- Editar y compilar el proyecto de prueba o la solución.
- Recompilar el proyecto o la solución.
- Ejecutar pruebas desde la ventana **Explorador de pruebas**.

Después de que **CodeLens** se inicialice, puede ver los iconos de estado de prueba encima de cada prueba unitaria.

![Iconos de CodeLens en C++](media/cpp-test-codelens-icons.png)

Haga clic en el icono para más información o para ejecutar o depurar la prueba unitaria:

![Ejecución y depuración de CodeLens en C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](unit-test-your-code.md)
