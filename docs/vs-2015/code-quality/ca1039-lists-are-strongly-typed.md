---
title: 'CA1039: Las listas están fuertemente tipadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3fb1a6255539ded989c5ad9638fc961d606a19f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559757"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Las listas están fuertemente tipadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|Identificador de comprobación|CA1039|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Tipo de público o protegido implementa <xref:System.Collections.IList?displayProperty=fullName> pero no proporciona un método fuertemente tipado para uno o varios de los siguientes:

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>Descripción de la regla
 Esta regla requiere <xref:System.Collections.IList> miembros de las implementaciones proporcionen fuertemente tipados para que los usuarios no deben convertir los argumentos en el <xref:System.Object?displayProperty=fullName> escriba cuando utilicen la funcionalidad proporcionada por la interfaz. El <xref:System.Collections.IList> interfaz se implementa mediante colecciones de objetos que se pueden acceder por índice. Esta regla supone que el tipo que implementa <xref:System.Collections.IList> hace esto para administrar una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.

 <xref:System.Collections.IList> implementa el <xref:System.Collections.ICollection?displayProperty=fullName> y <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaces. Si implementa <xref:System.Collections.IList>, debe proporcionar los miembros fuertemente tipados necesarios para <xref:System.Collections.ICollection>. Si los objetos de la colección extienden <xref:System.ValueType?displayProperty=fullName>, debe proporcionar un miembro fuertemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar la disminución del rendimiento debida a la conversión boxing; esto no es necesario cuando los objetos de la colección son un tipo de referencia.

 Para cumplir con esta regla, implemente los miembros de interfaz explícitamente mediante el uso de nombres en el formulario InterfaceName.InterfaceMemberName, como <xref:System.Collections.IList.Add%2A>. Los miembros de interfaz explícita utilicen los tipos de datos que se declaran por la interfaz. Implemente los miembros fuertemente tipados con el nombre de miembro de interfaz, como `Add`. Declare los miembros fuertemente tipados como pública y declarar los parámetros y devuelven los valores sean del tipo seguro que está administrado por la colección. Los tipos seguros reemplace tipos más débiles como <xref:System.Object> y <xref:System.Array> que se declaran mediante la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente explícitamente <xref:System.Collections.IList> miembros y proporcionar alternativas fuertemente tipadas para los miembros que se indicaron anteriormente. Para el código que implementa correctamente el <xref:System.Collections.IList> interfaz y proporciona los miembros fuertemente tipados, vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla al implementar una nueva colección basada en objetos, como una lista vinculada, donde los tipos que extienden la nueva colección determinan el tipo seguro. Estos tipos deben cumplir esta regla y exponer miembros fuertemente tipados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, el tipo `YourType` extiende <xref:System.Collections.CollectionBase?displayProperty=fullName>, así como todas las colecciones fuertemente tipadas. Tenga en cuenta que <xref:System.Collections.CollectionBase> proporciona la implementación explícita de la <xref:System.Collections.IList> una interfaz. Por lo tanto, debe proporcionar solo los miembros fuertemente tipados para <xref:System.Collections.IList> y <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vea también
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
