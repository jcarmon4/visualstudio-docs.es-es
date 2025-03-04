---
title: 'CA2234: Pasar objetos System.Uri en lugar de cadenas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74484c5f014c9a677c321a0d9fed649f016ea3c9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546883"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Pasar objetos System.Uri en lugar de cadenas

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|Identificador de comprobación|CA2234|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Se realiza una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "URI", "URI", "urn", "urn", "URL" o "URL" y el tipo declarativo del método contiene una sobrecarga de método correspondiente que tiene <xref:System.Uri?displayProperty=fullName> un parámetro.

De forma predeterminada, esta regla solo examina los tipos y métodos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Un nombre de parámetro se divide en tokens según la Convención de mayúsculas y minúsculas Camel y, a continuación, se comprueba cada token para ver si es igual a "URI", "URI", "urn", "urn", "URL" o "URL". Si hay una coincidencia, se supone que el parámetro representa un identificador uniforme de recursos (URI). Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La <xref:System.Uri> clase proporciona estos servicios de forma segura. Cuando hay una opción entre dos sobrecargas que solo difieren en cuanto a la representación de un URI, el usuario debe elegir la sobrecarga <xref:System.Uri> que toma un argumento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a la sobrecarga que <xref:System.Uri> toma el argumento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el parámetro de cadena no representa un URI.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (uso). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un `ErrorProne`método,, que infringe la regla y un método `SaferWay`,, que llama correctamente <xref:System.Uri> a la sobrecarga:

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System. Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: Los valores devueltos de URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)