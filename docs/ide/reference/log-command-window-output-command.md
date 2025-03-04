---
title: Registrar resultados de la ventana de comandos (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ab2dfea4c51ee33407088c208aea351732b8a4a
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043524"
---
# <a name="log-command-window-output-command"></a>Comando Registrar resultados de la ventana Comandos

Copia en un archivo todas las entradas y salidas de la ventana **Comandos**.

## <a name="syntax"></a>Sintaxis

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumentos

`filename`\
Opcional. Nombre del archivo de registro. De forma predeterminada, el archivo se crea en la carpeta de perfil del usuario. Si ya existe el nombre de archivo, el registro se anexa al final del archivo existente. Si no se especifica ningún archivo, se usa el último archivo especificado. Si no existe ningún archivo anterior, se crea un archivo de registro predeterminado, denominado cmdline.log.

> [!TIP]
> Para cambiar la ubicación en la que se guarda el archivo de registro, escriba la ruta de acceso completa del archivo, entre comillas si la ruta de acceso contiene algún espacio.

## <a name="switches"></a>Modificadores

/on\
Opcional. Inicia el registro de la ventana **Comandos** en el archivo especificado y anexa el archivo con la nueva información.

/off\
Opcional. Detiene el registro de la ventana **Comandos**.

/overwrite\
Opcional. Si el archivo especificado en el argumento `filename` coincide con un archivo existente, se sobrescribe.

## <a name="remarks"></a>Comentarios

Si no se especifica ningún archivo, se crea el archivo cmdline.log de forma predeterminada. De manera predeterminada, el alias de este comando es Log.

## <a name="examples"></a>Ejemplos

Este ejemplo crea un archivo de registro, cmdlog, e inicia el registro de comandos.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Este ejemplo detiene el registro de comandos.

```cmd
>Tools.LogCommandWindowOutput /off
```

Este ejemplo reanuda el registro de comandos en el archivo de registro usado anteriormente.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)