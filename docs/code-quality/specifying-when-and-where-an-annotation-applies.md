---
title: Especificar cuándo y dónde se aplica una anotación
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6c7adb310db9eece1d8d4a2881057cc1acde1062
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923813"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Especificar cuándo y dónde se aplica una anotación
Cuando una anotación es condicional, puede requerir que otras anotaciones lo especifiquen en el analizador.  Por ejemplo, si una función tiene una variable que puede ser sincrónica o asincrónica, la función se comporta de la siguiente manera: En el caso sincrónico, siempre se realiza correctamente, pero en el caso asincrónico informa de un error si no puede realizarse inmediatamente. Cuando se llama a la función de forma sincrónica, la comprobación del valor del resultado no proporciona ningún valor al analizador de código porque no habría devuelto.  Sin embargo, cuando se llama a la función de forma asincrónica y no se comprueba el resultado de la función, podría producirse un error grave. En este ejemplo se muestra una situación en la que se puede `_When_` usar la anotación, descrita más adelante en este artículo, para habilitar la comprobación.

## <a name="structural-annotations"></a>Anotaciones estructurales
Para controlar cuándo y dónde se aplican las anotaciones, utilice las siguientes anotaciones estructurales.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`es una expresión que produce un valor l. Las anotaciones de `anno-list` se aplican al objeto denominado por `expr`. Para cada anotación de `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa, y en condición posterior si la anotación se interpreta en condición posterior.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`es una expresión que produce un valor l. Las anotaciones de `anno-list` se aplican al objeto denominado por `expr`. Para cada anotación de `anno-list`, `expr` se interpreta en condición previa si la anotación se interpreta en condición previa y en condición posterior si la anotación se interpreta en condición posterior.<br /><br /> `iter`es el nombre de una variable cuyo ámbito es la anotación (inclusiva `anno-list`). `iter`tiene un tipo `long`implícito. Las variables con el mismo nombre en cualquier ámbito de inclusión se ocultan de la evaluación.<br /><br /> `elem-count`es una expresión que se evalúa como un entero.|
|`_Group_(anno-list)`|Todas las anotaciones de `anno-list` se consideran que tienen cualquier calificador que se aplique a la anotación de grupo que se aplica a cada anotación.|
|`_When_(expr, anno-list)`|`expr`es una expresión que se puede convertir en `bool`. Cuando es distinto de cero (`true`), las anotaciones que se especifican en `anno-list` se consideran aplicables.<br /><br /> De forma predeterminada, para cada anotación en `anno-list`, `expr` se interpreta como si se usaran los valores de entrada si la anotación es una condición previa, y como si se usaran los valores de salida si la anotación es una condición posterior. Para reemplazar el valor predeterminado, puede usar el `_Old_` intrínseco al evaluar una condición posterior para indicar que se deben usar los valores de entrada. **Nota:**  Se pueden habilitar diferentes anotaciones como consecuencia del uso `_When_` de si un valor mutable (por ejemplo, `*pLength`) está implicado porque el resultado evaluado de `expr` en condición previa puede diferir del resultado evaluado en la condición posterior.|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)