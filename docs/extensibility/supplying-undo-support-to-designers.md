---
title: Proporcionar deshacer a diseñadores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e243ccfc92c5e17dd25e6d77dede439daac08761
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747727"
---
# <a name="supply-undo-support-to-designers"></a>Fuente de alimentación de deshacer a diseñadores

Normalmente los diseñadores, editores, al igual que deben admitir las operaciones de deshacer para que los usuarios pueden invertir sus recientes cambios al modificar un elemento de código.

Mayoría de los diseñadores implementada en Visual Studio tiene "deshacer" automáticamente proporcionada por el entorno de soporte técnico.

Implementaciones de diseñador que necesitan para proporcionar compatibilidad con la característica de reversión:

- Proporcionar deshacer la administración mediante la implementación de la clase base abstracta <xref:System.ComponentModel.Design.UndoEngine>

- Admiten la persistencia de suministro y CodeDOM al implementar el <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> clases.

Para obtener más información sobre cómo escribir los diseñadores que utilizan .NET Framework, vea [ampliar compatibilidad en tiempo de diseño](/previous-versions/37899azc(v=vs.140)).

El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona una infraestructura de deshacer de forma predeterminada por:

- Proporcionar las implementaciones de administración a través de deshacer la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> y <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> clases.

- Proporciona persistencia y la compatibilidad de CodeDOM a través de la predeterminada <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> implementaciones.

## <a name="obtain-undo-support-automatically"></a>Obtener soporte para deshacer automáticamente

Cualquier diseñador creado en Visual Studio tiene compatibilidad de la fase de reversión automática y completa if, el diseñador:

- Hace uso de un <xref:System.Windows.Forms.Control> en función de clase para la interfaz de usuario.

- Emplea el sistema de análisis y generación de código estándar basado en CodeDOM para la persistencia y la generación de código.

   Para obtener más información sobre cómo trabajar con la compatibilidad de CodeDOM de Visual Studio, consulte [generación de código fuente dinámico y la compilación](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo usar Deshacer diseñador explícita
 Los diseñadores deben proporcionar su propia administración de deshacer si usan una interfaz gráfica de usuario que se conoce como un adaptador de vista, distinta de la proporcionada por <xref:System.Windows.Forms.Control>.

 Un ejemplo de esto podría crear un producto con una interfaz de diseño gráfica basada en web en lugar de una interfaz gráfica basada en .NET Framework.

 En tales casos, sería necesario registrar este adaptador de vista con el uso de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>y proporciona la administración de la fase de reversión explícita.

 Los diseñadores deben proporcionar CodeDOM y persistencia de soporte técnico si no usan el modelo de generación de código de Visual Studio proporciona en el <xref:System.CodeDom> espacio de nombres.

## <a name="undo-support-features-of-the-designer"></a>Compatibilidad con características del Diseñador de deshacer
 El SDK del entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar soporte técnico que se puede utilizar los diseñadores que no utilizan de deshacer <xref:System.Windows.Forms.Control> en función de las clases para sus interfaces de usuario o el modelo de persistencia y CodeDOM estándar.

 El <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase se deriva de .NET Framework <xref:System.ComponentModel.Design.UndoEngine> clase mediante la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> clase para administrar las operaciones de deshacer.

 Visual Studio proporciona la siguiente funcionalidad para deshacer diseñador:

- Funcionalidad de deshacer vinculada entre varios diseñadores.

- Unidades secundarias dentro de un diseñador pueden interactuar con sus elementos primarios mediante la implementación <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> en <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

El SDK del entorno proporciona compatibilidad con CodeDOM y persistencia proporcionando:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Un <xref:System.ComponentModel.Design.IComponentChangeService> proporcionado por el host de diseño de Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Use las características del SDK de entorno para proporcionar soporte para deshacer

Para obtener soporte para deshacer, un objeto que implementa un diseñador debe crear una instancia e inicializar una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase con válido <xref:System.IServiceProvider> implementación. Esto <xref:System.IServiceProvider> clase debe proporcionar los siguientes servicios:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Los diseñadores que utilizan la serialización de CodeDOM de Visual Studio pueden optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> proporcionado con el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] como su implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   En este caso, el <xref:System.IServiceProvider> clase proporcionada para el <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructor debe devolver este objeto como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> clase.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Los diseñadores que utilizan el valor predeterminado <xref:System.ComponentModel.Design.DesignSurface> proporcionado por el diseño de Visual Studio host se garantiza que tiene una implementación predeterminada de la <xref:System.ComponentModel.Design.IComponentChangeService> clase.

Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo en función de deshacer automáticamente realiza un seguimiento de cambios si:

- Los cambios de propiedad se realizan a través del <xref:System.ComponentModel.TypeDescriptor> objeto.

- <xref:System.ComponentModel.Design.IComponentChangeService> los eventos se generan manualmente cuando se confirma un cambio que se puede deshacer.

- Modificación en el diseñador se creó en el contexto de un <xref:System.ComponentModel.Design.DesignerTransaction>.

- El diseñador decide crear explícitamente mediante cualquiera de unidades de deshacer de la unidad de deshacer estándar proporcionada por una implementación de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o la implementación específica de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, que se deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> y también proporciona un implementación de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Vea también

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Ampliar la compatibilidad en tiempo de diseño](/previous-versions/37899azc(v=vs.140))