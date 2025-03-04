---
title: 'CA1806: No omitir resultados del método'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: jillfra
ms.openlocfilehash: 2e68fb6b4c40c165a09ae2631a2ad0a64bf52fbc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921555"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: No omitir resultados del método

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|Identificador de comprobación|CA1806|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Hay varias razones posibles para esta ADVERTENCIA:

- Se crea un nuevo objeto, pero nunca se usa.

- Se llama a un método que crea y devuelve una nueva cadena y la nueva cadena nunca se utiliza.

- Un método COM o P/Invoke que devuelve un código de error o HRESULT que nunca se usa. Descripción de la regla

La creación de objetos innecesarios y la recolección de elementos no utilizados asociada del objeto no usado degrada el rendimiento.

Las cadenas son inmutables y los métodos como String. ToUpper devuelven una nueva instancia de una cadena en lugar de modificar la instancia de la cadena en el método de llamada.

Si se omite el código de error o HRESULT, puede producirse un comportamiento inesperado en condiciones de error o en condiciones de recursos insuficientes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Si el método A crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como un argumento a otro método o asigne la instancia a una variable. Si la creación del objeto es innecesaria, quítela.-o-

Si el método A llama al método B, pero no utiliza la nueva instancia de la cadena que devuelve el método B. Pase la instancia como un argumento a otro método, asigne la instancia a una variable. O quite la llamada si no es necesario.

 -o bien-

Si el método A llama al método B, pero no usa el código de error o HRESULT que devuelve el método. Use el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como un argumento a otro método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla a menos que el acto de crear el objeto tenga algún propósito.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una clase que omite el resultado de llamar a String. Trim.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se corrige la infracción anterior asignando el resultado de String. Trim de nuevo a la variable en la que se llamó.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un método que no utiliza un objeto que crea.

> [!NOTE]
> Esta infracción no se puede reproducir en Visual Basic.

[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se corrige la infracción anterior quitando la creación innecesaria de un objeto.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->