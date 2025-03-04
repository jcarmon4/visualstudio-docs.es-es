---
title: 'CA2202: No usar Dispose varias veces en objetos'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fb70baa17bee484dc3c31d7c6ce9b302019403
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300599"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: No usar Dispose varias veces en objetos

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|Identificador de comprobación|CA2202|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Una implementación de método contiene rutas de acceso de código que podrían <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> provocar varias llamadas a o un equivalente de Dispose, como un método Close () en algunos tipos, en el mismo objeto.

## <a name="rule-description"></a>Descripción de la regla

Se puede llamar <xref:System.IDisposable.Dispose%2A> a un método correctamente implementado varias veces sin producir una excepción. Sin embargo, esto no se garantiza y, para evitar <xref:System.ObjectDisposedException?displayProperty=fullName> que se genere, <xref:System.IDisposable.Dispose%2A> no se debe llamar a más de una vez en un objeto.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2000 Desechar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie la implementación para que, independientemente de la ruta <xref:System.IDisposable.Dispose%2A> de acceso del código, se llame solo una vez para el objeto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Incluso si <xref:System.IDisposable.Dispose%2A> se sabe que para el objeto se puede llamar con seguridad varias veces, la implementación podría cambiar en el futuro.

## <a name="example"></a>Ejemplo

Las instrucciones anidadas`Using` (en Visual Basic) pueden producir infracciones de la advertencia CA2202. `using` Si el recurso IDisposable de la instrucción interna `using` anidada contiene el recurso de la instrucción externa `using` , el `Dispose` método del recurso anidado libera el recurso contenido. Cuando se produce esta situación, `Dispose` el método de la `using` instrucción externa intenta desechar su recurso por segunda vez.

En el ejemplo siguiente, un <xref:System.IO.Stream> objeto que se crea en una instrucción using externa se libera al final de la instrucción using interna en el método Dispose <xref:System.IO.StreamWriter> del objeto que contiene el `stream` objeto. Al final de la instrucción externa `using` , el `stream` objeto se libera una segunda vez. La segunda versión es una infracción de CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Ejemplo

Para resolver este problema, use un `try` / `finally` bloque en lugar de la instrucción `using` externa. En el `finally` bloque, asegúrese de que el `stream` recurso no sea NULL.

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> La `?.` sintaxis anterior es el [operador condicional null](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)