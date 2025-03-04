---
title: Obtención de información de servicio de la configuración de Store | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f65fe81d1b2382df3847c2cfdc0b8ffbfff5662
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342435"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtener información del servicio desde el almacén de configuración
Puede usar el almacén de configuración para encontrar todos los servicios disponibles o para determinar si está instalado un servicio determinado. Debe conocer el tipo de la clase de servicio.

## <a name="to-list-the-available-services"></a>Para enumerar los servicios disponibles

1. Cree un proyecto VSIX denominado `FindServicesExtension` y, a continuación, agregue un comando personalizado denominado `FindServicesCommand`. Para obtener más información sobre cómo crear un comando personalizado, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

2. En *FindServicesCommand.cs*, agregue las siguientes instrucciones using:

    ```vb
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtiene el almacén de configuración de la configuración y luego busque la subcolección servicios con nombre. Esta colección incluye todos los servicios disponibles. En el `MenuItemCommand` método, quite el código existente y reemplácelo con lo siguiente:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

5. En la instancia experimental, en el **herramientas** menú, haga clic en **FindServicesCommand invocar**.

     Debería ver un cuadro de mensaje enumera todos los servicios.

     Para comprobar esta configuración, puede usar el editor del registro.

## <a name="find-a-specific-service"></a>Buscar un servicio específico
 También puede usar el <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> método para determinar si se instala un servicio determinado. Debe conocer el tipo de la clase de servicio.

1. En MenuItemCallback del proyecto que creó en el procedimiento anterior, busque el almacén de configuración de la configuración para el `Services` recopilación que tiene la subcolección denominada por el GUID del servicio. En este caso, busque el servicio de ayuda.

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Compile la solución y comience la depuración.

3. En la instancia experimental, en el **herramientas** menú, haga clic en **FindServicesCommand invocar**.

     Debería ver un mensaje con el texto **ayudar el servicio está disponible:** seguido **True** o **False**. Para comprobar esta configuración, puede usar un editor del registro, como se muestra en los pasos anteriores.