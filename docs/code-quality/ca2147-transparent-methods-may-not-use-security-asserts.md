---
title: 'CA2147: Los métodos transparentes no pueden usar aserciones de seguridad'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b56001f5a083317911edde9282b66758deb1b6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920725"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Los métodos transparentes no pueden usar aserciones de seguridad

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|Identificador de comprobación|CA2147|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
El código marcado como <xref:System.Security.SecurityTransparentAttribute> no tiene permisos suficientes para la aserción.

## <a name="rule-description"></a>Descripción de la regla
Esta regla analiza todos los métodos y tipos de un ensamblado que es del 100% transparente o mixto y crítico, y marca cualquier uso declarativo o <xref:System.Security.CodeAccessPermission.Assert%2A>imperativo de.

En tiempo de ejecución, cualquier llamada <xref:System.Security.CodeAccessPermission.Assert%2A> a desde código transparente hará que <xref:System.InvalidOperationException> se produzca una excepción. Esto puede ocurrir en ensamblados transparentes del 100%, y también en ensamblados transparentes y críticos mixtos donde un método o tipo se declara transparente, pero incluye una aserción declarativa o imperativa.

El .NET Framework 2,0 presentó una característica denominada *transparencia*. Los métodos, los campos, las interfaces, las clases y los tipos individuales pueden ser transparentes o críticos.

No se permite que el código transparente eleve los privilegios de seguridad. Por lo tanto, todos los permisos concedidos o solicitados se pasan automáticamente a través del código al dominio de aplicación host o del llamador. Entre los ejemplos de elevaciones se incluyen aserciones, LinkDemands, SuppressUnmanagedCode `unsafe` y code.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para resolver el problema, marque el código que llama a la aserción con <xref:System.Security.SecurityCriticalAttribute>o quite la aserción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima un mensaje de esta regla.

## <a name="example"></a>Ejemplo
Este código producirá un `SecurityTestClass` error si es transparente, `Assert` cuando el método produce <xref:System.InvalidOperationException>una excepción.

[!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Ejemplo
Una opción consiste en revisar el código del método SecurityTransparentMethod en el ejemplo siguiente, y si el método se considera seguro para elevación, marque SecurityTransparentMethod con crítico para la seguridad. Esto requiere que se realice una auditoría de seguridad detallada, completa y sin errores en el método junto con las llamadas que se producen dentro del método bajo la aserción:

[!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

Otra opción es quitar la aserción del código y permitir que las peticiones de permisos de e/s de archivos subsiguientes fluyan más allá de SecurityTransparentMethod al autor de la llamada. Esto habilita las comprobaciones de seguridad. En este caso, no se necesita ninguna auditoría de seguridad, ya que las peticiones de permisos fluyen al llamador o al dominio de aplicación. Las peticiones de permisos se controlan estrechamente a través de la Directiva de seguridad, el entorno de hospedaje y las concesiones de permisos de origen de código.

## <a name="see-also"></a>Vea también
[Advertencias de seguridad](../code-quality/security-warnings.md)