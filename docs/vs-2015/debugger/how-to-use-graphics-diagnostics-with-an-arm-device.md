---
title: Procedimiento Usar diagnóstico de gráficos con un dispositivo ARM | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685871"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Procedimiento Usar diagnóstico de gráficos con un dispositivo ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diagnóstico de Gráficos es compatible con la depuración remota de las aplicaciones Direct3D en dispositivos basados en ARM que se ejecuten en Windows RT 8.1 o Windows Phone 8.1. Puede capturar información de gráficos de la aplicación Direct3D mientras se ejecuta en el dispositivo o utilizar el dispositivo como máquina de reproducción para información de gráficos capturada previamente.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Uso del Diagnóstico de gráficos con un dispositivo basado en ARM  
 Como Visual Studio no se puede ejecutar en dispositivos basados en ARM, debe utilizar el depurador remoto para analizar una aplicación que se ejecuta en ellos. El depurador remoto es compatible con la captura de gráficos y la reproducción, de modo que puede diagnosticar errores de presentación y evaluar el rendimiento de los gráficos en estos dispositivos de una manera tan sencilla como puede depurar la aplicación en ellos.  
  
 Para utilizar las funciones del diagnóstico de gráficos, primero habilite la depuración remota en el dispositivo.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Habilitación de la depuración remota en el dispositivo basado en ARM  
  
1. Instalar el [ARM Kits directiva](https://msdn.microsoft.com/windows/desktop/dn469188) en su dispositivo basado en ARM.  
  
2. Instalar el [herramientas de depuración remota](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) en su dispositivo basado en ARM.  
  
> [!IMPORTANT]
> Para los dispositivos Windows Phone 8.1, es posible que tenga que registrar el teléfono durante el desarrollo. Para ello, debe ser un desarrollador registrado. Para obtener más información, consulte [cómo implementar y ejecutar una aplicación para Windows Phone 8](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Después de habilitar la depuración remota en el dispositivo, conviértalo en su destino de depuración e inicie el Diagnóstico de gráficos.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Configuración e inicio de Diagnóstico de gráficos en su dispositivo  
  
1. En el **plataformas de solución** lista desplegable, seleccione **ARM** para que el dispositivo basado en ARM estará disponible como un destino de depuración remoto.  
  
2. En el **depurar destino** lista desplegable, seleccione el dispositivo ARM.  
  
3. En el menú, elija **depurar**, **gráficos**, **Iniciar diagnóstico**. (Teclado: Alt+F5)  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar Windows Store apps en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Cómo: Cambio de la máquina de reproducción de Diagnóstico de gráficos](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
