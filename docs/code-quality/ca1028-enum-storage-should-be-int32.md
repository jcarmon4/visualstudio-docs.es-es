---
title: 'CA1028: El almacenamiento de la enumeración debe ser de tipo Int32'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c91de575abe8b19a5d8f6fca864e2bc452da7cb2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547651"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: El almacenamiento de la enumeración debe ser de tipo Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|Identificador de comprobación|CA1028|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

El tipo subyacente de una enumeración no <xref:System.Int32?displayProperty=fullName>es.

De forma predeterminada, esta regla solo examina enumeraciones públicas, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De forma predeterminada, <xref:System.Int32?displayProperty=fullName> el tipo de datos se usa para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario ni se recomienda para la mayoría de los escenarios. No se consigue un aumento significativo del rendimiento mediante el uso de un tipo de <xref:System.Int32>datos menor que. Si no puede utilizar el tipo de datos predeterminado, debe usar uno de los tipos enteros conformes a Common Language System (CLS) <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> para asegurarse de que todos los valores de la enumeración se pueden representar en Lenguajes de programación conformes a CLS.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, a menos que existan problemas de <xref:System.Int32>tamaño o compatibilidad, use. En situaciones en <xref:System.Int32> las que no sea lo suficientemente grande como para contener <xref:System.Int64>los valores, use. Si la compatibilidad con versiones anteriores requiere un tipo de <xref:System.Byte> datos <xref:System.Int16>más pequeño, use o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla solo si los problemas de compatibilidad con versiones anteriores lo requieren. En las aplicaciones, si no se cumple esta regla normalmente no se producen problemas. En el caso de las bibliotecas, donde se requiere la interoperabilidad de lenguajes, el hecho de no cumplir esta regla podría afectar negativamente a los usuarios.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

En el ejemplo siguiente se muestran dos enumeraciones que no utilizan el tipo de datos subyacente recomendado.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Ejemplo de cómo corregir

En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de <xref:System.Int32>datos subyacente a.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1008: Las enumeraciones deben tener un valor cero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: No asignar nombre a los valores de enumeración ' Reserved '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: No Prefije valores de enumeración con el nombre de tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Vea también

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>