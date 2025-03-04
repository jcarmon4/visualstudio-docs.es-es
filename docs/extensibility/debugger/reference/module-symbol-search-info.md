---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c521ebe321813013b83a951d4d2aa5f60fd1646d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346614"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene información de estado sobre las rutas de acceso de búsqueda de símbolos que se ha buscado.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Miembros

`dwValidFields`\
Una combinación de marcas de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica el tipo de información de búsqueda descrito en esta estructura.

`bstrVerboseSearchInfo`\
Ruta de acceso de búsqueda y resultados concatenados en una sola cadena.

## <a name="remarks"></a>Comentarios

Esta estructura se devuelve desde una llamada a la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método.

Si el `bstrVerboseSearchInfo` campo no está vacío, a continuación, contiene una lista de rutas de acceso que buscará y los resultados de la búsqueda. La lista está formateada con una ruta de acceso, seguido de puntos suspensivos ("..."), seguido por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa mediante un par de "\r\n" (carro retorno/avance de línea). El patrón tiene este aspecto:

\<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado >

Tenga en cuenta que la última entrada no tiene una secuencia \r\n.

Este es un posible `bstrVerboseSearchInfo` cadena que se ha enviado a la salida estándar.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)