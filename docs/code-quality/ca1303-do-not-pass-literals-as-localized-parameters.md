---
title: 'CA1303: No pasar literales como parámetros localizados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc32db1aea9c5514a7548bc889b65463de3de3d5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714690"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: No pasar literales como parámetros localizados

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|Identificador de comprobación|CA1303|
|Categoría|Microsoft.Globalization|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un método pasa una literal de cadena como un parámetro a un método o constructor de. NET, y esa cadena debe ser localizable.

Esta advertencia se produce si una cadena literal se pasa como un valor a un parámetro o propiedad y uno o varios de los casos siguientes son verdadera:

- El <xref:System.ComponentModel.LocalizableAttribute> atributo del parámetro o la propiedad se establece en true.

- El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".

- El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".

## <a name="rule-description"></a>Descripción de la regla

Literales de cadena que se incrustan en el código fuente son difíciles de localizar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, reemplace el literal de cadena con una cadena que se recuperan a través de una instancia de la <xref:System.Resources.ResourceManager> clase.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si no se localizará la biblioteca de código o si la cadena no se expone al usuario final o un desarrollador que utiliza la biblioteca de código.

Los usuarios pueden eliminar el ruido de los métodos que no se deben pasar cadenas localizadas cambiando el parámetro o la propiedad, o marcando estos elementos como condicionales.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un método que produce una excepción cuando cualquiera de sus dos argumentos están fuera del intervalo. Para el primer argumento, el constructor de la excepción se pasa una cadena literal, lo que infringe esta regla. Para el segundo argumento, se pasa al constructor correctamente una cadena que se recuperan mediante un <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Vea también

- [Recursos en aplicaciones de escritorio](/dotnet/framework/resources/index)