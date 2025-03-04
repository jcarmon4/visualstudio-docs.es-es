---
title: 'CA1822: Marcar el miembro como estático | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42c6f0d333d1f7ee3f657b9c57c4154e9f824128
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201679"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Marcar miembros como estáticos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1822: Marcar el miembro como estático](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static).  
  
|||  
|-|-|  
|TypeName|MarkMethodsAsStatic|  
|Identificador de comprobación|CA1822|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|No problemático: si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: si simplemente cambia el miembro a un miembro de instancia con el `this` palabra clave.<br /><br /> Problemático: si cambia al miembro de un miembro de instancia a un miembro estático y está visible fuera del ensamblado.|  
  
## <a name="cause"></a>Causa  
 Un miembro que no tiene acceso a datos de instancia no está marcado como estático (compartido en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static (Shared en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros. Emisión de sitios de llamada no virtuales evitará que una comprobación en tiempo de ejecución para cada llamada que se asegura de que el puntero del objeto actual no es null. Esto puede lograr una mejora del rendimiento cuantificable para código sensibles al rendimiento. En algunos casos, el error para obtener acceso a la instancia del objeto actual representa un problema de corrección.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Marque el miembro como estático (o se compartirá [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) o use 'this' / '' en el método de cuerpo, si procede.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla para código lanzado al mercado anteriormente para que la solución sería un cambio importante.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1811: Evitar código privado fuera de lugar](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Quitar a variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
