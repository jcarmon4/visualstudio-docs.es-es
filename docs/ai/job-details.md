---
title: Visualización de trabajos recientes
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: a2970c0086ec18789347eebdea752487be18ce7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548404"
---
# <a name="view-recent-job-performance-and-details"></a>Ver el rendimiento y los detalles de trabajos recientes

Una vez que se envían los trabajos, puede ver la lista de trabajos para ver su estado, duración y mucho más.

1. En el **Explorador de servidores**, expanda el contexto de ejecución específico.
2. Haga doble clic en **Trabajos**.
3. Verá la lista de trabajos enviados a ese contexto de ejecución.
4. Seleccione un **Trabajo** determinado en la lista para ver los detalles.

![Supervisar trabajos](media/job-details/monitor-jobs.png)

> El historial de los trabajos enviados a las máquinas virtuales de Linux se almacena en el directorio /tmp de la máquina virtual. Por tanto, cada vez que se reinicia, se borra el historial de trabajos. Para un registro permanente del historial de trabajos, configure la máquina virtual como un contexto de ejecución en Azure Machine Learning y después envíe el trabajo a Azure Machine Learning (y seleccione la máquina virtual como el contexto de ejecución).