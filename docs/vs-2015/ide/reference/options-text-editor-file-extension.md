---
title: Opciones, editor de texto, extensión de archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd49b08e8bd48393a980fe775db66c96c0edc1fd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695830"
---
# <a name="options-text-editor-file-extension"></a>Opciones, editor de texto, extensión de archivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este cuadro de diálogo Opciones le permite especificar cómo se controlarán todos los archivos con determinadas extensiones de archivo mediante el Entorno de desarrollo integrado (IDE) de Visual Studio. Para cada **extensión** que especifique, puede seleccionar un editor asociado. Esto le permite elegir el diseñador o el editor del IDE en el que se abrirán los documentos de un tipo determinado. Para mostrar estas opciones, pulse **Opciones** del menú **Herramientas**, expanda el nodo **Editor de texto** y seleccione **Extensión de archivo**.  
  
 Cuando selecciona una opción "con codificación", se mostrará un cuadro de diálogo siempre que abra un documento de ese tipo que le permite seleccionar un esquema de codificación para ese documento. Esto puede resultar útil si está preparando versiones de sus documentos de proyecto para usarlos en diferentes plataformas o en diferentes idiomas de destino.  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Extensión**  
 Escriba la extensión de archivo cuyo editor asociado en el IDE quiere definir.  
  
 **Editor**  
 Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos con esta extensión de archivo. Cuando selecciona una opción "con codificación", se mostrará un cuadro de diálogo siempre que abra dicho documento que le permite seleccionar un esquema de codificación.  
  
 **Add**  
 Agrega una entrada que incluye la **extensión** y el **editor asociado** especificados a la lista de extensiones.  
  
 **Remove**  
 Elimina la entrada seleccionada de la lista de extensiones.  
  
 Lista de extensiones  
 Muestra todas las extensiones para las que se ha especificado un editor asociado.  
  
 **Asignar archivos sin extensión**  
 Seleccione esta opción si quiere especificar cómo se controlarán los archivos sin una extensión mediante el IDE.  
  
 **Opciones de archivos sin extensión**  
 Proporciona la misma lista que el **Editor**. Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos sin extensiones de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Administrar los modos del editor](../../ide/how-to-manage-editor-modes.md)
