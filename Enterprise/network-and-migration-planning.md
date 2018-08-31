---
title: Pianificazione della rete e della migrazione per Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contiene collegamenti a informazioni sulla pianificazione della rete e il testing e la migrazione a Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223058"
---
# <a name="network-and-migration-planning-for-office-365"></a>Pianificazione della rete e della migrazione per Office 365

In questo articolo contiene collegamenti a informazioni sulla pianificazione e test di rete e la migrazione a Office 365.
  
Prima di eseguire la distribuzione o la migrazione per la prima volta in Office 365, è possibile utilizzare le informazioni in questi argomenti per stimare la larghezza di banda necessaria, per poi testare e verificare di disporre di larghezza di banda sufficiente per distribuire o migrare in Office 365.

||
|:-----|
| In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|

|||
|:-----|:-----|
|![Vedere Cloud Microsoft Networking per poster architetti Enterprise](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|Per le procedure ottimizzare la rete per Office 365 e altre piattaforme Microsoft cloud e servizi, vedere il poster [Microsoft Cloud di rete per architetti Enterprise](https://aka.ms/cloudarchnetworking) . |
   
## <a name="estimate-network-bandwidth-requirements"></a>Stimare i requisiti di larghezza di banda di rete
<a name="EstimateBandwidthRequirements"> </a>

Utilizzo di Office 365 può aumentare l'utilizzo di circuito internet dell'organizzazione. È importante determinare se la quantità di larghezza di banda disponibile attualmente è sufficiente per gestire l'aumento stimato dopo aver distribuito Office 365 lasciando almeno 20% della capacità di gestire più occupata dei giorni.
  
Per calcolare la larghezza di banda, utilizzare la procedura seguente:
  
1. Valutare il numero di client che verrà utilizzata ogni uscita Internet. Consentono di gestire le informazioni sulla connessione possibile la nostra rete terabit al multi. 
    
2. Determinare i servizi di Office 365 e le funzionalità saranno disponibili per i client da utilizzare. Sarà probabilmente necessario gruppi di utenti con diversi servizi o i profili di utilizzo.
    
3. Misurare l'utilizzo di rete per un gruppo pilota dei client. Verificare i client pilota rappresentante dei profili diversi di utenti nell'organizzazione, nonché le posizioni geografiche diverse. È possibile cross-controllo i risultati con i vecchi calcolatori per [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)e [Skype per le aziende](https://go.microsoft.com/fwlink/p/?LinkId=321551) o [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) che viene eseguite la propria rete. 
    
4. Utilizzare le misure dal gruppo pilota estrapolare alle esigenze dell'intera organizzazione e nuovamente test per convalidare le stime prima di apportare modifiche alla rete.
    
## <a name="test-your-existing-network"></a>Test della rete esistente
<a name="calculators"> </a>

 **Strumenti di rete.** Testare e convalidare la larghezza di banda Internet per determinare il download, caricamento e latenza dei vincoli. Questi strumenti consentono di determinare le funzionalità della rete per la migrazione e dopo che ha completato la distribuzione. 
  
- [Microsoft messaggio Analyzer](https://technet.microsoft.com/library/jj649776.aspx): messaggio Analyzer è uno strumento efficace per la risoluzione dei problemi di rete. Messaggio Analyzer acquisisce, viene visualizzato e consente di analizzare il traffico di messaggistica basato su protocollo e messaggi di sistema. Messaggio Analyzer consente inoltre di importare, aggregare e analizzare i dati dai file di registro e di traccia.
    
- [Analizzatore connettività remota di Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): verificata la connettività nell'ambiente Exchange Online.
    
- Utilizzare l' [Assistente di ripristino per Office 365 e supporto tecnico clienti Microsoft](https://diagnostics.office.com/#/Download?env=SOC) per risolvere i problemi di Outlook e Office 365. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

Approfondire in queste procedure consigliate per ulteriori informazioni su come migliorare l'esperienza di Office 365.
  
1. Se si desidera iniziare a come consentire agli utenti subito? Per suggerimenti sull'utilizzo di Office 365, tra cui SharePoint Online, Exchange Online e Lync Online, la rete non è semplicemente collaborazione, vedere [procedure consigliate per l'utilizzo di Office 365 con reti lente](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . In questo articolo viene collegato alle carichi di contenuto su TechNet e Support.office.com fuori per ottimizzare l'esperienza di Office 365 e sono incluse informazioni su modi semplici per personalizzare le pagine web e su come configurare le impostazioni di Internet Explorer per un'esperienza ottimale di Office 365. 
    
2. Leggere i [Principi di connettività di rete di Office 365](https://aka.ms/o365networkingprinciples) per comprendere i principi di connettività per la gestione del traffico di Office 365 in modo sicuro e ottenere prestazioni ottimali. In questo articolo consentono di acquisire familiarità con le indicazioni più recenti per l'ottimizzazione in modo sicuro la connettività di rete di Office 365. 
    
3. Migliorare le prestazioni di migrazione della posta gestendo con attenzione la pianificazione per gli aggiornamenti di Windows. È possibile aggiornare i computer client in batch e verificare che tutti i computer client vengono aggiornati prima della migrazione a Office 365 per definire quali l'utilizzo della larghezza di banda di rete. Per ulteriori informazioni, vedere [manualmente l'aggiornamento e configurazione manuale dei desktop per Office 365 per gli aggiornamenti più recenti](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Il traffico di rete di Office 365 offre le prestazioni migliori quando è considerato come un servizio Internet attendibile e consentiti per ignorare la maggior parte del filtro tradizionali e analisi che alcune organizzazioni archiviare il traffico di rete di servizi Internet non attendibili. In genere include la rimozione in uscita, ad esempio l'autenticazione utente proxy e controllo dei pacchetti di elaborazione, nonché verifica uscita locale su Internet con corretto Network Address Translation (NAT) e sufficiente capacità della larghezza di banda per gestire l'aumento richieste di rete. Per ulteriori informazioni sulla configurazione della rete per gestire Office 365 come servizio Internet attendibile della rete, fare riferimento agli [endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
    
1. Verificare che [gli endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Il traffico aggiuntivo continui a Office 365 comporta un aumento delle connessioni in uscita proxy, nonché un aumento del traffico protetto tramite TLS/SSL.
    
2. Se il proxy in uscita richiede l'autenticazione degli utenti che si verifichi una perdita di funzionalità o la connettività lenta. Ignorare il requisito di autenticazione per i domini di Office 365 per ridurre il sovraccarico.
    
3. Se il numero di calendari e cassette postali condivisi è elevato, è possibile che si verifichi un aumento del numero di connessioni da Outlook a Exchange. Ad esempio, il client Outlook potrebbe aprirsi a due connessioni aggiuntive per ciascun calendario condiviso in uso. In tal caso, verificare che il proxy in uscita sia in grado di gestire le connessioni oppure escludere il proxy per le connessioni a Office 365 relative a Outlook.
    
4. Determinare il numero massimo di dispositivi supportati per un indirizzo IP pubblico e come bilanciare il carico tra più indirizzi IP. Per ulteriori informazioni, vedere [supporto di NAT con Office 365](nat-support-with-office-365.md).
    
5. Se si sta controllare le connessioni in uscita dal computer nella rete, ignorare questo filtro per i domini di Office 365 migliorare la connettività e le prestazioni. Inoltre, ignorando spesso l'ispezione in uscita consente di rimuovere la necessità di un singolo uscita Internet e consente locale uscita Internet per le richieste di rete di Office 365 destinate a.
    
6. Alcuni clienti trovare le impostazioni di rete interna possono influire sulle prestazioni. Impostazioni, ad esempio dimensione unità (Maximum Transmission Unit) di trasmissione massima, in rete la negoziazione automatica o il rilevamento automatico e route ottimale per Internet sono aree comuni da cercare.
    
## <a name="network-planning-reference-for-office-365"></a>Riferimenti per la pianificazione della rete per Office 365
<a name="NetReference"> </a>

In questi argomenti contengono informazioni dettagliate sulla informazioni di riferimento di rete di Office 365.
  
- [Gestione di endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Connettività client](client-connectivity.md)
    
- [Reti per la distribuzione di contenuti](content-delivery-networks.md)
    
- [Record esterno (Domain Name System) per Office 365](external-domain-name-system-records.md)
    
- [Supporto IPv6 nei servizi Office 365](ipv6-support.md)
    
- [Principi della connettività di rete di Office 365](https://aka.ms/o365networkingprinciples)
    
- [Microsoft Virtual Academy: Gestione delle prestazioni Office 365](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Rete video di Office 365 domande frequenti (FAQ)](office-365-video-networking-faq.md)
    
- [Pianificare per i dispositivi di rete che si connettono ai servizi di Office 365](plan-for-network-devices.md)
    
- [Assistenti distribuzione per i servizi di Office 365](deployment-advisors-for-office-365.md)
    

