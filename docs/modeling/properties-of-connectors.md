---
title: Propiedades de los conectores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754f479b99eef44159994425ddd7a0d812bcf2ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970814"
---
# <a name="properties-of-connectors"></a>Propiedades de los conectores
Los conectores representan relaciones de dominio en un diseñador generado.

 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Los conectores tienen las propiedades que aparecen en la tabla siguiente.

|Propiedad|Descripción|Default|
|-|-|-|
|Color|El color de este conector.|Negro|
|Estilo de guión|El estilo de guión para la línea de este conector (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|
|Estilo del extremo de origen|El estilo del extremo de origen para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o ninguno).|Ninguna|
|Estilo del extremo de destino|El estilo del extremo de destino para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o ninguno).|Ninguna|
|Color del texto|El color que se usa para los elementos Decorator de texto que están asociados con este conector.|Negro|
|Thickness|El grosor de la línea para este conector, medido en pulgadas.|0.03125|
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de este conector.|\<none>|
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera desde el conector (`none`, `abstract` o `sealed`).|ninguna|
|Conector base|La clase base de este conector.|(ninguno)|
|Name|El nombre de este conector.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado a este conector.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si se ha corregido, a continuación, el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define mediante código personalizado.|\<none>|
|Notas|Notas informales que están asociadas con este conector.|\<none>|
|Estilo de enrutamiento|El estilo que se utiliza para enrutar el conector. Un `Rectilinear` conector hace ángulo recto activa según sea necesario; un `Straight` conector no es así.|Rectilíneo|
|Color expuesto como propiedad<br /><br /> Estilo de guión expuestos como propiedad<br /><br /> Grosor expuesto como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad indicada de una forma. Para ello, haga clic en la definición de la forma y haga clic en **agregar expuestos**.|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name|El nombre que se mostrará en el diseñador generado para este conector.|\<none>|
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este elemento.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)