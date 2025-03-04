---
title: 'CA1411: Métodos de registro COM no deben ser visibles | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d7bcaf5637be70174a3a337343d92b7b3705b46
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692027"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Los métodos de registro COM no deben ser visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|Identificador de comprobación|CA1411|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método marcado con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo es visible externamente.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un ensamblado se registra con el modelo de objetos componentes (COM), se agregan entradas al registro para cada tipo COM-visible en el ensamblado. Los métodos marcados con el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> y <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos se denominan durante los procesos de registro y anulación del registro, respectivamente, para ejecutar código de usuario que es específico para el registro o anulación del registro de estos tipos. No se debe llamar a este código fuera de estos procesos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la accesibilidad del método que `private` o `internal` (`Friend` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos métodos que infringen la regla.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1410: Métodos de registro COM se deben asociar](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrar ensamblados con COM](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (herramienta de registro de ensamblados)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
