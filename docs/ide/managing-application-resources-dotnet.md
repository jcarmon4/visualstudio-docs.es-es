---
title: Administrar los recursos de la aplicación (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1681484500c382b296a03e78661b808825768a5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538114"
---
# <a name="manage-application-resources-net"></a>Administrar los recursos de la aplicación (.NET)

Los archivos de recursos son archivos que forman parte de una aplicación, pero no se compilan. Un ejemplo de estos archivos son los  archivos de icono de ejemplo o los archivos de audio. Puesto que estos archivos no forman parte del proceso de compilación, se pueden cambiar sin tener que volver a compilar los archivos binarios. Si piensa localizar la aplicación, debe usar los archivos de recursos para todas las cadenas y los demás recursos que deben cambiarse al localizar la aplicación.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Administración de recursos de aplicación (Visual Studio para Mac)](/visualstudio/mac/managing-app-resources).

Para obtener más información sobre los recursos de las aplicaciones de escritorio de .NET, vea [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Trabajar con recursos

En un proyecto de código administrado, abra la ventana de propiedades del proyecto. Puede abrir la ventana Propiedades de cualquiera de estas maneras:

- Hacer clic con el botón derecho en el nodo de proyecto en el **Explorador de soluciones** y seleccionar **Propiedades**.
- Escribir las **propiedades del proyecto** en el cuadro de búsqueda **Ctrl**+**Q**
- Presionar **Alt**+**Entrar** en el **Explorador de soluciones**

Seleccione la pestaña **Recursos** . Puede agregar un archivo *.resx* si el proyecto no contiene ninguno y luego agregar y eliminar diferentes tipos de recursos y modificar recursos existentes.

## <a name="resources-in-other-project-types"></a>Recursos en otros tipos de proyecto

Los recursos se administran de manera diferente en los proyectos de .NET que en otros tipos de proyecto. Para obtener más información sobre los recursos en:

- Aplicaciones de la Plataforma universal de Windows (UWP), vea [Recursos de aplicaciones y sistema de administración de recursos](/windows/uwp/app-resources/)
- Proyectos de C++, vea [Trabajar con archivos de recursos](/cpp/windows/working-with-resource-files) y [Cómo: Crear un recurso](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Vea también

- [Recursos de aplicaciones de escritorio (.NET Framework)](/dotnet/framework/resources/index)
- [Administración de recursos de aplicación (Visual Studio para Mac)](/visualstudio/mac/managing-app-resources)
