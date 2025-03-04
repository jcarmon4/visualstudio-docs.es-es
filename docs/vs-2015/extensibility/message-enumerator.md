---
title: Enumerador de mensajes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194339"
---
# <a name="message-enumerator"></a>Enumerador de mensaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las marcas siguientes se usan para la `TEXTOUTPROC` función, que es una función de devolución de llamada que el IDE proporciona cuando llama a la [SccOpenProject](../extensibility/sccopenproject-function.md) (consulte [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) para obtener más información sobre la devolución de llamada función).  
  
 Si el IDE se pide a cancelar el proceso, puede obtener uno de los mensajes de cancelación. En este caso, el origen de control usa complemento `SCC_MSG_STARTCANCEL` para pedir el IDE para mostrar el **cancelar** botón. Una vez hecho esto, se puede enviar cualquier conjunto de mensajes normales. Si alguno de estos Devuelve `SCC_MSG_RTN_CANCEL`, a continuación, el complemento se cierra la operación y devuelve. El complemento también sondea `SCC_MSG_DOCANCEL` periódicamente para determinar si el usuario ha cancelado la operación. Cuando se realizan todas las operaciones, o si el usuario ha cancelado, envía el complemento `SCC_MSG_STOPCANCEL`. El `SCC_MSG_INFO`, SCC_MSG_WARNING, y los tipos SCC_MSG_ERROR se utilizan para los mensajes que se muestran en la lista desplazable de mensajes. `SCC_MSG_STATUS` es un tipo especial que indica que el texto debería aparecer en una barra de estado o el área de presentación temporal. No permanecen permanentemente en la lista.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Miembros  
 SCC_MSG_RTN_CANCEL  
 Devolver desde la devolución de llamada para indicar la cancelación.  
  
 SCC_MSG_RTN_OK  
 Devolver desde la devolución de llamada para continuar.  
  
 SCC_MSG_INFO  
 Mensaje es informativo.  
  
 SCC_MSG_WARNING  
 Mensaje es una advertencia.  
  
 SCC_MSG_ERROR  
 Mensaje es un error.  
  
 SCC_MSG_STATUS  
 Mensaje está pensado para la barra de estado.  
  
 SCC_MSG_DOCANCEL  
 No hay texto; Devuelve el IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Inicia un bucle de cancelación.  
  
 SCC_MSG_STOPCANCEL  
 Detiene el bucle de cancelación.  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
