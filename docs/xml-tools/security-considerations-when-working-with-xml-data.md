---
title: Consideraciones de seguridad al trabajar con datos XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe4ec69f879478566cce8d077bb66b34da86f3d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926771"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Consideraciones de seguridad al trabajar con datos XML

En este tema se describen los problemas de seguridad que debe conocer al trabajar con el editor XML o el depurador de XSLT.

## <a name="xml-editor"></a>Editor XML

El editor XML se basa en el editor de texto de Visual Studio. Depende de las clases <xref:System.Xml> y <xref:System.Xml.Xsl> para controlar muchos de los procesos XML.

- Las transformaciones XSLT se ejecutan en un nuevo dominio de aplicación. Las transformaciones XSLT están en *espacio aislado*. es decir, la Directiva de seguridad de acceso del código del equipo se utiliza para determinar los permisos restringidos en función de dónde se encuentra la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

- La clase <xref:System.Xml.Xsl.XslCompiledTransform> se utiliza para compilar el XSLT al lenguaje intermedio de Microsoft con el fin de acelerar el rendimiento durante la ejecución.

- Los esquemas que apuntan a una ubicación externa del archivo de catálogo se descargan automáticamente cuando se carga por primera vez el editor XML. La clase <xref:System.Xml.Schema.XmlSchemaSet> se utiliza para compilar los esquemas. El archivo de catálogo que se incluye con el editor XML no tiene vínculos a esquemas externos. El usuario tiene que agregar explícitamente una referencia al esquema externo antes de que el editor XML Descargue el archivo de esquema. La descarga de HTTP puede deshabilitarse a través de la página **Opciones de herramientas diversas** del editor XML.

- El editor XML utiliza las <xref:System.Net> clases para descargar esquemas

## <a name="xslt-debugger"></a>depurador de XSLT

El depurador de XSLT utiliza el motor de depuración administrado de Visual Studio y las clases del espacio de nombres <xref:System.Xml> y <xref:System.Xml.Xsl>.

- El depurador ejecuta las transformaciones XSLT en un dominio de aplicación sandboxed. Se utiliza la directiva de seguridad de acceso del código del equipo para determinar los permisos restringidos según donde esté ubicada la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

- La hoja de estilos XSLT se compila mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>.

- El evaluador de expresiones XSLT se carga mediante el motor de depuración administrado. Este motor asume que todo el código se ejecuta desde el equipo local del usuario. En consecuencia, la clase <xref:System.Xml.Xsl.XslCompiledTransform> descarga el archivo XSLT en el equipo local del usuario. La posibilidad de que ocurra un aumento en los privilegios de ejecución se mitiga con la ejecución de todas las transformaciones XSLT en un nuevo dominio de aplicación con permisos restringidos

## <a name="see-also"></a>Vea también

- [Dominios de aplicación](/dotnet/framework/app-domains/application-domains)