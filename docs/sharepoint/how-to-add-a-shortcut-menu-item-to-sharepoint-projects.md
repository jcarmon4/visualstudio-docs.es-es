---
title: Procedimiento Agregar un elemento de menú contextual a los proyectos de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b5db3fe3aaf8dc57c7df6a63810106ae9fb30fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967127"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procedimiento Agregar un elemento de menú contextual a los proyectos de SharePoint
  Puede agregar un elemento de menú contextual para un proyecto de SharePoint. El elemento de menú aparece cuando un usuario del botón secundario en un nodo de proyecto **el Explorador de soluciones**.

 Los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, vea [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Para agregar un elemento de menú contextual a los proyectos de SharePoint

1. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> eventos de la *projectService* parámetro.

2. En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de objeto para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> colección del parámetro de argumentos del evento.

3. En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de objetos, realizar las tareas que desee ejecutar cuando un usuario hace clic en el elemento de menú contextual.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar un elemento de menú contextual a los nodos de proyecto de SharePoint en **el Explorador de soluciones**. Cuando el usuario hace clic con el botón un nodo de proyecto y hace clic en el **escribir mensaje de la ventana de salida** elemento de menú, Visual Studio muestra un mensaje en el **salida** ventana. En este ejemplo se usa el servicio de proyecto de SharePoint para mostrar el mensaje. Para obtener más información, consulte [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Extender los proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Cómo: Agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
