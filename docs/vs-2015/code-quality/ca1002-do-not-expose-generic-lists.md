---
title: 'CA1002: No exponer listas genéricas | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d1b4f67f25db7c0006decc5fc26696c6c5dad01
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685353"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: No exponer listas genéricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|Identificador de comprobación|CA1002|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo contiene un miembro visible externamente que es un <xref:System.Collections.Generic.List%601?displayProperty=fullName> escribe, devuelve un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo o cuya firma incluye un <xref:System.Collections.Generic.List%601?displayProperty=fullName> parámetro.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> es una colección genérica diseñada para el rendimiento y no para la herencia. <xref:System.Collections.Generic.List%601?displayProperty=fullName> no tiene a los miembros virtuales que resulte más fácil cambiar el comportamiento de una clase heredada. Las siguientes colecciones genéricas diseñadas para herencia y deben exponerse en lugar de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo a una de las colecciones genéricas que está diseñado para la herencia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que el ensamblado que genera esta advertencia no pretende ser una biblioteca reutilizable. Por ejemplo, sería seguro suprimir esta advertencia en una aplicación ajustada para el rendimiento que se obtuvo una mejora del rendimiento del uso de listas genéricas.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: No declarar a miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Utilizar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizar valores genéricos cuando sea apropiado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
