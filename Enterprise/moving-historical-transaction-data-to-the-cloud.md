---
title: Trasferimento dei dati cronologici delle transazioni nel cloud
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: 'Riepilogo: Come Contoso ha implementato SQL Server estensione del database per ridurre le esigenze di archiviazione in locale e giornaliera in esecuzione i costi.'
ms.openlocfilehash: 791b5d4f14ba7246221cf9b459c31c9ba1b54099
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915721"
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a>Trasferimento dei dati cronologici delle transazioni nel cloud

 **Riepilogo:** Contoso ha implementato come database esteso di SQL Server per ridurre le esigenze di archiviazione in locale e giornaliera costi contenuti.
  
Sistema di archiviazione dell'organizzazione Contoso archivia una grande quantità di dati di cronologia delle transazioni per la conformità ai requisiti normativi e per la ricerca di marketing e Business Intelligence analisi delle tendenze di spese. Contoso deve anche per il ripristino dei dati archiviati nastro magnetico, un processo molto tempo. L'hardware nel sistema di archiviazione aziendale Contoso è stato quasi alla fine del ciclo di vita e sostituirlo potrebbe essere molto costosa. 
  
Durante il relativo esigenza aziendale di scalabilità orizzontale verso il basso relativi centri dati locali, Contoso ha scelto per l'aggiornamento a SQL Server 2016 per la funzionalità ibrida Ridimensiona Database e il relativo una facile integrazione con Azure. Database esteso consente Contoso per spostare i dati con cold le tabelle in locale in storage cloud, liberare spazio su disco locale e la riduzione di manutenzione. Dati attivo e con cold sono le stesse tabelle e sono sempre disponibili per le applicazioni e dei relativi utenti e per la manutenzione, ad esempio backup e ripristino. Ridimensiona Database illustrato nella figura 1.
  
**Nella figura 1: SQL Server stiramento Database**

![Estensione database di SQL Server come soluzione di dati ibrida](media/Contoso-Poster/StretchDB01.png)
  
Nella figura 1 viene illustrato il modo in cui un client SQL invia query T-SQL per un server che esegue SQL Server 2016, che li inoltra a un Database Ridimensiona SQL Azure in Azure PaaS.
  
Per ulteriori informazioni, vedere [Database adatta](https://msdn.microsoft.com/library/dn935011.aspx).
  
Contoso utilizzata la procedura seguente per spostare i dati cronologici in cloud:
  
1. Analizzare i database
    
    Eseguire un'analisi delle tabelle nei database che lo scopo di spostamento nel cloud e corretto eventuali problemi. Il nuovo Advisor Database Ridimensiona ha dato loro una panoramica completa dei quali si aspettano da tutte le funzionalità di SQL Server 2016, incluse le tabelle contengono dati freddi potrebbero essere ridimensionati.
    
2. Aggiornamento
    
    Esistenti SQL Server aggiornati nel centro dati headquarters Parigi a SQL Server 2016.
    
3. Eseguire la migrazione dei dati con cold nel cloud
    
    Utilizzando SQL Management Studio, vengono identificati i database per estendere e le tabelle di eseguire la migrazione a istanze del Database esteso in Azure. Nel corso del tempo e in background, SQL Server 2016 spostati i dati cronologici per estendere i database in Azure.
    
Di seguito è la configurazione per un server che esegue SQL Server 2016 nella sede centrale Parigi risultante.
  
**Figura 2: Utilizzo di Database adatta per un server di datacenter di Contoso**

![Configurazione di Contoso dell'Estensione database di SQL Server per un singolo computer che esegue SQL Server](media/Contoso-Poster/StretchDB02.png)

  
Nella figura 2 viene illustrato come le query degli utenti a un server applicazioni nel centro dati di Contoso diventano query SQL che vengono passate a un Database Ridimensiona SQL Azure in Azure PaaS.
  
Gli utenti di accedere ai dati tramite query e App esistente. Criteri di accesso rimangono invariate. Non è stato spostato in avanti, è necessario per i backup su nastro. Manutenzione è costituita da eseguire il backup e ripristino dei dati attivo.
  
Dopo l'implementazione di Database Ridimensiona, Contoso:
  
- Ridurre le esigenze di archiviazione locale 85%.
    
- Eseguito l'aggiornamento del sistema di archiviazione dell'organizzazione e utilizzo del nastro magnetico archivi non necessarie.
    
- Riduzione dei costi in esecuzione giornalieri in modo significativo.
    
## <a name="see-also"></a>Vedere anche

[Scenari aziendali per Contoso Corporation](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Contoso nel Microsoft Cloud](contoso-in-the-microsoft-cloud.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)
  
[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://sway.com/FJ2xsyWtkJc2taRD)




