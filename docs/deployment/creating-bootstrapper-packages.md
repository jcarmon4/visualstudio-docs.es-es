---
title: Crear paquetes de programa previo
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dc22b775af048cc3138d6930a835a00c9d97b2a
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533337"
---
# <a name="create-bootstrapper-packages"></a>Crear paquetes de programa previo
El programa de instalación es un instalador genérico que se puede configurar para detectar e instalar componentes redistribuibles, como archivos de Windows Installer ( *.msi*) y programas ejecutables. El instalador también se conoce como programa previo. Se programa mediante un conjunto de manifiestos XML que especifican los metadatos que administrarán la instalación del componente.  Cada componente redistribuible, o requisito previo, que aparece en el cuadro de diálogo **requisitos previos** para ClickOnce es un paquete de programa previo. Un paquete de programa previo es un grupo de directorios y archivos que contienen archivos de manifiesto que describen cómo se debe instalar el requisito previo.

El programa previo detecta primero si los requisitos previos están ya instalados. Si no lo están, el programa previo muestra el contrato de licencia. Después de que el usuario acepta los contratos de licencia, comienza la instalación de los requisitos previos. Si se detectan todos los requisitos previos, el programa previo inicia el instalador de la aplicación.

## <a name="create-custom-bootstrapper-packages"></a>Crear paquetes de arranque personalizados
Puede generar los manifiestos de arranque mediante el editor XML de Visual Studio. Para ver un ejemplo de cómo crear un paquete de programa [previo, vea Tutorial: Cree un programa previo personalizado con un aviso](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)de privacidad.

Para crear un paquete de programa previo, debe crear un manifiesto del producto y, para cada versión localizada de un componente, también un manifiesto del paquete.

* El manifiesto del producto, *product. XML*, contiene metadatos independientes del lenguaje para el paquete. Contiene los metadatos comunes a todas las versiones localizadas del componente redistribuible.  Para crear este archivo, consulte [cómo: Cree un manifiesto](../deployment/how-to-create-a-product-manifest.md)del producto.

* El manifiesto del paquete, *Package. XML*, contiene metadatos específicos del lenguaje; Normalmente, contiene mensajes de error localizados. Un componente debe tener al menos un manifiesto del paquete por cada versión localizada de ese componente. Para crear este archivo, consulte [cómo: Cree un manifiesto](../deployment/how-to-create-a-package-manifest.md)del paquete.

Una vez creados estos archivos, coloque el archivo del manifiesto del producto en una carpeta con el nombre del programa previo personalizado. El archivo del manifiesto del paquete va en una carpeta con el nombre de la configuración regional. Por ejemplo, si el archivo del manifiesto del paquete es para la redistribución en inglés, coloque el archivo en una carpeta llamada en. Repita este proceso para cada configuración regional, como ja para japonés y de para alemán. El paquete del programa previo personalizado final podría tener la siguiente estructura de carpetas.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

A continuación, copie los archivos redistribuibles en la ubicación de la carpeta de arranque. Para obtener más información, vea [Cómo: Crear un paquete de programa previo localizado](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper*
```

o, para versiones anteriores de Visual Studio

```
*\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

o

```
*\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
```

También puede buscar la ubicación de la carpeta de arranque desde el valor de la **ruta de acceso** en la siguiente clave del registro:

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

En los sistemas de 64 bits, use la siguiente clave del Registro:

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Cada componente redistribuible aparece en su propia subcarpeta, en el directorio de los paquetes. El manifiesto del producto y los archivos redistribuibles deben colocarse en esta subcarpeta. Las versiones localizadas de los manifiestos de componentes y paquetes deben colocarse en subcarpetas denominadas según el nombre de la referencia cultural.

Una vez copiados estos archivos en la carpeta del programa previo, el paquete del programa previo aparece automáticamente en el cuadro de diálogo **Requisitos previos** de Visual Studio. Si el paquete del programa previo personalizado no aparece, cierre y vuelva a abrir el cuadro de diálogo **Requisitos previos**. Para obtener más información, consulta [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md).

La tabla siguiente muestra las propiedades que el programa previo rellena automáticamente.

|Propiedad|DESCRIPCIÓN|
|--------------|-----------------|
|ApplicationName|El nombre de la aplicación.|
|ProcessorArchitecture|El procesador y los bits por palabra de la plataforma de destino de un ejecutable. Los valores son los siguientes:<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Número de versión de los sistemas operativos Microsoft Windows 95, Windows 98 o Windows ME. La sintaxis de la versión es Principal.Secundaria.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Número de versión de los sistemas operativos Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 o Windows 7. La sintaxis de la versión es Principal.Secundaria.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Versión del ensamblado de Windows Installer (MSI. dll) que se va a ejecutar durante la instalación.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Esta propiedad se establece si el usuario tiene privilegios administrativos. Los valores son true o false.|
|InstallMode|El modo de instalación indica desde dónde debe instalarse el componente. Los valores son los siguientes:<br /><br /> -   HomeSite: los requisitos previos se instalan desde el sitio web del proveedor.<br />-   SpecificSite: los requisitos previos se instalan desde la ubicación que seleccione.<br />-   SameSite: los requisitos previos se instalan desde la misma ubicación que la aplicación.|

## <a name="separate-redistributables-from-application-installations"></a>Separar redistribuibles de las instalaciones de aplicaciones
Puede evitar que los archivos redistribuibles se implementen en proyectos de instalación. Para ello, cree una lista de redistribuibles en la carpeta RedistList de su directorio de .NET Framework:

`%ProgramFiles%\Microsoft.NET\RedistList`

La lista de redistribuibles es un archivo XML cuyo nombre debe seguir el formato siguiente: *Nombre de la compañía >.\< \< Nombre del componente >. RedistList. XML*. Por ejemplo, si el componente se llama Datawidgets y ha sido creado por Acme, use *Acme.DataWidgets.RedistList.xml*. El siguiente podría ser un ejemplo del contenido de la lista de redistribuibles:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Vea también
- [Cómo: Instalar los requisitos previos con una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Cuadro de diálogo Requisitos previos](../ide/reference/prerequisites-dialog-box.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)
- [Usar el programa previo de Visual Studio 2005 para poner en marcha su instalación](http://go.microsoft.com/fwlink/?LinkId=107537)
