---
title: SortOrder (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edab3547a16f32f3a8177b3efa7a342c4aae5955
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331855"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder (Elemento, Plantillas de Visual Studio)
Especifica un valor que se utiliza para organizar la plantilla, entre otras plantillas en la misma categoría, tal como aparece en el el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.

 \<VSTemplate> \<TemplateData> \<SortOrder>

## <a name="syntax"></a>Sintaxis

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Un `integer` que representa el valor de criterio de ordenación.

## <a name="remarks"></a>Comentarios
 `SortOrder` es un elemento opcional. El valor predeterminado es 100 y todos los valores deben ser múltiplos de 10.

 El `SortOrder` elemento se omite para las plantillas creadas por el usuario. Todas las plantillas creadas por el usuario se ordenan alfabéticamente.

 Las plantillas que tienen valores de ordenación bajos aparecen en uno el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo antes de las plantillas que tienen valores de ordenación alta.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los metadatos de un estándar [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla de clase.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 En este ejemplo, el `SortOrder` elemento es relativamente alto. Es probable que otros [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tendrán las plantillas de elemento un `SortOrder` inferior al valor `290` y aparecerá antes de esta plantilla en el **nuevo elemento** cuadro de diálogo.

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)