---
title: 'CA2103: Revisar la seguridad imperativa'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7acbb9d0127dd2ddb6668e72db8fa88124ec2b3c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921425"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Revisar la seguridad imperativa

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|Identificador de comprobación|CA2103|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método utiliza la seguridad imperativa y podría estar creando el permiso utilizando la información de estado y los valores devueltos que pueden cambiar mientras la solicitud está activa.

## <a name="rule-description"></a>Descripción de la regla
La seguridad imperativa utiliza objetos administrados para especificar permisos y acciones de seguridad durante la ejecución del código, en comparación con la seguridad declarativa, que utiliza atributos para almacenar permisos y acciones en los metadatos. La seguridad imperativa es muy flexible, ya que puede establecer el estado de un objeto de permiso y seleccionar acciones de seguridad mediante la información que no está disponible hasta el tiempo de ejecución. Junto con esa flexibilidad, existe el riesgo de que la información en tiempo de ejecución que se usa para determinar el estado de un permiso no se modifique, siempre y cuando la acción esté en vigor.

Utilice la seguridad declarativa siempre que sea posible. Las peticiones declarativas son más fáciles de entender.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Revise las demandas de seguridad imperativa para asegurarse de que el estado del permiso no se basa en la información que puede cambiar siempre que se use el permiso.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el permiso no depende de los datos modificados. Sin embargo, es mejor cambiar la demanda imperativa a su equivalente declarativo.

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Datos y modelado](/dotnet/framework/data/index)