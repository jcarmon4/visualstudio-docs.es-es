---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed287f2d90e1ee92c7e0fd4ae685fbb9f38854f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350586"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Especifica la estructura de la ubicación de la resolución de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Miembros
`bpType`\
Un valor de la [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumeración que especifica cómo interpretar la `bpResLocation` union o `unionmemberX` miembros.

`bpResLocation.bpresCode`\
[C++ sólo] Contiene el [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) estructura si `bpType`  =  `BPT_CODE`.

`bpResLocation.bpresData`\
[C++ sólo] Contiene el [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) estructura si `bpType`  =  `BPT_DATA`.

`bpResLocation.unused`\
[C++ sólo] Un marcador de posición.

`unionmember1`\
[C# sólo] Vea la sección Comentarios para interpretar.

`unionmember2`\
[C# sólo] Vea la sección Comentarios para interpretar.

`unionmember3`\
[C# sólo] Vea la sección Comentarios para interpretar.

`unionmember4`\
[C# sólo] Vea la sección Comentarios para interpretar.

## <a name="remarks"></a>Comentarios
Esta estructura es un miembro de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) y [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructuras.

 [C# sólo] El `unionmemberX` miembros se interpretan según la tabla siguiente. Mirando la columna izquierda de la `bpType` en valor, a continuación, para determinar qué cada `unionmemberX` miembro representa y serializar el `unionmemberX` en consecuencia. Vea el ejemplo de una forma para interpretar esta estructura en C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (expresión de datos)|`string` (nombre de función)|`string` (nombre de la imagen)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo interpretar la `BP_RESOLUTION_LOCATION` estructura en C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
