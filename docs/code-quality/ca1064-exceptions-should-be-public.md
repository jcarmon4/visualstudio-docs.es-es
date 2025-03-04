---
title: 'CA1064: Las excepciones deben ser públicas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b17ccfe66875588ac19c587ff6fcbd889d1e6a44
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922316"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Las excepciones deben ser públicas

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|Identificador de comprobación|CA1064|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
Una excepción no pública deriva directamente de <xref:System.Exception>, <xref:System.SystemException>o <xref:System.ApplicationException>.

## <a name="rule-description"></a>Descripción de la regla
Una excepción interna solo es visible dentro de su propio ámbito interno. Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla. Si la excepción interna se hereda de <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, el código externo no tendrá información suficiente para saber qué hacer con la excepción.

Sin embargo, si el código tiene una excepción pública que se usa más adelante como base para una excepción interna, es razonable asumir que el código más allá podrá hacer algo inteligente con la excepción base. La excepción pública tendrá más información de la que proporciona <xref:System.Exception>, <xref:System.SystemException>o <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Haga que la excepción sea pública o derive la excepción interna de una excepción pública que no <xref:System.Exception>sea <xref:System.SystemException>, o <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima un mensaje de esta regla si está seguro de que la excepción privada se detectará dentro de su propio ámbito interno.

## <a name="example"></a>Ejemplo
Esta regla se desencadena en el primer método de ejemplo, FirstCustomException porque la clase de excepción deriva directamente de la excepción y es interna. La regla no se activa en la clase SecondCustomException porque aunque la clase también deriva directamente de la excepción, la clase se declara Public. La tercera clase tampoco desencadena la regla porque no se deriva directamente de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>o <xref:System.ApplicationException?displayProperty=fullName>.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
