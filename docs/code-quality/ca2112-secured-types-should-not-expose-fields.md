---
title: 'CA2112: Los tipos seguros no deben exponer campos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43ef4165823f59045dda8c05b5679fdd3b795114
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921083"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Los tipos seguros no deben exponer campos

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|Identificador de comprobación|CA2112|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público o protegido contiene campos públicos y está protegido por una [petición de vínculo](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descripción de la regla
Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, haga que los campos sean no públicos y agregue propiedades o métodos públicos que devuelvan los datos de campo. Las comprobaciones de seguridad de LinkDemand en tipos protegen el acceso a las propiedades y los métodos del tipo. Sin embargo, la seguridad de acceso del código no se aplica a los campos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Tanto para los problemas de seguridad como para un buen diseño, debe corregir las infracciones haciendo que los campos públicos sean no públicos. Puede suprimir una advertencia de esta regla si el campo no contiene información que deba permanecer protegida y no se basa en el contenido del campo.

## <a name="example"></a>Ejemplo
El ejemplo siguiente se compone de un tipo de biblioteca`SecuredTypeWithFields`() con campos no seguros, un tipo (`Distributor`) que puede crear instancias del tipo de biblioteca y las instancias de pasadas erróneas a tipos no tienen permiso para crearlas, y el código de aplicación que puede leer los campos de una instancia aunque no tenga el permiso que protege el tipo.

El código de biblioteca siguiente infringe la regla.

[!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Ejemplo 1
La aplicación no puede crear una instancia debido a la petición de vínculo que protege el tipo protegido. La siguiente clase permite a la aplicación obtener una instancia del tipo protegido.

[!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Ejemplo 2
La siguiente aplicación muestra cómo, sin permiso para tener acceso a los métodos de un tipo protegido, el código puede tener acceso a sus campos.

[!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Reglas relacionadas

- [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también

- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)