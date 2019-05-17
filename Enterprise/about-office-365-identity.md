---
title: Modelli di identità di Office 365 e Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Informazioni sul modo in cui l'identità dell'utente viene gestita in Office 365.
ms.openlocfilehash: cd7fb1db2d5372097f3da0e6a2521335d7933015
ms.sourcegitcommit: 47c6156c0038745103b71f44b2a3b103c62e5d6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "34102465"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="f5161-103">Modelli di identità di Office 365 e Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="f5161-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="f5161-104">Office 365 utilizza Azure Active Directory (Azure AD), un servizio di autenticazione e identità utente basato sul cloud incluso nell'abbonamento a Office 365, per gestire le identità e l'autenticazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-104">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="f5161-105">Ottenere l'infrastruttura di identità configurata in modo corretto è fondamentale per la gestione dell'accesso utente e delle autorizzazioni di Office 365 per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f5161-105">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="f5161-106">Prima di iniziare, guardare questo video per una panoramica dei modelli di identità e dell'autenticazione sia per Office 365 che per Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-106">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="f5161-107">La prima scelta di pianificazione è il modello di identità di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-107">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="f5161-108">Modelli di identità di Office 365</span><span class="sxs-lookup"><span data-stu-id="f5161-108">Office 365 identity models</span></span>

<span data-ttu-id="f5161-109">Per pianificare gli account utente, è innanzitutto necessario comprendere i due modelli di identità in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-109">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="f5161-110">È possibile mantenere le identità dell'organizzazione solo nel cloud oppure è possibile mantenere le identità di servizi di dominio Active Directory (AD DS) locali e utilizzarle per l'autenticazione quando gli utenti accedono ai servizi cloud di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-110">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="f5161-111">Di seguito sono illustrati i due tipi di identità e i loro vantaggi e adattamenti.</span><span class="sxs-lookup"><span data-stu-id="f5161-111">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="f5161-112">Identità solo cloud</span><span class="sxs-lookup"><span data-stu-id="f5161-112">Cloud-only identity</span></span> | <span data-ttu-id="f5161-113">Identità ibrida</span><span class="sxs-lookup"><span data-stu-id="f5161-113">Hybrid identity</span></span> |
| <span data-ttu-id="f5161-114">Definizione</span><span class="sxs-lookup"><span data-stu-id="f5161-114">Definition</span></span> | <span data-ttu-id="f5161-115">L'account utente è presente solo nel tenant di Azure Active Directory (Azure AD) per l'abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-115">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="f5161-116">L'account utente esiste in servizi di dominio Active Directory e una copia è anche nel tenant di Azure AD per l'abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-116">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="f5161-117">L'account utente in Azure AD potrebbe includere anche una versione con hash della password dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="f5161-117">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="f5161-118">In che modo Microsoft 365 autentica le credenziali utente</span><span class="sxs-lookup"><span data-stu-id="f5161-118">How Microsoft 365 authenticates user credentials</span></span> | <span data-ttu-id="f5161-119">Il tenant di Azure AD per la sottoscrizione Microsoft 365 esegue l'autenticazione con l'account di identità cloud.</span><span class="sxs-lookup"><span data-stu-id="f5161-119">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="f5161-120">Il tenant di Azure AD per la sottoscrizione Microsoft 365 gestisce il processo di autenticazione oppure reindirizza l'utente a un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="f5161-120">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="f5161-121">Ideale per...</span><span class="sxs-lookup"><span data-stu-id="f5161-121">Best for…</span></span> | <span data-ttu-id="f5161-122">Organizzazioni che non dispongono o hanno bisogno di servizi di dominio Active Directory locali.</span><span class="sxs-lookup"><span data-stu-id="f5161-122">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="f5161-123">Organizzazioni che utilizzano servizi di dominio Active Directory o un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="f5161-123">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="f5161-124">Maggiore vantaggio</span><span class="sxs-lookup"><span data-stu-id="f5161-124">Greatest benefit</span></span> | <span data-ttu-id="f5161-125">Semplice da usare.</span><span class="sxs-lookup"><span data-stu-id="f5161-125">Simple to use.</span></span> <span data-ttu-id="f5161-126">Non sono necessari ulteriori server o strumenti di directory.</span><span class="sxs-lookup"><span data-stu-id="f5161-126">No extra directory tools or servers required.</span></span> | <span data-ttu-id="f5161-127">Gli utenti possono utilizzare le stesse credenziali per l'accesso a risorse locali o basate su cloud.</span><span class="sxs-lookup"><span data-stu-id="f5161-127">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

### <a name="cloud-only-identity"></a><span data-ttu-id="f5161-128">Identità solo cloud</span><span class="sxs-lookup"><span data-stu-id="f5161-128">Cloud-only identity</span></span>

<span data-ttu-id="f5161-129">Un'identità solo cloud utilizza gli account utente che esistono solo in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-129">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="f5161-130">L'identità del cloud in genere viene utilizzata dalle organizzazioni di piccole dimensioni che non dispongono di server locali oppure che non utilizzano servizi di dominio Active Directory per gestire le identità locali.</span><span class="sxs-lookup"><span data-stu-id="f5161-130">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="f5161-131">Di seguito sono ripartiti i componenti di base dell'identità solo cloud.</span><span class="sxs-lookup"><span data-stu-id="f5161-131">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="f5161-132">Sia gli utenti locali che quelli remoti (online) usano gli account utente e le password di Azure AD per accedere ai servizi cloud di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-132">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="f5161-133">Azure AD autentica le credenziali degli utenti in base agli account utente e alle password archiviati.</span><span class="sxs-lookup"><span data-stu-id="f5161-133">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

#### <a name="administration"></a><span data-ttu-id="f5161-134">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="f5161-134">Administration</span></span>
<span data-ttu-id="f5161-135">Poiché gli account utente sono archiviati solo in Azure AD, è possibile gestire le identità cloud con strumenti quali l'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) e Windows PowerShell con il modulo Azure Active Directory PowerShell per Graph.</span><span class="sxs-lookup"><span data-stu-id="f5161-135">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="f5161-136">Identità ibrida</span><span class="sxs-lookup"><span data-stu-id="f5161-136">Hybrid identity</span></span>

<span data-ttu-id="f5161-137">L'identità ibrida utilizza gli account provenienti da un servizio di dominio Active Directory locale e dispone di una copia nel tenant di Azure AD di un abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f5161-137">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="f5161-138">Tuttavia, la maggior parte delle modifiche scorre solo in un modo.</span><span class="sxs-lookup"><span data-stu-id="f5161-138">However, most changes only flow one way.</span></span> <span data-ttu-id="f5161-139">Le modifiche apportate agli account utente di servizi di dominio Active Directory vengono sincronizzate con la loro copia in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-139">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="f5161-140">Tuttavia, le modifiche apportate agli account basati sul cloud in Azure AD, ad esempio nuovi account utente, non vengono sincronizzate con servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f5161-140">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="f5161-141">Azure AD Connect fornisce la sincronizzazione degli account in uscita.</span><span class="sxs-lookup"><span data-stu-id="f5161-141">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="f5161-142">Viene eseguito su un server locale, verifica le modifiche apportate a servizi di dominio Active Directory e inoltra tali modifiche ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-142">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="f5161-143">Azure AD Connect offre la possibilità di filtrare gli account che vengono sincronizzati e se sincronizzare una versione con hash delle password degli utenti, nota come la sincronizzazione degli hash delle password (pH).</span><span class="sxs-lookup"><span data-stu-id="f5161-143">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="f5161-144">Quando si implementa l'identità ibrida, il servizio di dominio Active Directory locale è l'origine autorevole per le informazioni sull'account.</span><span class="sxs-lookup"><span data-stu-id="f5161-144">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="f5161-145">Questo significa che le attività di amministrazione vengono eseguite principalmente in locale, che vengono quindi sincronizzate con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-145">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="f5161-146">Di seguito sono ripartiti i componenti dell'identità ibrida.</span><span class="sxs-lookup"><span data-stu-id="f5161-146">Here are the components of hybrid identity.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="f5161-147">Il tenant di Azure AD ha una copia degli account di servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f5161-147">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="f5161-148">In questa configurazione, sia gli utenti locali che quelli remoti che accedono ai servizi cloud di Microsoft 365 eseguono l'autenticazione con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-148">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="f5161-149">È sempre necessario utilizzare Azure AD Connect per sincronizzare gli account utente per l'identità ibrida.</span><span class="sxs-lookup"><span data-stu-id="f5161-149">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="f5161-150">Sono necessari gli account utente sincronizzati in Azure AD per eseguire l'assegnazione delle licenze e la gestione dei gruppi, configurare le autorizzazioni e altre attività amministrative che coinvolgono gli account utente.</span><span class="sxs-lookup"><span data-stu-id="f5161-150">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

#### <a name="administration"></a><span data-ttu-id="f5161-151">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="f5161-151">Administration</span></span>

<span data-ttu-id="f5161-152">Poiché gli account utente originali e autorevoli sono archiviati in servizi di dominio Active Directory locali, è possibile gestire le identità con gli stessi strumenti di AD DS, ad esempio lo strumento utenti e computer di Active.</span><span class="sxs-lookup"><span data-stu-id="f5161-152">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="f5161-153">Non è possibile utilizzare l'interfaccia di amministrazione di Microsoft 365 o Windows PowerShell per gestire gli account utente sincronizzati in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f5161-153">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>


## <a name="next-step"></a><span data-ttu-id="f5161-154">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="f5161-154">Next step</span></span>

<span data-ttu-id="f5161-155">Se è necessario il modello di identità ibrido, vedere [Planning for your Identities Synchronized and Authentication Methods](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="f5161-155">If you need the hybrid identity model, see [planning for your synchronized identities and authentication methods](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="f5161-156">Video di formazione</span><span class="sxs-lookup"><span data-stu-id="f5161-156">Video training</span></span>

<span data-ttu-id="f5161-157">Vedere il corso video [Office 365: Manage Identities using Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), portato all'utente da LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="f5161-157">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
