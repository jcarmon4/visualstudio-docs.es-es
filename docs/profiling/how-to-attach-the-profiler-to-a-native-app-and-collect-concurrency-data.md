---
title: Asociación del generador de perfiles a una aplicación nativa para recopilar datos de simultaneidad
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 180c520b3bec53610f539ecb8ac21f86b5c5aa38
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261441"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Procedimiento para asociar el generador de perfiles a una aplicación nativa independiente y recopilar datos de simultaneidad mediante la línea de comandos
En este tema se describe cómo usar las herramientas de línea de comandos de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a una aplicación independiente nativa (C/C++) en ejecución y recopilar datos de contención de subprocesos.

> [!NOTE]
> Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana Símbolo del sistema o agregarla al propio comando.

 Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto a la aplicación y debe apagarse explícitamente.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Adjuntar el generador de perfiles a una aplicación nativa en ejecución

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Para adjuntar el generador de perfiles a una aplicación nativa en ejecución

1. En un símbolo del sistema, escriba el siguiente comando:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     Puede usar cualquiera de las opciones de la tabla siguiente con la opción **/start:concurrency**.

    |Opción|Descripción|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`Username`|Especifica el dominio y el nombre de usuario opcionales de la cuenta a la que se va a conceder acceso al generador de perfiles.|
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|

2. Adjunte el generador de perfiles a la aplicación de destino escribiendo el comando siguiente:

     **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`}

     `PID` especifica el identificador de proceso de la aplicación de destino. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.

## <a name="control-data-collection"></a>Controlar la recopilación de datos
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de *VSPerfCmd.exe*. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.

#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos

- Los pares de opciones de la tabla siguiente inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.

    |Opción|Descripción|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia ( **/globalon**) o detiene ( **/globaloff**) la recolección de datos para todos los procesos.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia ( **/processon**) o detiene ( **/processoff**) la recolección de datos para el proceso que especifica el identificador de proceso (`PID`).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (*ProcName*). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|

## <a name="end-the-profiling-session"></a>Finalización de la sesión de generación de perfiles
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Para dejar de recopilar datos de una aplicación que se perfila con el método de muestreo, puede cerrar la aplicación o invocar la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.

#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles

1. Desasocie el generador de perfiles de la aplicación de destino cerrándolo o escribiendo el siguiente comando:

     **VSPerfCmd /detach**

2. Escriba el siguiente comando para apagar el generador de perfiles:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)