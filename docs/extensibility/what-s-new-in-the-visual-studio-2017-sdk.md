---
title: ¿Qué&#39;s en el SDK de Visual Studio 2017 | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 434a04aaa8389b4b09f32778d5de63bd2a7d687f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350794"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>¿Qué&#39;s nuevo en Visual Studio 2017 SDK

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Para admitir la nueva instalación ligera de Visual Studio 2017, el formato de manifiesto de extensión VSIX se actualizó a la versión 3 (v3 VSIX).

El nuevo formato es compatible con:

* Requisitos previos detecta e instalarse mediante el VSIXInstaller se declaran explícitamente.
* Ensamblados Ngen de instalación de la extensión.
* Instalación de los recursos fuera de la raíz de extensión habitual.

Para obtener información acerca de estos cambios, vea los temas siguientes:

* [Cambios a la extensibilidad de Visual Studio 2017](breaking-changes-2017.md)
* [Compatibilidad con Ngen en VSIX v3](ngen-support.md)
* [Instale fuera de la carpeta de extensiones](set-install-root.md)
* [Extensibilidad de Visual Studio 2017 preguntas más frecuentes](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrar el proyecto de extensibilidad a Visual Studio 2017

Para obtener información sobre cómo actualizar los proyectos de extensibilidad y sus manifiestos VSIX a Visual Studio 2017, vea [Cómo: Migrar proyectos de extensibilidad de Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Plantillas de proyecto y elemento personalizadas

A partir de Visual Studio 2017, análisis de proyecto personalizado y las plantillas de elemento ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión con un archivo MSI, debe generar manualmente los archivos de manifiesto de plantilla. Para obtener más información, consulte [actualizar plantillas de proyecto y elemento personalizadas para Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). El esquema del manifiesto de plantilla está documentado en [referencia de esquema del manifiesto de plantilla de Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Directrices de rendimiento de la extensión actualizada

Hay un nuevo [Cómo: Diagnóstico de rendimiento de la extensión](how-to-diagnose-extension-performance.md) en el artículo [administrar VSPackages](managing-vspackages.md) para mostrar cómo detectar y analizar el impacto de la extensión en Visual Studio inicio y solución de los tiempos de carga.
