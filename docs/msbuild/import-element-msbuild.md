---
title: Elemento Import (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0dce682aad7ab0d049488a6da9b8ab4f3b444d88
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531708"
---
# <a name="import-element-msbuild"></a>Elemento Import (MSBuild)
Importa el contenido de un archivo de proyecto en otro archivo de proyecto.

\<Project> \<Import>

## <a name="syntax"></a>Sintaxis

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Project`|Atributo necesario.<br /><br /> Ruta de acceso del archivo de proyecto que se va a importar. La ruta puede incluir caracteres comodín. Los archivos coincidentes se importan según el criterio de ordenación. Mediante esta característica, puede agregar código a un proyecto simplemente agregando el archivo de código a un directorio.|
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|
|`Sdk`| Atributo opcional.<br /><br /> Hace referencia a un SDK de proyecto.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguna

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |
| [ImportGroup](../msbuild/importgroup-element.md) | Contiene una colección de elementos `Import` agrupados en una condición opcional. |

## <a name="remarks"></a>Comentarios
 Mediante el elemento `Import` , puede reutilizar código común a muchos archivos de proyecto. Esto facilita el mantenimiento del código, ya que las actualizaciones que realice en el código compartido se propagan a todos los proyectos que lo importen.

 Por convención, los archivos de proyecto compartidos e importados se guardan como archivos *.targets*, pero son archivos de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] estándar. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no impide importar un proyecto con una extensión de nombre de archivo diferente, pero se recomienda usar la extensión *.targets* para mantener la coherencia.

 Las rutas de acceso relativas de los proyectos importados se interpretan en relación con el directorio del proyecto que se importa. Por lo tanto, si un archivo de proyecto se importa en varios archivos de proyecto en ubicaciones diferentes, las rutas de acceso relativas del archivo de proyecto importado se interpretarán de manera diferente para cada proyecto importado.

 Se asignan valores basados en el archivo del proyecto que se importa a todas las propiedades reservadas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] relacionadas con el archivo de proyecto (por ejemplo, `MSBuildProjectDirectory` y `MSBuildProjectFile`) a las que se hace referencia en un proyecto importado.

 Si el proyecto importado no tiene un atributo `DefaultTargets` , los proyectos importados se examinan en el orden en que se importan y se usa el valor del primer atributo `DefaultTargets` detectado. Por ejemplo, si ProyectoA importa ProyectoB y ProyectoC (en ese orden), y ProyectoB importa ProyectoD, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] primero busca el atributo `DefaultTargets` especificado en ProyectoA, después en ProyectoB, luego en ProyectoD y, por último, en ProyectoC.

 El esquema de un proyecto importado es idéntico al de un proyecto estándar. Aunque [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede compilar un proyecto importado, es poco probable que lo haga porque un proyecto importado no suele contener información sobre las propiedades que se establecen o el orden en el que se ejecutan los destinos. El proyecto importado depende del proyecto en el que se importa para obtener esa información.

## <a name="wildcards"></a>Caracteres comodín
 En .NET Framework 4, MSBuild permite caracteres comodín en el atributo Project. Cuando hay caracteres comodín, se ordenan todas las coincidencias encontradas (para la reproducibilidad) y, después, se importan en ese orden como si dicho orden se hubiera establecido explícitamente.

 Esto es útil si quiere ofrecer un punto de extensibilidad para que otra persona pueda importar un archivo sin que usted tenga que agregar explícitamente el nombre del archivo al archivo de importación. Para este propósito, *Microsoft.Common.Targets* contiene la siguiente línea en la parte superior del archivo.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un proyecto que tiene varios elementos y propiedades y que importa un archivo de proyecto general.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [Cómo: Usar el mismo destino en varios archivos de proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
