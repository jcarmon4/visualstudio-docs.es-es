---
title: Implementar código personalizado en el repositorio directivas de análisis de código administrado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f0b22eabc4df4b6ce7e8596f0c6546cb3a4c61c8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696656"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementar directivas de protección de análisis de código personalizadas para el código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un directiva de protección especifica un conjunto de reglas que los miembros de un proyecto de equipo deben ejecutar en el código fuente antes de que el análisis de código está protegido al control de versiones. Microsoft proporciona un conjunto de estándar *conjuntos de reglas* ese análisis de código de grupo de reglas en las áreas funcionales. *Conjuntos de reglas de directiva de protección personalizadas* especificar un conjunto de reglas de análisis de código que son específicos de un proyecto de equipo. Un conjunto de reglas se almacena en un archivo .ruleset.  
  
 Las directivas de protección se establece en el nivel de proyecto de equipo y especificadas por la ubicación del archivo .ruleset en el árbol de control de versiones. No hay ninguna restricción en la ubicación del control de versión del conjunto de reglas personalizado de la directiva de equipo.  
  
 Análisis de código está configurado para los proyectos de código individuales en la ventana Propiedades para cada proyecto. Una regla personalizada establecido para un proyecto de código especificada por la ubicación física del archivo .ruleset en el equipo local. Cuando se especifica un archivo .ruleset que se encuentra en la misma unidad que el proyecto de código, Visual Studio usa una ruta de acceso relativa al archivo en la configuración del proyecto.  
  
 Es una práctica sugerida para la creación de un conjunto de reglas personalizadas de proyecto de equipo almacenar el archivo .ruleset de directiva de protección en una carpeta especial que no forma parte de cualquier proyecto de código. Si almacena el archivo en una carpeta dedicada, puede aplicar permisos restringirán quién pueden editar el archivo de reglas y se puede mover fácilmente la estructura de directorios contiene el proyecto a otro directorio o equipo.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Crear el conjunto de reglas personalizado en el repositorio del proyecto de equipo  
 Para crear una regla personalizada establecido para un proyecto de equipo, primero se crea una carpeta especial para la regla de directiva de protección se establece **Explorador de Control de código fuente**. A continuación, cree el archivo de conjunto de reglas y agregue el archivo al control de versiones. Por último, especifique el conjunto de reglas como la directiva de comprobación del análisis de código del proyecto de equipo.  
  
> [!NOTE]
> Para crear una carpeta en un proyecto de equipo, primero debe asignar la raíz del proyecto de equipo a una ubicación en el equipo local. Para obtener más información, consulte [crear y trabajar con áreas de trabajo (antiguo)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Para crear la carpeta de control de versiones para el conjunto de reglas de directiva de protección  
  
1. En [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], expanda el nodo de proyecto de equipo y, a continuación, haga clic en **Control de código fuente**.  
  
2. En el **carpetas** panel, haga clic en el proyecto de equipo y, a continuación, haga clic en **nueva carpeta**.  
  
3. En el panel de Control de código fuente principal, haga clic en **nueva carpeta**, haga clic en **cambiar el nombre**y escriba un nombre para la regla del conjunto de carpetas.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Para crear el conjunto de reglas de directiva de protección  
  
1. En el **archivo** menú, elija **New**y, a continuación, haga clic en **archivo**.  
  
2. En el **categorías** lista, haga clic en **General**.  
  
3. En el **plantillas** lista, haga doble clic en **conjunto de reglas de análisis de código**.  
  
4. Especificar las reglas que se va a incluir en el conjunto de reglas y, a continuación, guarde el archivo de conjunto de regla en la carpeta de conjunto de reglas que ha creado.  
  
     Para obtener más información, consulte [creación de conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Para agregar la regla de conjunto de archivos al control de versiones  
  
1. En **Explorador de Control de código fuente**, haga clic en la nueva carpeta y, a continuación, haga clic en **agregar elementos a la carpeta**.  
  
     Para obtener más información, consulte [usar control de versiones](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2. Haga clic en la regla establece el archivo que ha creado y, a continuación, haga clic en **finalizar**.  
  
     El archivo se agrega al control de código fuente y desprotegido.  
  
3. En el **Explorador de Control de código fuente** ventana de detalles, haga clic en el nombre de archivo y, a continuación, haga clic en **proteger cambios pendientes**.  
  
4. En el **en el repositorio** cuadro de diálogo, tiene la opción para agregar un comentario y, a continuación, haga clic en **proteger**.  
  
    > [!NOTE]
    > Si ya ha configurado una directiva de protección de análisis de código para el proyecto de equipo y ha seleccionado la **exigir la protección para que solo contenga los archivos que forman parte de la solución actual**, se desencadenará una advertencia de error de directiva. En el cuadro de diálogo de error de la directiva, seleccione **invalidar el error de directiva y continuar la protección**. Agregue un comentario necesario y, a continuación, haga clic en **Aceptar**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Para especificar la regla de conjunto de archivos como la directiva de protección  
  
1. En el **equipo** menú, elija **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.  
  
2. Haga clic en **directiva de protección**y, a continuación, haga clic en **agregar**.  
  
3. En el **directiva de protección** lista, haga doble clic en **análisis de código**y asegúrese de que el **aplicar análisis de código para código administrado** casilla está activada.  
  
4. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Seleccionar conjunto de reglas de Control de código fuente >** .  
  
5. Escriba la ruta de acceso del archivo de conjunto de regla de directiva de protección en el control de versiones.  
  
     La ruta de acceso debe ajustarse a la sintaxis siguiente:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    > Puede copiar la ruta de acceso mediante uno de los siguientes procedimientos en **Explorador de Control de código fuente**:  
  
    - En el **carpetas** panel, haga clic en la carpeta que contiene el archivo de conjunto de reglas. Copie la ruta de acceso de control de versiones de la carpeta que aparece en el **origen** cuadro y escriba el nombre del archivo de conjunto de reglas manualmente.  
  
    - En la ventana de detalles, haga clic en el archivo de conjunto de reglas y, a continuación, haga clic en **propiedades**. En el **General** pestaña, copie el valor en **nombre del servidor**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Sincronizando el conjunto de reglas de directiva de protección de los proyectos de código  
 Especifique una regla de directiva de protección del proyecto de equipo se establece como el conjunto de reglas de análisis de código de una configuración de proyecto de código en el cuadro de diálogo Propiedades del proyecto de código. Si el conjunto de reglas se encuentra en la misma unidad que el proyecto de código, una ruta de acceso relativa se utiliza para especificar el conjunto de reglas cuando se selecciona la ruta de acceso desde el cuadro de diálogo de archivo. Estructuras de control de la ruta de acceso relativa permite que la configuración de propiedades del proyecto que sean portables a otros equipos que usan la versión local similar.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Para especificar una regla de proyecto de equipo establecido como el conjunto de reglas de un proyecto de código  
  
1. Si es necesario, recuperar la carpeta de conjunto de reglas de directiva de protección y el archivo de control de versiones.  
  
     Puede realizar este paso en **Explorador de Control de código fuente** haciendo la regla establece carpeta y, a continuación, haga clic en **obtener última versión**.  
  
2. En **el Explorador de soluciones**, haga clic en el proyecto de código y, a continuación, haga clic en **propiedades**.  
  
3. **Haga clic en el análisis de código**.  
  
4. Si es necesario, haga clic en las opciones adecuadas en el **configuración** y **plataforma** enumera.  
  
5. Para ejecutar análisis de código cada vez que se compila el proyecto de código con la configuración especificada, seleccione el **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** casilla de verificación.  
  
6. Para omitir el código en componentes de otras empresas, seleccione el **Suprimir resultados del código generado** casilla de verificación.  
  
7. En el **ejecutar este conjunto de reglas** lista, haga clic en  **\<Examinar... >** .  
  
8. Especifique la versión local del archivo de conjunto de regla de directiva de protección.
