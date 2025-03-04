---
title: Descripción del directorio de plantilla (. Archivos VSDir) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad06428905f924e0e339882057ee4e657da47e8a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331113"
---
# <a name="template-directory-description-vsdir-files"></a>Archivos de descripción del directorio de plantilla (.Vsdir)
Un archivo de descripción del directorio de plantilla (.vsdir) es un archivo de texto que permite que el entorno de desarrollo integrado (IDE) para mostrar las carpetas, archivos .vsz del asistente y archivos de plantilla que están asociados con el proyecto en los cuadros de diálogo. El contenido incluye un registro por cada archivo o carpeta. Se combinan todos los archivos .vsdir en una ubicación que se hace referencia, aunque generalmente se proporciona solo un archivo .vsdir para describir varias carpetas, los asistentes o los archivos de plantilla.

 Carpetas (subdirectorios), los archivos que se hace referencia en el archivo vsdir y el propio archivo .vsdir se encuentran en el mismo directorio. Cuando el IDE ejecuta un asistente o muestra una carpeta o archivo en el **nuevo proyecto** o **Agregar nuevo elemento** cuadros de diálogo, el IDE examina el directorio que contiene los archivos para determinar si es un archivo .vsdir ejecutados presente. Si se encuentra un archivo VSDir, el IDE lo lee para determinar si contiene una entrada para el archivo o carpeta ejecutada o que se muestran. Si se encuentra una entrada, el IDE usa la información de la ejecución del asistente o presentación del contenido.

 El siguiente ejemplo de código pertenece al archivo SourceFiles.vsdir en el \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files clave de registro:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 En este caso, los dos registros están en un archivo. Una nueva línea (carácter de retorno de carro) separa cada registro. Cada línea representa un tipo de archivo diferente. Una canalización (&#124;) separa los campos de cada registro. Un único directorio puede contener varios archivos .vsdir que tienen nombres de archivo diferente, o puede tener un archivo VSDIR para cada tipo de archivo.

## <a name="fields"></a>Campos
 En la tabla siguiente se enumera los campos especificados para cada registro.

| Campo | Descripción |
| - | - |
| Nombre de ruta de acceso relativa (RelPathName) | El nombre del archivo .vsz, plantilla o carpeta, como HeaderFile.h o MyWizard.vsz. Este campo también puede ser un nombre que se utiliza para representar una carpeta. |
| {clsidPackage} | El GUID del VSPackage que permite el acceso a las cadenas localizadas, como LocalizedName, descripción, IconResourceId y SuggestedBaseName, en recursos de biblioteca (DLL) de vínculos dinámicos de satélite de VSPackage. IconResourceId se aplica si no se proporciona DLLPath. **Nota:**  Este campo es opcional, a menos que uno o varios de los campos anteriores son un identificador de recurso. Este campo está normalmente en blanco para los archivos .vsdir que se corresponden con asistentes de terceros que no traduzca su texto. |
| LocalizedName | El nombre localizado del asistente o archivo de plantilla. Este campo puede ser una cadena o un identificador de recursos de la forma "#ResID". Este nombre se muestra en el **Agregar nuevo elemento** cuadro de diálogo. **Nota:**  Si LocalizedName es un identificador de recurso, a continuación, se requiere {clsidPackage}. |
| SortPriority | Entero que representa la prioridad relativa de este archivo de plantilla o el asistente. Por ejemplo, si este elemento tiene un valor de 1, este artículo se muestra junto a otros elementos con un valor de 1 y por delante de todos los elementos con un valor de ordenación de 2 o superior.<br /><br /> Prioridad de ordenación es relativo a los elementos en el mismo directorio. Puede haber más de un archivo VSDir en el mismo directorio. En ese caso, los elementos de todos los <em>.</em> se combinan archivos VSDir en ese directorio. Los elementos con la misma prioridad se muestran en orden lexicográfico entre mayúsculas y minúsculas del nombre mostrado. El `_wcsicmp` función se usa para ordenar los elementos.<br /><br /> Los elementos que no se describe en los archivos .vsdir incluyen un número de prioridad mayor que el número de prioridad más alto en los archivos .vsdir. El resultado es que estos elementos están al final de la lista mostrada, independientemente de su nombre. |
| Descripción | La descripción localizada del archivo de plantilla o asistente. Este campo puede ser una cadena o un identificador de recursos de la forma "#ResID". Esta cadena aparece en la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo cuando se selecciona el elemento. |
| DLLPath o {clsidPackage} | Se usa para cargar un icono para el archivo de plantilla o el asistente. El icono se carga como un recurso fuera de un archivo .dll o .exe mediante la IconResourceId. Este archivo .dll o .exe puede identificarse mediante el uso de una ruta de acceso completa o mediante el uso de un GUID de un paquete VSPackage. La implementación del archivo DLL del VSPackage se usa para cargar el icono (no el archivo DLL de satélite). |
| IconResourceId | El identificador de recurso en la implementación de VSPackage o DLL DLL que determina el icono para mostrar. |
| Marcas (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Se utiliza para habilitar o deshabilitar la **nombre** y **ubicación** campos de la **Agregar nuevo elemento** cuadro de diálogo. El valor de la **marcas** campo es el equivalente decimal de la combinación de marcas de bits necesarios.<br /><br /> Cuando un usuario selecciona un elemento en el **New** ficha, el proyecto determina si el campo de nombre y el campo de ubicación se muestran cuando el **Agregar nuevo elemento** cuadro de diálogo se muestra por primera vez. Un elemento, mediante un archivo VSDir, puede controlar solo si están habilitados los campos frente a deshabilitado cuando se selecciona el elemento. |
| SuggestedBaseName | Representa el nombre predeterminado para el archivo, el asistente o la plantilla. Este campo es una cadena o un identificador de recursos de la forma "#ResID". El IDE usa este valor para proporcionar un nombre predeterminado para el elemento. Este valor base se anexa con un valor entero y que el nombre sea único, como MyFile21.asp.<br /><br /> En la lista anterior, descripción, DLLPath, IconResourceId, indicadores y SuggestedBaseNumber solo se aplican a los archivos de plantilla y el asistente. Estos campos no se aplican a las carpetas. Este hecho se ilustra en el código en el archivo BscPrjProjectItems el \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems clave de registro. Este archivo contiene tres registros (uno para cada carpeta) con cuatro campos para cada registro: RelPathName, {clsidPackage}, LocalizedName y SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Cuando se crea un archivo de asistente, también debe considerar los siguientes problemas.

- Los campos opcionales para los que no existen datos significativos tienen que contener un cero (0) como marcador de posición.

- Si se proporciona ningún nombre localizado, se usa el nombre de ruta de acceso relativa en el archivo del asistente.

- DLLPath invalida clsidPackage para la ubicación del icono.

- Si se define ningún icono, el IDE sustituye el icono predeterminado para un archivo que tiene esa extensión.

- Si no se proporciona ninguna sugerencia de nombre base, se utiliza 'Project'.

- Si elimina los archivos .vsz, carpetas o archivos de plantilla, debe quitar también los registros asociados desde el archivo vsdir.

## <a name="see-also"></a>Vea también
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)