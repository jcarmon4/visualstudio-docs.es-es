---
title: Creación de una extensión con una ventana de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431854"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Creación de una extensión con una ventana de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este procedimiento, aprenda a usar la plantilla de proyecto VSIX y la **ventana de herramientas personalizada** plantilla de elemento para crear una extensión con una ventana de herramientas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Creación de una ventana de herramientas  
  
1. Cree un proyecto VSIX denominado **FirstWindow**. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2. Cuando se abra el proyecto, agregue una plantilla de elemento de ventana de herramienta denominada **FirstWindow**. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# / extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de la ventana de herramienta a **FirstWindow.cs**.  
  
3. Compile la solución y comience la depuración.  
  
     Aparece la instancia experimental de Visual Studio. Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
4. En la instancia experimental, vaya a **vista / Windows otros**.  
  
     Debería ver un elemento de menú para **FirstWindow**. Haga clic en él.  
  
     Debería ver una ventana de herramientas con el título **FirstWindow** y un comentario de botón **Click Me!.**
