---
title: Conjunto de reglas Reglas recomendadas mixtas
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4401417aba2055e7b2189db6bf33503668c2a658
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585318"
---
# <a name="mixed-recommended-rules-rule-set"></a>Conjunto de reglas Reglas recomendadas mixtas

Las reglas recomendadas mixtas de Microsoft se centran en los problemas más C++ comunes y críticos de los proyectos que admiten Common Language Runtime, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Este conjunto de reglas incluye todas las reglas del conjunto de reglas [reglas mínimas mixtas](mixed-minimum-rules-rule-set.md) .

Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree C++ para los proyectos que admiten Common Language Runtime.

|Regla|DESCRIPCIÓN|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Uso de la memoria sin inicializar|
|[C6011](../code-quality/c6011.md)|Desreferenciación de un puntero null|
|[C6029](../code-quality/c6029.md)|Uso de un valor sin comprobar|
|[C6031](../code-quality/c6031.md)|Valor devuelto omitido|
|[C6053](../code-quality/c6053.md)|Terminación en cero de la llamada|
|[C6054](../code-quality/c6054.md)|Falta terminación cero|
|[C6059](../code-quality/c6059.md)|Concatenación incorrecta|
|[C6063](../code-quality/c6063.md)|Falta el argumento de cadena para la función de formato|
|[C6064](../code-quality/c6064.md)|Falta el argumento de entero para la función de formato|
|[C6066](../code-quality/c6066.md)|Falta el argumento de puntero para la función de formato|
|[C6067](../code-quality/c6067.md)|Falta el argumento de puntero de cadena para la función de formato|
|[C6101](../code-quality/c6101.md)|Devolución de memoria sin inicializar|
|[C6200](../code-quality/c6200.md)|El índice supera el valor máximo para el búfer|
|[C6201](../code-quality/c6201.md)|El índice supera el valor máximo para el búfer de pila|
|[C6214](../code-quality/c6214.md)|VALOR HRESULT de conversión no válido en BOOL|
|[C6215](../code-quality/c6215.md)|Conversión no válida de BOOL a HRESULT|
|[C6216](../code-quality/c6216.md)|VALOR BOOLEANO de conversión insertada en el compilador no válido|
|[C6217](../code-quality/c6217.md)|Prueba HRESULT no válida con NOT|
|[C6220](../code-quality/c6220.md)|Comparación de HRESULT no válida con-1|
|[C6226](../code-quality/c6226.md)|Asignación de HRESULT no válida a-1|
|[C6230](../code-quality/c6230.md)|Uso de HRESULT no válido como booleano|
|[C6235](../code-quality/c6235.md)|Constante distinta de cero con OR lógico|
|[C6236](../code-quality/c6236.md)|OR lógico con constante distinta de cero|
|[C6237](../code-quality/c6237.md)|Cero con efectos lógicos y pierde efectos secundarios|
|[C6242](../code-quality/c6242.md)|Desenredo local forzado|
|[C6248](../code-quality/c6248.md)|Creando DACL null|
|[C6250](../code-quality/c6250.md)|Descriptores de dirección no liberados|
|[C6255](../code-quality/c6255.md)|Uso no protegido de alloca|
|[C6258](../code-quality/c6258.md)|Usar el subproceso Terminate|
|[C6259](../code-quality/c6259.md)|Código muerto en un conmutador de bits o limitado|
|[C6260](../code-quality/c6260.md)|Uso de aritmética de bytes|
|[C6262](../code-quality/c6262.md)|Uso excesivo de la pila|
|[C6263](../code-quality/c6263.md)|Usar alloca in (bucle)|
|[C6268](../code-quality/c6268.md)|Faltan paréntesis en la conversión|
|[C6269](../code-quality/c6269.md)|Desreferencia de puntero omitida|
|[C6270](../code-quality/c6270.md)|Falta el argumento float para la función de formato|
|[C6271](../code-quality/c6271.md)|Argumento adicional para la función de formato|
|[C6272](../code-quality/c6272.md)|Argumento no flotante para la función de formato|
|[C6273](../code-quality/c6273.md)|Argumento no entero para la función de formato|
|[C6274](../code-quality/c6274.md)|Argumento sin caracteres para la función de formato|
|[C6276](../code-quality/c6276.md)|Conversión de cadena no válida|
|[C6277](../code-quality/c6277.md)|Llamada no válida a CreateProcess|
|[C6278](../code-quality/c6278.md)|Matriz: nueva no coincidente de eliminación escalar|
|[C6279](../code-quality/c6279.md)|Escalar-nueva matriz: eliminación no coincidente|
|[C6280](../code-quality/c6280.md)|Asignación de memoria: desasignación no coincidente|
|[C6281](../code-quality/c6281.md)|Precedencia de relación bit a bit|
|[C6282](../code-quality/c6282.md)|La asignación reemplaza la prueba|
|[C6283](../code-quality/c6283.md)|Matriz primitiva: no coincide el nuevo escalar-eliminación|
|[C6284](../code-quality/c6284.md)|Argumento de objeto no válido para la función de formato|
|[C6285](../code-quality/c6285.md)|Logical-or de constantes|
|[C6286](../code-quality/c6286.md)|Efectos secundarios que no son de cero o de pérdida|
|[C6287](../code-quality/c6287.md)|Prueba redundante|
|[C6288](../code-quality/c6288.md)|La inclusión mutua sobre Logical-and es false|
|[C6289](../code-quality/c6289.md)|La exclusión mutua sobre el operador lógico or es true|
|[C6290](../code-quality/c6290.md)|Prioridad entre operadores NOT lógico y AND bit a bit|
|[C6291](../code-quality/c6291.md)|Prioridad entre operadores NOT lógico y OR bit a bit|
|[C6292](../code-quality/c6292.md)|Número máximo de bucles|
|[C6293](../code-quality/c6293.md)|El número de bucles es inferior al mínimo|
|[C6294](../code-quality/c6294.md)|El cuerpo del bucle nunca se ejecutó|
|[C6295](../code-quality/c6295.md)|Bucle infinito|
|[C6296](../code-quality/c6296.md)|El bucle solo se ejecuta una vez|
|[C6297](../code-quality/c6297.md)|Resultado de la conversión de mayúsculas a un tamaño mayor|
|[C6299](../code-quality/c6299.md)|Comparación de bits a booleano|
|[C6302](../code-quality/c6302.md)|Argumento de cadena de caracteres no válido para la función de formato|
|[C6303](../code-quality/c6303.md)|Argumento de cadena de caracteres anchos no válido para la función de formato|
|[C6305](../code-quality/c6305.md)|Error de coincidencia en el uso de size y count|
|[C6306](../code-quality/c6306.md)|Llamada incorrecta a función de argumento variable|
|[C6308](../code-quality/c6308.md)|Pérdida de realloc|
|[C6310](../code-quality/c6310.md)|Constante de filtro de excepción no válida|
|[C6312](../code-quality/c6312.md)|Bucle de ejecución de excepción continua|
|[C6314](../code-quality/c6314.md)|Precedencia OR bit a bit|
|[C6317](../code-quality/c6317.md)|No complementario|
|[C6318](../code-quality/c6318.md)|Exception continue Search|
|[C6319](../code-quality/c6319.md)|Omitido por coma|
|[C6324](../code-quality/c6324.md)|Copia de cadena en lugar de comparación de cadenas|
|[C6328](../code-quality/c6328.md)|Error de coincidencia de tipo de argumento potencial|
|[C6331](../code-quality/c6331.md)|No hay marcas válidas de VirtualFree|
|[C6332](../code-quality/c6332.md)|Parámetro no válido de VirtualFree|
|[C6333](../code-quality/c6333.md)|VirtualFree tamaño no válido|
|[C6335](../code-quality/c6335.md)|Identificador del proceso de fuga|
|[C6381](../code-quality/c6381.md)|Falta la información de apagado|
|[C6383](../code-quality/c6383.md)|Elemento-Count recuento de bytes: saturación del búfer de recuento|
|[C6384](../code-quality/c6384.md)|División de tamaño de puntero|
|[C6385](../code-quality/c6385.md)|Saturación de lectura|
|[C6386](../code-quality/c6386.md)|Saturación de escritura|
|[C6387](../code-quality/c6387.md)|Valor de parámetro no válido|
|[C6388](../code-quality/c6388.md)|Valor de parámetro no válido|
|[C6500](../code-quality/c6500.md)|Propiedad de atributo no válida|
|[C6501](../code-quality/c6501.md)|Valores de propiedad de atributo en conflicto|
|[C6503](../code-quality/c6503.md)|Las referencias no pueden ser null|
|[C6504](../code-quality/c6504.md)|Null en valores que no son de puntero|
|[C6505](../code-quality/c6505.md)|MustCheck en valores void|
|[C6506](../code-quality/c6506.md)|Tamaño de búfer en valores que no son de puntero o matriz|
|[C6508](../code-quality/c6508.md)|Acceso de escritura en valores constantes|
|[C6509](../code-quality/c6509.md)|Return usado en condición previa|
|[C6510](../code-quality/c6510.md)|NullTerminated en valores que no son de puntero|
|[C6511](../code-quality/c6511.md)|MustCheck debe ser Yes o No|
|[C6513](../code-quality/c6513.md)|ElementSize sin tamaño de búfer|
|[C6514](../code-quality/c6514.md)|El tamaño del búfer supera el tamaño de la matriz|
|[C6515](../code-quality/c6515.md)|Tamaño de búfer en valores que no son de puntero|
|[C6516](../code-quality/c6516.md)|No hay propiedades del atributo|
|[C6517](../code-quality/c6517.md)|Tamaño válido en búfer no legible|
|[C6518](../code-quality/c6518.md)|Tamaño de escritura en búfer no modificable|
|[C6522](../code-quality/c6522.md)|Tipo de cadena de tamaño no válido|
|[C6525](../code-quality/c6525.md)|Cadena de tamaño no válida, ubicación inaccesible|
|[C6527](../code-quality/c6527.md)|Anotación no válida: La propiedad ' NeedsRelease ' no se puede usar en valores de tipo void|
|[C6530](../code-quality/c6530.md)|Estilo de cadena de formato no reconocido|
|[C6540](../code-quality/c6540.md)|El uso de anotaciones de atributo en esta función invalidará todas las anotaciones __declspec existentes|
|[C6551](../code-quality/c6551.md)|Especificación de tamaño no válido: no se puede analizar la expresión|
|[C6552](../code-quality/c6552.md)|Valor Deref= o Notref= no válido: no se puede analizar la expresión|
|[C6701](../code-quality/c6701.md)|Este no es un valor Yes/No/Maybe válido|
|[C6702](../code-quality/c6702.md)|Este no es un valor de cadena|
|[C6703](../code-quality/c6703.md)|El valor no es un número|
|[C6704](../code-quality/c6704.md)|Error de expresión de anotación inesperado|
|[C6705](../code-quality/c6705.md)|El número esperado de argumentos para la anotación no coincide con el número real de argumentos para la anotación|
|[C6706](../code-quality/c6706.md)|Error inesperado de la anotación|
|[C6995](../code-quality/c6995.md)|No se pudo guardar el archivo de registro XML|
|[C26100](../code-quality/c26100.md)|Condición de carrera|
|[C26101](../code-quality/c26101.md)|No se puede usar la operación de interbloqueo correctamente|
|[C26110](../code-quality/c26110.md)|El autor de la llamada no puede contener el bloqueo|
|[C26111](../code-quality/c26111.md)|No se pudo liberar el bloqueo del autor de la llamada|
|[C26112](../code-quality/c26112.md)|El autor de la llamada no puede contener ningún bloqueo|
|[C26115](../code-quality/c26115.md)|No se pudo liberar el bloqueo|
|[C26116](../code-quality/c26116.md)|No se puede adquirir o mantener el bloqueo|
|[C26117](../code-quality/c26117.md)|Liberación de bloqueo no retenido|
|[C26140](../code-quality/c26140.md)|Error de anotación SAL de simultaneidad|
|[C28020](../code-quality/c28020.md)|La expresión no es true en esta llamada|
|[C28021](../code-quality/c28021.md)|El parámetro que se va a anotar debe ser un puntero|
|[C28022](../code-quality/c28022.md)|Las clases de función de esta función no coinciden con las clases de función de la definición de tipo que se usa para definirla.|
|[C28023](../code-quality/c28023.md)|La función que se va a asignar o pasar \_debe\_tener\_ una anotación de clase de función para al menos una de las clases.|
|[C28024](../code-quality/c28024.md)|El puntero de función al que se asigna se anota con la clase de función, que no está incluida en la lista de clases de función.|
|[C28039](../code-quality/c28039.md)|El tipo de parámetro real debe coincidir exactamente con el tipo|
|[C28112](../code-quality/c28112.md)|Siempre se debe tener acceso a una variable a la que se tiene acceso a través de una función de interbloqueo a través de una función de interbloqueo.|
|[C28113](../code-quality/c28113.md)|Obtener acceso a una variable local a través de una función de interbloqueo|
|[C28125](../code-quality/c28125.md)|Se debe llamar a la función desde un bloque try/except|
|[C28137](../code-quality/c28137.md)|En su lugar, el argumento variable debe ser una constante (literal)|
|[C28138](../code-quality/c28138.md)|En su lugar, el argumento Constant debe ser variable|
|[C28159](../code-quality/c28159.md)|Considere la posibilidad de usar otra función en su lugar.|
|[C28160](../code-quality/c28160.md)|Error (anotación)|
|[C28163](../code-quality/c28163.md)|Nunca se debe llamar a la función desde dentro de un bloque try/except|
|[C28164](../code-quality/c28164.md)|El argumento se pasa a una función que espera un puntero a un objeto (no un puntero a un puntero)|
|[C28182](../code-quality/c28182.md)|Desreferenciación de un puntero null. El puntero contiene el mismo valor NULL que otro puntero.|
|[C28183](../code-quality/c28183.md)|El argumento puede ser un valor y es una copia del valor encontrado en el puntero|
|[C28193](../code-quality/c28193.md)|La variable contiene un valor que se debe examinar.|
|[C28196](../code-quality/c28196.md)|No se cumple el requisito. (La expresión no se evalúa como true).|
|[C28202](../code-quality/c28202.md)|Referencia no válida a un miembro no estático|
|[C28203](../code-quality/c28203.md)|Referencia ambigua a un miembro de la clase.|
|[C28205](../code-quality/c28205.md)|\_Correcto\_ \_o \_en casode\_ error usado en un contexto no válido|
|[C28206](../code-quality/c28206.md)|El operando izquierdo señala a un struct, use '->'|
|[C28207](../code-quality/c28207.md)|El operando izquierdo es un struct, use '->'|
|[C28209](../code-quality/c28209.md)|La declaración del símbolo tiene una declaración en conflicto|
|[C28210](../code-quality/c28210.md)|Las anotaciones del contexto __on_failure no deben estar en un contexto previo explícito|
|[C28211](../code-quality/c28211.md)|Se esperaba un nombre de contexto estático para SAL_context|
|[C28212](../code-quality/c28212.md)|Se esperaba una expresión de puntero para la anotación|
|[C28213](../code-quality/c28213.md)|La \_anotación\_usar\_anotacionesdecl\_ debe usarse para hacer referencia, sin modificación, a una declaración anterior.|
|[C28214](../code-quality/c28214.md)|Los nombres de los parámetros de atributo deben ser p1...p9|
|[C28215](../code-quality/c28215.md)|typefix no se puede aplicar a un parámetro que ya tenga un typefix|
|[C28216](../code-quality/c28216.md)|La anotación checkReturn solamente se aplica a las condiciones posteriores del parámetro de la función específica.|
|[C28217](../code-quality/c28217.md)|Para la función, el número de parámetros de la anotación no coincide con el encontrado en el archivo|
|[C28218](../code-quality/c28218.md)|En el caso del parámetro de función, el parámetro de la anotación no coincide con el que se encuentra en el archivo.|
|[C28219](../code-quality/c28219.md)|Se esperaba un miembro de enumeración para el parámetro de la anotación|
|[C28220](../code-quality/c28220.md)|Se esperaba una expresión de entero para el parámetro de la anotación|
|[C28221](../code-quality/c28221.md)|Se esperaba una expresión de cadena para el parámetro de la anotación|
|[C28222](../code-quality/c28222.md)|Se esperaba __yes, \__no, o \__maybe para la anotación|
|[C28223](../code-quality/c28223.md)|No se encontró el token o identificador para la anotación, parámetro|
|[C28224](../code-quality/c28224.md)|La anotación requiere parámetros|
|[C28225](../code-quality/c28225.md)|No se encontró el número correcto de parámetros necesarios en la anotación|
|[C28226](../code-quality/c28226.md)|La anotación no puede ser un PrimOp (en la declaración actual)|
|[C28227](../code-quality/c28227.md)|La anotación no puede ser un PrimOp (consulte la declaración anterior)|
|[C28228](../code-quality/c28228.md)|Parámetro de anotación: no se puede usar un tipo en las anotaciones|
|[C28229](../code-quality/c28229.md)|La anotación no admite parámetros|
|[C28230](../code-quality/c28230.md)|El tipo de parámetro no tiene ningún miembro.|
|[C28231](../code-quality/c28231.md)|La anotación solo es válida en la matriz|
|[C28232](../code-quality/c28232.md)|pre, post o deref no se aplican a ninguna anotación|
|[C28233](../code-quality/c28233.md)|pre, post o deref se aplican a un bloque|
|[C28234](../code-quality/c28234.md)|La expresión __at no se aplica a la función actual|
|[C28235](../code-quality/c28235.md)|La función no puede actuar por sí sola como una anotación|
|[C28236](../code-quality/c28236.md)|La anotación no se puede usar en una expresión|
|[C28237](../code-quality/c28237.md)|La anotación del parámetro ya no se admite|
|[C28238](../code-quality/c28238.md)|La anotación del parámetro tiene más de un valor, stringValue y longValue Use paramn=xxx|
|[C28239](../code-quality/c28239.md)|La anotación del parámetro tiene el valor stringValue o longValue, y paramn=xxx. Use solo paramn=xxx|
|[C28240](../code-quality/c28240.md)|La anotación del parámetro tiene param2 pero no param1|
|[C28241](../code-quality/c28241.md)|La anotación para la función del parámetro no se reconoce|
|[C28243](../code-quality/c28243.md)|La anotación para la función del parámetro requiere más desreferenciaciones de las que permite el tipo real anotado|
|[C28244](../code-quality/c28244.md)|La anotación de la función tiene un parámetro o anotación externa no analizable|
|[C28245](../code-quality/c28245.md)|La anotación para la función anota 'this' en una en una función no miembro|
|[C28246](../code-quality/c28246.md)|La anotación del parámetro para la función no coincide con el tipo del parámetro|
|[C28250](../code-quality/c28250.md)|Anotación incoherente de la función: la instancia anterior tiene un error.|
|[C28251](../code-quality/c28251.md)|Anotación incoherente de la función: esta instancia tiene un error.|
|[C28252](../code-quality/c28252.md)|Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.|
|[C28253](../code-quality/c28253.md)|Anotación incoherente de la función: el parámetro tiene otra anotación en esta instancia.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() no se admite en anotaciones|
|[C28262](../code-quality/c28262.md)|Se encontró un error de sintaxis de anotación en la función, para la anotación|
|[C28263](../code-quality/c28263.md)|Se encontró un error de sintaxis en una anotación condicional para la anotación intrínseca|
|[C28267](../code-quality/c28267.md)|Se encontró un error de sintaxis de anotaciones en la función.|
|[C28272](../code-quality/c28272.md)|La anotación del parámetro de la función, al examinar su incoherencia con la declaración de la función|
|[C28273](../code-quality/c28273.md)|Para la función, las pistas son incoherentes con la declaración de la función|
|[C28275](../code-quality/c28275.md)|El parámetro para \_el\_valor\_ de la macro es null|
|[C28279](../code-quality/c28279.md)|Para el símbolo, se encontró un 'begin' sin un 'end' coincidente|
|[C28280](../code-quality/c28280.md)|Para el símbolo, se encontró un 'end' sin un 'begin' coincidente|
|[C28282](../code-quality/c28282.md)|Las cadenas de formato deben estar en las condiciones previas|
|[C28285](../code-quality/c28285.md)|Para la función, error de sintaxis en el parámetro|
|[C28286](../code-quality/c28286.md)|Para la función, error de sintaxis cerca del final|
|[C28287](../code-quality/c28287.md)|Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no reconocido)|
|[C28288](../code-quality/c28288.md)|Para la función, error de sintaxis en la anotación \_At\_() (nombre de parámetro no válido)|
|[C28289](../code-quality/c28289.md)|Para la función: Readto o grabable no tenía una especificación de límite como parámetro|
|[C28290](../code-quality/c28290.md)|la anotación de la función contiene más valores External que el número real de parámetros|
|[C28291](../code-quality/c28291.md)|El valor null/notnull posterior en el nivel 0 de desreferenciación carece de sentido para la función.|
|[C28300](../code-quality/c28300.md)|Operandos de expresión de tipos no compatibles para el operador|
|[C28301](../code-quality/c28301.md)|No hay anotaciones para la primera declaración de la función.|
|[C28302](../code-quality/c28302.md)|Se encontró un operador \_Deref\_ adicional en la anotación.|
|[C28303](../code-quality/c28303.md)|Se encontró un operador \_Deref\_ ambiguo en la anotación.|
|[C28304](../code-quality/c28304.md)|Se encontró un operador \_Notref\_ mal colocado aplicado al token.|
|[C28305](../code-quality/c28305.md)|Se descubrió un error al analizar un token.|
|[C28306](../code-quality/c28306.md)|La anotación en el parámetro es obsoleta|
|[C28307](../code-quality/c28307.md)|La anotación en el parámetro es obsoleta|
|[C28350](../code-quality/c28350.md)|La anotación describe una situación no aplicable de forma condicional.|
|[C28351](../code-quality/c28351.md)|La anotación describe dónde no se puede usar un valor dinámico (una variable) en la condición.|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Declarar los controladores de evento correctamente|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marcar los ensamblados con AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Los tipos secundarios deben poder llamar a los métodos de interfaz|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Los tipos que poseen recursos nativos deben ser descartables|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Mover P/Invokes a la clase NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|No ocultar métodos de clase base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementar IDisposable correctamente|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|No producir excepciones en ubicaciones inesperadas|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar los aceleradores duplicados|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Debe haber puntos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Los elementos P/Invoke no deben estar visibles|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Los tipos de diseño automático no deben ser visibles a través de COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Llamar a GetLastError inmediatamente después de P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Los métodos de registro COM deben coincidir|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Declarar elementos P/Invoke correctamente|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar finalizadores vacíos|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Los campos de tipo de valor deben ser portátiles|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Las declaraciones P/Invoke deben ser portátiles|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|No bloquear objetos con identidad débil|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Revisar consultas SQL para comprobar si tienen vulnerabilidades de seguridad|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar serialización en argumentos de cadena P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revisar la seguridad declarativa en los tipos de valores|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Los punteros no deben estar visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Los tipos seguros no deben exponer campos|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La seguridad del método debe ser un supraconjunto del tipo|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Los métodos APTCA deben llamar solo a métodos APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Los tipos APTCA solo amplían tipos base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|No exponer indirectamente métodos con peticiones de vínculos|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Las peticiones de vínculos de invalidaciones deben ser idénticas a la base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluir cláusulas finally vulnerables en un bloque try externo|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Las peticiones de vínculos de tipos requieren peticiones de herencias|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Los delegados deben enlazarse a métodos con una transparencia coherente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Los métodos deben mantener una transparencia coherente al invalidar métodos base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Los métodos transparentes deben contener solo IL que se pueda comprobar|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|El código transparente no debe hacer referencia a elementos críticos para la seguridad|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Los métodos transparentes no deben satisfacer LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Los métodos transparentes no pueden usar aserciones de seguridad|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Los métodos transparentes no deben llamar a código nativo|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Reiniciar para mantener los detalles de la pila|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|No usar Dispose varias veces en objetos|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializar campos estáticos de tipo de valor insertados|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|No marcar los componentes con servicio como WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos descartables deben ser descartables|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|No llamar a métodos reemplazables en constructores|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Los tipos descartables deben declarar el finalizador|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Los finalizadores deben llamar al finalizador de la clase base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementar constructores de serialización|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Marcar puntos de entrada de Windows Forms con STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marcar todos los campos no serializables|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Llamar a métodos de clase base en tipos ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marcar los tipos ISerializable con SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementar métodos de serialización correctamente|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementar ISerializable correctamente|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Proporcionar argumentos correctos a los métodos de formato|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Comprobar NaN correctamente|