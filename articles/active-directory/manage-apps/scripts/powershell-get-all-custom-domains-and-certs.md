---
title: 'Ejemplo de PowerShell: aplicaciones de proxy de aplicación con dominios personalizados'
description: Ejemplo de PowerShell en el que se enumeran todas las aplicaciones de proxy de aplicación de Azure Active Directory (Azure AD) que usan dominios personalizados e información de certificados.
services: active-directory
author: kenwith
manager: CelesteDG
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.topic: sample
ms.date: 12/05/2019
ms.author: kenwith
ms.reviewer: japere
ms.openlocfilehash: 3e6f300126da0eeffe9d1c752102ab9ded81ff5b
ms.sourcegitcommit: 54d8052c09e847a6565ec978f352769e8955aead
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/18/2020
ms.locfileid: "88506760"
---
# <a name="get-all-application-proxy-apps-using-custom-domains-and-certificate-information"></a>Obtención de todas las aplicaciones de Application Proxy con dominios personalizados e información de certificados

En este script de PowerShell de ejemplo se enumeran todas las aplicaciones de proxy de aplicación de Azure Active Directory (Azure AD) que usan dominios personalizados y la información de certificados asociada a los dominios personalizados.

[!INCLUDE [quickstarts-free-trial-note](../../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [updated-for-az](../../../../includes/updated-for-az.md)]

[!INCLUDE [cloud-shell-try-it.md](../../../../includes/cloud-shell-try-it.md)]

Este ejemplo requiere el [módulo AzureAD V2 PowerShell para Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0) (AzureAD) o la [versión preliminar del módulo AzureAD V2 PowerShell para Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview) (AzureADPreview).

## <a name="sample-script"></a>Script de ejemplo

[!code-azurepowershell[main](~/powershell_scripts/application-proxy/get-all-custom-domains-and-certs.ps1 "Get all Application Proxy apps using custom domains and certificate information")]

## <a name="script-explanation"></a>Explicación del script

| Get-Help | Notas |
|---|---|
|[Get-AzureADServicePrincipal](https://docs.microsoft.com/powershell/module/azuread/get-azureadserviceprincipal?view=azureadps-2.0) | Obtiene una entidad de servicio. |
|[Get-AzureADApplication](https://docs.microsoft.com/powershell/module/azuread/get-azureadapplication?view=azureadps-2.0) | Obtiene una aplicación de Azure AD. |
|[Get-AzureADApplicationProxyApplication](https://docs.microsoft.com/powershell/module/azuread/get-azureadapplicationproxyapplication?view=azureadps-2.0) | Recupera una aplicación configurada para Application Proxy en Azure AD. |

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre el módulo de Azure AD PowerShell, consulte [Información general del módulo de Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0).

Para obtener otros ejemplos de PowerShell para Application Proxy, consulte [Ejemplos de Azure AD PowerShell para Azure AD Application Proxy](../application-proxy-powershell-samples.md).