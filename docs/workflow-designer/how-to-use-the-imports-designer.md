---
title: 'Diseñador de flujo de trabajo - Cómo: Usar el diseñador de importaciones'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11c0c959964fee21f2cdfe098907ab2dfe184f7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949073"
---
# <a name="how-to-use-the-imports-designer"></a>Procedimiento Usar el diseñador de importaciones

El diseñador de importaciones le permite escribir los espacios de nombres para los tipos que utilizará en sus expresiones. De forma similar a la **importa** o **mediante** habilitar palabras clave en Visual Basic y C#, la especificación de espacios de nombres en el Diseñador de importaciones le permite escribir simplemente un nombre de tipo en la expresión en lugar de un nombre completo nombre del tipo de versión.

El diseñador de importaciones reacciona tanto a los cambios en la interfaz de usuario como a los cambios que se efectúan cuando se guarda el flujo de trabajo. Cuando el flujo de trabajo está guardado, los espacios de nombres se pueden agregar automáticamente al diseñador de importaciones. Entre ellas se incluyen las siguientes:

- Espacios de nombres para cualquier tipo utilizado en declaraciones de variables y de argumentos.

- Espacios de nombres para cualquier tipo utilizado en expresiones.

- Cualquier otro espacio de nombres que se necesite para serializar el flujo de trabajo (por ejemplo, espacios de nombres utilizados por actividades personalizadas que se hayan colocado en el flujo de trabajo).

  Cuando se guarda el flujo de trabajo, podría observar que algunos espacios de nombres que ha eliminado manualmente se vuelven a agregar automáticamente al diseñador de importaciones debido a la lógica descrita en la lista anterior.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Para agregar un espacio de nombres a la lista de espacios de nombres importados

1. Abra una aplicación de servicio de flujo de trabajo de WCF, aplicación de consola de flujos de trabajo o proyecto de biblioteca de actividades en Visual Studio o una aplicación de flujo de trabajo rehospedado.

2. Haga clic en **importaciones** en la parte inferior del lienzo principal. Aparecerá el diseñador de importaciones.

3. Escriba o seleccione un espacio de nombres desde el control de lista desplegable en la parte superior del diseñador de importaciones.

     Cuando escriba, aparecerá una lista de espacios de nombres válidos que coinciden con los caracteres que se van escribiendo.

4. Presione **ENTRAR** para agregar el espacio de nombres a la lista.

5. Si desea quitar un espacio de nombres de la lista, seleccione el espacio de nombres y, a continuación, presione el **eliminar** en el teclado. Observe que un espacio de nombres solo se puede eliminar si el espacio de nombres no es válido por cualquier razón, por ejemplo si el proyecto ya no hace referencia al ensamblado que contiene el espacio de nombres.