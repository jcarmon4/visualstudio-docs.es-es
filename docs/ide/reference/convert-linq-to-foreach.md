---
title: Refactorización del código para convertir un bucle for en una instrucción foreach
description: Convierta cualquier consulta de LINQ escrita con una sintaxis de consulta en una instrucción foreach.
ms.date: 05/15/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 446d0f3a4988552e8e1fbbac32ca150491975d94
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483678"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactorización del código para convertir un bucle for en una instrucción foreach

Utilice esta refactorización para convertir la [sintaxis de consulta LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) en una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refactorización se aplica a lo siguiente:

- C#

## <a name="how-to-use-it"></a>Cómo usarlo

1. Seleccione toda la consulta LINQ a partir de `from`.

   > [!NOTE]
   > Esta refactorización solo puede usarse para convertir consultas LINQ expresadas con la sintaxis de consulta y no con la sintaxis de método.

1. Presione **Ctrl**+ **.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Convertir LINQ al menú de acciones rápidas de foreach](media/convert-linq-to-foreach.png)

1. Seleccione **Convertir en "foreach"** . También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

> [!NOTE]
> En C#, el código generado por estas refactorizaciones usa un tipo explícito o [var](/dotnet/csharp/language-reference/keywords/var) como variable de iteración del bucle `foreach`. El tipo en el código generado, explícito o implícito, depende de la configuración de estilo de código que queda dentro del ámbito. Estas opciones de estilo de código concretas se configuran en el nivel de máquina en **Herramientas** > **Opciones** > **Editor de texto** > **C#**  > **Estilo de código** > **General** > **Preferencias de \'var'** o en el nivel de solución en un archivo [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types). Si cambia una configuración de estilo de código en **Opciones**, vuelva a abrir el archivo de código para que los cambios surtan efecto.

## <a name="see-also"></a>Vea también

- [LINQ](/dotnet/standard/using-linq)
- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)