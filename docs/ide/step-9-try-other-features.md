---
title: 'Paso 9: Probar otras características'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24637ba56c3dfa2d9ce9c7e70452bcdc6788b51b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918713"
---
# <a name="step-9-try-other-features"></a>Paso 9: Probar otras características
Para aprender más, pruebe a cambiar los iconos y los colores, y agregue un temporizador de juego y sonidos. Para que el juego sea más desafiante, pruebe a aumentar el tamaño del tablero y a ajustar el temporizador.

Para descargar una versión completa del ejemplo, consulte [Complete Matching Game tutorial sample](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Ejemplo del tutorial Crear un juego de formar parejas).

## <a name="to-try-other-features"></a>Para probar otras características

- Reemplace los iconos y colores con los que prefiera.

    > [!TIP]
    > Observe la propiedad [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) de la etiqueta.

- Agregue un temporizador de juego que mida el tiempo que necesita el jugador para ganar.

    > [!TIP]
    > Para ello, agregue una etiqueta que muestre el tiempo transcurrido en el formulario sobre <xref:System.Windows.Forms.TableLayoutPanel>, y agregue otro temporizador al formulario que mida el tiempo. Utilice el código para iniciar el temporizador cuando el jugador inicie el juego, y detenga el temporizador después de que coincidan los dos iconos.

- Agregue un sonido para cuando el jugador encuentre una coincidencia, otro sonido para cuando destape dos iconos que no coincidan y un tercer sonido para cuando el programa vuelva a ocultar los iconos.

    > [!TIP]
    > Para reproducir sonido, use el espacio de nombres <xref:System.Media>. Consulte [Play Sounds in Windows Forms App (C#)](http://youtu.be/qOh4ooHg1UU) [Reproducir sonidos en la aplicación de Windows Forms (C# )] o [How To Play Audio In Visual Basic](http://youtu.be/-4oPDeQrtMs) (Cómo reproducir audio en Visual Basic) para obtener más información.

- Aumente el tamaño del tablero para complicar más el juego.

    > [!TIP]
    > Necesitará hacer algo más que agregar filas y columnas a TableLayoutPanel: también deberá tener en cuenta el número de iconos que cree.

- Para que el juego sea más desafiante, oculte el primer icono si el jugador es demasiado lento al reaccionar y no elige el segundo icono antes de que pase una cantidad de tiempo concreta.

## <a name="to-continue-or-review"></a>Para continuar o revisar

- Si se bloquea o tiene preguntas de programación, envíe la pregunta a uno de los Foros de MSDN. Consulte el [Foro de Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) y el [Foro de Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- Dispone de excelentes recursos de aprendizaje en vídeo gratuitos. Para obtener más información sobre la programación en Visual Basic, vea [Visual Basic Fundamentals: Development for absolute beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Fundamentos de Visual Basic: desarrollo para principiantes absolutos). Para obtener más información sobre la programación en Visual C#, vea [C# fundamentals: Development for absolute beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Fundamentos de C#: desarrollo para principiantes absolutos).

- Para volver al paso anterior del tutorial, vea [Paso 8: Agregar un método para comprobar si el jugador ganó](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
