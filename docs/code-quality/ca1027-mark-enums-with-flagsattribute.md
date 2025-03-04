---
title: 'CA1027: Marcar enumeraciones con FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92b74bcf587492155445c500252ea10773a5978b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547800"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Marcar enumeraciones con FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|Identificador de comprobación|CA1027|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Los valores de una enumeración son potencias de dos o son combinaciones de otros valores que se definen en la enumeración <xref:System.FlagsAttribute?displayProperty=fullName> y el atributo no está presente. Para reducir los falsos positivos, esta regla no notifica una infracción de las enumeraciones que tienen valores contiguos.

De forma predeterminada, esta regla solo examina enumeraciones públicas, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Se <xref:System.FlagsAttribute> aplica a una enumeración cuando se pueden combinar con sentido las constantes con nombre. Por ejemplo, considere una enumeración de los días de la semana en una aplicación que realiza un seguimiento de los recursos del día que están disponibles. Si la disponibilidad de cada recurso se codifica mediante la enumeración que tiene <xref:System.FlagsAttribute> presente, se puede representar cualquier combinación de días. Sin el atributo, solo se puede representar un día de la semana.

En el caso de los campos que almacenan enumeraciones combinables, los valores de enumeración individuales se tratan como grupos de bits en el campo. Por lo tanto, estos campos a veces se denominan *campos de bits*. Para combinar los valores de enumeración para el almacenamiento en un campo de bits, utilice los operadores condicionales booleanos. Para probar un campo de bits para determinar si un valor de enumeración específico está presente, utilice los operadores lógicos booleanos. Para un campo de bits para almacenar y recuperar correctamente los valores de enumeración combinados, cada valor que se define en la enumeración debe ser una potencia de dos. A menos que esto sea así, los operadores lógicos booleanos no podrán extraer los valores de enumeración individuales almacenados en el campo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, <xref:System.FlagsAttribute> agregue a la enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla si no desea que los valores de enumeración sean combinables.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `DaysEnumNeedsFlags` es una enumeración que cumple los requisitos para <xref:System.FlagsAttribute> usar pero no lo tiene. La `ColorEnumShouldNotHaveFlag` enumeración no tiene valores que sean potencias de dos, pero que especifica <xref:System.FlagsAttribute>incorrectamente. Esto infringe la regla [CA2217: No marque las enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.FlagsAttribute?displayProperty=fullName>