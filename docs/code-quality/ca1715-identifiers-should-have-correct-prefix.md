---
title: 'CA1715: Los identificadores deben tener el prefijo correcto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2a793f0a359cadc58c262861ee0495f92188d0b7
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547181"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Los identificadores deben tener el prefijo correcto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|Identificador de comprobación|CA1715|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en interfaces.<br /><br /> No problemático: cuando se produce en parámetros de tipo genérico.|

## <a name="cause"></a>Causa

El nombre de una interfaz no comienza con una ' I ' mayúscula.

-o bien-

El nombre de un [parámetro de tipo genérico](/dotnet/csharp/programming-guide/generics/generic-type-parameters) en un tipo o método no comienza con una letra ' t ' mayúscula.

De forma predeterminada, esta regla solo busca interfaces, tipos y métodos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Por Convención, los nombres de ciertos elementos de programación comienzan con un prefijo específico.

Los nombres de interfaz deben empezar con una ' I ' mayúscula seguida de otra letra mayúscula. Esta regla notifica las infracciones de los nombres de interfaz como "interfaz" y "IsolatedInterface".

Los nombres de parámetro de tipo genérico deben empezar con una t mayúscula y, opcionalmente, pueden ir seguidos de otra letra mayúscula. Esta regla notifica las infracciones de los nombres de parámetro de tipo genérico, como ' V ' y ' type '.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar qué partes del código analiza esta regla. Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parámetros de tipo de un solo carácter

Puede configurar si se deben excluir o no los parámetros de tipo de un solo carácter de esta regla. Por ejemplo, para especificar que esta regla *no debe* analizar los parámetros de tipo de un solo carácter, agregue uno de los siguientes pares clave-valor a un archivo. editorconfig en el proyecto:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Esta regla nunca se desencadena para un parámetro de `T`tipo denominado, por `Collection<T>`ejemplo,.

### <a name="api-surface"></a>Superficie de API

Puede configurar en qué partes del código base ejecutar esta regla, en función de su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre del identificador para que tenga el prefijo correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="interface-naming-example"></a>Ejemplo de nombres de interfaz

En el fragmento de código siguiente se muestra una interfaz con el nombre incorrecto:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

El siguiente fragmento de código corrige la infracción anterior al prefijar la interfaz con ' I ':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Ejemplo de nomenclatura de parámetros de tipo

En el fragmento de código siguiente se muestra un parámetro de tipo genérico con un nombre incorrecto:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

El siguiente fragmento de código corrige la infracción anterior al prefijar el parámetro de tipo genérico con ' t ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1722: Los identificadores no deben tener un prefijo incorrecto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)