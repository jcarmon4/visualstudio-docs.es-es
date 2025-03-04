---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75369df719b0cd140ce621e916215eb18cf30a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787624"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Agrega una instancia secundaria de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isn`  
 [in] El índice del elemento secundario en el elemento primario.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación usado para asociar la entrada secundaria con el objeto host.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Para el análisis, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script.  
  
 El delimitador permite que el motor para proporcionar el preprocesamiento de creación de script. Por ejemplo, el motor podría reemplazar una comilla simple con dos comillas simples para su uso como un delimitador. El motor determina cómo se usa el delimitador.  
  
 Se establece en NULL si un delimitador no marca el final del bloque de script.  
  
 `ppse`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptEntry` interfaz de la instancia secundaria.  
  
 Para `IScriptNode` objetos que representan una página Web, este parámetro devuelve un `IScriptEntry` instancia que especifica un bloque de script.  
  
 Para `IScriptEntry` objetos que representan un bloque de script, este parámetro devuelve un `IScriptEntry` instancia que especifica un objeto de función.  
  
 Para `IScriptEntry` objetos que representan una función de objeto, este método produce un error.  
  
 Para `IScriptScriptlet` objetos, este método produce un error.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El `IScriptNode` interfaz representa una página Web o sus elementos. El `IScriptEntry` interfaz (que se deriva `IScriptNode`) representa un bloque de script o un objeto de función. El `IScriptScriptlet` interfaz (que se deriva `IScriptEntry`) representa un controlador de eventos.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (interfaz)](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)