---
title: Entrenar un modelo de TensorFlow localmente
description: Ejecutar un modelo de TensorFlow localmente en herramientas de IA para Visual Studio
keywords: ia, visual studio, tensorflow, local
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 26668247bf993da3eb3f2803abaf9288e566ffee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555468"
---
# <a name="train-a-tensorflow-model-locally"></a>Entrenar un modelo de TensorFlow localmente

En este inicio rápido, se entrenará un modelo de TensorFlow con el conjunto de datos [MNIST](http://yann.lecun.com/exdb/mnist/) localmente en Visual Studio Tools para IA.

La base de datos MNIST tiene un conjunto de entrenamiento de 60 000 ejemplos y un conjunto de pruebas de 10 000 ejemplos de dígitos escritos a mano.

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar, asegúrese de que tener instalado lo siguiente:

### <a name="google-tensorflow"></a>Google TensorFlow

Ejecute el comando siguiente en un terminal:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy y SciPy
Instale [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) y [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Descargar el código de ejemplo
Descargue este [repositorio de GitHub](https://github.com/Microsoft/samples-for-ai) que contiene ejemplos para comenzar a usar el aprendizaje profundo en TensorFlow, CNTK, Theano y mucho más.

## <a name="open-solution-and-train-model"></a>Abrir la solución y entrenar el modelo

- Inicie Visual Studio y seleccione **Archivo > Nuevo > Proyecto o solución**.

- Seleccione la carpeta **Tensorflow Examples** en el repositorio de ejemplos descargado y abra el archivo **TensorflowExamples.sln**.

   ![Abrir el proyecto](media/tensorflow-local/open-project.png)

   ![Abrir la solución](media/tensorflow-local/open-solution.png)

- Busque el proyecto MNIST en el **Explorador de soluciones**, haga clic con el botón derecho y seleccione **Establecer como proyecto de inicio**.

- Haga clic en **Iniciar**.

- La salida se imprime en la consola.

   ![Salida de ejemplo de la consola](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Entrenar un modelo de TensorFlow en la nube](tensorflow-vm.md)