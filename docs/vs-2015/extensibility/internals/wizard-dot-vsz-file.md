---
title: Asistente (. Archivo vsz) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687663"
---
# <a name="wizard-vsz-file"></a>Archivo de asistente (.Vsz)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El entorno de desarrollo integrado (IDE) utiliza archivos .vsz para iniciar a asistentes. Estos archivos .vsz contienen información que el IDE se usa para determinar cuál es el Asistente para llamar a y qué información se va a pasar al asistente.  
  
 Un archivo .vsz es una versión de un archivo de texto con formato. ini que tiene secciones. Se almacena información conocida para el IDE al principio del archivo. Esto proporciona un vínculo entre el Asistente para la que llama el IDE y los parámetros que se encuentran en el archivo .vsz que se pasarán al IDE. El resto del archivo proporciona los parámetros que son específicos del asistente y que se recopilen por el IDE y pasa al Asistente específico.  
  
 El ejemplo siguiente muestra el contenido de un archivo .vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 A continuación es las partes en el archivo .vsz.  
  
|Parte|Descripción|  
|----------|-----------------|  
|VSWizard|El primer parámetro en el archivo es el número de versión del formato del archivo de plantilla. Este número de versión debe ser 6.0, 7.0, 7.1 u 8.0. Otros números no se puede iniciar y producen un error de formato no válido.|  
|Asistente|Este campo contiene el ProgID de OLE del asistente, o de forma alternativa una representación de cadena GUID del CLSID del asistente que le por el IDE.|  
|Parám|Estas partes son opcionales. Puede agregar tantas como sea necesario.|  
  
 Los parámetros permiten que el archivo .vsz pase parámetros personalizados adicionales al asistente. Cada valor se pasa como un elemento de cadena en una matriz de variantes al asistente. Para obtener más información, consulte [parámetros personalizados](../../extensibility/internals/custom-parameters.md). Para obtener información acerca de cómo usar un archivo .vsz en el desarrollo de asistentes personalizados, vea [. Archivo vsz (Control del proyecto)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Para agregar un identificador de configuración regional predeterminada para el archivo .vsz, especifique `FALLBACK_LCID`= xxxx, donde xxxx es el identificador de configuración regional, por ejemplo, 1033 para inglés. Cuando `FALLBACK_LCID` parámetro está definido, el asistente usa el identificador de configuración regional de reserva proporcionado si no se encuentra el Id. actual.  
  
## <a name="see-also"></a>Vea también  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
