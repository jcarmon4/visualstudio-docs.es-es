---
title: Modo mixto depuración para x64 procesos solo se admite cuando se usa Microsoft.NET Framework 4 o posterior | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 821efec0beb26cea150fe0cfac20f0dc4c45d5f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845710"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>El modo de depuración mixto para procesos x64 solo se admite cuando se usa Microsoft .NET Framework 4 o posterior
Las versiones de .NET Framework anteriores a la 4 no proporcionan compatibilidad para la depuración en modo mixto de procesos de 64 bits. Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.

### <a name="workarounds"></a>Soluciones

- Actualice el proyecto para usar Microsoft .NET Framework 4 o posterior.

     -o bien-

     Depurar el código administrado y el código nativo en sesiones de depuración independientes.

     -o bien-

     Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para cambiar la plataforma a de 32 bits (Visual Basic o C#)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en su proyecto y después seleccione **Propiedades**.

2. En las páginas de propiedades, haga clic en la pestaña **Compilar** o **Depurar**.

3. Haga clic en **Plataforma** y seleccione x86 en la lista de plataformas.

     De forma predeterminada, los compiladores de C# y Visual Basic generan código que puede ejecutarse en cualquier CPU. En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits. Para ejecutarse en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Para cambiar la plataforma a 32 bits (C/C++)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el proyecto y, a continuación, haga clic en **Propiedades**.

2. En las páginas de propiedades, haga clic en **Plataforma** y seleccione Win32 en la lista de plataformas.

### <a name="to-correct-this-error"></a>Para corregir este error

- Consulte [configurar la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)