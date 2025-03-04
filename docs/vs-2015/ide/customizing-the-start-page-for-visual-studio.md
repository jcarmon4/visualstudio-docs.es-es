---
title: Personalización de la página de inicio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 266082af039ee7f0ba2bd60e0c9a67145aaed1d3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701137"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personalizar la página principal de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varias formas predeterminadas de personalizar la página principal de Visual Studio: se puede mostrar el cuadro de diálogo **Abrir proyecto** o abrir la solución que se ha cargado en último lugar. También puede mostrar una página principal personalizada, que es una página XAML de Windows Presentation Foundation (WPF), que se ejecuta en una ventana de herramientas y ejecuta comandos internos de Visual Studio.

## <a name="customizing-the-default-start-page"></a>Personalizar la página principal predeterminada

1. En la barra de menús, elija **Herramientas**, **Opciones**.

2. Expanda **Entorno** y después elija **Inicio**.

3. En la lista **Al inicio**, elija el elemento que quiera personalizar.

## <a name="show-a-custom-start-page"></a>Mostrar una página principal personalizada

1. Instale una página principal personalizada de una de las siguientes maneras:

    - Instálela desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/), desde otro sitio web o desde una página de su intranet local.

        > [!NOTE]
        > Si le gusta una página de una versión anterior de Visual Studio, puede actualizarla con Visual Studio SDK. Consulte [How to: Upgrade a Visual Studio Custom Start Page](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md) (Procedimiento para actualizar una página de inicio personalizada de Visual Studio).

         Abra un archivo .vsix que contenga una página principal personalizada, o copie y pegue los archivos de la página principal en la carpeta **%USERPROFILE%\Mis documentos\Visual Studio 2015\StartPages** del equipo.

    - Cree su propia página principal si ha instalado Visual Studio SDK.

         Consulte [Crear su propia página de inicio](../misc/creating-your-own-start-page.md).

2. En la barra de menús, elija **Herramientas**, **Opciones**.

3. Expanda **Entorno** y después elija **Inicio**.

4. En la lista **Personalizar página principal**, seleccione la página que quiera.

> [!NOTE]
> Si un error de una página principal personalizada hace que Visual Studio se bloquee, inicie Visual Studio en modo seguro y después establezca que se use la página principal predeterminada. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vea también
 [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Crear su propia página de inicio](../misc/creating-your-own-start-page.md)
