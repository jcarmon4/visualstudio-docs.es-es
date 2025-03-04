---
title: Buscar problemas potenciales mediante analizadores de mapas de código | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd771cf35ef684edd8d5c9dd82436759ec9443a3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437498"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Buscar posibles problemas mediante analizadores de mapas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ejecute analizadores en mapas de código para identificar código demasiado complejo o que sea necesario mejorar. Por ejemplo, puede usar estos analizadores:  
  
|**Para buscar código que incluya**|**Examine estas áreas para ver si:**|  
|-------------------------------|--------------------------------------------|  
|Bucles o dependencias circulares|Puede simplificarlos y ver si puede interrumpir estos ciclos.|  
|Demasiadas dependencias|Están realizando demasiadas funciones o determinan el impacto de cambiar estas áreas. En un mapa de código correcto, aparecerá un número mínimo de dependencias. Para que el código resulte más fácil de mantener, cambiar, probar y reutilizar, piense si puede refactorizar estas áreas para definirlas de forma más nítida o si puede combinar el código que realiza funciones similares.|  
|Ninguna dependencia|Son necesarias o si debe quitar este código.|  
  
## <a name="analyze-code-maps"></a>Analizar mapas de código  
  
1. En la barra de herramientas del mapa, elija **Diseño**, **Analizadores**y, después, el analizador que desea ejecutar:  
  
   |**Analizador**|**Para identificar nodos que**|  
   |------------------|--------------------------------|  
   |**Analizador de referencias circulares**|Tienen dependencias circulares entre sí. **Nota:**  Las dependencias circulares que se encuentran en el **genéricos** grupo no se muestran en el mapa al expandir el grupo.|  
   |**Buscar analizador de concentradores**|Se encuentran entre el 25 % de los nodos con mayor número de conexiones.<br /><br /> **Para ocultar el resto de nodos del mapa**<br /><br /> -Abra el menú contextual del mapa, elija **avanzadas**, **seleccione**, **ocultar no seleccionados**.<br />     El mapa oculta los nodos no seleccionados y el analizador identifica los nuevos nodos como concentradores.|  
   |**Analizador de nodos a los que no se hace referencia**|No tienen referencias de otros nodos. **Advertencia:**  Compruebe cada uno de estos casos antes de asumir que el código no se usa. Ciertas dependencias, como las dependencias XAML y las dependencias de tiempo de ejecución, no se encuentran de forma estática en el código.|  
  
   Los analizadores de mapa de código continuarán ejecutándose después de aplicarlos. Si cambia el mapa, los analizadores aplicados volverán a procesar automáticamente el mapa actualizado. Para detener la ejecución de un analizador, en la barra de herramientas del mapa, elija **Diseño**, **Analizadores**. Desactive el analizador seleccionado.  
  
> [!TIP]
> Si tiene un mapa muy grade y ejecuta el analizador, podría producirse una excepción de memoria. Si esto ocurre, edite el mapa para reducir su ámbito o genere uno más pequeño y, después, ejecute el analizador.  
  
## <a name="see-also"></a>Vea también  
 [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de código para depurar sus aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
