---
title: 'CA1811: Evitar código privado al que no se llama'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c144db920bfa04055c81227e4cc2c230ed2f097d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921328"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitar código privado al que no se llama

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|Identificador de comprobación|CA1811|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un miembro privado o interno (nivel de ensamblado) no tiene llamadores en el ensamblado, no lo invoca el Common Language Runtime y no lo invoca un delegado. Esta regla no comprueba los siguientes miembros:

- Miembros de interfaz explícitos.

- Constructores estáticos.

- Constructores de serialización.

- Métodos marcados <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> con <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>o.

- Miembros que se reemplazan.

## <a name="rule-description"></a>Descripción de la regla
Esta regla puede notificar falsos positivos si se producen puntos de entrada que no están identificados actualmente por la lógica de la regla. Además, un compilador puede emitir código no invocable en un ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite el código que no se pueda invocar o agregue código que lo llame.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
[CA1812: Evitar clases internas sin instancias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Revisar los parámetros no usados](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Quitar variables locales no usadas](../code-quality/ca1804-remove-unused-locals.md)