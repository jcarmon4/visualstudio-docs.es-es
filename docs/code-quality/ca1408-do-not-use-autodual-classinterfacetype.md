---
title: 'CA1408: No utilizar AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b79483e8703ea297634d0d81d5449c09b58c9fb7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921981"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: No utilizar AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|Identificador de comprobación|CA1408|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo visible del modelo de objetos componentes (com) se marca <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> con el atributo establecido `AutoDual` en el <xref:System.Runtime.InteropServices.ClassInterfaceType>valor de.

## <a name="rule-description"></a>Descripción de la regla
Los tipos que utilizan una interfaz dual permiten a los clientes enlazarse a un diseño de interfaz concreto. Cualquier cambio que se introduzca en una versión futura en el diseño del tipo o en cualquier tipo base provocará un error en los clientes COM que están enlazados a la interfaz. De forma predeterminada, si <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> no se especifica el atributo, se usa una interfaz de solo envío.

A menos que se marque lo contrario, todos los tipos públicos no genéricos son visibles para COM; todos los tipos no públicos y genéricos son invisibles para COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el valor del <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributo por el `None` valor de <xref:System.Runtime.InteropServices.ClassInterfaceType> y defina explícitamente la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla a menos que esté seguro de que el diseño del tipo y sus tipos base no cambiarán en una versión futura.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una clase que infringe la regla y una nueva declaración de la clase para usar una interfaz explícita.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1403: Los tipos de diseño automático no deben ser visibles para COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: Marcar interfaces comSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Vea también

- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)