---
title: Distribuire Office 365 la sincronizzazione delle Directory in Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: 'Riepilogo: Distribuire Azure Connect Active Directory in una macchina virtuale in Azure per sincronizzare gli account tra la directory locale e il tenant Azure Active Directory la sottoscrizione a Office 365.'
ms.openlocfilehash: 31a72d027acd274c9908a7e63e83843bce9cec71
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="7fe0a-103">Distribuire Office 365 la sincronizzazione delle Directory in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="7fe0a-104">**Riepilogo:** Distribuzione di Azure Active Directory Connect in una macchina virtuale in Azure per sincronizzare gli account tra la directory locale e il tenant Azure Active Directory la sottoscrizione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="7fe0a-p101">Azure Active Directory (AD) Connect (precedentemente noto come lo strumento di sincronizzazione della Directory, strumento di sincronizzazione Directory o lo strumento DirSync.exe) è un'applicazione basata su server installata in un server di dominio per la sincronizzazione di Windows Server in locale Utenti di Active Directory per il tenant Azure Active Directory la sottoscrizione a Office 365. È possibile installare Connetti Azure Active Directory in un server locale, ma è anche possibile installarlo in una macchina virtuale in Azure per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="7fe0a-107">È possibile effettuare il provisioning e configurare i server basati su cloud più rapidamente, in modo da rendere disponibili i servizi in minor tempo.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="7fe0a-108">Azure offre una maggiore disponibilità del sito in tutta semplicità.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="7fe0a-109">È possibile ridurre il numero di server locali dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="7fe0a-p102">Questa soluzione richiede la connettività tra la rete locale e la rete virtuale Azure. Per ulteriori informazioni, vedere [Connect una rete locale a una rete virtuale Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="7fe0a-p103">In questo articolo viene descritta la sincronizzazione di un singolo dominio in una singola foresta. Azure Active Directory Connetti Sincronizza tutti i domini di Windows Server Active Directory nella foresta di Active Directory con Office 365. Se si dispone di più foreste di Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione di Directory a più foreste con Scenario Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7fe0a-p104">Azure Active Directory (Azure Active Directory) utilizzata da Office 365 per il servizio directory. La sottoscrizione di Office 365 include un tenant di Azure Active Directory. In questo tenant anche utilizzabile per la gestione delle identità dell'organizzazione con altri carichi di lavoro cloud, incluse le applicazioni SaaS e altre App in Azure.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="7fe0a-118">Panoramica relativa alla distribuzione della sincronizzazione directory di Office 365 in Azure </span><span class="sxs-lookup"><span data-stu-id="7fe0a-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="7fe0a-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="7fe0a-119"></span></span>

<span data-ttu-id="7fe0a-120">Nel diagramma seguente viene illustrato in esecuzione in una macchina virtuale in Azure (server di sincronizzazione directory) che consente di sincronizzare una foresta di Windows Server Active Directory locale alla sottoscrizione anOffice 365 Azure Connect di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Strumento di Azure AD Connect su una macchina virtuale per sincronizzare account locali nel tenant Azure AD di una sottoscrizione a Office 365 con flusso di traffico](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="7fe0a-p105">Nel diagramma, esistono due reti connesse mediante una connessione VPN o ExpressRoute sito per sito. Esiste una rete locale dove si trovano i controller di dominio Windows Server Active Directory e non esiste una rete virtuale Azure con un server di sincronizzazione delle directory, che corrisponde a una macchina virtuale in esecuzione [Connetti Azure Active Directory](https://www.microsoft.com/download/details.aspx?id=47594). Esistono due flussi principale del traffico proveniente dal server di sincronizzazione delle directory:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="7fe0a-125">Azure AD Connect esegue la query a un controller di dominio nella rete locale per apportare modifiche ad account e password.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="7fe0a-p106">Azure Active Directory Connetti invia le modifiche agli account e password per l'istanza di Azure Active Directory della sottoscrizione a Office 365. Dal momento che il server di sincronizzazione delle directory è una parte estesa della rete locale, le modifiche vengono inviate tramite server proxy di rete locale.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="7fe0a-p107">Questa soluzione viene descritta la sincronizzazione di un singolo dominio Active Directory in una singola foresta di Active Directory. Azure Active Directory Connetti Sincronizza tutti i domini di Active Directory nella foresta di Active Directory con Office 365. Se si dispone di più foreste di Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione di Directory a più foreste con Scenario Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="7fe0a-p108">In entrambi i casi, il traffico generato da Azure Active Directory Connetti in esecuzione nella macchina virtuale Azure viene inoltrato a un gateway in rete virtuale in Azure, che quindi inoltra il traffico tra la connessione a siti VPN o ExpressRoute al dispositivo gateway VPN su la rete locale. L'infrastruttura di routing di rete locale inoltra quindi il traffico alla destinazione, ad esempio un controller di dominio o un server proxy.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="7fe0a-133">La distribuzione di questa soluzione comprende due passaggi principali:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="7fe0a-p109">Creare una rete virtuale Azure e stabilire una connessione VPN da sito alla rete locale. Per ulteriori informazioni, vedere [Connect una rete locale a una rete virtuale Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="7fe0a-p110">Installare [Connetti Azure Active Directory](https://www.microsoft.com/download/details.aspx?id=47594) in un computer aggiunto al dominio virtuale in Azure e quindi sincronizzare locale Windows Server Active Directory per Office 365. Comporta:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="7fe0a-138">Creazione di una macchina virtuale Azure per eseguire Connetti Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="7fe0a-139">Installazione e configurazione di [Azure Active Directory Connetti](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="7fe0a-p111">La configurazione di Azure Active Directory Connect richiede le credenziali dell'account di amministratore di Azure Active Directory e un account di amministratore di Windows Server Active Directory aziendale (nome utente e password). Connetti Azure Active Directory viene eseguito immediatamente e in modo continuativo per sincronizzare la foresta di Windows Server Active Directory locale per Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="7fe0a-142">Prima di distribuire la soluzione nell'ambiente di produzione, utilizzare le istruzioni nella [sincronizzazione delle Directory per l'ambiente di sviluppo e di testing di Office 365](dirsync-for-your-office-365-dev-test-environment.md) per impostare questa configurazione come un modello di prova per dimostrazioni o la sperimentazione.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="7fe0a-143">Al termine della configurazione di Azure AD Connect, questo non salva le credenziali dell'account amministratore dell'organizzazione di Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7fe0a-p112">Questa soluzione viene descritta la sincronizzazione di una singola foresta di Windows Server Active Directory per Office 365. La topologia riportata in questo articolo rappresenta un solo modo per implementare questa soluzione. La topologia dell'organizzazione può variare in base sui requisiti di rete univoco e considerazioni sulla protezione.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="7fe0a-147">Piano per l'hosting di un server di sincronizzazione delle directory per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-147">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="7fe0a-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="7fe0a-148"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="7fe0a-149">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="7fe0a-149">Prerequisites</span></span>

<span data-ttu-id="7fe0a-150">Prima di iniziare, rivedere i prerequisiti relativi alla soluzione:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="7fe0a-151">Esaminare il contenuto correlato pianificazione nella [pianificazione della rete virtuale Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="7fe0a-152">Verificare che siano soddisfatti tutti i [Prerequisiti](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) per la configurazione della rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="7fe0a-p113">Disporre di una sottoscrizione a Office 365 che include la funzionalità di integrazione di Active Directory. Per informazioni sulle sottoscrizioni a Office 365, passare alla [pagina di sottoscrizione Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="7fe0a-155">Eseguire il provisioning di una macchina virtuale Azure che esegue Azure Active Directory Connetti per sincronizzare la foresta di Windows Server Active Directory locale con Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="7fe0a-156">È necessario disporre delle credenziali (nomi e password) per un account di amministratore di Windows Server Active Directory dell'organizzazione e un account di amministratore di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="7fe0a-157">Presupposti per la progettazione dell’architettura della soluzione</span><span class="sxs-lookup"><span data-stu-id="7fe0a-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="7fe0a-158">Di seguito sono riportate le scelte di progettazione effettuate per questa soluzione:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="7fe0a-p114">Questa soluzione utilizza una rete virtuale Azure singola con una connessione VPN del sito per sito. La rete virtuale Azure ospita una singola subnet che contiene un solo server, il server di sincronizzazione directory cui è in esecuzione Connetti Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="7fe0a-161">Nella rete locale, sono disponibili un controller di dominio e alcuni server DNS.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="7fe0a-p115">Connetti Azure Active Directory esegue la sincronizzazione delle password hash invece di single sign-on. Non è necessario distribuire un'infrastruttura di Active Directory Federation Services (ADFS). Per ulteriori informazioni sulla sincronizzazione hash password e le opzioni di single sign-on, vedere [scelta del metodo di autenticazione appropriata per la soluzione di identità ibrido Azure Active Directory](http://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="7fe0a-p116">Quando si distribuisce la soluzione nel proprio ambiente, sono disponibili ulteriori opzioni di progettazione che è possibile considerare. Tale opzioni includono:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="7fe0a-167">Se sono presenti server DNS in una rete virtuale Azure esistente, determinare se si desidera che il server di sincronizzazione directory di utilizzarli per la risoluzione dei nomi anziché i server DNS nella rete locale.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="7fe0a-p117">Se sono presenti i controller di dominio in una rete virtuale Azure esistente, determinare se la configurazione di siti di Active Directory e servizi può essere una migliore opzione. Il server di sincronizzazione directory eseguire una query i controller di dominio nella rete virtuale Azure per le modifiche di account e password anziché i controller di dominio nella rete locale.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="7fe0a-170">Guida di orientamento alla distribuzione</span><span class="sxs-lookup"><span data-stu-id="7fe0a-170">Deployment roadmap</span></span>
<span data-ttu-id="7fe0a-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="7fe0a-171"></span></span>

<span data-ttu-id="7fe0a-172">Distribuzione di Azure Active Directory Connect in una macchina virtuale in Azure è costituito da tre fasi:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="7fe0a-173">Fase 1: Creare e configurare la rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="7fe0a-174">Fase 2: Creare e configurare la macchina virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="7fe0a-175">Fase 3: Installare e configurare Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7fe0a-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="7fe0a-176">Dopo la distribuzione, è necessario assegnare percorsi e licenze ai nuovi account utente in Office 365.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="7fe0a-177">Il [Server di sincronizzazione delle Directory in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contiene tutti i blocchi di Azure PowerShell per creare questa soluzione, i diagrammi in formato di Microsoft PowerPoint e Visio e una cartella di lavoro di Microsoft Excel configurazione generati dal Blocchi di comandi PowerShell Azure personalizzati per le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-177">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="7fe0a-178">Fase 1: Creare e configurare la rete virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="7fe0a-179">Per creare e configurare la rete virtuale Azure, completare [fase 1: preparare la rete locale](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e [fase 2: creare la rete virtuale cross-premise in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) nella distribuzione roadmap di [connettere una rete locale a un Rete virtuale Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="7fe0a-180">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-180">This is your resulting configuration.</span></span>
  
![Fase 1 del server di sincronizzazione delle directory per Office 365 in hosting in Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="7fe0a-182">Nella figura viene illustrata una rete locale connessa a una rete virtuale di Azure tramite una connessione VPN da sito a sito o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="7fe0a-183">Fase 2: Creare e configurare la macchina virtuale di Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="7fe0a-p118">Creare la macchina virtuale in Azure utilizzando le istruzioni [Crea il prima macchina virtuale di Windows nel portale di Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilizzare le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="7fe0a-p119">Nel riquadro di **elementi di base** , selezionare nello stesso gruppo di sottoscrizione, posizione e delle risorse come la rete virtuale. Registrare il nome utente e password in un luogo sicuro. È necessario queste versioni successive per la connessione alla macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="7fe0a-189">Nel riquadro **Selezionare una dimensione di** scegliere le dimensioni **A2 Standard** .</span><span class="sxs-lookup"><span data-stu-id="7fe0a-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="7fe0a-p120">Nel riquadro **Impostazioni** nella sezione **archiviazione** selezionare il tipo di archiviazione **Standard** . Nella sezione **rete** selezionare il nome della rete virtuale e le subnet per ospitare il server di sincronizzazione directory (non GatewaySubnet). Lasciare tutte le altre impostazioni sui rispettivi valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="7fe0a-193">Verificare che il server di sincronizzazione directory utilizza DNS correttamente controllando il servizio DNS interno per assicurarsi che sia stato aggiunto un indirizzo record (a) per la macchina virtuale con il relativo indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-193">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="7fe0a-p121">Utilizzare le istruzioni nella [connessione alla macchina virtuale e accesso](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) per connettersi al server di sincronizzazione directory con una connessione Desktop remoto. Dopo l'accesso, aggiungere la macchina virtuale al dominio di Windows Server Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="7fe0a-p122">Per Azure Active Directory connessione accedere alle risorse Internet, è necessario configurare il server di sincronizzazione delle directory per l'utilizzo proxy server della rete locale. Contattare l'amministratore di rete per individuare eventuali passaggi di configurazione aggiuntive per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="7fe0a-198">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-198">This is your resulting configuration.</span></span>
  
![Fase 2 del server di sincronizzazione delle directory per Office 365 in hosting in Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="7fe0a-200">Nella figura viene illustrata la macchina virtuale server di directory sync in cross-premise reti virtuali Azure.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-200">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="7fe0a-201">Fase 3: Installare e configurare Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="7fe0a-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="7fe0a-202">Completare la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="7fe0a-p123">Connettersi al server di sincronizzazione delle directory mediante una connessione Desktop remoto con un account di dominio di Windows Server Active Directory che dispone dei privilegi di amministratore locale. Vedere [Connect to la macchina virtuale e sign-on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="7fe0a-205">Dal server di sincronizzazione delle directory, aprire l'articolo [configurare la sincronizzazione delle directory in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e seguire le istruzioni per la sincronizzazione della directory con la sincronizzazione delle password hash.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-205">From the directory sync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="7fe0a-p124">Il programma di installazione crea l'account **AAD_xxxxxxxxxxxx** nell'unità organizzativa (OU) gli utenti locali. Non spostare o rimuovere l'account o la sincronizzazione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="7fe0a-208">Questa è la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-208">This is your resulting configuration.</span></span>
  
![Fase 3 del server di sincronizzazione delle directory per Office 365 in hosting in Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="7fe0a-210">In questa figura viene illustrato il server di sincronizzazione directory con Azure Active Directory Connetti in cross-premise reti virtuali Azure.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-210">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="7fe0a-211">Assegnare percorsi e licenze agli utenti in Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe0a-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="7fe0a-p125">Azure AD Connect aggiunge account alla sottoscrizione a Office 365 da Windows Server AD locale, ma per consentire agli utenti di accedere a Office 365 e utilizzarne i servizi, gli account devono essere configurati con un percorso e le licenze. Seguire questi passaggi per aggiungere il percorso e attivare le licenze per gli account utente appropriati:</span><span class="sxs-lookup"><span data-stu-id="7fe0a-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="7fe0a-214">Accedere alla [pagina del portale di Office 365](https://portal.office.com)e quindi fare clic su **amministratore**.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="7fe0a-215">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="7fe0a-216">Nell’elenco degli account utente, selezionare la casella di controllo accanto all'utente che si desidera attivare.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="7fe0a-217">Nella pagina per l'utente, fare clic su **Modifica** per **le licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="7fe0a-218">Nella pagina **dei titoli di prodotto** selezionare un percorso per utente per la **posizione**e quindi abilitare i titoli appropriati per l'utente.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="7fe0a-219">Al termine, fare clic su **Salva**e quindi fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="7fe0a-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="7fe0a-220">Tornare al passaggio 3 per altri utenti.</span><span class="sxs-lookup"><span data-stu-id="7fe0a-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7fe0a-221">Concetti</span><span class="sxs-lookup"><span data-stu-id="7fe0a-221">See Also</span></span>

<span data-ttu-id="7fe0a-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="7fe0a-222"></span></span>

[<span data-ttu-id="7fe0a-223">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="7fe0a-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="7fe0a-224">Connettere una rete locale a una rete virtuale di Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7fe0a-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="7fe0a-225">Connettere il download Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="7fe0a-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="7fe0a-226">Configurare la sincronizzazione delle directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="7fe0a-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="7fe0a-227">Server di sincronizzazione delle directory in Azure Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="7fe0a-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



