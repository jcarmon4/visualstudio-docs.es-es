---
title: No se puede eliminar la propiedad porque participa en la asociación
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d277919229316768cde27efdc9b2797d0351e9fe
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458506"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>No se puede eliminar la propiedad &lt;nombre de propiedad&gt; porque participa en la asociación &lt;nombre de asociación&gt;

La propiedad seleccionada está establecida como **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.

Establezca la **propiedad de asociación** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. En **Object Relational Designer**, seleccione la línea de asociación que conecta las clases de datos indicadas en el mensaje de error.

2. Haga doble clic en la línea para abrir el cuadro de diálogo **Editor de asociaciones**.

3. Quite la propiedad de **Propiedades de la asociación**.

4. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)