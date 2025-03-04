---
title: 'CA1017: Marcar los ensamblados con ComVisibleAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bc88d3932baa5bbb4a723d7a16509831d58146
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923087"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Marcar los ensamblados con ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|Identificador de comprobación|CA1017|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un ensamblado no tiene aplicado <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> el atributo.

## <a name="rule-description"></a>Descripción de la regla
El <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo determina el modo en que los clientes com acceden al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad de COM se puede establecer para un ensamblado entero y, a continuación, se puede invalidar para tipos y miembros de tipo individuales. Si el atributo no está presente, el contenido del ensamblado es visible para los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue el atributo al ensamblado. Si no desea que el ensamblado esté visible para los clientes COM, aplique el atributo y establezca su valor en `false`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Si desea que el ensamblado esté visible, aplique el atributo y establezca su valor en `true`.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un ensamblado <xref:System.Runtime.InteropServices.ComVisibleAttribute> que tiene aplicado el atributo para evitar que sea visible para los clientes com.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)