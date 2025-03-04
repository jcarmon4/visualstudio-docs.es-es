---
title: 'CA3010: Revisión de código en busca de vulnerabilidades de inyección de XAML'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 965e0d800bd7c725236d96499d2bf2d441b40412
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841088"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Revisión de código en busca de vulnerabilidades de inyección de XAML

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|Identificador de comprobación|CA3010|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Solicitud HTTP no sea de confianza de entrada alcanza un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> Load (método).

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento a ataques de inyección de código XAML. XAML es un lenguaje de marcado que representa directamente la creación de instancias y la ejecución de objetos. Esto significa que los elementos creados en XAML pueden interactuar con los recursos del sistema (por ejemplo, red acceso y el archivo de sistema de E/S). Si un atacante puede controlar la entrada a un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> cargar llamada al método, a continuación, el atacante puede ejecutar código.

Esta regla intenta encontrar la entrada de las solicitudes HTTP que se alcanza un <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> Load (método).

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que carga el XAML, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) acerca de cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

No cargar el XAML que no se confía.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
