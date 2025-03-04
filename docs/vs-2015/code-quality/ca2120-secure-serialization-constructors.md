---
title: 'CA2120: Proteger los constructores de serialización | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ea70b7f9462e3195a78b915691a5069ebd6fe6aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154361"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Proteger los constructores de serializaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|Identificador de comprobación|CA2120|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz, no es una interfaz o delegado y se declara en un ensamblado que permite llamadores parcialmente confiables. El tipo tiene un constructor que toma un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto y un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (la firma del constructor de serialización). Este constructor no está protegido mediante una comprobación de seguridad, pero se protegen uno o más constructores regulares del tipo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa el <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz. El constructor de serialización es necesario y se usa para deserializar o volver a crear los objetos que se han serializado utilizando el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método. Dado que el constructor de serialización asigna e inicializa objetos, las comprobaciones de seguridad que están presentes en constructores regulares también deben estar presentes en el constructor de serialización. Si se infringe esta regla, los llamadores que no se podrían crear una instancia en caso contrario, podrían usar el constructor de serialización para hacer esto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proteja el constructor de serialización con la demanda de seguridad que son idénticas a las que protegen otros constructores.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una infracción de la regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
