---
title: Inspección rápida (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ac805ebea19604343d561bf553448fff2ca575
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701743"
---
# <a name="quick-watch-command"></a>Inspección rápida (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra el texto seleccionado o especificado en el campo Expresión del [cuadro de diálogo Inspección rápida](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Puede usar este cuadro de diálogo para calcular el valor actual de una variable o expresión reconocida por el depurador, o el contenido de un registro. Además, puede cambiar el valor de cualquier variable no constante o el contenido de cualquier registro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Opcional. El texto que se va a agregar al cuadro de diálogo **InspecciónRápida**.  
  
## <a name="remarks"></a>Comentarios  
 Si `text` se omite, el texto seleccionado actualmente o la palabra en el cursor se agrega a la ventana Inspección.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Utilizar el cuadro de diálogo Inspección rápida](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
