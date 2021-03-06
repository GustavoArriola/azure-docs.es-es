---
title: 'Inicio rápido: Modificación de cuentas de aplicaciones de la plataforma de identidad de Microsoft | Azure'
description: En este inicio rápido, va a configurar una aplicación registrada en la plataforma de identidad de Microsoft para cambiar los usuarios o las cuentas que pueden acceder a la aplicación.
services: active-directory
author: rwike77
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: quickstart
ms.workload: identity
ms.date: 05/08/2019
ms.author: ryanwi
ms.custom: aaddev
ms.reviewer: aragra, lenalepa, sureshja
ms.openlocfilehash: d143bde9c22bc726f00b5c209d1b7fbc131905b0
ms.sourcegitcommit: 32c521a2ef396d121e71ba682e098092ac673b30
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2020
ms.locfileid: "91258020"
---
# <a name="quickstart-modify-the-accounts-supported-by-an-application"></a>Inicio rápido: Modificación de las cuentas compatibles con una aplicación

Al registrar una aplicación en la plataforma de identidad de Microsoft, tal vez quiera que solo tengan acceso a la aplicación los usuarios de la organización. Como alternativa, también puede desear que la aplicación sea accesible para los usuarios de organizaciones externas, así como para los usuarios que no formen necesariamente parte de una organización (cuentas personales).

En esta guía de inicio rápido, aprenderá a modificar la configuración de la aplicación para cambiar quién o qué cuentas pueden acceder a la aplicación.

## <a name="prerequisites"></a>Prerrequisitos

* Finalización de [Inicio rápido: Registro de una aplicación en la plataforma de identidad de Microsoft](quickstart-register-app.md)

## <a name="sign-in-to-the-azure-portal-and-select-the-app"></a>Inicio de sesión en Azure Portal y selección de la aplicación

Antes de configurar la aplicación, siga estos pasos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con una cuenta personal, profesional o educativa de Microsoft.
1. Si la cuenta proporciona acceso a más de un inquilino, haga clic en la cuenta en la esquina superior derecha y establezca la sesión del portal en el inquilino de Azure AD deseado.
1. En el panel de navegación izquierdo, seleccione el servicio **Azure Active Directory** y, después, seleccione **Registros de aplicaciones**.
1. Busque y seleccione la aplicación que desea configurar. Cuando haya seleccionado la aplicación, verá la página **Introducción** de la aplicación o la de registro principal.
1. Siga los pasos para [cambiar el registro de la aplicación para admitir distintas cuentas](#change-the-application-registration-to-support-different-accounts).
1. Si tiene una aplicación de página única, [habilite la concesión implícita de OAuth 2.0](#enable-oauth-20-implicit-grant-for-single-page-applications).

## <a name="change-the-application-registration-to-support-different-accounts"></a>Cambio del registro de la aplicación para admitir distintas cuentas

Si está escribiendo una aplicación que quiere poner a disposición de clientes o asociados externos a la organización, debe actualizar la definición de la aplicación en Azure Portal.

> [!IMPORTANT]
> Azure AD necesita que el URI del identificador de las aplicaciones multiinquilino sea único globalmente. El URI de id. de aplicación es una de las maneras en que una aplicación se identifica en los mensajes de protocolo. Cuando la aplicación es de un solo inquilino, es suficiente con que el URI de identificador de aplicación sea único en dicho inquilino. En el caso de una aplicación multiempresa, debe ser único a nivel global de forma que Azure AD pueda encontrar la aplicación entre todos los inquilinos. El carácter globalmente único viene impuesto por la necesidad de que el URI de id. de aplicación tenga un nombre de host que coincida con un dominio comprobado del inquilino de Azure AD. Por ejemplo, si el nombre del inquilino es contoso.onmicrosoft.com, un identificador URI de identificador de aplicación válido sería `https://contoso.onmicrosoft.com/myapp`. Si el inquilino tiene el dominio comprobado contoso.com, un URI del identificador de aplicación válido también sería `https://contoso.com/myapp`. Si el URI de id. de aplicación no sigue este patrón, la configuración de una aplicación como multiinquilino dará error.

### <a name="to-change-who-can-access-your-application"></a>Para cambiar quién puede acceder a la aplicación

1. Desde la página **Introducción** de la aplicación, seleccione la sección **Autenticación** y cambie el valor seleccionado en **Tipos de cuentas compatibles**.
    * Seleccione **Accounts in this directory only** (Solo las cuentas de este directorio) si va a crear una aplicación de línea de negocio (LOB). Esta opción no está disponible si la aplicación no está registrada en un directorio.
    * Seleccione **Cuentas en cualquier directorio organizativo** si desea tener como destino todos los clientes de negocios y del sector educativo.
    * Seleccione **Cuentas en cualquier directorio organizativo y cuentas Microsoft personales** para establecer como destino el mayor conjunto posible de clientes.
1. Seleccione **Guardar**.

## <a name="enable-oauth-20-implicit-grant-for-single-page-applications"></a>Habilitación de la concesión implícita de OAuth 2.0 en aplicaciones de página única

Las aplicaciones de página única (SPA) normalmente tienen una estructura con un front-end de JavaScript que se ejecuta en el explorador, que llama al back-end de la API web de la aplicación para llevar a cabo la lógica de negocios. Para las SPA hospedadas en Azure AD, se usa la concesión implícita de OAuth 2.0 para autenticar al usuario en Azure AD y obtener un token que puede usar para proteger las llamadas desde el cliente JavaScript de la aplicación hasta la API web de back-end.

Después de que el usuario haya dado su consentimiento, este mismo protocolo de autenticación se puede usar para obtener tokens para proteger las llamadas entre el cliente y otros recursos de API web configurados para la aplicación. Para saber más sobre la concesión de autorización implícita y ayudarle a decidir si es adecuada para el escenario de su aplicación, consulte el flujo de concesión implícita de OAuth 2.0 en Azure AD [v1.0](../azuread-dev/v1-oauth2-implicit-grant-flow.md) y [v2.0](v2-oauth2-implicit-grant-flow.md).

De forma predeterminada, la concesión implícita de OAuth 2.0 está deshabilitada para las aplicaciones. Para habilitar la concesión implícita de OAuth 2.0 para la aplicación, siga los pasos descritos a continuación.

### <a name="to-enable-oauth-20-implicit-grant"></a>Para habilitar la concesión implícita de OAuth 2.0

1. En el panel de navegación izquierdo, seleccione el servicio **Azure Active Directory** y, después, seleccione **Registros de aplicaciones**.
1. Busque y seleccione la aplicación que desea configurar. Cuando haya seleccionado la aplicación, verá la página **Introducción** de la aplicación o la de registro principal.
1. Desde la página **Introducción** de la aplicación, seleccione la sección **Autenticación**.
1. En **Configuración avanzada**, busque la sección **Concesión implícita**.
1. Seleccione **Tokens de identificador**, **Tokens de acceso** o ambos.
1. Seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Directrices de personalización de marca para aplicaciones](howto-add-branding-in-azure-ad-apps.md)
