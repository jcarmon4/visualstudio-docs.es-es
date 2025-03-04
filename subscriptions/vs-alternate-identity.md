---
title: Identidades de los suscriptores de Visual Studio
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Cómo agregar una identidad alternativa a la suscripción de Visual Studio para usar Azure DevOps y Azure
ms.openlocfilehash: 5a496af29e520b72e24348a68692efc582fff600
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681229"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades de los suscriptores de Visual Studio
Cuando activa una suscripción de Visual Studio, vinculamos la identidad (o inicio de sesión) que ha usado durante la activación con la suscripción de Visual Studio. De esta manera, podremos reconocerle en el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), en Azure DevOps y en Azure.

En Azure DevOps, comprobamos el estado de la suscripción de Visual Studio cada vez que inicia sesión y le concederemos características automáticamente dentro del ámbito de cada organización de la que sea miembro.
Dado que estas características se incluyen como una ventaja de suscriptor, no supone un gasto extra incluirle como miembro de una organización de Azure DevOps si usa una identidad que está vinculada a su suscripción de Visual Studio.

En Azure, comprobamos el estado de la suscripción de Visual Studio cuando se activa su [crédito mensual de Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que es una ventaja de suscriptor.

En el [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), puede agregar una **identidad alternativa**, además de la identidad que ha usado durante la activación. Se permite agregar una identidad alternativa si se ha usado una cuenta de Microsoft para activar la suscripción. De este modo, puede agregar también una cuenta profesional o educativa (que use para iniciar sesión en Visual Studio, en Office 365 o en la red de la empresa o del centro educativo), lo que le permitirá tener acceso a Azure DevOps tanto a través de su cuenta personal como de su cuenta profesional o educativa.

## <a name="add-an-alternate-account-to-your-subscription"></a>Agregar una cuenta alternativa a la suscripción
La adición de una cuenta alternativa a la suscripción de Visual Studio permite acceder a las ventajas de la suscripción, como Azure DevOps y Azure, con una identidad diferente a la que se asigna la suscripción. En el pasado, esta funcionalidad solo estaba disponible si la suscripción de Visual Studio (VS) se había asignado a una cuenta Microsoft (MSA). Se ha ampliado esta funcionalidad para cuentas profesionales o educativas de Azure Active Directory (Azure AD).

No proporciona una copia de suscripción a la otra cuenta; simplemente ofrece la posibilidad de acceder a las dos ventajas con la cuenta alternativa.

En todas las suscripciones puede agregar una "cuenta profesional o educativa" para usarla con las ventajas que requieren un inicio de sesión (IDE de VS, Azure DevOps y Azure).

### <a name="add-the-alternate-account"></a>Agregar la cuenta alternativa
1. Inicie sesión en el portal de suscriptores de Visual Studio con la cuenta de Microsoft (https://my.visualstudio.com).
2. Haga clic en la pestaña **Suscripciones**.
3. Elija **Agregar cuenta alternativa**.
4. Agregue la cuenta profesional o educativa.
    > [!div class="mx-imgBorder"]
    > ![Agregar cuenta profesional o educativa](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use su cuenta profesional o educativa para iniciar sesión en Azure DevOps (https://{suCuenta}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Usar la cuenta profesional o educativa](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

La cuenta alternativa se agrega a la suscripción de Visual Studio, lo que permite que ambas identidades usen las ventajas de la suscripción que requieren que inicie sesión con la cuenta alternativa (IDE, Azure DevOps y Azure).

## <a name="faq"></a>Preguntas más frecuentes

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>P:  ¿Por qué Azure DevOps no me reconoce como suscriptor de Visual Studio?

R: Azure DevOps debería reconocer la suscripción automáticamente cuando inicie sesión con su identidad principal o alternativa. Si no es así, puede probar a hacer lo siguiente:

* Compruebe que tiene una suscripción activa de Visual Studio que incluya [Azure DevOps](vs-azure-devops.md#eligibility) como ventaja.

* Confirme que está usando un inicio de sesión/identidad que es la identidad principal o alternativa de su suscripción de Visual Studio.

* Vaya al [portal de suscriptores de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) al menos una vez antes de iniciar sesión en Azure DevOps.

Si Azure DevOps sigue sin reconocer la suscripción, póngase en contacto con el [soporte técnico de Azure DevOps](https://azure.microsoft.com/support/devops/).
