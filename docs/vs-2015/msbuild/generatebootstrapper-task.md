---
title: GenerateBootstrapper (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 488caf02a20b4f0855df1ba2ef64c85e70e1a6a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149634"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proporciona una forma automatizada de detectar, descargar e instalar una aplicación y sus requisitos previos. Actúa como instalador único que integra los instaladores independientes de todos los componentes que forman una aplicación.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `GenerateBootstrapper` .  
  
- `ApplicationFile`  
  
   Parámetro `String` opcional.  
  
   Especifica el archivo que utilizará el programa previo para iniciar la instalación de la aplicación una vez instalados todos los requisitos previos. Se producirá un error de compilación si no se especifican los parámetros `BootstrapperItems` ni `ApplicationFile`.  
  
- `ApplicationName`  
  
   Parámetro `String` opcional.  
  
   Especifica el nombre de la aplicación que va a instalar el programa previo. Este nombre aparecerá en la interfaz de usuario que el programa previo utiliza durante la instalación.  
  
- `ApplicationRequiresElevation`  
  
   Parámetro `Boolean` opcional.  
  
   Si `true`, el componente se ejecuta con permisos elevados cuando se instala en un equipo de destino.  
  
- `ApplicationUrl`  
  
   Parámetro `String` opcional.  
  
   Especifica la ubicación web que hospeda el instalador de la aplicación.  
  
- `BootstrapperComponentFiles`  
  
   Parámetro de salida `String[]` opcional.  
  
   Especifica la ubicación generada de los archivos de paquete de programa previo.  
  
- `BootstrapperItems`  
  
   Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.  
  
   Especifica los productos que se van a compilar en el programa previo. Los elementos pasados a este parámetro deben tener la sintaxis siguiente:  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   El atributo `Include` se utiliza para representar el nombre de un requisito previo que debe estar instalado. Los metadatos del elemento `ProductName` son opcionales, y el motor de compilación los utilizará como un nombre descriptivo en caso de que no se encuentre el paquete. Estos elementos no son parámetros de entrada [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] requeridos, salvo que no se especifique ningún `ApplicationFile`. Debe incluir un elemento para cada requisito previo que se debe instalar para la aplicación.  
  
   Se producirá un error de compilación si no se especifican los parámetros `BootstrapperItems` ni `ApplicationFile`.  
  
- `BootstrapperKeyFile`  
  
   Parámetro de salida `String` opcional.  
  
   Especifica la ubicación de compilación de setup.exe.  
  
- `ComponentsLocation`  
  
   Parámetro `String` opcional.  
  
   Especifica una ubicación en que el programa previo va a buscar los requisitos previos de instalación que se deben instalar. Este parámetro puede tener los valores siguientes:  
  
  - `HomeSite`: Indica que el proveedor del componente hospeda el requisito previo.  
  
  - `Relative`: Indica que el requisito previo está en la misma ubicación de la aplicación.  
  
  - `Absolute`: Indica que todos los componentes deben encontrarse en una dirección URL centralizada. Este valor debe utilizarse junto con el parámetro de entrada `ComponentsUrl`.  
  
    Si `ComponentsLocation` no se especifica, `HomeSite` se utiliza de forma predeterminada.  
  
- `ComponentsUrl`  
  
   Parámetro `String` opcional.  
  
   Especifica la dirección URL que contiene los requisitos previos de instalación.  
  
- `CopyComponents`  
  
   Parámetro `Boolean` opcional.  
  
   Si `true`, el programa previo copia todos los archivos de salida en la ruta de acceso especificada en el parámetro `OutputPath`. Todos los valores del parámetro `BootstrapperComponentFiles` deben basarse en esta ruta de acceso. Si `false`, los archivos no se copian y los valores de `BootstrapperComponentFiles` se basan en el valor del parámetro `Path`.  El valor predeterminado de este parámetro es `true`.  
  
- `Culture`  
  
   Parámetro `String` opcional.  
  
   Especifica la referencia cultural que se utilizará para la interfaz de usuario del programa previo y los requisitos previos de instalación. Si la referencia cultural especificada no está disponible, la tarea utiliza el valor del parámetro `FallbackCulture`.  
  
- `FallbackCulture`  
  
   Parámetro `String` opcional.  
  
   Especifica la referencia cultural secundaria que se utilizará para la interfaz de usuario del programa previo y los requisitos previos de instalación.  
  
- `OutputPath`  
  
   Parámetro `String` opcional.  
  
   Especifica la ubicación en que se copiarán setup.exe y todos los archivos de paquete.  
  
- `Path`  
  
   Parámetro `String` opcional.  
  
   Especifica la ubicación de todos los paquetes de requisitos previos disponibles.  
  
- `SupportUrl`  
  
   Parámetro `String` opcional.  
  
   Especifica la dirección URL que se debe proporcionar si se produce un error en la instalación del programa previo.  
  
- `Validate`  
  
   Parámetro `Boolean` opcional.  
  
   Si `true`, el programa previo realiza una validación XSD en los elementos del programa previo de entrada especificados. El valor predeterminado de este parámetro es `false`.  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `GenerateBootstrapper` para instalar una aplicación que debe tener [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] instalado como requisito previo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
