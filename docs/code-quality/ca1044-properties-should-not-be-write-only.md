---
title: 'CA1044: Las propiedades no deben ser de solo escritura'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b3e05f53c4efd16f02bc71c3c478e5ffe3ef8bc8
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547581"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Las propiedades no deben ser de solo escritura

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|Identificador de comprobación|CA1044|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Una propiedad tiene un descriptor de acceso set pero no un descriptor de acceso get.

De forma predeterminada, esta regla solo examina los tipos públicos, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los descriptores de acceso get proporcionan acceso de lectura a una propiedad y los descriptores de acceso proporcionan acceso de escritura. Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto se debe a que permitir que un usuario establezca un valor y, a continuación, impedir que el usuario vea el valor no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue un descriptor de acceso get a la propiedad. Como alternativa, si el comportamiento de una propiedad de solo escritura es necesario, considere la posibilidad de convertir esta propiedad en un método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Se recomienda no suprimir las advertencias de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1044.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `BadClassWithWriteOnlyProperty` es un tipo con una propiedad de solo escritura. `GoodClassWithReadWriteProperty`contiene el código corregido.

[!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
[!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]