---
title: 'CA1713: Los eventos no deben tener prefijos antes ni después'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee39ffbfd2e73a14fd42d574cef92a24784d1ad4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921669"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Los eventos no deben tener prefijos antes ni después

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|Identificador de comprobación|CA1713|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
El nombre de un evento empieza por ' Before ' o ' After '.

## <a name="rule-description"></a>Descripción de la regla
Los nombres de evento deben describir la acción que genera el evento. Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones. Por ejemplo, al asignar un nombre a un par de eventos que se genera al cerrar un recurso, puede asignarle el nombre ' closing ' y ' Closed ', en lugar de ' BeforeClose ' y ' AfterClose '.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Quite el prefijo del nombre del evento y considere la posibilidad de cambiar el nombre para utilizar el pasador presente o pasado de un verbo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.