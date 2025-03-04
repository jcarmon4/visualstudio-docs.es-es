---
title: Edición de suscripciones en el Portal de administración | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Obtenga más información sobre cómo los administradores pueden editar asignaciones de suscripción.
ms.openlocfilehash: e55cee74f861973e3cc29e3f19dc9b31a107f437
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605666"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Edición de asignaciones de suscripciones de Visual Studio
Como administrador de suscripciones, puede hacer cambios en las suscripciones asignadas a personas de su organización.  En este artículo se describen los tipos de cambios que puede realizar y se proporcionan los pasos necesarios.

## <a name="change-subscriber-information"></a>Cambio de la información del suscriptor
Puede editar la información del suscriptor para corregir los errores o actualizarla.

Para editar un suscriptor, seleccione los puntos suspensivos (...) que aparecen junto a la dirección de correo electrónico del suscriptor al mantener el mouse sobre él. Aparecerá una lista desplegable.  Seleccione **Editar** para modificar los detalles del suscriptor. También puede hacer doble clic en la fila del suscriptor en la cuadrícula para abrir la ventana de edición.
> [!div class="mx-imgBorder"]
> ![Selección de un suscriptor para editarlo](_img/edit-license/select-subscriber.png)

Puede actualizar nombre del suscriptor, los apellidos, el país, el idioma y las descargas. Edite la información del suscriptor y haga clic en **Guardar**.

   > [!NOTE]
   > Si tiene que cambiar el nivel de suscripción de un suscriptor, primero debe eliminar el usuario del portal y volverlo a agregar. Los niveles de suscripción no son editables.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Edición en masa de varios suscriptores
Puede editar varios suscriptores a la vez mediante el proceso de edición en masa. Esta característica se usa principalmente en organizaciones que están efectuando cambios en la dirección de correo electrónico corporativa o cuando una organización ha decidido restringir el acceso a las descargas.

   > [!IMPORTANT]
   > Los niveles de suscripción, es decir, Enterprise, Professional, etc., y los GUID de suscripción no se pueden modificar.  Si intenta realizar una carga con estos elementos cambiados, no podrá hacerla.

1. Para editar varios suscriptores a la vez, navegue hasta la pestaña Suscriptores. En la cinta de la parte superior, haga clic en **Edición en masa**.

2. La edición en masa usa una plantilla de Excel para realizar modificaciones en la información de los suscriptores. En el cuadro Edición en masa, haga clic en **Export this Excel** (Exportar este Excel) para descargar la lista actual de los suscriptores con toda su información.
   > [!div class="mx-imgBorder"]
   > ![Edición de una licencia: exportación en masa de la lista de ediciones](_img/edit-license/edit-license-bulk-edit-export.png)

3. Después, guarde el archivo localmente de modo que pueda encontrarlo fácilmente y realizar los cambios necesarios antes de cargarlo. Para garantizar una carga correcta, **no edite el nivel de suscripción ni el GUID de suscripción**, ya que si lo hace la carga no se podrá efectuar.

4. Vuelva al Portal de administradores de suscripciones de Visual Studio y, en el cuadro de diálogo Edición en masa, haga clic en **Examinar**. Seleccione el archivo de Excel que ha guardado y haga clic en **Aceptar**. Verá el progreso de la carga en la pantalla.
   > [!div class="mx-imgBorder"]
   > ![Edición de una licencia: carga de archivos de ediciones en masa](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Cuando haya cargado el archivo, verá una notificación en la que se le indicará que se ha realizado correctamente. En este momento, los cambios se reflejarán en la información del suscriptor.

## <a name="next-steps"></a>Pasos siguientes
- Si necesita ayuda para encontrar una suscripción determinada, consulte [Búsqueda de suscripciones](search-license.md).
- ¿Necesita crear una lista de todas las suscripciones?  Consulte [Exportar suscripciones](exporting-subscriptions.md).