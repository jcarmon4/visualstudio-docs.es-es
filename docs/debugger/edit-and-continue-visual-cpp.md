---
title: Editar y continuar (Visual C++) | Microsoft Docs
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff67be52c36050f513fc3ef6530a6bd81d8988d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851149"
---
# <a name="edit-and-continue-visual-c"></a>Editar y continuar (Visual C++)
Puede usar Editar y continuar en proyectos de Visual C++. Consulte [cambios de código compatible (C++)](../debugger/supported-code-changes-cpp.md) para obtener información acerca de las limitaciones de editar y continuar.

Para obtener más información acerca de las mejoras de Visual Studio 2015 Update 3, vea [C++ editar y continuar en Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 La opción de compilador [/Zo (Mejorar la depuración optimizada)](/cpp/build/reference/zo-enhance-optimized-debugging) que se introdujo en Visual Studio 2013 actualización 3 agrega información adicional a los archivos .pdb (símbolo) para los archivos binarios que se compilan sin la opción [/Od (Deshabilitar (Depurar))](https://msdn.microsoft.com/library/aafb762y.aspx).

 **/ Zo** deshabilita Editar y continuar. Vea [Cómo: Depuración de código optimizado](../debugger/how-to-debug-optimized-code.md).

## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Habilitar o deshabilitar Editar y continuar
 Quizá quiera deshabilitar la invocación automática de Editar y continuar si realiza modificaciones en el código que no quiere aplicar durante la sesión de depuración actual. También puede volver a habilitar la invocación automática de Editar y continuar.

> [!IMPORTANT]
> Para la configuración de compilación necesaria y otra información sobre la compatibilidad de característica, consulte [ C++ editar y continuar en Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Si está en una sesión de depuración, detenga la depuración (**MAYÚS + F5**).

2. En el menú **Herramientas** , elija **Opciones**.

3. En el cuadro de diálogo **Opciones**, seleccione **Depuración > General**.

4. Para habilitar, seleccione **Habilitar Editar y continuar**. Para deshabilitar, desactive la casilla de verificación.

5. En el grupo **Editar y continuar** , active o desactive la casilla **Habilitar la opción Editar y continuar nativa** .

   La modificación de esta configuración afecta a todos los proyectos en los que trabaje. No es necesario recompilar la aplicación después de cambiar esta configuración. Si compila la aplicación desde la línea de comandos o desde un archivo Make, pero realiza la depuración en el entorno de Visual Studio, puede seguir usando Editar y continuar si establece la opción **/ZI**.

## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Aplicar cambios en el código de forma explícita
 En Visual C++, Editar y continuar puede aplicar cambios de código de dos maneras. Los cambios de código se pueden aplicar de forma implícita cuando se elige un comando de ejecución, o de forma explícita mediante el comando **Aplicar cambios en el código** .

 Cuando los cambios en el código se aplican de forma explícita, el programa permanece en modo de interrupción y no se produce ninguna ejecución.

- Para aplicar los cambios en el código de manera explícita, vaya al menú **Depurar** y elija **Aplicar cambios en el código**.

## <a name="BKMK_How_to_stop_code_changes"></a> Detener cambios en el código
 Mientras Editar y continuar se encuentra en proceso de aplicar los cambios del código, puede detener la operación.

 Para detener la aplicación de los cambios en el código:

- En el menú **Depurar** , elija **Detener la aplicación de cambios en el código**.

  Este elemento de menú sólo es visible cuando se están aplicando los cambios del código.

  Si elige esta opción, no se confirmará ninguno de los cambios en el código.

## <a name="BKMK_How_to_reset_the_point_of_execution"></a> Restablecer el punto de ejecución
 Algunos cambios realizados en el código pueden hacer que el punto de ejecución se desplace a una nueva ubicación cuando Editar y continuar aplique los cambios. Editar y continuar coloca el punto de ejecución con la mayor exactitud posible, pero puede ocurrir que los resultados no sean correctos en todos los casos.

 En Visual C++, un cuadro de diálogo le informa cuando cambia el punto de ejecución. Deberá comprobar si la ubicación es correcta antes de continuar con la depuración. Si no es correcta, utilice el comando **Establecer instrucción siguiente** . Para más información, consulte [Establecer la siguiente instrucción que se debe ejecutar](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

## <a name="BKMK_How_to_work_with_stale_code"></a> Trabajar con código obsoleto
 En algunos casos, la función Editar y continuar no puede aplicar al archivo ejecutable cambios en el código de forma inmediata, pero puede que lo consiga más tarde si continúa la depuración. Esto ocurre si se modifica una función que llama a la función actual o se agregan más de 64 bytes de nuevas variables a una función que está en la pila de llamadas.

 En esos casos, el depurador sigue ejecutando el código original hasta que se puedan aplicar los cambios. El código obsoleto aparece como una ventana de archivo de código fuente temporal en una ventana de código fuente independiente, con un título como `enc25.tmp`. El código fuente modificado continúa apareciendo en la ventana de código fuente original. Si intenta modificar el código obsoleto, aparece un mensaje de advertencia.

## <a name="see-also"></a>Vea también
- [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)