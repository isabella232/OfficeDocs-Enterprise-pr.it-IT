---
title: Project Server 2010 fine del supporto roadmap
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
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
description: Nel 13 ottobre 2020 il supporto termina per Project Server 2010. Utilizzare questo articolo per pianificare l'aggiornamento a questo punto.
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549785"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Data di fine progetto Server 2010 della Guida di orientamento al supporto

2010 termina il supporto per applicazioni e server di Office 2010 ed è necessario considerare i piani per la migrazione. Se si stanno attualmente utilizzando Project Server 2010, si noti che e questi altri prodotti correlati avranno seguente fine del periodo di supporto:
  
|**Prodotto**|**fine del periodo supportato**|
|:-----|:-----|
|Project Server 2010  <br/> |13 ottobre 2020  <br/> |
|Project Portfolio Server 2010  <br/> |13 ottobre 2020  <br/> |
|Project Standard 2010  <br/> |13 ottobre 2020  <br/> |
|Project Professional 2010  <br/> |13 ottobre 2020  <br/> |
   
Per ulteriori informazioni sui server di Office 2010 sta per raggiungere pensionistico, vedere [aggiornamento da prodotti client e server di Office 2010](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office).
  
## <a name="what-does-end-of-support-mean"></a>Quali fine consente di supporto Media?

Project Server, ad esempio quasi tutti i prodotti Microsoft, con un ciclo di vita del supporto durante il quale si forniscono le nuove funzionalità, correzioni, correzioni rapide per la sicurezza e così via. Questo ciclo di vita dura in genere per 10 anni dalla data di rilascio iniziale del prodotto e fine di questo ciclo di vita è noto come fine del prodotto del supporto tecnico. Dal momento che Project Server 2010 raggiunta la fine del supporto di 10 ottobre 2020, Microsoft non fornirà più:
  
- Supporto tecnico per i problemi che possono verificarsi.
    
- Correzioni degli errori per i problemi che vengono individuate e che possono influenzare la stabilità e facilità di utilizzo del server.
    
- Le patch di protezione per le vulnerabilità che vengono individuate e che potrebbe essere vulnerabile ad attacchi di violazioni della protezione del server.
    
- Aggiornamenti di fuso orario.
    
L'installazione di Project Server 2010 continua a eseguire dopo tale data. Tuttavia, a causa di modifiche elencate in precedenza, è consigliabile eseguire la migrazione da Project Server 2010 più presto possibile.
  
## <a name="what-are-my-options"></a>Che cosa sono le opzioni disponibili.

Se si utilizza Project Server 2010, è necessario esplorare le opzioni di migrazione, sono:
  
- Eseguire la migrazione a Project Online
    
- Eseguire la migrazione a una nuova versione locale di Project Server (preferibilmente 2019 Server Project).
    
|**Il motivo per cui si desidera eseguire la migrazione a Project Online**|**Il motivo per cui si desidera eseguire la migrazione a Project Server 2019**|
|:-----|:-----|
| È possibile che gli utenti mobili.  <br/>  I costi per eseguire la migrazione sono un grosso problema (hardware, software, ore e tentativo di implementare, ecc.).  <br/>  Dopo la migrazione, dei costi di manutenzione ambiente sono un grosso problema (ad esempio, gli aggiornamenti automatici, è garantito tempo di attività e così via.).  <br/> | Le regole business impedire me operativo la mia azienda nel cloud.  <br/>  Ambiente necessario controllo degli aggiornamenti.  <br/> |
   
> [!NOTE]
> Per ulteriori informazioni sulle opzioni per lo spostamento tra i server di Office 2010, vedere [le risorse che consentono di eseguire l'aggiornamento da Office 2010 server e client](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products). Si noti che Project Server non supporta una configurazione ibrida dal Server di Project e Project Online non possono condividere lo stesso pool di risorse. 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Considerazioni importanti che necessarie per la pianificazione della migrazione da Project Server 2010

È necessario tenere presente quanto segue quando si pianifica la migrazione da Project Server 2010:
  
- **Ottieni assistenza di un Partner Microsoft** - l'aggiornamento da Project Server 2010 può essere una sfida e richiede una quantità preparazione e pianificazione. Può essere particolarmente complesso in caso di quello per installare e configurare Project Server 2010 in origine. Fortunatamente, esistono Microsoft Partners è possibile attivare a cui effettuare questa operazione per professione, se si prevede di eseguire la migrazione a Project Server 2019 o a Project Online. È possibile cercare un Partner Microsoft per facilitare la migrazione nel [Centro Partner Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Può coinvolgere backup di un elenco di tutti i Partner Microsoft esperti nel progetto eseguendo una ricerca in termini *Gestione Portfolio e progetto oro* . 
    
- **Pianificare le personalizzazioni** - tenere presente che molte delle personalizzazioni si dispone di utilizzo dell'ambiente Project Server 2010 potrebbe non funzionare durante la migrazione a Project Server 2019 o a Project Online. Non esistono differenze big tra versioni, nonché i sistemi operativi richiesti, server di database e browser client supportati per funzionare con la versione più recente di architettura di Project Server. Disporre di un piano sul posto su come testare o rigenerare le personalizzazioni in base alle esigenze nel nuovo ambiente. Pianificazione per l'aggiornamento sarà anche una buona opportunità per verificare se una personalizzazione a specifica sia effettivamente necessario quando ci si sposta in avanti. [Creare un piano per le personalizzazioni correnti durante l'aggiornamento a SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061) con alcune grande informazioni generali sulla pianificazione per le personalizzazioni correnti durante l'aggiornamento e la valutazione. 
    
- **Tempi e pazienza** - aggiornamento pianificazione, l'esecuzione e test richiede molto tempo e fatica, in particolare se esegue l'aggiornamento a Project Server 2019. Ad esempio, se esegue la migrazione da Project Server 2010 a Project Server 2019, si verrà innanzitutto necessario eseguire la migrazione da Project Server 2010 a Project Server 2013 e controllare i dati e quindi eseguire la stessa operazione durante la migrazione a ciascuna versione successiva (oggetto Project Server 2016 e quindi 2019 Project Server). È possibile contattare un Partner Microsoft per confrontare i costi stimati con le stime del tempo necessario per poter eseguire questa operazione e il relativo costo. 
    
## <a name="migrate-to-project-online"></a>Eseguire la migrazione a Project Online

Se si sceglie di eseguire la migrazione da Project Server 2010 a Project Online, è possibile eseguire le operazioni seguenti per eseguire manualmente la migrazione di dati del piano di progetto:
  
1. Salvataggio da Project Server 2010 per i piani di progetto. Formato di file MPP.
    
2. Utilizzo di Project Professional 2016, Project Professional 2019 o il Client Desktop Project Online, aprire ogni file con estensione mpp, quindi salvare e pubblicare in Project Online.
    
È possibile creare manualmente la configurazione di Project Web Access in Project Online (ad esempio, ricreare eventuali campi personalizzati necessari o i calendari dell'organizzazione). Microsoft Partners consentono inoltre con questa proprietà.
  
Risorse principali:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Introduzione a Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Come installare e utilizzare Project Online.  <br/> |
|[Descrizioni dei servizi in linea di Project](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informazioni sui diversi piani di Project Online sono disponibili.  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Eseguire la migrazione a una nuova versione locale di Project Server

Mentre è fortemente ritiene che è possibile ottenere la migliore esperienza utente e valore eseguendo la migrazione a Project Online, è inoltre la comprensione che alcune organizzazioni necessario mantenere i dati di progetto in un ambiente locale. Se si sceglie di conservare i dati di project in locale, è possibile eseguire la migrazione dell'ambiente Project Server 2010 a Project Server 2013, Project Server 2016 o 2019 di Project Server.
  
È consigliabile eseguire la migrazione a Project Server 2019 se è possibile eseguire la migrazione a Project Online. Project Server 2019 include la maggior parte della chiave le funzionalità e miglioramenti inclusi con le versioni precedenti di Project Server e più simile alla funzionalità disponibili con Project Online (sebbene alcune caratteristiche sono disponibili solo in Project Online).
  
Al termine di ogni migrazione, è necessario controllare i dati per verificare che sia migrati correttamente.
  
> [!NOTE]
> Se si prevede di migrazione a Project Server 2013 solo se si è limitato a una soluzione locale, è importante notare che ha solo pochi anni più di supporto da sinistra. Project Server 2013 con Service Pack 2 è fine del supporto data 13/10/2023. Per ulteriori informazioni sulla fine del periodo di supporto, vedere [Ciclo di vita del prodotto Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066). 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Come è possibile eseguire la migrazione a Project Server 2019?

Le differenze tra Project Server 2010 e Project Server 2019 dell'architettura impedisce a un percorso di migrazione diretto. Ciò significa che è necessario eseguire la migrazione dei dati di Project Server 2010 a dalla prossima versione successiva di Project Server fino a quando l'aggiornamento a Project Server 2019.
  
È necessario eseguire le operazioni seguenti per l'aggiornamento a Project Server 2019:
  
1. Passaggio 1: Eseguire la migrazione dei dati da Project Server 2010 a Project Server 2013.
    
2. Passaggio 2: Eseguire la migrazione dei dati di Project 2013 servire 2016 di Project Server.
    
3. Passaggio 3: Eseguire la migrazione dei dati da Project Server 2016 2019 di Project Server.
    
Al termine di ogni migrazione, è necessario controllare i dati per verificare che sia migrati correttamente.
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>Passaggio 1: Eseguire la migrazione a Project Server 2013

Il primo passaggio della migrazione dei dati di Project Server 2010 a Project Server 2019 viene innanzitutto eseguire la migrazione a Project Server 2013. 
  
Per una spiegazione esauriente del è necessario eseguire l'aggiornamento da Project Server 2010 a Project Server 2013, vedere il set di contenuti di [eseguire l'aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) in TechNet. 
  
Risorse principali:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Panoramica del processo di aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |È possibile ottenere una conoscenza generale di è necessario eseguire l'aggiornamento da Project Server 2010 a Project Server 2013.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Esaminare pianificazione che è necessario prendere in fase di aggiornamento da Project Server 2010 a Project Server 2013, inclusi i requisiti di sistema.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Aspetti da conoscere l'aggiornamento alla versione corrente

[Novità dell'aggiornamento di Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) fornisce le informazioni importanti modifiche per l'aggiornamento per questa versione, da più importanti: 
  
- Non esiste alcun aggiornamento sul posto a Project Server 2013. Il collegamento di database metodo è l'unico metodo supportato per l'aggiornamento da Project Server 2010 a Project Server 2013.
    
- Il processo di aggiornamento non solo la conversione dei dati di Project Server 2010 nel formato Project Server 2013, ma verrà inoltre consolidare i quattro database di Project Server 2010 in un unico database di Project Web App.
    
- Sia SharePoint Server 2013 e Project Server 2013 modificato dalla versione precedente per l'autenticazione basata sulle attestazioni. È necessario apportare considerazioni durante l'aggiornamento se si utilizza l'autenticazione classica. Per ulteriori informazioni, vedere [eseguire la migrazione dall'autenticazione in modalità classica all'autenticazione basata sulle attestazioni in SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Risorse aggiuntive:
  
- [Panoramica del processo di aggiornamento a Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Aggiornare i database e le raccolte siti di Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramma del processo di aggiornamento Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Il consolidamento dei Database grande, Project Server 2010 per 2013 Migration 8 semplici passaggi](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>Passaggio 2 eseguire la migrazione a Project Server 2016

Dopo la migrazione a Project Server 2013 e verificare che sia sono eseguita correttamente la migrazione dei dati, il passaggio successivo consiste nel migrare i dati in Project Server 2016.
  
Per informazioni complete sulle operazioni da eseguire per l'aggiornamento da Project Server 2013 a Project Server 2016, vedere il set di contenuti di [eseguire l'aggiornamento a Project Server 2016](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Risorse principali:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Panoramica del processo di aggiornamento a Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |È possibile ottenere una conoscenza generale di è necessario per l'aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Esaminare le considerazioni di pianificazione che è necessario prendere in fase di aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Aspetti da conoscere l'aggiornamento alla versione corrente

[Aspetti da tenere presente relativamente a Project Server 2016 aggiornamento](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) fornisce le informazioni importanti modifiche per l'aggiornamento per questa versione, che comprendono: 
  
- Quando si crea l'ambiente Project Server 2016 a cui verrà eseguita la migrazione dei dati di Project Server 2013, tenere presente che i file di installazione di Project Server 2016 sono inclusi in SharePoint Server 2016. Per ulteriori informazioni, vedere [distribuzione di Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Piani delle risorse sono deprecati in Project Server 2016. I piani delle risorse di Project Server 2013 viene migrati per interventi di risorse in Project Server 2016 e in Project Online. Vedere [Overview: Engagement per i risorse](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) per ulteriori informazioni. 
    
### <a name="step-3-migrate-to-project-server-2019"></a>Passaggio 3 migrazione a Project Server 2019

Dopo la migrazione a Project Server 2016 e verificare che sia sono eseguita correttamente la migrazione dei dati, il passaggio successivo consiste nel migrare i dati in Project Server 2019.
  
Per informazioni complete sulle operazioni da eseguire per l'aggiornamento da Project Server 2016 a Project Server 2019, vedere il set di contenuti di [eseguire l'aggiornamento a Project Server 2019](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016) .
  
Risorse principali:
  
|**Risorsa**|**Descrizione**|
|:-----|:-----|
|[Processo di aggiornamento di panoramica del 2019 di Project Server](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |È possibile ottenere una conoscenza generale di è necessario per l'aggiornamento da Project Server 2013 a Project Server 2016.  <br/> |
|[Pianificare l'aggiornamento a Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Esaminare le considerazioni di pianificazione che è necessario prendere in fase di aggiornamento da Project Server 2016 a Project Server 2019.  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Aspetti da conoscere l'aggiornamento alla versione corrente

[Aspetti da tenere presente relativamente a Project Server 2019 aggiornamento](https://go.microsoft.com/fwlink/p/?linkid=841827) fornisce le informazioni importanti modifiche per l'aggiornamento per questa versione, che comprendono: 
  
- Il processo di aggiornamento sarà la migrazione dei dati dal database di Project Server 2016 al database del contenuto di SharePoint Server 2019.  Project Server 2019 non tempo lo creerà è proprietario del database di Project Server nella farm di SharePoint Server.

- Dopo l'aggiornamento, tenere conto delle diverse modifiche in Project Web App.  Per una descrizione di queste, vedere [What's new in Project Server 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).


## <a name="migrate-from-portfolio-server-2010"></a>Eseguire la migrazione da Portfolio Server 2010

Project Portfolio Server 2010 è stato utilizzato con Project Server 2010 per l'ottimizzazione, ordine di priorità e strategia portfolio. Nessun altre versioni di Project Portfolio Server sono stati creati dopo la versione corrente. Funzionalità di gestione del portfolio, tuttavia, sono disponibili nelle versioni successive di Project Server e la versione Premium di Project Online. Impossibile eseguire la migrazione di dati da Project Portfolio Server 2010 a uno. Dati, ad esempio i driver di business dovranno essere ricreate.
  
Altre risorse:
  
- [Descrizioni dei servizi di Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): fare riferimento alle funzionalità di gestione portfolio inclusi in Project Server 2016 e Project Online Premium.
    
- [Guida alla migrazione di Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Argomenti correlati

[Aggiornamento da SharePoint 2010](upgrade-from-sharepoint-2010.md)
  
[Risorse che consentono di eseguire l'aggiornamento da Office 2010 server e client](upgrade-from-office-2010-servers-and-products.md)
  

