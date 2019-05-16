---
title: Guida di orientamento alla fine del supporto di Project Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: Il 13 ottobre 2020, il supporto termina per Project Server 2010. Utilizzare questo articolo per pianificare l'aggiornamento.
ms.openlocfilehash: 1c8e6eab592e2974c334367e7931395e867ad97e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071042"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Guida di orientamento alla fine del supporto di Project Server 2010

Il supporto termina per i server e le applicazioni di Office 2010 nel 2010 ed è necessario prendere in considerazione i piani per la migrazione. Se si sta attualmente utilizzando Project Server 2010, tenere presente che questo e altri prodotti correlati avranno le seguenti date di supporto:
  
|**Prodotto**|**Data di fine del supporto**|
|:-----|:-----|
|Project Server 2010  <br/> |13 ottobre 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 ottobre 2020  <br/> |
|Project 2010 standard  <br/> |13 ottobre 2020  <br/> |
|Project 2010 Professional  <br/> |13 ottobre 2020  <br/> |
   
Per ulteriori informazioni sui server di Office 2010 che raggiungono il pensionamento, vedere [upgrade from office 2010 Servers and client Products](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Cosa significa fine del supporto?

Project Server, come quasi tutti i prodotti Microsoft, ha un ciclo di vita di supporto durante il quale vengono fornite nuove funzionalità, correzioni di bug, correzioni di sicurezza e così via. Questo ciclo di vita di solito dura 10 anni a partire dalla data di rilascio iniziale del prodotto e la fine di questo ciclo di vita è nota come fine del prodotto di supporto. Poiché Project Server 2010 ha raggiunto la fine del supporto il 10 ottobre 2020, Microsoft non fornirà più:
  
- Supporto tecnico per i problemi che possono verificarsi.
    
- Correzioni dei bug per i problemi individuati e che possono influire sulla stabilità e sull'usabilità del server.
    
- Correzioni per la sicurezza per le vulnerabilità individuate e che possono rendere il server vulnerabile alle violazioni della sicurezza.
    
- Aggiornamenti del fuso orario.
    
L'installazione di Project Server 2010 continuerà a essere eseguita dopo questa data. Tuttavia, a causa delle modifiche elencate in alto, è consigliabile eseguire la migrazione da Project Server 2010 appena possibile.
  
## <a name="what-are-my-options"></a>Quali sono le opzioni disponibili?

Se si utilizza Project Server 2010, è necessario esplorare le opzioni di migrazione, che sono le seguenti:
  
- Eseguire la migrazione a Project online
    
- Eseguire la migrazione a una nuova versione locale di Project Server (preferibilmente Project Server 2019).
    
|**Perché preferirei eseguire la migrazione a Project online**|**Perché preferirei eseguire la migrazione a Project Server 2019**|
|:-----|:-----|
| Gli utenti di dispositivi mobili.  <br/>  I costi per la migrazione sono una grande preoccupazione (hardware, software, ore e tentativi di implementazione, ecc.).  <br/>  Dopo la migrazione, i costi per il mantenimento dell'ambiente sono una grande preoccupazione (ad esempio, aggiornamenti automatici, tempo di uptime garantito e così via).  <br/> | Le regole business mi impediscono di gestire l'attività nel cloud.  <br/>  È necessario controllare gli aggiornamenti per l'ambiente.  <br/> |
   
> [!NOTE]
> Per ulteriori informazioni sulle opzioni per lo spostamento dai server di Office 2010, vedere [risorse che consentono di eseguire l'aggiornamento da server e client di office 2010](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Si noti che Project Server non supporta una configurazione ibrida poiché Project Server e Project online non possono condividere lo stesso pool di risorse. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Considerazioni importanti che è necessario apportare quando si pianifica la migrazione da Project Server 2010

Quando si pianifica la migrazione da Project Server 2010, è necessario tenere presente quanto segue:
  
- **Ottenere assistenza da un partner Microsoft** -l'aggiornamento da Project Server 2010 può essere una sfida e richiede molta preparazione e pianificazione. Può essere particolarmente difficile se non si è in grado di installare e configurare Project Server 2010 in origine. Fortunatamente, ci sono partner Microsoft che è possibile rivolgersi a chi lo può fare per vivere, se si prevede di eseguire la migrazione a Project Server 2019 o a Project online. È possibile cercare un partner Microsoft per facilitare la migrazione nel [centro partner Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). È possibile recuperare un elenco di tutti i partner Microsoft con competenza in Project eseguendo una ricerca sul termine *progetto Gold e sulla gestione del portfolio* . 
    
- **Pianificare le personalizzazioni** : tenere presente che molte delle personalizzazioni che si utilizzano nell'ambiente di project Server 2010 potrebbero non funzionare durante la migrazione a project server 2019 o a Project online. Esistono grandi differenze nell'architettura di Project Server tra le versioni, così come i sistemi operativi necessari, i server di database e i browser Web client supportati per l'utilizzo con la versione più recente. Disporre di un piano su come testare o ricreare le personalizzazioni in base alle esigenze nel nuovo ambiente. La pianificazione dell'aggiornamento sarà anche una buona occasione per verificare se è necessaria una specifica personalizzazione quando ci si sposta in avanti. [La creazione di un piano per le personalizzazioni correnti durante l'aggiornamento a SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) contiene alcune informazioni generali sulla valutazione e la pianificazione delle personalizzazioni correnti durante l'aggiornamento. 
    
- **Tempo e pazienza** : la pianificazione, l'esecuzione e il testing dell'aggiornamento richiederanno molto tempo ed energie, soprattutto se si esegue l'aggiornamento a Project Server 2019. Ad esempio, se si esegue la migrazione da Project Server 2010 a Project Server 2019, è necessario eseguire la migrazione da Project Server 2010 a Project Server 2013 e quindi controllare i dati e quindi eseguire la stessa operazione quando si esegue la migrazione a ogni versione successiva (Project Server 2016 e quindi Project Server 2019). È possibile verificare con un partner Microsoft la possibilità di confrontare i costi stimati con le stime relative al tempo necessario per la loro attività e a quale costo. 
    
## <a name="migrate-to-project-online"></a>Eseguire la migrazione a Project online

Se si sceglie di eseguire la migrazione da Project Server 2010 a Project online, è possibile eseguire le operazioni seguenti per eseguire la migrazione manuale dei dati del piano del progetto:
  
1. Salvare i piani di progetto da Project Server 2010 a. Formato MPP.
    
2. Utilizzando Project Professional 2016, Project Professional 2019 o il client desktop di Project online, aprire ogni file con estensione MPP e quindi salvarlo e pubblicarlo in Project online.
    
È possibile creare manualmente la configurazione di Project Web Access in Project online, ad esempio ricreare tutti i campi personalizzati o i calendari dell'organizzazione necessari. Microsoft Partners può anche aiutarti in questo.
  
Risorse chiave:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Introduzione a Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Come eseguire l'installazione e l'utilizzo di Project online.  <br/> |
|[Descrizioni dei servizi di Project online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informazioni sui diversi piani di Project online che sono disponibili per l'utente.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Eseguire la migrazione a una nuova versione locale di Project Server

Anche se si ritiene che sia possibile ottenere il miglior valore e l'esperienza utente eseguendo la migrazione a Project online, è inoltre necessario che alcune organizzazioni debbano mantenere i dati del progetto in un ambiente locale. Se si sceglie di mantenere i dati del progetto in locale, è possibile eseguire la migrazione dell'ambiente Project Server 2010 a Project Server 2013, Project Server 2016 o Project Server 2019.
  
È consigliabile eseguire la migrazione a Project Server 2019 se non è possibile eseguire la migrazione a Project online. In Project Server 2019 è inclusa la maggior parte delle funzionalità e dei miglioramenti inclusi nelle versioni precedenti di Project Server e corrisponde più fedelmente all'esperienza disponibile con Project Online (anche se alcune funzionalità sono disponibili solo in Project online).
  
Dopo aver completato ogni migrazione, è necessario controllare i dati per verificare che la migrazione sia stata eseguita correttamente.
  
> [!NOTE]
> Se si sta prendendo in considerazione la migrazione a Project Server 2013 solo se si è limitati a una soluzione locale, è importante tenere presente che sono rimasti solo alcuni anni di supporto. La data di fine del supporto di Project Server 2013 con Service Pack 2 è 10/13/2023. Per ulteriori informazioni sulle date di fine del supporto, vedere Criteri del ciclo di vita dei [prodotti Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Come si esegue la migrazione a Project Server 2019?

Le differenze architettoniche tra Project Server 2010 e Project Server 2019 impediscono un percorso di migrazione diretto. Questo significa che sarà necessario eseguire la migrazione dei dati di Project Server 2010 alla successiva versione successive di Project Server finché non si esegue l'aggiornamento a Project Server 2019.
  
Per eseguire l'aggiornamento a Project Server 2019, sarà necessario eseguire le operazioni seguenti:
  
1. Passaggio 1: eseguire la migrazione dei dati da Project Server 2010 a Project Server 2013.
    
2. Passaggio 2: eseguire la migrazione dei dati da Project serv 2013 a Project Server 2016.
    
3. Passaggio 3: eseguire la migrazione dei dati da Project Server 2016 a Project Server 2019.
    
Dopo aver completato ogni migrazione, è necessario controllare i dati per verificare che la migrazione sia stata eseguita correttamente.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Passaggio 1: eseguire la migrazione a Project Server 2013

Il primo passaggio per la migrazione dei dati di Project Server 2010 a Project Server 2019 consiste nella prima migrazione a Project Server 2013. 
  
Per una descrizione completa delle operazioni da eseguire per l'aggiornamento da Project Server 2010 a Project Server 2013, vedere l' [aggiornamento a Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) content set on TechNet. 
  
Risorse chiave:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Panoramica del processo di aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Ottenere informazioni di alto livello su ciò che è necessario eseguire per eseguire l'aggiornamento da Project Server 2010 a Project Server 2013.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Esaminare le considerazioni relative alla pianificazione che è necessario eseguire durante l'aggiornamento da Project Server 2010 a Project Server 2013, inclusi i requisiti di sistema.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Elementi da sapere sull'aggiornamento a questa versione

[What ' s New in Project Server 2013 upgrade](https://go.microsoft.com/fwlink/p/?linkid=841824) indica alcune importanti modifiche per l'aggiornamento per questa versione, la più importante è: 
  
- Non è presente alcun aggiornamento sul posto a Project Server 2013. Il metodo basato sul collegamento di database è l'unico metodo supportato per l'aggiornamento da Project Server 2010 a Project Server 2013.
    
- Il processo di aggiornamento non solo convertirà i dati di Project Server 2010 nel formato di Project Server 2013, ma consoliderà anche i quattro database di Project Server 2010 in un singolo database di Project Web App.
    
- Sia SharePoint Server 2013 che Project Server 2013 sono stati modificati per l'autenticazione basata sulle attestazioni dalla versione precedente. Quando si utilizza l'autenticazione classica, è necessario prendere in considerazione le considerazioni relative all'aggiornamento. Per ulteriori informazioni, vedere [Eseguire la migrazione dall'autenticazione in modalità classica a quella basata su attestazioni in SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Risorse aggiuntive:
  
- [Panoramica del processo di aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Aggiornare i database e le raccolte siti di Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramma del processo di aggiornamento di Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Grande consolidamento dei database, Project Server 2010 to 2013 Migration in 8 semplici passaggi](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Passaggio 2 alla migrazione a Project Server 2016

Dopo aver eseguito la migrazione a Project Server 2013 e aver verificato che i dati sono stati migrati correttamente, il passaggio successivo consiste nella migrazione dei dati a Project Server 2016.
  
Per una descrizione completa delle operazioni da eseguire per l'aggiornamento da Project Server 2013 a Project Server 2016, vedere il set [di contenuto upgrade to Project server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Risorse chiave:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Panoramica del processo di aggiornamento a Project Server 2013](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Ottenere informazioni di alto livello su ciò che è necessario eseguire per eseguire l'aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2013](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Esaminare le considerazioni relative alla pianificazione che è necessario eseguire durante l'aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Elementi da sapere sull'aggiornamento a questa versione

[Le operazioni necessarie per l'aggiornamento a Project Server 2016](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) indicano alcune importanti modifiche per l'aggiornamento per questa versione, tra cui: 
  
- Quando si crea l'ambiente Project Server 2016 in cui verrà eseguita la migrazione dei dati di Project Server 2013, tenere presente che i file di installazione di Project Server 2016 sono inclusi in SharePoint Server 2016. Per ulteriori informazioni, vedere [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- I piani delle risorse sono deprecati in Project Server 2016. I piani delle risorse di Project Server 2013 verranno migrati negli impegni delle risorse in Project Server 2016 e in Project online. Per ulteriori informazioni, vedere [Panoramica: impegni delle risorse](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Passaggio 3 eseguire la migrazione a Project Server 2019

Dopo aver eseguito la migrazione a Project Server 2016 e aver verificato che i dati sono stati migrati correttamente, il passaggio successivo consiste nella migrazione dei dati a Project Server 2019.
  
Per una descrizione completa delle operazioni da eseguire per l'aggiornamento da Project Server 2016 a Project Server 2019, vedere il set [di contenuto upgrade to Project server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Risorse chiave:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Panoramica del processo di aggiornamento di Project Server 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Ottenere informazioni di alto livello su ciò che è necessario eseguire per eseguire l'aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Esaminare le considerazioni relative alla pianificazione che è necessario eseguire durante l'aggiornamento da Project Server 2016 a Project Server 2019.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Elementi da sapere sull'aggiornamento a questa versione

[Le operazioni necessarie per l'aggiornamento a Project Server 2019](https://go.microsoft.com/fwlink/p/?linkid=841827) indicano alcune importanti modifiche per l'aggiornamento per questa versione, tra cui: 
  
- Il processo di aggiornamento eseguirà la migrazione dei dati dal database di Project Server 2016 al database del contenuto di SharePoint Server 2019.  Project Server 2019 non verrà creato a lungo dal proprietario del database di Project Server nella farm di SharePoint Server.

- Dopo l'aggiornamento, tenere conto di diverse modifiche in Project Web App.  Per una descrizione di questi elementi, vedere [What ' s New in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Eseguire la migrazione da Portfolio Server 2010

Project Portfolio Server 2010 è stato utilizzato con Project Server 2010 per la strategia di portfolio, la definizione di priorità e l'ottimizzazione. Non sono state create altre versioni del server del portfolio di progetti dopo questa versione. Tuttavia, le funzionalità di gestione del portfolio sono disponibili nelle versioni successive di Project Server e nella versione Premium di Project online. Non è possibile eseguire la migrazione dei dati di Project Portfolio Server 2010. I dati, ad esempio i driver di business, dovranno essere ricreati.
  
Altre risorse:
  
- [Descrizioni dei servizi di Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): vedere le funzionalità di gestione del portfolio incluse in project server 2016 e Project Online Premium.
    
- [Guida alla migrazione di Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Argomenti correlati

[Aggiornamento da SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Risorse utili per l'aggiornamento da server e client di Office 2010](upgrade-from-office-2010-servers-and-products.md)
  

