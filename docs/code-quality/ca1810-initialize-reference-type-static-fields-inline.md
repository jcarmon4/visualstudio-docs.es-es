---
title: 'CA1810: Inicializar campos estáticos de tipo de referencia insertados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8838de46c6b14f698194f343aebec30402452970
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921528"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializar campos estáticos de tipo de referencia insertados

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|Identificador de comprobación|CA1810|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo de referencia declara un constructor estático explícito.

## <a name="rule-description"></a>Descripción de la regla
Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. La inicialización estática se desencadena cuando se tiene acceso a cualquier miembro estático o cuando se crea una instancia del tipo. Sin embargo, la inicialización estática no se desencadena si se declara una variable del tipo pero no se usa, lo que puede ser importante si la inicialización cambia el estado global.

Cuando todos los datos estáticos se inicializan en línea y no se declara un constructor estático explícito, los compiladores del lenguaje intermedio de Microsoft `beforefieldinit` (MSIL) agregan la marca y un constructor estático implícito, que inicializa los datos estáticos, al tipo de MSIL. definir. Cuando el compilador JIT encuentra la `beforefieldinit` marca, no se agrega la mayor parte del tiempo que las comprobaciones del constructor estático. Se garantiza que la inicialización estática se produce en algún momento antes de que se tenga acceso a los campos estáticos, pero no antes de que se invoque un método estático o un constructor de instancia. Tenga en cuenta que la inicialización estática puede producirse en cualquier momento después de declarar una variable del tipo.

Las comprobaciones del constructor estático pueden reducir el rendimiento. A menudo, solo se usa un constructor estático para inicializar campos estáticos, en cuyo caso solo debe asegurarse de que la inicialización estática se produce antes del primer acceso de un campo estático. El `beforefieldinit` comportamiento es adecuado para estos y otros tipos. Solo es apropiado cuando la inicialización estática afecta al estado global y se cumple una de las siguientes condiciones:

- El efecto en el estado global es costoso y no es necesario si no se utiliza el tipo.

- Se puede tener acceso a los efectos globales de estado sin tener acceso a los campos estáticos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el rendimiento no es un problema. o bien, si los cambios de estado global causados por la inicialización estática son caros o se debe garantizar que se produzcan antes de que se llame a un método estático del tipo o se cree una instancia del tipo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un `StaticConstructor`tipo,, que infringe la regla y un tipo `NoStaticConstructor`,, que reemplaza el constructor estático con la inicialización alineada para satisfacer la regla.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Observe la adición de la `beforefieldinit` marca en la definición de MSIL para `NoStaticConstructor` la clase.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA2207 Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)