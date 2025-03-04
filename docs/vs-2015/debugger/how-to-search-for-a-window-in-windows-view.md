---
title: Procedimiento Buscar una ventana de Windows Vista | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439077"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedimiento Buscar una ventana en la vista Ventanas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar una ventana concreta en la vista de Windows mediante su identificador, título, clase o una combinación de su título y la clase como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrará los atributos de la ventana seleccionada en el árbol de la ventana.  
  
 Inicio con el árbol expandido en el segundo nivel (todas las ventanas que son elementos secundarios del escritorio), para que pueda identificar nivel del escritorio de windows por su nombre de clase y el título. Una vez que haya elegido una ventana de nivel de escritorio, puede expandir ese nivel para buscar una ventana secundaria concreta.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Para buscar una ventana en la vista de Windows  
  
1. Organizar las ventanas por lo que ese Spy ++ la [Windows Vista](../debugger/windows-view.md) ventana y la ventana de destino están visibles.  
  
2. Desde el **búsqueda** menú, elija **Buscar ventana**.  
  
     El [cuadro de diálogo Buscar ventana](../debugger/window-search-dialog-box.md) se abre.  
  
    > [!TIP]
    > Para reducir la confusión en la pantalla, seleccione el **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++ y deja solo la **Buscar ventana** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.  
  
3. Arrastre el **herramienta de búsqueda** a través de la ventana de destino. A medida que arrastra la herramienta, el **Buscar ventana** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
     -O bien-  
  
     Si conoce el identificador de la ventana que desee (por ejemplo, desde el depurador), puede escribirla en el **controlar** cuadro.  
  
     -O bien-  
  
     Si conoce el título o una clase de la ventana que desea, puede escribir en el **título** y **clase** cuadros de texto y borre el **controlar** cuadro de texto.  
  
4. Elija **seguridad** o **abajo** para la dirección inicial de la búsqueda.  
  
5. Haga clic en **Aceptar**.  
  
     Si se encuentra una ventana coincidente, se resalta en el [Windows Vista](../debugger/windows-view.md) ventana.
