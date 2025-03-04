---
title: 'CA2105: Campos de matriz deben no ser de solo lectura | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4741b30d1429a1a179328c8fb4b150fc4f920612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154377"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Los campos de matrices no deben ser de solo lectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|Identificador de comprobación|CA2105|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Se declara un campo público o protegido que contiene una matriz de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 Al aplicar el `readonly` (`ReadOnly` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) no se puede cambiar el modificador en un campo que contiene una matriz, el campo para hacer referencia a una matriz distinta. Sin embargo, se pueden cambiar los elementos de la matriz almacenados en un campo de solo lectura. Código que toma decisiones o realiza operaciones que se basan en los elementos de una matriz de solo lectura que se puede acceder públicamente podría contener una vulnerabilidad de seguridad explotable.

 Tenga en cuenta que también tiene un campo público infringe la regla de diseño [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir la vulnerabilidad de seguridad identificada por esta regla, no confíe en el contenido de una matriz de solo lectura que se puede acceder públicamente. Se recomienda encarecidamente que utilice uno de los procedimientos siguientes:

- Reemplace la matriz con una colección fuertemente tipada que no se puede cambiar. Para obtener más información, consulta <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Reemplace el campo público con un método que devuelve un clon de una matriz privada. Dado que el código no se basa en el clon, no hay ningún riesgo si se modifican los elementos.

  Si eligió el segundo enfoque, no debe reemplazar el campo de una propiedad; las propiedades que devuelven matrices afectan negativamente al rendimiento. Para obtener más información, consulte [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Exclusión de una advertencia de esta regla no es recomendable. Se producen casi no hay escenarios donde el contenido de un campo de solo lectura no es importante. Si este es el caso con su escenario, quite el `readonly` modificador en lugar de excluir el mensaje.

## <a name="example"></a>Ejemplo
 Este ejemplo demuestra los peligros de infringir esta regla. La primera parte muestra una biblioteca de ejemplo que tiene un tipo, `MyClassWithReadOnlyArrayField`, que contiene dos campos (`grades` y `privateGrades`) que no son seguras. El campo `grades` es público y, por tanto, es vulnerable a cualquier llamador. El campo `privateGrades` es privado, pero sigue siendo vulnerable porque se devuelve a los autores de llamadas por la `GetPrivateGrades` método. El `securePrivateGrades` campo se expone de forma segura mediante el `GetSecurePrivateGrades` método. Se declara como privado para seguir las buenas prácticas de diseño. La segunda parte muestra código que cambia los valores almacenados en el `grades` y `privateGrades` miembros.

 La biblioteca de clases de ejemplo aparece en el ejemplo siguiente.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Ejemplo
 El código siguiente usa la biblioteca de clases de ejemplo para ilustrar los problemas de seguridad de la matriz de solo lectura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 El resultado de este ejemplo es:

 **Antes de manipulación: Notas: 90, 90, 90 grados privada: 90, 90, 90 grados seguros, 90, 90, 90**
**después de manipulación: Notas: 90, 555, 90 grados privada: 90, 555, 90 secure calificaciones, 90, 90, 90**
## <a name="see-also"></a>Vea también
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
