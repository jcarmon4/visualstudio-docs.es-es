---
title: 'CA1714: Las enumeraciones Flags deben tener nombres en plural'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d71200c6c7fbb61e7994119fde5e75f7623fa669
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547194"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Las enumeraciones Flags deben tener nombres en plural

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1714|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Una enumeración tiene <xref:System.FlagsAttribute?displayProperty=fullName> y su nombre no termina en ' '.

De forma predeterminada, esta regla solo examina las enumeraciones visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los tipos marcados con <xref:System.FlagsAttribute> tienen nombres que están en plural porque el atributo indica que se puede especificar más de un valor. Por ejemplo, una enumeración que define los días de la semana puede estar pensada para su uso en una aplicación donde se pueden especificar varios días. Esta enumeración debe tener <xref:System.FlagsAttribute> y se puede llamar ' Days '. Una enumeración similar que permite especificar un solo día no tendría el atributo y se podría llamar ' Day '.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Haga que el nombre de la enumeración sea una palabra plural o <xref:System.FlagsAttribute> Quite el atributo si no se deben especificar varios valores de enumeración simultáneamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una infracción si el nombre es una palabra en plural pero no termina en ' '. Por ejemplo, si la enumeración de varios días que se ha descrito anteriormente se denominara "DaysOfTheWeek", esto infringiría la lógica de la regla pero no su intención. Dichas infracciones deben suprimirse.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Diseño de enumeración](/dotnet/standard/design-guidelines/enum)