---
title: VSTextBuffer (objeto) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a324db2226056fd3f41180055600671a8979a67
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312801"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer (objeto)
El objeto de búfer de texto representa una secuencia de texto Unicode, que suele estar asociado con un archivo. Un <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto puede utilizarse fuera del contexto del editor de núcleo, como en un asistente.

 En la tabla siguiente se muestra las interfaces de `VSTextBuffer`.

|Método|Descripción|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Interfaz OLE estándar. Se utiliza para controlar en el búfer de deshacer/rehacer.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Interfaz OLE estándar.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Interfaz OLE estándar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite la creación de acciones compuestos (es decir, las acciones que se agrupan en una unidad de deshacer y rehacer único).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita la persistencia de datos administrados por el búfer de texto del documento.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Proporciona servicios básicos; muchos clientes usan.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Se usa para buscar un búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Proporciona de lectura y escritura mediante coordenadas bidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Proporciona de lectura y escritura mediante coordenadas unidimensionales. Se hereda de `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Rápido, proporciona acceso secuencial orientado a secuencias al texto en el búfer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Proporciona acceso a una colección genérica de propiedades. La propiedad más importante es el nombre o el moniker del búfer. Puede almacenar sus propios datos aleatorios en el búfer con esta interfaz mediante la creación de un GUID y usarlo como clave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Admite puntos de conexión para los eventos.|

## <a name="remarks"></a>Comentarios
 El `VSTextBuffer` se encuentra normalmente por un `QueryInterface` llamar en `IVsTextBuffer`. Para obtener más información, consulte [búfer de texto](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Edición de cifras](https://www.microsoft.com/download/details.aspx?id=55984)