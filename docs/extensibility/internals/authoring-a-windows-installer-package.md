---
title: Creación de un paquete de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da68fa0a6c115a09ba2050f8c84ea6700ee4fc76
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315791"
---
# <a name="author-a-windows-installer-package"></a>Crear un paquete de Windows Installer
El modelo de Windows Installer de las unidades de datos. En lugar de escribir un script de procedimiento para copiar archivos y escribir entradas del registro, por ejemplo, crea filas y columnas en tablas de base de datos que contienen datos de archivos y del registro.

## <a name="database-entries"></a>Entradas de la base de datos
Para instalar un paquete VSPackage, un paquete de Windows Installer debe contener las entradas de la base de datos para llevar a cabo las siguientes tareas:

- Busque en el sistema para encontrar las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el paquete de VS es compatible con (con las tablas de Windows Installer que incluyan AppSearch, CompLocator, RegLocator, DrLocator y firma).

- Cancelar la instalación si ninguna versión compatible de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está instalado o si no se cumple otro requisito de sistema de VSPackage (con la tabla LaunchCondition).

- Instale el paquete VSPackage y los archivos dependientes (con el directorio, componente y tablas de archivos).

- Agregue la información adecuada para el VSPackage en el registro (con la tabla del registro).

- Integrar el VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante una llamada a **devenv.exe /setup** (con la tabla CustomAction).

Para obtener más información, consulte [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Herramientas de instalación
Una variedad de herramientas del programa de instalación de aplicaciones de terceros proporcionan un entorno de desarrollo para paquetes de Windows Installer. Las siguientes herramientas gratuitas están disponibles:

- InstallShield limited edition

   Puede obtener una versión limitada de InstallShield a través de Visual Studio **nuevo proyecto** cuadro de diálogo. Expanda **otros tipos de proyectos** y, a continuación, seleccione **instalación e implementación**. Seleccione la plantilla de InstallShield.

- Windows Installer XML toolset

   El conjunto de herramientas de Windows Installer XML (WiX) compila paquetes de Windows Installer desde archivos de origen XML. El conjunto de herramientas de WiX es un proyecto de código abierto de Microsoft. Puede descargar el código fuente y los archivos ejecutables de [conjunto de herramientas de Wix](http://sourceforge.net/projects/wix).

   Para los productos comerciales que se integran en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizando el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], consulte [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vea también
- [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)