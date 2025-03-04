---
title: 'CA1407: Evitar los miembros estáticos en tipos visibles a través de COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631be1a93318cd24af4251fefbc710294fa52bf7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922008"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evitar los miembros estáticos en tipos visibles a través de COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|Identificador de comprobación|CA1407|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo que está marcado específicamente como visible para el modelo de objetos componentes (com) `public``static` contiene un método.

## <a name="rule-description"></a>Descripción de la regla
COM no admite `static` métodos.

Esta regla omite los descriptores de acceso de propiedades y eventos, métodos de sobrecarga de operadores o métodos marcados mediante el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo o el <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo.

De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos.

Para que se produzca esta regla, debe establecerse <xref:System.Runtime.InteropServices.ComVisibleAttribute> un nivel de ensamblado en `false` y la <xref:System.Runtime.InteropServices.ComVisibleAttribute> clase debe establecerse `true`en, como se muestra en el código siguiente.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el diseño para utilizar un método de instancia que proporcione la misma funcionalidad `static` que el método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si un cliente com no requiere acceso a la funcionalidad proporcionada por el `static` método.

## <a name="example-violation"></a>Ejemplo de infracción

### <a name="description"></a>DESCRIPCIÓN
En el ejemplo siguiente se `static` muestra un método que infringe esta regla.

### <a name="code"></a>Código
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Comentarios
En este ejemplo, no se puede llamar al método **book. FromPages** desde com.

## <a name="example-fix"></a>Corrección de ejemplo

### <a name="description"></a>DESCRIPCIÓN
Para corregir la infracción en el ejemplo anterior, podría cambiar el método a un método de instancia, pero esto no tiene sentido en esta instancia. Una solución mejor es aplicar `ComVisible(false)` explícitamente al método para que resulte claro a otros desarrolladores que el método no se puede visualizar desde com.

El siguiente ejemplo se <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> aplica al método.

### <a name="code"></a>Código
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1017: Marcar ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Evite argumentos Int64 para clientes de Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Evitar campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vea también
[Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)