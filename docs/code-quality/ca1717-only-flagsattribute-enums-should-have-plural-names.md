---
title: 'CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d760802422773b3713fa7ea08ce0ce7a191f418
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547116"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1717|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

El nombre de una enumeración finaliza en una palabra plural y la enumeración no está marcada <xref:System.FlagsAttribute?displayProperty=fullName> con el atributo.

De forma predeterminada, esta regla solo examina las enumeraciones visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Las convenciones de nomenclatura dictan que un nombre plural para una enumeración indica que se puede especificar más de un valor de la enumeración simultáneamente. El <xref:System.FlagsAttribute> indica a los compiladores que la enumeración se debe tratar como un campo de bits que habilita las operaciones bit a bit en la enumeración.

Si solo se puede especificar un valor de una enumeración a la vez, el nombre de la enumeración debe ser una palabra singular. Por ejemplo, una enumeración que define los días de la semana puede estar pensada para su uso en una aplicación donde se pueden especificar varios días. Esta enumeración debe tener <xref:System.FlagsAttribute> y se puede llamar ' Days '. Una enumeración similar que permite especificar un solo día no tendría el atributo y se podría llamar ' Day '.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo necesario para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Haga que el nombre de la enumeración sea una palabra singular <xref:System.FlagsAttribute>o agregue la.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de la regla si el nombre termina en una palabra singular.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1714: Las enumeraciones de marcas deben tener nombres en plural](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Diseño de enumeración](/dotnet/standard/design-guidelines/enum)