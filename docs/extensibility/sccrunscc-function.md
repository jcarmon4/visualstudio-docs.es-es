---
title: SccRunScc (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec6f430b4fee28e0bd1a9d5b1c64f9e8d95b2a97
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338690"
---
# <a name="sccrunscc-function"></a>SccRunScc (Función)
Esta función invoca a la herramienta de administración de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] La estructura de contexto de complemento de control de origen.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos especificados en el `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de archivo seleccionado.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La herramienta de administración de control de código fuente se invocó correctamente.|
|SCC_I_OPERATIONCANCELED|Se canceló la operación.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_CONNECTIONFAILURE|No se pudo conectar con el sistema de control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Esta función permite al llamador tener acceso a toda la gama de características del sistema de control de código fuente a través de una herramienta de administración externo. Si el sistema de control de origen no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar funciones de administración necesarios.

 Esta función se invoca con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, la lista de archivos puede utilizarse para preseleccionar archivos en la interfaz de administración; en caso contrario, se puede omitir la lista.

 Esta función normalmente se invoca cuando el usuario selecciona el **iniciar \<servidor de Control de código fuente >** desde el **archivo** -> **Control de código fuente** menú. Esto **iniciar** opción de menú puede siempre deshabilitada o incluso ocultar estableciendo una entrada del registro. Vea [Cómo: Instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obtener más información. Esta función se invoca sólo si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el `SCC_CAP_RUNSCC` bit de capacidad (vea [marcadores de capacidad](../extensibility/capability-flags.md) para obtener más información sobre este y otros bits capacidad).

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Cómo: Instalar un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Marcadores de capacidad](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)