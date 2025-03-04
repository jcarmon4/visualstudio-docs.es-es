---
title: Probar una aplicación grande con varias asignaciones de IU
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eb49e4e84f61e817e3df8bbbdd20c6922d180ee
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926739"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Probar una aplicación grande con varias asignaciones de IU

En este tema se describe cómo usar pruebas automatizadas de IU cuando esté probando una aplicación grande mediante varias asignaciones de IU.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisitos**

- Visual Studio Enterprise

Al crear una nueva prueba automatizada de IU, el marco de pruebas de Visual Studio genera de manera predeterminada código para la prueba en una clase [UIMap](/previous-versions/dd580454(v=vs.140)). Para obtener más información sobre cómo registrar pruebas automatizadas de IU, vea [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md) y [Anatomía de una prueba automatizada de IU](../test/anatomy-of-a-coded-ui-test.md).

El código generado para la asignación de IU contiene una clase para cada objeto con el que la prueba interactúa. Para cada método generado, se genera una clase complementaria específicamente para los parámetros de ese método. Si hay un número elevado de objetos, páginas y formularios y controles en la aplicación, la asignación de IU puede llegar a ser muy grande. Además, si hay varias personas trabajando en las pruebas, la aplicación se vuelve pesada con un único archivo grande de asignación de IU.

El uso de varios archivos de asignación de IU puede aportar las ventajas siguientes:

- Cada asignación se puede asociar a un subconjunto lógico de la aplicación. Esto hace que los cambios sean más fáciles de administrar.

- Cada evaluador puede trabajar en una sección de la aplicación y proteger su código sin interferir con otros evaluadores que trabajan en otras secciones de la aplicación.

- Las incorporaciones a la interfaz de usuario de la aplicación se pueden escalar incrementalmente con un efecto mínimo sobre las pruebas para otras partes de la interfaz de usuario.

## <a name="do-you-need-multiple-ui-maps"></a>¿Necesita varias asignaciones de IU?
Cree varias asignaciones de IU en cada uno de estos tipos de situaciones:

- Varios conjuntos complejos de controles de IU compuestos que realizan conjuntamente una operación lógica, como una página de registro de un sitio web o la página de compra de un carro de la compra.

- Un conjunto independiente de controles al que se tiene acceso desde varios lugares de la aplicación, como un asistente con varias páginas de operaciones. Si cada página de un asistente es especialmente compleja, podría crear asignaciones de IU diferentes para cada página.

## <a name="add-multiple-ui-maps"></a>Agregar varias asignaciones de interfaz de usuario

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Para agregar una asignación de IU al proyecto de prueba de IU codificada

1. En el **Explorador de soluciones**, para crear una carpeta en el proyecto de prueba automatizada de IU y almacenar todas las asignaciones de IU, haga clic con el botón derecho en el archivo de proyecto de prueba automatizada de IU, apunte a **Agregar** y seleccione **Nueva carpeta**. Por ejemplo, podría denominarla `UIMaps`.

    La nueva carpeta se mostrará en el proyecto de prueba de IU codificada.

2. Haga clic con el botón derecho en la carpeta `UIMaps`, apunte a **Agregar** y seleccione **Nuevo elemento**.

    Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

   > [!NOTE]
   > Para agregar una nueva asignación de prueba de IU codificada debe estar en un proyecto de prueba de IU codificada.

3. Seleccione **Asignación de pruebas automatizadas de IU** en la lista.

    En el cuadro **Nombre**, escriba un nombre para la nueva asignación de IU. Use el nombre del componente o de la página que representará la asignación (por ejemplo, `HomePageMap`).

4. Haga clic en **Agregar**.

    La ventana de Visual Studio se minimiza y aparece el cuadro de diálogo **Generador de pruebas automatizadas de IU**.

5. Registre las acciones para el primer método y seleccione **Generar código**.

6. Después de registrar todas las acciones y aserciones para el primer componente o página y de agruparlas en métodos, cierre el cuadro de diálogo **Generador de pruebas automatizadas de IU**.

7. Siga creando asignaciones de IU. Registre las acciones y aserciones, agrúpelas en métodos para cada componente y después genere el código.

   En muchos casos, la ventana de nivel superior de la aplicación permanece constante para todos los asistentes, formularios y páginas. Aunque cada asignación de IU tiene una clase para la ventana de nivel superior, probablemente todas las asignaciones estén haciendo referencia a la misma ventana de nivel superior dentro de la cual se ejecutan todos los componentes de la aplicación. Las pruebas automatizadas de IU buscan controles jerárquicamente de arriba abajo, empezando en la ventana de nivel superior, por lo que en una aplicación compleja, la ventana de nivel superior real podría estar duplicada en cada asignación de IU. Si la ventana de nivel superior real está duplicada, se realizarán varias modificaciones si esa ventana cambia. Esto podría producir problemas de rendimiento al cambiar entre asignaciones de IU.

   Para minimizar este efecto, puede usar el método `CopyFrom()` para asegurarse de que la nueva ventana de nivel superior de esa asignación de IU sea la misma que la ventana de nivel superior principal.

## <a name="example"></a>Ejemplo

El ejemplo siguiente forma parte de una clase de utilidad que permite acceder a cada componente y sus controles secundarios, que están representados por las clases generadas en las diversas asignaciones de IU.

En este ejemplo, una aplicación web denominada `Contoso` tiene una página principal, una página de productos y una página de carro de la compra. Todas estas páginas comparten una ventana de nivel superior común, que es la ventana del explorador. Hay una asignación de IU para cada página y la clase de utilidad tiene código similar al siguiente:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Vea también

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md)
- [Anatomía de una prueba automatizada de IU](../test/anatomy-of-a-coded-ui-test.md)
