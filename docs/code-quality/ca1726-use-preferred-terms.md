---
title: 'CA1726: Utilizar términos preferidos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4e068fee014d767b7afcdf8183ac6611b299f36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921583"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizar términos preferidos

|||
|-|-|
|TypeName|UsePreferredTerms|
|Identificador de comprobación|CA1726|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en ensamblados<br /><br /> Sin interrupción: cuando se desencadena en parámetros de tipo|

## <a name="cause"></a>Causa

El nombre de un identificador visible externamente incluye un término para el que existe un término alternativo más apropiado. O bien, el nombre incluye el término marca o marcas.

## <a name="rule-description"></a>Descripción de la regla

Esta regla analiza un identificador en tokens. Cada token único y cada combinación de token doble contigua se comparan con los términos que están integrados en la regla y en la sección desusada de cualquier diccionario personalizado. En la tabla siguiente se muestran los términos que están integrados en la regla y sus alternativas preferidas.

|Término obsoleto|Término preferido|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` o `Flags`|No hay ningún término de reemplazo. No usar.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, reemplace el término por el término alternativo preferido.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla solo si el nombre del identificador es intencionado y está relacionado específicamente con el término original en lugar de con el término preferido.

## <a name="related-rules"></a>Reglas relacionadas
[Advertencias sobre nomenclatura](../code-quality/naming-warnings.md)