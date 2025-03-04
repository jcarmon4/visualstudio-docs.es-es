---
title: Inspeccionar variables - ventanas automático y variables locales | Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60bb98644c1905b030176b28b97575b379bed38d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564585"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Inspeccionar las variables en las ventanas automático y variables locales

El **automático** y **variables locales** ventanas muestran valores de variables durante la depuración. Windows solo están disponibles durante una sesión de depuración. El **automático** ventana muestra las variables usadas en torno al punto de interrupción actual. El **variables locales** ventana muestra las variables definidas en el ámbito local, que normalmente es la función actual o el método. Si se trata de la primera vez que ha probado para depurar el código, es posible que desea leer [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de pasar a través de este artículo.

 El **automático** ventana está disponible para C#, código de Visual Basic, C++ y Python, pero no para JavaScript o F#.

Para abrir el **automático** ventana, durante la depuración, seleccione **depurar** > **Windows** > **automático**, o presione **Ctrl**+**Alt**+**V** > **A**.

Para abrir el **variables locales** ventana, durante la depuración, seleccione **depurar** > **Windows** > **variables locales**, o presione **Alt**+**4**.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. Para Visual Studio para Mac, consulte [visualizaciones de datos en Visual Studio para Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Usar las ventanas automático y variables locales

Matrices y objetos se muestran en el **automático** y **variables locales** windows como controles de árbol. Seleccione la flecha situada a la izquierda de un nombre de variable para expandir la vista para mostrar los campos y propiedades. Este es un ejemplo de un <xref:System.IO.FileStream?displayProperty=fullName> objeto en el **variables locales** ventana:

![Locals-FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")

Un valor de color rojo en el **variables locales** o **automático** ventana significa que el valor ha cambiado desde la última evaluación. El cambio podría ser una sesión de depuración anterior, o porque ha cambiado el valor en la ventana.

El formato numérico de forma predeterminada en las ventanas del depurador es decimal. Para cambiarlo en formato hexadecimal, haga clic en el **variables locales** o **automático** ventana y seleccione **presentación Hexadecimal**. Este cambio afecta a todas las ventanas del depurador.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Editar valores de variable en la ventana automático o variables locales

Para editar los valores de la mayoría de las variables en el **automático** o **variables locales** windows, haga doble clic en el valor y escriba el nuevo valor.

Puede escribir una expresión para un valor; por ejemplo, `a + b`. El depurador acepta la mayoría de las expresiones de lenguaje válidas.

En el código C++ nativo, se debe calificar el contexto de un nombre de variable. Para obtener más información, vea [Operador de contexto en el depurador de Visual Studio (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Asegúrese de que comprende las consecuencias antes de cambiar los valores y expresiones. Algunas causas posibles son:
>
>- La evaluación de algunas expresiones puede cambiar el valor de una variable o afectar de otra forma al estado del programa. Por ejemplo, evaluar `var1 = ++var2` cambia el valor de ambos `var1` y `var2`. Estas expresiones se dice que tienen [efectos](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efectos secundarios pueden producir resultados inesperados si no es consciente de ellos.
>
>- La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inofensiva puede causar cambios en alguno de los bits de la variable de punto flotante.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Buscar en la ventana automático o variables locales

Puede buscar palabras clave en las columnas Nombre, valor y tipo de la **automático** o **variables locales** ventana mediante la barra de búsqueda encima de cada ventana. Presione ENTRAR o seleccione una de las flechas para ejecutar una búsqueda. Para cancelar una búsqueda en curso, seleccione el icono "x" en la barra de búsqueda.

Utilice las flechas izquierdas y derecha (MAYÚS + F3 y F3, respectivamente) navegar entre encuentra coincidencias.

![Búsqueda en la ventana variables locales](../debugger/media/ee-search-locals.png "búsqueda en la ventana variables locales")

Para realizar la búsqueda exhaustiva de más o menos, use el **búsqueda más profunda** lista desplegable en la parte superior de la **automático** o **variables locales** ventana Seleccionar cuántos niveles de profundidad desea buscar en objetos anidados. 

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Cambiar el contexto de la ventana automático o variables locales

Puede usar el **ubicación de depuración** barra de herramientas para seleccionar una función deseada, el subproceso o proceso, que cambia el contexto para el **automático** y **variables locales** windows.

Para habilitar el **ubicación de depuración** barra de herramientas, haga clic en una parte vacía del área de barra de herramientas y seleccione **ubicación de depuración** desde la lista desplegable o seleccione **vista**  >   **Las barras de herramientas** > **ubicación de depuración**.

Establezca un punto de interrupción e inicie la depuración. Cuando se alcanza el punto de interrupción, se pausa la ejecución y se puede ver la ubicación en la **ubicación de depuración** barra de herramientas.

![Barra de herramientas ubicación de depuración](../debugger/media/debuglocationtoolbar.png "barra de herramientas ubicación de depuración")

## <a name="bkmk_whatvariables"></a> Las variables en la ventana automático (C#, C++, Visual Basic, Python)

Diferentes lenguajes de código muestran distintas variables en el **automático** ventana.

- En C# y Visual Basic, la ventana **Automático** muestra cualquier variable que se usa en la línea actual o anterior. Por ejemplo, en C# o Visual Basic de código, declare las variables de cuatro siguientes:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Establezca un punto de interrupción en la línea `c = 3;`, e iniciar el depurador. Cuando la ejecución se detiene, el **automático** mostrará la ventana:

   ![Automático-CSharp](../debugger/media/autos-csharp.png "automático-CSharp")

   El valor de `c` es 0, porque la línea `c = 3` aún no se ha ejecutado.

- En C++, el **automático** ventana muestra las variables utilizadas en al menos tres líneas anteriores a la línea actual donde se pausa la ejecución. Por ejemplo, en el código de C++, declara seis variables:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Establezca un punto de interrupción en la línea `e = 5;` y ejecute el depurador. Cuando la ejecución se detiene, el **automático** mostrará la ventana:

    ![Autos-C++](../debugger/media/autos-cplus.png "Autos-C++")

    La variable `e` no está inicializada, porque la línea `e = 5` aún no se ha ejecutado.

## <a name="bkmk_returnValue"></a> View return values of method calls
 En el código de .NET y C++, puede examinar los valores devueltos en la **automático** ventana paso a paso a través o fuera de una llamada al método. Llamada al método de visualización, se devuelven los valores pueden ser útiles cuando no se almacenan en variables locales. Un método podría utilizarse como un parámetro o como el valor devuelto de otro método.

 Por ejemplo, la siguiente C# código agrega los valores devueltos de dos funciones:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

Para ver los valores devueltos de la `sumVars()` y `subtractVars()` llama al método en la ventana automático:

1. Establezca un punto de interrupción en la línea `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Inicie la depuración y cuando la ejecución se detiene en el punto de interrupción, seleccione **saltar** o presione **F10**. Debería ver los siguientes valores devueltos en la **automático** ventana:

  ![Valor devuelven de autos C# ](../debugger/media/autosreturnvaluecsharp2.png "automático de valor devueltoC#")

## <a name="see-also"></a>Vea también

- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ventanas del depurador](../debugger/debugger-windows.md)
