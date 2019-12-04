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
ms.openlocfilehash: 6815c89821216416379a27eb525e66b90b828ea8
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813414"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="f0c93-103">Identità solo cloud di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0c93-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="f0c93-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="f0c93-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="f0c93-105">Con l'identità solo cloud, tutti gli utenti, i gruppi e i contatti vengono archiviati nel tenant di Azure Active Directory (Azure AD) dell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="f0c93-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="f0c93-106">Ecco i componenti di base dell'identità solo cloud.</span><span class="sxs-lookup"><span data-stu-id="f0c93-106">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="f0c93-107">Gli utenti e i loro account utente nelle organizzazioni possono essere categorizzati in vari modi.</span><span class="sxs-lookup"><span data-stu-id="f0c93-107">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="f0c93-108">Ad esempio, alcuni sono dipendenti e hanno uno stato permanente.</span><span class="sxs-lookup"><span data-stu-id="f0c93-108">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="f0c93-109">Alcuni sono fornitori, appaltatori o partner che hanno uno stato temporaneo.</span><span class="sxs-lookup"><span data-stu-id="f0c93-109">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="f0c93-110">Alcuni sono utenti esterni che non dispongono di account utente, ma è comunque necessario concedere l'accesso a servizi e risorse specifici per supportare l'interazione e la collaborazione.</span><span class="sxs-lookup"><span data-stu-id="f0c93-110">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="f0c93-111">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f0c93-111">For example:</span></span>

- <span data-ttu-id="f0c93-112">Gli account tenant rappresentano gli utenti all'interno dell'organizzazione con la licenza per i servizi cloud</span><span class="sxs-lookup"><span data-stu-id="f0c93-112">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="f0c93-113">Gli account business to business (B2B) rappresentano gli utenti esterni all'organizzazione che invitano a partecipare alla collaborazione per fare il punto sui tipi di utenti dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f0c93-113">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="f0c93-114">Quali sono i raggruppamenti?</span><span class="sxs-lookup"><span data-stu-id="f0c93-114">What are the groupings?</span></span> <span data-ttu-id="f0c93-115">Ad esempio, è possibile raggruppare gli utenti in base alla funzione o allo scopo di alto livello dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f0c93-115">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="f0c93-p104">Inoltre, alcuni servizi cloud possono essere condivisi al di fuori dell'organizzazione senza alcun account utente. È necessario identificare anche questi gruppi di utenti.</span><span class="sxs-lookup"><span data-stu-id="f0c93-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="f0c93-118">È possibile utilizzare i gruppi in Azure AD per diversi scopi che semplificano la gestione dell'ambiente cloud.</span><span class="sxs-lookup"><span data-stu-id="f0c93-118">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="f0c93-119">Ad esempio, con i gruppi di Azure AD, è possibile:</span><span class="sxs-lookup"><span data-stu-id="f0c93-119">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="f0c93-120">Utilizzo delle licenze basate su gruppo per assegnare le licenze per Office 365 agli account utente automaticamente non appena vengono aggiunti.</span><span class="sxs-lookup"><span data-stu-id="f0c93-120">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="f0c93-121">Aggiungere account utente a gruppi specifici in modo dinamico in base agli attributi dell'account utente, come per esempio il reparto.</span><span class="sxs-lookup"><span data-stu-id="f0c93-121">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="f0c93-122">Effettuare automaticamente il provisioning degli utenti per le applicazioni Software as a Service (SaaS) e proteggere l'accesso a tali applicazioni con l'autenticazione a più fattori e altre regole di accesso condizionale.</span><span class="sxs-lookup"><span data-stu-id="f0c93-122">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="f0c93-123">Provisioning delle autorizzazioni e dei livelli di accesso per i siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f0c93-123">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="f0c93-124">È possibile creare nuovi ***utenti*** con:</span><span class="sxs-lookup"><span data-stu-id="f0c93-124">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="f0c93-125">L'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f0c93-125">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="f0c93-126">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0c93-126">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="f0c93-127">È possibile creare nuovi ***gruppi*** con:</span><span class="sxs-lookup"><span data-stu-id="f0c93-127">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="f0c93-128">L'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f0c93-128">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="f0c93-129">PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0c93-129">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="f0c93-130">Passaggio successivo per le identità solo cloud</span><span class="sxs-lookup"><span data-stu-id="f0c93-130">Next step for cloud-only identities</span></span>

<span data-ttu-id="f0c93-131">[Assegnare licenze agli account utente](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="f0c93-131">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md)</span></span>
