---
title: Asistentes | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687631"
---
# <a name="wizards"></a>Asistentes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Después de crear un asistente, normalmente desea agregarla a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integra el entorno de desarrollo (IDE) para que otros usuarios puedan usarlo. A continuación, aparece el asistente se ha agregado en el **Agregar nuevo proyecto** o **Agregar nuevo elemento** cuadros de diálogo. Para ver el **Agregar nuevo proyecto** o **Agregar nuevo elemento** diálogo cuadros, haga clic en una solución abierta en **el Explorador de soluciones**, apunte a **agregar**, y a continuación, haga clic en **nuevo proyecto** o **nuevo elemento**.  
  
 Los asistentes pueden implementarse en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para permitir que los usuarios Seleccione desde una vista de árbol de valores disponibles cuando abran el **Agregar nuevo proyecto** cuadro de diálogo o la **Agregar nuevo elemento** cuadro de diálogo, o cuando haga clic en un elemento de **el Explorador de soluciones**.  
  
 En el asistente, puede proporcionar la opción de localizar el nombre de un nuevo proyecto o ITE y puede determinar el icono de que los usuarios verán cuando seleccionen el asistente. También puede controlar el orden en que aparecen elementos nuevos en relación con otros elementos disponibles; no es necesario que los elementos organizarse alfabéticamente.  
  
 También puede proporcionar a un asistente que se inicia de forma diferente, según los parámetros personalizados que se pasan al asistente cuando se abre.  
  
 Los temas de esta sección describen los archivos que implementan para que se produzca la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo para mostrar el Asistente entre las plantillas y los asistentes disponibles y los requisitos que el asistente debe cumplir para que funcione correctamente en el IDE.  
  
## <a name="in-this-section"></a>En esta sección  
 [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Proporciona información general de qué plantilla de archivos de descripción de directorio y se explica cómo funcionan en el IDE para mostrar las carpetas, archivos .vsz del asistente y archivos de plantilla que están asociados con un proyecto en los cuadros de diálogo.  
  
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explica cómo inicia el IDE de asistentes y enumera las tres partes del archivo .vsz.  
  
 [Interfaz de asistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Describe el `IDTWizard` interfaz que deben implementar los asistentes para trabajar en el IDE.  
  
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)  
 Explica cómo se implementan los asistentes y lo que ocurre cuando el IDE pasa los parámetros de contexto para la implementación.  
  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)  
 Explica cómo utilizar parámetros personalizados para controlar el funcionamiento del asistente después de que se inicia el asistente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.  
  
 [Tutorial: Crear un asistente](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Muestra cómo crear a un asistente.  
  
 [Ampliación de proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
