---
title: SccAddFilesFromSCC (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200909"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función agrega una lista de archivos de control de código fuente al proyecto abierto actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [in, out] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).  
  
 lpAuxProjPath  
 [in, out] Cadena auxiliar que identifica el proyecto (hasta `SCC_PRJPATH_`tamaño, incluido el terminador nulo).  
  
 cFiles  
 [in] Número de archivos proporcionado por `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Matriz de nombres de archivo para agregar al proyecto actual.  
  
 lpDestination  
 [in] La ruta de acceso de destino donde están los archivos que se va a escribir.  
  
 lpComment  
 [in] El comentario que se aplicará a cada uno de los archivos que se va a agregar.  
  
 pbResults  
 [in, out] Matriz de marcas que está establecida para indicar éxito (distinto de cero o TRUE) o error (cero o FALSE) para cada archivo (tamaño de la matriz debe ser al menos `cFiles` largo).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Value|DESCRIPCIÓN|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Proyecto no está abierto.|  
|SCC_E_OPNOTPERFORMED|No es el mismo proyecto según lo especificado por conexión `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Usuario no está autorizado para actualizar la base de datos.|  
|SCC_E_NONSPECIFICERROR|Error desconocido.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
