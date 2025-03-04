---
title: Solución de problemas del Visor de ayuda | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77529ad9957694b1ea1853b3e8b1b1cc29c45e2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429735"
---
# <a name="troubleshooting-the-help-viewer"></a>Solución de problemas del Visor de Ayuda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se describen los problemas que pueden surgir con el Visor de Ayuda.  
  
## <a name="audio-doesnt-work"></a>El audio no funciona.  
 El Visor de Ayuda no incluye un reproductor de audio. Si descarga contenido que contiene audio y no ocurre nada al elegir **Reproducir**, instale un reproductor de audio.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>La búsqueda no funciona en Windows Server 2008, Windows Server 2008 SP1 o Windows Server 2008 R2.  
 Las características de búsqueda y filtrado en el Visor de Ayuda requieren que el servicio de Windows Search esté instalado y activado. De forma predeterminada, este servicio está desactivado en Windows Server 2008, Windows Server 2008 con Service Pack 1 (SP1) y Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Para activar el servicio de Windows Search  
  
1. Inicie el Administrador del servidor.  
  
2. En el panel de navegación izquierdo, elija **Roles**.  
  
3. En el panel Resumen de roles, elija **Agregar rol**.  
  
4. Elija el rol Servicios de archivo y después elija el botón **Siguiente**.  
  
5. Elija el servicio de rol de Windows Search.  
  
## <a name="additional-resources"></a>Recursos adicionales  
 Puede obtener más información y proporcionar comentarios sobre el Visor de Ayuda mediante los siguientes recursos:  
  
- Para enviar comentarios, vea [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) en el sitio web de Microsoft o envíe un correo a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
- Para obtener más información, consulte el [sistema de ayuda y documentación para desarrolladores de](http://go.microsoft.com/fwlink/?LinkId=232741) foro y [profesionales de la Ayuda](http://go.microsoft.com/fwlink/?LinkId=232743) blog.  
  
## <a name="see-also"></a>Vea también  
 [Guía del administrador del Visor de Ayuda 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)
