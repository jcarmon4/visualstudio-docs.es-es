---
title: Advertencias de confiabilidad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 328e374a12b45c4a139d5e59c33be3a7bd74ac3d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142197"
---
# <a name="reliability-warnings"></a>advertencias de confiabilidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Advertencias de confiabilidad admiten la confiabilidad de la biblioteca y aplicación, como el uso de memoria y subproceso correcto.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Regla|DESCRIPCIÓN|  
|----------|-----------------|  
|[CA2000: Eliminar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|  
|[CA2001: Evite llamar a métodos problemáticos](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un miembro llama a un método potencialmente peligroso o problemático.|  
|[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|  
|[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un subproceso administrado se trata como un subproceso de Win32.|  
|[CA2004: Quite las llamadas a GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Si va a convertir al uso SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no debe llamar a GC. Controla KeepAlive, suponiendo que no tienen un finalizador sino que dependen de SafeHandle para finalizar el sistema operativo para ellos.|  
|[CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|
