---
title: Procedimiento Usar asistentes con plantillas de proyectos
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3831cbc484fde7c61dbe1baf5ecd9ab07556a7f5
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342413"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedimiento Usar a asistentes con plantillas de proyecto

Visual Studio proporciona la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> que, cuando se implementa, permite ejecutar código personalizado cuando un usuario crea un proyecto a partir de una plantilla.

Personalización de la plantilla de proyecto puede usarse para mostrar la interfaz de usuario personalizada que recopila la entrada del usuario para personalizar la plantilla, agregue archivos adicionales a la plantilla, o cualquier otra acción que se permiten en un proyecto.

El <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> se denominan métodos de interfaz en distintos momentos mientras se crea el proyecto, tan pronto como un usuario hace clic **Aceptar** en el **nuevo proyecto** cuadro de diálogo. Cada método de la interfaz se denomina de modo que describa el punto en el que se llama. Por ejemplo, Visual Studio llama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> inmediatamente cuando empieza a crear el proyecto, lo que un buen lugar para escribir código personalizado para recopilar entradas del usuario.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Crear un proyecto de plantilla de proyecto con un proyecto VSIX

Comenzar a crear una plantilla personalizada con el proyecto de plantilla de proyecto, que forma parte del SDK de Visual Studio. En este procedimiento, utilizaremos un C# proyecto de plantilla de proyecto, pero también hay un proyecto de plantilla de proyecto de Visual Basic. A continuación, un proyecto de VSIX se agregue a la solución que contiene el proyecto de plantilla de proyecto.

1. Crear un C# proyecto de plantilla de proyecto (en Visual Studio, seleccione **archivo** > **New** > **proyecto** y busque "plantilla de proyecto" ). Asígnele el nombre **MyProjectTemplate**.

   > [!NOTE]
   > Se le pedirá que instale el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

2. Agregue un nuevo proyecto VSIX en la misma solución que el proyecto de plantilla de proyecto (en **el Explorador de soluciones**, seleccione el nodo de la solución, contextual y seleccione **agregar** > **nuevo proyecto**  y busque "vsix"). Asígnele el nombre **MyProjectWizard.**

3. Establezca el proyecto VSIX como proyecto de inicio. En **el Explorador de soluciones**, seleccione el nodo del proyecto VSIX, contextual y seleccione **establecer como proyecto de inicio**.

4. Agregue el proyecto de plantilla como un recurso del proyecto VSIX. En **el Explorador de soluciones**, en el nodo del proyecto VSIX, busque el *source.extension.vsixmanifest* archivo. Haga doble clic en él para abrirlo en el editor de manifiestos.

5. En el editor de manifiestos, seleccione el **activos** ficha en el lado izquierdo de la ventana.

6. En el **activos** ficha, seleccione **New**. En el **Agregar nuevo activo** ventana para el campo de tipo, seleccione **Microsoft.VisualStudio.ProjectTemplate**. En el **origen** campos, seleccione **un proyecto de la solución actual**. En el **proyecto** campos, seleccione **MyProjectTemplate**. A continuación, haga clic en **Aceptar**.

7. Compile la solución y comience la depuración. Se muestra una segunda instancia de Visual Studio. (Esto puede tardar unos minutos).

8. En la segunda instancia de Visual Studio, intente crear un nuevo proyecto con la nueva plantilla (**archivo** > **New** > **proyecto**, busque " MyProject"). Debería aparecer el nuevo proyecto con una clase denominada **Class1**. Ahora ha creado una plantilla de proyecto personalizado. Detener ahora la depuración.

## <a name="create-a-custom-template-wizard"></a>Crear a un asistente de plantilla personalizada

Este procedimiento muestra cómo crear a un asistente personalizado que abre un formulario de Windows antes de crea el proyecto. El formulario permite a los usuarios agregar un valor de parámetro personalizado que se agrega al código fuente durante la creación del proyecto.

1. Configurar el proyecto VSIX para que pueda crear un ensamblado.

2. En **el Explorador de soluciones**, seleccione el nodo del proyecto VSIX. A continuación **el Explorador de soluciones**, debería ver el **propiedades** ventana. Si no lo hace, seleccione **vista** > **ventana propiedades**, o bien presione **F4**. En el **propiedades** ventana, seleccione los siguientes campos a `true`:

   - **IncludeAssemblyInVSIXContainer**

   - **IncludeDebugSymbolsInVSIXContainer**

   - **IncludeDebugSymbolsInLocalVSIXDeployment**

3. Agregue el ensamblado como un recurso para el proyecto VSIX. Abra el *source.extension.vsixmanifest* de archivo y seleccione el **activos** ficha. En el **Agregar nuevo activo** ventana, para **tipo** seleccione **Microsoft.VisualStudio.Assembly**, para **origen** seleccione **A proyecto de la solución actual**y para **proyecto** seleccione **MyProjectWizard**.

4. Agregue las siguientes referencias al proyecto VSIX. (En **el Explorador de soluciones**, bajo el nodo de proyecto VSIX, seleccione **referencias**, con el botón secundario y seleccione **Agregar referencia**.) En el **Agregar referencia** cuadro de diálogo, en el **Framework** pestaña, busque el **System.Windows Forms** ensamblado y selecciónelo. Además, busque y seleccione el **sistema** y **System.Drawing** ensamblados. Ahora seleccione el **extensiones** ficha. Buscar el **EnvDTE** ensamblado y selecciónelo. También encontrará el **Microsoft.VisualStudio.TemplateWizardInterface** ensamblado y selecciónelo. Haga clic en **Aceptar**.

5. Agregue una clase para la implementación del Asistente para el proyecto VSIX. (En **el Explorador de soluciones**, haga clic en el nodo del proyecto VSIX y seleccione **agregar**, a continuación, **nuevo elemento**, a continuación, **clase**.) Nombre de la clase **WizardImplementation**.

6. Reemplace el código en el *WizardImplementationClass.cs* archivo con el código siguiente:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    El **UserInputForm** al que hace referencia en este código se implementarán más adelante.

    La clase `WizardImplementation` contiene las implementaciones de método para cada miembro de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. En este ejemplo, solo el método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> realiza una tarea. Los demás métodos no hacen nada o devuelven `true`.

    El método <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> acepta cuatro parámetros:

   - Un parámetro <xref:System.Object> que se puede convertir en el objeto <xref:EnvDTE._DTE> raíz, para permitirle personalizar el proyecto.

   - Un parámetro <xref:System.Collections.Generic.Dictionary%602> que contiene una colección de todos los parámetros predefinidos en la plantilla. Para obtener más información sobre los parámetros de plantilla, consulte [parámetros de plantilla](../ide/template-parameters.md).

   - Un parámetro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> que contiene información sobre qué tipo de plantilla se utiliza.

   - Un <xref:System.Object> matriz que contiene un conjunto de parámetros que se pasa al asistente por Visual Studio.

     Este ejemplo agrega un valor de parámetro del formulario de entrada de datos al parámetro <xref:System.Collections.Generic.Dictionary%602>. Cada instancia del parámetro `$custommessage$` del proyecto se reemplazará por el texto escrito por el usuario.

7. Ahora cree la **UserInputForm**. En el *WizardImplementation.cs* , agregue el código siguiente después del final de la `WizardImplementation` clase.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    El formulario de datos proporcionados por el usuario proporciona un formulario simple para escribir un parámetro personalizado. El formulario contiene un cuadro de texto denominado `textBox1` y un botón denominado `button1`. Cuando se hace clic en el botón, el texto del cuadro de texto se almacena en el parámetro `customMessage`.

## <a name="connect-the-wizard-to-the-custom-template"></a>Conecte al Asistente para la plantilla personalizada

En el orden de la plantilla de proyecto personalizadas utilizar al Asistente personalizado, deberá firmar el ensamblado del asistente y agregue algunas líneas a la plantilla de proyecto personalizadas para que lo sepan dónde encontrar la implementación del asistente cuando se crea un nuevo proyecto.

1. Firmar el ensamblado. En el **el Explorador de soluciones**, seleccione el proyecto VSIX, contextual y seleccione **las propiedades del proyecto**.

2. En el **las propiedades del proyecto** ventana, seleccione el **firma** ficha en el **firma** pestaña **firmar el ensamblado**. En el **elegir un archivo de clave de nombre seguro** campos, seleccione  **\<New >** . En el **crear clave de nombre seguro** ventana, en el **nombre de archivo de clave** , escriba **key.snk**. Desactive el **proteger mi archivo de clave con una contraseña** campo.

3. En el **el Explorador de soluciones**, seleccione el proyecto VSIX y busque el **propiedades** ventana.

4. Establecer el **copiar el directorio de salida a la salida de compilación** campo **true**. Esto permite que el ensamblado que se copiará en el directorio de salida cuando se vuelve a generar la solución. Aún se encuentra en el `.vsix` archivo. Debe ver el ensamblado para averiguar su clave de firma.

5. Recompilar la solución.

6. Ahora puede encontrar el archivo key.snk en el directorio del proyecto MyProjectWizard ( *\<su ubicación de disco > \MyProjectTemplate\MyProjectWizard\key.snk*). Copia el *key.snk* archivo.

7. Vaya al directorio de resultados y encontrar el ensamblado ( *\<su ubicación de disco > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Pegar la *key.snk* archivo aquí. (Esto no es absolutamente necesario, pero lo será más fácil los pasos siguientes).

8. Abra una ventana de comandos y cambie al directorio en el que se ha creado el ensamblado.

9. Buscar el *sn.exe* herramienta de firma. Por ejemplo, en un sistema operativo de 64 bits de Windows 10, una ruta de acceso típica sería la siguiente:

     *Herramientas de C:\Program archivos (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1*

     Si no se encuentra la herramienta, intente ejecutar **donde /R. sn.exe** en la ventana de comandos. Tome nota de la ruta de acceso.

10. Extraiga la clave pública desde el *key.snk* archivo. En la ventana de comandos, escriba

     **\<ubicación de sn.exe > \sn.exe -p key.snk outfile.key.**

     No se olvide de delimitar la ruta de acceso de *sn.exe* entre comillas si hay espacios en los nombres de directorio.

11. Obtener la clave pública token desde el archivo externo:

     **\<ubicación de sn.exe > \sn.exe -t outfile.key.**

     De nuevo, no olvide las comillas. Debería ver una línea en la salida similar al siguiente

     **Token de clave pública es \<token >**

     Tome nota de este valor.

12. Agregar la referencia para el Asistente personalizado para el *.vstemplate* archivo de la plantilla de proyecto. En el **el Explorador de soluciones**, busque el archivo denominado *MyProjectTemplate.vstemplate*y ábralo. Después de finalizar la \<TemplateContent > sección, agregue la siguiente sección:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Donde **MyProjectWizard** es el nombre del ensamblado, y **token** es el token que copió en el paso anterior.

13. Guarde todos los archivos en el proyecto y volver a generar.

## <a name="add-the-custom-parameter-to-the-template"></a>Agregue el parámetro personalizado a la plantilla

En este ejemplo, el proyecto que se utiliza como plantilla muestra el mensaje especificado en el formulario de entrada de usuario del Asistente personalizado.

1. En el **el Explorador de soluciones**, vaya a la **MyProjectTemplate** del proyecto y abra *Class1.cs*.

2. En el método `Main` de la aplicación, agregue la siguiente línea de código.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    El parámetro `$custommessage$` se reemplaza por el texto escrito en el formulario de datos proporcionados por el usuario cuando se crea un proyecto a partir de la plantilla.

Este es el archivo de código completo antes de se ha exportado a una plantilla.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Utilizar al Asistente personalizado

Ahora puede crear un proyecto a partir de la plantilla y utilizar el asistente personalizado.

1. Recompile la solución e iniciar la depuración. Aparece una segunda instancia de Visual Studio.

2. Cree un nuevo proyecto MyProjectTemplate. (**Archivo** > **nueva** > **proyecto**).

3. En el **nuevo proyecto** cuadro de diálogo, busque "myproject" buscar la plantilla, escriba un nombre y haga clic en **Aceptar**.

     Se abrirá el formulario de datos proporcionados por el usuario.

4. Escriba un valor para el parámetro personalizado y haga clic en el botón.

     El formulario de datos proporcionados por el usuario del asistente se cierra y se crea un proyecto a partir de la plantilla.

5. En **el Explorador de soluciones**, haga clic en el archivo de código fuente y haga clic en **ver código**.

     Observe que `$custommessage$` se ha reemplazado con el texto escrito en el formulario de datos proporcionados por el usuario del asistente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [WizardExtension (elemento) (plantillas de Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Paquetes NuGet en plantillas de Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
