---
title: Assegnare le licenze di Office 365 agli account utente
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Descrive come assegnare le licenze di Office 365 agli account utente, individualmente o in base all'appartenenza a un gruppo.
ms.openlocfilehash: 3ffd51b6b3ab4add900746f14f013a307ca352ad
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843787"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Assegnare le licenze di Office 365 agli account utente

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

Per il modello di identità solo cloud, è possibile assegnare le licenze di Office 365 agli account utente quando vengono create, a seconda della modalità di creazione.

Per il modello di identità ibrida, quando gli account utente di servizi di dominio Active Directory (AD DS) vengono sincronizzati per la prima volta, non viene assegnata automaticamente una licenza di Office 365.

In entrambi i casi, è necessario assegnare una licenza agli account utente in modo che gli utenti possano accedere ai servizi di Office 365, ad esempio la posta elettronica e Microsoft teams.

È possibile assegnare le licenze agli account utente singolarmente o automaticamente tramite l'appartenenza al gruppo.

Per assegnare le licenze di Office 365 a singoli account utente, è possibile utilizzare:

- [L'interfaccia di amministrazione di Microsoft 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [PowerShell di Office 365](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Per l'assegnazione di licenze automatiche, vedere [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Passaggi successivi

Con l'intero set di account utente a cui sono state assegnate le licenze, ora è possibile eseguire le operazioni seguenti:

- [Implementare la sicurezza](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Distribuire il software client, ad esempio Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Configurare la gestione dei dispositivi mobili in Office 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configurare servizi e applicazioni](configure-services-and-applications.md)
