---
title: 'CA1060: Mover P/Invokes a la clase NativeMethods'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c05c0b17bc9866edd7c07874be14578ed4cf884
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922559"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Mover P/Invokes a la clase NativeMethods

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|Identificador de comprobación|CA1060|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

Un método usa servicios de invocación de plataforma para tener acceso a código no administrado y no es miembro de una de las clases **NativeMethods** .

## <a name="rule-description"></a>Descripción de la regla

Los métodos de invocación de plataforma, como los que están marcados <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> con el atributo, o los métodos que se definen `Declare` mediante la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]palabra clave en, tienen acceso al código no administrado. Estos métodos deben estar en una de las clases siguientes:

- **NativeMethods** : esta clase no suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> no se debe aplicar a esta clase). Esta clase es para los métodos que se pueden usar en cualquier lugar porque se realizará un recorrido de pila.

- **SafeNativeMethods** : esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase). Esta clase es para los métodos seguros para que cualquier usuario llame a. Los autores de llamadas de estos métodos no son necesarios para realizar una revisión de seguridad completa para asegurarse de que el uso es seguro porque los métodos son inofensivos para cualquier llamador.

- **UnsafeNativeMethods** : esta clase suprime los recorridos de pila para el permiso de código no administrado. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> se aplica a esta clase). Esta clase es para los métodos que son potencialmente peligrosos. Cualquier llamador de estos métodos debe realizar una revisión de seguridad completa para asegurarse de que el uso es seguro porque no se realizará ningún recorrido de pila.

Estas clases se declaran`Friend`como `internal` (, en Visual Basic) y declaran un constructor privado para evitar que se creen instancias nuevas. Los métodos de estas clases deben ser `static` y `internal` (`Shared` y `Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, mueva el método a la clase **NativeMethods** adecuada. Para la mayoría de las aplicaciones, el movimiento de P/Invoke a una nueva clase denominada **NativeMethods** es suficiente.

Sin embargo, si está desarrollando bibliotecas para usarlas en otras aplicaciones, considere la posibilidad de definir otras dos clases que se llamen como **SafeNativeMethods** y **UnsafeNativeMethods**. Estas clases se asemejan a la clase **NativeMethods** ; sin embargo, se marcan con un atributo especial denominado **SuppressUnmanagedCodeSecurityAttribute**. Cuando se aplica este atributo, el tiempo de ejecución no realiza un recorrido de pila completo para asegurarse de que todos los llamadores tienen el permiso **UnmanagedCode** . Normalmente, el tiempo de ejecución comprueba este permiso en el inicio. Dado que la comprobación no se realiza, puede mejorar considerablemente el rendimiento de las llamadas a estos métodos no administrados, también permite que el código con permisos limitados llame a estos métodos.

Sin embargo, debe usar este atributo con mucha atención. Puede tener implicaciones de seguridad graves si se implementa incorrectamente.

Para obtener información sobre cómo implementar los métodos, vea el ejemplo de **NativeMethods** , el ejemplo de **SafeNativeMethods** y el ejemplo de **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se declara un método que infringe esta regla. Para corregir la infracción, el **RemoveDirectory** P/Invoke debe moverse a una clase adecuada que esté diseñada para contener solo p/Invoke.

[!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
[!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Ejemplo de NativeMethods

### <a name="description"></a>DESCRIPCIÓN
Dado que la clase **NativeMethods** no debe marcarse mediante **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes que se colocan en ella necesitará el permiso **UnmanagedCode** . Dado que la mayoría de las aplicaciones se ejecutan desde el equipo local y se ejecutan con plena confianza, esto no suele ser un problema. Sin embargo, si está desarrollando bibliotecas reutilizables, considere la posibilidad de definir una clase **SafeNativeMethods** o **UnsafeNativeMethods** .

En el ejemplo siguiente se muestra un método **Interaction. Beep** que contiene la función **MessageBeep** de User32. dll. **MessageBeep** P/Invoke se coloca en la clase **NativeMethods** .

### <a name="code"></a>Código
[!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
[!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Ejemplo de SafeNativeMethods

### <a name="description"></a>DESCRIPCIÓN
Los métodos P/Invoke que se pueden exponer de forma segura a cualquier aplicación y que no tienen ningún efecto secundario deben colocarse en una clase denominada **SafeNativeMethods**. No tiene que solicitar permisos y no tiene que prestar mucha atención a la ubicación desde la que se les llama.

En el ejemplo siguiente se muestra una propiedad **Environment. TickCount** que contiene la función **GetTickCount** de Kernel32. dll.

### <a name="code"></a>Código
[!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
[!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Ejemplo de UnsafeNativeMethods

### <a name="description"></a>DESCRIPCIÓN
Los métodos P/Invoke a los que no se puede llamar de manera segura y que podrían provocar efectos secundarios deberían colocarse en una clase denominada **UnsafeNativeMethods**. Estos métodos deben comprobarse rigurosamente para asegurarse de que no se exponen al usuario de forma involuntaria. La regla [CA2118: Revise el uso](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) de SuppressUnmanagedCodeSecurityAttribute puede ayudarle con esto. Como alternativa, los métodos deben tener otro permiso exigido en lugar de **UnmanagedCode** cuando los usan.

En el ejemplo siguiente se muestra un método **cursor. Hide** que contiene la función **ShowCursor** de User32. dll.

### <a name="code"></a>Código
[!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
[!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Vea también

- [Advertencias de diseño](../code-quality/design-warnings.md)