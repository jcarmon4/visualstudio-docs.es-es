---
title: Limitaciones sobre la depuración de WCF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3faa57a0a2ca413898364c2d4ad1891df85f1ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176801"
---
# <a name="limitations-on-wcf-debugging"></a>Limitaciones de la depuración de WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay tres maneras mediante las que puede empezar a depurar un servicio WCF:  
  
- Se depura un proceso cliente que llama a un servicio. El depurador va al servicio. El servicio no tiene que estar en la misma solución que la aplicación cliente.  
  
- Se depura un proceso cliente que realiza una solicitud a un servicio. El servicio debe formar parte de la solución.  
  
- Se utiliza **Asociar al proceso** para asociarse a un servicio que se está ejecutando actualmente. La depuración comienza dentro del servicio.  
  
  En este tema se describen las limitaciones de estos escenarios.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitaciones de ir a un servicio  
 Para ir a un servicio desde una aplicación cliente que está depurando, se deben cumplir las siguientes condiciones:  
  
- El cliente debe llamar al servicio utilizando un objeto de cliente sincrónico.  
  
- La operación del contrato no puede ser unidireccional.  
  
- Si el servidor es asincrónico, no se puede ver la pila de llamadas completa mientras se esté ejecutando el código dentro del servicio.  
  
- La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Este código solo se tiene que agregar una vez. Puede agregar este código modificando el archivo .config o asociándose al servicio mediante **Asociar al proceso**. Si se utiliza **Asociar al proceso** en un servicio, el código de depuración se agrega automáticamente al archivo .config. Después de esto, puede depurar e ir al servicio sin tener que modificar el archivo .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitaciones de salir de un servicio  
 Salir de un servicio y regresar al cliente tiene las mismas limitaciones que se describieron para ir a un servicio. Además, el depurador debe estar asociado al cliente. Si está depurando un cliente y va a un servicio, el depurador seguirá asociado al servicio. Esto es cierto si inició el cliente utilizando **Iniciar depuración** o se asoció al cliente utilizando **Asociar al proceso**. Si empieza a depurar asociándose al servicio, el depurador no estará asociado aún al cliente. En tal caso, si tiene que salir del servicio y regresar al cliente, primero deberá utilizar **Asociar al proceso** para asociarse manualmente al cliente.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitaciones de la asociación automática a un servicio  
 Asociarse automáticamente a un servicio tiene las siguientes limitaciones:  
  
- El servicio debe formar parte de la solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que está depurando.  
  
- El servicio debe estar hospedado. Puede formar parte de un proyecto de sitio web (sistema de archivos y HTTP), proyecto de aplicación web (sistema de archivos y HTTP) o proyecto de biblioteca de servicio WCF. Los proyectos de biblioteca de servicio WCF pueden ser bibliotecas de servicio o bibliotecas de servicio de flujo de trabajo.  
  
- Este servicio se debe invocar desde un cliente WCF.  
  
- La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Autohospedaje  
 Un *servicio que se hospeda a sí mismo* es un servicio WCF que no se ejecuta dentro de IIS, el host de servicio WCF o el servidor de desarrollo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obtener información sobre cómo depurar un servicio autohospedado, vea [Cómo: Depurar un servicio WCF Autohospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Autohospedaje  
 Para permitir la depuración de aplicaciones de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5, se debe instalar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5 antes de instalar [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]. Si [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] se instala antes de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5, se produce un error al intentar depurar una aplicación de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5. El mensaje de error es, "No se puede ir automáticamente al servidor". Para corregir este problema, use el Windows **Panel de Control**, **programas y características** para reparar su [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] instalación.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de servicios WCF](../debugger/debugging-wcf-services.md)   
 [Procedimientos: Depuración de un servicio WCF autohospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
