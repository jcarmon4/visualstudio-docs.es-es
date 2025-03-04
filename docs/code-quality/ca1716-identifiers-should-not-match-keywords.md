---
title: 'CA1716: Los identificadores no deben coincidir con palabras clave'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a51ac9509cf891c05166d46e4b72b862c0dc723
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547081"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Los identificadores no deben coincidir con palabras clave

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|Identificador de comprobación|CA1716|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

El nombre de un espacio de nombres, tipo o miembro virtual o de interfaz coincide con una palabra clave reservada en un lenguaje de programación.

De forma predeterminada, esta regla solo examina los espacios de nombres, tipos y miembros visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los identificadores de los espacios de nombres, los tipos y los miembros virtuales y de interfaz no deben coincidir con las palabras clave definidas por los lenguajes que tienen como destino el Common Language Runtime. Dependiendo del lenguaje que se use y de la palabra clave, los errores del compilador y las ambigüedades pueden dificultar el uso de la biblioteca.

Esta regla comprueba las palabras clave en los idiomas siguientes:

- Visual Basic
- C#
- C++/CLI

La comparación sin distinción entre mayúsculas y minúsculas se usa para palabras clave de Visual Basic y la comparación con distinción entre mayúsculas y minúsculas se usa para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Seleccione un nombre que no aparezca en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir una advertencia de esta regla si está convencido de que el identificador no confundirá a los usuarios de la API y que la biblioteca se puede usar en todos los idiomas disponibles en .NET.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).