---
title: 'Error: Error de autenticación de Kerberos | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5e85bc7a5bac87692448aab393056fa1db5edbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535648"
---
# <a name="error-kerberos-authentication-failed"></a>Error: Error de autenticación Kerberos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al intentar realizar la depuración remota, podría aparecer el siguiente mensaje de error:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 Este error se produce cuando el Monitor de depuración remota de Visual Studio se está ejecutando con la cuenta de sistema local o de servicio de red. Con una de estas cuentas, el depurador remoto debe establecer una conexión de autenticación Kerberos para comunicarse de vuelta con el equipo host del depurador de Visual Studio.  
  
 La autenticación Kerberos no está disponible bajo estas condiciones:  
  
- El equipo de destino o el equipo host del depurador está en un grupo de trabajo, en lugar de en un dominio  
  
   \- o -  
  
- Kerberos está deshabilitado en el controlador de dominio.  
  
  Si la autenticación Kerberos no está disponible, cambie la cuenta que se usa para ejecutar el Monitor de depuración remota de Visual Studio. Para conocer el procedimiento, consulte [Error: El servicio de Visual Studio Remote Debugger del equipo de destino no se puede conectar a este equipo](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
  Si ambos equipos están conectados al mismo dominio y todavía aparece este mensaje, compruebe que DNS en el equipo de destino está resolviendo correctamente el nombre del equipo host del depurador. Vea el procedimiento siguiente.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Para comprobar que DNS en el equipo de destino está resolviendo correctamente el nombre del equipo host del depurador  
  
1. En el equipo de destino, abra el menú **Inicio**, elija **Accesorios** y, a continuación, haga clic en **Símbolo del sistema**.  
  
2. En la ventana **Símbolo del sistema**, escriba:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3. La primera línea de la respuesta `ping` muestra el nombre del equipo completo y la dirección IP que devuelve DNS para el equipo especificado.  
  
4. En el equipo host del depurador, abra una ventana **Símbolo del sistema** y ejecute `ipconfig`.  
  
5. Compare los valores de la dirección IP.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
