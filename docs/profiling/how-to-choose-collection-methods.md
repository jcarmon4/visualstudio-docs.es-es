---
title: Procedimiento Elegir métodos de recopilación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe046f07a27a9fdcf07fc891f7c264a45a3d61c
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744724"
---
# <a name="how-to-choose-collection-methods"></a>Procedimiento Elegir métodos de recopilación

Las Herramientas de generación de perfiles de Visual Studio admiten tres métodos de recopilación de datos de rendimiento: muestreo, instrumentación y simultaneidad. También puede utilizar el método de muestreo o de instrumentación para recopilar datos de duración y de asignación de memoria de .NET.

Puede utilizar propiedad de la sesión de rendimiento **Método** para especificar el método de recolección más adecuado para su aplicación. Puede establecer el método de colección en el Asistente de rendimiento, el Explorador de rendimiento o las páginas de propiedades de una sesión de rendimiento. Si utiliza las herramientas de línea de comandos, consulte [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md) para obtener más información.

## <a name="performance-wizard"></a>Asistente para rendimiento

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Para seleccionar un método de colección mediante el Asistente de rendimiento

- En la primera página del asistente, seleccione una de las siguientes opciones:

| Opción | Descripción |
|----------------------------| - |
| **Muestreo de la CPU** | Recopila estadísticas de la aplicación que son útiles para el análisis inicial y para analizar problemas de utilización de CPU. |
| **Instrumentación** | Recopila datos de control de tiempo detallados que son útiles para un análisis enfocado y para analizar problemas de rendimiento de entrada/salida. |
| **Asignación de memoria de .NET** | Recopila datos de asignación de memoria de .NET Framework con el método de generación de perfiles de muestreo. |
| **Simultaneidad** | Recopila datos de contención de recursos numéricos. |

## <a name="performance-explorer"></a>Explorador de rendimiento

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Para seleccionar un método de colección mediante el Explorador de rendimiento

1. En la barra de herramientas **Explorador de rendimiento**, haga clic en la flecha situada junto a la lista desplegable **Método**.

2. Haga clic en el método de recolección que prefiera.

## <a name="performance-session-property-pages"></a>Páginas de propiedades de la sesión de rendimiento

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Para seleccionar el método de muestreo o instrumentación mediante las propiedades de la sesión de rendimiento

1. En **Explorador de rendimiento**, seleccione la sesión de rendimiento.

     Un nombre de archivo de la sesión de rendimiento tiene la extensión .*psess*.

2. Haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.

3. En las **Páginas de propiedades**, haga clic en **General**.

4. Haga clic en el método de recolección que prefiera.

    - Para obtener información sobre las demás opciones que están disponibles al recopilar datos de muestreo, consulte [Recopilar estadísticas de rendimiento mediante el uso de muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Para obtener información sobre las demás opciones que están disponibles al recopilar datos de muestreo, consulte [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Para seleccionar la recopilación de datos de memoria de .NET mediante las propiedades de la sesión de rendimiento

1. En **Explorador de rendimiento**, seleccione la sesión de rendimiento.

     Un nombre de archivo de la sesión de rendimiento tiene la extensión .psess.

2. Haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.

3. En las **Páginas de propiedades**, haga clic en **General**.

4. Haga clic en **Muestreo** o **Instrumentación**.

5. Haga clic en **Recopilar información de asignación de objetos .NET** para recopilar el tamaño y el número de asignaciones de objetos de .NET Framework.

6. Haga clic en **Recopilar también la información de duración de los objetos .NET** para recopilar datos sobre las generaciones de recolección de elementos no utilizados en que se reclama la memoria del objeto (opcional).

     Para obtener información sobre las demás opciones que están disponibles al recopilar datos de memoria de .NET, vea [Recopilar datos de duración y asignación de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Para seleccionar la recopilación de datos de simultaneidad mediante las propiedades de la sesión de rendimiento

1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.

2. En las **Páginas de propiedades**, haga clic en **General**.

3. Haga clic en **Simultaneidad**.

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)
[Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)