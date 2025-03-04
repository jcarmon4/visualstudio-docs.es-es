---
title: CV_CPU_TYPE_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CPU_TYPE_e enumeration
ms.assetid: df470a7e-1d04-448e-b920-c731189514fa
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6821b6a6504fd82e0e6180149120b71bc2daf47c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444478"
---
# <a name="cvcputypee"></a>CV_CPU_TYPE_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el procesador de destino.  
  
> [!NOTE]
> El procesador se identifica en el elemento de enumeración tras el `CV_CFL_*` prefijo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef enum CV_CPU_TYPE_e {   
   CV_CFL_8080         = 0x00,  
   CV_CFL_8086         = 0x01,  
   CV_CFL_80286        = 0x02,  
   CV_CFL_80386        = 0x03,  
   CV_CFL_80486        = 0x04,  
   CV_CFL_PENTIUM      = 0x05,  
   CV_CFL_PENTIUMII    = 0x06,  
   CV_CFL_PENTIUMPRO   = CV_CFL_PENTIUMII,  
   CV_CFL_PENTIUMIII   = 0x07,  
   CV_CFL_MIPS         = 0x10,  
   CV_CFL_MIPSR4000    = CV_CFL_MIPS,  
   CV_CFL_MIPS16       = 0x11,  
   CV_CFL_MIPS32       = 0x12,  
   CV_CFL_MIPS64       = 0x13,  
   CV_CFL_MIPSI        = 0x14,  
   CV_CFL_MIPSII       = 0x15,  
   CV_CFL_MIPSIII      = 0x16,  
   CV_CFL_MIPSIV       = 0x17,  
   CV_CFL_MIPSV        = 0x18,  
   CV_CFL_M68000       = 0x20,  
   CV_CFL_M68010       = 0x21,  
   CV_CFL_M68020       = 0x22,  
   CV_CFL_M68030       = 0x23,  
   CV_CFL_M68040       = 0x24,  
   CV_CFL_ALPHA        = 0x30,  
   CV_CFL_ALPHA_21064  = 0x30,  
   CV_CFL_ALPHA_21164  = 0x31,  
   CV_CFL_ALPHA_21164A = 0x32,  
   CV_CFL_ALPHA_21264  = 0x33,  
   CV_CFL_ALPHA_21364  = 0x34,  
   CV_CFL_PPC601       = 0x40,  
   CV_CFL_PPC603       = 0x41,  
   CV_CFL_PPC604       = 0x42,  
   CV_CFL_PPC620       = 0x43,  
   CV_CFL_PPCFP        = 0x44,  
   CV_CFL_SH3          = 0x50,  
   CV_CFL_SH3E         = 0x51,  
   CV_CFL_SH3DSP       = 0x52,  
   CV_CFL_SH4          = 0x53,  
   CV_CFL_SHMEDIA      = 0x54,  
   CV_CFL_ARM3         = 0x60,  
   CV_CFL_ARM4         = 0x61,  
   CV_CFL_ARM4T        = 0x62,  
   CV_CFL_ARM5         = 0x63,  
   CV_CFL_ARM5T        = 0x64,  
   CV_CFL_ARM6         = 0x65,  
   CV_CFL_ARM_XMAC     = 0x66,  
   CV_CFL_ARM_WMMX     = 0x67,  
   CV_CFL_OMNI         = 0x70,  
   CV_CFL_IA64         = 0x80,  
   CV_CFL_IA64_1       = 0x80,  
   CV_CFL_IA64_2       = 0x81,  
   CV_CFL_CEE          = 0x90,  
   CV_CFL_AM33         = 0xA0,  
   CV_CFL_M32R         = 0xB0,  
   CV_CFL_TRICORE      = 0xC0,  
   CV_CFL_X64          = 0xD0,  
   CV_CFL_AMD64        = CV_CFL_X64,  
   CV_CFL_EBC          = 0xE0,  
   CV_CFL_THUMB        = 0xF0  
   CV_CFL_ARMNT        = 0xF4,  
   CV_CFL_D3D11_SHADER = 0x100,  
} CV_CPU_TYPE_e;  
```  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se devuelven mediante una llamada a la [Get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)
