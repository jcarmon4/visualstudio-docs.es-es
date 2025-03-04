---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143549"
---

1. En el equipo donde tiene el proyecto de ASP.NET abierto en Visual Studio, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y elija **Publicar**.

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, haga clic en **Importar perfil**.

    ![Elegir Publicar](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue hasta la ubicación del archivo de configuración de publicación que creó en la sección anterior.

1. En el cuadro de diálogo **Importar archivo de configuración de publicación**, vaya al perfil que creó en la sección anterior, selecciónelo y haga clic en **Abrir**.

    Visual Studio comienza el proceso de implementación y la ventana Salida muestra el progreso y los resultados.

    Si recibe errores de implementación, haga clic en **Configuración** para editar la configuración. Modifique la configuración y haga clic en **Validar** para probar la nueva configuración. Si no se encuentra el nombre de host, pruebe la dirección IP en lugar del nombre de host en los campos **Servidor** y **Dirección URL de destino**.

    ![Edite la configuración de la herramienta de publicación](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
