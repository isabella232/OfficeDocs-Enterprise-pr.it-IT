---
title: Ripristino di emergenza di SharePoint Server 2013 in Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998168"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Ripristino di emergenza di SharePoint Server 2013 in Microsoft Azure

 Con Azure è possibile creare un ambiente di ripristino di emergenza per la farm locale di SharePoint. In questo articolo viene descritto come progettare e implementare questa soluzione.

 **Video sul ripristino di emergenza di SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
Utilizzare questo articolo con il modello della soluzione seguente: **Ripristino di emergenza di SharePoint Microsoft Azure**.
  
[![Processo di ripristino di emergenza di SharePoint in Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Utilizzare i servizi infrastruttura di Azure per il ripristino di emergenza

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
I vantaggi per l'uso di servizi infrastruttura di Azure includono:
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **Impegno ridotto dei centri dati** Utilizzare servizi infrastruttura di Azure anziché investire in un centro dati secondario in un'area diversa.
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**Tabella: Ambienti di ripristino**

|**Tipo di ambiente di ripristino**|**Descrizione**|
|:-----|:-----|
|Hot  <br/> |Una farm a dimensioni complete viene sottoposta a provisioning e viene eseguita allo standby.  <br/> |
|Warm  <br/> |La farm viene creata e le macchine virtuali sono in esecuzione e aggiornate.  <br/> Il ripristino include il collegamento di database di contenuto, le applicazioni dei servizii di provisioning e la ricerca per indicizzazione del contenuto.  <br/> La farm può essere una versione ridotta della farm di produzione e quindi essere ampliata per soddisfare la base utenti completa.  <br/> |
|Cold  <br/> |La farm viene creata completamente, ma le macchine virtuali sono arrestate.  <br/> La gestione dell'ambiente include l'avvio periodico delle macchine virtuali, l'applicazione di patch, l'aggiornamento e la verifica dell'ambiente.  <br/> Avviare l'ambiente completo in caso di calamità.  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
Per ulteriori informazioni sulle soluzioni di ripristino di emergenza, vedere [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) e [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Descrizione della soluzione

La soluzione di ripristino di emergenza con warm standby richiede l'ambiente seguente:
  
- Una farm di produzione di SharePoint locale
    
- Una farm di SharePoint di ripristino in Azure
    
- Una connessione VPN da sito a sito tra i due ambienti.
    
La figura seguente illustra questi tre elementi.
  
**Figura: elementi di una soluzione con warm standby in Azure**

![Elementi di una soluzione con warm standby di SharePoint in Azure](media/AZarch-AZWarmStndby.png)
  
Il log shipping di SQL Server con Replica DFS viene utilizzato per copiare i backup di database e i registri transazioni nella farm di ripristino in Azure: 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- I registri vengono riprodotti in SQL Server nell'ambiente di ripristino in Azure.
    
- I database di contenuto di SharePoint sottoposti a log shipping non vengono associati nell'ambiente di ripristino finché non viene eseguita un esercizio di ripristino.
    
Per ripristinare la farm, effettuare i seguenti passaggi:
  
1. Arrestare il log shipping
    
2. Smettere di accettare il traffico alla farm primaria.
    
3. Riprodurre i registri di transazioni finali.
    
4. Collegare i database di contenuto alla farm.
    
5. Ripristinare le applicazioni di servizio dai database di servizi replicati.
    
6. Aggiornare i record DNS in modo che puntino alla farm di ripristino.
    
7. Avviare una ricerca per indicizzazione completa.
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
Dopo che è stato eseguito un ripristino, questa soluzione fornisce gli elementi elencati nella tabella seguente.
  
**Tabella: Obiettivi del ripristino della soluzione**

|**Elemento**|**Descrizione**|
|:-----|:-----|
|Siti e contenuto  <br/> |Siti e contenuto sono disponibili nell'ambiente di ripristino.  <br/> |
|Una nuova istanza di ricerca  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|Servizi  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Raccolta dati di integrità e utilizzo <br/>  Servizio informazioni sullo stato <br/>  Word Automation <br/>  Qualsiasi altro servizio che non usa un database <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**Tabella: Altri elementi che possono essere gestiti da MCS o da un partner**

|**Elemento**|**Descrizione**|
|:-----|:-----|
|Sincronizzazione di soluzioni farm personalizzate  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|Connessioni a origini dati in locale  <br/> |Potrebbe non essere pratico replicare le connessioni a sistemi di dati di back-end, ad esempio le connessioni controller di dominio di backup e le origini di contenuto di ricerca.  <br/> |
|Scenari di ripristino di ricerca  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
Le istruzioni fornite in questo articolo presuppongono che la farm locale sia già progettata e distribuita.
  
## <a name="detailed-architecture"></a>Architettura dettagliata

In teoria, la configurazione della farm di ripristino in Azure è identica alla farm di produzione locale, incluse le seguenti caratteristiche:
  
- Stessa rappresentazione dei ruoli del server
    
- Stessa configurazione delle personalizzazioni
    
- Stessa configurazione dei componenti di ricerca
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>Ambienti con warm standby

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
Nella figura seguente viene illustrata una soluzione di ripristino di emergenza da una farm di SharePoint locale a una farm di SharePoint basata su Azure che viene configurata come ambiente con warm standby.
  
**Figura: topologia ed elementi chiave di una farm di produzione e di una farm di ripristino con warm standby.**

![Topologia di una farm di SharePoint e una farm di ripristino con warm standby](media/AZarch-AZWarmStndby.png)
  
In questo diagramma:
  
- Sono illustrati due ambienti affiancati: la farm di SharePoint locale e la farm con warm standby in Azure.
    
- Ogni ambiente include una condivisione di file.
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- Replica DFS copia i file dalla condivisione file nell'ambiente locale alla condivisione file nell'ambiente Azure.
    
- Il log shipping riproduce i log dalla condivisione di file dell'ambiente Azure nella replica primaria nel gruppo di disponibilità AlwaysOn di SQL Server nell'ambiente di ripristino.
    
### <a name="cold-standby-environments"></a>Ambienti con cold standby

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- Condivisione file
    
- Server database primario
    
- Almeno una macchina virtuale che esegue Active Directory Domain Services di Windows Server e DNS
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**Figura: farm di ripristino con cold standby e macchine virtuali in esecuzione**

![Elementi di una soluzione con cold standby di SharePoint in Azure](media/AZarch-AZColdStndby.png)
  
Dopo il failover a un ambiente con cold standby, tutte le macchine virtuali vengono avviate ed è necessario configurar il metodo per ottenere la disponibilità elevata dei server di database, ad esempio i gruppi di disponibilità di SQL Server AlwaysOn.
  
Se vengono implementati più gruppi di archiviazione (i database vengono suddivisi tra più set di disponibilità elevata di SQL Server), il database primario per ogni gruppo di archiviazione deve essere in esecuzione per accettare i log associati al relativo gruppo di archiviazione.
  
### <a name="skills-and-experience"></a>Competenze ed esperienze

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [Servizi di replica DFS](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server Failover Clustering (WSFC) con SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [Gruppi di disponibili AlwaysOn (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Backup e ripristino di database SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Installazione di SharePoint Server 2013 e distribuzione delle farm](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>Guida di orientamento al ripristino di emergenza

![Rappresentazione grafica della guida di orientamento per il ripristino di emergenza di SharePoint.](media/Azure-DRroadmap.png)
  
Questa guida di orientamento presuppone che si disponga già di una farm SharePoint Server 2013 distribuita nell'ambiente di produzione.
  
**Tabella: Guida di orientamento per il ripristino di emergenza**

|**Fase**|**Descrizione**|
|:-----|:-----|
|Fase 1  <br/> |Progettare l'ambiente di ripristino di emergenza.  <br/> |
|Fase 2  <br/> |Creare la rete virtuale di Azure e la connessione VPN.  <br/> |
|Fase 3  <br/> |Distribuire Active Directory e Domain Name Services nella rete virtuale di Azure.  <br/> |
|Fase 4  <br/> |Distribuire la farm di ripristino di SharePoint in Azure  <br/> |
|Fase 5  <br/> |Configurare DFSR tra le farm  <br/> |
|Fase 6  <br/> |Configurare il log shipping nella farm di ripristino  <br/> |
|Fase 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  Arrestare il log shipping <br/>  Ripristinare i backup. <br/>  Eseguire la ricerca per indicizzazione del contenuto. <br/>  Ripristinare i servizi. <br/>  Gestire i record DNS. <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Fase 1: Progettare l'ambiente di ripristino di emergenza

Utilizzare le istruzioni in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) per progettare l'ambiente di ripristino di emergenza, inclusa la farm di ripristino di SharePoint. È possibile utilizzare la grafica nella [soluzione di ripristino di emergenza di SharePoint nel](https://go.microsoft.com/fwlink/p/?LinkId=392554) file di Azure Visio per avviare il processo di progettazione. È consigliabile progettare l'intero ambiente prima di iniziare qualsiasi lavoro nell'ambiente Azure.
  
Oltre al materiale sussidiario fornito in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) per la progettazione della rete virtuale, la connessione VPN, Active Directory e la farm di SharePoint, assicurarsi di aggiungere un ruolo di condivisione file per l'ambiente di Azure.
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Figura: Posizionamento di un file server utilizzato per una soluzione di ripristino di emergenza**

![Mostra una macchina virtuale di condivisione file aggiunta allo stesso servizio cloud contenente i ruoli del server di database di SharePoint.](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Fase 2: Creare la rete virtuale di Azure e la connessione VPN.

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- Pianificare lo spazio di indirizzi IP privato di Rete virtuale.
    
- Pianificare le modifiche dell'infrastruttura di routing per la Rete virtuale.
    
- Pianificare le regole del firewall per il traffico da e verso il dispositivo VPN locale.
    
- Creare la rete virtuale cross-premise in Azure.
    
- Configurare il routing tra la rete locale e la Rete virtuale.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Fase 3: Distribuire Active Directory e Domain Name Services nella rete virtuale di Azure

Questa fase include la distribuzione di Windows Server Active Directory e DNS alla Rete virtuale in uno scenario ibrido come descritto in [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) e come illustrato nella figura seguente.
  
**Figura: Configurazione del dominio ibrido Active Directory**

![Due macchine virtuali distribuite nella rete virtuale di Azure e la subnet della farm di SharePoint sono controller di dominio di replica e server DNS](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Per il materiale sussidiario sulla configurazione di un controller di dominio in Azure, vedere [Installazione di un controller di dominio Active Directory di replica in una rete virtuale di Azure](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Fase 4: Distribuire la farm di ripristino di SharePoint in Azure

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
Considerare le seguenti procedure apprese con la creazione del nostro ambiente per modelli di verifica:
  
- Creare macchine virtuali mediante il portale Azure o PowerShell.
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- Utilizzare una convenzione di denominazione per le macchine virtuali.
    
- Prestare attenzione alla posizione del centro dati in cui vengono distribuite le macchine virtuali.
    
- La funzione di adattamento automatico in Azure non è supportata per i ruoli di SharePoint.
    
- Non configurare gli elementi nella farm che verrà ripristinata, ad esempio le raccolte siti. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Fase 5: Configurare DFSR tra le farm

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
Dal Dashboard Server Manager, procedere come segue:
  
- Configurare il server locale.
    
- Avviare **Aggiunta guidata ruoli e funzionalità**.
    
- Apri il nodo **Servizi file e archiviazione**.
    
- Selezionare **Spazi dei nomi DFS** e **Replica DFS**.
    
- Fare clic su **Avanti** per completare la procedura guidata.
    
Nella tabella seguente vengono forniti i collegamenti ad articoli di riferimento DFSR e ai post di blog.
  
**Tabella: Articoli di riferimento per DFSR**

|**Titolo**|**Descrizione**|
|:-----|:-----|
|[Replica](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |Argomento di DFS Management TechNet con collegamenti per la replica  <br/> |
|[Replica DFS: Guida di sopravvivenza](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Wiki con collegamenti a informazioni DFS  <br/> |
|[Replica DFS: Domande frequenti](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |Argomento DFS replica TechNet  <br/> |
|[Blog di Jose Barreto](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Blog scritto dal responsabile programma di un’entità di sicurezza del team di File Server Microsoft  <br/> |
|[Team di Archiviazione Microsoft - Blog sugli schedari](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Blog su servizi file e le funzionalità di archiviazione in Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Fase 6: Configurare il log shipping nella farm di ripristino

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Fase 7: Convalidare failover e ripristino

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>Arrestare il log shipping

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Ripristinare i backup

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Ricerca per indicizzazione dell'origine contenuto

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
Per avviare una ricerca per indicizzazione completa, procedere come segue:
  
1. In Amministrazione centrale SharePoint 2013 andare a **Gestione applicazioni** > **Applicazioni di servizio** > **Gestisci applicazioni di servizio** e fare clic sull'applicazione Servizio di ricerca di cui si desidera effettuare una ricerca per indicizzazione.
    
2. Nella pagina **Amministrazione ricerca** fare clic su **Origini di contenuto**, puntare all'origine contenuto desiderata, fare clic sulla freccia e quindi fare clic su **Avvia ricerca per indicizzazione completa**.
    
### <a name="recover-farm-services"></a>Ripristinare i servizi farm

Nella tabella seguente viene illustrato come ripristinare i servizi che dispongono di database per i quali è stato eseguito il log shipping, i servizi che dispongono di database per i quali non si consiglia il ripristino con il log shipping e i servizi che non dispongono di database.
  
> [!IMPORTANT]
> Ripristinando un database di SharePoint locale nell'ambiente di Azure, i servizi di SharePoint che non sono stati già installati manualmente in Azure non verranno ripristinati. 
  
**Tabella: Riferimenti di database dell'applicazione di servizio**

|**Ripristinare questi servizi dai database per i quali è stato eseguito il log shipping**|**Sebbene questi servizi dispongano di database, ma è consigliabile avviarli senza ripristinarne i database**|**Questi servizi non archiviano i dati nei database. Avviarli dopo il failover**|
|:-----|:-----|:-----|
| Servizio di traduzione automatica <br/>  Servizio metadati gestiti <br/>  Servizio di archiviazione sicura <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Servizio impostazioni di sottoscrizione di Microsoft SharePoint Foundation <br/> | Raccolta dati di integrità e utilizzo <br/>  Servizio informazioni sullo stato <br/>  Word Automation <br/> | Excel Services <br/>  PerformancePoint Services <br/>  Conversione PowerPoint <br/>  Servizio grafica di Visio <br/>  Gestione del lavoro <br/> |
   
Nell'esempio seguente viene illustrato come ripristinare il servizio metadati gestiti da un database.
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
Innanzitutto, utilizzare  `New-SPMetadataServiceApplication` e specificare l'opzione `DatabaseName` con il nome del database ripristinato.
  
Successivamente, configurare la nuova applicazione di servizio metadati gestiti sul server secondario, come indicato di seguito:
  
- Nome: Servizio metadati gestiti
    
- Server di database: il nome del database del log delle transazioni spedito
    
- Nome database:Managed_Metadata_DB
    
- Pool di applicazioni: Applicazioni di servizio di SharePoint 
    
### <a name="manage-dns-records"></a>Gestione dei record DNS

È necessario creare manualmente i record DNS in modo che puntino alla farm di SharePoint in uso.
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
Per l'accesso esterno alla farm di SharePoint, è possibile creare un record host su un server DNS esterno con lo stesso URL utilizzato dai client sulla rete Intranet (ad esempio, `https://sharepoint.contoso.com` ) che punta a un indirizzo IP esterno nel firewall. (Una procedura consigliata, in questo esempio, consiste nel configurare il DNS suddiviso in modo che il server DNS interno sia autorevole `contoso.com` e INSTRADE le richieste direttamente al cluster di farm di SharePoint, anziché instradare le richieste DNS al server DNS esterno). È quindi possibile mappare l'indirizzo IP esterno all'indirizzo IP interno del cluster locale in modo che i client possano trovare le risorse che stanno cercando.
  
Da qui è possibile incorrere in scenari di ripristino di emergenza diversi:
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
Se si utilizzano raccolte siti con nome host, come consigliato nell' [architettura e nella distribuzione della raccolta siti con nome host (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), potrebbero essere presenti diverse raccolte siti ospitate dalla stessa applicazione Web nella farm di SharePoint, con nomi DNS univoci (ad esempio, `https://sales.contoso.com` e `https://marketing.contoso.com` ). In questo caso, è possibile creare record DNS per ogni raccolta siti che punta all'indirizzo IP del cluster. Quando una richiesta raggiunge i server Web front-end di SharePoint, questi gestiscono il routing di ogni richiesta alla raccolta siti appropriata.
  
## <a name="microsoft-proof-of-concept-environment"></a>Ambiente del modello di verifica di Microsoft

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
La tabella seguente descrive le macchine virtuali Hyper-V che sono state create e configurate per l'ambiente di test locale.
  
**Tabella: Macchine virtuali per il test locale**

|**Nome del server**|**Ruolo**|**Configurazione**|
|:-----|:-----|:-----|
|DC1  <br/> |Controller di dominino con Active Directory  <br/> |Due processori  <br/> Da 512 MB a 4 GB di RAM  <br/> 1 disco rigido da 127 GB  <br/> |
|RRAS  <br/> |Server configurato con il ruolo di Routing e Accesso remoto (RRAS).  <br/> |Due processori  <br/> 2 - 8 GB di RAM  <br/> 1 disco rigido da 127 GB  <br/> |
|FS1  <br/> |File server con condivisioni per i backup e un endpoint per DFSR.  <br/> |Quattro processori  <br/> 2 - 12 GB di RAM  <br/> 1 disco rigido da 127 GB  <br/> 1 disco rigido da 1 TB (SAN)  <br/> 1 disco rigido da 750 GB  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Server Web front-end.  <br/> |Quattro processori  <br/> 16 GB di RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Server applicazioni.  <br/> |Quattro processori  <br/> 2 - 16 GB di RAM  <br/> |
|SP-SQL-HA1 SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |Quattro processori  <br/> 2 - 16 GB di RAM  <br/> |
   
La tabella seguente descrive le configurazioni di unità per le macchine virtuali Hyper-V che abbiamo creato e configurato per i server Web front-end e i server applicazioni per l'ambiente di test locale.
  
**Tabella: Requisiti delle unità macchina virtuale per i server Web front-end e i server applicazioni per il test locale**

|**Lettera di unità**|**Dimensioni**|**Nome della directory**|**Percorso**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Unità di sistema  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Unità di registro (40 GB)  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATI  <br/> |
|F  <br/> |80  <br/> |Pagina (36 GB)  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\MSSQL\\DATI  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**Tabella: Requisiti delle unità macchina virtuale per i server di database per il test locale**

|**Lettera di unità**|**Dimensioni**|**Nome della directory**|**Percorso**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Directory radice dati  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Directory database utente  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATI  <br/> |
|F  <br/> |500  <br/> |Directory log database utente  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATI  <br/> |
|G  <br/> |500  <br/> |Directory DB temp  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Directory log DB temp  <br/> |<DriveLetter>:\\Programmi\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATI  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Configurazione dell'ambiente di testing

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
Abbiamo distribuito l'ambiente di testing nelle tre fasi indicate di seguito:
  
- Configurazione dell'infrastruttura ibrida
    
- Provisioning dei server
    
- Distribuzione delle farm di SharePoint.
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Configurazione dell'infrastruttura ibrida

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>Provisioning dei server

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>Distribuzione delle farm di SharePoint.

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Abbiamo la farm e unito altri server nell'ordine seguente:
  
- Provisioning di SP-SQL-HA1 e SP-SQL-HA2.
    
- Configurazione di AlwaysOn e creazione di tre gruppi di disponibilità per la farm.  
    
- Provisioning di SP-APP1 all'host Amministrazione centrale.
    
- Provisioning di SP-WFE1 e SP-WFE2 per ospitare la cache distribuita. 
    
Abbiamo utilizzato il parametro  _skipRegisterAsDistributedCachehost_ quando abbiamo eseguito **psconfig.exe** alla riga di comando. Per ulteriori informazioni, vedere [Plan for Feeds and the Distributed cache Service in SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Abbiamo ripetuto i passaggi seguenti nell'ambiente di ripristino:
  
- Provisioning di AZ-SQL-HA1 e AZ-SQL-HA2.
    
- Configurazione di AlwaysOn e creazione di tre gruppi di disponibilità per la farm.
    
- Provisioning di  AZ-APP1 per l’hosting di Amministrazione centrale.
    
- Provisioning di AZ-WFE1 e AZ-WFE2 per ospitare la cache distribuita.
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
La tabella seguente descrive le macchine virtuali, le subnet e i set di disponibilità che abbiamo configurato per la nostra farm di ripristino.
  
**Tabella: Infrastruttura della farm di ripristino**

|**Nome del server**|**Ruolo**|**Configurazione**|**Subnet**|**Set di disponibilità**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Controller di dominino con Active Directory  <br/> |Due processori  <br/> Da 512 MB a 4 GB di RAM  <br/> 1 disco rigido da 127 GB  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |File server con condivisioni per i backup e un endpoint per DFSR.  <br/> | Configurazione di A5: <br/>  Due processori <br/>  14 GB di RAM <br/>  1 disco rigido da 127 GB <br/>  1 disco rigido da 135 GB <br/>  1 disco rigido da 127 GB <br/>  1 disco rigido da 150 GB <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Server Web di front-end  <br/> | Configurazione di A5: <br/>  Due processori <br/>  14 GB di RAM <br/>  1 disco rigido da 127 GB <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Server applicazioni  <br/> | Configurazione di A5: <br/>  Due processori <br/>  14 GB di RAM <br/>  1 disco rigido da 127 GB <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |Server di database e repliche primarie e secondarie per gruppi di disponibilità AlwaysOn  <br/> | Configurazione di A5: <br/>  Due processori <br/>  14 GB di RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Operations

Dopo che il team di testing ha stabilizzato gli ambienti della farm e ha completato il test funzionale, sono state iniziate le seguenti attività necessarie per configurare l'ambiente di ripristino locale:
  
- Configurazione di backup completi e differenziali.
    
- Configurazione del servizio DFSR nei file server che trasferiscono i log delle transazioni tra l'ambiente locale e l'ambiente Azure.
    
- Configurazione del log shipping nel server di database principale.
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>Database

I nostri test di failover hanno interessato i seguenti database: 
  
- WSS_Content
    
- ManagedMetadata
    
- Database dei profili
    
- Database di sincronizzazione
    
- Database social
    
- Hub tipo di contenuto (un database per un hub diffusione tipo di contenuto dedicato)
    
## <a name="troubleshooting-tips"></a>Suggerimenti per la risoluzione dei problemi

La sezione illustra i problemi che si sono verificati durante il test e le relative soluzioni. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>L'utilizzo dello Strumento di gestione archivio termini ha causato l'errore "The Managed Metadata Store or Connection is currently not available", in cui si comunica che l'archivio dei metadati gestiti o la connessione non è disponibile al momento.

Assicurarsi che l'account del pool di applicazioni utilizzato dall'applicazione Web disponga dell’autorizzazione Accesso in lettura all'archivio termini.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>I set di termini personalizzati non sono disponibili nella raccolta siti

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Il comando Get-ADForest di Windows PowerShell genera l'errore, "Termine 'Get-ADForest' non riconosciuto come nome di cmdlet, funzione, programma eseguibile o file script."

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Errore di creazione del gruppo di disponibilità all'avvio della sessione 'AlwaysOn_health' XEvent in '<server name>'

Verificare che entrambi i nodi del cluster di failover siano nello stato "Attivo" e non "Sospeso" o "Interrotto". 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>Il processo di log shipping di SQL Server ha esito negativo con un errore di accesso negato nel tentativo di connettersi alla condivisione file

Assicurarsi che SQL Server Agent sia in esecuzione con le credenziali di rete, anziché le credenziali predefinite.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>Il processo di log shipping di SQL Server indica l'esito positivo, ma i file non vengono copiati

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Il servizio Metadati gestiti (o un altro servizio di SharePoint) non si avvia automaticamente dopo l'installazione

I servizi potrebbero richiedere alcuni minuti per avviarsi, a seconda delle prestazioni e del carico corrente del server di SharePoint. Scegliere manualmente **Start** per il servizio e fornire il tempo sufficiente per l'avvio aggiornando di tanto in tanto la schermata Servizi nel server per monitorarne lo stato. Nel caso in cui il servizio resti in stato di arresto, abilitare la registrazione diagnostica di SharePoint, tentare di avviare di nuovo il servizio e quindi verificare l'assenza di errori nel log. Per ulteriori informazioni, vedere [Configure diagnostic logging in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Dopo la modifica DNS per l'ambiente di failover di Azure, i browser client continuano a usare il vecchio indirizzo IP del sito di SharePoint

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Risorse aggiuntive

[Opzioni di disponibilità elevata e di ripristino di emergenza supportate per database di SharePoint](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Configurare gruppi di disponibilità AlwaysOn di SQL Server 2012 per SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>Vedere anche

[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.yml)



