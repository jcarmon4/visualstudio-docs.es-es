---
title: Diagramas de secuencia de propiedades de elementos de UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a6008566f71a241fb5daccab8d6a5dcb68882452
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444410"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propiedades de los elementos de diagramas de secuencia de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de secuencia UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
> Este tema trata sobre las propiedades de los elementos de los diagramas de secuencia UML. Para obtener más información sobre cómo leer diagramas de secuencia UML, vea [diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de secuencia UML, vea [diagramas de secuencia UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Propiedad|Default|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todas|Identifica el elemento.|  
|**Nombre completo**|Paquete:: Name|Todas|Identifica de forma única el elemento. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Los elementos de trabajo**|0 asociados|Todas|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(en blanco)|Todas|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(valor predeterminado para el tipo de elemento)|Línea de vida, mensaje|Color de la forma. Se trata de una propiedad de la forma, no del elemento que muestra.|  
|**Type**|(en blanco)|Lifeline|El tipo de la instancia que representa la línea de vida.<br /><br /> Si hay un símbolo de referencia que se muestra en el encabezado de la línea de vida, esta clase o interfaz existe por separado en el Explorador de modelos UML y puede aparecer en un diagrama de clases.|  
|**Actor**|False|Lifeline|Indica si la línea de vida representa un componente de usuario, dispositivo o software que es externo al componente al que hace referencia el diagrama.|  
|**Kind**|**Completa** -un mensaje con remitente y receptor.<br /><br /> **Se encontró** -un mensaje que tiene un remitente no especificado.<br /><br /> **Perdido** -un mensaje que tiene un destinatario no especificado.|Mensaje|Indica qué extremos de un mensaje están unidos a una línea de vida.<br /><br /> Esta propiedad no se puede cambiar. Se establece cuando se crea el mensaje.|  
|**Sort**|**AsynchCall** -un mensaje asincrónico.<br /><br /> **SynchCall** -un mensaje sincrónico.<br /><br /> **Respuesta** -elemento devuelto de un mensaje sincrónico.<br /><br /> **CreateMessage** -creación de una mensaje de instancia.|Mensaje|El tipo de mensaje. Esta propiedad no se puede cambiar. Viene determinado por la herramienta que usa para crear el mensaje.|  
|**Operación**|(vacío)|Mensaje|Un método llamado por el mensaje en la línea de vida receptora.<br /><br /> Sólo está visible si la línea de vida receptora está vinculada a una interfaz o una clase.|  
|**Hace referencia a**|Diagrama de secuencia|Interaction Use|Diagrama de secuencia llamado por uso de interacción.|  
|**Operador de interacción**|Establece cuando se utiliza el **rodear con** comando|Fragmento combinado|Operador representado por este fragmento o colección de fragmentos.|  
|**Guard**|(vacío)|Operando de interacción de un fragmento combinado|La secuencia del fragmento no a menos que la restricción sea true.<br /><br /> Para seleccionar el fragmento superior de cualquier fragmento combinado, haga clic debajo del título del fragmento.|  
|**Mín., máx.**|(sin restricción)|Fragmento combinado de bucle|El número mínimo y máximo de veces que se ejecuta el bucle.|  
|**Mensajes**|(vacío)|Tener en cuenta y<br /><br /> omitir fragmentos combinados|Los mensajes que se tienen en cuenta o se omiten en este fragmento.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de secuencia de UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramas de secuencia de UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Describir el flujo de control con fragmentos de diagramas de secuencia de UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
