---
title: Procedimiento Modelar un terreno en 3D | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90a24ef7b5bff321d460834a8fdde24e3e6cfd75
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434443"
---
# <a name="how-to-model-3-d-terrain"></a>Procedimiento Modelo terreno en 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Editor de modelos para crear un modelo de terreno en 3D.  
  
 Este documento muestra estas actividades:  
  
- Agregar objetos a una escena  
  
- Selección de caras y puntos  
  
- Trasladar selecciones  
  
- Usar la herramienta **Subdividir cara**  
  
- Enmarcar un objeto en la superficie de diseño  
  
## <a name="creating-a-3-d-terrain-model"></a>Crear un modelo de terreno en 3D  
 Puede crear un terreno en 3D subdividiendo un plano para crear caras adicionales y después manipulando los vértices para crear características de terreno interesantes.  
  
 Cuando termine, el modelo debe tener este aspecto:  
  
 ![Escena 3D que muestra un modelo de terreno](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>Para crear un modelo de terreno en 3D  
  
1. Cree un modelo 3D con el que trabajar. Para obtener información sobre cómo agregar un modelo al proyecto, vea la sección Introducción de [Editor de modelos](../designers/model-editor.md).  
  
2. Agregue un plano a la escena. En el **Cuadro de herramientas**, en **Formas**, seleccione **Plano** y muévalo a la superficie de diseño.  
  
   > [!TIP]
   > Para facilitar el trabajo con el objeto de plano, también puede enmarcarlo en la superficie de diseño. En el modo **Seleccionar**, seleccione el objeto de plano y, después, en la barra de herramientas del Editor de modelos, pulse el botón **Objeto de marco**.  
  
3. Cambie al modo de selección de caras. En la barra de herramientas del Editor de modelos, elija **Seleccionar cara**.  
  
4. Subdivida el plano. En el modo de selección de cara, elija el plano una vez para activarlo para la selección y, después, vuelva a elegirlo para seleccionar su única cara. En la barra de herramientas del Editor de modelos, haga clic en **Subdividir cara**. Esto agrega vértices nuevos al plano que lo dividen en cuatro particiones de igual tamaño.  
  
5. Cree más subdivisiones. Con las caras nuevas aún seleccionadas, elija **Subdividir cara** dos veces más. Esto crea un total de 64 caras. Mediante la creación de más subdivisiones, puede dar incluso más detalles al terreno.  
  
6. Cambie al modo de selección de punto. En la barra de herramientas del Editor de modelos, elija **Seleccionar punto**.  
  
7. Modifique un punto para crear una característica de terreno. En el modo de selección de punto, seleccione uno de los puntos y, después, en la barra de herramientas del Editor de modelos, elija la herramienta **Trasladar**. Aparecerá un cuadro que representa el punto en la superficie de diseño. Use la flecha verde para mover el cuadro y, por tanto, modificar el alto del punto. Repita este paso con diferentes puntos para crear características interesantes de terreno.  
  
   > [!TIP]
   > Puede seleccionar varios puntos a la vez para modificarlos de forma uniforme.  
  
   El modelo de terreno está completado. Este es el modelo final de nuevo, con sombreado Phong aplicado:  
  
   ![Escena 3D que muestra un modelo de terreno](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
   Puede usar este modelo de terreno para mostrar el efecto del sombreador de degradado que se describe en [Cómo: Crear un sombreador de degradado basado en geometría](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Vea también  
 [Editor de modelos](../designers/model-editor.md)
