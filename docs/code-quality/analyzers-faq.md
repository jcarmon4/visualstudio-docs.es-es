---
title: EditorConfig frente a analizadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53bd2139d5b81ed743cdfd92fe76cb575dcc6487
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547894"
---
# <a name="code-analysis-faq"></a>Preguntas más frecuentes sobre análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P**: ¿Debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**R**: Los archivos. editorconfig y de análisis de código funcionan en mano. Al definir estilos de código [en un archivo. editorconfig](../ide/editorconfig-code-style-settings-reference.md) o en la página de [Opciones editor de texto](../ide/code-styles-and-code-cleanup.md) , en realidad está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig también se pueden usar para configurar algunos paquetes del analizador de terceros, como los analizadores de [FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**P**: ¿Debo configurar mis analizadores mediante un conjunto de reglas o un archivo. editorconfig?

**R**: Los conjuntos de reglas y los archivos. editorconfig son maneras mutuamente excluyentes de configurar analizadores. Pueden coexistir. Los [conjuntos de reglas](analyzer-rule-sets.md) permiten habilitar y deshabilitar reglas y establecer su gravedad. Los archivos EditorConfig ofrecen otras maneras de configurar reglas. En el caso de los analizadores de FxCop, los archivos. editorconfig permiten [definir los tipos de código que se van a analizar](fxcop-analyzer-options.md). En el caso de los analizadores integrados en Visual Studio, los archivos. editorconfig permiten [definir los estilos de código preferidos](../ide/editorconfig-code-style-settings-reference.md) para un código base.

Además de los conjuntos de reglas y los archivos. editorconfig, algunos analizadores de terceros se configuran mediante el uso de archivos de texto marcados C# como [archivos adicionales](../ide/build-actions.md#build-action-values) para los compiladores de y VB.

> [!NOTE]
> Los archivos EditorConfig no se pueden usar para configurar el análisis heredado, mientras que los conjuntos de reglas pueden.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P**: ¿Funciona el análisis de código basado en .NET Compiler Platform en compilaciones de integración continua (CI)?

**R**: Sí. En el caso de los analizadores que se instalan desde un paquete NuGet, esas reglas se [aplican en el momento](roslyn-analyzers-overview.md#build-errors)de la compilación, incluso durante una compilación de CI. Los analizadores usados en las compilaciones de elementos de configuración respetan la configuración de reglas de ambos [conjuntos de reglas](analyzer-rule-sets.md) y [archivos. editorconfig](configure-fxcop-analyzers.md). Actualmente, los analizadores de código que están integrados en Visual Studio no están disponibles como un paquete NuGet, por lo que estas reglas no se pueden aplicar en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores de IDE frente a StyleCop

**P**: ¿Cuál es la diferencia entre los analizadores de código del IDE de Visual Studio y los analizadores de StyleCop?

**R**: El IDE de Visual Studio incluye analizadores integrados que buscan problemas de estilo de código y calidad. Estas reglas le ayudan a usar las nuevas características del lenguaje a medida que se introducen y mejoran el mantenimiento del código. Los analizadores de IDE se actualizan continuamente con cada versión de Visual Studio.

Los analizadores de [StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete NuGet que comprueban la coherencia de estilo en el código. En general, las reglas de StyleCop permiten establecer preferencias personales para un código base sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente al análisis heredado

**P**: ¿Cuál es la diferencia entre el análisis heredado y el análisis de código basado en .NET Compiler Platform?

**R**: el análisis de código basado en .net Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, consulte [preguntas más frecuentes sobre](fxcop-analyzers-faq.md) [el análisis basado en .net Compiler Platform frente al análisis heredado](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) y los analizadores de FxCop.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)