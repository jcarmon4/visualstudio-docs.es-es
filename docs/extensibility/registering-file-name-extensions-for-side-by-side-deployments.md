---
title: Registrar las extensiones de nombre de archivo para las implementaciones en paralelo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bdfb562ddfcce2584b8868c3c931c21f9dbc127
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334225"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Registrar extensiones de nombre de archivo para las implementaciones en paralelo
Para los paquetes VSPackage implementados en un entorno en paralelo, debe registrar las extensiones de nombre de archivo para asociar los archivos con la versión correcta de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A menos que use una extensión de nombre de archivo específicos de la versión, el registro permite a los usuarios abrir el proyecto y archivos de proyecto elemento en la versión adecuada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>En esta sección
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md) describe cómo se registran las extensiones de nombre de archivo.

- [Especifique los controladores de archivo de extensiones de nombre de archivo](../extensibility/specifying-file-handlers-for-file-name-extensions.md) proporciona información sobre cómo registrar las aplicaciones que se pueden abrir, edit y así sucesivamente, una extensión de nombre de archivo determinado.

- [Registrar los verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md) explica cómo registrar los verbos.

- [Administrar asociaciones de archivos en paralelo](../extensibility/managing-side-by-side-file-associations.md) se describe cómo controlar las instalaciones en paralelo en el que una versión determinada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe invocarse para abrir un archivo.

## <a name="related-sections"></a>Secciones relacionadas
- [Compatibilidad con varias versiones de Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) se describen los problemas relacionados con varias versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y su VSPackage durante el desarrollo e implementación a los usuarios finales.