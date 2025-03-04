---
title: 'CA1721: Los nombres de propiedades no deben coincidir con los métodos get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44028caf027191846fa653db06abbe4027fdde8d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547091"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Los nombres de propiedades no deben coincidir con los métodos get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|Identificador de comprobación|CA1721|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

El nombre de un miembro comienza con ' get ' y, de lo contrario, coincide con el nombre de una propiedad. Por ejemplo, un tipo que contiene un método denominado ' GetColor ' y una propiedad denominada ' color ' provocan una infracción de la regla.

De forma predeterminada, esta regla solo examina los miembros y las propiedades visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Las propiedades y métodos "Get" deberían tener nombres que distingan claramente su función.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esta coherencia reduce el tiempo necesario para aprender una nueva biblioteca de software y aumenta la confianza de los clientes de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Cambie el nombre para que no coincida con el nombre de un método que tiene el prefijo ' get '.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

> [!NOTE]
> Esta advertencia se puede excluir si el método "Get" se debe a la implementación de la interfaz IExtenderProvider.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente contiene un método y una propiedad que infringen esta regla.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1024: Usar propiedades cuando corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)