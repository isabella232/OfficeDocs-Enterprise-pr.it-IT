---
title: Modelli di gestione delle identità di Office 365 e Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 05/20/2019
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
description: Informazioni sulla gestione delle identità utente in Office 365.
ms.openlocfilehash: 0cc40323d978fe9ab13e3326dac183143a014406
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "40071878"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="11628-103">Modelli di gestione delle identità di Office 365 e Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="11628-103">Office 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="11628-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="11628-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="11628-105">Per gestire le identità e l'autenticazione, Office 365 usa Azure Active Directory (Azure AD), un servizio di autenticazione e gestione delle identità utente basato sul cloud incluso nell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="11628-105">Office 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Office 365 subscription, to manage identities and authentication for Office 365.</span></span> <span data-ttu-id="11628-106">La configurazione corretta dell'infrastruttura di gestione delle identità è di fondamentale importanza per gestire l'accesso utente e le autorizzazioni di Office 365 per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="11628-106">Getting your identity infrastructure configured correctly is vital to managing Office 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="11628-107">Prima di iniziare, guardare questo video che illustra i modelli di gestione delle identità e l'autenticazione sia per Office 365 che per Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-107">Before you begin, watch this video for an overview of identity models and authentication for both Office 365 and Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="11628-108">La prima opzione di pianificazione è il modello di gestione delle identità di Office 365.</span><span class="sxs-lookup"><span data-stu-id="11628-108">Your first planning choice is the Office 365 identity model.</span></span>

## <a name="office-365-identity-models"></a><span data-ttu-id="11628-109">Modelli di gestione delle identità di Office 365</span><span class="sxs-lookup"><span data-stu-id="11628-109">Office 365 identity models</span></span>

<span data-ttu-id="11628-110">Per pianificare gli account utente, è necessario prima di tutto conoscere i due modelli di gestione delle identità disponibili in Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="11628-111">È possibile mantenere le identità dell'organizzazione solo nel cloud. In alternativa, è possibile mantenere le identità Active Directory Domain Services (AD DS) in locale e usarle per l'autenticazione quando gli utenti accedono ai servizi cloud di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="11628-112">Ecco i due tipi di identità con la descrizione dei vantaggi e dell'ambiente in cui sono più indicati.</span><span class="sxs-lookup"><span data-stu-id="11628-112">Here are the two types of identity and their best fit and benefits.</span></span>

|||
|:-------|:-----|:-----|
|  | <span data-ttu-id="11628-113">**Identità solo cloud**</span><span class="sxs-lookup"><span data-stu-id="11628-113">**Cloud-only identity**</span></span> | <span data-ttu-id="11628-114">**Identità ibrida**</span><span class="sxs-lookup"><span data-stu-id="11628-114">**Hybrid identity**</span></span> |
| <span data-ttu-id="11628-115">**Definizione**</span><span class="sxs-lookup"><span data-stu-id="11628-115">**Definition**</span></span> | <span data-ttu-id="11628-116">L'account utente esiste solo nel tenant di Azure Active Directory (Azure AD) per l'abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-116">User account only exists in the Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="11628-117">L'account utente esiste in AD DS, ma una copia si trova anche nel tenant di Azure AD per l'abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-117">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="11628-118">L'account utente in Azure AD può includere anche una versione con hash della password dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="11628-118">The user account in Azure AD might also include a hashed version of the user account password.</span></span> |
| <span data-ttu-id="11628-119">**Autenticazione delle credenziali utente in Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="11628-119">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="11628-120">Per eseguire l'autenticazione, il tenant di Azure AD per l'abbonamento a Microsoft 365 usa l'account dell'identità cloud.</span><span class="sxs-lookup"><span data-stu-id="11628-120">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="11628-121">Il tenant di Azure AD per l'abbonamento a Microsoft 365 gestisce il processo di autenticazione oppure reindirizza l'utente a un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="11628-121">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="11628-122">**Indicato per**</span><span class="sxs-lookup"><span data-stu-id="11628-122">**Best for**</span></span> | <span data-ttu-id="11628-123">Organizzazioni che non hanno o necessitano di un'istanza locale di AD DS.</span><span class="sxs-lookup"><span data-stu-id="11628-123">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="11628-124">Organizzazioni che usano AD DS o un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="11628-124">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="11628-125">**Principale vantaggio**</span><span class="sxs-lookup"><span data-stu-id="11628-125">**Greatest benefit**</span></span> | <span data-ttu-id="11628-126">Semplice da usare.</span><span class="sxs-lookup"><span data-stu-id="11628-126">Simple to use.</span></span> <span data-ttu-id="11628-127">Non richiede altri strumenti o server di directory.</span><span class="sxs-lookup"><span data-stu-id="11628-127">No extra directory tools or servers required.</span></span> | <span data-ttu-id="11628-128">Gli utenti possono usare le stesse credenziali per accedere a risorse locali o basate sul cloud.</span><span class="sxs-lookup"><span data-stu-id="11628-128">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="11628-129">Identità solo cloud</span><span class="sxs-lookup"><span data-stu-id="11628-129">Cloud-only identity</span></span>

<span data-ttu-id="11628-130">Un'identità solo cloud usa solo gli account utente che esistono in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-130">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="11628-131">Viene in genere usata da organizzazioni di piccole dimensioni che non dispongono di server locali o non usano AD DS per gestire le identità locali.</span><span class="sxs-lookup"><span data-stu-id="11628-131">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="11628-132">Ecco i componenti di base dell'identità solo cloud.</span><span class="sxs-lookup"><span data-stu-id="11628-132">Here are the basic components of cloud-only identity.</span></span>
 
![Componenti di base dell'identità solo cloud](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="11628-134">Sia gli utenti locali che quelli remoti (online) usano gli account utente e le password di Azure AD per accedere ai servizi cloud di Office 365.</span><span class="sxs-lookup"><span data-stu-id="11628-134">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Office 365 cloud services.</span></span> <span data-ttu-id="11628-135">Azure AD autentica le credenziali utente in base agli account utente e alle password archiviate.</span><span class="sxs-lookup"><span data-stu-id="11628-135">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="11628-136">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="11628-136">Administration</span></span>
<span data-ttu-id="11628-137">Dal momento che gli account utente vengono solo archiviati in Azure AD, è possibile gestire le identità cloud con strumenti come l'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) e Windows PowerShell con il modulo PowerShell per Graph di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="11628-137">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and Windows PowerShell with the Azure Active Directory PowerShell for Graph module.</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="11628-138">Identità ibrida</span><span class="sxs-lookup"><span data-stu-id="11628-138">Hybrid identity</span></span>

<span data-ttu-id="11628-139">L'identità ibrida usa gli account che provengono da un'istanza locale di AD DS e per i quali esiste una copia nel tenant di Azure AD di un abbonamento a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="11628-139">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="11628-140">Tuttavia, la maggior parte delle modifiche è unidirezionale.</span><span class="sxs-lookup"><span data-stu-id="11628-140">However, most changes only flow one way.</span></span> <span data-ttu-id="11628-141">Le modifiche apportate agli account utente di AD DS vengono sincronizzate con le copie corrispondenti in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-141">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="11628-142">Le modifiche apportate agli account basati sul cloud in Azure AD, ad esempio i nuovi account utente, non vengono invece sincronizzate con AD DS.</span><span class="sxs-lookup"><span data-stu-id="11628-142">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="11628-143">Azure AD Connect offre la sincronizzazione continua degli account.</span><span class="sxs-lookup"><span data-stu-id="11628-143">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="11628-144">Viene eseguito in un server locale, verifica la presenza di modifiche in AD DS e invia queste modifiche ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-144">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="11628-145">Azure AD Connect consente di filtrare gli account sincronizzati e scegliere se eseguire la sincronizzazione di una versione con hash delle password utente, nota come sincronizzazione dell'hash delle password (PHS).</span><span class="sxs-lookup"><span data-stu-id="11628-145">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="11628-146">Durante l'implementazione dell'identità ibrida, l'istanza locale di AD DS costituisce l'origine autorevole delle informazioni sull'account.</span><span class="sxs-lookup"><span data-stu-id="11628-146">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="11628-147">Questo significa che le attività di amministrazione vengono eseguite principalmente in locale e quindi sincronizzate con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-147">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="11628-148">Ecco i componenti dell'identità ibrida.</span><span class="sxs-lookup"><span data-stu-id="11628-148">Here are the components of hybrid identity.</span></span>

![Componenti dell'identità ibrida](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="11628-150">Il tenant di Azure AD contiene una copia degli account di AD DS.</span><span class="sxs-lookup"><span data-stu-id="11628-150">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="11628-151">In questa configurazione sia gli utenti locali che gli utenti remoti che accedono ai servizi cloud di Microsoft 365 eseguono l'autenticazione in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-151">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="11628-152">È sempre necessario usare Azure AD Connect per sincronizzare gli account utenti per l'identità ibrida.</span><span class="sxs-lookup"><span data-stu-id="11628-152">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="11628-153">Gli account utente sincronizzati in Azure AD sono necessari per l'assegnazione di licenze e la gestione dei gruppi, nonché per configurare le autorizzazioni e per altre attività amministrative che interessano gli account utente.</span><span class="sxs-lookup"><span data-stu-id="11628-153">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="11628-154">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="11628-154">Administration</span></span>

<span data-ttu-id="11628-155">Dal momento che gli account utente originali e autorevoli sono archiviati nell'istanza locale di AD DS, è possibile gestire le identità con gli stessi strumenti di AD DS, ad esempio lo strumento Utenti e computer di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="11628-155">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="11628-156">Non viene invece usata l'interfaccia di amministrazione di Microsoft 365 o Windows PowerShell per gestire gli account utente sincronizzati in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="11628-156">You don’t use the Microsoft 365 admin center or Windows PowerShell to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="11628-157">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="11628-157">Next step</span></span>

<span data-ttu-id="11628-158">Se è necessario il modello di gestione delle identità solo cloud, vedere [Identità solo cloud](cloud-only-identities.md).</span><span class="sxs-lookup"><span data-stu-id="11628-158">If you need the cloud-only identity model, see [Cloud-only identities](cloud-only-identities.md).</span></span>

<span data-ttu-id="11628-159">Se è necessario il modello di gestione delle identità ibrido, vedere [Sincronizzazione della directory](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="11628-159">If you need the hybrid identity model, see [directory synchronization](plan-for-directory-synchronization.md).</span></span>
  

## <a name="video-training"></a><span data-ttu-id="11628-160">Video di formazione</span><span class="sxs-lookup"><span data-stu-id="11628-160">Video training</span></span>

<span data-ttu-id="11628-161">Vedere il video corso sulla [gestione delle identità con Azure AD Connect in Office 365](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx) offerto da LinkedIn Learning.</span><span class="sxs-lookup"><span data-stu-id="11628-161">See the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>

## <a name="see-also"></a><span data-ttu-id="11628-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="11628-162">See also</span></span>

[<span data-ttu-id="11628-163">Panoramica di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="11628-163">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
