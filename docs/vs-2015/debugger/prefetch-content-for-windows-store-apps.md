---
title: Precargar contenido para aplicaciones de Windows Store | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4e0d9c73277a913a7539ab5eeed4cca738d9bd5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700753"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Precargar contenido para aplicaciones de la Tienda Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Para hacer que la aplicación de Windows Store con más capacidad de respuesta, puede solicitar Windows que precargue algún contenido web, como páginas web o imágenes, en la aplicación [WinINet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](https://msdn.microsoft.com/library/aa383630.aspx)memoria caché. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la clase [Windows.Networking.BackgroundTransfer.ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) permiten especificar los URI del contenido que se desea precargar. En el [ejemplo de precarga de contenido](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) de Windows SDK dispones de ejemplos para agregar la funcionalidad ContentPrefetcher a una aplicación.  
  
 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puedes usar el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher  
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o se han modificado, tienes que iniciar y detener la aplicación antes de elegir el comando **Desencadenar precarga de aplicaciones de la Tienda Windows**. Primero se ejecuta la aplicación para registrar los URI. Después, el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** hace que ContentPrefetcher descargue el contenido y lo agregue a la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.  
  
1. Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el menú **Depurar**, seleccione **Iniciar depuración** (método abreviado de teclado: F5).  
  
2. En el **depurar** menú, elija **Detener depuración** (método abreviado de teclado: MAYÚS + F5).  
  
3. En el menú **Depurar**, elija **Otros destinos de depuración** y después **Desencadenar precarga de aplicaciones de la Tienda Windows**.  
  
   Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.  
  
> [!NOTE]
> Repite estos pasos siempre que agregues o modifiques el contenido web especificado.  
  
## <a name="see-also"></a>Vea también  
 [Entrada de blog: Desencadenar precarga de aplicaciones de Windows Store en Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)
