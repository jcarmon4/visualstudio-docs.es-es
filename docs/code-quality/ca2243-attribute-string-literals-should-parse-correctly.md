---
title: 'CA2243: Los literales de cadena de atributo se deben analizar correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c0f078c21de023b1f5cfacde0cf122c179adb2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919896"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Los literales de cadena de atributo se deben analizar correctamente

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|Identificador de comprobación|CA2243|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
El parámetro de literal de cadena de un atributo no se analiza correctamente para una dirección URL, un GUID o una versión.

## <a name="rule-description"></a>Descripción de la regla
Puesto que los atributos se <xref:System.Attribute?displayProperty=fullName>derivan de y los atributos se usan en tiempo de compilación, solo se pueden pasar valores constantes a sus constructores. Los parámetros de atributo que deben representar direcciones URL, GUID y versiones no se pueden escribir <xref:System.Uri?displayProperty=fullName>como <xref:System.Guid?displayProperty=fullName>, y <xref:System.Version?displayProperty=fullName>, porque estos tipos no se pueden representar como constantes. En su lugar, deben representarse mediante cadenas.

Dado que el parámetro se escribe como una cadena, es posible que se pase un parámetro con un formato incorrecto en tiempo de compilación.

Esta regla usa una heurística de nomenclatura para buscar parámetros que representan un identificador uniforme de recursos (URI), un identificador único global (GUID) o una versión, y comprueba que el valor pasado es correcto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Cambie la cadena de parámetro a una dirección URL, un GUID o una versión correctos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el parámetro no representa una dirección URL, un GUID o una versión.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra el código para el AssemblyFileVersionAttribute que infringe esta regla.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

La regla se desencadena con los parámetros siguientes:

- Los parámetros que contienen ' version ' y no se pueden analizar en System. version.

- Los parámetros que contienen "GUID" y no se pueden analizar en System. GUID.

- Los parámetros que contienen "URI", "urn" o "URL" y no se pueden analizar en System. Uri.

## <a name="see-also"></a>Vea también

- [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)