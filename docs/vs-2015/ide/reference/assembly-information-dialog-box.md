---
title: Información de ensamblado (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbcc8f31d00c270cf0eb9af8d3283a8674a639e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703703"
---
# <a name="assembly-information-dialog-box"></a>Información de ensamblado (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El cuadro de diálogo **Información de ensamblado** se usa para especificar los valores de los atributos de ensamblado globales de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], que se almacenan en el archivo AssemblyInfo creado automáticamente con el proyecto. En el **Explorador de soluciones**, el archivo se encuentra en el nodo **Mi proyecto** en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (haga clic en **Mostrar todos los archivos** para verlo); se encuentra en **Propiedades** en [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Para obtener más información sobre atributos de ensamblado, consulte [Atributos](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Para acceder a este cuadro de diálogo, seleccione un nodo de proyecto en el **Explorador de soluciones** y después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Aplicación**. En la página **Aplicación**, haga clic en el botón **Información de ensamblado**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Título**  
 Especifica un título para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Descripción**  
 Especifica una descripción opcional para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Empresa**  
 Especifica un nombre de empresa para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Producto**  
 Especifica un nombre de producto para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Especifica un aviso de copyright para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marca comercial**  
 Especifica una marca comercial para el manifiesto del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Versión de ensamblado**  
 Especifica la versión del ensamblado. Se corresponde con <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Versión de archivo**  
 Especifica un número de versión que indica al compilador que use una versión específica para el recurso de versión de archivo Win32. Se corresponde con <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Un GUID único que identifica el ensamblado. Al crear un proyecto, Visual Studio genera un GUID para el ensamblado. Se corresponde con <xref:System.Guid>.  
  
 **Independiente del idioma**  
 Especifica la cultura que admite el ensamblado. Se corresponde con <xref:System.Resources.NeutralResourcesLanguageAttribute>. El valor predeterminado es **(None)**.  
  
 **Crear ensamblado visible a través de COM**  
 Especifica si los tipos del ensamblado estarán disponibles para COM. Se corresponde con <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Vea también  
 [Página de aplicación, Diseñador de proyectos (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atributos](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
