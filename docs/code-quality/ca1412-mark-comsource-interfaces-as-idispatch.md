---
title: 'CA1412: Marcar las interfaces ComSource como IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e0a7214ce37aa48d69b9261d686960fa0a4c308c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546354"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Marcar las interfaces ComSource como IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|Identificador de comprobación|CA1412|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo se marca con el <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo y al menos una interfaz especificada no está marcado con el <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo establecido en el `InterfaceIsDispatch` valor.

## <a name="rule-description"></a>Descripción de la regla

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> se usa para identificar las interfaces de eventos que expone una clase a los clientes del modelo de objetos componentes (COM). Estas interfaces deben exponerse como `InterfaceIsIDispatch` para permitir que los clientes COM de Visual Basic 6 recibir notificaciones de eventos. De forma predeterminada, si una interfaz no está marcada con el <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo, se expone como una interfaz dual.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregar o modificar el <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo para que su valor se establece en InterfaceIsIDispatch para todas las interfaces que se especifican con el <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra una clase donde una de las interfaces infringe la regla.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)