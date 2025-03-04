---
title: Especificar la ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48ac65ef8fb7a67783a3c9c5a9652accf86821fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979840"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Especificar la ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles

La ruta de acceso a las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no se agrega a la variable de entorno PATH. En equipos de 32 bits, las herramientas se encuentran en un único directorio. En los equipos de 64 bits, están disponibles las versiones de 32 y 64 bits de las herramientas de generación de perfiles.

## <a name="32-bit-computers"></a>Equipos de 32 bits
::: moniker range=">=vs-2019"
 Para el código nativo, las API del generador de perfiles de Visual Studio se encuentran en *VSPerf.dll*. El archivo de encabezado (*VSPerf.h*) y la biblioteca de importación (*VSPerf.lib*) se encuentran en el directorio *Microsoft Visual Studio\2019\Team Tools\Performance Tools\PerfSDK*.
::: moniker-end
::: moniker range="vs-2017"
 Para el código nativo, las API del generador de perfiles de Visual Studio se encuentran en *VSPerf.dll*. El archivo de encabezado (*VSPerf.h*) y la biblioteca de importación (*VSPerf.lib*) se encuentran en el directorio *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.
::: moniker-end

 Para el código administrado, las API del generador de perfiles se encuentran en *Microsoft.VisualStudio.Profiler.dll*. Este archivo DLL se encuentra en el directorio *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>Equipos de 64 bits

En los equipos de 64 bits, especifique la ruta de acceso según la plataforma de destino de la aplicación para la que se genera el perfil.

::: moniker range=">=vs-2019"
- En las aplicaciones de 32 bits, el directorio de herramientas de generador de perfiles predeterminado es:

     (nativo) *Microsoft Visual Studio\2019\Team Tools\Performance Tools\PerfSDK* (managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- En las aplicaciones de 64 bits, el directorio de herramientas de generador de perfiles predeterminado es:

     (nativo) *Microsoft Visual Studio\2019\Team Tools\Performance Tools\x64\PerfSDK* (managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end

::: moniker range="vs-2017"
- En las aplicaciones de 32 bits, el directorio de herramientas de generador de perfiles predeterminado es:

     (nativo) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- En las aplicaciones de 64 bits, el directorio de herramientas de generador de perfiles predeterminado es:

     (nativo) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end