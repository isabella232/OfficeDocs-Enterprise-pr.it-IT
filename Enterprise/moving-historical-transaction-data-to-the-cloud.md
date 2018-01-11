---
title: Spostamento dei dati di cronologia delle transazioni per il cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 'Riepilogo: Come Contoso ha implementato SQL Server estensione del database per ridurre le esigenze di archiviazione in locale e giornaliera in esecuzione i costi.'
ms.openlocfilehash: ef21b00f54fcc6efda2e83cb5952a99c7b8c8f28
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="d3e0f-103">Spostamento dei dati di cronologia delle transazioni per il cloud</span><span class="sxs-lookup"><span data-stu-id="d3e0f-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="d3e0f-104">**Riepilogo:** Contoso ha implementato come database esteso di SQL Server per ridurre le esigenze di archiviazione in locale e giornaliera costi contenuti.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="d3e0f-p101">Sistema di archiviazione dell'organizzazione Contoso archivia una grande quantità di dati di cronologia delle transazioni per la conformità ai requisiti normativi e per la ricerca di marketing e Business Intelligence analisi delle tendenze di spese. Contoso deve anche per il ripristino dei dati archiviati nastro magnetico, un processo molto tempo. L'hardware nel sistema di archiviazione aziendale Contoso è stato quasi alla fine del ciclo di vita e sostituirlo potrebbe essere molto costosa.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="d3e0f-p102">Durante il relativo esigenza aziendale di scalabilità orizzontale verso il basso relativi centri dati locali, Contoso ha scelto per l'aggiornamento a SQL Server 2016 per la funzionalità ibrida Ridimensiona Database e il relativo una facile integrazione con Azure. Database esteso consente Contoso per spostare i dati con cold le tabelle in locale in storage cloud, liberare spazio su disco locale e la riduzione di manutenzione. Dati attivo e con cold sono le stesse tabelle e sono sempre disponibili per le applicazioni e dei relativi utenti e per la manutenzione, ad esempio backup e ripristino. Ridimensiona Database illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="d3e0f-112">**Nella figura 1: SQL Server stiramento Database**</span><span class="sxs-lookup"><span data-stu-id="d3e0f-112">**Figure 1: SQL Server Stretch Database**</span></span>

![Estensione database di SQL Server come soluzione di dati ibrida](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="d3e0f-114">Nella figura 1 viene illustrato il modo in cui un client SQL invia query T-SQL per un server che esegue SQL Server 2016, che li inoltra a un Database Ridimensiona SQL Azure in Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="d3e0f-115">Per ulteriori informazioni, vedere [Database adatta](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="d3e0f-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="d3e0f-116">Contoso utilizzata la procedura seguente per spostare i dati cronologici in cloud:</span><span class="sxs-lookup"><span data-stu-id="d3e0f-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="d3e0f-117">Analizzare i database</span><span class="sxs-lookup"><span data-stu-id="d3e0f-117">Analyze databases</span></span>
    
    <span data-ttu-id="d3e0f-p103">Eseguire un'analisi delle tabelle nei database che lo scopo di spostamento nel cloud e corretto eventuali problemi. Il nuovo Advisor Database Ridimensiona ha dato loro una panoramica completa dei quali si aspettano da tutte le funzionalità di SQL Server 2016, incluse le tabelle contengono dati freddi potrebbero essere ridimensionati.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="d3e0f-120">Aggiornamento</span><span class="sxs-lookup"><span data-stu-id="d3e0f-120">Upgrade</span></span>
    
    <span data-ttu-id="d3e0f-121">Esistenti SQL Server aggiornati nel centro dati headquarters Parigi a SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="d3e0f-122">Eseguire la migrazione dei dati con cold nel cloud</span><span class="sxs-lookup"><span data-stu-id="d3e0f-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="d3e0f-p104">Utilizzando SQL Management Studio, vengono identificati i database per estendere e le tabelle di eseguire la migrazione a istanze del Database esteso in Azure. Nel corso del tempo e in background, SQL Server 2016 spostati i dati cronologici per estendere i database in Azure.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="d3e0f-125">Di seguito è la configurazione per un server che esegue SQL Server 2016 nella sede centrale Parigi risultante.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="d3e0f-126">**Figura 2: Utilizzo di Database adatta per un server di datacenter di Contoso**</span><span class="sxs-lookup"><span data-stu-id="d3e0f-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![Configurazione di Contoso dell'Estensione database di SQL Server per un singolo computer che esegue SQL Server](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="d3e0f-128">Nella figura 2 viene illustrato come le query degli utenti a un server applicazioni nel centro dati di Contoso diventano query SQL che vengono passate a un Database Ridimensiona SQL Azure in Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="d3e0f-p105">Gli utenti di accedere ai dati tramite query e App esistente. Criteri di accesso rimangono invariate. Non è stato spostato in avanti, è necessario per i backup su nastro. Manutenzione è costituita da eseguire il backup e ripristino dei dati attivo.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="d3e0f-133">Dopo l'implementazione di Database Ridimensiona, Contoso:</span><span class="sxs-lookup"><span data-stu-id="d3e0f-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="d3e0f-134">Ridurre le esigenze di archiviazione locale 85%.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="d3e0f-135">Eseguito l'aggiornamento del sistema di archiviazione dell'organizzazione e utilizzo del nastro magnetico archivi non necessarie.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="d3e0f-136">Riduzione dei costi in esecuzione giornalieri in modo significativo.</span><span class="sxs-lookup"><span data-stu-id="d3e0f-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d3e0f-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3e0f-137">See Also</span></span>

[<span data-ttu-id="d3e0f-138">Scenari aziendali per Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="d3e0f-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="d3e0f-139">Contoso nel Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="d3e0f-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="d3e0f-140">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="d3e0f-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d3e0f-141">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="d3e0f-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="d3e0f-142">Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT</span><span class="sxs-lookup"><span data-stu-id="d3e0f-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




