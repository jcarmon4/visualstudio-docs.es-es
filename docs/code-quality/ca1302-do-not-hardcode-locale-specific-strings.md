---
title: 'CA1302: No codificar las cadenas específicas de configuración regional'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0b3789b5e786038c2bf1fe5e823a1b0fb4f7a7c9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922723"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: No codificar las cadenas específicas de configuración regional

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|Identificador de comprobación|CA1302|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un método utiliza un literal de cadena que representa parte de la ruta de acceso de ciertas carpetas del sistema.

## <a name="rule-description"></a>Descripción de la regla
La <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumeración contiene miembros que hacen referencia a carpetas especiales del sistema. Las ubicaciones de estas carpetas pueden tener valores diferentes en distintos sistemas operativos, el usuario puede cambiar algunas de las ubicaciones y se localizan las ubicaciones. Un ejemplo de una carpeta especial es la carpeta del sistema, que es "C:\windows\system32" [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] en, pero "C:\winnt\system32 [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]" en. El <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> método devuelve las ubicaciones que están asociadas a la <xref:System.Environment.SpecialFolder> enumeración. Las ubicaciones devueltas por <xref:System.Environment.GetFolderPath%2A> se localizan y son adecuadas para el equipo que se está ejecutando actualmente.

Esta regla acorta las rutas de acceso de carpetas que se recuperan mediante el <xref:System.Environment.GetFolderPath%2A> método en niveles de directorio independientes. Cada literal de cadena se compara con los tokens. Si se encuentra una coincidencia, se supone que el método está compilando una cadena que hace referencia a la ubicación del sistema asociada al token. Para la portabilidad y la localizabilidad, <xref:System.Environment.GetFolderPath%2A> utilice el método para recuperar las ubicaciones de las carpetas especiales del sistema en lugar de utilizar literales de cadena.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, recupere la ubicación mediante <xref:System.Environment.GetFolderPath%2A> el método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el literal de cadena no se utiliza para hacer referencia a una de las ubicaciones del sistema asociadas a la <xref:System.Environment.SpecialFolder> enumeración.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se crea la ruta de acceso de la carpeta de datos de la aplicación común, que genera tres advertencias de esta regla. A continuación, en el ejemplo se recupera la ruta de <xref:System.Environment.GetFolderPath%2A> acceso mediante el método.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1303: No pasar literales como parámetros localizados](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)