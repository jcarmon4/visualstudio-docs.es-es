---
title: Agregar publicador de confianza para el equipo cliente para las aplicaciones ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 426096670df1099568cadc2af68ae0ff50ca71e5
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263158"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Procedimiento Adición de un publicador de confianza a un equipo cliente para aplicaciones ClickOnce
Con la implementación de aplicaciones de confianza, puede configurar equipos cliente para que las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se ejecuten con un nivel superior de confianza sin preguntar al usuario. En los procedimientos siguientes se muestra cómo usar la herramienta de línea de comandos CertMgr.exe para agregar el certificado de un publicador al almacén de publicadores de confianza de un equipo cliente.

 Los comandos que se usan varían ligeramente si la entidad de certificación (CA) que emitió el certificado forma parte de la raíz de confianza del cliente. Si un equipo cliente de Windows forma parte de un dominio, contendrá en una lista las CA que se consideren raíces de confianza. Suele ser el administrador del sistema quien configura esta lista. Si el certificado fue emitido por una de estas raíces de confianza o por una CA vinculada a una raíz de confianza, puede agregar el certificado al almacén raíz de confianza del cliente. En cambio, si el certificado no fue emitido por una de estas raíces de confianza, debe agregarlo al almacén raíz de confianza y al almacén de publicadores de confianza del cliente.

> [!NOTE]
> Debe agregar los certificados de esta manera en todos los equipos cliente en los que quiera implementar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que requiere permisos elevados. Puede agregar los certificados manualmente o mediante una aplicación implementada en los clientes. Solo tiene que configurar estos equipos una vez, tras lo cual puede implementar cualquier número de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmadas con el mismo certificado.

 También puede agregar un certificado a un almacén mediante programación a través de la clase <xref:System.Security.Cryptography.X509Certificates.X509Store> .

 Para obtener información general sobre la implementación de aplicaciones de confianza, vea [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Para agregar un certificado al almacén de publicadores de confianza en la raíz de confianza

1. Obtenga un certificado digital de una CA.

2. Exporte el certificado en el formato Base64 X.509 ( *.cer*). Para obtener más información sobre los formatos de certificado, vea [Exportar un certificado](http://go.microsoft.com/fwlink/?LinkId=164793).

3. Desde el símbolo del sistema en los equipos cliente, ejecute el comando siguiente:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Para agregar un certificado al almacén de publicadores de confianza en una raíz diferente

1. Obtenga un certificado digital de una CA.

2. Exporte el certificado en el formato Base64 X.509 ( *.cer*). Para obtener más información sobre los formatos de certificado, consulte [Exportar un certificado](http://go.microsoft.com/fwlink/?LinkId=164793).

3. Desde el símbolo del sistema en los equipos cliente, ejecute el comando siguiente:

     **certmgr.exe -add good.cer -c -s -r localMachine Root**

     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Vea también
- [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Proteger aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)
- [Cómo: Habilitar a la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Cómo: Agregar un publicador de confianza en un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Cómo: Repetición de la firma de manifiestos de implementación y aplicación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Cómo: Configuración del comportamiento del mensaje sobre la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)