---
title: 'CA1011: Considere la posibilidad de pasar los tipos base como parámetros | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d3104f7173721668538e6d73c1c5492c5c388ba5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151106"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considerar pasar los tipos base como parámetros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|Identificador de comprobación|CA1011|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Una declaración de método incluye un parámetro formal que es un tipo derivado y el método llama a solo los miembros del tipo base del parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Cuando el argumento se utiliza en el cuerpo del método, el método específico que se ejecuta depende del tipo del argumento. Si no se requiere la funcionalidad adicional proporcionada por el tipo derivado, el uso del tipo base permite un uso más amplio del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla

- Si el método requiere la funcionalidad específica que proporciona el tipo derivado

   \- o -

- para exigir que solo el tipo derivado, o un tipo más derivado, se pasa al método.

  En estos casos, el código será más sólido debido a la comprobación de tipos seguros proporcionado por el compilador y el tiempo de ejecución.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `ManipulateFileStream`, que puede utilizarse solo con un <xref:System.IO.FileStream> objeto, lo que infringe esta regla. Un segundo método, `ManipulateAnyStream`, cumple la regla reemplazando el <xref:System.IO.FileStream> parámetro mediante el uso de un <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
