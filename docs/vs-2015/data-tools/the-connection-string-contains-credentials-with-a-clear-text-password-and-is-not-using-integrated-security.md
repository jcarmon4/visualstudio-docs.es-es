---
title: La cadena de conexión contiene credenciales con una contraseña de texto no cifrado y no usa seguridad integrada | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3b75c4e7cf1b1d0374c9ff648861e049aca988c4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424953"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La cadena de conexión contiene credenciales con una contraseña en texto no cifrado y no usa seguridad integrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

¿Desea guardar la cadena de conexión en el archivo DBML y archivos de configuración de la aplicación actuales con esta información confidencial?  Haga clic en No para guardar la cadena de conexión sin la información confidencial.  
  
 Al trabajar con conexiones de datos que incluyen información confidencial (contraseñas incluidas en la cadena de conexión), se puede optar por guardar la cadena de conexión en el archivo DBML y el archivo de configuración de la aplicación de un proyecto, con o sin la información confidencial.  
  
> [!WARNING]
> Al establecer explícitamente la propiedad **Configuración de la aplicación** de las propiedades de la **Conexión** en **Falso**, se agregará la contraseña al archivo DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Para guardar la cadena de conexión con la información confidencial en la configuración de la aplicación del proyecto  
  
- Haga clic en **Sí**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación. La cadena de conexión incluye la información confidencial en texto sin formato. El archivo DBML no contiene ninguna información confidencial.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Para guardar la cadena de conexión sin la información confidencial en la configuración de la aplicación del proyecto  
  
- Haga clic en **No**.  
  
     La cadena de conexión se almacena como una configuración de la aplicación, pero no se incluye la contraseña.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
