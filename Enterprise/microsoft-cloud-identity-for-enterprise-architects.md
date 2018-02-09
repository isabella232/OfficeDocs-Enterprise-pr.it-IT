---
title: "Identità cloud Microsoft per Enterprise Architects"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: d27b5085-7325-4ab9-9d9a-438908a65d2c
description: "Riepilogo: Progettare una soluzione di identità per i servizi cloud e le piattaforme Microsoft."
ms.openlocfilehash: 78a975a9d4f22ce6e624983db21dae1a762a3c09
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-cloud-identity-for-enterprise-architects"></a><span data-ttu-id="113dd-103">Identità cloud Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="113dd-103">Microsoft Cloud Identity for Enterprise Architects</span></span>

 <span data-ttu-id="113dd-104">**Riepilogo:** Progettare una soluzione di identità per i servizi cloud e le piattaforme Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113dd-104">**Summary:** Design your identity solution for Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="113dd-p101">In questo articolo viene descritto cosa devono sapere gli architetti IT sulla progettazione di identità per le organizzazioni che utilizzano i servizi cloud e le piattaforme Microsoft. È possibile visualizzare questo articolo anche come poster di 5 pagine e stamparlo in formato tabloid (noto anche come ledger, 11 x 17 o A3).</span><span class="sxs-lookup"><span data-stu-id="113dd-p101">This article describes what IT architects need to know about designing identity for organizations using Microsoft cloud services and platforms. You can also view this article as a 5-page poster and print it in tabloid format (also known as ledger, 11 x 17, or A3).</span></span>
  
<span data-ttu-id="113dd-107">[![Immagine di scorrimento per modello di identità del cloud Microsoft](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="113dd-107">[![Thumb image for Microsoft cloud identity model](images/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png) 
](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="113dd-108">![File PDF](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![File Visio](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![Visualizzare una pagina con le versioni in altre lingue](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[Altre lingue](https://www.microsoft.com/download/details.aspx?id=54431)</span><span class="sxs-lookup"><span data-stu-id="113dd-108">![PDF file](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586) | ![Visio file](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd) | ![See a page with versions in additional languages](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[More languages](https://www.microsoft.com/download/details.aspx?id=54431)</span></span>
  
<span data-ttu-id="113dd-109">È inoltre possibile visualizzare tutti i modelli nelle [Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md) e consultare la [Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://aka.ms/cloudarchitecture).</span><span class="sxs-lookup"><span data-stu-id="113dd-109">You can also see all of the models in the [Microsoft Cloud IT architecture resources](microsoft-cloud-it-architecture-resources.md) and swipe through [Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://aka.ms/cloudarchitecture).</span></span>
  
> [!NOTE]
> <span data-ttu-id="113dd-p102">Questo articolo riflette la versione di gennaio 2016 del poster **Identità cloud Microsoft per Enterprise Architects**. Non contiene le modifiche apportate alla versione di aprile 2016 o successiva del poster.</span><span class="sxs-lookup"><span data-stu-id="113dd-p102">This article reflects the January 2016 version of the **Microsoft cloud identity for enterprise architects** poster. It does not contain the changes for the April 2016 or later versions of the poster.</span></span>
  
## <a name="designing-identity-for-the-microsoft-cloud"></a><span data-ttu-id="113dd-112">Progettazione dell'identità per il cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="113dd-112">Designing identity for the Microsoft cloud</span></span>

<span data-ttu-id="113dd-p103">L'integrazione delle identità con il cloud Microsoft consente di accedere a una vasta gamma di servizi e opzioni di piattaforme cloud. Esistono due opzioni principali:</span><span class="sxs-lookup"><span data-stu-id="113dd-p103">Integrating your identities with the Microsoft cloud provides access to a broad range of services and cloud platform options. There are two main options:</span></span>
  
- <span data-ttu-id="113dd-p104">È possibile integrare con Microsoft Azure Active Directory (AD). Ciò include la sincronizzazione degli account locali con Azure AD, il provider di identità per il cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113dd-p104">You can integrate with Microsoft Azure Active Directory (AD). This involves synchronizing your on-premises accounts to Azure AD, the identity provider for the Microsoft cloud.</span></span>
    
- <span data-ttu-id="113dd-117">È possibile estendere l'ambiente Servizi di dominio Active Directory (AD DS) alle macchine virtuali in esecuzione nei servizi infrastruttura di Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-117">You can extend your on-premises Active Directory Domain Services (AD DS) environment to virtual machines running in Microsoft Azure infrastructure services.</span></span>
    
![Opzioni per la progettazione delle identità nel cloud](images/08277e96-e4d2-43cb-a56f-a11c7647881a.png)
  
 <span data-ttu-id="113dd-119">**Figura 1: opzioni per la progettazione delle identità nel cloud**</span><span class="sxs-lookup"><span data-stu-id="113dd-119">**Figure 1: Options for designing your identities in the cloud**</span></span>
  
<span data-ttu-id="113dd-120">Nella figura 1 viene illustrato che Azure AD è il provider di identità per i servizi Microsoft SaaS (Software as a Service) e le applicazioni Azure PaaS (Platform as a Service) e che le applicazioni line-of-business possono utilizzare AD DS locale.</span><span class="sxs-lookup"><span data-stu-id="113dd-120">Figure 1 shows how Azure AD is the identity provider for Microsoft Software as a Service (SaaS) services and Azure Platform as a Service (PaaS) applications and how line-of-business applications can use on-premises AD DS.</span></span> 
  
### <a name="azure-active-directory"></a><span data-ttu-id="113dd-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="113dd-121">Azure Active Directory</span></span>

<span data-ttu-id="113dd-p105">Microsoft Azure AD è il servizio di gestione degli accessi e delle identità ospitato nel cloud Microsoft. Si trova al centro dei servizi cloud e delle piattaforme Microsoft. L'integrazione con Azure AD fornisce l'accesso a tutti i servizi Microsoft SaaS tramite gli account e le password correnti. Tale integrazione fornisce inoltre l'identità basata su cloud per applicazioni PaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-p105">Microsoft Azure AD is the Microsoft cloud-hosted identity and access management service. It's at the center of Microsoft cloud services and platforms. Integrating with Azure AD provides access to all of the Microsoft SaaS services using your current set of accounts and passwords. That integration also provides cloud-based identity for Azure PaaS applications.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="113dd-126">Azure AD non sostituisce la necessità di disporre di AD DS locale per le aziende o di macchine virtuali basate su Windows in esecuzione nell'infrastruttura distribuita come servizio (Infrastructure as a Service, IaaS) di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-126">Azure AD does not replace the need for AD DS on-premises for enterprise organizations or for Windows -based virtual machines running in Azure Infrastructure as a Service (IaaS).</span></span> 
  
<span data-ttu-id="113dd-127">Sono disponibili tre versioni di Azure AD: gratuita, di base e premium.</span><span class="sxs-lookup"><span data-stu-id="113dd-127">There are three editions of Azure AD: Free, Basic, and Premium.</span></span> 
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="113dd-128">**Gratuita**</span><span class="sxs-lookup"><span data-stu-id="113dd-128">**Free**</span></span> <br/> |<span data-ttu-id="113dd-129">**Di base**</span><span class="sxs-lookup"><span data-stu-id="113dd-129">**Basic**</span></span> <br/> |<span data-ttu-id="113dd-130">**Premium**</span><span class="sxs-lookup"><span data-stu-id="113dd-130">**Premium**</span></span> <br/> |
| <span data-ttu-id="113dd-131">	Gestione degli account utente</span><span class="sxs-lookup"><span data-stu-id="113dd-131">Manage user accounts</span></span> <br/>  <span data-ttu-id="113dd-132">Sincronizzazione con directory locali</span><span class="sxs-lookup"><span data-stu-id="113dd-132">Synchronize with on-premises directories</span></span> <br/>  <span data-ttu-id="113dd-133">Single Sign-On in Azure, Office 365 e migliaia di altre note applicazioni SaaS, come Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox e altro</span><span class="sxs-lookup"><span data-stu-id="113dd-133">Single sign-on across Azure, Office 365, and thousands of other popular SaaS applications, such as Salesforce, Workday, Concur, DocuSign, Google Apps, Box, ServiceNow, Dropbox, and more</span></span> <br/> | <span data-ttu-id="113dd-134">Include tutte le capacità della versione gratuita, oltre a:</span><span class="sxs-lookup"><span data-stu-id="113dd-134">Includes all of the abilities in the Free edition, plus:</span></span> <br/>  <span data-ttu-id="113dd-135">Informazioni personalizzate distintive dell'azienda</span><span class="sxs-lookup"><span data-stu-id="113dd-135">Company branding</span></span> <br/>  <span data-ttu-id="113dd-136">Accesso alle applicazioni sulla base di un gruppo</span><span class="sxs-lookup"><span data-stu-id="113dd-136">Group-based application access</span></span> <br/>  <span data-ttu-id="113dd-137">Reimpostazione password self-service</span><span class="sxs-lookup"><span data-stu-id="113dd-137">Self-service password reset</span></span> <br/>  <span data-ttu-id="113dd-138">Contratto di servizio aziendale del 99,9%</span><span class="sxs-lookup"><span data-stu-id="113dd-138">Enterprise SLA of 99.9%</span></span> <br/> | <span data-ttu-id="113dd-139">Include tutte le caratteristiche della versione gratuita e della versione di base, oltre a:</span><span class="sxs-lookup"><span data-stu-id="113dd-139">Includes all of the features of the Free and Basic editions, plus:</span></span> <br/>  <span data-ttu-id="113dd-140">Gestione gruppi self-service</span><span class="sxs-lookup"><span data-stu-id="113dd-140">Self-service group management</span></span> <br/>  <span data-ttu-id="113dd-141">Avvisi e report di sicurezza avanzata</span><span class="sxs-lookup"><span data-stu-id="113dd-141">Advanced security reports and alerts</span></span> <br/>  <span data-ttu-id="113dd-142">Autenticazione a più fattori</span><span class="sxs-lookup"><span data-stu-id="113dd-142">Multi-factor authentication</span></span> <br/>  <span data-ttu-id="113dd-143">Reimpostazione della password con write-back in AD DS locale</span><span class="sxs-lookup"><span data-stu-id="113dd-143">Password reset with write-back to on-premises AD DS</span></span> <br/>  <span data-ttu-id="113dd-144">Sincronizzazione bidirezionale dello strumento Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="113dd-144">Azure AD Connect tool bidirectional synchronization</span></span> <br/>  <span data-ttu-id="113dd-145">Proxy di applicazione Azure AD</span><span class="sxs-lookup"><span data-stu-id="113dd-145">Azure AD Application Proxy</span></span> <br/>  <span data-ttu-id="113dd-146">	Microsoft Forefront Identity Manager (MIM)</span><span class="sxs-lookup"><span data-stu-id="113dd-146">Microsoft Forefront Identity Manager (MIM)</span></span> <br/> |
   
<span data-ttu-id="113dd-147">Per ulteriori informazioni sulle versioni, vedere [Edizioni di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span><span class="sxs-lookup"><span data-stu-id="113dd-147">For more information about versions, see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
### <a name="option-1-integrate-with-azure-active-directory"></a><span data-ttu-id="113dd-148">Opzione 1: integrazione con Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="113dd-148">Option 1: Integrate with Azure Active Directory</span></span>

<span data-ttu-id="113dd-p106">La maggior parte delle organizzazioni sincronizza un insieme di oggetti e attributi con il tenant di Azure AD. Lo strumento Azure AD Connect consente di sincronizzare gli account tra AD DS locale e un tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-p106">Most organizations synchronize a standard set of objects and attributes to their Azure AD tenant. The Azure AD Connect tool synchronizes your accounts between on-premises AD DS and an Azure AD tenant.</span></span>
  
![Integrazione con Azure AD](images/3ce05e49-2cb6-4cdc-99ab-d96c5bd12fe8.png)
  
 <span data-ttu-id="113dd-152">**Figura 2: integrazione con Azure AD**</span><span class="sxs-lookup"><span data-stu-id="113dd-152">**Figure 2: Integrating with Azure AD**</span></span>
  
<span data-ttu-id="113dd-p107">Nella figura 2 viene illustrato come lo strumento Azure AD Connect ottiene le modifiche di AD DS e le invia al tenant di Azure AD. In questo caso, il tenant di Azure AD è un duplicato ospitato nel cloud di contenuto della directory locale essenziale.</span><span class="sxs-lookup"><span data-stu-id="113dd-p107">Figure 2 shows how the Azure AD Connect tool obtains AD DS changes and sends them to your Azure AD tenant. In this case, your Azure AD tenant is a cloud-hosted duplicate of essential on-premises directory content.</span></span>
  
<span data-ttu-id="113dd-p108">Molte organizzazioni utilizzano AD DS come provider di identità locale. È possibile utilizzare un altro tipo di provider di identità locale (come uno di quelli che usano LDAP) e sincronizzarlo con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-p108">Many organizations use AD DS as their on-premises identity provider. You can use a different type of identity provider on-premises (such as one that uses LDAP), and synchronize these to Azure AD.</span></span>
  
### <a name="option-2-extend-ad-ds-to-azure"></a><span data-ttu-id="113dd-157">Opzione 2: estensione di AD DS ad Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-157">Option 2: Extend AD DS to Azure</span></span>

<span data-ttu-id="113dd-p109">L'estensione di AD DS a macchine virtuali in esecuzione nei servizi infrastruttura di Azure supporta un diverso set di soluzioni e applicazioni rispetto alla sincronizzazione con Azure AD. Eccone due:</span><span class="sxs-lookup"><span data-stu-id="113dd-p109">Extending AD DS to virtual machines running in Azure infrastructure services supports a different set of solutions and applications compared to synchronization with Azure AD. Here are two:</span></span>
  
- <span data-ttu-id="113dd-160">Supporta le soluzioni basate su cloud che richiedono l'autenticazione Kerberos o NTLM, oppure le macchine virtuali aggiunte a un dominio di AD DS.</span><span class="sxs-lookup"><span data-stu-id="113dd-160">Supports cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="113dd-161">Aggiunge un'ulteriore potenziale integrazione per i servizi cloud e le applicazioni nei servizi cloud e nelle piattaforme Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113dd-161">Adds additional integration potential for cloud services and applications across Microsoft cloud services and platforms.</span></span>
    
![Estensione di Servizi di dominio Active Directory ad Azure](images/4675cf17-962c-4840-b1dc-bbd1d8894a27.png)
  
 <span data-ttu-id="113dd-163">**Figura 3: estensione di AD DS ad Azure**</span><span class="sxs-lookup"><span data-stu-id="113dd-163">**Figure 3: Extending AD DS to Azure**</span></span>
  
<span data-ttu-id="113dd-p110">Nella figura 3 viene illustrato un controller di dominio di AD DS connesso a una rete virtuale di Azure mediante un dispositivo VPN locale e un gateway VPN di Azure. La rete virtuale di Azure contiene i server per un'applicazione line-of-business e il relativo insieme di controller di dominio di AD DS.</span><span class="sxs-lookup"><span data-stu-id="113dd-p110">Figure 3 shows an AD DS domain controller connected to an Azure virtual network through an on-premises VPN device and an Azure VPN gateway. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers.</span></span>
  
### <a name="more-information"></a><span data-ttu-id="113dd-166">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="113dd-166">More Information</span></span>

- [<span data-ttu-id="113dd-167">La sincronizzazione della directory con Office 365 è facile</span><span class="sxs-lookup"><span data-stu-id="113dd-167">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="113dd-168">Infografica: Gestione di identità e accesso nel cloud</span><span class="sxs-lookup"><span data-stu-id="113dd-168">Infographic: Cloud identity and access management</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524282)
    
- [<span data-ttu-id="113dd-169">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="113dd-169">Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524283)
    
## <a name="integrate-your-on-premises-ad-ds-accounts-with-microsoft-azure-ad"></a><span data-ttu-id="113dd-170">Integrazione degli account di AD DS locali con Microsoft Azure AD</span><span class="sxs-lookup"><span data-stu-id="113dd-170">Integrate your on-premises AD DS accounts with Microsoft Azure AD</span></span>

<span data-ttu-id="113dd-171">Sincronizzando gli account di AD DS locali con Azure AD, gli utenti possono utilizzare i propri account di AD DS per accedere:</span><span class="sxs-lookup"><span data-stu-id="113dd-171">By synchronizing your on-premises AD DS accounts with Azure AD, your users can use their on-premises AD DS accounts to access:</span></span>
  
- <span data-ttu-id="113dd-172">A tutti i servizi SaaS Microsoft (Office 365, Microsoft Intune e Dynamics CRM Online)</span><span class="sxs-lookup"><span data-stu-id="113dd-172">All of the Microsoft SaaS services (Office 365, Microsoft Intune, and Dynamics CRM Online)</span></span>
    
- <span data-ttu-id="113dd-173">Alle applicazioni in esecuzione in PaaS di Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-173">Your applications running in Azure PaaS</span></span>
    
<span data-ttu-id="113dd-174">Per configurare questa integrazione è possibile procedere in due modi:</span><span class="sxs-lookup"><span data-stu-id="113dd-174">There are two ways to configure this integration:</span></span>
  
- <span data-ttu-id="113dd-175">Sincronizzazione di password e directory</span><span class="sxs-lookup"><span data-stu-id="113dd-175">Directory and password synchronization</span></span>
    
- <span data-ttu-id="113dd-176">Federazione e Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="113dd-176">Federation and single sign-on</span></span>
    
<span data-ttu-id="113dd-p111">Iniziare con l'opzione più semplice che risponde alle proprie esigenze. È possibile passare da un'opzione all'altra, se necessario.</span><span class="sxs-lookup"><span data-stu-id="113dd-p111">Start with the simplest option that meets your needs. You can switch between these options, if needed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="113dd-179">L'uso di account basati solo sul cloud (non integrati con AD DS locale) non è consigliabile per le organizzazioni su scala aziendale.</span><span class="sxs-lookup"><span data-stu-id="113dd-179">Using cloud-only accounts (not integrating with your on-premises AD DS) is not recommended for enterprise-scale organizations.</span></span> 
  
### <a name="directory-and-password-synchronization"></a><span data-ttu-id="113dd-180">Sincronizzazione di password e directory</span><span class="sxs-lookup"><span data-stu-id="113dd-180">Directory and password synchronization</span></span>

<span data-ttu-id="113dd-181">Questa è l'opzione più semplice e richiede solo un server che esegue lo strumento Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="113dd-181">This is the simplest option and requires only a server running the Azure AD Connect tool.</span></span> 
  
![Configurazione della sincronizzazione di password e directory](images/e7dcfe8f-dab5-461e-89cc-d7a48f58dc0f.png)
  
 <span data-ttu-id="113dd-183">**Figura 4: configurazione della sincronizzazione di password e directory**</span><span class="sxs-lookup"><span data-stu-id="113dd-183">**Figure 4: Directory and password synchronization configuration**</span></span>
  
<span data-ttu-id="113dd-p112">Nella figura 4 viene illustrato un datacenter del cloud privato o locale con un controller di dominio di AD DS. Un server che esegue lo strumento Azure AD Connect consente di sincronizzare l'elenco di nomi dell'account con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-p112">Figure 4 shows an on-premises or private cloud datacenter with an AD DS domain controller. A server running the Azure AD Connect tool synchronizes the list of account names with Azure AD.</span></span>
  
<span data-ttu-id="113dd-186">Con questa opzione:</span><span class="sxs-lookup"><span data-stu-id="113dd-186">With this option:</span></span>
  
- <span data-ttu-id="113dd-p113">Gli account utente vengono sincronizzati da AD DS locale (o da un altro provider di identità) al tenant di Azure AD. La directory locale rimane l'origine autorevole per gli account e consente all'utente di gestire le modifiche di tutti gli account.</span><span class="sxs-lookup"><span data-stu-id="113dd-p113">User accounts are synchronized from your on-premises AD DS (or other identity provider) to your Azure AD tenant. The on-premises directory remains the authoritative source for accounts and you manage all account changes from there.</span></span>
    
- <span data-ttu-id="113dd-189">Azure AD esegue tutte le autenticazioni per i servizi basati su SaaS Microsoft e le applicazioni PaaS di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-189">Azure AD performs all authentication for Microsoft SaaS-based services and Azure PaaS applications.</span></span>
    
- <span data-ttu-id="113dd-190">È inoltre possibile configurare la sincronizzazione per più foreste di AD DS.</span><span class="sxs-lookup"><span data-stu-id="113dd-190">You can also configure synchronization for multiple AD DS forests.</span></span>
    
<span data-ttu-id="113dd-191">Con la sincronizzazione delle password:</span><span class="sxs-lookup"><span data-stu-id="113dd-191">With password synchronization:</span></span>
  
- <span data-ttu-id="113dd-192">Agli utenti viene richiesto di immettere una password per accedere ai servizi cloud, che è identica a quella che utilizzano per le risorse locali.</span><span class="sxs-lookup"><span data-stu-id="113dd-192">Users are prompted to enter a password when accessing cloud services, which is the same password that they use for on-premises resources.</span></span>
    
- <span data-ttu-id="113dd-p114">Le password degli utenti non vengono mai inviate come testo non crittografato ad Azure AD. Al contrario, viene utilizzato un hash della password. A livello di crittografia, non è possibile decrittografare o decompilare l'hash della password e ottenere la password come testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="113dd-p114">User passwords are never sent as cleartext to Azure AD. Instead, a hash of the password is used. It is cryptographically impossible to decrypt or reverse-engineer the password hash and obtain the cleartext password.</span></span> 
    
<span data-ttu-id="113dd-196">Con l'autenticazione a più fattori (MFA):</span><span class="sxs-lookup"><span data-stu-id="113dd-196">With multi-factor authentication (MFA):</span></span>
  
- <span data-ttu-id="113dd-197">È possibile usufruire delle caratteristiche di base di MFA offerte con Office 365.</span><span class="sxs-lookup"><span data-stu-id="113dd-197">You can take advantage of basic MFA features offered with Office 365.</span></span>
    
- <span data-ttu-id="113dd-198">Gli sviluppatori di applicazioni PaaS di Azure possono usufruire del servizio di autenticazione a più fattori di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-198">Azure PaaS application developers can take advantage of the Azure Multi-Factor Authentication service.</span></span>
    
<span data-ttu-id="113dd-199">La sincronizzazione delle directory non consente l'integrazione con soluzioni MFA locali.</span><span class="sxs-lookup"><span data-stu-id="113dd-199">Directory synchronization does not provide integration with on-premises MFA solutions.</span></span>
  
### <a name="federation-and-single-sign-on"></a><span data-ttu-id="113dd-200">Federazione e Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="113dd-200">Federation and single sign-on</span></span>

<span data-ttu-id="113dd-201">Questa opzione richiede server e infrastruttura aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="113dd-201">This option requires additional servers and infrastructure.</span></span> 
  
![Server necessari per l'autenticazione federata](images/1e54f0d2-e650-4eb5-957f-4f1d3c44da16.png)
  
 <span data-ttu-id="113dd-203">**Figura 5: server necessari per l'autenticazione federata**</span><span class="sxs-lookup"><span data-stu-id="113dd-203">**Figure 5: Servers needed for federated authentication**</span></span>
  
<span data-ttu-id="113dd-p115">Nella figura 5 viene illustrato l'insieme di componenti per l'autenticazione federata. Azure AD contatta un proxy applicazione Web, che inoltra la richiesta di autenticazione a un server di Active Directory Federation Services (AD FS), che a sua volta inoltra la richiesta a un controller di dominio di AD DS per la valutazione e la risposta. Un server che esegue lo strumento Azure AD Connect consente di sincronizzare l'elenco di nomi dell'account da AD DS ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-p115">Figure 5 shows the set of components for federated authentication. Azure AD contacts a web application proxy, which forwards the authentication request to an Active Directory Federation Services (AD FS) server, which forwards the request to an AD DS domain controller for evaluation and response. A server running the Azure AD Connect tool synchronizes the list of account names from AD DS to Azure AD.</span></span>
  
<span data-ttu-id="113dd-207">La federazione fornisce le seguenti funzionalità aziendali aggiuntive:</span><span class="sxs-lookup"><span data-stu-id="113dd-207">Federation provides these additional enterprise capabilities:</span></span>
  
- <span data-ttu-id="113dd-208">Tutte le richieste di autenticazione inviate ad Azure AD vengono inoltrate ed eseguite rispetto al provider di identità locale mediante AD FS.</span><span class="sxs-lookup"><span data-stu-id="113dd-208">All authentication requests sent to Azure AD are forwarded to and performed against the on-premises identity provider through AD FS.</span></span>
    
- <span data-ttu-id="113dd-209">Funziona con i provider di identità non Microsoft.</span><span class="sxs-lookup"><span data-stu-id="113dd-209">Works with non-Microsoft identity providers.</span></span>
    
- <span data-ttu-id="113dd-210">La sincronizzazione degli hash delle password può agire come backup delle informazioni di accesso per l'accesso federato (ad esempio, se l'autenticazione federata ha esito negativo).</span><span class="sxs-lookup"><span data-stu-id="113dd-210">Password hash synchronization can act as a sign-in backup for federated sign-in (for example, if the federated authentication fails).</span></span>
    
<span data-ttu-id="113dd-211">Usare la federazione nei seguenti casi:</span><span class="sxs-lookup"><span data-stu-id="113dd-211">Use federation if:</span></span>
  
- <span data-ttu-id="113dd-p116">Single Sign-On è obbligatorio. Con Single Sign-On, agli utenti non viene richiesto di immettere le credenziali (nome utente o password) per accedere a un servizio cloud.</span><span class="sxs-lookup"><span data-stu-id="113dd-p116">Single sign-on is required. With single sign-on, users are not prompted to enter any credentials (user name or password), when accessing a cloud service.</span></span>
    
- <span data-ttu-id="113dd-214">AD FS è già stato distribuito.</span><span class="sxs-lookup"><span data-stu-id="113dd-214">AD FS is already deployed.</span></span>
    
- <span data-ttu-id="113dd-215">Si utilizza un provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="113dd-215">You use a third-party identity provider.</span></span>
    
- <span data-ttu-id="113dd-216">Si utilizza Forefront Identity Manager 2010 R2 (non supporta la sincronizzazione degli hash delle password).</span><span class="sxs-lookup"><span data-stu-id="113dd-216">You use Forefront Identity Manager 2010 R2 (does not support password hash synchronization).</span></span>
    
- <span data-ttu-id="113dd-217">Si dispone di una smart card integrata in locale o un'altra soluzione MFA.</span><span class="sxs-lookup"><span data-stu-id="113dd-217">You have an on-premises integrated smart card or other MFA solution.</span></span>
    
- <span data-ttu-id="113dd-218">Si necessita di controllare l'accesso e/o di disabilitare account.</span><span class="sxs-lookup"><span data-stu-id="113dd-218">You require sign-in audit and/or disablement of accounts.</span></span>
    
- <span data-ttu-id="113dd-219">L'organizzazione richiede restrizioni client di accesso in base al percorso di rete o alle ore lavorative.</span><span class="sxs-lookup"><span data-stu-id="113dd-219">Your organization requires client sign-in restrictions by network location or work hours.</span></span>
    
- <span data-ttu-id="113dd-220">È necessaria la conformità con Federal Information Processing Standards (FIPS).</span><span class="sxs-lookup"><span data-stu-id="113dd-220">You must comply with Federal Information Processing Standards (FIPS).</span></span>
    
<span data-ttu-id="113dd-221">L'autenticazione federata richiede un investimento maggiore in infrastrutture locali.</span><span class="sxs-lookup"><span data-stu-id="113dd-221">Federated authentication requires a greater investment in infrastructure on-premises.</span></span>
  
- <span data-ttu-id="113dd-p117">I server locali devono essere accessibili da Internet mediante un firewall aziendale. È consigliabile utilizzare i server Proxy applicazione Web distribuiti nella rete perimetrale.</span><span class="sxs-lookup"><span data-stu-id="113dd-p117">The on-premises servers must be Internet-accessible through a corporate firewall. Microsoft recommends the use of Web Application Proxy servers deployed in your perimeter network.</span></span>
    
- <span data-ttu-id="113dd-224">Richiede componenti hardware, licenze e operazioni per server AD FS, proxy AD FS o server proxy di applicazione Web, firewall e servizi di bilanciamento del carico.</span><span class="sxs-lookup"><span data-stu-id="113dd-224">Requires hardware, licenses, and operations for AD FS servers, AD FS proxy or Web Application Proxy servers, firewalls, and load balancers.</span></span> 
    
- <span data-ttu-id="113dd-225">Disponibilità e prestazioni sono importanti per garantire agli utenti l’accesso a Office 365 e ad altre applicazioni cloud.</span><span class="sxs-lookup"><span data-stu-id="113dd-225">Availability and performance are important to ensure users can access Office 365 and other cloud applications.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="113dd-226">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="113dd-226">More Information</span></span>

- [<span data-ttu-id="113dd-227">La sincronizzazione della directory con Office 365 è facile</span><span class="sxs-lookup"><span data-stu-id="113dd-227">Synchronizing your directory with Office 365 is easy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524281)
    
- [<span data-ttu-id="113dd-228">Preparazione per il provisioning degli utenti verso Office 365 tramite la sincronizzazione di directory</span><span class="sxs-lookup"><span data-stu-id="113dd-228">Prepare to provision users through directory synchronization to Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524284)
    
- [<span data-ttu-id="113dd-229">Autenticazione a più fattori per Office 365</span><span class="sxs-lookup"><span data-stu-id="113dd-229">Multi-Factor Authentication for Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=392012)
    
- [<span data-ttu-id="113dd-230">Multi-Factor Authentication di Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-230">Azure Multi-Factor Authentication</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524285)
    
- [<span data-ttu-id="113dd-231">TechEd 2014: Integrazione directory: creazione di una directory con Active Directory e Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="113dd-231">TechEd 2014: Directory Integration: Creating One Directory with Active Directory and Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524286)
    
## <a name="extend-ad-ds-to-azure"></a><span data-ttu-id="113dd-232">estensione di AD DS ad Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-232">Extend AD DS to Azure</span></span>

<span data-ttu-id="113dd-233">L'estensione di AD DS ad Azure è il primo passaggio per il supporto delle applicazioni line-of-business in esecuzione sulle macchine virtuali nei servizi infrastruttura di Azure, che fornisce:</span><span class="sxs-lookup"><span data-stu-id="113dd-233">Extending AD DS to Azure is the first step to support line-of-business applications running on virtual machines in Azure infrastructure services, which provides:</span></span>
  
- <span data-ttu-id="113dd-234">Supporto per le soluzioni basate su cloud che richiedono l'autenticazione Kerberos o NTLM, oppure le macchine virtuali aggiunte a un dominio di AD DS.</span><span class="sxs-lookup"><span data-stu-id="113dd-234">Support for cloud-based solutions that require NTLM or Kerberos authentication, or AD DS domain-joined virtual machines.</span></span>
    
- <span data-ttu-id="113dd-235">Potenziale integrazione aggiuntiva per servizi cloud e applicazioni e può essere aggiunto in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="113dd-235">Additional integration potential for cloud services and applications and can be added at any time.</span></span>
    
![Estensione di Servizi di dominio Active Directory a una rete virtuale di Azure](images/9fe2e27d-7fc8-441a-a694-1db4b9f6d03f.png)
  
 <span data-ttu-id="113dd-237">**Figura 6: estensione di Servizi di dominio Active Directory a una rete virtuale di Azure**</span><span class="sxs-lookup"><span data-stu-id="113dd-237">**Figure 6: Extending AD DS to an Azure virtual network**</span></span>
  
<span data-ttu-id="113dd-p118">Nella figura 6 viene illustrato un datacenter del cloud privato o locale con AD DS connesso a una rete virtuale di Azure con una connessione VPN da sito a sito o ExpressRoute. La rete virtuale di Azure contiene i server per un'applicazione line-of-business e il relativo insieme di controller di dominio di AD DS. Questa configurazione è una distribuzione ibrida di AD DS in locale e nei servizi infrastruttura di Azure. Richiede:</span><span class="sxs-lookup"><span data-stu-id="113dd-p118">Figure 6 shows an on-premises or private cloud datacenter with AD DS connected to an Azure virtual network with a site-to-site VPN or ExpressRoute connection. The Azure virtual network contains servers for a line-of-business application and its own set of AD DS domain controllers. This configuration is a hybrid deployment of AD DS on-premises and in Azure infrastructure services. It requires:</span></span>
  
- <span data-ttu-id="113dd-242">Una rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-242">An Azure virtual network.</span></span>
    
- <span data-ttu-id="113dd-243">Una connessione tra un router o un dispositivo VPN (Virtual Private Network) locale e un gateway VPN di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-243">A connection between an on-premises virtual private network (VPN) device or router and an Azure VPN gateway.</span></span>
    
- <span data-ttu-id="113dd-244">L'utilizzo di una porzione dello spazio di indirizzi IP locali per le macchine virtuali nella rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="113dd-244">Using a portion of your on-premises IP address space for the virtual machines in the virtual network.</span></span>
    
- <span data-ttu-id="113dd-245">La distribuzione di uno o più controller di dominio nella rete virtuale designata come server di catalogo globale (riduce il traffico in uscita attraverso la connessione VPN).</span><span class="sxs-lookup"><span data-stu-id="113dd-245">Deploying one or more domain controllers in the virtual network designated as global catalog servers (reduces egress traffic across the VPN connection).</span></span>
    
<span data-ttu-id="113dd-246">Questa architettura di identità supporta un insieme di soluzioni e applicazioni diverso rispetto a quello della sincronizzazione con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-246">This identity architecture supports a different set of solutions and applications compared to synchronization with Azure AD.</span></span>
  
### <a name="on-premises-to-azure-connection-options"></a><span data-ttu-id="113dd-247">Opzioni di connessione dalla rete locale a quella di Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-247">On-premises to Azure connection options</span></span>

<span data-ttu-id="113dd-248">Per connettere la rete locale a una rete virtuale di Azure, è possibile utilizzare:</span><span class="sxs-lookup"><span data-stu-id="113dd-248">To connect your on-premises network to an Azure virtual network, you can use:</span></span>
  
- <span data-ttu-id="113dd-249">Una connessione VPN da sito a sito, che consente di connettere da 1 a 10 siti (comprese le altre reti virtuali di Azure) a una singola rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-249">A site-to-site VPN connection, which can connect 1-10 sites (including other Azure virtual networks) to a single Azure virtual network.</span></span>
    
- <span data-ttu-id="113dd-p119">ExpressRoute, un collegamento WAN sicuro e privato ad Azure mediante un provider di servizi di datacenter e di rete partner. Le connessioni ExpressRoute possono offrire una maggiore affidabilità, una larghezza di banda superiore e latenze inferiori.</span><span class="sxs-lookup"><span data-stu-id="113dd-p119">ExpressRoute, a private, secure WAN link to Azure through a partner network and datacenter services provider. ExpressRoute connections can offer increased reliability, higher bandwidth, and lower latencies.</span></span>
    
### <a name="more-information"></a><span data-ttu-id="113dd-252">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="113dd-252">More Information</span></span>

- [<span data-ttu-id="113dd-253">Connessione cross-premise per reti virtuali</span><span class="sxs-lookup"><span data-stu-id="113dd-253">Cross-premises connectivity for virtual networks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524293)
    
- [<span data-ttu-id="113dd-254">Panoramica tecnica relativa a ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="113dd-254">ExpressRoute Technical Overview</span></span>](https://go.microsoft.com/fwlink/?LinkID=392081)
    
- [<span data-ttu-id="113dd-255">Linee guida per la distribuzione di Windows Server Active Directory in macchine virtuali di Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-255">Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524295)
    
## <a name="integrate-your-applications-with-cloud-identities"></a><span data-ttu-id="113dd-256">Integrare le applicazioni con identità cloud</span><span class="sxs-lookup"><span data-stu-id="113dd-256">Integrate your applications with cloud identities</span></span>

<span data-ttu-id="113dd-p120">Durante la progettazione e lo sviluppo delle applicazioni che vengono eseguite nel cloud, l'obiettivo deve essere la coerenza dell'esperienza utente in merito al processo di autenticazione, compreso l'insieme di credenziali necessarie. Ad esempio, quando si utilizzano le credenziali di Windows, che si tratti di Azure AD o di un'estensione di AD DS, occorre accertarsi che gli utenti possano eseguire l'autenticazione rapidamente e concentrarsi sulle proprie attività.</span><span class="sxs-lookup"><span data-stu-id="113dd-p120">When designing and developing applications that run in the cloud, you should aim for consistency of the user experience for the authentication process, including the set of required credentials. For example, when using Windows credentials, whether against Azure AD or an extended AD DS, ensure that users can quickly authenticate and focus on their tasks.</span></span>
  
![Integrare le applicazioni con identità cloud](images/1e6304b0-fa15-4f80-a3b4-7507a28808ae.png)
  
 <span data-ttu-id="113dd-260">**Figura 7: integrare le applicazioni con identità cloud**</span><span class="sxs-lookup"><span data-stu-id="113dd-260">**Figure 7: Integrate your applications with cloud identities**</span></span>
  
<span data-ttu-id="113dd-261">Nella figura 7 vengono illustrate tre opzioni per l'integrazione dell'applicazione con identità cloud.</span><span class="sxs-lookup"><span data-stu-id="113dd-261">Figure 7 shows three options for integrating your application with cloud identities.</span></span>
  
1. <span data-ttu-id="113dd-262">Registrare le applicazioni ospitate nel cloud con Azure AD.</span><span class="sxs-lookup"><span data-stu-id="113dd-262">Register your cloud-hosted applications with Azure AD.</span></span>
    
    <span data-ttu-id="113dd-p121">Vedere l'articolo MSDN [Integrazione di applicazioni con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). Ciò consente di utilizzare Azure AD per autenticare l'accesso all'applicazione PaaS, oltre a permettere a utenti o amministratori di autorizzare l'applicazione ad accedere ai contenuti per conto di altri servizi cloud, come Office 365. Ulteriori informazioni ed esempi di codice sono disponibili nell'articolo MSDN [Scenari di autenticazione per Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span><span class="sxs-lookup"><span data-stu-id="113dd-p121">See the MSDN article [Integrating Applications with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524303). This lets you use Azure AD to authenticate access to your PaaS application, as well as allowing users or administrators to grant rights to your application to access content on their behalf from other cloud services, such as Office 365. More details and code samples can be found in the MSDN article [Authentication Scenarios for Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524304).</span></span> 
    
2. <span data-ttu-id="113dd-266">Le applicazioni che richiedono l'autenticazione programmatica per avere accesso a un'applicazione protetta da AD DS, AD FS in Windows Server 2012 R2 o Azure AD possono utilizzare:</span><span class="sxs-lookup"><span data-stu-id="113dd-266">Applications that require programmatic authentication to gain access to an application secured by AD SD, AD FS on Windows Server 2012 R2, or Azure AD can use:</span></span>
    
  - <span data-ttu-id="113dd-267">[API Graph di Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span><span class="sxs-lookup"><span data-stu-id="113dd-267">The [Azure AD Graph API](https://go.microsoft.com/fwlink/p/?LinkId=524305)</span></span>
    
  - [<span data-ttu-id="113dd-268">Active Directory Authentication Library (ADAL)</span><span class="sxs-lookup"><span data-stu-id="113dd-268">Active Directory Authentication Library (ADAL)</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=524297)
    
    <span data-ttu-id="113dd-p122">L'API Graph di Azure AD supporta l'autorizzazione OAuth e la connessione OpenID. Funziona anche con le applicazioni PaaS.</span><span class="sxs-lookup"><span data-stu-id="113dd-p122">The Azure AD Graph API supports OAuth and OpenID Connect. It also works with PaaS applications.</span></span>
    
3. <span data-ttu-id="113dd-p123">Configurare le applicazioni locali o le applicazioni line-of-business in esecuzione su macchine virtuali in una rete virtuale di Azure per utilizzare direttamente l'autenticazione di Windows (NTLM o Kerberos). Si tratta dell'esperienza utente migliore e richiede la configurazione minima per gli sviluppatori di applicazioni server.</span><span class="sxs-lookup"><span data-stu-id="113dd-p123">Configure on-premises applications or line-of-business applications running on virtual machines in an Azure virtual network to use Windows authentication (NTLM or Kerberos) directly. This is the best experience for users and requires the least configuration for server application developers.</span></span>
    
### <a name="application-integration-example"></a><span data-ttu-id="113dd-273">Esempio di integrazione di applicazioni</span><span class="sxs-lookup"><span data-stu-id="113dd-273">Application integration example</span></span>

<span data-ttu-id="113dd-p124">Un'organizzazione compila un'applicazione ASP.NET che espone un endpoint REST in cui altre applicazioni possono ottenere i dati sulle vendite più recenti. L'accesso a tale endpoint REST è protetto con Azure AD. Le applicazioni devono fornire le credenziali per essere autenticate da Azure AD prima che l'applicazione ASP.NET invii i dati richiesti. Gli altri sviluppatori dell'organizzazione possono quindi scrivere le proprie applicazioni che utilizzano i dati sulle vendite dall'endpoint REST.</span><span class="sxs-lookup"><span data-stu-id="113dd-p124">An organization builds an ASP.NET application that exposes a REST endpoint where other applications can obtain the latest sales data. Access to that REST endpoint is secured with Azure AD. Applications must provide credentials that can be authenticated by Azure AD before the ASP.NET application sends the requested data. Other developers in the organization can then write their own applications that use the sales data from the REST endpoint.</span></span>
  
<span data-ttu-id="113dd-p125">Per eseguire l'autenticazione di Azure AD e recuperare i dati, ADAL gestisce il processo di autenticazione dell'utente e trasmette il token di accesso all'applicazione, affinché venga usato per accedere ai dati sulle vendite. ADAL supera gran parte della complessità dell'acquisizione e dell'analisi dei token, dei flussi OAuth e di altri elementi. ADAL è un'altra soluzione tecnologica in continua evoluzione, quindi gli sviluppatori devono cercare la versione più recente su NuGet.</span><span class="sxs-lookup"><span data-stu-id="113dd-p125">To authenticate to Azure AD and retrieve data, ADAL manages the user authentication process and hands the access token off to the application so it can be used to gain access to the sales data. ADAL abstracts out much of the complexity of obtaining and parsing tokens, OAuth flows, and other elements. ADAL is another technology solution that is rapidly changing so developers should look for the latest version on NuGet.</span></span>
  
## <a name="deploying-directory-components-in-azure"></a><span data-ttu-id="113dd-281">Distribuzione dei componenti della directory ad Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-281">Deploying directory components in Azure</span></span>

<span data-ttu-id="113dd-p126">È possibile distribuire i componenti della directory, come i server per la sincronizzazione delle password o per l'autenticazione federata, in una rete virtuale di Azure anziché in un datacenter locale. Valutarne i vantaggi, specialmente se si ha intenzione di estendere AD DS ad Azure.</span><span class="sxs-lookup"><span data-stu-id="113dd-p126">You can deploy directory components, such as servers for password synchronization or federated authentication, in an Azure virtual network rather than an on-premises datacenter. Consider its benefits, especially if you plan to extend AD DS into Azure.</span></span>
  
<span data-ttu-id="113dd-284">Di seguito sono riportati i componenti della directory che è possibile inserire in una rete virtuale di Azure:</span><span class="sxs-lookup"><span data-stu-id="113dd-284">Here are the directory components that can be put in an Azure virtual network:</span></span>
  
- <span data-ttu-id="113dd-285">	Strumento Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="113dd-285">Azure AD Connect tool</span></span>
    
- <span data-ttu-id="113dd-286">Componenti di autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="113dd-286">Federated authentication components</span></span>
    
- <span data-ttu-id="113dd-287">Ambiente AD DS autonomo</span><span class="sxs-lookup"><span data-stu-id="113dd-287">A standalone AD DS environment</span></span>
    
### <a name="ad-connect-tool"></a><span data-ttu-id="113dd-288">Strumento AD Connect</span><span class="sxs-lookup"><span data-stu-id="113dd-288">AD Connect tool</span></span>

<span data-ttu-id="113dd-p127">Lo strumento Azure AD Connect può essere ospitato nel cloud in una rete virtuale di Azure. Prendere in considerazione i vantaggi della distribuzione di questo carico di lavoro in Azure:</span><span class="sxs-lookup"><span data-stu-id="113dd-p127">The Azure AD Connect tool can be hosted in the cloud on an Azure virtual network. Consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="113dd-291">Possibilità di provisioning più veloce e costi delle operazioni più bassi</span><span class="sxs-lookup"><span data-stu-id="113dd-291">Potentially faster provisioning and lower cost of operations</span></span>
    
- <span data-ttu-id="113dd-292">Disponibilità migliorata</span><span class="sxs-lookup"><span data-stu-id="113dd-292">Increased availability</span></span>
    
![Strumento AD Connect in esecuzione nei servizi infrastruttura di Azure](images/97593481-e06a-4e34-b8b5-cc63acb5f9f1.png)
  
 <span data-ttu-id="113dd-294">**Figura 8: strumento AD Connect in esecuzione in Azure**</span><span class="sxs-lookup"><span data-stu-id="113dd-294">**Figure 8: The AD Connect tool running in Azure**</span></span>
  
<span data-ttu-id="113dd-p128">Nella figura 8 viene illustrato lo strumento AD Connect in esecuzione su una macchina virtuale in una rete virtuale di Azure, che esegue una query in un controller di dominio AD DS locale per ottenere le modifiche apportate all'account e quindi invia tali modifiche a Office 365. Questa soluzione funziona con:</span><span class="sxs-lookup"><span data-stu-id="113dd-p128">Figure 8 shows the AD Connect tool running on a virtual machine in an Azure virtual network, which queries an on-premises AD DS domain controller for account changes and then sends those changes to Office 365. This solution works with:</span></span>
  
- <span data-ttu-id="113dd-297">Servizi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="113dd-297">Office 365 services.</span></span>
    
- <span data-ttu-id="113dd-298">Applicazioni PaaS di Azure disponibili su Internet.</span><span class="sxs-lookup"><span data-stu-id="113dd-298">Azure PaaS applications that are available over the Internet.</span></span>
    
- <span data-ttu-id="113dd-299">Applicazioni line-of-business in Azure disponibili da ambienti locali mediante la connessione VPN da sito a sito o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="113dd-299">Line-of-business applications in Azure that are available from on-premises environments through the site-to-site VPN or ExpressRoute connection.</span></span>
    
<span data-ttu-id="113dd-300">Per ulteriori informazioni, vedere [Integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="113dd-300">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="federated-authentication-infrastructure"></a><span data-ttu-id="113dd-301">Infrastruttura di autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="113dd-301">Federated authentication infrastructure</span></span>

<span data-ttu-id="113dd-302">Se non è stato ancora distribuito AD FS locale, valutare i vantaggi della distribuzione del carico di lavoro in Azure:</span><span class="sxs-lookup"><span data-stu-id="113dd-302">If you haven't already deployed AD FS on-premises, consider these benefits of deploying this workload to Azure:</span></span>
  
- <span data-ttu-id="113dd-303">Garantisce autonomia per l'autenticazione ai servizi cloud (no dipendenze locali)</span><span class="sxs-lookup"><span data-stu-id="113dd-303">Provides autonomy for authentication to cloud services (no on-premises dependencies)</span></span>
    
- <span data-ttu-id="113dd-304">Riduce server e strumenti disponibili in locale</span><span class="sxs-lookup"><span data-stu-id="113dd-304">Reduces servers and tools hosted on-premises</span></span>
    
- <span data-ttu-id="113dd-305">Utilizza un gateway VPN da sito a sito su un cluster di failover a due nodi per la connessione ad Azure (novità)</span><span class="sxs-lookup"><span data-stu-id="113dd-305">Uses a site-to-site VPN gateway on a two-node failover cluster to connect to Azure (new)</span></span>
    
- <span data-ttu-id="113dd-306">Usa ACL per permettere ai server proxy di applicazione Web di comunicare solo con AD FS, non direttamente con controller di dominio o altri server</span><span class="sxs-lookup"><span data-stu-id="113dd-306">Uses ACLs to ensure that Web Application Proxy servers can only communicate with AD FS, not domain controllers or other servers directly</span></span>
    
![Distribuzione dell'infrastruttura di autenticazione federata in Azure](images/4e023dd4-b9fb-403a-a8eb-069b56d7a65e.png)
  
 <span data-ttu-id="113dd-308">**Figura 9: distribuzione dell'infrastruttura di autenticazione federata in Azure**</span><span class="sxs-lookup"><span data-stu-id="113dd-308">**Figure 9: Deploying your federated authentication infrastructure in Azure**</span></span>
  
<span data-ttu-id="113dd-p129">Nella figura 9 viene illustrato un insieme di controller di dominio locali che replicano le informazioni di AD DS con un insieme di controller di dominio in una rete virtuale di Azure. Lo strumento Azure AD Connect in esecuzione su un server nella rete virtuale di Azure esegue una query sui controller di dominio locali per ottenere le modifiche e quindi invia tali modifiche ad Azure AD. Le richieste di autenticazione in ingresso per Azure AD dai servizi Microsoft SaaS, dalle applicazioni PaaS di Azure e da altre applicazioni cloud vengono inoltrate a un bilanciamento del carico esterno, che inoltra la richiesta a un insieme di server proxy di applicazione Web. I server proxy di applicazione Web inoltrano la richiesta a un bilanciamento del carico interno, che inoltra la richiesta a un insieme di server AD FS. I server AD FS inoltrano quindi la richiesta a un controller di dominio per convalidare le credenziali inviate.</span><span class="sxs-lookup"><span data-stu-id="113dd-p129">Figure 9 shows a set of on-premises domain controllers replicating AD DS information with a set of domain controllers in an Azure virtual network. The Azure AD Connect tool running on a server in the Azure virtual network queries the local domain controllers for changes and then sends those changes to Azure AD. Incoming authentication requests to Azure AD from Microsoft SaaS services, Azure PaaS applications, and other cloud applications are forwarded to an external load balancer, which forwards the request to a set of Web Application Proxy servers. The Web Application Proxy servers forward the request to an internal load balancer, which forwards the request to a set of AD FS servers. The AD FS servers then forward the request to a domain controller to validate the send credentials.</span></span>
  
 <span data-ttu-id="113dd-314">Questa soluzione funziona con:</span><span class="sxs-lookup"><span data-stu-id="113dd-314">This solution works with:</span></span>
  
- <span data-ttu-id="113dd-315">Applicazioni che richiedono Kerberos</span><span class="sxs-lookup"><span data-stu-id="113dd-315">Applications that require Kerberos</span></span>
    
- <span data-ttu-id="113dd-316">Tutti i servizi SaaS di Microsoft</span><span class="sxs-lookup"><span data-stu-id="113dd-316">All of Microsoft's SaaS services</span></span>
    
- <span data-ttu-id="113dd-317">Applicazioni in Azure per Internet</span><span class="sxs-lookup"><span data-stu-id="113dd-317">Applications in Azure that are Internet-facing</span></span>
    
- <span data-ttu-id="113dd-318">Applicazioni in IaaS o PaaS di Azure che richiedono l'autenticazione con l'insieme di account nei servizi di dominio AD DS dell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="113dd-318">Applications in Azure IaaS or PaaS that require authentication with the set of accounts in your organization's AD DS</span></span>
    
<span data-ttu-id="113dd-319">Per ulteriori informazioni, vedere [Integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="113dd-319">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
### <a name="standalone-ad-ds-environment-in-an-azure-virtual-network"></a><span data-ttu-id="113dd-320">Ambiente AD DS autonomo in una rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="113dd-320">Standalone AD DS environment in an Azure virtual network</span></span>

<span data-ttu-id="113dd-p130">Non è sempre necessario integrare un'applicazione cloud con il proprio ambiente locale. Ad esempio, un dominio AD DS autonomo in una rete virtuale di Azure supporta le applicazioni pubbliche, come i siti Internet.</span><span class="sxs-lookup"><span data-stu-id="113dd-p130">You don't always need to integrate a cloud application with your on-premises environment. For example, a standalone AD DS domain in an Azure virtual network supports applications that are public-facing, such as Internet sites.</span></span>
  
![Ambiente di Servizi di dominio Active Directory autonomo per un'applicazione basata su server](images/98c7349f-535d-4c9b-8de4-e580f6d573d4.png)
  
 <span data-ttu-id="113dd-324">**Figura 10: ambiente AD DS autonomo per un'applicazione basata su server**</span><span class="sxs-lookup"><span data-stu-id="113dd-324">**Figure 10: A standalone AD DS environment for a server-based application**</span></span>
  
<span data-ttu-id="113dd-p131">Nella figura 10 viene illustrata una rete virtuale di Azure che ospita un insieme di server AD DS, fornendo i servizi di AD DS e DNS, con un insieme di server che ospitano un'applicazione. Questa soluzione funziona con:</span><span class="sxs-lookup"><span data-stu-id="113dd-p131">Figure 10 shows an Azure virtual network hosting a set of AD DS servers, providing both AD DS and DNS services, with a set of servers that host an application. This solution works with:</span></span>
  
- <span data-ttu-id="113dd-327">Applicazioni e siti Web con connessione Internet</span><span class="sxs-lookup"><span data-stu-id="113dd-327">Internet-facing web sites and applications</span></span>
    
- <span data-ttu-id="113dd-328">Applicazioni che richiedono l'autenticazione NTLM o Kerberos</span><span class="sxs-lookup"><span data-stu-id="113dd-328">Applications that require NTLM or Kerberos authentication</span></span>
    
- <span data-ttu-id="113dd-329">Applicazioni in esecuzione su server basati su Windows che richiedono AD DS</span><span class="sxs-lookup"><span data-stu-id="113dd-329">Applications running on Windows-based servers that require AD DS</span></span>
    
<span data-ttu-id="113dd-330">Per ulteriori informazioni, vedere [Integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span><span class="sxs-lookup"><span data-stu-id="113dd-330">For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=524307).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="113dd-331">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="113dd-331">See Also</span></span>

[<span data-ttu-id="113dd-332">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="113dd-332">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="113dd-333">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="113dd-333">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



