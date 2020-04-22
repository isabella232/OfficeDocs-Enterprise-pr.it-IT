---
title: Sincronizzazione della directory e dell'identità ibrida per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 04/20/2010
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Descrive la sincronizzazione della directory con Office 365, la pulizia dei servizi di dominio Active Directory e lo strumento Azure Active Directory Connect.
ms.openlocfilehash: 44894cdbc65c243ce0c4a66ceba1d123ece49c62
ms.sourcegitcommit: f2e640ffdbef95c6d98845f85fd9bea21a7388aa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "43580933"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="7a0ad-103">Sincronizzazione della directory e dell'identità ibrida per Office 365</span><span class="sxs-lookup"><span data-stu-id="7a0ad-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="7a0ad-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="7a0ad-105">A seconda delle esigenze aziendali e dei requisiti tecnici, il modello di identità ibrido e la sincronizzazione della directory rappresentano la scelta più comune per i clienti aziendali che adottano Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="7a0ad-106">La sincronizzazione della directory consente di gestire le identità nei servizi di dominio Active Directory e tutti gli aggiornamenti per gli account utente, i gruppi e i contatti vengono sincronizzati con il tenant Azure Active Directory (Azure AD) dell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="7a0ad-107">Quando gli account utente di servizi di dominio Active Directory vengono sincronizzati per la prima volta, non viene assegnata automaticamente una licenza di Office 365 e non possono accedere ai servizi di Office 365, ad esempio la posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="7a0ad-108">È necessario assegnare una licenza a questi account utente, sia singolarmente che dinamicamente tramite l'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="7a0ad-109">Autenticazione per l'identità ibrida</span><span class="sxs-lookup"><span data-stu-id="7a0ad-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="7a0ad-110">Quando si utilizza il modello di identità ibrido, esistono due tipi di autenticazione:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="7a0ad-111">Autenticazione gestita</span><span class="sxs-lookup"><span data-stu-id="7a0ad-111">Managed authentication</span></span>

  <span data-ttu-id="7a0ad-112">Azure AD gestisce il processo di autenticazione utilizzando una versione con hash locale memorizzata della password o invia le credenziali a un agente software locale per l'autenticazione da parte di servizi di dominio Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="7a0ad-113">Autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="7a0ad-113">Federated authentication</span></span>

  <span data-ttu-id="7a0ad-114">Azure AD reindirizza il computer client richiedendo l'autenticazione per contattare un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="7a0ad-115">Autenticazione gestita</span><span class="sxs-lookup"><span data-stu-id="7a0ad-115">Managed authentication</span></span>

<span data-ttu-id="7a0ad-116">Esistono due tipi di autenticazione gestita:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="7a0ad-117">Sincronizzazione dell'hash delle password (PHS)</span><span class="sxs-lookup"><span data-stu-id="7a0ad-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="7a0ad-118">L'autenticazione viene eseguita direttamente da Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="7a0ad-119">Autenticazione pass-through (PTA)</span><span class="sxs-lookup"><span data-stu-id="7a0ad-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="7a0ad-120">L'autenticazione di Azure AD viene eseguita da AD DS.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="7a0ad-121">Sincronizzazione hash delle password</span><span class="sxs-lookup"><span data-stu-id="7a0ad-121">Password hash synchronization</span></span>

<span data-ttu-id="7a0ad-122">Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli account utente di servizi di dominio Active Directory con Office 365 e gestire gli utenti in locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="7a0ad-123">Gli hash delle password degli utenti vengono sincronizzati da servizi di dominio Active Directory ad Azure AD in modo che gli utenti abbiano la stessa password locale e nel cloud.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="7a0ad-124">Questo è il modo più semplice per abilitare l'autenticazione per le identità di servizi di dominio Active Directory in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![Sincronizzazione dell'hash delle password (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="7a0ad-126">Quando le password vengono modificate o reimpostate in locale, i nuovi hash delle password vengono sincronizzati con Azure AD, in modo che gli utenti possano sempre utilizzare la stessa password per le risorse cloud e le risorse locali.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-126">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="7a0ad-127">Le password degli utenti non vengono mai inviate ad Azure AD o archiviate in Azure AD in testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-127">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="7a0ad-128">Alcune funzionalità Premium di Azure AD, ad esempio la protezione delle identità, richiedono pH indipendentemente dal metodo di autenticazione selezionato.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-128">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="7a0ad-129">Per ulteriori informazioni, vedere [choosing pH](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-129">See [choosing PHS](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="7a0ad-130">Autenticazione pass-through</span><span class="sxs-lookup"><span data-stu-id="7a0ad-130">Pass-through authentication</span></span>

<span data-ttu-id="7a0ad-131">L'autenticazione pass-through (PTA) fornisce una semplice convalida delle password per i servizi di autenticazione di Azure AD utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con il servizio di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-131">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="7a0ad-132">Con l'autenticazione pass-through (PTA), è possibile sincronizzare gli account utente di servizi di dominio Active Directory con Office 365 e gestire gli utenti in locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-132">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![Autenticazione pass-through (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="7a0ad-134">PTA consente agli utenti di accedere alle risorse e alle applicazioni locali e di Office 365 utilizzando l'account locale e la password.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-134">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="7a0ad-135">Questa configurazione consente di convalidare le password degli utenti direttamente nei servizi di dominio Active Directory locali senza archiviare gli hash delle password in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-135">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="7a0ad-136">PTA è anche per le organizzazioni con un requisito di sicurezza per applicare immediatamente gli Stati degli account utente locali, i criteri di password e le ore di accesso.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-136">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="7a0ad-137">Per ulteriori informazioni, vedere [scegliere PTA](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-137">See [choosing PTA](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="7a0ad-138">Autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="7a0ad-138">Federated authentication</span></span>

<span data-ttu-id="7a0ad-139">L'autenticazione federata è principalmente per organizzazioni aziendali di grandi dimensioni con requisiti di autenticazione più complessi.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-139">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="7a0ad-140">Le identità di servizi di dominio Active Directory sono sincronizzate con Office 365 e gli account utente vengono gestiti in locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-140">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="7a0ad-141">Con l'autenticazione federata, gli utenti hanno la stessa password in locale e nel cloud e non devono accedere di nuovo per utilizzare Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-141">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="7a0ad-142">L'autenticazione federata può supportare ulteriori requisiti di autenticazione, ad esempio l'autenticazione basata su smartcard o un'autenticazione a più fattori di terze parti e in genere è necessario quando le organizzazioni dispongono di un requisito di autenticazione non supportato nativamente da Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-142">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="7a0ad-143">Per ulteriori informazioni, vedere [scelta dell'autenticazione federata](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-143">See [choosing federated authentication](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="7a0ad-144">Provider di identità e autenticazione di terze parti</span><span class="sxs-lookup"><span data-stu-id="7a0ad-144">Third-party authentication and identity providers</span></span>

<span data-ttu-id="7a0ad-145">Gli oggetti directory locali possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti (IdP).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-145">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="7a0ad-146">Se nell'organizzazione viene utilizzata una soluzione di terze parti, è possibile configurare l'accesso con tale soluzione per Office 365 purché la soluzione di Federazione di terze parti sia compatibile con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-146">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="7a0ad-147">Per ulteriori informazioni, vedere [compatibilità di Azure ad Federation](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-147">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="7a0ad-148">Pulizia di servizi di dominio Active Directory</span><span class="sxs-lookup"><span data-stu-id="7a0ad-148">AD DS Cleanup</span></span>

<span data-ttu-id="7a0ad-149">Per garantire una transizione senza problemi a Office 365 mediante la sincronizzazione, è necessario preparare la foresta di AD DS prima di iniziare la distribuzione della sincronizzazione della directory di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-149">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="7a0ad-150">Quando si [Configura la sincronizzazione della directory in Office 365](set-up-directory-synchronization.md), uno dei passaggi è [scaricare ed eseguire lo strumento IdFix](install-and-run-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-150">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="7a0ad-151">È possibile utilizzare lo strumento IdFix per facilitare la [pulizia della directory](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-151">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="7a0ad-152">La pulizia della directory dovrebbe concentrarsi sulle attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-152">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="7a0ad-153">Rimuovere gli attributi **ProxyAddress** e **userPrincipalName** duplicati.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-153">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="7a0ad-154">Aggiornare gli attributi **userPrincipalName** vuoti e non validi con gli attributi **userPrincipalName** validi.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-154">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="7a0ad-155">Rimuovere i caratteri non validi e discutibili negli attributi **DATANAME**, cognome ( **sn** ), **sAMAccountName**, **DisplayName**, **mail**, **proxyAddresses**, **mailNickname**e **userPrincipalName** .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-155">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="7a0ad-156">Per informazioni dettagliate sulla preparazione degli attributi, vedere [l'elenco degli attributi sincronizzati tramite lo strumento di sincronizzazione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-156">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a0ad-157">Si tratta degli stessi attributi sincronizzati da Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-157">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="7a0ad-158">Considerazioni sulla distribuzione di più foreste</span><span class="sxs-lookup"><span data-stu-id="7a0ad-158">Multi-forest deployment considerations</span></span>

<span data-ttu-id="7a0ad-159">Per più foreste e opzioni SSO, utilizzare l' [installazione personalizzata di Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-159">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="7a0ad-160">Se l'organizzazione dispone di più foreste per l'autenticazione (foreste di accesso), è consigliabile eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-160">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="7a0ad-161">**Valutare la possibilità di consolidare le foreste.**</span><span class="sxs-lookup"><span data-stu-id="7a0ad-161">**Consider consolidating your forests.**</span></span> <span data-ttu-id="7a0ad-162">In generale, è necessario un sovraccarico maggiore per la gestione di più foreste.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-162">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="7a0ad-163">A meno che l'organizzazione non disponga di vincoli di sicurezza che determinano la necessità di foreste separate, valutare la possibilità di semplificare l'ambiente locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-163">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="7a0ad-164">**Utilizzare solo nella foresta di accesso principale.**</span><span class="sxs-lookup"><span data-stu-id="7a0ad-164">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="7a0ad-165">Valutare la possibilità di distribuire Office 365 solo nella foresta di accesso principale per l'implementazione iniziale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-165">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="7a0ad-166">Se non è possibile consolidare la distribuzione di servizi di dominio Active Directory a più foreste o se si utilizzano altre funzionalità di gestione delle identità, potrebbe essere possibile sincronizzarle con l'aiuto di Microsoft o di un partner.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-166">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="7a0ad-167">Per ulteriori informazioni, vedere [multi-Forest Directory Sync with Single Sign-on scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) .</span><span class="sxs-lookup"><span data-stu-id="7a0ad-167">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="7a0ad-168">Caratteristiche che dipendono dalla sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="7a0ad-168">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="7a0ad-169">La sincronizzazione della directory è necessaria per le caratteristiche e le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-169">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="7a0ad-170">Accesso Single Sign-on (SSO) di Azure AD</span><span class="sxs-lookup"><span data-stu-id="7a0ad-170">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="7a0ad-171">Coesistenza Skype</span><span class="sxs-lookup"><span data-stu-id="7a0ad-171">Skype coexistence</span></span>
- <span data-ttu-id="7a0ad-172">Distribuzione ibrida di Exchange, tra cui:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-172">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="7a0ad-173">Elenco indirizzi globale (GAL, Global Address List) completamente condiviso tra l'ambiente Exchange locale e Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-173">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="7a0ad-174">Sincronizzazione delle informazioni dell'elenco indirizzi globale da diversi sistemi di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-174">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="7a0ad-175">La possibilità di aggiungere gli utenti a e rimuovere gli utenti dalle offerte di servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-175">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="7a0ad-176">Per questo è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="7a0ad-176">This requires the following:</span></span>
  - <span data-ttu-id="7a0ad-177">La sincronizzazione bidirezionale deve essere configurata durante la configurazione della sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-177">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="7a0ad-178">Per impostazione predefinita, gli strumenti di sincronizzazione della directory scrivono le informazioni della directory solo nel cloud.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-178">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="7a0ad-179">Quando si configura la sincronizzazione bidirezionale, è possibile abilitare la funzionalità di write-back in modo che un numero limitato di attributi dell'oggetto vengano copiati dal cloud e quindi riscriverli nel servizio di dominio Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-179">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="7a0ad-180">Il write-back è noto anche come modalità ibrida di Exchange.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-180">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="7a0ad-181">Una distribuzione ibrida di Exchange locale</span><span class="sxs-lookup"><span data-stu-id="7a0ad-181">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="7a0ad-182">La possibilità di spostare le cassette postali degli utenti in Office 365 mantenendo le cassette postali degli utenti locali.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-182">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="7a0ad-183">I mittenti attendibili e i mittenti bloccati in locale vengono replicati in Office 365.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-183">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="7a0ad-184">La delega di base e la funzionalità di invio per conto di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-184">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="7a0ad-185">Si dispone di una soluzione di autenticazione con smart card o multi-factor integrata.</span><span class="sxs-lookup"><span data-stu-id="7a0ad-185">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="7a0ad-186">Sincronizzazione di foto, miniature, sale conferenze e gruppi di sicurezza</span><span class="sxs-lookup"><span data-stu-id="7a0ad-186">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="7a0ad-187">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="7a0ad-187">Next step</span></span>

<span data-ttu-id="7a0ad-188">Quando si è pronti per la distribuzione dell'identità ibrida, vedere [Prepare to provisioning Users](prepare-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="7a0ad-188">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7a0ad-189">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a0ad-189">See also</span></span>

[<span data-ttu-id="7a0ad-190">Panoramica di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="7a0ad-190">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

