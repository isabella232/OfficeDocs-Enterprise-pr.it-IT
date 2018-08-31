---
title: Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: "Connessione a Office 365 utilizzando Azure ExpressRoute si basa su annunci BGP di subnet IP specifici che rappresentano le reti in cui sono distribuiti gli endpoint di Office 365. A causa della natura globale di Office 365 e il numero di servizi che costituiscono Office 365, i clienti spesso hanno l'esigenza di gestire gli annunci che accettano all'interno della rete. La riduzione del numero di subnet IP; definito prefissi IP il resto di questo articolo, affinché siano allineati ai terminologia relativa alla gestione di rete BGP, i seguenti obiettivi end è utile per i clienti:"
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541140"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365

Connessione a Office 365 utilizzando Azure ExpressRoute si basa su annunci BGP di subnet IP specifici che rappresentano le reti in cui sono distribuiti gli endpoint di Office 365. A causa della natura globale di Office 365 e il numero di servizi che costituiscono Office 365, i clienti spesso hanno l'esigenza di gestire gli annunci che accettano all'interno della rete. La riduzione del numero di subnet IP; definito prefissi IP il resto di questo articolo, affinché siano allineati ai terminologia relativa alla gestione di rete BGP, i seguenti obiettivi end è utile per i clienti:
  
- **Gestire i prefissi IP richiesti numeri accettati** - clienti che dispongono di un'infrastruttura di rete interna o gestore telefonico di rete che supporta solo un numero limitato di prefissi IP e i clienti che dispongono di un gestore telefonico di rete che le spese per accettare i prefissi di sopra di un numero limitato desidera calcolare il numero totale di prefissi già annunciato alla rete e selezionare quali applicazioni di Office 365 sono più adeguate per ExpressRoute.

- **Gestire la quantità di larghezza di banda richiesta sul circuito Azure ExpressRoute** - clienti potrebbero essere necessario definire la busta della larghezza di banda dei servizi di Office 365 sul percorso ExpressRoute rispetto al percorso Internet. In questo modo i clienti prenotare ExpressRoute della larghezza di banda per specifiche applicazioni, ad esempio Skype per le aziende e instradare le applicazioni di Office 365 rimanenti sul percorso Internet.

Per assistere i clienti con questi obiettivi, i prefissi di Office 365 IP che pubblicizzati su ExpressRoute contrassegnati con servizio BGP community valori specifici come illustrato nell'esempio riportato di seguito.
  
> [!NOTE]
> È necessario prevedere traffico di rete associato con altre applicazioni da includere nel valore della community. Questo è il comportamento previsto per un Software globale come un servizio che offre con centri dati e i servizi condivisi. Questa è stata ridotta a icona quando possibile con i due obiettivi sopra elencati, gestione prefisso count e/o della larghezza di banda presente.

|**Servizio**|**Valore Community BGP**|**Note**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Sono compresi i servizi Exchange ed EOP\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype per le aziende\*  <br/> |12076:5030  <br/> |Skype for Business Online  <br/> |
|altri servizi di Office 365\*  <br/> |12076:5100  <br/> |Inclusioni di Azure Active Directory (gli scenari di autenticazione e la sincronizzazione delle Directory) e servizi di portale di Office 365  <br/> |
|\*L'ambito degli scenari di servizio incluse in ExpressRoute descritte nell'articolo [endpoint di Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Altri servizi e i valori di community BGP possibile aggiungere in futuro. [Visualizzare l'elenco corrente delle community BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Che cosa sono gli scenari più comuni per l'utilizzo delle community BGP?

I clienti possono utilizzare le community BGP per definire quali gruppi di prefissi IP che vengono accettati dai loro rete attraverso ExpressRoute Azure, pertanto che influenzano il numero totale di prefisso IP e busta previsto della larghezza di banda di determinati servizi di Office 365. È importante tenere presente che tutti i piani Office 365 richiederà che Internet associato traffico indipendentemente dall'utilizzo di Azure ExpressRoute o BGP community. Nei tre scenari seguenti vengono descritti gli utilizzi più comuni di questa funzionalità.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scenario 1: Ridurre al minimo il numero di prefissi IP di Office 365

Contoso Corporation è una società di 50.000 persona attualmente utilizzato da Office 365 per Exchange Online e SharePoint Online. Nell'analisi ExpressRoute requisiti che Contoso determina relativi dispositivi di rete in tutti i percorsi regionali non possono gestire routing dimensioni tabella sopra 100 voci route aggiuntive. Contoso esaminato il numero totale di prefissi IP ExpressRoute sarebbe advertise per l'elenco completo dei servizi di Office 365 e conclusi superiore a 100. Per restare in 100 voci di route aggiuntive, Contoso fornisce l'utilizzo della ExpressRoute per Office 365 solo il valore SharePoint Online BGP community, 12076:5020, ricevute tramite Microsoft ExpressRoute peering.

|**Tag di community BGP utilizzato**|**Funzionalità instradabile su Azure ExpressRoute**|**Route Internet necessari**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for Business  <br/> | DNS, CRL, &amp; CDN richieste  <br/>  Tutti gli altri servizi di Office 365 non specificamente supportate su Azure ExpressRoute  <br/>  Tutti gli altri servizi cloud Microsoft  <br/>  Portale di Office 365, autenticazione di Office 365, &amp; Office Online  <br/>  Exchange Online Protection e Skype per le aziende Online, Exchange Online  <br/> |

> [!NOTE]
> Per ottenere il numero inferiore di prefisso per ogni servizio, verrà mantenute una quantità minima di sovrapposizione tra i servizi. Questo è il comportamento previsto.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scenario 2: ExpressRoute all'ambito e la larghezza di banda interno utilizzato per alcuni servizi di Office 365

Fabrikam Inc, un'azienda di grandi dimensioni multinazionale con una rete eterogenea distribuita, è una sottoscrizione di molti servizi di Office 365, inclusi; Exchange Online, SharePoint Online e Skype for Business in linea. Infrastruttura di distribuzione interna di Fabrikam in grado di gestire migliaia di prefissi IP nelle tabelle di routing; Tuttavia, è solo Fabrikam desidera eseguire il provisioning ExpressRoute e interno della larghezza di banda per le applicazioni di Office 365 più sensibili alle prestazioni di rete e utilizzare la larghezza di banda Internet esistente per tutte le altre applicazioni di Office 365.
  
Per questo motivo, Fabrikam definisce l'ambito della larghezza di banda relativi ExpressRoute Azure per appena Skype per valore Business Online BGP Community 12076:5030, ricevute tramite Microsoft ExpressRoute peering. Il traffico di rete rimanenti associato a Office 365 continua a utilizzare i punti di uscita internet.

|**Tag di community BGP utilizzato**|**Funzionalità instradabile su Azure ExpressRoute**|**Route Internet necessari**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype SIP segnalazione, download, la condivisione di funzionalità vocali, video e desktop  <br/> | DNS, CRL, &amp; CDN richieste  <br/>  Tutti gli altri servizi di Office 365 non specificamente supportate su Azure ExpressRoute  <br/>  Tutti gli altri servizi cloud Microsoft  <br/>  Portale di Office 365, autenticazione di Office 365, &amp; Office Online  <br/>  Skype per telemetria Business, suggerimenti rapidi client Skype, connettività per messaggistica immediata pubblica  <br/>  Exchange Online, Exchange Online Protection e SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scenario 3: Ambiti ExpressRoute Azure per solo i servizi di Office 365

Woodgrove Bank è un cliente di diversi i servizi cloud Microsoft, quali Office 365. Dopo la valutazione della rete capacità e consumo Woodgrove Bank decide di distribuire Azure ExpressRoute come percorso preferito per i servizi di Office 365 supportati. Le tabelle di routing possono supportare l'elenco completo dei prefissi IP di Office 365 e Azure ExpressRoute parte del circuito che abbia effettuato il provisioning supportano tutte le esigenze di larghezza di banda e latenza previste.
  
Per verificare che il traffico di rete associato a servizi cloud Microsoft diversa da Office 365, Woodgrove Bank fornisce l'utilizzo della ExpressRoute per Office 365 per tutti i prefissi IP contrassegnati con valori community BGP specifici di Office 365, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Tag di community BGP utilizzato**|**Funzionalità instradabile su Azure ExpressRoute**|**Route Internet necessari**|
|:-----|:-----|:-----|
|Exchange, Skype per le aziende, SharePoint, &amp; altri servizi  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive for Business  <br/> Skype SIP segnalazione, download, la condivisione di funzionalità vocali, video e desktop  <br/> Portale di Office 365, autenticazione di Office 365, &amp; Office Online  <br/> | DNS, CRL, &amp; CDN richieste  <br/>  Tutti gli altri servizi di Office 365 non specificamente supportate su Azure ExpressRoute  <br/>  Tutti gli altri servizi cloud Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Considerazioni per l'utilizzo della caratteristica community BGP principali sulla pianificazione

Clienti che scelgono per sfruttare i vantaggi delle community BGP per influire sulla modalità ExpressRoute è stato annunciato e propagati attraverso la rete del cliente devono tenere presente quanto segue in considerazione:
  
- Quando si utilizzano le community BGP nella struttura della rete che è importante garantire la simmetria route viene conservata. In alcuni casi, l'aggiunta o rimozione delle community BGP può creare una situazione in routing simmetrico viene interrotto e la configurazione del routing deve essere aggiornata per ristabilire il routing simmetrico.

- Ambito ExpressRoute Azure con valori di community BGP è un'operazione di clienti. Microsoft verrà advertise tutti i prefissi IP associate alla relazione peering indipendentemente dal fatto qualsiasi ambito configurato dal cliente.

- ExpressRoute Azure non supporta le azioni nella rete Microsoft basata su cliente assegnato community BGP.

- I prefissi IP utilizzati da Office 365are contrassegna solo con servizio specifico BGP community valori posizione non sono supportate le community BGP specifiche. Servizi di Office 365 sono natura, filtro in base alla posizione del tenant prefissi globali o dati all'interno dell'area di Office 365 non sono supportati. L'approccio consigliato consiste nel configurare la rete per coordinare il più corta o un percorso di rete preferita dal percorso di rete dell'utente in Microsoft globale network, indipendentemente dalla posizione fisica dell'indirizzo IP del servizio Office 365 richieste.

- I prefissi IP inclusi in ogni valore community BGP rappresentano una subnet che contiene gli indirizzi IP per l'applicazione di Office 365 associato al valore. In alcuni casi, più di un'applicazione di Office 365 con indirizzi IP all'interno di una subnet causando un prefisso IP esistenti in più di un valore di community. Si tratta, anche se raramente, comportamento previsto a causa della frammentazione di allocazione e non influisce sugli obiettivi di gestione prefisso count o della larghezza di banda. Si consiglia di utilizzare "Consenti cosa è necessario" affrontare "Nega cosa non è necessario" in contrapposizione a quelli per sfruttare i vantaggi delle community BGP per Office 365 per ridurre al minimo gli effetti.

- Utilizzo della caratteristica community BGP non modifica i requisiti di connettività di rete o configurazione necessaria per l'utilizzo di Office 365 sottostante. I clienti che desiderano accedere a Office 365 sono comunque necessari siano in grado di accedere a Internet.

- Ambito ExpressRoute Azure con le community BGP riguarda solo le route che tramite la relazione peering Microsoft può visualizzare la rete interna. Potrebbe essere necessario effettuare le configurazioni livello applicazioni aggiuntivi, ad esempio l'utilizzo di una configurazione PAC o WPAD in combinazione con la distribuzione con ambito.

- Oltre a utilizzare Microsoft assegnato community BGP, i clienti possono scegliere di assegnare i propri community BGP a Office 365 IP prefissi individuati attraverso ExpressRoute Azure per influenzare il routing interno. Un caso di utilizzo più comuni assegna una community BGP posizione in base a tutte le route individuate attraverso ogni determinato ExpressRoute peering posizione e quindi utilizzando downstream tali informazioni nella rete cliente per coordinare il più corta o percorso di rete in preferito Rete di Microsoft. L'utilizzo del cliente assegnato community BGP con ExpressRoute per gli scenari di Office 365 non rientra nell'ambito del controllo di Microsoft o della visibilità.

Questo è un collegamento breve è possibile utilizzare il ritorno: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Argomenti correlati

[Connettività di rete con Office 365](network-connectivity.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)
  
[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
  
[Qualità multimediale e le prestazioni di connettività di rete in Skype for Business in linea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute e QoS in Skype for Business in linea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flusso di chiamate tramite ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
  
[Supporto per le community BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)
  
[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)
  
[ExpressRoute Azure per la formazione su Office 365](https://channel9.msdn.com/series/aer)
