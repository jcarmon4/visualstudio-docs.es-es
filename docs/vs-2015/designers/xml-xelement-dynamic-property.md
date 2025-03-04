---
title: Xml (Propiedad dinámica de XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148047"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtiene el contenido XML sin formato del elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Un <xref:System.String> que representa el contenido XML sin formato del elemento.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Otras referencias  
 [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valor](../designers/value-xelement-dynamic-property.md)
