---
title: Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Riepilogo: informazioni su come distribuire Azure AD Connect in una macchina virtuale in Azure per eseguire la sincronizzazione degli account tra la directory locale e il tenant di Azure AD della sottoscrizione a Office 365.'
ms.openlocfilehash: c37fd1e31684590b0b564b3fed402b5c33c062a3
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="b62e9-103">Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-103">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>

 <span data-ttu-id="b62e9-104">**Riepilogo:** informazioni su come distribuire Azure AD Connect in una macchina virtuale in Azure per eseguire la sincronizzazione degli account tra la directory locale e il tenant di Azure AD della sottoscrizione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62e9-104">**Summary:** Deploy Azure AD Connect (DirSync) on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="b62e9-p101">Azure Active Directory (AD) Connect (precedentemente noto come Strumento di sincronizzazione della directory, strumento di sincronizzazione directory o strumento DirSync.exe) è un'applicazione basata su server che l'utente installa su un server appartenente a un dominio al fine di sincronizzare gli utenti di Windows Server Active Directory locali nel tenant di Azure Active Directory di una sottoscrizione a Office 365. È possibile installare Azure AD Connect su un server in locale o su una macchina virtuale in Azure per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Windows_Azure for the following reasons:</span></span>
  
- <span data-ttu-id="b62e9-107">È possibile effettuare il provisioning e configurare i server basati su cloud più rapidamente, in modo da rendere disponibili i servizi in minor tempo.</span><span class="sxs-lookup"><span data-stu-id="b62e9-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="b62e9-108">Azure offre una migliore disponibilità del sito con un numero minore di operazioni.</span><span class="sxs-lookup"><span data-stu-id="b62e9-108">Windows_Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="b62e9-109">È possibile ridurre il numero di server locali dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="b62e9-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="b62e9-p102">Questa soluzione richiede che venga stabilita una connessione tra la rete locale e la rete virtuale di Azure. Per ulteriori informazioni, vedere [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="b62e9-p103">In questo articolo viene descritta la sincronizzazione di un singolo dominio in una foresta singola. Azure AD Connect consente di sincronizzare con Office 365 tutti i domini di Windows Server AD nella foresta Active Directory. Se l'utente dispone di più foreste Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione della directory a più foreste con Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Union_Lite_2nd, see  Multi-forest Directory Sync with Single Sign-On Scenario https://go.microsoft.com/fwlink/p/?LinkId=393091 .</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b62e9-p104">Office 365 utilizza Azure Active Directory (Azure AD) come servizio directory. La sottoscrizione a Office 365 include un tenant di Azure AD. È possibile utilizzare il tenant anche per la gestione delle identità dell'organizzazione con altri carichi di lavoro cloud, tra cui altre app e applicazioni SaaS in Azure.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p104">Union_Lite_2nd uses WindowsAzureActiveDirectory (WindowsAzureAD_2nd)  for its directory service. Your Office 365 subscription includes an WindowsAzureAD_2nd tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Windows_Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="b62e9-118">Panoramica relativa alla distribuzione della sincronizzazione directory di Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="b62e9-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="b62e9-119"></span></span>

<span data-ttu-id="b62e9-120">Il diagramma seguente mostra Azure AD Connect in esecuzione in una macchina virtuale in Azure (il server di sincronizzazione della directory) che consente di sincronizzare e inserire nella foresta di Windows Server AD in locale una sottoscrizione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62e9-120">The following diagram shows Azure AD Connect running on a virtual machine in Windows_Azure (the DirSync server) that synchronizes and on-premises Windows Server AD forest to anUnion_Lite_2nd subscription.</span></span>
  
![Strumento di Azure AD Connect su una macchina virtuale per sincronizzare account locali nel tenant Azure AD di una sottoscrizione a Office 365 con flusso di traffico](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="b62e9-p105">Nel diagramma, sono riportate due reti connesse tramite una VPN da sito a sito o una connessione ExpressRoute. Una è la rete locale in cui si trovano i controller di dominio di Windows Server AD, mentre l'altra è una rete virtuale di Azure con un server di sincronizzazione della directory, una macchina virtuale che esegue [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). I flussi di traffico principali provenienti dal server di sincronizzazione della directory sono due:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Windows_Azure virtual network with a DirSync server, a virtual machine running  Azure AD Connect https://www.microsoft.com/download/details.aspx?id=47594 . There are two main traffic flows originating from the DirSync server:</span></span>
  
-  <span data-ttu-id="b62e9-125">Azure AD Connect esegue la query a un controller di dominio nella rete locale per apportare modifiche ad account e password.</span><span class="sxs-lookup"><span data-stu-id="b62e9-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="b62e9-p106">Azure AD Connect invia le modifiche apportate ad account e password all'istanza della sottoscrizione a Office 365. Dal momento che il server di sincronizzazione della directory è in una parte estesa della rete locale in uso, tali modifiche vengono inviate tramite il server proxy della rete locale.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p106">Azure AD Connect sends the changes to accounts and passwords to the WindowsAzureAD_2nd instance of your Union_Lite_2nd subscription. Because the DirSync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network’s proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b62e9-p107">Questa soluzione descrive la sincronizzazione di un singolo dominio di Active Directory, in una foresta Active Directory singola. Azure AD Connect consente di sincronizzare tutti i domini di Active Directory nella foresta Active Directory con Office 365. Se l'utente dispone di più foreste Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione della directory a più foreste con Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p107">This article describes synchronization of a single domain in a single forest. The Azure AD Connect tool synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Union_Lite_2nd, see  Multi-forest Directory Sync with Single Sign-On Scenario http://go.microsoft.com/fwlink/p/?LinkId=393091 .</span></span> 
  
<span data-ttu-id="b62e9-p108">In entrambi i casi, il traffico proveniente da Azure AD Connect in esecuzione sulla macchina virtuale Azure viene inoltrato a un gateway nella rete virtuale di Azure, attraverso la quale il traffico viene inoltrato, tramite la connessione VPN da sito a sito o la connessione ExpressRoute, al dispositivo gateway VPN nella rete locale. A questo punto, l'infrastruttura di routing della rete locale inoltra il traffico alla relativa destinazione, ad esempio verso un controller di dominio o un server proxy.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Windows_Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="b62e9-133">La distribuzione di questa soluzione comprende due passaggi principali:</span><span class="sxs-lookup"><span data-stu-id="b62e9-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="b62e9-p109">Creare una rete virtuale Azure e stabilire una connessione VPN da sito a sito verso la rete locale. Per ulteriori informazioni, vedere [Connettere una rete locale a una rete virtuale di Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p109">Create an Windows_Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see Connect an on-premises network to a Microsoft Azure Virtual Network.</span></span>
    
2. <span data-ttu-id="b62e9-p110">Installare [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) in una macchina virtuale appartenente a un dominio di Azure e sincronizzare Windows Server AD locale con Office 365. Questa operazione implica:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p110">Install  Azure AD Connect https://www.microsoft.com/download/details.aspx?id=47594  on a domain-joined virtual machine in Windows_Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="b62e9-138">La creazione di una macchina virtuale di Azure per l'esecuzione di Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="b62e9-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="b62e9-139">L'installazione e la configurazione di [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="b62e9-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="b62e9-p111">La configurazione di Azure AD Connect richiede le credenziali (nome utente e password) di un account amministratore di Azure AD e di un account amministratore dell'organizzazione Windows Server AD. Azure AD Connect si connette immediatamente e su base continuativa per sincronizzare la foresta di Windows Server AD locale con Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an WindowsAzureAD_2nd administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Union_Lite_2nd.</span></span>
    
<span data-ttu-id="b62e9-142">Prima di distribuire questa soluzione in produzione, utilizzare le istruzioni in [Sincronizzazione della directory per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md) per impostare questa configurazione come modello di verifica, per dimostrazioni o per sperimentazione.</span><span class="sxs-lookup"><span data-stu-id="b62e9-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="b62e9-143">Al termine della configurazione di Azure AD Connect, le credenziali dell'account amministratore dell'organizzazione di Windows Server AD non vengono memorizzate.</span><span class="sxs-lookup"><span data-stu-id="b62e9-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b62e9-p112">Questa soluzione descrive la procedura di sincronizzazione di una singola foresta di Windows Server AD con Office 365. La topologia discussa in questo articolo rappresenta soltanto un modo per implementare la soluzione. La topologia dell'organizzazione potrebbe essere differente in base ai requisiti di rete univoci e alle considerazioni di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p112">This solution describes synchronizing a single Active Directory forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization’s topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="b62e9-147">Piano per ospitare un server di sincronizzazione della directory per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-147">Plan for hosting a DirSync server for Office 365 in Azure</span></span>
<span data-ttu-id="b62e9-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="b62e9-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="b62e9-149">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b62e9-149">Prerequisites</span></span>

<span data-ttu-id="b62e9-150">Prima di iniziare, rivedere i prerequisiti relativi alla soluzione:</span><span class="sxs-lookup"><span data-stu-id="b62e9-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="b62e9-151">Rivedere i contenuti sulla pianificazione correlati in [Pianificare la rete virtuale di Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span><span class="sxs-lookup"><span data-stu-id="b62e9-151">Review the related planning content in [Plan your Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="b62e9-152">Assicurarsi che siano soddisfatti tutti i [prerequisiti](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) relativi alla configurazione della rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b62e9-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="b62e9-p113">Disporre di una sottoscrizione a Office 365 comprensiva della funzionalità di integrazione di Active Directory. Per informazioni sulle sottoscrizioni a Office 365, visitare la [pagina della sottoscrizione a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p113">Have an Union_Lite_2nd subscription that includes the Active Directory integration feature. For information about Union_Lite_2nd subscriptions, go to the  Office 365 subscription page https://go.microsoft.com/fwlink/p/?LinkId=394278 .</span></span>
    
- <span data-ttu-id="b62e9-155">Effettuare il provisioning di una macchina virtuale Azure che esegue Azure AD Connect per sincronizzare la foresta di Windows Server AD locale con Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62e9-155">Provision one WindowsAzureVirtualMachine_1st that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Union_Lite_2nd.</span></span>
    
    <span data-ttu-id="b62e9-156">È necessario disporre delle credenziali (nomi e password) dell'account amministratore dell'organizzazione di Windows Server AD e dell'account amministratore di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b62e9-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Windows_Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="b62e9-157">Presupposti per la progettazione dell’architettura della soluzione</span><span class="sxs-lookup"><span data-stu-id="b62e9-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="b62e9-158">Di seguito sono riportate le scelte di progettazione effettuate per questa soluzione:</span><span class="sxs-lookup"><span data-stu-id="b62e9-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="b62e9-p114">In questa soluzione viene utilizzata una singola rete virtuale Azure con una connessione VPN da sito a sito. La rete virtuale Azure ospita una singola subnet che contiene il server di sincronizzazione della directory, sul quale è in esecuzione Azure AD Connect. </span><span class="sxs-lookup"><span data-stu-id="b62e9-p114">This solution uses a single Windows_Azure virtual network with a site-to-site VPN connection. The Windows_Azure virtual network hosts a single subnet that contains one server, the DirSync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="b62e9-161">Nella rete locale, sono disponibili un controller di dominio e alcuni server DNS.</span><span class="sxs-lookup"><span data-stu-id="b62e9-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="b62e9-p115">Azure AD Connect esegue la sincronizzazione dell'hash delle password al posto del Single Sign-On. Non è necessario distribuire un'infrastruttura AD FS (Active Directory Federation Services). Per ulteriori informazioni sulla sincronizzazione della password e su Single Sign-On, vedere [Scelta del giusto metodo di autenticazione per la soluzione ibrida di gestione delle identità di Azure Active Directory](http://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="b62e9-p116">Quando si distribuisce la soluzione nel proprio ambiente, sono disponibili ulteriori opzioni di progettazione che è possibile considerare. Tale opzioni includono:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="b62e9-167">Se in una rete virtuale Azure esistente sono disponibili server DNS, determinare se si desidera che il server di sincronizzazione della directory li utilizzi per la risoluzione dei nomi al posto dei server DNS presenti nella rete locale.</span><span class="sxs-lookup"><span data-stu-id="b62e9-167">If there are existing DNS servers in an existing Windows_Azure virtual network, determine whether you want your DirSync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="b62e9-p117">Se in una rete virtuale Azure esistente sono disponibili controller di dominio, determinare se la configurazione di siti e servizi di Active Directory rappresenta una migliore opzione. Anziché utilizzare i controller di dominio nella rete locale, il server di sincronizzazione della directory può eseguire query con i controller di dominio nella rete virtuale Azure per cercare le modifiche apportate ad account e password.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p117">If there are domain controllers in an existing Windows_Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory synchronization server can query the domain controllers in the Windows_Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="b62e9-170">Guida di orientamento alla distribuzione</span><span class="sxs-lookup"><span data-stu-id="b62e9-170">Deployment roadmap</span></span>
<span data-ttu-id="b62e9-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="b62e9-171"></span></span>

<span data-ttu-id="b62e9-172">La distribuzione di Azure AD Connect in una macchina virtuale in Azure è costituita da tre fasi:</span><span class="sxs-lookup"><span data-stu-id="b62e9-172">Deploying Azure AD Connect on a virtual machine in  Windows_Azure consists of three phases:</span></span>
  
- <span data-ttu-id="b62e9-173">Fase 1: Creare e configurare la rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="b62e9-174">Fase 2: Creare e configurare la macchina virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="b62e9-175">Fase 3: Installare e configurare Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b62e9-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="b62e9-176">Dopo la distribuzione, è necessario assegnare percorsi e licenze ai nuovi account utente in Office 365.</span><span class="sxs-lookup"><span data-stu-id="b62e9-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="b62e9-177">Il [Server di sincronizzazione delle directory in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contiene tutti i blocchi di Azure PowerShell che consentono di creare questa soluzione, i diagrammi in formato Microsoft PowerPoint e Visio e una cartella di lavoro per la configurazione di Microsoft Excel, che genera i blocchi di comandi di Azure PowerShell personalizzati in base alle impostazioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b62e9-177">The  DirSync Server in Azure Deployment Kit https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded  contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="b62e9-178">Fase 1: Creare e configurare la rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="b62e9-179">Per creare e configurare la rete virtuale di Azure, completare la [Fase 1: Preparare la rete locale](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e la [Fase 2: Creare la rete virtuale cross-premise in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) nella guida di orientamento alla distribuzione di [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="b62e9-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="b62e9-180">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="b62e9-180">This is your resulting configuration.</span></span>
  
![Fase 1 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="b62e9-182">Nella figura viene illustrata una rete locale connessa a una rete virtuale di Azure tramite una connessione VPN da sito a sito o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="b62e9-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="b62e9-183">Fase 2: Creare e configurare la macchina virtuale Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="b62e9-p118">Creare la macchina virtuale in Azure seguendo le istruzioni disponibili nell’articolo [Creare una macchina virtuale Windows con il portale di Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilizzare le seguenti impostazioni:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p118">Create the virtual machine in Windows_Azure using the instructions  Create your first Windows virtual machine in the Azure portal https://go.microsoft.com/fwlink/p/?LinkId=393098 . Use the following settings:</span></span>
  
- <span data-ttu-id="b62e9-p119">Nel riquadro **Impostazioni di base**, selezionare la stessa sottoscrizione, lo stesso percorso e lo stesso gruppo di risorse della rete virtuale. Registrare nome utente e password in un percorso sicuro. Saranno necessari più avanti per connettersi alla macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="b62e9-189">Nel riquadro **Scegli una dimensione**, scegliere la dimensione **A2 Standard**.</span><span class="sxs-lookup"><span data-stu-id="b62e9-189">On the **Choose a size** pane, choose the **A2  Standard** size.</span></span>
    
- <span data-ttu-id="b62e9-p120">Nel riquadro **Impostazioni**, nella sezione **Archiviazione**, selezionare il tipo di disco **Standard**. Nella sezione **Rete**, selezionare il nome della rete virtuale e della subnet per ospitare il server di sincronizzazione della directory (non GatewaySubnet). Lasciare i valori predefiniti per tutte le altre impostazioni.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type and the storage account set up with your virtual network. In the **Network** section, select the name of your virtual network and the subnet for hosting virtual machines (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="b62e9-193">Verificare che il server di sincronizzazione della directory stia utilizzando correttamente il DNS controllando il DNS interno e accertandosi che sia stato aggiunto un record Address (A) per la macchina virtuale con l'indirizzo IP. </span><span class="sxs-lookup"><span data-stu-id="b62e9-193">Verify that your DirSync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="b62e9-p121">Seguire le istruzioni in [Connettersi e accedere alla macchina virtuale](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) per connettersi al server di sincronizzazione della directory con Connessione Desktop remoto. Dopo l'accesso, aggiungere la macchina virtuale al dominio di Windows Server AD locale.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p121">Use the instructions in [Connect to the virtual machine and sign onhttps://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the DirSync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="b62e9-p122">Affinché Azure AD Connect riesca ad accedere alle risorse di Internet, è necessario configurare il server di sincronizzazione della directory per utilizzare il server proxy della rete locale. È necessario contattare l'amministratore di rete per visualizzare eventuali ulteriori procedure di configurazione da eseguire.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p122">For Azure AD Connect to gain access to Internet resources, you must configure the DirSync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="b62e9-198">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="b62e9-198">This is your resulting configuration.</span></span>
  
![Fase 2 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="b62e9-200">Nella figura viene illustrata la macchina virtuale del server di sincronizzazione della directory nella rete virtuale Azure cross-premise.</span><span class="sxs-lookup"><span data-stu-id="b62e9-200">This figure shows the DirSync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="b62e9-201">Fase 3: Installare e configurare Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b62e9-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="b62e9-202">Completare la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="b62e9-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="b62e9-p123">Eseguire la connessione al server di sincronizzazione della directory utilizzando Connessione Desktop remoto con un account di dominio di Windows Server AD dotato dei privilegi di amministratore locale. Vedere [Connettersi e accedere alla macchina virtuale](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="b62e9-p123">Connect to the DirSync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign onhttps://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="b62e9-205">Dal server di sincronizzazione della directory, aprire l'articolo [Configurare la sincronizzazione della directory per Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e seguire le istruzioni per la sincronizzazione della directory con sincronizzazione dell'hash delle password.</span><span class="sxs-lookup"><span data-stu-id="b62e9-205">From the DirSync server, open  the [Set up directory synchronization in Office 365https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="b62e9-p124">Il programma di installazione crea l'account **AAD_xxxxxxxxxxxx** nell'unità organizzativa Utenti locali. Non spostare o eliminare l'account, altrimenti la sincronizzazione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="b62e9-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="b62e9-208">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="b62e9-208">This is your resulting configuration.</span></span>
  
![Fase 3 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="b62e9-210">Nella figura viene illustrato il server di sincronizzazione della directory con Azure AD Connect nella rete virtuale Azure cross-premise.</span><span class="sxs-lookup"><span data-stu-id="b62e9-210">This figure shows the DirSync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="b62e9-211">Assegnare percorsi e licenze agli utenti in Office 365</span><span class="sxs-lookup"><span data-stu-id="b62e9-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="b62e9-p125">Azure AD Connect aggiunge account alla sottoscrizione a Office 365 da Windows Server AD locale, ma per consentire agli utenti di accedere a Office 365 e utilizzarne i servizi, gli account devono essere configurati con un percorso e le licenze. Seguire questi passaggi per aggiungere il percorso e attivare le licenze per gli account utente appropriati:</span><span class="sxs-lookup"><span data-stu-id="b62e9-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="b62e9-214">Accedere alla [pagina del portale di Office 365](https://portal.office.com), quindi fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b62e9-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="b62e9-215">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="b62e9-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="b62e9-216">Nell’elenco degli account utente, selezionare la casella di controllo accanto all'utente che si desidera attivare.</span><span class="sxs-lookup"><span data-stu-id="b62e9-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="b62e9-217">Nella pagina dell'utente, fare clic su **Modifica** per **Licenze di prodotto**.</span><span class="sxs-lookup"><span data-stu-id="b62e9-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="b62e9-218">Nella pagina **Licenze di prodotto**, selezionare un percorso per l'utente per **Percorso**, quindi abilitare le licenze opportune per l'utente.</span><span class="sxs-lookup"><span data-stu-id="b62e9-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the  appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="b62e9-219">Al termine dell'operazione, fare clic su **Salva** e fare clic due volte su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="b62e9-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="b62e9-220">Tornare al passaggio 3 per altri utenti.</span><span class="sxs-lookup"><span data-stu-id="b62e9-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="b62e9-221">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b62e9-221">See Also</span></span>

<span data-ttu-id="b62e9-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="b62e9-222"></span></span>

[<span data-ttu-id="b62e9-223">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="b62e9-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="b62e9-224">Connettere una rete locale a una rete virtuale di Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="b62e9-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="b62e9-225">Scaricare Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b62e9-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="b62e9-226">Configurare la sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="b62e9-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="b62e9-227">Server di sincronizzazione della directory in Azure Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="b62e9-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



