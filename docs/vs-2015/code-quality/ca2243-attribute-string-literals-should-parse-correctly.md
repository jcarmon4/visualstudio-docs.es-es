---
title: 'CA2243: Literales de cadena de atributo se deben analizar correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f23db8a9674de621090be70067a555ef4fca2b99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201500"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Los literales de cadena de atributo se deben analizar correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|Identificador de comprobación|CA2243|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Parámetro literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.

## <a name="rule-description"></a>Descripción de la regla
 Puesto que se derivan de los atributos <xref:System.Attribute?displayProperty=fullName>y los atributos se usan en tiempo de compilación, solo los valores constantes que se pueden pasar a sus constructores. Parámetros de atributo que se deben representar direcciones URL, GUID y las versiones no se pueden escribir como <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, y <xref:System.Version?displayProperty=fullName>, ya que estos tipos no se puede representar como constantes. En su lugar, deben representarse mediante cadenas.

 Dado que el parámetro es una cadena, es posible que se puede pasar un parámetro con formato incorrecto en tiempo de compilación.

 Esta regla utiliza una heurística de nomenclatura para buscar los parámetros que representan un identificador uniforme de recursos (URI), un identificador único global (GUID) o una versión y comprueba que el valor pasado es correcto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie la cadena de parámetro a una dirección URL tiene el formato correcto, GUID o una versión.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el parámetro no representa una dirección URL, un GUID o una versión.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra código para AssemblyFileVersionAttribute que infringe esta regla.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 La regla se desencadena por el texto siguiente:

- Parámetros que contienen 'version' y no se puede analizar como System.Version.

- Parámetros que contienen 'guid' y no se puede analizar como System.Guid.

- Parámetros que contienen "uri", 'urn' o 'url' y no se puede analizar a System.Uri.

## <a name="see-also"></a>Vea también
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
