---
title: 'CA1031: No capturar los tipos de excepción general | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4588a949b4b6439c3f76270b0bcdab9cd52c23d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431224"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|Identificador de comprobación|CA1031|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se captura en un `catch` instrucción o una cláusula catch general como `catch()` se utiliza.

## <a name="rule-description"></a>Descripción de la regla
 No se deben capturar excepciones generales.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, detectar una excepción más específica o vuelva a producir la excepción general como la última instrucción del `catch` bloque.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Detectar tipos de excepción general se pueden ocultar problemas en tiempo de ejecución de usuario de la biblioteca y puede dificultar la depuración.

> [!NOTE]
> A partir de la [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], common language runtime (CLR) ya no entrega excepciones de estado dañado que se producen en el sistema operativo y el código administrado, como las infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], controlarse en código administrado. Si desea compilar una aplicación en el [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o versiones posteriores y mantener el control de excepciones de estado dañado, puede aplicar el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al método que controla la excepción de estado dañado.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla y un tipo que implementa correctamente el `catch` bloque.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
