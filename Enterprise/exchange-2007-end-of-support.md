---
title: Guida sulla fine del supporto di Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
description: In 11 aprile 2017, Exchange Server 2007 stata raggiunta la fine del supporto tecnico. Se non sono già iniziato la migrazione da Exchange 2007 a Office 365 o Exchange 2016, è ora per avviare la pianificazione.
ms.openlocfilehash: 674de8904d03e024a8a75b945b5ef94319214f92
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915571"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Guida sulla fine del supporto di Exchange 2007

In **11 aprile 2017**, Exchange Server 2007 stata raggiunta la fine del supporto tecnico. Se non sono già iniziato la migrazione da Exchange 2007 a Office 365 o Exchange 2016, è ora per avviare la pianificazione. 
  
## <a name="what-does-end-of-support-mean"></a>Quali fine consente di supporto Media?

Exchange Server, come quasi tutti i prodotti Microsoft, dispone di un ciclo di vita del supporto durante il quale si forniscono le nuove funzionalità, correzioni, correzioni rapide per la sicurezza e così via. Questo ciclo di vita dura in genere per 10 anni dalla data di rilascio iniziale del prodotto e fine di questo ciclo di vita è noto come fine del prodotto del supporto tecnico. Poiché Exchange 2007 raggiunta la fine del supporto di 11 aprile 2017, non è più disponibile:
  
- Supporto tecnico per i problemi che possono verificarsi;
    
- Correzioni degli errori per i problemi che vengono individuate e che possono influenzare la stabilità e l'usabilità di server.
    
- Le patch di protezione per le vulnerabilità che vengono individuate e che potrebbe essere vulnerabile ad attacchi di violazioni della protezione, il server
    
- Aggiornamenti di fuso orario.
    
L'installazione di Exchange 2007 continua a eseguire dopo tale data. Tuttavia, a causa di modifiche elencate in precedenza, è consigliabile eseguire la migrazione da Exchange 2007 più presto possibile.
  
Per ulteriori informazioni di supporto termina il server di Office 2007, vedere [pianificare l'aggiornamento dal server di Office 2007 e prodotti](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Che cosa sono le opzioni disponibili.

Ora che Exchange 2007 è stata raggiunta la fine del supporto, è consigliabile considerare le opzioni e preparare un piano di migrazione. Si può:
  
- Eseguire la migrazione a Office 365 utilizzando completa, in fasi o migrazione ibrida;
    
- Eseguire la migrazione di server Exchange 2007 a una versione più recente di Exchange sui server locale.
    
Nelle sezioni seguenti utilizzando ogni opzione in modo più dettagliato.
  
### <a name="migrate-to-office-365"></a>Eseguire la migrazione a Office 365

Migrare la posta elettronica a Office 365 è l'opzione migliore e più semplice che consente di ritirare la distribuzione di Exchange 2007. Migrazione a Office 365, è possibile effettuare un singolo hop da 10 anni tecnologia alle funzionalità di sistema all'avanguardia, ad esempio:
  
- Funzionalità di conformità, come i criteri di conservazione, sul posto e conservazione per controversia legale, in-place eDiscovery e ulteriori;
    
- Gruppi di Office 365.
    
- Cartella Posta in arrivo previsto;
    
- Approfondire Analitica;
    
- API REST per l'accesso programmatico a posta elettronica, calendario, contatti e così via.
    
Office 365 inoltre Ottiene esperienze e nuove caratteristiche prima e i singoli utenti possono in genere iniziare a utilizzare immediatamente. Oltre a nuove funzionalità, non sarà necessario preoccupare:
  
- Acquisto e manutenzione di hardware,
    
- Prestando riscaldamento e raffreddamento dei server;
    
- Mantenere aggiornati su correzioni della protezione, prodotto e fuso orario.
    
- Gestione di archiviazione e il software per supportare i requisiti di conformità;
    
- L'aggiornamento a una nuova versione di Exchange - si è sempre alla versione più recente di Exchange in Office 365.
    
#### <a name="how-should-i-migrate-to-office-365"></a>Come è deve essere implementata la migrazione a Office 365?

A seconda dell'organizzazione, sono disponibili alcune opzioni che saranno consentono a Office 365. Quando si sceglie l'opzione di migrazione, è necessario prendere in considerazione alcuni aspetti quali il numero di postazioni o è necessario spostare le cassette postali, per quanto tempo si desidera la migrazione all'ultima e se è necessaria una facile integrazione tra Office 365 durante l'installazione locale e la migrazione. Questa tabella mostra le opzioni di migrazione e i fattori più importanti che è necessario determinare quale metodo si vuole usare.
  
| |
|**Opzione di migrazione**|**Dimensioni dell'organizzazione**|**Durata**|
|:-----|:-----|:-----|
|Migrazione completa  <br/> |Meno di 150 postazioni  <br/> |Una settimana o minore di  <br/> |
|Migrazione in fasi  <br/> |Più di 150 postazioni  <br/> |Alcune settimane  <br/> |
|Migrazione ibrida completa  <br/> |Diverse centinaia di migliaia di postazioni  <br/> |Alcuni mesi o più  <br/> |
   
Nelle sezioni seguenti offrono una panoramica di questi metodi. Estrarre [stabilire su un percorso di migrazione](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) per informazioni dettagliate di ogni metodo. 
  
#### <a name="cutover-migration"></a>Migrazione completa

Migrazione completa è una cui, una pre-data e un'ora, vuoi migrare tutte le cassette postali, gruppi di distribuzione, contatti e così via, di Office 365; al termine, si verrà Arresta server Exchange locale e iniziare a utilizzare Office 365 in modo esclusivo.
  
Il metodo di migrazione completa è ideale per organizzazioni di piccole dimensioni che non hanno molto numero di cassette postali, ottenere rapidamente a Office 365 e non si desidera gestire alcuni dei complessità degli altri metodi. È anche un po' limitato dal momento che deve essere completato una settimana o meno e richiede agli utenti di riconfigurare i profili di Outlook. Durante la migrazione completa in grado di gestire fino a 2.000 cassette postali, si consiglia che la migrazione di un massimo di cassette 150 postali con questo metodo. Se si tenta di eseguire la migrazione delle cassette postali più di 150, può essere eseguito da tempo per il trasferimento di tutte le cassette postali prima la scadenza e del supporto IT possono ottenere personale sovraccarico che consentono agli utenti di riconfigurare Outlook.
  
Se si sta valutando eseguendo una migrazione completa, ecco prendere in considerazione alcuni aspetti da considerare:
  
- Office 365, sarà necessario connettersi al server Exchange 2007 utilizzando Outlook via Internet tramite la porta TCP 443;
    
- Verranno spostate tutte le cassette postali locali a Office 365;
    
- È necessario un account di amministratore locale che dispone di accesso per leggere il contenuto delle cassette postali degli utenti;
    
- Exchange 2007 accettate domini che si desidera utilizzare in Office 365 devono da aggiungere come domini verificati il servizio.
    
- Tra il momento di avviare la migrazione e quando si inizia la fase di completamento, Office 365 sincronizzerà periodicamente di Office 365 e cassette postali locali. Consente di eseguire la migrazione senza doversi preoccupare posta elettronica vengono lasciato presenti nelle cassette postali locale;
    
- Gli utenti riceveranno nuove password temporanea per il proprio account di Office 365 di cui hanno bisogno per passare al momento dell'accesso alle cassette postali per la prima volta.
    
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
    
- Gli utenti saranno necessario configurare un nuovo profilo di Outlook in ognuno dei dispositivi e scaricare nuovamente il messaggio di posta elettronica. La quantità di posta elettronica che vengono scaricate può variare. Per ulteriori informazioni, dare uno sguardo al [modificare la quantità mail per mantenere non in linea](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Per ulteriori informazioni sulla migrazione completa, esaminare:
  
- [È necessario tenere presente relativamente a una migrazione completa di posta elettronica a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Eseguire una migrazione totale di messaggi di posta elettronica a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migrazione in fasi

Migrazione in fasi è uno di cui si dispone di alcune centinaia o alcune migliaia di cassette postali che si desidera eseguire la migrazione a Office 365, è necessario eseguire una settimana o più per completare la migrazione e non necessario qualsiasi delle caratteristiche di migrazione ibrida avanzate come informazioni di calendario sulla disponibilità condivise endali.
  
Migrazione a fasi è ideale per le aziende che è necessario richiedere più tempo per eseguire la migrazione di cassette postali a Office 365, ma ancora prevede di eseguire la migrazione entro pochi settimane. È possibile eseguire la migrazione delle cassette postali in "batch" che consentono di controllare il numero e il, vengono eseguita la migrazione delle cassette postali in un momento specifico. Si potrebbero in blocco delle cassette postali degli utenti dello stesso reparto, ad esempio, per assicurarsi che vengono tutte spostate contemporaneamente. In alternativa, può lasciare le cassette postali executive finché l'ultimo batch. Come migrazioni complete, gli utenti saranno necessario ricreare i profili di Outlook.
  
Se si sta valutando eseguendo una migrazione in fasi, ecco alcuni aspetti da considerare:
  
- Office 365, sarà necessario connettersi al server Exchange 2007 utilizzando Outlook via Internet tramite la porta TCP 443;
    
- È necessario un account di amministratore locale che dispone di accesso per leggere il contenuto delle cassette postali degli utenti;
    
- Exchange 2007 accettate domini che si desidera utilizzare in Office 365 devono da aggiungere come domini verificati il servizio.
    
- È necessario creare un file CSV con il nome completo e indirizzo di ciascuna cassetta postale che si desidera eseguire la migrazione di un batch di posta elettronica. Sarà inoltre necessario includere una nuova password per ciascuna cassetta postale che si sta eseguendo la migrazione e quindi inviare la password per ogni utente. L'utente verrà richiesto di modificare la password la prima volta che accedono alle cassette postali di Office 365 nuovo;
    
- Tra il momento si avvia il batch di migrazione e quando si inizia la fase di completamento, Office 365 sincronizzerà periodicamente incluse nel batch di cassette postali di Office 365 e locali. Consente di eseguire la migrazione senza doversi preoccupare posta elettronica vengono lasciato presenti nelle cassette postali locale;
    
- Gli utenti riceveranno nuove password temporanea per il proprio account di Office 365 di cui hanno bisogno per passare al momento dell'accesso nella propria cassetta postale per la prima volta.
    
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
    
- Gli utenti saranno necessario configurare un nuovo profilo di Outlook in ognuno dei dispositivi e scaricare nuovamente il messaggio di posta elettronica. La quantità di posta elettronica che vengono scaricate può variare. Per ulteriori informazioni, dare uno sguardo al [modificare la quantità mail per mantenere non in linea](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).
    
Per ulteriori informazioni sulla migrazione a fasi, esaminare:
  
- [È necessario tenere presente relativamente a una migrazione in fasi di posta elettronica a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Eseguire una migrazione in fasi di posta elettronica a Office 365](https://support.office.com/en-us/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Ibrida completa

Una migrazione completa ibrida è uno in cui l'organizzazione dispone di centinaia, fino a decine di migliaia di cassette postali e si desidera spostare alcuni o tutti gli utenti a Office 365. Poiché le migrazioni sono in genere più lungo termine, migrazioni ibride consentono di:
  
- Visualizzare le informazioni di disponibilità del calendario per gli utenti gli utenti locali in Office 365 e viceversa.
    
- Visualizzare un elenco indirizzi globale unificato che contiene destinatari in locali e di Office 365;
    
- Visualizzare complete schede dei destinatari di Outlook per tutti gli utenti, indipendentemente dal fatto che essi si locale o in Office 365,
    
- Proteggere le comunicazioni di posta elettronica tra i server Exchange locali e Office 365 tramite TLS e certificati.
    
- Gestire i messaggi inviati tra i server Exchange locali e Office 365 come interni, che consente di:
    
  - Valutare ed elaborate dagli agenti di trasporto e di conformità assegnazione messaggi interni, in modo corretto
    
  - Ignorare i filtri di protezione da posta indesiderati.
    
Migrazioni ibride completa sono la soluzione migliore per le organizzazioni che prevedono la possibilità di mantenersi in una configurazione ibrida per numero di mesi o più. Si otterranno le funzionalità elencate in precedenza in questa sezione, nonché la sincronizzazione delle directory, migliori funzionalità di conformità integrata e la possibilità di spostare le cassette postali da e verso Office 365 utilizzando spostamenti delle cassette postali in linea. Office 365 diventa un'estensione dell'organizzazione locale.
  
Se si sta valutando eseguendo una migrazione completa ibrida, ecco alcuni aspetti da considerare:
  
- Migrazioni ibride completo non sono appropriate per tutti i tipi di organizzazioni. A causa della complessità delle migrazioni ibride completa, le organizzazioni con meno di alcune cassette centinaia postali non viene visualizzato in genere i benefici giustificano il lavoro e dei costi necessari per configurare uno. Se questo sembra nell'organizzazione, è consigliabile prendere in considerazione le migrazioni Cutover o in fasi.
    
- È necessario distribuire almeno un server di Exchange 2013 nell'organizzazione di Exchange 2007 che funga da un "server ibrido". Il server comunicherà con Office 365 per conto del server Exchange 2007;
    
- Office 365, sarà necessario connettersi a "server" ibrido tramite Outlook via Internet tramite la porta TCP 443;
    
- È necessario configurare la sincronizzazione delle directory con Azure Active Directory la connessione (AADConnect) tra i server di Active Directory locali e Office 365;
    
- Gli utenti saranno in grado di eseguire l'accesso alle cassette postali di Office 365 utilizzando lo stesso nome utente e password che utilizzano al momento dell'accesso in rete locale (richiede la connessione di Azure Active Directory con la sincronizzazione delle password e/o Active Directory Federation Services).
    
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
    
- Gli utenti non è necessario configurare un nuovo profilo di Outlook nella maggior parte dei dispositivi (alcuni telefoni Android precedenti potrebbe essere necessario un nuovo profilo) e non sono più necessari per il download nuovamente il messaggio di posta elettronica.
    
Se un suoni di migrazione completa ibrida appropriata, esaminare le risorse seguenti per facilitare la migrazione:
  
- [Assistente per la distribuzione di Exchange](https://aka.ms/exdeploy)
    
- [Distribuzioni ibride di Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
    
- [Configurazione ibrida guidata](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
    
- [Domande frequenti sulla configurazione ibrida guidata](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
    
- [Prerequisiti per la distribuzione ibrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Eseguire la migrazione a una versione più recente di Exchange Server

Mentre è fortemente ritiene che è possibile ottenere la migliore esperienza utente e valore eseguendo la migrazione a Office 365, è inoltre la comprensione che alcune organizzazioni è necessario mantenere i messaggio di posta elettronica locale. Questo può essere dovuto ai requisiti normativi, garantire dati non viene archiviato in un centro dati che si trova in un altro paese e così via. Se si sceglie di conservare i messaggio di posta elettronica locale, è possibile eseguire la migrazione dell'ambiente di Exchange 2007 a Exchange 2010, Exchange 2013 o 2016 Exchange.
  
È consigliabile eseguire la migrazione a Exchange 2016 se è possibile eseguire la migrazione a Office 365. Exchange 2016 include tutte le funzionalità e miglioramenti inclusi con le versioni precedenti di Exchange e corrisponde maggiormente l'esperienza disponibile con Office 365 (sebbene alcune caratteristiche sono disponibili solo in Office 365). Estrarre alcuni dei fattori che è stati pienamente di tutte le:
  
|**Versione di Exchange**|**Caratteristiche**|
|:-----|:-----|
|Exchange 2010  <br/> | Role Based Access Control (autorizzazioni senza ACL)  <br/>  Criteri cassetta postale di Outlook Web Access  <br/>  Possibilità di condividere libero/occupato e delegare i calendari tra organizzazioni  <br/> |
|Exchange 2013  <br/> | *Funzionalità di Exchange 2010 e...*  <br/>  Architettura semplificata la riduzione del numero dei ruoli del server a tre (Trasporto Edge di cassette postali, accesso Client,)  <br/>  Perdita prevenzione criteri dati (DLP) che consentono di mantenere la perdita di informazioni riservate  <br/>  In modo significativo Outlook Web App esperienza migliorata  <br/> |
|Exchange 2016  <br/> | *Funzionalità di Exchange 2013 e...*  <br/>  Altri ruoli del server semplificata solo delle cassette postali e Trasporto Edge  <br/>  DLP migliorata e integrazione con SharePoint  <br/>  Resilienza dei database migliorato  <br/>  Collaborazione sui documenti online  <br/> |
   
#### <a name="which-version-should-i-migrate-to"></a>Quale versione deve essere implementata la migrazione a?

È consigliabile inizialmente presuppongono che consente la migrazione a Exchange 2016. Utilizzare le informazioni seguenti per verificare i presupposti oppure per escludere 2016 Exchange. Se non è possibile migrare a Exchange 2016 per uno dei motivi o un altro, la stessa elaborare con Exchange 2013 e così via.
  
|**Considerazione**|**Ulteriori informazioni**|
|:-----|:-----|
|Fine del periodo di supporto  <br/> | Come Exchange 2007, ogni versione di Exchange ha il proprio fine del periodo supportato:  <br/> **Exchange 2010** - gennaio 2020  <br/> **Exchange 2013** - aprile 2023  <br/> **Exchange 2016** - 2025 ottobre  <br/>  Prima fine del supporto di data, prima sarà necessario eseguire la migrazione di un'altra. Gennaio 2020 è molto più vicino di quanto sembri!<br/> |
|Percorso di migrazione a Exchange 2010 e 2013  <br/> |Di seguito sono le fasi generali per la migrazione a Exchange 2010 o Exchange 2013:  <br/> Installazione di Exchange 2010 o 2013 nei servizi di spostamento dell'organizzazione di Exchange 2007 esistenti e altre infrastrutture a Exchange 2010 o 2013 spostamento delle cassette postali e cartelle pubbliche in Exchange 2010 o 2013 Decommission rimanenti server Exchange 2007 |
|Percorso di migrazione a Exchange 2016  <br/> |Di seguito sono le fasi generali per la migrazione a Exchange 2016:  <br/> Installare Exchange 2013 nei servizi di spostamento dell'organizzazione di Exchange 2007 esistenti e altre dell'infrastruttura per le cassette postali di Exchange 2013 Move e le cartelle pubbliche di Exchange 2013 Decommission rimanente 2016 Exchange installare server di Exchange 2007 esistenti Organizzazione di Exchange 2013. Spostare le cassette postali, le cartelle pubbliche, servizi e altre infrastruttura Exchange 2016 (ordine non ha alcuna importanza). Rimuovere il server di Exchange 2013 rimanenti > [!NOTE]> migrazione da Exchange 2013 a Exchange 2016 è semplice. Entrambe le versioni hanno quasi gli stessi requisiti hardware. Ciò e fatti che sono le versioni in modo compatibile, indica che è possibile ricreare un server di Exchange Server 2013 è stato acquistato e installare Exchange 2016 su di esso. E con spostamenti delle cassette postali online, gli utenti in genere mai noterà delle relative cassette postali da spostare disattivare il server e quindi nuovamente dopo che è stato ricostruito con Exchange 2016.           |
|Coesistenza della versione  <br/> | Durante la migrazione a:  <br/> **Exchange 2016** Exchange 2016 non può essere installato in un'organizzazione che include un server Exchange 2007. È innanzitutto necessario eseguire la migrazione a Exchange 2010 o 2013 (è consigliabile Exchange 2013), rimuovere tutti i server Exchange 2007 e quindi eseguire la migrazione a Exchange 2016.<br/> **Exchange 2010 o Exchange 2013** È possibile installare Exchange 2010 o Exchange 2013 nell'organizzazione di Exchange 2007 esistente. In questo modo è possibile installare uno o più Exchange 2010 o 2013 server ed eseguire la migrazione.<br/> |
|Hardware dei server  <br/> | Requisiti hardware dei server sono state modificate da Exchange 2007. È necessario verificare che sia compatibile con i componenti hardware che si desidera utilizzare. È possibile trovare ulteriori informazioni sui requisiti hardware per ogni versione di seguito:<br/> [Requisiti di sistema di Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx) <br/> [Requisiti di sistema di Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx) <br/> [Requisiti di sistema di Exchange 2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx) <br/>  Si noterà che con notevoli miglioramenti delle prestazioni di Exchange, e aumentare la potenza e la capacità di archiviazione in server più recenti, sarà necessario meno server per supportare lo stesso numero di cassette postali.  <br/> |
|Versione del sistema operativo  <br/> | Le versioni del sistema operativo minimo supportato per ogni versione sono:  <br/> **Exchange 2016** Windows Server 2012  <br/> **Exchange 2013** Windows Server 2008 R2 SP1  <br/> **Exchange 2010** Windows Server 2008 SP2  <br/>  È possibile trovare ulteriori informazioni sul supporto dei sistemi operativi nella [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Livello di funzionalità di Active Directory foresta  <br/> | Il minimo supportato foresta niveaux fonctionnels Active Directory per ogni versione sono:  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  È possibile trovare ulteriori informazioni sul supporto di livello funzionale di foresta nella [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
|Versioni client di Office  <br/> | Le versioni client Office supportate minime per ogni versione sono:  <br/> **Exchange 2016** Office 2010 (con gli aggiornamenti più recenti)  <br/> **Exchange 2013** Office 2007 SP3  <br/> **Exchange 2010** Office 2003  <br/>  È possibile trovare ulteriori informazioni sul supporto di client Office a [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).  <br/> |
   
#### <a name="how-do-i-migrate"></a>Come eseguire la migrazione?

Se si è deciso che si desidera mantenere i messaggio di posta elettronica locale, è possibile utilizzare le risorse seguenti per facilitare la migrazione:
  
- [Assistente per la distribuzione di Exchange](https://aka.ms/exdeploy)
    
- Active Directory schema le modifiche per Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- Requisiti di sistema per Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.141%29.aspx)
    
- Prerequisiti di Exchange, [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx), [2010](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.141%29.aspx)
    
## <a name="what-if-i-need-help"></a>Cosa succede se ho bisogno di assistenza?

Se si sta eseguendo la migrazione a Office 365, potrebbe essere idonei per utilizzare il servizio Microsoft FastTrack. FastTrack fornisce consigliate, strumenti e risorse per effettuare la migrazione a Office 365 il più agevole possibile. È necessario che tutto ciò tecnico reale di esaminare la migrazione di pianificazione e progettare completamente alla migrazione delle cassette postali ultima. Se si desidera fornire ulteriori informazioni FastTrack, dare uno sguardo al [FastTrack Microsoft](https://fasttrack.microsoft.com/).
  
Se riscontrano problemi durante la migrazione a Office 365 e non si utilizza FastTrack o la migrazione a una versione più recente di Exchange Server, siamo a tua disposizione per. Di seguito sono riportate alcune risorse che è possibile utilizzare:
  
- [Community di documentazione tecnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
    
- [Assistenza clienti](https://support.microsoft.com/en-us/gp/support-options-for-business)
    
## <a name="related-topics"></a>Argomenti correlati

[Risorse che consentono di eseguire l'aggiornamento di Office 2007 Server e client](upgrade-from-office-2007-servers-and-products.md)
  
[Gruppo pensionistico per Office (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
  

