---
title: SccCheckout (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5160a2600a8eb3250702dd0836d812b668a3d1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333874"
---
# <a name="scccheckout-function"></a>SccCheckout (función)
Dada una lista de nombres de archivo completo, esta función desprotege ellos en la unidad local. El comentario se aplica a todos los archivos que se va a desproteger. El argumento comentario puede ser un `null` cadena.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[in] La estructura de contexto de complemento de control de origen.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos seleccionados que se desprotegerán.

 lpFileNames

[in] Matriz de nombres de ruta de acceso local completa de archivos que se va a desproteger.

 lpComment

[in] Comentario que se aplicará a cada uno de los archivos seleccionados que se va a desproteger.

 Opciones

[in] Indicadores de comandos (consulte [marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[in] Opciones de específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Desprotección fue correcta.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico. El archivo no se ha desprotegido.|
|SCC_E_ALREADYCHECKEDOUT|El usuario ya tiene el archivo desprotegido.|
|SCC_E_FILEISLOCKED|El archivo está bloqueado, lo que prohíbe la creación de nuevas versiones.|
|SCC_E_FILEOUTEXCLUSIVE|Otro usuario ha hecho una desprotección exclusiva en este archivo.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)