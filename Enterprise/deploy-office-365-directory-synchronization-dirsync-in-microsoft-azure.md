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
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a>Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure

 **Riepilogo:** informazioni su come distribuire Azure AD Connect in una macchina virtuale in Azure per eseguire la sincronizzazione degli account tra la directory locale e il tenant di Azure AD della sottoscrizione a Office 365.
  
Azure Active Directory (AD) Connect (precedentemente noto come Strumento di sincronizzazione della directory, strumento di sincronizzazione directory o strumento DirSync.exe) è un'applicazione basata su server che l'utente installa su un server appartenente a un dominio al fine di sincronizzare gli utenti di Windows Server Active Directory locali nel tenant di Azure Active Directory di una sottoscrizione a Office 365. È possibile installare Azure AD Connect su un server in locale o su una macchina virtuale in Azure per i motivi seguenti:
  
- È possibile effettuare il provisioning e configurare i server basati su cloud più rapidamente, in modo da rendere disponibili i servizi in minor tempo.
    
- Azure offre una migliore disponibilità del sito con un numero minore di operazioni.
    
- È possibile ridurre il numero di server locali dell'organizzazione.
    
> [!IMPORTANT]
> Questa soluzione richiede che venga stabilita una connessione tra la rete locale e la rete virtuale di Azure. Per ulteriori informazioni, vedere [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!IMPORTANT]
> In questo articolo viene descritta la sincronizzazione di un singolo dominio in una foresta singola. Azure AD Connect consente di sincronizzare con Office 365 tutti i domini di Windows Server AD nella foresta Active Directory. Se l'utente dispone di più foreste Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione della directory a più foreste con Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
> [!NOTE]
> Office 365 utilizza Azure Active Directory (Azure AD) come servizio directory. La sottoscrizione a Office 365 include un tenant di Azure AD. È possibile utilizzare il tenant anche per la gestione delle identità dell'organizzazione con altri carichi di lavoro cloud, tra cui altre app e applicazioni SaaS in Azure. 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Panoramica relativa alla distribuzione della sincronizzazione directory di Office 365 in Azure
<a name="Overview"> </a>

Il diagramma seguente mostra Azure AD Connect in esecuzione in una macchina virtuale in Azure (il server di sincronizzazione della directory) che consente di sincronizzare e inserire nella foresta di Windows Server AD in locale una sottoscrizione a Office 365.
  
![Strumento di Azure AD Connect su una macchina virtuale per sincronizzare account locali nel tenant Azure AD di una sottoscrizione a Office 365 con flusso di traffico](images/CP_DirSyncOverview.png)
  
Nel diagramma, sono riportate due reti connesse tramite una VPN da sito a sito o una connessione ExpressRoute. Una è la rete locale in cui si trovano i controller di dominio di Windows Server AD, mentre l'altra è una rete virtuale di Azure con un server di sincronizzazione della directory, una macchina virtuale che esegue [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). I flussi di traffico principali provenienti dal server di sincronizzazione della directory sono due:
  
-  Azure AD Connect esegue la query a un controller di dominio nella rete locale per apportare modifiche ad account e password.
    
-  Azure AD Connect invia le modifiche apportate ad account e password all'istanza della sottoscrizione a Office 365. Dal momento che il server di sincronizzazione della directory è in una parte estesa della rete locale in uso, tali modifiche vengono inviate tramite il server proxy della rete locale.
    
> [!NOTE]
> Questa soluzione descrive la sincronizzazione di un singolo dominio di Active Directory, in una foresta Active Directory singola. Azure AD Connect consente di sincronizzare tutti i domini di Active Directory nella foresta Active Directory con Office 365. Se l'utente dispone di più foreste Active Directory da sincronizzare con Office 365, vedere [Sincronizzazione della directory a più foreste con Single Sign-On](https://go.microsoft.com/fwlink/p/?LinkId=393091). 
  
In entrambi i casi, il traffico proveniente da Azure AD Connect in esecuzione sulla macchina virtuale Azure viene inoltrato a un gateway nella rete virtuale di Azure, attraverso la quale il traffico viene inoltrato, tramite la connessione VPN da sito a sito o la connessione ExpressRoute, al dispositivo gateway VPN nella rete locale. A questo punto, l'infrastruttura di routing della rete locale inoltra il traffico alla relativa destinazione, ad esempio verso un controller di dominio o un server proxy.
  
La distribuzione di questa soluzione comprende due passaggi principali:
  
1. Creare una rete virtuale Azure e stabilire una connessione VPN da sito a sito verso la rete locale. Per ulteriori informazioni, vedere [Connettere una rete locale a una rete virtuale di Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Installare [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) in una macchina virtuale appartenente a un dominio di Azure e sincronizzare Windows Server AD locale con Office 365. Questa operazione implica:
    
    La creazione di una macchina virtuale di Azure per l'esecuzione di Azure AD Connect.
    
    L'installazione e la configurazione di [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    La configurazione di Azure AD Connect richiede le credenziali (nome utente e password) di un account amministratore di Azure AD e di un account amministratore dell'organizzazione Windows Server AD. Azure AD Connect si connette immediatamente e su base continuativa per sincronizzare la foresta di Windows Server AD locale con Office 365.
    
Prima di distribuire questa soluzione in produzione, utilizzare le istruzioni in [Sincronizzazione della directory per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md) per impostare questa configurazione come modello di verifica, per dimostrazioni o per sperimentazione.
  
> [!IMPORTANT]
> Al termine della configurazione di Azure AD Connect, le credenziali dell'account amministratore dell'organizzazione di Windows Server AD non vengono memorizzate. 
  
> [!NOTE]
> Questa soluzione descrive la procedura di sincronizzazione di una singola foresta di Windows Server AD con Office 365. La topologia discussa in questo articolo rappresenta soltanto un modo per implementare la soluzione. La topologia dell'organizzazione potrebbe essere differente in base ai requisiti di rete univoci e alle considerazioni di sicurezza. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a>Piano per ospitare un server di sincronizzazione della directory per Office 365 in Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, rivedere i prerequisiti relativi alla soluzione:
  
- Rivedere i contenuti sulla pianificazione correlati in [Pianificare la rete virtuale di Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).
    
- Assicurarsi che siano soddisfatti tutti i [prerequisiti](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) relativi alla configurazione della rete virtuale di Azure.
    
- Disporre di una sottoscrizione a Office 365 comprensiva della funzionalità di integrazione di Active Directory. Per informazioni sulle sottoscrizioni a Office 365, visitare la [pagina della sottoscrizione a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=394278).
    
- Effettuare il provisioning di una macchina virtuale Azure che esegue Azure AD Connect per sincronizzare la foresta di Windows Server AD locale con Office 365.
    
    È necessario disporre delle credenziali (nomi e password) dell'account amministratore dell'organizzazione di Windows Server AD e dell'account amministratore di Azure Active Directory.
    
### <a name="solution-architecture-design-assumptions"></a>Presupposti per la progettazione dell’architettura della soluzione

Di seguito sono riportate le scelte di progettazione effettuate per questa soluzione:
  
- In questa soluzione viene utilizzata una singola rete virtuale Azure con una connessione VPN da sito a sito. La rete virtuale Azure ospita una singola subnet che contiene il server di sincronizzazione della directory, sul quale è in esecuzione Azure AD Connect.  
    
- Nella rete locale, sono disponibili un controller di dominio e alcuni server DNS.
    
- Azure AD Connect esegue la sincronizzazione dell'hash delle password al posto del Single Sign-On. Non è necessario distribuire un'infrastruttura AD FS (Active Directory Federation Services). Per ulteriori informazioni sulla sincronizzazione della password e su Single Sign-On, vedere [Scelta del giusto metodo di autenticazione per la soluzione ibrida di gestione delle identità di Azure Active Directory](http://aka.ms/auth-options).
    
Quando si distribuisce la soluzione nel proprio ambiente, sono disponibili ulteriori opzioni di progettazione che è possibile considerare. Tale opzioni includono:
  
- Se in una rete virtuale Azure esistente sono disponibili server DNS, determinare se si desidera che il server di sincronizzazione della directory li utilizzi per la risoluzione dei nomi al posto dei server DNS presenti nella rete locale.
    
- Se in una rete virtuale Azure esistente sono disponibili controller di dominio, determinare se la configurazione di siti e servizi di Active Directory rappresenta una migliore opzione. Anziché utilizzare i controller di dominio nella rete locale, il server di sincronizzazione della directory può eseguire query con i controller di dominio nella rete virtuale Azure per cercare le modifiche apportate ad account e password.
    
## <a name="deployment-roadmap"></a>Guida di orientamento alla distribuzione
<a name="DeploymentRoadmap"> </a>

La distribuzione di Azure AD Connect in una macchina virtuale in Azure è costituita da tre fasi:
  
- Fase 1: Creare e configurare la rete virtuale di Azure
    
- Fase 2: Creare e configurare la macchina virtuale di Azure
    
- Fase 3: Installare e configurare Azure AD Connect
    
Dopo la distribuzione, è necessario assegnare percorsi e licenze ai nuovi account utente in Office 365.
  
> [!TIP]
> Il [Server di sincronizzazione delle directory in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contiene tutti i blocchi di Azure PowerShell che consentono di creare questa soluzione, i diagrammi in formato Microsoft PowerPoint e Visio e una cartella di lavoro per la configurazione di Microsoft Excel, che genera i blocchi di comandi di Azure PowerShell personalizzati in base alle impostazioni dell'utente.
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Creare e configurare la rete virtuale di Azure

Per creare e configurare la rete virtuale di Azure, completare la [Fase 1: Preparare la rete locale](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) e la [Fase 2: Creare la rete virtuale cross-premise in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) nella guida di orientamento alla distribuzione di [Connect an on-premises network to a Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Questa è la configurazione risultante.
  
![Fase 1 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Nella figura viene illustrata una rete locale connessa a una rete virtuale di Azure tramite una connessione VPN da sito a sito o ExpressRoute.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Creare e configurare la macchina virtuale Azure

Creare la macchina virtuale in Azure seguendo le istruzioni disponibili nell’articolo [Creare una macchina virtuale Windows con il portale di Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). Utilizzare le seguenti impostazioni:
  
- Nel riquadro **Impostazioni di base**, selezionare la stessa sottoscrizione, lo stesso percorso e lo stesso gruppo di risorse della rete virtuale. Registrare nome utente e password in un percorso sicuro. Saranno necessari più avanti per connettersi alla macchina virtuale.
    
- Nel riquadro **Scegli una dimensione**, scegliere la dimensione **A2 Standard**.
    
- Nel riquadro **Impostazioni**, nella sezione **Archiviazione**, selezionare il tipo di disco **Standard**. Nella sezione **Rete**, selezionare il nome della rete virtuale e della subnet per ospitare il server di sincronizzazione della directory (non GatewaySubnet). Lasciare i valori predefiniti per tutte le altre impostazioni.
    
Verificare che il server di sincronizzazione della directory stia utilizzando correttamente il DNS controllando il DNS interno e accertandosi che sia stato aggiunto un record Address (A) per la macchina virtuale con l'indirizzo IP.  
  
Seguire le istruzioni in [Connettersi e accedere alla macchina virtuale](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) per connettersi al server di sincronizzazione della directory con Connessione Desktop remoto. Dopo l'accesso, aggiungere la macchina virtuale al dominio di Windows Server AD locale.
  
Affinché Azure AD Connect riesca ad accedere alle risorse di Internet, è necessario configurare il server di sincronizzazione della directory per utilizzare il server proxy della rete locale. È necessario contattare l'amministratore di rete per visualizzare eventuali ulteriori procedure di configurazione da eseguire.
  
Questa è la configurazione risultante.
  
![Fase 2 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Nella figura viene illustrata la macchina virtuale del server di sincronizzazione della directory nella rete virtuale Azure cross-premise.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Installare e configurare Azure AD Connect

Completare la procedura seguente:
  
1. Eseguire la connessione al server di sincronizzazione della directory utilizzando Connessione Desktop remoto con un account di dominio di Windows Server AD dotato dei privilegi di amministratore locale. Vedere [Connettersi e accedere alla macchina virtuale](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).
    
2. Dal server di sincronizzazione della directory, aprire l'articolo [Configurare la sincronizzazione della directory per Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) e seguire le istruzioni per la sincronizzazione della directory con sincronizzazione dell'hash delle password.
    
> [!CAUTION]
> Il programma di installazione crea l'account **AAD_xxxxxxxxxxxx** nell'unità organizzativa Utenti locali. Non spostare o eliminare l'account, altrimenti la sincronizzazione avrà esito negativo.
  
Questa è la configurazione risultante.
  
![Fase 3 del server di sincronizzazione della directory per Office 365 ospitato su Azure](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Nella figura viene illustrato il server di sincronizzazione della directory con Azure AD Connect nella rete virtuale Azure cross-premise.
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Assegnare percorsi e licenze agli utenti in Office 365

Azure AD Connect aggiunge account alla sottoscrizione a Office 365 da Windows Server AD locale, ma per consentire agli utenti di accedere a Office 365 e utilizzarne i servizi, gli account devono essere configurati con un percorso e le licenze. Seguire questi passaggi per aggiungere il percorso e attivare le licenze per gli account utente appropriati:
  
1. Accedere alla [pagina del portale di Office 365](https://portal.office.com), quindi fare clic su **Admin**.
    
2. Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.
    
3. Nell’elenco degli account utente, selezionare la casella di controllo accanto all'utente che si desidera attivare.
    
4. Nella pagina dell'utente, fare clic su **Modifica** per **Licenze di prodotto**.
    
5. Nella pagina **Licenze di prodotto**, selezionare un percorso per l'utente per **Percorso**, quindi abilitare le licenze opportune per l'utente.
    
6. Al termine dell'operazione, fare clic su **Salva** e fare clic due volte su **Chiudi**.
    
7. Tornare al passaggio 3 per altri utenti.
    
## <a name="see-also"></a>Vedere anche

<a name="DeploymentRoadmap"> </a>

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
  
[Connettere una rete locale a una rete virtuale di Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Scaricare Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurare la sincronizzazione della directory in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[Server di sincronizzazione della directory in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



