---
title: Funciones intrínsecas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 65a5272d74e1987cd7838932182e7e59c9c53f21
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923947"
---
# <a name="intrinsic-functions"></a>Funciones intrínsecas
Una expresión en SAL puede ser una expresión CC++ o siempre que se trata de una expresión que no tiene efectos secundarios; por ejemplo, + +,--, y las llamadas a función tienen efectos secundarios en este contexto.  Sin embargo, SAL proporciona algunos objetos similares a funciones y algunos símbolos reservados que se pueden usar en las expresiones SAL. Estas se conocen como *funciones intrínsecas*.

## <a name="general-purpose"></a>Uso general
Las siguientes anotaciones de la función intrínsecas proporcionan una utilidad general para SAL.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_Curr_`|Sinónimo del objeto que se está anotando actualmente.  Cuando la `_At_` anotación está en uso, `_Curr_` es igual que el primer parámetro de `_At_`.  De lo contrario, es el parámetro o el valor completo de la función o devolución con el que está asociada léxicamente la anotación.|
|`_Inexpressible_(expr)`|Expresa una situación en la que el tamaño de un búfer es demasiado complejo para representarlo mediante una expresión de anotación; por ejemplo, cuando se calcula examinando un conjunto de datos de entrada y contando a continuación los miembros seleccionados.|
|`_Nullterm_length_(param)`|`param`es el número de elementos del búfer hasta, pero sin incluir un terminador null. Se puede aplicar a cualquier búfer de tipo no agregado, no void.|
|`_Old_(expr)`|Cuando se evalúa en condición previa, `_Old_` devuelve el valor `expr`de entrada.  Cuando se evalúa en una condición posterior, devuelve el valor `expr` tal como se hubiera evaluado en condición previa.|
|`_Param_(n)`|El `n`parámetro TH para una función, contando entre `n`1 y, y `n` es una constante entera literal. Si el parámetro se denomina, esta anotación es idéntica a tener acceso al parámetro por su nombre. **Nota:** `n` puede hacer referencia a los parámetros posicionales definidos por puntos suspensivos o que se pueden usar en prototipos de función donde no se usan nombres.|
|`return`|La palabra claveC++ `return` C/Reserved se puede usar en una expresión sal para indicar el valor devuelto de una función.  El valor solo está disponible en post State; se trata de un error de sintaxis para usarlo en el estado anterior.|

## <a name="string-specific"></a>Específico de cadena
Las siguientes anotaciones de función intrínseca permiten la manipulación de cadenas. Las cuatro funciones tienen el mismo propósito: devolver el número de elementos del tipo que se encuentra antes de un terminador nulo. Las diferencias son los tipos de datos de los elementos a los que se hace referencia. Tenga en cuenta que si desea especificar la longitud de un búfer terminado en null que no está compuesto por caracteres, use la `_Nullterm_length_(param)` anotación de la sección anterior.

|Anotación|DESCRIPCIÓN|
|----------------|-----------------|
|`_String_length_(param)`|`param`es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación está reservada para tipos de cadena de caracteres.|
|`strlen(param)`|`param`es el número de elementos de la cadena hasta, pero sin incluir un terminador nulo. Esta anotación se reserva para su uso en matrices de caracteres y se parece a la función en tiempo de ejecución de C [strlen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|
|`wcslen(param)`|`param`es el número de elementos de la cadena hasta un terminador nulo (pero no se incluye). Esta anotación se reserva para su uso en matrices de caracteres anchos y se parece a la función de tiempo de ejecución de C [wcslen ()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)