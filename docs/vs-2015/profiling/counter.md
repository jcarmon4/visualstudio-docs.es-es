---
title: Contador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5da78c33af599accf5ff3a2e09a9afb52982573a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149278"
---
# <a name="counter"></a>Contador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Counter** recopila datos de los contadores de rendimiento del procesador (hardware).  
  
- Si usa el método de generación de perfiles mediante muestreo, **Counter** especifica el contador de rendimiento del procesador y el número de eventos de contador que se usarán como intervalo de muestreo. Cuando se usa el muestreo solamente se puede especificar un contador.  
  
- Si usa el método de generación de perfiles mediante instrumentación, el número de eventos de contador que se produjeron en el intervalo entre los eventos de colección anterior y actual figuran como campos independientes en los informes del generador de perfiles. Cuando se usa la instrumentación se pueden especificar varias opciones **Counter**.  
  
  Cada tipo de procesador tiene su propio conjunto de contadores de rendimiento de hardware. El generador de perfiles define un conjunto de contadores de rendimiento genéricos que son comunes a casi todos los procesadores. Para enumerar los contadores genéricos y específicos del procesador del equipo, utilice el comando **QueryCounters** de VSPerfCmd.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Name`  
 El nombre del contador. Utilice la opción **/QueryCounters** de VSPerfCmd.exe para enumerar los nombres de los contadores disponibles en el equipo.  
  
 `Reload`  
 El número de eventos de contador en el intervalo de muestreo. No utilice esta opción con el método de instrumentación.  
  
 `FriendlyName`  
 (Opcional) La cadena que se utiliza en lugar de `Name` en los encabezados de columna de los informes y las vistas del generador de perfiles.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción Counter solo puede utilizarse con una de las siguientes opciones:  
  
 **Start:** `Trace`  
 Inicializa el generador de perfiles para utilizar el método de instrumentación.  
  
 **Launch:** `AppName`  
 Inicia la aplicación específica y el generador de perfiles. El generador de perfiles se debe inicializar para utilizar el método de muestreo.  
  
 **Attach:** `PID`  
 Inicia el generador de perfiles y lo adjunta al proceso especificado por el identificador de proceso. El generador de perfiles se debe inicializar para utilizar el método de muestreo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo del método de muestreo se muestra cómo muestrear una aplicación cada 1000 apariciones del contador genérico NonHaltedCycles del generador de perfiles.  
  
 En el ejemplo del método de instrumentación se muestra cómo inicializar el generador de perfiles para recopilar eventos del contador L2InstructionFetches. El nombre de contador L2InstructionFetches es específico del procesador.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>Otras referencias  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
