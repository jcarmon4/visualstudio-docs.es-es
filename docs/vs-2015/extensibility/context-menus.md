---
title: Menús contextuales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184268"
---
# <a name="context-menus"></a>Menús contextuales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menús contextuales se muestran cuando un usuario del botón secundario en una región activa del área de cliente y borrar cuando se suelta el botón secundario del mouse.  
  
## <a name="editor-context-menus"></a>Menús contextuales del editor  
 Mediante la interceptación `ECMD_SHOWCONTEXTMENU`, el servicio de lenguaje puede controlar los menús contextuales que se mostrarán en el editor. Para mostrar su propio menú contextual, controlar este comando cuando se pasa en su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Si no controla este comando, el IDE muestra un menú estándar de contexto proporcionado para el editor. También puede controlar el contenido del menú contextual en una base por marcador. Para obtener más información al respecto, consulte [utilizando marcadores de texto con la API heredada](../extensibility/using-text-markers-with-the-legacy-api.md) y [intercepción de comandos del servicio de lenguaje heredado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un servicio de lenguaje heredado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)
