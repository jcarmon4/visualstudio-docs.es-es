---
title: Procedimientos recomendados para la seguridad en VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697268"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedimientos recomendados para seguridad en VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para instalar el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] en el equipo, debe ejecutar en un contexto con credenciales administrativas. La unidad básica de seguridad e implementación de un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aplicación es el [VSPackages](../../extensibility/internals/vspackages.md). Se debe registrar un VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], que también requiere credenciales administrativas.  
  
 Los administradores tienen permisos completos para escribir en el registro y sistema de archivos y para ejecutar cualquier código. Debe tener estos permisos para desarrollar, implementar o instalar un paquete VSPackage.  
  
 Tan pronto como se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar inadvertidamente un VSPackage que tenga propósitos maliciosos.  
  
 Los usuarios deben garantizar que se instalen los VSPackages únicamente desde orígenes de confianza. Las empresas de desarrollo de VSPackages fuertemente deben el nombre y firmarlos garantizar que el usuario que la manipulación se evita. Las empresas que desarrollan los paquetes VSPackage deben examinar sus dependencias externas, como servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.  
  
 Para obtener más información, vea instrucciones de codificación segura para .NET Framework ([https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad de complementos](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Seguridad DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
