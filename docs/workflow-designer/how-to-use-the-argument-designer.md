---
title: 'Diseñador de flujo de trabajo - Cómo: Usar el diseñador de argumentos'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c333e78de17a3af5b4f7f0be46c19cf3120231d
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746909"
---
# <a name="how-to-use-the-argument-designer"></a>Procedimiento Usar el diseñador de argumentos

El Diseñador de argumentos facilita al permitir que los datos fluyen hacia dentro y fuera de una actividad. Obtener acceso al diseñador haciendo clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de argumentos que aparecen en un formato tabular y se pueden ordenar por cada uno de los encabezados de columna, excepto para el **valor predeterminado** columna. Cada argumento contiene un nombre, dirección IN/OUT/IN-OUT/PROPERTY, tipo y valor de la expresión predeterminado (en su caso). El nombre y el valor de la expresión predeterminado son campos de texto editable y el tipo y la dirección son listas desplegables. Para obtener más información, consulte [Variables y argumentos (. NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Para crear un argumento nuevo

1. En Visual Studio, abra una solución de flujo de trabajo o actividad.

2. Abra el Diseñador de argumentos, al hacer clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de argumentos.

3. Haga clic en la fila vacía con la etiqueta **crear argumento**. Esto agregará una nueva fila con un nuevo argumento mediante los siguientes valores predeterminados: argumentx para el **nombre** donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de argumento único, **en**  para el **dirección**, y **cadena** para el **tipo de argumento**. No se agrega ningún valor para **valor predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar un argumento, seleccione el argumento haciendo clic en él y, a continuación, presione el **eliminar** clave.

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)