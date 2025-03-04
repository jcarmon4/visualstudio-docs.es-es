---
title: Comentarios de tareas
description: Agregar comentarios de tarea en el código
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692322"
---
# <a name="task-comments"></a>Comentarios de tareas

Al escribir código, un procedimiento habitual es comentar de forma explícita el código sin terminar o cuestionable o las soluciones rápidas con advertencias. Los tokens de señal predeterminados que proporciona Visual Studio para Mac son TODO, HACK, FIXME y UNDONE. Se pueden definir tokens personalizados en **Visual Studio > Preferencias > Entorno > Tareas**, como se muestra en la siguiente imagen:

![Preferencias de la lista de tareas](media/source-editor-image10.png)

Para agregar un nuevo comentario de tarea, agregue un comentario que incluya la palabra clave tarea. Por ejemplo:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio para Mac dirige la atención a estos marcadores al resaltarlos en el panel **Lista de tareas**, que se muestra al ir a **Vista > Paneles > Tarea**:

![Panel Lista de tareas](media/source-editor-image11.png)

## <a name="see-also"></a>Vea también

- [Uso de la lista de tareas (Visual Studio en Windows)](/visualstudio/ide/using-the-task-list)