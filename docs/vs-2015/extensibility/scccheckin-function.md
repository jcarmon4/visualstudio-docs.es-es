---
title: SccCheckin (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189532"
---
# <a name="scccheckin-function"></a>SccCheckin (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función comprueba en los archivos anteriormente desprotegidos para el sistema de control de código fuente, almacenar los cambios y crear una nueva versión. Esta función se invoca con un recuento y una matriz de nombres de los archivos que se comprobará.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 nFiles  
 [in] Número de archivos seleccionados deben registrarse.  
  
 lpFileNames  
 [in] Matriz de nombres de ruta de acceso local completa de los archivos se protejan.  
  
 lpComment  
 [in] Comentario que se aplicará a cada uno de los archivos seleccionados que se va a proteger. Se trata de `NULL` si el complemento de control de código fuente puede solicitarle un comentario.  
  
 Opciones  
 [in] Marcas de comando, ya sea 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opciones específicas del complemento de control de código fuente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|DESCRIPCIÓN|  
|-----------|-----------------|  
|SCC_OK|Los archivos se ha protegido correctamente.|  
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECIFICERROR|Error no específico. Archivo no se protegió.|  
|SCC_E_NOTCHECKEDOUT|El usuario no ha desprotegido el archivo, por lo que no puede protegerlo.|  
|SCC_E_CHECKINCONFLICT|No se pudo realizar la inserción en el repositorio porque:<br /><br /> -Otro usuario ha registrado con antelación y `bAutoReconcile` era false.<br /><br /> -o bien-<br /><br /> -La combinación automática no es posible (por ejemplo, cuando los archivos son binarios).|  
|SCC_E_VERIFYMERGE|Archivo ha sido combinada automáticamente, pero no se ha comprobado espera de comprobación de usuario.|  
|SCC_E_FIXMERGE|Archivo ha sido combinada automática, pero no se ha comprobado debido a un conflicto de combinación que debe resolverse manualmente.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación antes de completarse.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|  
  
## <a name="remarks"></a>Comentarios  
 El comentario se aplica a todos los archivos que se va a proteger. El argumento comentario puede ser un `null` de cadena, en cuyo caso el complemento de control de código fuente puede pedir al usuario una cadena de comentario para cada archivo.  
  
 El `fOptions` argumento se puede proporcionar un valor de la `SCC_KEEP_CHECKEDOUT` marca para indicar que la intención del usuario para proteger el archivo y compruébelo de nuevo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
