---
title: -Log (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18b455d3da5693e5a82dbf45e52d04b18edaef5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199093"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De manera predeterminada, el archivo de registro es:  
  
 *% APPDATA %* \Microsoft\VisualStudio\\*Versión*\ActivityLog.xml  
  
 en que *Versión* es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Comentarios  
 Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.  
  
 El registro se escribe para todas las instancias de Visual Studio que se han invocado con el modificador /log. No registra las instancias de Visual Studio que se han invocado sin el modificador.  
  
## <a name="see-also"></a>Otras referencias  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
