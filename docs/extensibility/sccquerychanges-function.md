---
title: SccQueryChanges (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353512"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (Función)
Esta función enumera una lista de archivos, que proporciona información sobre los cambios de nombre para cada archivo a través de una función de devolución de llamada especificada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parámetros
 pContext

[in] El puntero de contexto de complemento de control de código fuente.

 nFiles

[in] Número de archivos en `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de archivo para obtener información acerca de.

 pfnCallback

[in] Función de devolución de llamada para llamar para cada nombre de archivo en la lista (consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obtener más información).

 pvCallerData

[in] Valor que se pasa sin cambios a la función de devolución de llamada.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proceso de consulta se completó correctamente.|
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto en control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado o general.|

## <a name="remarks"></a>Comentarios
 Son los cambios que se consulta al espacio de nombres: en concreto, el cambio de nombre, agregar y quitar un archivo.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Códigos de error](../extensibility/error-codes.md)