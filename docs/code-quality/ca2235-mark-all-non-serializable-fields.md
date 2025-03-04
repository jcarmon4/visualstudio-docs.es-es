---
title: 'CA2235: Marcar todos los campos no serializables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177388"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Marcar todos los campos no serializables

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|Identificador de comprobación|CA2235|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.

## <a name="rule-description"></a>Descripción de la regla

Un tipo serializable es aquel que está marcado con el <xref:System.SerializableAttribute?displayProperty=fullName> atributo. Cuando se serializa el tipo, un <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> excepción se produce si el tipo contiene un campo de instancia de un tipo que no es serializable *y* no implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz.

> [!TIP]
> CA2235 no se activa por ejemplo campos de tipos que implementan <xref:System.Runtime.Serialization.ISerializable> porque proporcionan su propia lógica de serialización.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, aplique el <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo en el campo que no es serializable.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Sólo suprima una advertencia de esta regla si un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo se declara que permite que las instancias del campo al que se serializan y deserializan.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra dos tipos: uno que infringe la regla y que cumple la regla.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Comentarios

Regla CA2235 no analiza los tipos que implementan la <xref:System.Runtime.Serialization.ISerializable> interfaz (a menos que también se marcan con el <xref:System.SerializableAttribute> atributo). Esto es porque [regla CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) ya recomienda marcar los tipos que implementan la <xref:System.Runtime.Serialization.ISerializable> interactuar con el <xref:System.SerializableAttribute> atributo.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)