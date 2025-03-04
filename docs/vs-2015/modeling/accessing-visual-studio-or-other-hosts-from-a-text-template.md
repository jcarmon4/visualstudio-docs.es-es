---
title: Obtener acceso a Visual Studio 2015 u otros hosts desde una plantilla de texto | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872005"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Tener acceso a Visual Studio u otros hosts desde una plantilla de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una plantilla de texto, puede usar los métodos y las propiedades que expone el host que ejecuta la plantilla, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]como.

 Esto se aplica a las plantillas de texto normales, no a las plantillas de texto preprocesadas.

## <a name="obtaining-access-to-the-host"></a>Obtención de acceso al host

Establezca `hostspecific="true"` en la `template` Directiva. Esto le permite usar `this.Host`, que tiene el tipo [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Este tipo tiene miembros que puede usar, por ejemplo, para resolver nombres de archivo y registrar errores.

### <a name="resolving-file-names"></a>Resolver nombres de archivo
 Para buscar la ruta de acceso completa de un archivo con respecto a la plantilla de texto, utilice este. Host. ResolvePath ().

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

### <a name="displaying-error-messages"></a>Mostrar mensajes de error
 En este ejemplo registra los mensajes al transformar la plantilla. Si el host es [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se agregan a la ventana de error.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>

```

## <a name="using-the-visual-studio-api"></a>Uso de la API de Visual Studio
 Si está ejecutando una plantilla de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede utilizar `this.Host` para obtener acceso a los servicios proporcionados por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y cualquier paquete o extensión que se cargue.

 Establecer hostspecific = "true" y convertir `this.Host` a <xref:System.IServiceProvider>.

 Este ejemplo obtiene la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API, <xref:EnvDTE.DTE>, como un servicio:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

```

## <a name="using-hostspecific-with-template-inheritance"></a>Usar hostSpecific con herencia de plantilla
 Especificar `hostspecific="trueFromBase"` si también usa el `inherits` atributo, y si se hereda de una plantilla que especifica `hostspecific="true"`. Esto evita una advertencia del compilador en el efecto de `Host` que la propiedad se ha declarado dos veces.
