---
title: Procedimiento Crear un informe de comparación del generador de perfiles desde un símbolo del sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11a3850073068cf280901a6948565329e83f4629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973961"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Procedimiento Crear un informe de comparación del generador de perfiles desde un símbolo del sistema
Puede generar un informe de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que compara los datos de rendimiento de dos archivos de datos de generación de perfiles (.*vsp* o .*vsps*). El informe muestra las diferencias, reducciones de rendimiento y mejoras producidas de una sesión de generación de perfiles a la otra. Los valores del informe presentan el delta (o cambio) de la base de referencia del primer archivo que especifique. Este delta se calcula al determinar la diferencia entre el valor anterior, que es el valor de la base de referencia, y el valor del resultado del nuevo análisis. Las comparaciones de datos del generador de perfiles pueden basarse en las funciones del código, los módulos de la aplicación, las líneas, los punteros de instrucciones (IP) y los tipos.

 Para obtener una lista de los identificadores de las categorías de comparación y los campos, escriba la siguiente línea de comandos:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Use la sintaxis siguiente para crear el informe de comparación:

 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [ **/** `Options`]

 Puede agregar opciones de la tabla siguiente a la línea de comandos **VSPerfReport /diff**.

|Opción|Descripción|
|------------|-----------------|
|**DiffThreshold:** [*Value*]|Omita la diferencia si está por debajo de este valor de umbral de porcentaje. Además, no aparecen nuevos datos que tengan valores por debajo de este umbral.|
|**DiffTable:** *TableName*|Use esta tabla para comparar archivos. De forma predeterminada, se usa la tabla de funciones. Especifique el identificador que aparece en **VSPerfReport /querydifftables**.|
|**DiffColumn:** *ColumnName*|Use esta columna para comparar valores. De forma predeterminado, se usa la columna de porcentaje de muestras exclusivas. Especifique el identificador que aparece en **VSPerfReport /querydifftables**.|