---
title: 'DA0503: Promedio de espacio de trabajo en bytes para el proceso del que se está generando el perfil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2453b73d7dae0a6a53130156cdb1ce35d38d43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935993"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Promedio de espacio de trabajo en bytes para el proceso del que se está generando el perfil

|||
|-|-|
|Identificador de regla|DA0503|
|Categoría|Supervisión de recursos|
|Método de generación de perfiles|Todas|
|Mensaje|Esta información se recopiló únicamente con fines informativos. El contador del espacio de trabajo del proceso mide el uso de memoria física que hace el proceso del que está generando perfiles. El valor notificado es el promedio calculado de todos los intervalos de medición.|
|Tipo de regla|Información|

 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Este mensaje indica la cantidad media de memoria física que el proceso está utilizando actualmente en bytes (el espacio de trabajo). El espacio de trabajo del proceso representa las páginas del espacio de direcciones de proceso que residen actualmente en la memoria física.

 El valor notificado incluye páginas residentes de los segmentos de memoria compartida a las que el proceso ha hecho referencia. Los archivos DLL compartidos a los que el proceso hace referencia se incluyen en los segmentos de memoria compartida que se cuentan. El valor del espacio de trabajo del proceso puede ser mayor que la cantidad de memoria virtual que el proceso ha asignado debido a los segmentos de memoria compartida.

 El valor notificado es el promedio de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil.

 El tamaño del espacio de trabajo del proceso refleja cuánta memoria virtual está usando activamente el proceso. También se ve afectado por la cantidad de memoria física (o RAM) disponible para ejecutar la aplicación y la contención para esa memoria física de otros procesos en ejecución. Si se limita la memoria física, el valor del espacio de trabajo del proceso tenderá a variar considerablemente a medida que los sistemas operativos recorten periódicamente las páginas relativamente inactivas de los espacios de trabajo del proceso para intentar equilibrar el uso de memoria entre los procesos activos.

 Para obtener más información sobre los espacios de trabajo del proceso, consulte [Espacio de trabajo](http://go.microsoft.com/fwlink/?LinkId=177830) en la documentación de administración de memoria de Windows de MSDN.

## <a name="how-to-use-rule-data"></a>Cómo usar los datos de la regla
 Utilice el valor de la regla para comparar el rendimiento de distintas versiones o compilaciones del programa o para entender el rendimiento de la aplicación en otros escenarios de generación de perfiles diferentes.

 Haga doble clic en el mensaje en la ventana Lista de errores para navegar a la [vista Marcas](../profiling/marks-view.md) de los datos de generación de perfiles. Busque las columnas **Process\Working Set** y **Memory\Pages/sec**. Compare las dos columnas y determine si hay fases concretas de la ejecución del programa que se encuentren asociadas a una actividad de E/S de paginación mayor.