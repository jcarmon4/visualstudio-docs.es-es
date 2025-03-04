---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50b2e269ec292aaf37b8d0c707fa27ff8268a1f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969713"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
La opción **GC** habilita la recopilación de datos de asignación de memoria de .NET Framework y de duración de objetos. La opción **GC** solo puede usarse con el método de generación de perfiles de muestreo y únicamente con la opción **Launch**.

 Al utilizar la opción **GC**, el comando **/sampleon** de VSPerfClrEnv no es necesario.

 Si no se especifica ningún parámetro, o si se especifica el parámetro **Asignación**, solo se recopilan datos de asignación de memoria de .NET Framework. Si se especifica el parámetro **Duración**, se recopilan datos de asignación de memoria de .NET Framework y de duración de objetos de .NET Framework.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parámetros
 **Allocation** Valor predeterminado. Recopila datos de asignación de memoria de .NET Framework.

 **Lifetime** Recopila datos de asignación de memoria de .NET Framework y de duración de objetos de .NET Framework.

## <a name="required-options"></a>Opciones necesarias
 La opción **GC** solo se puede usar con la opción **Launch**.

 **Launch:** `AppName` Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se inicia una aplicación y se recopilan datos de asignación de memoria de .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)