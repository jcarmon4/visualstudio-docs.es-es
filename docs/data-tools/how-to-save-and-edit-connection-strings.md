---
title: Procedimiento Guardar y editar cadenas de conexión
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1f8300043f9a16c7d92d72c4dcb22e4cd0432a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566981"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Procedimiento Guardar y editar cadenas de conexión
Cadenas de conexión en aplicaciones de Visual Studio se guardan en el archivo de configuración de aplicación (también denominado configuración de la aplicación) o codificadas de forma rígida directamente en la aplicación. Si guarda las cadenas de conexión en el archivo de configuración de la aplicación, se simplifica la tarea de mantenimiento de la aplicación. Si la cadena de conexión debe modificarse, se puede actualizar en el archivo de configuración de la aplicación (cosa que no sucede si hubiera que cambiarla en el código fuente y tener que recompilar la aplicación).

Almacenar información confidencial (como la contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. Las cadenas de conexión almacenadas en el archivo de configuración de la aplicación no están ni cifradas ni protegidas, con lo cual existe la posibilidad de que alguien acceda al archivo y vea el contenido. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.

Si decide no usar la seguridad integrada de Windows y su base de datos requiere un nombre de usuario y una contraseña, estos se pueden omitir en la cadena de conexión, pero la aplicación tendrá que suministrar esta información para poder conectarse a la base de datos. Así, por ejemplo, puede crear un cuadro de diálogo que pida esta información al usuario y que cree la cadena de conexión dinámicamente en tiempo de ejecución. La seguridad puede seguir siendo un problema si alguien intercepta esa información en su recorrido a la base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Para guardar una cadena de conexión en el Asistente para configuración de orígenes de datos
En el **Asistente para configuración de origen de datos**, seleccione la opción para guardar la conexión en el **Guardar cadena de conexión en el archivo de configuración de aplicación** página.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Para guardar la cadena de conexión directamente en la configuración de la aplicación
1. En el **Explorador de soluciones**, haga doble clic en el icono **Mi proyecto** (Visual Basic) o en el icono **Propiedades** (C#) para abrir el **Diseñador de proyectos**.
1. Seleccione la pestaña **Configuración**.
1. Escriba un **Nombre** para la cadena de conexión. Haga referencia a este nombre cuando acceda a la cadena de conexión en el código.
1. Establezca el **Tipo** en (**Cadena de conexión**).
1. Deje el **Ámbito** establecido en **Aplicación**.
1. Escriba la cadena de conexión en el **valor** campo, o haga clic en el **puntos suspensivos** botón (…) en el **valor** campo para abrir el **depropiedadesdeconexión** cuadro de diálogo para crear la cadena de conexión.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Editar las cadenas de conexión almacenadas en la configuración de aplicación
La información de conexión almacenada en la configuración de la aplicación se puede modificar con el **Diseñador de proyectos**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Para modificar una cadena de conexión almacenada en la configuración de la aplicación
1. En el **Explorador de soluciones**, haga doble clic en el icono **Mi proyecto** (Visual Basic) o en el icono **Propiedades** (C#) para abrir el **Diseñador de proyectos**.
1. Seleccione la pestaña **Configuración**.
1. Busque la conexión que desea editar y seleccione el texto en el **valor** campo.
1. Modifique la cadena de conexión en el **valor** campo, o haga clic en el **puntos suspensivos** botón (…) en el **valor** campo para modificar la conexión con el **conexión Propiedades** cuadro de diálogo.

## <a name="edit-connection-strings-for-datasets"></a>Editar las cadenas de conexión para los conjuntos de datos
Puede modificar la información de conexión para cada TableAdapter en un conjunto de datos.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Para editar una cadena de conexión para un TableAdapter en un conjunto de datos
1. En **el Explorador de soluciones**, haga doble clic en el conjunto de datos (**.xsd** archivo) que tenga conexión a la que desea editar.
1. Seleccione el **TableAdapter** o consulta que tenga la conexión que desea editar.
1. En el **propiedades** ventana, expanda el **nodo conexión**.
1. Para modificar rápidamente la cadena de conexión, edite el **ConnectionString** propiedad, o haga clic en la flecha hacia abajo en la **conexión** propiedad y elija **nueva conexión**.

## <a name="security"></a>Seguridad
Almacenar información confidencial (como una contraseña) en la cadena de conexión puede afectar la seguridad de la aplicación. El uso de la seguridad integrada de Windows es una forma más segura de controlar el acceso a una base de datos.
Para más información, consulte [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Vea también

- [Agregar conexiones](../data-tools/add-new-connections.md)