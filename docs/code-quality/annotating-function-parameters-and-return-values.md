---
title: Anotar parámetros de función y valores devueltos
ms.date: 07/11/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 8f07650e47398b028460776f41557a3f853eaad3
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919615"
---
# <a name="annotating-function-parameters-and-return-values"></a>Anotar parámetros de función y valores devueltos
En este artículo se describen los usos habituales de las anotaciones para parámetros de funciones simples, escalares y punteros a estructuras y clases, y la mayoría de los tipos de búferes.  En este artículo también se muestran patrones de uso comunes para las anotaciones. Para obtener más anotaciones relacionadas con las funciones, consulte anotar el comportamiento de la [función](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parámetros de puntero
En el caso de las anotaciones de la tabla siguiente, cuando se anota un parámetro de puntero, el analizador informa de un error si el puntero es NULL.  Esto se aplica a los punteros y a cualquier elemento de datos al que se señale.

**Anotaciones y descripciones**

- `_In_`

     Anota los parámetros de entrada que son escalares, estructuras, punteros a estructuras y similares.  Se puede usar explícitamente en escalares simples.  El parámetro debe ser válido en el estado anterior y no se modificará.

- `_Out_`

     Anota los parámetros de salida que son escalares, estructuras, punteros a estructuras y similares.  No se aplica a un objeto que no puede devolver un valor, por ejemplo, un valor escalar que se pasa por valor.  No es necesario que el parámetro sea válido en el estado anterior, pero debe ser válido en post-State.

- `_Inout_`

     Anota un parámetro que la función va a cambiar.  Debe ser válido en el estado anterior y posterior, pero se supone que tiene valores distintos antes y después de la llamada. Debe aplicarse a un valor modificable.

- `_In_z_`

     Puntero a una cadena terminada en null que se usa como entrada.  La cadena debe ser válida en el estado anterior.  Se prefieren `PSTR`las variantes de, que ya tienen las anotaciones correctas.

- `_Inout_z_`

     Puntero a una matriz de caracteres terminada en null que se va a modificar.  Debe ser válido antes y después de la llamada, pero se supone que el valor ha cambiado.  Se puede moverse el terminador null, pero solo se puede tener acceso a los elementos hasta el terminador null original.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Puntero a una matriz, que es leída por la función.  La matriz es de elementos `s` de tamaño, todos los cuales deben ser válidos.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_In_reads_z_(s)`

     Puntero a una matriz terminada en NULL y tiene un tamaño conocido. Los elementos hasta el terminador nulo, o `s` si no hay ningún terminador nulo, deben ser válidos en el estado anterior.  Si el tamaño se conoce en bytes, escale `s` según el tamaño del elemento.

- `_In_reads_or_z_(s)`

     Puntero a una matriz terminada en null o tiene un tamaño conocido, o ambos. Los elementos hasta el terminador nulo, o `s` si no hay ningún terminador nulo, deben ser válidos en el estado anterior.  Si el tamaño se conoce en bytes, escale `s` según el tamaño del elemento.  (Se usa para `strn` la familia.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Puntero a una matriz de `s` elementos (resp. bytes) que escribirá la función.  Los elementos de la matriz no tienen que ser válidos en el estado anterior y el número de elementos que son válidos en post-State no está especificado.  Si hay anotaciones en el tipo de parámetro, se aplican en el estado posterior. Por ejemplo, considere el fragmento de código siguiente:

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     En este ejemplo, el autor de la llamada proporciona un `size` búfer de `p1`elementos para.  `MyStringCopy`hace que algunos de esos elementos sean válidos. Lo que es más importante `_Null_terminated_` , la anotación `PWSTR` en significa `p1` que termina en null en post-State.  De esta manera, el número de elementos válidos sigue siendo bien definido, pero no se requiere un recuento específico de elementos.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_Out_writes_z_(s)`

     Puntero a una matriz de `s` elementos.  Los elementos no tienen que ser válidos en el estado anterior.  En el estado posterior, los elementos hasta el terminador nulo (que debe estar presente) deben ser válidos.  Si el tamaño se conoce en bytes, escale `s` según el tamaño del elemento.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Puntero a una matriz, que se lee y se escribe en la función.  Es de elementos de `s` tamaño y válido en estado anterior y posterior.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_Inout_updates_z_(s)`

     Puntero a una matriz terminada en NULL y tiene un tamaño conocido. Los elementos hasta el terminador nulo (que debe estar presente) deben ser válidos en el estado anterior y posterior.  Se supone que el valor de post-State es diferente del valor en el estado anterior; Esto incluye la ubicación del terminador null. Si el tamaño se conoce en bytes, escale `s` según el tamaño del elemento.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Puntero a una matriz de `s` elementos.  Los elementos no tienen que ser válidos en el estado anterior.  En post-State, los elementos hasta el `c`elemento-TH deben ser válidos.  Si el tamaño se conoce en bytes, `s` escale `c` y por el tamaño del elemento o `_bytes_` use la variante, que se define como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, cada elemento que existe en el búfer hasta `s` en el estado anterior es válido en el estado posterior.  Por ejemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Puntero a una matriz, que es leída y escrita por la función.  Se trata de elementos `s` de tamaño, todos los cuales deben ser válidos en el estado anterior `c` , y los elementos deben ser válidos en post-State.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_Inout_updates_z_(s)`

     Puntero a una matriz terminada en NULL y tiene un tamaño conocido. Los elementos hasta el terminador nulo (que debe estar presente) deben ser válidos en el estado anterior y posterior.  Se supone que el valor de post-State es diferente del valor en el estado anterior; Esto incluye la ubicación del terminador null. Si el tamaño se conoce en bytes, escale `s` según el tamaño del elemento.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Puntero a una matriz de `s` elementos.  Los elementos no tienen que ser válidos en el estado anterior.  En post-State, los elementos hasta el `c`elemento-TH deben ser válidos.  Si el tamaño se conoce en bytes, `s` escale `c` y por el tamaño del elemento o `_bytes_` use la variante, que se define como:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, cada elemento que existe en el búfer hasta `s` en el estado anterior es válido en el estado posterior.  Por ejemplo:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Puntero a una matriz, que es leída y escrita por la función.  Se trata de elementos `s` de tamaño, todos los cuales deben ser válidos en el estado anterior `c` , y los elementos deben ser válidos en post-State.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Puntero a una matriz, que es leída y escrita por la función de elementos de tamaño `s` . Definido como equivalente a:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     En otras palabras, cada elemento que existe en el búfer hasta `s` en el estado anterior es válido en el estado anterior y posterior.

     La `_bytes_` variante proporciona el tamaño en bytes en lugar de los elementos. Úselo solo cuando el tamaño no se puede expresar como elementos.  Por ejemplo, `char` las cadenas usarían `_bytes_` la variante solo si se usa `wchar_t` una función similar.

- `_In_reads_to_ptr_(p)`

     Un puntero a una matriz para la que la `p` expresión  -  `_Curr_` (es decir `p` , `_Curr_`menos) se define mediante el estándar de lenguaje adecuado.  Los elementos anteriores a `p` deben ser válidos en el estado anterior.

- `_In_reads_to_ptr_z_(p)`

     Un puntero a una matriz terminada en null para la que `p` la expresión  -  `_Curr_` (es `p` decir `_Curr_`, menos) se define mediante el estándar de lenguaje adecuado.  Los elementos anteriores a `p` deben ser válidos en el estado anterior.

- `_Out_writes_to_ptr_(p)`

     Un puntero a una matriz para la que la `p` expresión  -  `_Curr_` (es decir `p` , `_Curr_`menos) se define mediante el estándar de lenguaje adecuado.  Los elementos anteriores a `p` no tienen que ser válidos en el estado anterior y deben ser válidos en post-State.

- `_Out_writes_to_ptr_z_(p)`

     Un puntero a una matriz terminada en null para la que `p` la expresión  -  `_Curr_` (es `p` decir `_Curr_`, menos) se define mediante el estándar de lenguaje adecuado.  Los elementos anteriores a `p` no tienen que ser válidos en el estado anterior y deben ser válidos en post-State.

## <a name="optional-pointer-parameters"></a>Parámetros de puntero opcionales

Cuando una anotación de parámetro de puntero `_opt_`incluye, indica que el parámetro puede ser null. De lo contrario, la anotación realiza la misma forma que la versión que `_opt_`no incluye. Esta es una lista de las `_opt_` variantes de las anotaciones de parámetros de puntero:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parámetros de puntero de salida
Los parámetros de puntero de salida requieren una notación especial para eliminar la ambigüedad nula en el parámetro y la ubicación señalada.

**Anotaciones y descripciones**

- `_Outptr_`

   El parámetro no puede ser NULL y en el estado posterior la ubicación señalada no puede ser NULL y debe ser válida.

- `_Outptr_opt_`

   El parámetro puede ser null, pero en el estado posterior la ubicación señalada no puede ser NULL y debe ser válida.

- `_Outptr_result_maybenull_`

   El parámetro no puede ser NULL y en el estado posterior la ubicación señalada puede ser null.

- `_Outptr_opt_result_maybenull_`

   El parámetro puede ser NULL y en el estado posterior la ubicación señalada puede ser null.

  En la tabla siguiente, se insertan subcadenas adicionales en el nombre de la anotación para calificar más el significado de la anotación.  Las distintas subcadenas son `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`y `_to_`.

> [!IMPORTANT]
> Si la interfaz que va a anotar es COM, utilice el formulario COM de estas anotaciones. No use las anotaciones COM con ninguna otra interfaz de tipo.

**Anotaciones y descripciones**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   El puntero devuelto tiene `_Null_terminated_` la anotación.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   El puntero devuelto tiene semántica de com y, por tanto `_On_failure_` , lleva una condición post de que el puntero devuelto es NULL.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   El puntero devuelto apunta a un búfer válido de `s` elementos de tamaño o bytes.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   El puntero devuelto apunta a un búfer de `s` elementos de tamaño o bytes, de los `c` cuales el primero es válido.

  Ciertas convenciones de interfaz suponen que los parámetros de salida se anulan en caso de error.  A excepción del código COM explícito, se prefieren los formularios de la tabla siguiente.  En el caso de código COM, use los formularios COM correspondientes que se enumeran en la sección anterior.

  **Anotaciones y descripciones**

- `_Result_nullonfailure_`

   Modifica otras anotaciones. El resultado se establece en NULL si se produce un error en la función.

- `_Result_zeroonfailure_`

   Modifica otras anotaciones. El resultado se establece en cero si se produce un error en la función.

- `_Outptr_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se ejecuta correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro no opcional.

- `_Outptr_opt_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se ejecuta correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro opcional.

- `_Outref_result_nullonfailure_`

   El puntero devuelto apunta a un búfer válido si la función se ejecuta correctamente, o null si se produce un error en la función. Esta anotación es para un parámetro de referencia.

## <a name="output-reference-parameters"></a>Parámetros de referencia de salida

Un uso común del parámetro de referencia es para los parámetros de salida.  Para los parámetros de referencia de salida simples ( `int&`por`_Out_` ejemplo,) proporciona la semántica correcta.  Sin embargo, cuando el valor de salida es un puntero ( `int *&`por ejemplo), las anotaciones de `_Outptr_ int **` puntero equivalentes como no proporcionan la semántica correcta.  Para expresar de manera concisa la semántica de los parámetros de referencia de salida para los tipos de puntero, use estas anotaciones compuestas:

**Anotaciones y descripciones**

- `_Outref_`

     El resultado debe ser válido en post-State y no puede ser null.

- `_Outref_result_maybenull_`

     El resultado debe ser válido en post-State, pero puede ser null en post-State.

- `_Outref_result_buffer_(s)`

     El resultado debe ser válido en post-State y no puede ser null. Señala a un búfer válido de `s` elementos size.

- `_Outref_result_bytebuffer_(s)`

     El resultado debe ser válido en post-State y no puede ser null. Señala a un búfer válido de `s` tamaño de bytes.

- `_Outref_result_buffer_to_(s, c)`

     El resultado debe ser válido en post-State y no puede ser null. Apunta al búfer de `s` elementos, de los cuales el `c` primero es válido.

- `_Outref_result_bytebuffer_to_(s, c)`

     El resultado debe ser válido en post-State y no puede ser null. Apunta al búfer de `s` bytes del que el primer `c` es válido.

- `_Outref_result_buffer_all_(s)`

     El resultado debe ser válido en post-State y no puede ser null. Apunta a un búfer válido de `s` elementos válidos de tamaño.

- `_Outref_result_bytebuffer_all_(s)`

     El resultado debe ser válido en post-State y no puede ser null. Apunta a un búfer válido `s` de bytes de elementos válidos.

- `_Outref_result_buffer_maybenull_(s)`

     El resultado debe ser válido en post-State, pero puede ser null en post-State. Señala a un búfer válido de `s` elementos size.

- `_Outref_result_bytebuffer_maybenull_(s)`

     El resultado debe ser válido en post-State, pero puede ser null en post-State. Señala a un búfer válido de `s` tamaño de bytes.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     El resultado debe ser válido en post-State, pero puede ser null en post-State. Apunta al búfer de `s` elementos, de los cuales el `c` primero es válido.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     El resultado debe ser válido en post-State, pero puede ser null en post State. Apunta al búfer de `s` bytes del que el primer `c` es válido.

- `_Outref_result_buffer_all_maybenull_(s)`

     El resultado debe ser válido en post-State, pero puede ser null en post State. Apunta a un búfer válido de `s` elementos válidos de tamaño.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     El resultado debe ser válido en post-State, pero puede ser null en post State. Apunta a un búfer válido `s` de bytes de elementos válidos.

## <a name="return-values"></a>Valores devueltos

El valor devuelto de una función es similar `_Out_` a un parámetro, pero se encuentra en un nivel diferente de desreferencia y no tiene que tener en cuenta el concepto del puntero al resultado.  En el caso de las anotaciones siguientes, el valor devuelto es el objeto anotado: un escalar, un puntero a una estructura o un puntero a un búfer. Estas anotaciones tienen la misma semántica que la anotación correspondiente `_Out_` .

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Parámetros de cadena de formato

- `_Printf_format_string_`Indica que el parámetro es una cadena de formato que se utiliza `printf` en una expresión.

     **Ejemplo**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Indica que el parámetro es una cadena de formato que se utiliza `scanf` en una expresión.

     **Ejemplo**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Indica que el parámetro es una cadena de formato que se utiliza `scanf_s` en una expresión.

     **Ejemplo**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Otras anotaciones comunes

**Anotaciones y descripciones**

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     El parámetro, el campo o el resultado está en el intervalo (inclusivo `low` ) `hi`de a.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` que se aplica al objeto anotado junto con las condiciones de estado previo o posterior.

    > [!IMPORTANT]
    > Aunque los nombres contengan "in" y "out", la semántica `_In_` de `_Out_` y **no** se aplica a estas anotaciones.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     El valor anotado es exactamente `expr`.  Equivalente a `_Satisfies_(_Curr_ == expr)` que se aplica al objeto anotado junto con las condiciones de estado previo o posterior.

- `_Struct_size_bytes_(size)`

     Se aplica a una declaración de clase o struct.  Indica que un objeto válido de ese tipo puede ser mayor que el tipo declarado, con el número de bytes que proporciona `size`.  Por ejemplo:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     A continuación, el tamaño de búfer en bytes de `MyStruct *` un parámetro `pM` de tipo se toma para:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Recursos relacionados

[Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Vea también

- [Uso de anotaciones SAL para reducir defectos de código de C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Introducción a SAL](../code-quality/understanding-sal.md)
- [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)
- [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)
- [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)
- [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funciones intrínsecas](../code-quality/intrinsic-functions.md)
- [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)