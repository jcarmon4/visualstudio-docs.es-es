---
title: 'CA1412: Marcar las Interfaces ComSource como IDispatch | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d72dd7e143720ce4ef2fce364a7e5ed3529ff9f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691991"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Marcar las interfaces ComSource como IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una clase donde una de las interfaces infringe la regla.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1408: No utilizar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vea también
 [Cómo: Generar eventos controlados por un receptor COM](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [interoperar con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
