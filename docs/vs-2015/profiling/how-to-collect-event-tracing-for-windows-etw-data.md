---
title: Procedimiento Recopilar datos de seguimiento de eventos para Windows (ETW) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432818"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procedimiento Recopilar el seguimiento de eventos para Windows (ETW) datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seguimiento de eventos para Windows (ETW) es una eficaz utilidad de seguimiento de nivel de kernel que activa el kernel de registro del generador de perfiles o eventos definidos por la aplicación. Los datos recopilados del proveedor de eventos se pueden ver utilizando la opción /**Summary: ETW** de la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md). Utilice este informe para determinar dónde se producen problemas de rendimiento en la aplicación.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Para habilitar proveedores de seguimiento de eventos  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2. En **Páginas de propiedades**, haga clic en las propiedades de **Eventos de Windows**.  
  
3. En la lista **Seleccionar proveedor de seguimiento de eventos del que recopilar datos**, seleccione los proveedores de eventos que desea utilizar para generar perfiles de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
