---
title: Compatibilidad con Ngen en VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24f1b0a26875bbbf8dfc4ac7db1049f7309d9aa2
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891119"
---
# <a name="ngen-support-in-vsix-v3"></a>Compatibilidad con Ngen en VSIX v3

Con Visual Studio 2017 y las nuevas VSIX v3 (versión 3) manifiesto de la extensión formato de extensión a los desarrolladores ahora pueden "ngen" sus ensamblados en tiempo de instalación.

A continuación es un extracto de MSDN que se explica qué "ngen" hace:

>El generador de imágenes nativas (*Ngen.exe*) es una herramienta que mejora el rendimiento de las aplicaciones administradas. *Ngen.exe* crea imágenes nativas, que son archivos que contienen código máquina compilado específico del procesador y los instala en la caché de imágenes nativas del equipo local. El runtime puede usar imágenes nativas de la memoria caché en lugar de usar el compilador Just-In-Time (JIT) para compilar el ensamblado original.
>
>desde [Ngen.exe (generador de imágenes nativas)](/dotnet/framework/tools/ngen-exe-native-image-generator)

A fin "ngen" un ensamblado, la extensión VSIX debe instalarse "por instancia por equipo". Esta opción puede habilitarse activando la casilla "todos los usuarios" el `extension.vsixmanifest` diseñador:

![Compruebe todos los usuarios](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Habilitación de Ngen

Para habilitar ngen para un ensamblado, puede usar el **propiedades** ventana de Visual Studio.

Hay 4 propiedades que se pueden establecer:

1. **Ngen** (Boolean): si es true, el instalador de Visual Studio le "ngen" del ensamblado.
2. **Aplicación Ngen** (cadena) - Ngen proporciona la oportunidad de usar una aplicación *app.config* archivo con el fin de resolver las dependencias de ensamblado. Este valor debe establecerse en una aplicación cuya *app.config* que desea usar (relativa al directorio de instalación de Visual Studio).
3. **Arquitectura Ngen** (enumeración): la arquitectura para compilar el ensamblado de forma nativa. Las opciones son: una. B NotSpecified. X86 c. X64 d. Todo
4. **Prioridad Ngen** (entero entre 1 y 3) - nivel de la prioridad de Ngen está documentada en [niveles de prioridad de Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Este es un vistazo a la **propiedades** ventana en acción:

![Ngen en Propiedades](media/ngen-in-properties.png)

Esto agregará los metadatos para la referencia de proyecto dentro del proyecto VSIX *.csproj* archivo:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="extra-information"></a>Información adicional

Se aplican los cambios de propiedad diseñador a algo más que las referencias de proyecto; puede establecer los metadatos de Ngen para los elementos dentro de su proyecto (con los mismos métodos que se ha descrito anteriormente) de siempre que los elementos son ensamblados .NET.