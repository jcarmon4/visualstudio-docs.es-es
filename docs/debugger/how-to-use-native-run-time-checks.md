---
title: Procedimiento Utilizar comprobaciones nativas en tiempo de ejecución | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4ccf0fea80ddfcc7db0921512391f5063a8f2dad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846975"
---
# <a name="how-to-use-native-run-time-checks"></a>Procedimiento Uso de comprobaciones nativas en tiempo de ejecución
En Visual C++, puede realizar [runtime_checks](/cpp/preprocessor/runtime-checks) nativas para detectar errores en tiempo de ejecución, tales como:

- Daños en el puntero de la pila

- Saturación de matrices locales

- Daños en la pila

- Dependencias en variables locales sin inicializar

- Pérdida de datos en una asignación a una variable corta.

  Si utiliza **/RTC** con una generación optimizada (**/O**), obtendrá un error del compilador. Si utiliza un pragma `runtime_checks` en una versión optimizada, el pragma no surte ningún efecto.

  Cuando se depura un programa con las comprobaciones en tiempo de ejecución habilitadas, la acción predeterminada es la de que el programa se detenga y se interrumpa su depuración cuando se produzca un error en tiempo de ejecución. Puede cambiar este comportamiento predeterminado para cualquier comprobación en tiempo de ejecución. Para obtener más información, consulte [administrar excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).

  Los siguientes procedimientos describen cómo habilitar las comprobaciones en tiempo de ejecución nativas en una versión de depuración y cómo modificar el comportamiento de la comprobación en tiempo de ejecución nativa.

  Los demás temas de esta sección contienen información sobre:

- [Personalizar las comprobaciones en tiempo de ejecución con la biblioteca en tiempo de ejecución de C](../debugger/native-run-time-checks-customization.md)

- [Utilizar comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Para habilitar las comprobaciones nativas en tiempo de ejecución en una versión de depuración

- Utilice la opción **/RTC** y vincule la versión de depuración de una biblioteca C en tiempo de ejecución (/MDd, por ejemplo).

### <a name="to-modify-native-run-time-check-behavior"></a>Para modificar el comportamiento de las comprobaciones nativas en tiempo de ejecución

- Utilice la directiva pragma `runtime_checks` .

## <a name="see-also"></a>Vea también
- [Depurar en Visual Studio](../debugger/index.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Comprobar errores en tiempo de ejecución](/cpp/c-runtime-library/run-time-error-checking)