---
title: Actualizar datos mediante un TableAdapter | Microsoft Docs
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30d1fd3ee211d6b30f435104a2e2f9b42ed100c0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692344"
---
# <a name="update-data-by-using-a-tableadapter"></a>Actualizar datos mediante un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de modificar y validados los datos del conjunto de datos, puede enviar los datos actualizados a una llamada databaseby el `Update` método de un TableAdapter. El `Update` método actualiza una tabla de datos única y se ejecuta el comando correcto (INSERT, UPDATE o DELETE) basándose en la <xref:System.Data.DataRow.RowState%2A> de cada fila de datos en la tabla. Cuando un conjunto de datos con tablas relacionadas, Visual Studio genera una clase TableAdapterManager que usar para realizar las actualizaciones. La clase TableAdapterManager garantiza que las actualizaciones se realizan en el orden correcto basándose en las restricciones de clave externa que se definen en la base de datos. Cuando utilice controles enlazados a datos, la arquitectura de enlace de datos crea una variable de miembro de la clase TableAdapterManager llamada tableAdapterManager. Para obtener más información, consulte [información general de actualización jerárquica](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
> Al intentar actualizar un origen de datos con el contenido de un conjunto de datos, puede obtener errores. Para evitar errores, se recomienda recomiendautilizar coloca el código que llama el adaptador `Update` método dentro de un `try` / `catch` bloque.  
  
 El procedimiento exacto para actualizar un origen de datos puede variar según las necesidades empresariales, pero incluye los siguientes pasos:  
  
1. Llame a la del adaptador `Update` método en un `try` / `catch` bloque.  
  
2. Si se detecta una excepción, buscar la fila de datos que causó el error. Para obtener más información, vea [Cómo: Localizar filas con errores](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3. Concilie el problema de los datos de fila (mediante programación si es posible, o mediante la presentación de la fila no válida para el usuario para la modificación) y, a continuación, inténtelo de nuevo la actualización (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData a una base de datos  
 Llame a la `Update` método de un TableAdapter. Pase el nombre de la tabla de datos que contiene los valores que se escriban en la base de datos.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para actualizar una base de datos mediante un TableAdapter  
  
- Incluya el TableAdapter`Update` método en un `try` / `catch` bloque. El ejemplo siguiente muestra cómo actualizar el contenido de la `Customers` tabla `NorthwindDataSet` desde dentro un `try` / `catch` bloque.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
