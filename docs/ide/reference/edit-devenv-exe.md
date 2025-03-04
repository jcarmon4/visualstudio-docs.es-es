---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f0eb7cab3b1bc764f663cd647811928510281e8
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432005"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Abre el archivo especificado en una instancia existente de Visual Studio.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumentos

- *File1*

  Opcional. Archivo que se abrirá en una instancia existente de Visual Studio. Si no existe ninguna instancia de Visual Studio, se creará una instancia con un diseño de ventana simplificado y la herramienta abrirá *File1* en la nueva instancia.

- *FileN*

  Opcional. Uno o más archivos adicionales que se abrirán en la instancia existente de Visual Studio.

## <a name="remarks"></a>Comentarios

Si no se especifica ningún archivo, recibirá el foco una instancia de Visual Studio existente. Si no se especifica ningún archivo y no existe ninguna instancia de Visual Studio, la herramienta creará una instancia con un diseño de ventana simplificado.

Si la instancia de Visual Studio existente se encuentra en el estado modal, el archivo se abrirá en la instancia existente cuando Visual Studio salga del estado modal. Por ejemplo, esta situación puede producirse cuando esté abierto el [cuadro de diálogo Opciones](../../ide/reference/options-dialog-box-visual-studio.md).

Si hay más de una instancia de Visual Studio abierta, el archivo se abre en la instancia abierta más recientemente.

## <a name="example"></a>Ejemplo

En el primer ejemplo se abre el archivo `MyFile.cs` en una instancia existente de Visual Studio. Si no existe ninguna instancia de Visual Studio, la herramienta abre el archivo en una nueva instancia. El segundo ejemplo es similar, excepto que abre tres archivos en lugar de uno.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
