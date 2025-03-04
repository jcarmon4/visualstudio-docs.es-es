---
title: Editor XML y el Diseñador de esquemas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7493d6c10c83b16ad7579299a49a7747e34c20b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746516"
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio

*Extensible Markup Language (XML)* es un lenguaje de marcado que proporciona un formato para describir los datos. XML separa los datos y asociados de su presentación mediante el uso de hojas de estilos como lenguaje de hojas de estilo Extensible (XSL) y hojas de estilos en cascada (CSS). Visual Studio incluye herramientas y características que facilitan el trabajo con XML, XSLT y esquemas XML.

## <a name="xml-editor"></a>Editor XML

El [editor XML](xml-editor.md) se usa para editar documentos XML. Proporciona sintaxis XML completa comprobación de validación de esquemas mientras escribe, codificación en colores e IntelliSense. Cuando se proporciona un esquema o una definición de tipo de documento, IntelliSense lo utiliza para mostrar los elementos y atributos permitidos.

Otras características son:

- Compatibilidad con fragmentos XML, incluye fragmentos generados por esquema

- Para que los elementos se pueden expandir y contraer la esquematización de documentos

- La capacidad para ejecutar transformaciones XSLT y ver los resultados como texto, XML o HTML

- La capacidad para generar esquemas (XSD) del documento de instancia XML

- Compatibilidad con la edición de hojas de estilos XSLT, incluida la compatibilidad con IntelliSense

- Explorador de esquemas XML

## <a name="xml-schema-designer"></a>Diseñador de esquemas XML

El [Diseñador de esquemas XML](xml-schema-designer.md) se integra con Visual Studio y el editor XML para permitirle trabajar con esquemas de lenguaje (XSD) de definición de esquemas XML.

## <a name="xslt-debugging"></a>Depuración de XSLT

Visual Studio admite [depurar hojas de estilos XSLT](../xml-tools/debugging-xslt.md). Mediante el depurador, puede definir puntos de interrupción en una hoja de estilos XSLT, ir a una hoja de estilos XSLT a partir del código, etc.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="see-also"></a>Vea también

- <xref:System.Xml?displayProperty=fullName>
- [Transformaciones XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Procesar datos XML mediante el modelo de datos XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Document Object Model (DOM) para XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Modelo de objetos de esquema XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)