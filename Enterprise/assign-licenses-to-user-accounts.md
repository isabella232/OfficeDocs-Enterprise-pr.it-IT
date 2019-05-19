---
title: Assegnare le licenze di Office 365 agli account utente
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
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
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164601"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="b8288-103">Assegnare le licenze di Office 365 agli account utente</span><span class="sxs-lookup"><span data-stu-id="b8288-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="b8288-104">Per il modello di identità solo cloud, è possibile assegnare le licenze di Office 365 agli account utente quando vengono create, a seconda della modalità di creazione.</span><span class="sxs-lookup"><span data-stu-id="b8288-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="b8288-105">Per il modello di identità ibrida, quando gli account utente di servizi di dominio Active Directory (AD DS) vengono sincronizzati per la prima volta, non viene assegnata automaticamente una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b8288-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="b8288-106">In entrambi i casi, è necessario assegnare una licenza agli account utente in modo che gli utenti possano accedere ai servizi di Office 365, ad esempio la posta elettronica e Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="b8288-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="b8288-107">È possibile assegnare le licenze agli account utente singolarmente o automaticamente tramite l'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="b8288-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="b8288-108">Per assegnare le licenze di Office 365 a singoli account utente, è possibile utilizzare:</span><span class="sxs-lookup"><span data-stu-id="b8288-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="b8288-109">Interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b8288-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="b8288-110">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b8288-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="b8288-111">Per l'assegnazione di licenze automatiche, vedere [Group-based Licensing in Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="b8288-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8288-112">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b8288-112">Next steps</span></span>

<span data-ttu-id="b8288-113">Con l'intero set di account utente a cui sono state assegnate le licenze, ora è possibile eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b8288-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="b8288-114">Distribuire il software client, ad esempio Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="b8288-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="b8288-115">Configurare la gestione dei dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="b8288-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="b8288-116">Configurare servizi e applicazioni</span><span class="sxs-lookup"><span data-stu-id="b8288-116">Configure services and applications</span></span>](configure-services-and-applications.md)
