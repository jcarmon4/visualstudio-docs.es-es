---
title: Implementar una interfaz
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 58c714dec8b8a4679d34168cdaf901dc2fb94ea6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974831"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementación de una interfaz en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite generar inmediatamente el código necesario para implementar una interfaz.

**Cuándo:** Se quiere heredar de una interfaz.

**Por qué:** Se podrían implementar manualmente todas las interfaces una por una, pero esta característica generará de forma automática todas las firmas de método.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo, que señala que ha hecho referencia a una interfaz, pero que no ha implementado todos los miembros requeridos.

   - C#:

       ![Código resaltado (C#)](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/interface-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece.
      - Haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

3. Seleccione **Implementar interfaz** en el menú desplegable.

   ![Vista previa de implementación de interfaz](media/interface-preview-cs.png)

   > [!TIP]
   > - Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.
   > - Use los vínculos **Documento**, **Proyecto** y **Solución** de la parte inferior de la ventana de vista previa para crear las firmas de método adecuadas entre las múltiples clases que implementan la interfaz.

   Las firmas de método de la interfaz se crean y están listas para su implementación.

   - C#:

       ![Resultado de implementación de interfaz (C#)](media/interface-result-cs.png)

   - Visual Basic:

       ![Resultado de implementación de interfaz (VB)](media/interface-result-vb.png)

   > [!TIP]
   > (Solo C#) Use la opción **Implementar la interfaz de forma explícita** para colocar delante de cada método generado el nombre de la interfaz y, así, evitar conflictos de nombres.
   >
   > ![Resultado de la implementación de la interfaz de forma explícita](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)