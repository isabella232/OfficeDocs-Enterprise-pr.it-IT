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
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="0e51c-103">Assegnare le licenze di Office 365 agli account utente</span><span class="sxs-lookup"><span data-stu-id="0e51c-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="0e51c-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="0e51c-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="0e51c-105">Per il modello di identità solo cloud, è possibile assegnare le licenze di Office 365 agli account utente quando vengono create, a seconda della modalità di creazione.</span><span class="sxs-lookup"><span data-stu-id="0e51c-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="0e51c-106">Per il modello di identità ibrida, quando gli account utente di servizi di dominio Active Directory (AD DS) vengono sincronizzati per la prima volta, non viene assegnata automaticamente una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="0e51c-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="0e51c-107">In entrambi i casi, è necessario assegnare una licenza agli account utente in modo che gli utenti possano accedere ai servizi di Office 365, ad esempio la posta elettronica e Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="0e51c-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="0e51c-108">È possibile assegnare le licenze agli account utente singolarmente o automaticamente tramite l'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="0e51c-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="0e51c-109">Per assegnare le licenze di Office 365 a singoli account utente, è possibile utilizzare:</span><span class="sxs-lookup"><span data-stu-id="0e51c-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="0e51c-110">L'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0e51c-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="0e51c-111">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="0e51c-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="0e51c-112">Per l'assegnazione di licenze automatiche, vedere [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="0e51c-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e51c-113">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="0e51c-113">Next steps</span></span>

<span data-ttu-id="0e51c-114">Con l'intero set di account utente a cui sono state assegnate le licenze, ora è possibile eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="0e51c-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="0e51c-115">Implementare la sicurezza</span><span class="sxs-lookup"><span data-stu-id="0e51c-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="0e51c-116">Distribuire il software client, ad esempio Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="0e51c-116">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="0e51c-117">Configurare la gestione dei dispositivi mobili in Office 365</span><span class="sxs-lookup"><span data-stu-id="0e51c-117">Set up Mobile Device Management in Office 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="0e51c-118">Configurare servizi e applicazioni</span><span class="sxs-lookup"><span data-stu-id="0e51c-118">Configure services and applications</span></span>](configure-services-and-applications.md)
