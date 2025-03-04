---
title: Configurar análisis de código
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1b09b77eb051d32a3aabb929e9058786215cfb4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551051"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Procedimiento Configurar el análisis heredado para código administrado

En Visual Studio, puede elegir en una lista de [conjuntos de reglas](../code-quality/rule-set-reference.md) de análisis de código para aplicarlos a un proyecto de código administrado. De forma predeterminada, el **reglas mínimas recomendadas de Microsoft** se selecciona el conjunto de reglas, pero puede aplicar una regla diferente establecer si lo desea. Conjuntos de reglas pueden aplicarse a uno o varios proyectos en una solución.

Para obtener información sobre cómo configurar un conjunto de reglas para las aplicaciones Web de [ASP.net, consulte Cómo: Configurar el análisis de código para una aplicación](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)Web ASP.net.

> [!NOTE]
> Este artículo se aplica al análisis heredado y no a los [analizadores de código basados en .net Compiler Platform](use-roslyn-analyzers.md), que no ejecutan el análisis de código después de la compilación.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Configurar un conjunto de reglas para un proyecto de .NET Framework

1. Abra el **análisis de código** ficha en páginas de propiedades del proyecto. Puede hacerlo en cualquiera de las maneras siguientes:

   - En **el Explorador de soluciones**, seleccione el proyecto. En la barra de menús, seleccione **analizar** > **configurar análisis de código** > **para \<NombreDelProyecto >** .

   - Haga clic en el proyecto en **el Explorador de soluciones** y seleccione **propiedades**y, a continuación, seleccione el **análisis de código** ficha.

1. En el **configuración** y **plataforma** listas, seleccione la plataforma de destino y de configuración de compilación.

1. Para ejecutar análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione el **Habilitar análisis de código al compilar** casilla de verificación. También puede ejecutar análisis de código seleccionando **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<NombreDelProyecto >** .

1. De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias de código generado, desactive la **Suprimir resultados del código generado** casilla de verificación.

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla, sin tener que sobrescribe.

1. En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:

    - Seleccione el conjunto de reglas que desea usar.

    - Seleccione  **\<Examinar... >** encontrar establece una regla personalizada existente que no está en la lista.

    - Definir un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar conjuntos de reglas para varios proyectos en una solución

De forma predeterminada, todos los proyectos administrados de una solución se asignan los *reglas mínimas recomendadas de Microsoft* conjunto de reglas de análisis de código. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el **propiedades** cuadro de diálogo de la solución.

1. Abra la solución en Visual Studio.

2. En el **analizar** menú, seleccione **configurar análisis de código para solución**.

3. Si es necesario, expanda **propiedades comunes**y, a continuación, seleccione **configuración de análisis de código**.

4. Puede especificar un conjunto de reglas para uno o varios proyectos:

    - Para especificar un conjunto de reglas para un proyecto individual, seleccione el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla **Ctrl** y seleccione los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga presionada la tecla **MAYÚS** y haga clic en la lista de proyectos.

5. Seleccione el **Pravidel** campo de un proyecto y, a continuación, seleccione el nombre de la regla establece que desea aplicar.

## <a name="see-also"></a>Vea también

- [Referencia del conjunto de reglas Análisis de código](../code-quality/rule-set-reference.md)
- [Cómo: Configurar el análisis de código para una aplicación Web de ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)
