---
title: 'DA0010: GetHashCode que consume muchos recursos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2a1ddeb2b12d592c93bb0e5b88ba76c1b01c3c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936558"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: GetHashCode que consume muchos recursos

|||
|-|-|
|Identificador de regla|DA0010|
|Categoría|Uso de .NET Framework|
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|
|Mensaje|Las funciones GetHashCode deben consumir pocos recursos y no asignar ninguna memoria. Reduzca la complejidad de la función de código hash si es posible.|
|Tipo de mensaje|Advertencia|

## <a name="cause"></a>Motivo
 Las llamadas al método GetHashCode del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método asigna memoria.

## <a name="rule-description"></a>Descripción de la regla
 La técnica de hash permite localizar rápidamente un elemento determinado en una colección grande. Dado que las tablas hash pueden ser grandes y tienen que admitir velocidades de acceso muy altas, deben ser eficaces. Una implicación de este requisito es que los métodos GetHashCode en .NET Framework no deben asignar memoria. La asignación de memoria aumenta la carga en el recolector de elementos no utilizados y expone al método a posibles retrasos si es necesario ejecutar la recopilación de elementos no utilizados como resultado de la solicitud de asignación.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Reduzca la complejidad del método.