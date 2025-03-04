---
title: Trabajar con código de Visual C++ (Diseñador de clases) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ebe8c65748ba0380a7c4f171d940c3d78f52a577
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698082"
---
# <a name="working-with-visual-c-code-class-designer"></a>Trabajar con código de Visual C++ (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de clases muestra una superficie de diseño visual denominada *diagrama de clases* que ofrece una representación visual de los elementos de código del proyecto. Puede usar diagramas de clases para diseñar y visualizar clases y otros tipos en un proyecto.  
  
 El Diseñador de clases admite los siguientes elementos de código de C++:  
  
- Clase (se asemeja a una forma de clase administrada, salvo que puede tener varias relaciones de herencia)  
  
- Clase anónima (muestra el nombre de la vista de clase que se genera para el tipo anónimo)  
  
- Clase de plantilla  
  
- Struct  
  
- Enum  
  
- Macro (muestra la vista posterior al proceso de la macro)  
  
- Definición de tipo  
  
> [!NOTE]
> No es igual que el diagrama de clases UML, que se puede crear en un proyecto de modelado. Para obtener más información, vea [Diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md).  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>Solucionar problemas de visualización y resolución de tipos  
  
### <a name="location-of-source-files"></a>Ubicación de archivos de origen  
 El Diseñador de clases no mantiene un seguimiento de la ubicación de los archivos de origen. Por lo tanto, si modifica la estructura del proyecto o mueve archivos de origen en el proyecto, el Diseñador de clases puede perder la pista del tipo (sobre todo del tipo de origen de una definición de tipo, clases base o tipos de asociación). Puede que obtenga un error, como **El Diseñador de clases no puede mostrar este tipo**. Si lo recibe, arrastre otra vez el código fuente modificado o reubicado al diagrama de clases para volver a mostrarlo.  
  
### <a name="update-and-performance-issues"></a>Actualización y problemas de rendimiento  
 En los proyectos de Visual C++, puede tardarse entre 30 y 60 segundos para que un cambio en el archivo de código fuente aparezca en el diagrama de clases. Es posible que este retraso también provoque que el Diseñador de clases produzca el error **No se encontraron tipos en la selección**. Si recibe un error de este tipo, haga clic en **Cancelar** en el mensaje de error y espere a que el elemento de código aparezca en la vista de clases. Después de esto, el Diseñador de clases debe poder mostrar el tipo.  
  
 Si un diagrama de clases no se actualiza con los cambios realizados en el código, es posible que tenga que cerrar el diagrama y volver a abrirlo.  
  
### <a name="type-resolution-issues"></a>Problemas de resolución de tipo  
 Puede que el Diseñador de clases no pueda resolver tipos por las razones siguientes:  
  
- El tipo está en un proyecto o ensamblado al que no se hace referencia desde el proyecto que contiene el diagrama de clases. Para corregir este error, agregue una referencia al proyecto o ensamblado que contiene el tipo. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- El tipo no está en el ámbito correcto, por lo que el Diseñador de clases no puede encontrarlo. Asegúrese de que al código no le falta una instrucción `using`, `imports` o `#include`. Asegúrese también de que no quitó el tipo (o un tipo relacionado) del espacio de nombres en el que se encontraba originalmente.  
  
- El tipo no existe (o se convirtió en comentario). Para corregir este error, asegúrese de que no convirtió el tipo en comentario ni lo eliminó.  
  
- El tipo se encuentra en una biblioteca a la que hace referencia una directiva #import. Una posible solución alternativa es agregar manualmente el código generado (archivo .tlh) a una directiva #include en el archivo de encabezado.  
  
  El error que probablemente más va a encontrar para un problema de resolución de tipos es **No se pudo encontrar el código para una o varias formas en el diagrama de clase "\<element>"**. Este mensaje de error no necesariamente indica que el código sea incorrecto. Solo indica que ese diseñador de clases no pudo mostrar el código. Pruebe las siguientes medidas.  
  
- Asegúrese de que el tipo existe. Asegúrese de que no eliminó involuntariamente el código fuente ni lo convirtió en comentario.  
  
- Asegúrese de que el Diseñador de clases admite el tipo especificado. Vea [Limitaciones de los elementos de código C++](#limitations).  
  
- Intente resolver el tipo. Puede que el tipo esté en un proyecto o ensamblado al que no se hace referencia desde el proyecto que contiene el diagrama de clases. Para corregir este error, agregue una referencia al proyecto o ensamblado que contiene el tipo. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Asegúrese de que el tipo está en el ámbito correcto para que el Diseñador de clases pueda encontrarlo. Asegúrese de que al código no le falta una instrucción `using`, `imports` o `#include`. Asegúrese también de que no quitó el tipo (o un tipo relacionado) del espacio de nombres en el que se encontraba originalmente.  
  
### <a name="troubleshooting-other-error-messages"></a>Solucionar problemas de otros mensajes de error  
 Puede encontrar ayuda para solucionar problemas referentes a errores y advertencias en los foros públicos de Microsoft Developer Network (MSDN). Vea el [foro del Diseñador de clases de Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).  
  
## <a name="limitations"></a> Limitaciones de los elementos de código C++  
  
- Cuando se carga un proyecto de Visual C++, Diseñador de clases funciona en modo de solo lectura. Puede cambiar el diagrama de clases, pero no guardar cambios desde el diagrama de clases en el código fuente.  
  
- El Diseñador de clases solo admite semántica de C++ nativa. Para proyectos de Visual C++ que se compilan en código administrado, el Diseñador de clases solo presentará elementos de código que sean tipos nativos. Por lo tanto, puede agregar un diagrama de clases a un proyecto, pero el Diseñador de clases no le permitirá ver los elementos en los que la propiedad `IsManaged` se establece en `true` (es decir, tipos de valor y tipos de referencia).  
  
- Para proyectos de Visual C++, el Diseñador de clases solo lee la definición del tipo. Por ejemplo, suponga que define un tipo en un archivo de encabezado (.h) y define sus miembros en un archivo de implementación (.cpp). Si llama a "Ver diagrama de clases" en el archivo de implementación (.cpp), el Diseñador de clases no muestra nada. Otro ejemplo, si llama a "Ver diagrama de clase" en un archivo .cpp que usa una instrucción `#include` para incluir otros archivos pero no contiene ninguna definición de clase real, el Diseñador de clases tampoco mostrará nada.  
  
- Los archivos IDL (.idl), que definen las interfaces COM y las bibliotecas de tipos, no se muestran en los diagramas a menos que se compilen en código C++ nativo.  
  
- El Diseñador de clases no admite funciones ni variables globales.  
  
- El Diseñador de clases no admite uniones. Se trata de un tipo especial de clase en la que la memoria asignada solo es la cantidad necesaria para el miembro de datos más grande de la unión.  
  
- El Diseñador de clases no muestra tipos de datos básicos como `int` y `char`.  
  
- El Diseñador de clases no muestra tipos definidos fuera del proyecto actual si el proyecto no tiene referencias correctas a esos tipos.  
  
- El Diseñador de clases puede mostrar tipos anidados, pero no las relaciones entre un tipo anidado y otros tipos.  
  
- El Diseñador de clases no puede mostrar tipos que sean de tipo void o que deriven de un tipo void.  
  
## <a name="see-also"></a>Vea también  
 [Diseñar y ver clases y tipos](../ide/designing-and-viewing-classes-and-types.md)   
 [Trabajar con clases y otros tipos (Diseñador de clases)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Trabajar con diagramas de clases (Diseñador de clases)](../ide/working-with-class-diagrams-class-designer.md)   
 [Diseñar clases y tipos (Diseñador de clases)](../ide/designing-classes-and-types-class-designer.md)   
 [Información adicional sobre los errores del Diseñador de clases](../ide/additional-information-about-class-designer-errors.md)   
 [Clase de Visual C++ en el Diseñador de clases](../ide/visual-cpp-classes-in-class-designer.md)   
 [Estructuras de Visual C++ en el Diseñador de clases](../ide/visual-cpp-structures-in-class-designer.md)   
 [Enumeraciones de Visual C++ en el Diseñador de clases](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Definiciones de tipos de Visual C++ en el Diseñador de clases](../ide/visual-cpp-typedefs-in-class-designer.md)
