---
title: '&lt;dependencia&gt; elemento (aplicación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41e6e5bf2152fffb06acfb8b5e1f3283da75a19a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745952"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dependencia&gt; elemento (aplicación ClickOnce)
Identifica una dependencia de plataforma o ensamblado que se requiere para la aplicación.

## <a name="syntax"></a>Sintaxis

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `dependency` elemento es necesario. Puede haber varias instancias de `dependency` en el manifiesto de aplicación mismo.

 El `dependency` elemento no tiene atributos y contiene los siguientes elementos secundarios.

### <a name="dependentos"></a>dependentOS
 Opcional. Contiene el `osVersionInfo` elemento. El `dependentOS` y `dependentAssembly` elementos se excluyen mutuamente: uno de ellos debe existir para un `dependency` elemento, pero no ambos.

 `dependentOS` admite los siguientes atributos.

|Atributo|Descripción|
|---------------|-----------------|
|`supportUrl`|Opcional. Especifica una dirección URL de soporte técnico para la plataforma dependiente. Esta dirección URL se muestra al usuario si se encuentra la plataforma requerida.|
|`description`|Opcional. Se describe en forma legible, el sistema operativo descrito por el `dependentOS` elemento.|

### <a name="osversioninfo"></a>osVersionInfo
 Obligatorio. Este elemento es un elemento secundario del elemento `dependentOS` y contiene el elemento `os` . Este elemento no tiene atributos.

### <a name="os"></a>Elementos y atributos
 Obligatorio. Este elemento es un elemento secundario del elemento `osVersionInfo` . Este elemento tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`majorVersion`|Obligatorio. Especifica el número de versión principal del sistema operativo.|
|`minorVersion`|Obligatorio. Especifica el número de versión secundaria del sistema operativo.|
|`buildNumber`|Obligatorio. Especifica el número de compilación del sistema operativo.|
|`servicePackMajor`|Obligatorio. Especifica el número principal de service pack del sistema operativo.|
|`servicePackMinor`|Opcional. Especifica el número secundario de service pack del sistema operativo.|
|`productType`|Opcional. Identifica el valor de tipo de producto. Valores válidos son `server`, `workstation` y `domainController`. Por ejemplo, para Windows 2000 Professional, este valor de atributo es `workstation`.|
|`suiteType`|Opcional. Identifica un conjunto de productos disponible en el sistema o el tipo de configuración del sistema. Los valores válidos son `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` y `terminal`. Por ejemplo, para Windows 2000 Professional, este valor de atributo es `professional`.|

### <a name="dependentassembly"></a>dependentAssembly
 Opcional. Contiene el `assemblyIdentity` elemento. El `dependentOS` y `dependentAssembly` elementos se excluyen mutuamente: uno de ellos debe existir para un `dependency` elemento, pero no ambos.

 `dependentAssembly` tiene los siguientes atributos.

| Atributo | Descripción |
|-----------------------| - |
| `dependencyType` | Obligatorio. Especifica el tipo de dependencia. Los valores válidos son `preprequisite` y `install`. Un `install` ensamblado se instala como parte de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación. Un `prerequisite` ensamblado debe estar presente en la caché de ensamblados global (GAC) antes de la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede instalar la aplicación. |
| `allowDelayedBinding` | Obligatorio. Especifica si el ensamblado se puede cargar mediante programación en tiempo de ejecución. |
| `group` | Opcional. Si el `dependencyType` atributo está establecido en `install`, designa un grupo de ensamblados con nombre que solo se instalan a petición. Para obtener más información, vea [Tutorial: Descarga de ensamblados a petición con la API de implementación ClickOnce mediante el diseñador](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Si establece en `framework` y `dependencyType` atributo está establecido en `prerequisite`, designa el ensamblado como parte de .NET Framework. No se comprueba la caché de ensamblado global (GAC) para este ensamblado cuando se instala en .NET Framework 4 y versiones posteriores. |
| `codeBase` | Obligatorio cuando el `dependencyType` atributo está establecido en `install`. La ruta de acceso al ensamblado dependiente. Puede ser una ruta de acceso absoluta o una ruta de acceso en relación con el código del manifiesto a la base. Esta ruta de acceso debe ser un URI válido en orden para el manifiesto del ensamblado sea válido. |
| `size` | Obligatorio cuando el `dependencyType` atributo está establecido en `install`. El tamaño del ensamblado dependiente, en bytes. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Obligatorio. Este elemento es un elemento secundario del elemento `dependentAssembly` y tiene los atributos siguientes.

|Atributo|Descripción|
|---------------|-----------------|
|`name`|Obligatorio. Identifica el nombre de la aplicación.|
|`version`|Obligatorio. Especifica el número de versión de la aplicación en el formato siguiente: `major.minor.build.revision`|
|`publicKeyToken`|Opcional. Especifica una cadena hexadecimal de 16 caracteres que representa los últimos 8 bytes de la `SHA-1` valor hash de la clave pública con la que se firma la aplicación o el ensamblado. La clave pública utilizada para firmar el catálogo debe ser 2048 bits o más.|
|`processorArchitecture`|Opcional. Especifica el procesador. Los valores válidos son `x86` para Windows de 32 bits y `I64` para Windows de 64 bits.|
|`language`|Opcional. Identifica los códigos de idioma de dos partes, como EN-US, del ensamblado.|

### <a name="hash"></a>hash
 El `hash` elemento es un elemento secundario opcional de la `assemblyIdentity` elemento. El elemento `hash` no tiene atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utiliza un valor hash algorítmico de todos los archivos en una aplicación como una comprobación de seguridad para asegurarse de que ninguno de los archivos se han modificado después de la implementación. Si el `hash` elemento no se incluye, no se realizará esta comprobación. Por lo tanto, si se omite el `hash` elemento no se recomienda.

### <a name="dsigtransforms"></a>dsig:Transforms
 El `dsig:Transforms` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:Transforms` no tiene atributos.

### <a name="dsigtransform"></a>dsig: Transform
 El `dsig:Transform` elemento es un elemento secundario necesario de la `dsig:Transforms` elemento. El elemento `dsig:Transform` tiene los atributos siguientes:

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `urn:schemas-microsoft-com:HashTransforms.Identity`. |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 El `dsig:DigestMethod` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:DigestMethod` tiene los atributos siguientes:

| Atributo | Descripción |
|-------------| - |
| `Algorithm` | El algoritmo utilizado para calcular la síntesis de este archivo. Actualmente el único valor utilizado por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] es `http://www.w3.org/2000/09/xmldsig#sha1`. |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 El `dsig:DigestValue` elemento es un elemento secundario necesario de la `hash` elemento. El elemento `dsig:DigestValue` no tiene atributos. Su valor de texto es el hash calculado para el archivo especificado.

## <a name="remarks"></a>Comentarios
 Todos los ensamblados usados por la aplicación deben tener su correspondiente `dependency` elemento. Los ensamblados dependientes no incluyen ensamblados que deben estar preinstalados en la caché global de ensamblados como ensamblados de plataforma.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo de código ilustra `dependency` elementos en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de aplicación. Este ejemplo de código forma parte de un ejemplo más extenso proporcionado para el [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md) tema.

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Vea también
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<dependencia > elemento](../deployment/dependency-element-clickonce-deployment.md)