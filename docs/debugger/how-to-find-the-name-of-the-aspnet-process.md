---
title: Busque el proceso ASP.NET en ejecución | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 27221a4ae47b9fb06130b550ceb6d3cc1f00dce0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906815"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Buscar el nombre de un proceso de ASP.NET

Para depurar un ejecución [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación, debe asociar el depurador de Visual Studio para el [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesos por nombre.

**Para averiguar qué proceso se está ejecutando una aplicación ASP.NET:**

1. Con la aplicación en ejecución en Visual Studio, seleccione **depurar** > **asociar al proceso**.

1. En el **asociar al proceso** cuadro de diálogo, escriba las primeras letras del proceso de los nombres de la lista siguiente, o bien escribirlos en el cuadro de búsqueda. Lo que se está ejecutando es la ejecución de la aplicación ASP.NET. Adjuntar al proceso para depurar la aplicación.

    - *w3wp.exe* es IIS 6.0 y versiones posteriores.
    - *aspnet_wp.exe* es versiones anteriores de IIS.
    - *iisexpress.exe* es IISExpress.
    - *dotnet.exe* es ASP.NET Core.
    - *Inetinfo.exe* está en proceso de ejecutar las aplicaciones ASP anteriores.

>[!NOTE]
>Visual Studio 2012 y anterior [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código puede estar en el sistema de archivos y ejecutar en el servidor de prueba *WebDev.WebServer.exe* o *WebDev.WebServer40.exe*. En este caso, para la depuración local, adjuntar a *WebDev.WebServer.exe* o *WebDev.WebServer40.exe* en lugar de la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proceso.

**Vea también:**

- [Adjuntar a un proceso en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Requisitos previos para la depuración remota de aplicaciones web](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)
- [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)