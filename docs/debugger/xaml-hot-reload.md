---
title: Escribir y depurar XAML mediante la recarga activa de XAML
description: La recarga activa de XAML, o editar y continuar de XAML, permite realizar cambios en el código XAML mientras se ejecutan las aplicaciones.
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0acacac883153990861385c96eeb3379c464f97f
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871000"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escribir y depurar código XAML en ejecución con la recarga activa de XAML en Visual Studio

La recarga activa de XAML le ayuda a compilar la interfaz de usuario (UI) de la aplicación para UWP o de UWP permitiéndole realizar cambios en el código XAML mientras se ejecuta la aplicación. La recarga activa está disponible en Visual Studio y Blend para Visual Studio. Esta característica le permite compilar y probar incrementalmente el código XAML con la ventaja de que el contexto de datos de la aplicación en ejecución, el estado de autenticación y otras complejidades del mundo real son difíciles de simular durante el tiempo de diseño.

La recarga activa de XAML es especialmente útil en estos escenarios:

* Corrección de los problemas de la interfaz de usuario encontrados en el código XAML después de que la aplicación se iniciara en modo de depuración.

* Compilar un nuevo componente de interfaz de usuario para una aplicación que está en desarrollo, mientras se aprovecha el contexto de tiempo de ejecución de la aplicación.

|Tipos de aplicación admitidos|Sistema operativo y herramientas|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 y versiones posteriores |
|Aplicaciones universales de Windows (UWP)|Windows 10 y versiones posteriores, con el [SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> La recarga activa de XAML de Visual Studio solo se admite actualmente cuando se ejecuta la aplicación en Visual Studio o Blend para Visual Studio con el depurador adjunto (**F5** o **iniciar**depuración). No puede habilitar esta experiencia mediante [asociar al proceso](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="known-limitations"></a>Limitaciones conocidas

A continuación se indican las limitaciones conocidas de la recarga activa de XAML. Para evitar cualquier limitación en la que se ejecute, simplemente detenga el depurador y, a continuación, complete la operación.

|Limitación|WPF|UWP|Notas|
|-|-|-|-|
|Cableado de eventos a controles mientras la aplicación se está ejecutando|No admitido|No compatible|Vea el error: *Error al comprobar el evento*|
|Crear objetos de recursos en un diccionario de recursos como los de la página o la ventana de la aplicación o *app. Xaml*|No admitido|Compatible|Ejemplo: agregar un `SolidColorBrush` a un diccionario de recursos para su uso `StaticResource`como.</br>Nota: Los recursos estáticos, convertidores de estilo y otros elementos que se escriben en un diccionario de recursos se pueden aplicar/usar al usar la recarga activa de XAML. Solo se admite la creación del recurso.</br> Cambiar la propiedad del `Source` Diccionario de recursos.|
|Agregar nuevos controles, clases, ventanas u otros archivos al proyecto mientras la aplicación se está ejecutando|No admitido|No admitido|None|
|Administración de paquetes NuGet (agregar, quitar o actualizar paquetes)|No admitido|No admitido|None|
|Cambiar el enlace de datos que usa la extensión de marcado {x:Bind}|N/D|Compatible con Visual Studio 2019 y versiones posteriores|No se admite en Visual Studio 2017 o versiones anteriores|

## <a name="error-messages"></a>mensajes de error

Es posible que se produzcan los siguientes errores al usar la recarga activa de XAML.

|Mensaje de error|DESCRIPCIÓN|
|-|-|
|Error al comprobar el evento|Error indica que está intentando conectar un evento a uno de los controles, lo que no se admite mientras la aplicación se está ejecutando.|
|Editar y continuar de XAML no ha encontrado elementos para actualizar.|Se produce un error cuando se edita XAML que no se puede actualizar en la aplicación.</br> A veces, este error puede solucionarse mediante la aplicación en ejecución para navegar a una vista en la que se usa el código XAML.</br> A veces, este error significa que no se puede aplicar el cambio específico hasta que se reinicie la sesión de depuración. |
|Este cambio no se admite durante una sesión de depuración.|Error indica que el cambio que está intentando no es compatible con la recarga activa de XAML. Detenga la sesión de depuración, realice el cambio y, a continuación, reinicie la sesión de depuración.|
