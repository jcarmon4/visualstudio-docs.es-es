---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 393abb3b1e1872a416865cbfee5c142bef98ce78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838459"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Se abre una sesión para consultar los símbolos.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parámetros
ppSession

[out] Devuelve un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto que representa la sesión abierta.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_UNEXPECTED|El [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objeto previamente no se ha inicializado con un origen de símbolos.|
|E_INVALIDARG|El parámetro `ppSession` no es válido.|
|E_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|

## <a name="remarks"></a>Comentarios
Este método abre un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto para un origen de datos.

`IDiaSession` los objetos implementan las consultas en el origen de datos. Una sesión administra un espacio de direcciones para cada conjunto de símbolos de depuración. Si el archivo .exe o .dll descrito por los símbolos del origen de datos está activo en la dirección de varios intervalos de direcciones (por ejemplo, porque tienen varios procesos de carga), a continuación, se debe usar una sesión para cada intervalo de direcciones.

## <a name="example"></a>Ejemplo

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Vea también
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
