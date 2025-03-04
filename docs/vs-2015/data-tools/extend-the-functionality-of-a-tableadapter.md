---
title: Extender la funcionalidad de un TableAdapter | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e14acedeab457df10cc011a94f96d7202972eea
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697896"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ampliar la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.  
  
 El código que define un TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de Dataset**, o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que el código que se eliminen durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.  
  
 Las clases parciales permiten que el código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (tipos)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Busque los TableAdapters en el código  
 Aunque los TableAdapters están diseñados con la **Diseñador de Dataset**, las clases TableAdapter generadas no son las clases anidadas de <xref:System.Data.DataSet>. Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de datos del TableAdapter asociado. Por ejemplo, si la aplicación contiene un conjunto de datos denominado `HRDataSet`, los TableAdapters se encontrarían en el `HRDataSetTableAdapters` espacio de nombres. (La convención de nomenclatura sigue este patrón: *DatasetName* + `TableAdapters`).  
  
 En el siguiente ejemplo se da por supuesto un TableAdapter llamado `CustomersTableAdapter`está en un proyecto con `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter  
  
1. Agregar una nueva clase al proyecto, vaya a la **proyecto** menú y seleccionando**Agregar clase**.  
  
2. Asigne a la clase el nombre `CustomersTableAdapterExtended`.  
  
3. Seleccione **Agregar**.  
  
4. Reemplace el código con el espacio de nombres correcto y el nombre de clase parcial para el proyecto como sigue:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
