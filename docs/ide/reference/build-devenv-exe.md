---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67aba8d93514618fc09abe933cfd28023136a4d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790920"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Compila una solución o proyecto mediante un archivo de configuración de solución especificado.

## <a name="syntax"></a>Sintaxis

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Obligatorio. Ruta de acceso completa y nombre del archivo de solución.

- *SolnConfigName*

  Opcional. Nombre de la configuración de solución (por ejemplo, `Debug` o `Release`) que se usará para compilar la solución indicada en *SolutionName*. Si hay varias plataformas de solución disponibles, también se tiene que especificar la plataforma (por ejemplo, `Debug|Win32`). Si no se especifica este argumento o se usa una cadena vacía (`""`), la herramienta usará la configuración activa de la solución.

- `/Project` *ProjName*

  Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nombre de una configuración de compilación del proyecto (por ejemplo, `Debug` o `Release`) que se usará para crear el proyecto indicado. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si se especifica este modificador, reemplaza al argumento *SolnConfigName*.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

- El modificador `/Build` realiza la misma función que el comando de menú **Compilar solución** en el entorno de desarrollo integrado (IDE).

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana de comandos o en cualquier archivo de registro especificado con el modificador `/Out`.

- El modificador `/Build` solo compila proyectos que han cambiado desde la última compilación. Para compilar todos los proyectos en una solución, use [/rebuild](../../ide/reference/rebuild-devenv-exe.md) en su lugar.

- Si recibe el mensaje de error **Configuración del proyecto no válida**, asegúrese de que ha especificado una plataforma de solución o de proyecto (por ejemplo, `Debug|Win32`).

## <a name="example"></a>Ejemplo

El comando siguiente compila el proyecto `CSharpWinApp` con la configuración de compilación del proyecto `Debug` en `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Compilación y limpieza de proyectos y soluciones](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)