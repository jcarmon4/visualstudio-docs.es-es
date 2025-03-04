---
title: advertencias de confiabilidad
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 009422eaf9ac81af6e8f9d48732655b2528c85a0
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976143"
---
# <a name="reliability-warnings"></a>Advertencias de confiabilidad

Advertencias de confiabilidad admiten la confiabilidad de la biblioteca y aplicación, como el uso de memoria y subproceso correcto. Las reglas de confiabilidad se incluyen:

|Regla|Descripción|
|----------|-----------------|
|[CA2000: Eliminar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|
|[CA2001: Evite llamar a métodos problemáticos](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Un miembro llama a un método potencialmente peligroso o problemático.|
|[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|
|[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Un subproceso administrado se trata como un subproceso de Win32.|
|[CA2004: Quite las llamadas a GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Si va a convertir al uso SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no debe llamar a GC. Controla KeepAlive, suponiendo que no tienen un finalizador sino que dependen de SafeHandle para finalizar el sistema operativo para ellos.|
|[CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|
|[CA2007: No espera una tarea directamente](../code-quality/ca2007-do-not-directly-await-task.md)|Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directamente.|