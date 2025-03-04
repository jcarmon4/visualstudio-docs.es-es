---
title: Constantes (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed505499efcabd7173fea9d668cd9afa5ed6d925
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555083"
---
# <a name="constants-debug-interface-access-sdk"></a>Constantes (Debug Interface Access SDK)
Estas constantes de cadena pueden utilizarse para identificar las distintas secciones de un archivo de base de datos (PDB) de depuración de programa a través del SDK de DIA.

## <a name="constants"></a>Constantes
El siguiente se declara como macros de C o C++.

|Macro|Valor|
|-----------|-----------|
|`DiaTable_Symbols`|L "Símbolos"|
|`DiaTable_Sections`|L "Secciones"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L "SegmentMap"|
|`DiaTable_Dbg`|L "Dbg"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L "FrameData"|

## <a name="example"></a>Ejemplo
Este es un ejemplo utilizando uno de estos símbolos:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Requisitos
Encabezado: dia2.h

## <a name="see-also"></a>Vea también
- [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
