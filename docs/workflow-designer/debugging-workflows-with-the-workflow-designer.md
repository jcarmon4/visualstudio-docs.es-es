---
title: Depurar flujos de trabajo con el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1270e57ae6c9235311569c04ebb982157ea3b608
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949752"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Depurar flujos de trabajo con el Diseñador de flujo de trabajo

El **Workflow Designer** proporciona la capacidad para depurar flujos de trabajo y actividades personalizadas. El proceso y comportamiento son similares a la del depurador de Visual Studio de forma predeterminada.

## <a name="invoke-the-workflow-debugger"></a>Invocar al depurador de flujo de trabajo

Generalmente, los flujos de trabajo se depuran de la misma manera que los programas escritos otros lenguajes de programación de Visual Studio. Puede iniciar el depurador de flujo de trabajo de las siguientes maneras:

- Seleccione **asociar al proceso** en el **depurar** menú para seleccionar el proceso de host para la instancia de flujo de trabajo. Este procedimiento es igual que el que se utiliza para adjuntar a un proceso de host en código administrado.

- Presione **F5** para iniciar la ejecución de una instancia del flujo de trabajo o continuar ejecutándose después de que se ha alcanzado un punto de interrupción.

- Usar depuración remota. Para obtener información sobre el uso de la depuración remota, vea [Cómo: Habilitar la depuración remota](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Si la aplicación de flujo de trabajo tiene como destino el x86 arquitectura y se hospeda en un equipo que ejecuta un sistema operativo de 64 bits, la depuración remota no funcionará a menos que Visual Studio está instalado en el equipo remoto o el destino de la aplicación de flujo de trabajo se cambia a  **Cualquier CPU**.

## <a name="step-through-code"></a>Examinar el código

- **El paso**: Ir a una actividad presionando **F11**. El depurador avanza paso a paso por todos los controladores definidos. Si no hay ningún controlador definido, puede ejecutar la actividad paso a paso o, en las actividades compuestas, que contienen otras actividades, puede entrar en la primera actividad en ejecución.

- **Paso para salir:** Salir de una actividad presionando **MAYÚS**+**F11**. Al salir paso a paso de una actividad, se ejecutan hasta el final la actividad actual y todas sus actividades del mismo nivel. A continuación, el depurador se interrumpe en el elemento primario de la actividad actual. Al salir paso a paso de un controlador del código, el depurador se interrumpe en la actividad a la que está asociado el controlador.

- **Paso a paso**: Paso a través de una actividad presionando **F10**. Al ejecutar paso a paso por procedimientos una actividad compuesta, el depurador se interrumpe en el primer elemento secundario ejecutable de la actividad compuesta. Al ejecutar paso a paso por procedimientos una actividad no compuesta, como <xref:System.Activities.Statements.Assign>, el depurador ejecuta la actividad y sus controladores asociados y se interrumpe en la actividad siguiente. Si la actividad que se ejecuta es la última actividad secundaria de una actividad compuesta, después de la ejecución el depurador se interrumpe en la actividad primaria.

## <a name="debug-with-f5"></a>Depurar con F5

Si va a compilar una aplicación de consola de flujo de trabajo, presione **F5** para comenzar la depuración en su aplicación y el flujo de trabajo. Si va a compilar una biblioteca de actividades por sí mismo, debe especificar una aplicación host ejecutable como proyecto de inicio. Para establecer un proyecto de inicio en **el Explorador de soluciones**, haga clic en el nombre del proyecto del host y seleccione **establecer como proyecto de inicio**.