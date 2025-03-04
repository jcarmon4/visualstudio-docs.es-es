---
title: Características de Shell del Diseñador de flujo de trabajo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f732fd66439897b67f150ddb9603b7d67003eff2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431380"
---
# <a name="workflow-designer-shell-features"></a>Características del shell del Diseñador de flujo de trabajo
[!INCLUDE[wfd1](../includes/wfd1-md.md)] se crea a partir de tres áreas de interfaz de usuario principales: la superficie del diseñador, la barra de ruta de navegación que está encima de la superficie y el shell que está debajo. La barra de ruta de navegación, que se encuentra en la parte superior de la pantalla, se utiliza para mostrar la lista de antecesores de la actividad raíz actual. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Cómo: Usar ruta de navegación](../workflow-designer/how-to-use-breadcrumb-navigation.md). La superficie del diseñador, que se encuentra en el centro de la pantalla, se utiliza para crear los flujos de trabajo. El shell, que se encuentra en la parte inferior de la pantalla, contiene diversos botones para administrar la vista actual.  
  
## <a name="shell-features"></a>Características del shell  
 El shell tiene botones a la derecha de la barra que puede utilizar para acercar o alejar el flujo de trabajo, ajustar el contenido del flujo de trabajo según el tamaño de la pantalla y mostrar u ocultar el mapa general. También puede acercar o alejar un flujo de trabajo con los métodos abreviados de teclado CTRL++ y CTRL+ -.  
  
## <a name="overview-map"></a>Mapa general  
 El mapa general muestra una versión reducida de la totalidad de la actividad en la raíz de la ruta de navegación actual, incluso todos sus elementos secundarios y los expandidos. Hay una ventanilla, un rectángulo con un borde naranja, que resalta la parte de la actividad que se muestra en esos momentos en el editor. Si se arrastra el rectángulo en torno al mapa general, se desplaza el diseñador de flujos de trabajo y cambia la vista del editor.  
  
> [!NOTE]
> La interfaz de usuario [!INCLUDE[wfd2](../includes/wfd2-md.md)] está virtualizada. Los diseñadores de actividades se presentan solo cuando se requieran. Si una parte del flujo de trabajo no se ha dibujado nunca en la superficie del diseñador, esa parte aparecerá en blanco en el mapa general. Al desplazarse por el mapa general, se dibuja enteramente el flujo de trabajo.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Copiar o guardar flujos de trabajo como imágenes  
 Los flujos de trabajo se pueden copiar en formato de mapa de bits o guardar en formato de mapa de bits o de vector. Copiar o guardar una imagen ofrece una forma de exportar a otro programa una vista de la totalidad de la actividad en la raíz de la ruta de navegación actual, lo cual incluye todos sus elementos secundarios y los expandidos.  
  
 Para copiar como imagen, haga clic en cualquier lugar en el diseñador y seleccione **copiar como imagen**. Para guardar como imagen, haga clic en cualquier lugar en el diseñador y seleccione **Guardar como imagen**. Los flujos de trabajo pueden guardarse en formato JPG, PNG, GIF o XPS. El formato seleccionado en el **Guardar como** cuadro de diálogo en el **Guardar como tipo:** cuadro de lista en la parte inferior de la ventana de lista desplegable.  
  
## <a name="fonts-and-colors"></a>Fuentes y colores  
 Las fuentes que se utilizan en [!INCLUDE[wfd2](../includes/wfd2-md.md)] dentro de [!INCLUDE[vs2010](../includes/vs2010-md.md)] están controladas por la fuente del entorno. Los colores que se muestran en [!INCLUDE[wfd2](../includes/wfd2-md.md)] cambian si está utilizando una combinación de colores de alto contraste para el tema del sistema operativo. Debe reiniciar [!INCLUDE[vs2010](../includes/vs2010-md.md)] tras realizar un cambio en la fuente o configuración del color antes de que los cambios surtan efecto en [!INCLUDE[wfd2](../includes/wfd2-md.md)].