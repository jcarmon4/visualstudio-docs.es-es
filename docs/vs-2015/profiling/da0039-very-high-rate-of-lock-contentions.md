---
title: 'DA0039: Frecuencia muy alta de contenciones de bloqueo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14192551543bdfd5cc352ed4c7c45fa95630dcd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156427"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Frecuencia muy alta de contenciones de bloqueo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [DA0039: Muy alta frecuencia de contenciones de bloqueo](https://docs.microsoft.com/visualstudio/profiling/da0039-very-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|Identificador de regla|DA0039|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Instrumentación<br /><br /> Memoria de .NET|  
|Message|Hay una frecuencia muy alta de contenciones de bloqueo de .NET. Investigue la razón de esta contención de bloqueo ejecutando un perfil de simultaneidad.|  
|Tipo de regla|Advertencia|  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 25 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Causa  
 Los datos de rendimiento del sistema recopilados con los datos de generación de perfiles indican que se produjo una tasa excesivamente alta de contenciones de bloqueo durante la ejecución de la aplicación. Considere la posibilidad de volver a generar perfiles con el método de generación de perfiles de simultaneidad para encontrar la causa de la contención.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los bloqueos se utilizan para proteger las secciones críticas de código que un subproceso debe ejecutar en serie a la vez en una aplicación con múltiples subprocesos. Common Language Run-time (CLR) de Microsoft .NET proporciona un conjunto completo de sincronización y primitivas de bloqueo. Por ejemplo, el lenguaje C# admite una instrucción de bloqueo (SyncLock en Visual Basic). Una aplicación administrada puede llamar a la `Monitor.Enter` y `Monitor.Exit` métodos en el espacio de nombres System.Threading para adquirir y liberar un bloqueo directamente. .NET Framework admite sincronización adicional y primitivas de bloqueo, incluidas las clases que admiten las exclusiones mutuas, ReaderWriterLock y semáforos. Para obtener más información, consulte [Información general sobre las primitivas de sincronización](http://go.microsoft.com/fwlink/?LinkId=177867) en la Guía del desarrollador de .NET Framework en el sitio web de MSDN. Las clases de .NET Framework están superpuestas a los servicios de sincronización de nivel inferior integrados en el sistema operativo Windows. Estos incluyen objetos de sección crítica y muchas funciones de espera y señalización de eventos diferentes. Para obtener más información, consulte la sección [Sincronización](http://go.microsoft.com/fwlink/?LinkId=177869) de Desarrollo para Win32 y COM en MSDN Library  
  
 Subyacentes a las clases de .NET Framework y los objetos nativos de Windows que se usan para la sincronización y el bloqueo, se encuentran ubicaciones de memoria compartida que se deben cambiar mediante operaciones de bloqueo. Las operaciones de bloqueo utilizan instrucciones específicas del hardware que operan en ubicaciones de memoria compartida para cambiar su estado mediante operaciones atómicas. Se garantiza que las operaciones atómicas sean coherentes en todos los procesadores del equipo. Los bloqueos y WaitHandles son objetos .NET que utilizan automáticamente las operaciones de bloqueo cuando se establecen o restablecen. Puede haber otras estructuras de datos de memoria compartida en la aplicación que también requieran que utilice operaciones de bloqueo para que se actualicen de una manera segura para subprocesos. Para obtener más información, consulte [Operaciones de bloqueo](http://go.microsoft.com/fwlink/?LinkId=177870) en la sección de .NET Framework de MSND Library  
  
 La sincronización y el bloqueo son mecanismos utilizados para garantizar que las aplicaciones multi-threading se ejecuten correctamente. Cada subproceso de una aplicación multi-threading es una unidad de ejecución independiente programada de forma independiente por el sistema operativo. Cada vez que un subproceso que intenta adquirir un bloqueo se retrasa porque otro subproceso está reteniendo el bloqueo, se produce una contención de bloqueo.  
  
 Los bloqueos suelen estar anidados. El anidamiento se produce cuando un subproceso que ejecuta una sección crítica realiza una función que a continuación exige otro bloqueo. Cierta cantidad de anidamiento de bloqueo es inevitable. La sección crítica puede llamar a un método de .NET Framework que se basa en los bloqueos para asegurarse de que es seguro para subprocesos. Una llamada de alguna sección crítica de su aplicación en un método de Framework que también bloquee mediante un controlador de bloqueo diferente hace que los bloqueos se aniden. Las condiciones de bloqueo anidadas pueden provocar problemas de rendimiento que son considerablemente difíciles de aclarar y corregir.  
  
 Esta regla se desencadena cuando las mediciones tomadas durante una generación de perfiles indican que hay una cantidad excesivamente alta de contención de bloqueo. Las contenciones de bloqueo retrasan la ejecución de subprocesos que están esperando para adquirir el bloqueo. Deberían investigarse incluso las cantidades bastante pequeñas de contención de bloqueo en pruebas unitarias o en pruebas de carga que se ejecuten en hardware de gama baja.  
  
> [!NOTE]
> Cuando la frecuencia de contenciones de bloqueo notificadas en los datos de generación de perfiles es considerable pero no excesiva, se desencadena el mensaje informativo [DA0038: Alta tasa de contenciones de bloqueo](../profiling/da0038-high-rate-of-lock-contentions.md) mensaje de información que se desencadena en lugar de este mensaje de advertencia.  
  
## <a name="how-to-investigate-a-warning"></a>Cómo investigar una advertencia  
 Haga doble clic en el mensaje para navegar a la vista [Marcas](../profiling/marks-view.md) de los datos de generación de perfiles.  Busque la columna **LocksAndThreads de .NET CLR\Tasa de contención por segundo**. Determine si hay fases concretas de ejecución del programa en que la contención de bloqueo sea mayor que en otras.  
  
 Esta regla solo se desencadena cuando no está utilizando el método de generación de perfiles de simultaneidad. El método de generación de perfiles de simultaneidad es la mejor herramienta para diagnosticar problemas de rendimiento relacionados con la contención de bloqueo en la aplicación. Recopile datos de generación de perfiles de simultaneidad para comprender el comportamiento de bloqueo de la aplicación. Esto incluye entender qué bloqueos compiten fuertemente, cuánto se retrasa el tiempo de ejecución de subprocesos a la espera de los bloqueos que compiten y qué código concreto hay implicado. Perfiles de simultaneidad recopilan datos en todas las contenciones de bloqueo, incluidos el comportamiento de bloqueo de las instalaciones de Windows nativas, las clases de .NET Framework y cualquier otra biblioteca de terceros las referencias de la aplicación. Para obtener información sobre la generación de perfiles de simultaneidad del IDE de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consulte [Recopilar datos de simultaneidad de subprocesos y procesos](../profiling/collecting-thread-and-process-concurrency-data.md). Para acceder a los vínculos para obtener información sobre la generación de perfiles de simultaneidad desde la línea de comandos, consulte la sección **Uso del método de simultaneidad para recopilar datos de contención de recursos y actividad de subprocesos** de [Uso de métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
