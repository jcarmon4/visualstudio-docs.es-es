---
title: 'CA2106: Asegurar aserciones | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1fb1968c6e2750f658f39f009c97fbab133cccab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687405"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Proteger las aserciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el llamador, el llamador podría ejecutar código indirectamente mediante el uso de sus permisos. Aserciones sin comprobaciones de seguridad están permitidos únicamente cuando esté seguro de que la aserción no se puede usar de manera perjudicial. Una aserción es inofensiva si el código que se llama es inocuo, o los usuarios no pueden pasar información arbitraria al código que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar una petición de seguridad para el método o su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de revisar cuidadosamente la seguridad.

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
