---
title: Actualizando la interfaz de usuario | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cec2e3a1049f59fa585e4f3a7b0bd608740ccfa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316345"
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los nuevos comandos.

 En una aplicación típica de Win32, el conjunto de comandos que se puede sondear continuamente y se puede ajustar el estado de los comandos individuales tal y como el usuario ve a ellos. Sin embargo, dado que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell puede hospedar un número ilimitado de VSPackages, amplia sondeo podría disminuir la capacidad de respuesta, especialmente de sondeo a través de los ensamblados de interoperabilidad entre código administrado y COM.

### <a name="to-update-the-ui"></a>Para actualizar la interfaz de usuario

1. Realice uno de estos pasos:

    - Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz puede obtenerse a partir del <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de servicio, como se indica a continuación.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         Si el parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> es distinto de cero (`TRUE`), a continuación, la actualización se realiza de forma sincrónica e inmediatamente. Se recomienda pasar cero (`FALSE`) para este parámetro ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca cuando se crea el comando en el archivo .vsct. No obstante, utilice la marca con precaución o disminuya el rendimiento. Para obtener más información acerca de las marcas de comando, consulte el [comando marca elemento](../extensibility/command-flag-element.md) documentación.

    - En los VSPackages que hospedar un control ActiveX mediante el modelo de activación en contexto en una ventana, podría ser más conveniente usar el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz son funcionalmente equivalentes. Ambas hacen que el entorno volver a consultar el estado de todos los comandos. Normalmente, una actualización no se realiza inmediatamente. En su lugar, una actualización se retrasa hasta el tiempo de inactividad. El shell se almacena en caché el estado del comando para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca cuando se crea el comando en el archivo .vsct. No obstante, use la marca con precaución porque podría disminuir el rendimiento.

         Tenga en cuenta que puede obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz mediante una llamada a la `QueryInterface` método en un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objeto u obtenido por la interfaz desde el <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.

## <a name="see-also"></a>Vea también
- [Adición de elementos de la interfaz de usuario por VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../extensibility/internals/command-implementation.md)