---
title: 'Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar el equipo en la red. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd1402a476ce2dceaaaf78580b36db20c3eed24f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682556"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Error: No se puede conectar a la máquina &lt;nombre&gt;. No se puede encontrar el equipo en la red.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este comportamiento se produce si se da una de las condiciones siguientes:  
  
- La conexión al equipo remoto se interrumpe.  
  
- La cuenta de usuario en el equipo remoto está deshabilitada.  
  
- La contraseña en el equipo remoto ha expirado.  
  
### <a name="to-resolve-this-behavior"></a>Para solucionar este comportamiento  
  
- Asegúrese de que el equipo local y el equipo remoto están en la misma red. Para ello, utilice el Explorador de Microsoft Windows (o el Explorador de archivos) para intentar tener acceso al equipo remoto.  
  
     — y —  
  
- Asegúrese de que la cuenta de usuario que utiliza para conectarse al equipo remoto esté habilitada.  
  
     — y —  
  
- Asegúrese de que la contraseña que utiliza para conectarse al equipo remoto sea válida y no haya expirado.  
  
## <a name="see-also"></a>Vea también  
 [Configurar las herramientas remotas en el dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
