---
title: Identità solo cloud di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
description: In questo articolo viene descritto come creare utenti e gruppi quando la sottoscrizione di Office 365 utilizza identità solo cloud.
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072278"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="bd28a-103">Identità solo cloud di Office 365</span><span class="sxs-lookup"><span data-stu-id="bd28a-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="bd28a-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="bd28a-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="bd28a-105">Con l'identità solo cloud, tutti gli utenti, i gruppi e i contatti vengono archiviati nel tenant di Azure Active Directory (Azure AD) dell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="bd28a-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="bd28a-106">Ecco i componenti di base dell'identità solo cloud.</span><span class="sxs-lookup"><span data-stu-id="bd28a-106">Here are the basic components of cloud-only identity.</span></span>
 
![I componenti di base dell'identità solo cloud](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="bd28a-108">Gli utenti e i loro account utente nelle organizzazioni possono essere categorizzati in vari modi.</span><span class="sxs-lookup"><span data-stu-id="bd28a-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="bd28a-109">Ad esempio, alcuni sono dipendenti e hanno uno stato permanente.</span><span class="sxs-lookup"><span data-stu-id="bd28a-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="bd28a-110">Alcuni sono fornitori, appaltatori o partner che hanno uno stato temporaneo.</span><span class="sxs-lookup"><span data-stu-id="bd28a-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="bd28a-111">Alcuni sono utenti esterni che non dispongono di account utente, ma è comunque necessario concedere l'accesso a servizi e risorse specifici per supportare l'interazione e la collaborazione.</span><span class="sxs-lookup"><span data-stu-id="bd28a-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="bd28a-112">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="bd28a-112">For example:</span></span>

- <span data-ttu-id="bd28a-113">Gli account tenant rappresentano gli utenti all'interno dell'organizzazione con la licenza per i servizi cloud</span><span class="sxs-lookup"><span data-stu-id="bd28a-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="bd28a-114">Gli account business to business (B2B) rappresentano gli utenti esterni all'organizzazione che invitano a partecipare alla collaborazione per fare il punto sui tipi di utenti dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="bd28a-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="bd28a-115">Quali sono i raggruppamenti?</span><span class="sxs-lookup"><span data-stu-id="bd28a-115">What are the groupings?</span></span> <span data-ttu-id="bd28a-116">Ad esempio, è possibile raggruppare gli utenti in base alla funzione o allo scopo di alto livello dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="bd28a-116">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="bd28a-p104">Inoltre, alcuni servizi cloud possono essere condivisi al di fuori dell'organizzazione senza alcun account utente. È necessario identificare anche questi gruppi di utenti.</span><span class="sxs-lookup"><span data-stu-id="bd28a-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="bd28a-119">È possibile utilizzare i gruppi in Azure AD per diversi scopi che semplificano la gestione dell'ambiente cloud.</span><span class="sxs-lookup"><span data-stu-id="bd28a-119">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="bd28a-120">Ad esempio, con i gruppi di Azure AD, è possibile:</span><span class="sxs-lookup"><span data-stu-id="bd28a-120">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="bd28a-121">Utilizzo delle licenze basate su gruppo per assegnare le licenze per Office 365 agli account utente automaticamente non appena vengono aggiunti.</span><span class="sxs-lookup"><span data-stu-id="bd28a-121">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="bd28a-122">Aggiungere account utente a gruppi specifici in modo dinamico in base agli attributi dell'account utente, come per esempio il reparto.</span><span class="sxs-lookup"><span data-stu-id="bd28a-122">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="bd28a-123">Effettuare automaticamente il provisioning degli utenti per le applicazioni Software as a Service (SaaS) e proteggere l'accesso a tali applicazioni con l'autenticazione a più fattori e altre regole di accesso condizionale.</span><span class="sxs-lookup"><span data-stu-id="bd28a-123">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="bd28a-124">Provisioning delle autorizzazioni e dei livelli di accesso per i siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bd28a-124">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="bd28a-125">È possibile creare nuovi ***utenti*** con:</span><span class="sxs-lookup"><span data-stu-id="bd28a-125">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="bd28a-126">L'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bd28a-126">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="bd28a-127">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="bd28a-127">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="bd28a-128">È possibile creare nuovi ***gruppi*** con:</span><span class="sxs-lookup"><span data-stu-id="bd28a-128">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="bd28a-129">L'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bd28a-129">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="bd28a-130">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="bd28a-130">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="bd28a-131">Passaggio successivo per le identità solo cloud</span><span class="sxs-lookup"><span data-stu-id="bd28a-131">Next step for cloud-only identities</span></span>

<span data-ttu-id="bd28a-132">[Assegnare licenze agli account utente](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="bd28a-132">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md)</span></span>
