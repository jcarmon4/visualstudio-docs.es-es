---
title: 'CA1040: Evitar las interfaces vacías'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 491923cb46100e9239b889024ade00022318b6cd
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547705"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitar las interfaces vacías

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|Identificador de comprobación|CA1040|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa

La interfaz no declara ningún miembro ni implementa dos o más interfaces.

De forma predeterminada, esta regla solo busca interfaces visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro. Por lo tanto, no define un contrato que se pueda implementar.

Si el diseño incluye interfaces vacías que se espera que implementen, probablemente esté usando una interfaz como un marcador o una manera de identificar un grupo de tipos. Si esta identificación se va a producir en tiempo de ejecución, la manera correcta de lograrlo es usar un atributo personalizado. Utilice la presencia o ausencia del atributo, o las propiedades del atributo, para identificar los tipos de destino. Si la identificación debe realizarse en tiempo de compilación, es aceptable usar una interfaz vacía.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Quite la interfaz o Agréguele miembros. Si la interfaz vacía se usa para etiquetar un conjunto de tipos, reemplace la interfaz por un atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla cuando la interfaz se utiliza para identificar un conjunto de tipos en tiempo de compilación.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1040.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una interfaz vacía.

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]