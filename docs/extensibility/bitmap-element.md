---
title: Elemento de mapa de bits | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cba0f5ccd3228466740a9fb907e6c20ce5400c48
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333581"
---
# <a name="bitmap-element"></a>Bitmap (elemento)
Define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo.

## <a name="syntax"></a>Sintaxis

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Obligatorio. GUID del identificador de comando/identificador de GUID.<br /><br /> El atributo de guid para un mapa de bits no está asociado con cualquier VSPackage u otro grupo de comandos.  Debe ser único para la definición del mapa de bits y no debe usarse para ningún otro propósito.|
|resID|Id. del identificador de comando/identificador de GUID. Se requiere el resID o el atributo href.<br /><br /> El atributo resID es un identificador de recurso de entero que determina la Tira de mapa de bits que se va a cargar durante la combinación de tabla de comandos.  Cuando se carga la tabla de comandos, se cargarán los mapas de bits especificado por el identificador de recurso del recurso del mismo módulo.|
|usedList|Requerido si está presente el atributo resID. Selecciona las imágenes disponibles en la Tira de mapa de bits.|
|href|Ruta de acceso al mapa de bits. Se requiere el resID o el atributo href.<br /><br /> La ruta de inclusión se busca el archivo de imagen indicado, que está incrustado en el archivo binario resultante.  Durante la combinación de tabla de comandos, se copia la imagen y es necesaria ninguna búsqueda de recursos adicionales o carga.  Si no está presente el atributo usedList, están disponibles todas las imágenes en la franja. **Nota:**  Las imágenes pueden proporcionarse en uno de los distintos formatos que incluyen *.bmp*, *.png*, y *.gif*.  Las versiones anteriores del compilador no eran compatibles con las imágenes de mapa de bits de 32 bits que tenían información alfa para la transparencia parcial. La solución alternativa para estas versiones es utilizar el *.png* formato.|
|Condición|Opcional. Consulte [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Bitmaps (elemento)](../extensibility/bitmaps-element.md)|Agrupa los elementos de mapa de bits.|

## <a name="example"></a>Ejemplo

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Vea también
- [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)