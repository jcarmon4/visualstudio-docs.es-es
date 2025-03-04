---
title: Registrar una ventana de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8178938715278bf69fe8f4cc1b336bbd19cec04e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535650"
---
# <a name="registering-a-tool-window"></a>Registro de una ventana de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede registrar las ventanas de herramienta con <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> y  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Ejemplo  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 En el código anterior, el <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra las ventanas de herramientas PersistedWindowPane y DynamicWindowPane con Visual Studio. La ventana de herramientas persistente está acoplada y por fichas con **el Explorador de soluciones**, y la ventana dinámica tiene un valor predeterminado a partir de posición y tamaño. La ventana dinámica se realiza transitoria, lo que indica que no se crea durante el inicio. Escribe un valor DontForceCreate en la clave de ToolWindows en el registro del sistema. Para obtener más información, consulte [configuración de pantalla de ventana de herramienta](../extensibility/tool-window-display-configuration.md).
