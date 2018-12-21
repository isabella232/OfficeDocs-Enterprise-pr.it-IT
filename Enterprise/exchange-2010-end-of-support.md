---
title: Exchange 2010 fine del supporto roadmap
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
description: Exchange 2010 sta raggiungendo fine del supporto tecnico. Utilizzare questa Guida di orientamento pianificazione come guida per preparare l'aggiornamento a Exchange Online o una versione più recente di Exchange Server locale.
ms.openlocfilehash: d9dcc2120f549c55fedc78483689dbded0a4464f
ms.sourcegitcommit: b45ad32a0a421d9834424e02838b6f941c259b9b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "27382697"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Exchange 2010 fine del supporto roadmap

Su **14 gennaio 2020**, Exchange Server 2010 verrà raggiunta fine del supporto tecnico. Se non sono già iniziato la migrazione da Exchange 2010 a Office 365 o Exchange 2016, è ora per avviare la pianificazione.

## <a name="what-does-end-of-support-mean"></a>Quali fine consente di supporto Media?

Exchange Server, come quasi tutti i prodotti Microsoft, dispone di un ciclo di vita del supporto durante il quale si forniscono le nuove funzionalità, correzioni, correzioni rapide per la sicurezza e così via. Questo ciclo di vita dura in genere per 10 anni dalla data di rilascio iniziale del prodotto e fine di questo ciclo di vita è noto come fine del prodotto del supporto tecnico. Quando Exchange 2010 raggiunge la fine del supporto di 14 gennaio 2020, Microsoft non fornirà più:

- Supporto tecnico per i problemi che possono verificarsi;
- Correzioni degli errori per i problemi che vengono individuate e che possono influenzare la stabilità e l'usabilità di server.
- Le patch di protezione per le vulnerabilità che vengono individuate e che potrebbe essere vulnerabile ad attacchi di violazioni della protezione, il server
- Aggiornamenti di fuso orario.

L'installazione di Exchange 2010 continua a eseguire dopo tale data. Tuttavia, a causa di modifiche elencate in precedenza, è consigliabile eseguire la migrazione da Exchange 2010 più presto possibile.

Per ulteriori informazioni di supporto termina il server di Office 2010, vedere [le risorse che consentono di eseguire l'aggiornamento da Office 2010 server e client](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products).

## <a name="what-are-my-options"></a>Che cosa sono le opzioni disponibili.

Con Exchange 2010 sta per raggiungere la fine del supporto, questo è il momento giusto per esplorare le opzioni e preparare un piano di migrazione. Si può:

- Esegue la migrazione completa a Office 365. Eseguire la migrazione delle cassette postali ibridi completa, minimo o migrazione ibrida completa e quindi remove locale Active Directory e dei server di Exchange.
- Eseguire la migrazione di server Exchange 2010 a Exchange 2016 nei server locali.

> [!IMPORTANT]
> Se l'organizzazione decide di eseguire la migrazione delle cassette postali a Office 365, ma si propone di conservare DirSync o della connessione di Azure Active Directory sul posto per continuare la gestione degli account utente da Active Directory locale, è necessario tenere presente almeno un Exchange server locale. Se viene rimosso l'ultimo server di Exchange, non sarà in grado di apportare modifiche ai destinatari di Exchange in Exchange Online. Ciò avviene perché l'origine dell'autorità rimane in Active Directory locale e modifiche devono essere resi disponibili. In questo scenario sono disponibili le opzioni seguenti:

- (**Scelta consigliata**) Se è possibile eseguire la migrazione delle cassette postali a Office 365 e aggiornare i server per il 14 giugno 2020, utilizzare Exchange 2010 per connettersi a Office 365 ed eseguire la migrazione delle cassette postali. Successivamente, eseguire la migrazione di Exchange 2010 a Exchange 2016 e rimuovere eventuali altri server Exchange 2010.
- Se non è possibile completare la migrazione delle cassette postali e aggiornamento del server locale per il 14 giugno 2020, aggiornare i server di Exchange 2010 locale a Exchange 2016 prima, utilizzare Exchange 2016 per connettersi a Office 365 ed eseguire la migrazione delle cassette postali.

> [!NOTE]
> Mentre un po' più complessa, è possibile migrare le cassette postali durante la migrazione di server Exchange 2010 locale a Exchange 2016 a Office 365.

Nelle sezioni seguenti utilizzando ogni opzione in modo più dettagliato.

## <a name="migrate-to-office-365"></a>Eseguire la migrazione a Office 365

Migrare la posta elettronica a Office 365 è l'opzione migliore e più semplice che consente di ritirare la distribuzione di Exchange 2010. Migrazione a Office 365, è possibile effettuare un hop singolo dalla tecnologia precedente alle funzionalità di punta, ad esempio:

- Funzionalità di conformità, come i criteri di conservazione, sul posto e conservazione per controversia legale, in-place eDiscovery e ulteriori;
- Team di Microsoft;
- Power BI;
- Cartella Posta in arrivo previsto;
- Approfondire Analitica;

Office 365 inoltre Ottiene esperienze e nuove caratteristiche prima e i singoli utenti possono in genere iniziare a utilizzare immediatamente. Oltre a nuove funzionalità, non sarà necessario preoccupare:

- Acquisto e manutenzione di hardware,
- Prestando riscaldamento e raffreddamento dei server;
- Mantenere aggiornati su correzioni della protezione, prodotto e fuso orario.
- Gestione di archiviazione e il software per supportare i requisiti di conformità;
- L'aggiornamento a una nuova versione di Exchange - si è sempre alla versione più recente di Exchange in Office 365.

### <a name="how-should-i-migrate-to-office-365"></a>Come è deve essere implementata la migrazione a Office 365?

A seconda dell'organizzazione, sono disponibili alcune opzioni che saranno consentono a Office 365. Quando si sceglie l'opzione di migrazione, è necessario prendere in considerazione alcuni aspetti quali il numero di postazioni o è necessario spostare le cassette postali, per quanto tempo si desidera la migrazione all'ultima e se è necessaria una facile integrazione tra Office 365 durante l'installazione locale e la migrazione. Questa tabella mostra le opzioni di migrazione e i fattori più importanti che è necessario determinare quale metodo si vuole usare.

| **Opzione di migrazione**     | **Dimensioni dell'organizzazione** | **Durata**        |
|--------------------------|-----------------------|---------------------|
| Migrazione completa        | Meno di 150 postazioni  | Una settimana o minore di      |
| Migrazione ibrida minimo | Meno di 150 postazioni  | Alcune settimane o minore di |
| Migrazione ibrida completa    | Più di 150 postazioni   | Alcune settimane o più |

Nelle sezioni seguenti offrono una panoramica di questi metodi. Estrarre [stabilire su un percorso di migrazione](https://support.office.com/en-us/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) per informazioni dettagliate di ogni metodo.

### <a name="cutover-migration"></a>Migrazione completa

Migrazione completa è una cui, una pre-data e un'ora, vuoi migrare tutte le cassette postali, gruppi di distribuzione, contatti e così via, di Office 365; al termine, si verrà Arresta server Exchange locale e iniziare a utilizzare Office 365 in modo esclusivo.

Il metodo di migrazione completa è ideale per organizzazioni di piccole dimensioni che non hanno molto numero di cassette postali, ottenere rapidamente a Office 365 e non si desidera gestire alcuni dei complessità degli altri metodi. È anche un po' limitato dal momento che deve essere completato una settimana o meno e richiede agli utenti di riconfigurare i profili di Outlook. Durante la migrazione completa in grado di gestire fino a 2.000 cassette postali, si consiglia che la migrazione di un massimo di cassette 150 postali con questo metodo. Se si tenta di eseguire la migrazione delle cassette postali più di 150, può essere eseguito da tempo per il trasferimento di tutte le cassette postali prima la scadenza e del supporto IT possono ottenere personale sovraccarico che consentono agli utenti di riconfigurare Outlook.

Se si sta valutando eseguendo una migrazione completa, ecco prendere in considerazione alcuni aspetti da considerare:

- Office 365, sarà necessario connettersi al server Exchange 2010 utilizzando Outlook via Internet tramite la porta TCP 443;
- Verranno spostate tutte le cassette postali locali a Office 365;
- È necessario un account di amministratore locale che dispone di accesso per leggere il contenuto delle cassette postali degli utenti;
- Exchange 2010 accettate domini che si desidera utilizzare in Office 365 devono da aggiungere come domini verificati il servizio.
- Tra il momento di avviare la migrazione e quando si inizia la fase di completamento, Office 365 sincronizzerà periodicamente di Office 365 e cassette postali locali. Consente di eseguire la migrazione senza doversi preoccupare posta elettronica vengono lasciato presenti nelle cassette postali locale;
- Gli utenti riceveranno nuove password temporanea per il proprio account di Office 365 di cui hanno bisogno per passare al momento dell'accesso alle cassette postali per la prima volta.
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
- Gli utenti saranno necessario configurare un nuovo profilo di Outlook in ognuno dei dispositivi e scaricare nuovamente il messaggio di posta elettronica. La quantità di posta elettronica che vengono scaricate può variare. Per ulteriori informazioni, dare uno sguardo al [modificare la quantità mail per mantenere non in linea](https://support.office.com/en-us/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&rs=en-US&ad=US&fromAR=1).

Per ulteriori informazioni sulla migrazione completa, esaminare:

- [È necessario tenere presente relativamente a una migrazione completa di posta elettronica a Office 365](https://support.office.com/en-us/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
- [Eseguire una migrazione totale di messaggi di posta elettronica a Office 365](https://support.office.com/en-us/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

### <a name="minimal-hybrid-migration"></a>Migrazione ibrida minimo

Ibrida minimo o express, la migrazione è una in cui si dispongono di centinaia di cassette postali da migrare a Office 365, può completare la migrazione entro pochi settimane e non è necessario uno della funzionalità di migrazione ibrida avanzate come calendario sulla disponibilità condivise informazioni.

Migrazione ibrida minimo è ideale per le aziende che è necessario richiedere più tempo per eseguire la migrazione di cassette postali di Office 365, ma ancora piano per il completamento della migrazione entro pochi settimane. Alcuni vantaggi della migrazione ibrida completa più avanzata senza molte delle complessità. È possibile controllare le cassette postali di quante e quali, viene eseguita la migrazione in un momento specifico; Verranno create con il nome utente e password agli account locale, le cassette postali di Office 365 e, a differenza di migrazioni complete, gli utenti non sarà necessario ricreare i profili di Outlook.

Se si intende eseguire la migrazione ibrida minimo, ecco alcuni aspetti da considerare:

- È necessario eseguire una sincronizzazione delle directory occasionale tra i server di Active Directory locali e Office 365;
- Gli utenti saranno in grado di eseguire l'accesso alle cassette postali di Office 365 utilizzando lo stesso nome utente e password che erano in uso quando è stata eseguita la migrazione di cassette postali;
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
- Gli utenti non è necessario configurare un nuovo profilo di Outlook nella maggior parte dei dispositivi (alcuni telefoni Android precedenti potrebbe essere necessario un nuovo profilo) e non sono più necessari per il download nuovamente il messaggio di posta elettronica.

Per ulteriori informazioni sulla migrazione ibrida minimo, dare uno sguardo [all'Utilizzo minimo ibrida rapidamente la migrazione delle cassette postali di Exchange a Office 365](https://support.office.com/article/Use-Minimal-Hybrid-to-quickly-migrate-Exchange-mailboxes-to-Office-365-fdecceed-0702-4af3-85be-f2a0013937ef)

### <a name="full-hybrid"></a>Ibrida completa

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

- Migrazioni ibride completo non sono appropriate per tutti i tipi di organizzazioni. A causa della complessità delle migrazioni ibride completa, le organizzazioni con meno di alcune cassette centinaia postali non viene visualizzato in genere i benefici giustificano il lavoro e dei costi necessari per configurare uno. Se questo sembra nell'organizzazione, è consigliabile prendere in considerazione le migrazioni complete o minimo ibrida invece;
- È necessario configurare la sincronizzazione delle directory con Azure Active Directory la connessione (AADConnect) tra i server di Active Directory locali e Office 365;
- Gli utenti saranno in grado di eseguire l'accesso alle cassette postali di Office 365 utilizzando lo stesso nome utente e password che utilizzano al momento dell'accesso in rete locale (richiede la connessione di Azure Active Directory con la sincronizzazione delle password e/o Active Directory Federation Services).
- È necessario una licenza di Office 365 che include Exchange Online per ciascuna cassetta postale utente, che eseguire la migrazione;
- Gli utenti non è necessario configurare un nuovo profilo di Outlook nella maggior parte dei dispositivi (alcuni telefoni Android precedenti potrebbe essere necessario un nuovo profilo) e non sono più necessari per il download nuovamente il messaggio di posta elettronica.

> [!IMPORTANT]
> Se l'organizzazione decide di eseguire la migrazione delle cassette postali a Office 365, ma si propone di conservare DirSync o della connessione di Azure Active Directory sul posto per continuare la gestione degli account utente da Active Directory locale, è necessario tenere presente almeno un Exchange server locale. Se viene rimosso l'ultimo server di Exchange, non sarà in grado di apportare modifiche ai destinatari di Exchange in Exchange Online. Ciò avviene perché l'origine dell'autorità rimane in Active Directory locale e modifiche devono essere resi disponibili.

Se un suoni di migrazione completa ibrida appropriata, esaminare le risorse seguenti per facilitare la migrazione:

- [Assistente per la distribuzione di Exchange](https://aka.ms/exdeploy)
- [Distribuzioni ibride di Exchange Server](https://technet.microsoft.com/en-us/library/jj200581%28v=exchg.150%29.aspx)
- [Configurazione ibrida guidata](https://technet.microsoft.com/en-us/library/hh529921%28v=exchg.150%29.aspx)
- [Domande frequenti sulla configurazione ibrida guidata](https://technet.microsoft.com/en-us/library/mt488940%28v=exchg.150%29.aspx)
- [Prerequisiti per la distribuzione ibrida](https://technet.microsoft.com/en-us/library/hh534377%28v=exchg.150%29.aspx)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Eseguire l'aggiornamento a una versione più recente di Exchange Server in locale

Mentre è fortemente ritiene che è possibile ottenere la migliore esperienza utente e valore eseguendo la migrazione completa a Office 365, è inoltre la comprensione che alcune organizzazioni è necessario mantenere alcuni server Exchange locale. È possibile a causa di requisiti normativi, garantire dati non vengono memorizzati in un Data Center presente in un altro paese o, potrebbe essere perché hai requisiti che non possono essere soddisfatti nel cloud, o le impostazioni univoche o può essere semplicemente che è necessario Exchange a gestire le cassette postali cloud poiché non è ancora utilizzare Active Directory locale. In qualsiasi caso per cui si sceglie o devono avere a disposizione di Exchange in locale, è necessario assicurarsi che l'ambiente di Exchange 2010 in modo da almeno Exchange 2013 o 2016 Exchange ed Exchange 2010 è stata rimossa prima della data di fine del supporto.

Per risultati ottimali, è consigliabile aggiornare l'ambiente locale rimanente per Exchange 2016. Non è necessario se si desidera passare direttamente da Exchange Server 2010 a Exchange Server 2016, installare Exchange Server 2013.

Exchange 2016 include tutte le funzionalità e miglioramenti inclusi con le versioni precedenti di Exchange e corrisponde maggiormente l'esperienza disponibile con Office 365 (sebbene alcune caratteristiche sono disponibili solo in Office 365). Estrarre alcuni dei fattori che è stati pienamente di tutte le:

| **Versione di Exchange**                     | **Funzionalità**                                                                                                                                                                                                                                         |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange 2013                            | Architettura semplificata la riduzione del numero dei ruoli del server a tre (Trasporto Edge di cassette postali, accesso Client,)                                                                                                                                        |
|                                          | Perdita prevenzione criteri dati (DLP) che consentono di mantenere la perdita di informazioni riservate                                                                                                                                                                |
|                                          | In modo significativo Outlook Web App esperienza migliorata                                                                                                                                                                                                    |
| Exchange 2016                            | *Funzionalità di Exchange 2013 e...*                                                                                                                                                                                                                   |
|                                          | Altri ruoli del server semplificata solo delle cassette postali e Trasporto Edge                                                                                                                                                                                   |
|                                          | DLP migliorata e integrazione con SharePoint                                                                                                                                                                                                  |
|                                          | Resilienza dei database migliorato                                                                                                                                                                                                                         |
|                                          | Collaborazione sui documenti online                                                                                                                                                                                                                        |

| **Considerazione**                        | **Ulteriori informazioni sulla**                                                                                                                                                                                                                                        |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fine del periodo di supporto                     | Come Exchange 2010, ogni versione di Exchange ha il proprio fine del periodo supportato:                                                                                                                                                                        |
|                                          | **Exchange 2013** - aprile 2023                                                                                                                                                                                                                       |
|                                          | **Exchange 2016** - 2025 ottobre                                                                                                                                                                                                                     |
|                                          | Prima fine del supporto di data, prima sarà necessario eseguire la migrazione di un'altra. Aprile 2023 è molto più vicino di quanto sembri!                                                                                                                 |
| Percorso di migrazione a Exchange 2013 o 2016  | Il percorso di migrazione da Exchange 2010 a una versione più recente è la stessa sia che si scelga di Exchange 2013 o 2016 Exchange:                                                                                                                              |
|                                          | Installare Exchange 2013 o 2016 nei servizi di spostamento dell'organizzazione di Exchange 2010 esistenti e altre infrastruttura Exchange 2013 o 2016 spostamento delle cassette postali e cartelle pubbliche in Exchange 2013 o Decommission 2016 rimanenti server Exchange 2010  |
| Coesistenza della versione                      | Durante la migrazione a Exchange 2013 oppure Exchange 2016, è possibile installare entrambe le versioni in un'organizzazione di Exchange 2010 esistente. In questo modo è possibile installare uno o più server Exchange 2013 oppure Exchange 2016 ed eseguire la migrazione.             |
| Hardware dei server                          | Requisiti hardware dei server sono state modificate da Exchange 2010. È necessario verificare che sia compatibile con i componenti hardware che si desidera utilizzare. È possibile trovare ulteriori informazioni sui requisiti hardware per ogni versione di seguito:                                      |
|                                          | [Requisiti di sistema di Exchange 2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx)                                                                                                                                      |
|                                          | [Requisiti di sistema di Exchange 2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)                                                                                                                                      |
|                                          | Si noterà che con notevoli miglioramenti delle prestazioni di Exchange, e aumentare la potenza e la capacità di archiviazione in server più recenti, sarà necessario meno server per supportare lo stesso numero di cassette postali.                       |
| Versione del sistema operativo                 | Le versioni del sistema operativo minimo supportato per ogni versione sono:                                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2012                                                                                                                                                                                                                |
|                                          | **Exchange 2013** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | È possibile trovare ulteriori informazioni sul supporto dei sistemi operativi nella [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                        |
| Livello di funzionalità di Active Directory foresta | Il minimo supportato foresta niveaux fonctionnels Active Directory per ogni versione sono:                                                                                                                                                                |
|                                          | **Exchange 2016** Windows Server 2008 R2 SP1                                                                                                                                                                                                         |
|                                          | **Exchange 2013** Windows Server 2003                                                                                                                                                                                                                |
|                                          | È possibile trovare ulteriori informazioni sul supporto di livello funzionale di foresta nella [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                 |
| Versioni client di Office                   | Le versioni client Office supportate minime per ogni versione sono:                                                                                                                                                                                   |
|                                          | **Exchange 2016** Office 2010 (con gli aggiornamenti più recenti)                                                                                                                                                                                              |
|                                          | **Exchange 2013** Office 2007 SP3                                                                                                                                                                                                                    |
|                                          | È possibile trovare ulteriori informazioni sul supporto di client Office a [Matrice di supporto per Exchange](https://technet.microsoft.com/en-us/library/ff728623%28v=exchg.150%29.aspx).                                                                           |

Per facilitare la migrazione, è possibile utilizzare le risorse seguenti:

- [Assistente per la distribuzione di Exchange](https://aka.ms/exdeploy)
- Active Directory schema le modifiche per Exchange [2016](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/EN-US/library/bb738144%28v=exchg.150%29.aspx)
- Requisiti di sistema per Exchange [2016](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/aa996719%28v=exchg.150%29.aspx)
- Prerequisiti per Exchange [2016](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.160%29.aspx), [2013](https://technet.microsoft.com/en-us/library/bb691354%28v=exchg.150%29.aspx)

## <a name="what-if-i-need-help"></a>Cosa succede se ho bisogno di assistenza?

Se si sta eseguendo la migrazione a Office 365, potrebbe essere idonei per utilizzare il servizio Microsoft FastTrack. FastTrack fornisce consigliate, strumenti e risorse per effettuare la migrazione a Office 365 il più agevole possibile. È necessario che tutto ciò tecnico reale di esaminare la migrazione di pianificazione e progettare completamente alla migrazione delle cassette postali ultima. Se si desidera fornire ulteriori informazioni FastTrack, dare uno sguardo al [FastTrack Microsoft](https://fasttrack.microsoft.com/).

Se riscontrano problemi durante la migrazione a Office 365 e non si utilizza FastTrack o la migrazione a una versione più recente di Exchange Server, siamo a tua disposizione per. Di seguito sono riportate alcune risorse che è possibile utilizzare:

- [Community di documentazione tecnica](https://social.technet.microsoft.com/Forums/office/en-US/home?category=exchangeserver)
- [Assistenza clienti](https://support.microsoft.com/en-us/gp/support-options-for-business)

## <a name="related-topics"></a>Argomenti correlati

[Risorse che consentono di eseguire l'aggiornamento da Office 2010 server e client](https://docs.microsoft.com/en-us/office365/enterprise/upgrade-from-office-2010-servers-and-products)

[Gruppo pensionistico per Office (Microsoft Tech Community)](https://go.microsoft.com/fwlink/?linkid=842065)
