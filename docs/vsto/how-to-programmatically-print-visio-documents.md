---
title: Procedimiento Imprimir documentos de Visio mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bf492c866a43a0098fbcad5660a19c57fc90a3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955873"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procedimiento Imprimir documentos de Visio mediante programación
  Puede imprimir un documento de Microsoft Office Visio completo o solo una página concreta.

 Para obtener detalles sobre los métodos de impresión, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Document.Print) y [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Imprimir un documento de Visio

### <a name="to-print-a-complete-document"></a>Para imprimir un documento completo

- Llame al método `Microsoft.Office.Interop.Visio.Document.Print` del objeto `Microsoft.Office.Interop.Visio.Document` que quiere imprimir.

     En el siguiente ejemplo de código se imprime el documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Imprimir una página de un documento de Visio

### <a name="to-print-a-page-of-a-document"></a>Para imprimir una página de un documento

- Llame al método `Microsoft.Office.Interop.Visio.Pages.Print` del objeto `Microsoft.Office.Interop.Visio.Pages` que quiere imprimir.

     El siguiente ejemplo de código imprime la primera página del documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
