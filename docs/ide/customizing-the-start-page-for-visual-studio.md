---
title: Cambiar la experiencia de inicio
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b31f033b9c04871e57836dd263071d87a24fda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824261"
---
# <a name="customize-startup"></a>Personalizar el inicio

La experiencia de inicio de Visual Studio se puede personalizar de varias maneras. Por ejemplo, puede elegir que se abra la solución más reciente o un entorno de desarrollo vacío.

::: moniker range="vs-2017"

También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation (WPF), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Para cambiar la pantalla de inicio

1. En la barra de menús, elija **Herramientas** > **Opciones**.

2. Expanda **Entorno** y después elija **Inicio**.

::: moniker range="vs-2017"

3. En la lista **Al iniciar el sistema**, seleccione el elemento que se mostrará después del inicio de Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. En la lista **On startup, open** (Al iniciar, abrir), seleccione cuál debe ser el comportamiento al iniciarse Visual Studio. Puede elegir **Start window** (Ventana de inicio, que permite abrir un proyecto nuevo o existente), **Most recent solution** (Solución más reciente) o **Emtpy environment** (Entorno vacío).

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Para mostrar una página principal personalizada

Puede [crear su propia página de inicio personalizada](../extensibility/creating-a-custom-start-page.md) mediante el SDK de Visual Studio, o usar una que alguien más ya haya creado. Por ejemplo, puede encontrar páginas de inicio personalizadas en [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Para instalar una página de inicio personalizada, abra el archivo *.vsix* o copie y pegue los archivos de la página principal en la carpeta *%USERPROFILE%\Documentos\Visual Studio 2017\StartPages* del equipo.

### <a name="to-select-which-custom-start-page-to-display"></a>Para seleccionar la página de inicio personalizada que se va a mostrar

1. En la barra de menús, seleccione **Herramientas** > **Opciones**.

1. Expanda **Entorno** y después elija **Inicio**.

1. En la lista **Personalizar página principal**, seleccione la página que quiera.

> [!TIP]
> Si un error de una página principal personalizada hace que Visual Studio se bloquee, abra Visual Studio en modo seguro y después establezca que se use la página principal predeterminada. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vea también

- [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end