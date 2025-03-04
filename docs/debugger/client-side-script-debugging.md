---
title: Depuración de scripts del lado cliente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1501cd0243d6dc17cc627715eda85e755aec4502
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564091"
---
# <a name="client-side-script-debugging"></a>Depuración de secuencias de comandos en el cliente
El depurador de Visual Studio proporciona un entorno de depuración completo para encontrar y corregir errores en los scripts de cliente en las páginas de ASP.NET.

## <a name="opening-script-documents"></a>Abrir documentos de script
En el **Explorador de soluciones** , puede ver listas de documentos de script de cliente y servidor. Puede abrir cualquier documento de script en el **Explorador de soluciones**. Para obtener más información, vea [Cómo: Visualización de documentos de script](../debugger/how-to-view-script-documents.md).

## <a name="breakpoint-mapping"></a>Asignación de puntos de interrupción
 En Visual Studio, no puede depurar directamente código de servidor, pero puede establecer un punto de interrupción en un archivo de servidor. Visual Studio asigna automáticamente el punto de interrupción a una ubicación correspondiente en el archivo de cliente y crea un punto de interrupción asignado en el código de cliente.

## <a name="manually-or-automatically-attaching-to-script"></a>Asociar a script manual o automáticamente
 Para empezar a depurar el script en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el depurador debe asociarse al script que se desea depurar. Esto se puede realizar manual o automáticamente.

 Puede establecer una asociación manualmente utilizando la interfaz del depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para elegir un proceso de script en ejecución al que desee asociarse. Para obtener más información, vea [Cómo: Asociación a script](../debugger/how-to-attach-to-script.md).

 El depurador se asocia automáticamente al script cuando se produce una de las siguientes situaciones:

- Se encuentra un punto de interrupción establecido en el script

- Se alcanza una instrucción `Stop` de VBScript o una instrucción `debugger` de JScript en el script.

- El explorador o el servidor encuentra un error de sintaxis o en tiempo de ejecución en el script. Cuando esto se produce, aparece un cuadro de diálogo que ofrece la opción de comenzar la depuración.

  Al asociarse manualmente a un script, el proceso del script sigue ejecutándose hasta que se detenga de algún modo. Puede detenerlo eligiendo **Interrumpir** en el menú **Depurar** .

  Cuando el depurador se asocia automáticamente, la ejecución del script se detiene en la línea en la que se produjo el punto de interrupción, la instrucción `Stop` , la instrucción `debugger` o el error, o en el punto en el que decidió iniciar la depuración en Internet Explorer.

  En ese punto, puede utilizar los medios normales del depurador para comenzar la depuración. Por ejemplo, puede utilizar los comandos **Step** para seguir ejecutando el código la línea por línea. Puede usar la ventana **Pila de llamadas** para ver y controlar el flujo del script. Puede utilizar las ventanas de variables o la ventana **Inmediato** para ver o cambiar variables y propiedades.

## <a name="enhanced-error-messages-for-script-debugging"></a>Mensajes de error mejorados para la depuración de script
 Visual Studio proporciona mensajes de error mejorados para problemas comunes de depuración de script. Estos mensajes no aparecen a menos que establezca una asociación manualmente a Internet Explorer. Si encuentra una condición de error al abrir Internet Explorer automáticamente, pruebe a establecer una asociación manualmente para que pueda ver los mensajes de error.

## <a name="debugging-ajax-script-applications"></a>Depurar aplicaciones de script AJAX
 Las aplicaciones web habilitadas para AJAX usan abundante script y presentan retos de depuración especiales. Para obtener información sobre las técnicas de depuración para AJAX, vea

 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).

## <a name="see-also"></a>Vea también

- [Depurar aplicaciones de ASP.NET y AJAX](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)
- [Limitaciones de la depuración de scripts](../debugger/limitations-on-script-debugging.md)
- [Ventanas de variables](../debugger/debugger-windows.md)
- [Ventana Inmediato](../ide/reference/immediate-window.md)
- [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)