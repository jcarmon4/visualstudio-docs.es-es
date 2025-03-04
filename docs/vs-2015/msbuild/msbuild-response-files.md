---
title: Archivos de respuesta de MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189381"
---
# <a name="msbuild-response-files"></a>Archivos de respuesta de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los archivos de respuesta (.rsp) son archivos de texto que contienen modificadores de línea de comandos de MSBuild.exe. Cada modificador puede estar en una línea independiente o todos los modificadores pueden aparecen en una sola línea. Las líneas de comentario van precedidas del símbolo **#** . El modificador **@** se usa para pasar otro archivo de respuesta a MSBuild.exe.  
  
 El archivo de respuesta automática es un archivo .rsp especial que MSBuild.exe usa automáticamente al crear un proyecto. Este archivo, MSBuild.rsp, debe estar en el mismo directorio que MSBuild.exe, de lo contrario no se encontrará. Puede editar este archivo para especificar los modificadores de línea de comandos predeterminados a MSBuild.exe. Por ejemplo, si usa el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **/logger** a MSBuild.rsp y MSBuild.exe usará el registrador cada vez que se compila un proyecto.  
  
## <a name="see-also"></a>Otras referencias  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)
