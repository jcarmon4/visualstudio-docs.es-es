---
title: Tarea FindInList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c2f6c5f14f6eff818a265e097f02e2bc76c7372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996673"
---
# <a name="findinlist-task"></a>FindInList (tarea)
Busca en una lista especificada un elemento con las especificaciones coincidentes.

## <a name="parameters"></a>Parámetros
 En la tabla siguiente se describen los parámetros de [FindInList (tarea)](../msbuild/findinlist-task.md).

|Parámetro|Descripción|
|---------------|-----------------|
|`CaseSensitive`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la búsqueda distingue entre mayúsculas y minúsculas; en caso contrario, no lo hace. El valor predeterminado es `true`.|
|`FindLastMatch`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, devuelve la última coincidencia; en caso contrario, devuelve la primera. El valor predeterminado es `false`.|
|`ItemFound`|Parámetro de salida de solo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Primer elemento coincidente que se encuentra en la lista, si existe.|
|`ItemSpecToFind`|Parámetro `String` requerido.<br /><br /> Especificación de elemento que se va a buscar.|
|`List`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Lista en la que se va a buscar la especificación de elemento.|
|`MatchFileNameOnly`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, solo se compara con la parte del nombre de archivo de la especificación de elemento; en caso contrario, se compara con toda la especificación de elemento. El valor predeterminado es `true`.|

## <a name="remarks"></a>Comentarios
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)