---
title: Procedimiento Configurar el comportamiento mensaje de confianza de ClickOnce | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58e5f0e9154137097a94637799966ee94818fca4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150829"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedimiento Configurar el comportamiento del mensaje relativo a la confianza de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede configurar el aviso de confianza de ClickOnce para controlar si los usuarios finales tienen la opción de instalar las aplicaciones ClickOnce, por ejemplo, las aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, las aplicaciones de consola, WPF en explorador las aplicaciones y soluciones de Office. Configure el aviso de confianza mediante el establecimiento de las claves del registro en cada equipo de usuario final.  
  
 La siguiente tabla muestra las opciones de configuración que se pueden aplicar a cada una de las cinco zonas (Internet, UntrustedSites, MyComputer, LocalIntranet y TrustedSites).  
  
|Opción|Valor de configuración del registro|DESCRIPCIÓN|  
|------------|----------------------------|-----------------|  
|Habilitar el aviso de confianza.|`Enabled`|El aviso de confianza de ClickOnce es la pantalla para que los usuarios finales pueden conceder confianza a las aplicaciones ClickOnce.|  
|Restringir el aviso de confianza.|`AuthenticodeRequired`|El aviso de confianza de ClickOnce solo se muestra si las aplicaciones ClickOnce están firmadas con un certificado que identifica al publicador.|  
|Deshabilitar el aviso de confianza.|`Disabled`|No se muestra el aviso de confianza de ClickOnce para aplicaciones ClickOnce que no estén firmadas con un certificado de confianza explícita.|  
  
 En la tabla siguiente se muestra el comportamiento predeterminado para cada zona. La columna aplicaciones hace referencia a las aplicaciones de Windows Forms, aplicaciones de Windows Presentation Foundation, aplicaciones de explorador WPF y aplicaciones de consola.  
  
|Zona|APLICACIONES|soluciones de Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Puede invalidar esta configuración habilitando, restringir o deshabilitar el aviso de confianza de ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Habilitar el aviso de confianza de ClickOnce  
 Habilitar el aviso de confianza para una zona cuando desee que los usuarios finales se le ofrecerá la opción de instalar y ejecutar las aplicaciones ClickOnce que proceden de esa zona.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para habilitar el aviso de confianza de ClickOnce mediante el editor del registro  
  
1. Abra el Editor del Registro:  
  
    1. Haga clic en **Inicio** y después en **Ejecutar**.  
  
    2. En el **abierto** , escriba `regedit` (o `regedit32` en Windows de 32 bits) y, a continuación, haga clic en **Aceptar**.  
  
2. Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créelo.  
  
3. Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave de valor de cadena|Value|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Para las soluciones de Office, `Internet` tiene el valor predeterminado `AuthenticodeRequired` y `UntrustedSites` tiene el valor `Disabled`. Para todos los demás, `Internet` tiene el valor predeterminado `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para habilitar el aviso de confianza de ClickOnce mediante programación  
  
1. Crear una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2. Abra el archivo Program.cs o de Program.vb para su edición y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3. Compile y ejecute la aplicación.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Restringir el aviso de confianza de ClickOnce  
 Restringir el aviso de confianza para que las soluciones deben estar firmadas con certificados de Authenticode que dispongan de una identidad conocida antes de que los usuarios se le solicitará una decisión de confianza.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir el aviso de confianza de ClickOnce mediante el editor del registro  
  
1. Abra el Editor del Registro:  
  
    1. Haga clic en **Inicio** y después en **Ejecutar**.  
  
    2. En el **abierto** , escriba `regedit` (o `regedit32` en Windows de 32 bits) y, a continuación, haga clic en **Aceptar**.  
  
2. Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créelo.  
  
3. Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave de valor de cadena|Value|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir el aviso de confianza de ClickOnce mediante programación  
  
1. Crear una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2. Abra el archivo Program.cs o de Program.vb para su edición y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3. Compile y ejecute la aplicación.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Deshabilitar el aviso de confianza de ClickOnce  
 Puede deshabilitar el aviso de confianza para que los usuarios finales no tienen la opción para instalar las soluciones que no son de confianza ya en su directiva de seguridad.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para deshabilitar el aviso de confianza de ClickOnce mediante el editor del registro  
  
1. Abra el Editor del Registro:  
  
    1. Haga clic en **Inicio** y después en **Ejecutar**.  
  
    2. En el **abierto** , escriba `regedit` (o `regedit32` en Windows de 32 bits) y, a continuación, haga clic en **Aceptar**.  
  
2. Busque la siguiente clave del registro:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Si la clave no existe, créelo.  
  
3. Agregue las siguientes subclaves como **valor de cadena**, si no existe ya, con los valores asociados que se muestra en la tabla siguiente.  
  
    |Subclave de valor de cadena|Valor|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para deshabilitar el aviso de confianza de ClickOnce mediante programación  
  
1. Crear una aplicación de consola de Visual Basic o Visual C# en Visual Studio.  
  
2. Abra el archivo Program.cs o de Program.vb para su edición y agregue el código siguiente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3. Compile y ejecute la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Cómo: Habilitar a la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedimientos: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedimientos: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cómo: Agregar un publicador de confianza en un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Cómo: Repetición de la firma de manifiestos de implementación y aplicación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
