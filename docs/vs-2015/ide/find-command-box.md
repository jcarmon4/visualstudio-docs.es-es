---
title: Cuadro Buscar comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8bddc27eb4a59b65796c7837ae4561e5d56a5d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160675"
---
# <a name="findcommand-box"></a>Buscar/Comando (cuadro)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar texto y ejecutar comandos de Visual Studio desde el cuadro **Buscar comando**. El cuadro **Comando/Buscar** todavía está disponible como un control de la barra de herramientas, pero ya está visible de manera predeterminada. Puede mostrar el cuadro **Comando/Buscar** pulsando **Agregar o quitar botones** en la barra de herramientas **Estándar** y, después, pulsar **Buscar**.  
  
 Para ejecutar un comando de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], precédalo de un signo mayor que (>).  
  
 El cuadro **Buscar comando** conserva los últimos 20 elementos escritos y los muestra en una lista desplegable. Puede navegar por la lista mediante el uso de las teclas de dirección.  
  
 ![Cuadro Buscar comando](../ide/media/findcommandbox.png "FindCommandBox")  
Buscar/Comando (cuadro)  
  
## <a name="searching-for-text"></a>Buscar texto  
 De forma predeterminada, cuando se especifica texto en el cuadro **Buscar comando** y se presiona la tecla ENTRAR, Visual Studio busca la ventana de herramientas o documento actuales con las opciones especificadas en el cuadro de diálogo **Buscar en archivos**. Para obtener más información, consulta [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Escribir comandos  
 Para usar el cuadro **Buscar comando** para emitir un solo comando o alias de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en lugar de buscar texto, escriba el comando de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], precedido de un signo mayor que (>). Por ejemplo:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 También puede usar la ventana Comandos para escribir y ejecutar uno o varios comandos. Algunos comandos o alias pueden escribirse y ejecutarse por sí solos; otros requieren argumentos en su sintaxis. Para obtener una lista de los comandos que tienen argumentos, vea [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Caracteres de escape  
 Un carácter de intercalación (^) en una línea de comandos significa que el carácter que le sigue se interpreta literalmente, en lugar de interpretarse como un carácter de control. Esto se puede usar para insertar comillas rectas ("), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de parámetro o modificador, con la excepción de los nombres de los modificadores. Por ejemplo,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 El símbolo de intercalación funciona igual tanto si está dentro como fuera de unas comillas. Si el símbolo de intercalación es el último carácter de la línea, se ignora.  
  
## <a name="see-also"></a>Otras referencias  
 [Ventana Comandos](../ide/reference/command-window.md)   
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
