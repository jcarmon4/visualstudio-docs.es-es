---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96b24dac472525a711073eccf41355ddb6f10611
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554240"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Proporciona control sobre cómo el SDK de DIA calcula direcciones virtuales relativas y virtuales para los objetos de depuración.

## <a name="syntax"></a>Sintaxis

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDiaAddressMap`.

|Método|Descripción|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indica si se ha establecido un mapa de direcciones para una sesión determinada.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Especifica si se debe usar la asignación de dirección para traducir las direcciones de símbolos.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indica si está habilitado el cálculo y el uso de direcciones virtuales relativas.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permite al cliente habilitar o deshabilitar el cálculo de direcciones virtuales relativas.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Recupera la alineación de imagen actual.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Establece la alineación de imagen.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Conjuntos de imágenes encabezados para habilitar la traducción de direcciones virtuales relativas.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Proporciona un mapa de direcciones para admitir las traducciones de diseño de imagen.|

## <a name="remarks"></a>Comentarios
 El control proporcionado por esta interfaz se encapsula en dos conjuntos de datos que proporcione: encabezados de la imagen y asignaciones de direcciones. La mayoría de los clientes usa la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método para buscar la información de depuración adecuados para una imagen y el método normalmente pueden detectar todos los datos necesarios encabezados y mapas de sí mismo. Sin embargo, algunos clientes implementan procesamiento especializado y búsqueda de datos. Estos clientes usan los métodos de la `IDiaAddressMap` interfaz para proporcionar el SDK de DIA con los resultados de búsqueda.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz está disponible en el objeto de sesión DIA. El cliente llama a la `QueryInterface` método de DIA sesión objeto interfaz, normalmente [IDiaSession](../../debugger/debug-interface-access/idiasession.md), para recuperar el `IDiaAddressMap` interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2.h

 Biblioteca: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)