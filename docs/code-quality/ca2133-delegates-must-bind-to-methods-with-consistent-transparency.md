---
title: 'CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0745506bfe55305c9c3a55f57823e5d80c453006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796744"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|Identificador de comprobación|CA2133|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

> [!NOTE]
> Esta advertencia solo se aplica al código que se está ejecutando el CoreCLR (la versión de CLR que es específica para las aplicaciones web de Silverlight).

## <a name="cause"></a>Motivo

Esta advertencia se desencadena en un método que enlaza un delegado que está marcado con el <xref:System.Security.SecurityCriticalAttribute> a un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La advertencia también desencadena un método que enlaza un delegado que es transparente o crítico para la seguridad a un método crítico.

## <a name="rule-description"></a>Descripción de la regla

Tipos de delegado y los métodos que se enlazan deben tener una transparencia coherente. Los delegados de transparentes y crítico para la seguridad solo pueden enlazar a otros métodos transparentes o crítico para la seguridad. De forma similar, los delegados críticos solo pueden enlazar a métodos críticos. Estas reglas de enlace garantizan que el único código que puede invocar un método a través de un delegado también pudiera haber invocado el mismo método directamente. Por ejemplo, reglas de enlace evitar que el código transparente de la llamada a código crítico directamente a través de un delegado transparente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta advertencia, cambie la transparencia del delegado o del método que enlaza para que la transparencia de los dos son equivalentes.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]