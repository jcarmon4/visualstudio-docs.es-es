---
title: DebugBreak y __debugbreak | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2a40943233e7dfffd3340f2e27da1d43a76a0a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691173"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak y __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La función DebugBreak de Win32 o la función [__debugbreak](https://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) intrínseca se puede llamar en cualquier punto del código. `DebugBreak` y `__debugbreak` tienen el mismo efecto que Establecer un punto de interrupción en dicha posición.  
  
 Como `DebugBreak` es una llamada a una función del sistema, se deben instalar los símbolos de depuración del sistema para asegurarse de que se muestra la información correcta de la pila de llamadas tras una interrupción. De lo contrario, la información de la pila de llamadas mostrada por el depurador podría ser incorrecta. Si utiliza `__debugbreak`, no es necesario ningún símbolo.  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](https://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
