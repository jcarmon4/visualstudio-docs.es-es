---
title: -Out (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e1f20b446d355ea0cbc6700de5f2e6f79de51d09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187882"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica un archivo que se va a almacenar y muestra los errores al ejecutar, compilar, recompilar o implementar una solución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argumentos  
 `FileName`  
 Obligatorio. Ruta de acceso y nombre del archivo que va a recibir los errores al compilar un ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica un nombre de archivo que no existe, se crea automáticamente el archivo. Si el archivo ya existe, los resultados se anexan al contenido existente del archivo.  
  
 Los errores de compilación de la línea de comandos se muestran en la ventana **Comando** y la vista Generador de soluciones de la ventana **Salida**. Esta opción es útil si está ejecutando generaciones desatendidas y necesita ver los resultados.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se ejecuta `MySolution` y se escriben los errores en el archivo `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Otras referencias  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
