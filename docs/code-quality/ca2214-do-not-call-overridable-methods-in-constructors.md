---
title: 'CA2214: No llamar a métodos reemplazables en constructores'
ms.date: 05/29/2016
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a59346cb70269d4d2b405279fc9ea5573a879b1e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547001"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: No llamar a métodos reemplazables en constructores

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|Identificador de comprobación|CA2214|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

El constructor de un tipo no sellado llama a un método virtual definido en su clase.

## <a name="rule-description"></a>Descripción de la regla

Cuando se llama a un método virtual, el tipo real que ejecuta el método no se selecciona hasta el tiempo de ejecución. Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor de la instancia que invoca el método.

> [!NOTE]
> La implementación de análisis heredada de esta regla tiene un mensaje de diagnóstico**distinto de "nombre del constructor"\[contiene una cadena de llamadas que da como resultado una llamada a un método virtual definido por la clase. Revise la siguiente pila de llamadas para ver si**hay consecuencias no deseadas. La implementación de los [analizadores FxCop](install-fxcop-analyzers.md) de esta regla tiene un mensaje de diagnóstico de "**no llamar a métodos reemplazables en constructores**".

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, no llame a los métodos virtuales de un tipo desde dentro de los constructores del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Se debe rediseñar el constructor para eliminar la llamada al método virtual.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el efecto de infringir esta regla. La aplicación de prueba crea una instancia `DerivedType`de, que hace que se ejecute`BadlyConstructedType`su constructor de clase base (). `BadlyConstructedType`el constructor de llama incorrectamente al método `DoSomething`virtual. Como muestra el resultado, `DerivedType.DoSomething()` ejecuta antes `DerivedType`de que se ejecute el constructor de.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Este ejemplo produce el siguiente resultado:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```