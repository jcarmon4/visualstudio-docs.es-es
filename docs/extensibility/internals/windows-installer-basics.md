---
title: Conceptos básicos de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc52f846d7883d32f567df449a93c2626a710f81
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323046"
---
# <a name="windows-installer-basics"></a>Datos básicos de Windows Installer
El instalador de Windows se instala y desinstala las aplicaciones o productos de software en el equipo del usuario, realizar estas tareas en unidades denominadas componentes del instalador de Windows (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para configuraciones mediante Windows Installer.

 Para obtener documentación completa de Windows Installer, vea el tema de Platform SDK, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Creación de un VSPackage
 Windows Installer utiliza paquetes de instalación, que contienen información que Windows Installer necesita para instalar, desinstalar o reparar un producto y para ejecutar la interfaz de usuario (UI) de programa de instalación. Cada paquete de instalación incluye un archivo .msi, que contiene una base de datos de la instalación, un flujo de información de resumen y los flujos de datos para las distintas partes de la instalación. Para usar el programa de instalación, debe crear una instalación. Dado que el instalador organiza las instalaciones en torno al concepto de componentes y almacena información sobre la instalación en una base de datos relacional, el proceso de creación de un paquete de instalación ampliamente implica los pasos siguientes:

1. Planear la configuración de creación para admitir el control de versiones y estrategias en paralelo.

2. Identificar las características que se presentará a los usuarios.

3. Organice el VSPackage y las dependencias en componentes.

4. Rellenar la base de datos con la información de instalación.

5. Validar el paquete de instalación.

   Esta documentación se ocupa principalmente de los pasos primeros y terceros del proceso. Durante estos pasos organizar sus características de VSPackage en WICs por lo que puede enmarcar el control de versiones y la estrategia para las versiones posteriores de la cuenta de servicio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Los tres pasos restantes se tratan detalladamente en la documentación de Windows Installer en Platform SDK.

## <a name="key-terms"></a>Términos clave
 Estos son definiciones de términos clave relacionados con la tecnología de Windows Installer.

 Archivos de recursos, las claves del registro, los accesos directos, o y así sucesivamente que puede instalarse en un equipo. Estos recursos se agrupan lógicamente en componentes de Windows Installer.

 Componente de instalador de Windows (WIC) en la unidad básica de instalación que representa una agrupación lógica de los recursos relacionados que se instalan y desinstalan como una unidad. Componentes de Windows Installer se identifican mediante un identificador único de componentes o GUID. Además, Windows Installer mantiene su referencia de recuento en el nivel de WIC. Para obtener la flexibilidad de control de versiones máxima, incluyen no más de un recurso principal, como un archivo DLL, en un determinado WIC. Tenga en cuenta que después de identificar y rellenar un WIC, asígnele un GUID e implementarlo, no se puede cambiar su composición. Para obtener más información, consulte [organizar las aplicaciones en componentes](/windows/desktop/Msi/organizing-applications-into-components).

 Unidad de un paquete (paquete Redist) de implementación que consta de un archivo .msi y archivos de origen externo a la que puede indicar este archivo. Un paquete contiene toda la información que necesita Windows Installer para ejecutar la interfaz de usuario y para instalar o desinstalar la aplicación.

 archivo de almacenamiento estructurado COM de un archivo .msi que contiene las instrucciones y los datos necesarios para instalar una aplicación. Cada paquete contiene al menos un archivo MSI. El archivo .msi contiene la base de datos de instalador, una secuencia de información de resumen y posiblemente una o varias transformaciones y los archivos de origen interno. Que se instalen archivos pueden se comprimen en un archivador y almacenarse en una secuencia en el archivo .msi o almacenados, comprimidos o sin comprimir, fuera del archivo .msi en el medio de origen. Para obtener más información, consulte [extensiones de archivo de Windows Installer](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Cumplimiento de las reglas de Windows Installer
 Dos conjuntos de reglas determinan la implementación de recursos a través de los componentes de la instalación. Un conjunto de reglas se mantiene mediante el instalador de Windows, mientras se debe aplicar el segundo conjunto como autor de la instalación.

> [!NOTE]
> Sólo si se ejecuta una validación del archivo .msi, se produce el cumplimiento de reglas de Windows Installer. No obstante, se les advierte para tratar estas reglas como los procedimientos recomendados. Para obtener más información, consulte [validar una base de datos de instalación](/windows/desktop/Msi/validating-an-installation-database) y [validación del paquete](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Reglas exigidas por el instalador

- Todos los archivos de un determinado componente deben instalarse en el mismo directorio. Por el contrario, deben pertenecer archivos instalados para separar las carpetas para separar los componentes.

- Puede haber solo una ruta de acceso de clave por componente. La ruta de acceso de clave es simplemente una archivo o clave del registro que representa el componente completo.

#### <a name="component-provider-responsibilities"></a>Responsabilidades del proveedor de componentes

- Los dos recursos que es posible que se envían por separado en las versiones posteriores deben existir en componentes independientes. Los recursos deben estar agrupados en el mismo componente sólo cuando esté seguro de que estos recursos nunca se enviarán por separado. De hecho, se recomienda que todos los recursos principales (por ejemplo, archivos DLL) siempre se encuentran en WICs independientes. Para obtener más información, consulte [definir componentes del instalador](/windows/desktop/Msi/defining-installer-components).

- Nunca debe enviar ningún recurso con control de versiones en más de un WIC.

## <a name="see-also"></a>Vea también
- [¿Qué ocurre si se interrumpen las reglas de componente?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)