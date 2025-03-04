---
title: 'CA1053: Los tipos titulares estáticos no deben tener constructores'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fec59e1d683c7867eb1cad9ae4e796a0815200d4
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604787"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Los tipos titulares estáticos no deben tener constructores predeterminados

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|Identificador de comprobación|CA1053|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

> [!NOTE]
> La regla CA1053 se combina [en CA1052: Los tipos de titulares estáticos deben estar sellados](ca1052-static-holder-types-should-be-sealed.md) en los analizadores de [FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Causa

Un tipo público público o anidado declara solo miembros estáticos y tiene un constructor predeterminado.

## <a name="rule-description"></a>Descripción de la regla

El constructor predeterminado no es necesario porque la llamada a miembros estáticos no requiere una instancia del tipo. Además, dado que el tipo no tiene miembros no estáticos, la creación de una instancia no proporciona acceso a ninguno de los miembros del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el constructor predeterminado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. La presencia del constructor predeterminado sugiere que el tipo no es un tipo estático.