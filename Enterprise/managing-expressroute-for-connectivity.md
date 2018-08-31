---
title: Gestione di ExpressRoute per la connettività di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute per Office 365 offre un percorso alternativo di routing per raggiungere molti servizi di Office 365 senza la necessità di tutto il traffico in uscita a internet. Anche se la connessione a internet per Office 365 è comunque necessario, la route specifiche Microsoft annuncia tramite BGP alla propria rete rendere il diretto ExpressRoute a commutazione di circuito preferito a meno che non sono disponibili altre configurazioni di rete. Le tre aree comuni che è possibile configurare per gestire questo routing sono prefix filtro, sicurezza e conformità.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541176"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Gestione di ExpressRoute per la connettività di Office 365

ExpressRoute per Office 365 offre un percorso alternativo di routing per raggiungere molti servizi di Office 365 senza la necessità di tutto il traffico in uscita a internet. Anche se la connessione a internet per Office 365 è comunque necessario, la route specifiche Microsoft annuncia tramite BGP alla propria rete rendere il diretto ExpressRoute a commutazione di circuito preferito a meno che non sono disponibili altre configurazioni di rete. Le tre aree comuni che è possibile configurare per gestire questo routing sono prefix filtro, sicurezza e conformità.
  
> [!NOTE]
> Microsoft ha modificato come viene esaminato il dominio di routing Peering Microsoft per Azure ExpressRoute. Avvio del 31 luglio 2017, tutti i clienti di Azure ExpressRoute consentono Peering Microsoft direttamente dalla console di amministrazione di Azure o tramite PowerShell. Dopo aver attivato Microsoft Peering, ai clienti possono creare filtri di route per la ricezione di annunci route BGP per le applicazioni di Engagement per i clienti Dynamics 365 (precedentemente note come CRM Online). Clienti che necessitano di ExpressRoute Azure per Office 365 devono ottenere la revisione da Microsoft poter creare filtri di route per Office 365. Rivolgersi al team di Account Microsoft per informazioni su come richiedere un esame per l'attivazione di Office 365 ExpressRoute. Sottoscrizioni non autorizzate tenta di creare filtri di route per Office 365 verranno visualizzato un [messaggio di errore](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Prefix filtro

È consigliabile che i clienti accettano tutte le route BGP come annunciato da Microsoft, le route fornite seguito da un processo di revisione e convalida rigoroso la rimozione di eventuali vantaggi per il controllo è stato aggiunto. ExpressRoute disponibili in modo nativo i controlli consigliati, ad esempio la proprietà prefix IP, l'integrità e scala - Nessuna route in ingresso filtro sul lato cliente.
  
Se si richiedono ulteriori operazioni di convalida di proprietà route tra ExpressRoute peering pubblica, è possibile controllare le route annunciate rispetto all'elenco di tutti i prefissi IPv4 e IPv6 che rappresentano [gli intervalli IP pubblici di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Questi intervalli coprire lo spazio degli indirizzi Microsoft completa e modificare raramente, una gamma di intervalli per filtrare i dati affidabile che offre anche protezione aggiuntiva per i clienti preoccupate non Microsoft proprietà route nella loro ambiente. Nel caso in cui viene apportata una modifica, verranno eseguita in 1st del mese e il numero di versione nella sezione **Dettagli** della pagina Modifica ogni volta che viene aggiornato il file.
  
Esistono diversi motivi per evitare l'utilizzo degli [intervalli di indirizzi IP e gli URL di Office 365](https://aka.ms/o365endpoints) per generare gli elenchi del filtro prefisso. Tra cui:
  
- I prefissi di Office 365 IP seguito da una quantità elevata di modifiche regolarmente.

- L'URL di Office 365 e l'indirizzo IP intervalli sono progettati per la gestione dei firewall consente elenchi e infrastruttura Proxy, non il routing.

- Gli intervalli di indirizzi IP e gli URL di Office 365 non comprendono altri servizi Microsoft che possono essere nell'ambito per le connessioni ExpressRoute.

| |
|**Opzione**|**Complessità**|**Modificare il controllo**|
|:-----|:-----|:-----|
|Accetta tutte le route di Microsoft  <br/> |**Basso:** Clienti si basa sulle controlli di Microsoft per verificare che tutte le route in modo corretto e di proprietà.  <br/> |Nessuno  <br/> |
|Microsoft Filter proprietà supernets  <br/> |**Medio:** Clienti implementa prefisso riepilogati gli elenchi di filtro per consentire solo Microsoft proprietà route.  <br/> |I clienti devono verificare che gli aggiornamenti poco frequenti siano presenti in filtri di route.  <br/> |
|Filtrare gli intervalli IP di Office 365  <br/> [!CAUTION] Non consigliato
|**Elevata:** Clienti di filtrare route basate sulla prefissi di Office 365 IP definiti.  <br/> |I clienti devono implementare un processo di gestione delle modifiche affidabile per gli aggiornamenti mensili.  <br/> [!CAUTION]Questa soluzione richiede modifiche significative in corso. Modifiche non è implementate in tempo will, potrebbe risultare un'interruzione del servizio.   |

Connessione a Office 365 utilizzando Azure ExpressRoute si basa su annunci BGP di subnet IP specifici che rappresentano le reti in cui sono distribuiti gli endpoint di Office 365. A causa della natura globale di Office 365 e il numero di servizi che compongono Office 365, i clienti spesso hanno l'esigenza di gestire gli annunci che accettano all'interno della rete. Se si è interessati con un numero di prefissi annunciato nell'ambiente, la caratteristica [community BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) consente di filtrare gli annunci per un set specifico di servizi di Office 365. Questa caratteristica è ora in anteprima.
  
Indipendentemente dal fatto come gestire gli annunci di route BGP provenienti da Microsoft, non di acquisire qualsiasi esposizione particolare ai servizi di Office 365 rispetto alla connessione a Office 365 tramite un solo a commutazione di circuito di internet. Microsoft gestisce la protezione stessa, conformità e sui livelli di prestazioni dal tipo di circuito che viene utilizzato un cliente per connettersi a Office 365.
  
### <a name="security"></a>Sicurezza

È consigliabile mantenere i propri controlli perimetrale rete e protezione per le connessioni da e verso ExpressRoute pubblici e peering Microsoft, che include le connessioni da e verso i servizi di Office 365. Controlli di sicurezza devono essere disponibili per le richieste di rete recarsi in uscita dalla rete in rete Microsoft e su come in ingresso dalla rete di Microsoft per la rete.
  
#### <a name="outbound-from-customer-to-microsoft"></a>In uscita dal cliente a Microsoft
  
Quando i computer si connettono a Office 365, si connettono allo stesso insieme di endpoint indipendentemente dal fatto che viene eseguita la connessione attraverso un internet o a commutazione di circuito ExpressRoute. Indipendentemente dal fatto circuito in uso, è consigliabile considerare servizi di Office 365 come più attendibili di destinazioni internet generico. I controlli di protezione recapito esterno dovrebbero consistere nelle porte e protocolli per ridurre i rischi e ridurre al minimo interventi di manutenzione. Informazioni sulle porte necessarie è disponibile nell'articolo di riferimento [endpoint di Office 365](https://aka.ms/o365endpoints) .
  
Per i controlli sono stati aggiunti, è possibile utilizzare il filtraggio all'interno dell'infrastruttura proxy a livello FQDN per limitare o controllare alcune o tutte le richieste di rete indirizzate a internet o a Office 365. Conservare l'elenco di nomi di dominio completi quando vengono rilasciate caratteristiche e le offerte di Office 365 evolvono richiede la gestione delle modifiche più affidabile e il rilevamento delle modifiche per la pubblicazione [endpoint di Office 365](https://aka.ms/o365endpoints).
  
> [!CAUTION]
> È consigliabile che non utilizzare unicamente su IP prefissi per gestire la sicurezza in uscita a Office 365.

|**Opzione**|**Complessità**|**Modificare il controllo**|
|:-----|:-----|:-----|
|Nessuna restrizione  <br/> |**Basso:** Clienti consente l'accesso illimitato in uscita a Microsoft.  <br/> |Nessuno  <br/> |
|Limitazioni delle porte  <br/> |**Basso:** Clienti limita l'accesso in uscita a Microsoft per le porte previste.  <br/> |Poco frequenti.  <br/> |
|Restrizioni di nome di dominio completo  <br/> |**Elevata:** Clienti limita l'accesso in uscita a Office 365 basato su FQDN pubblicato.  <br/> |Modifiche apportate ogni mese.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>In ingresso da Microsoft per cliente
  
Esistono diversi scenari facoltativi che richiedono Microsoft avviare le connessioni di rete.
  
- ADFS durante la convalida della password per l'accesso.

- [Distribuzioni ibride di Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Posta elettronica da un tenant Exchange Online a un host locale.

- SharePoint Online posta inviare da SharePoint Online a un host locale.

- [SharePoint federati ricerca ibrida](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS ibrido di SharePoint](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype per l'ambiente ibrido di Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) e/o [Skype per la federazione di Business](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype per Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Si consiglia di accettare le connessioni tramite il circuito internet anziché il circuito ExpressRoute per ridurre la complessità. Se la conformità o le prestazioni effettive necessità che necessario accettare le connessioni in ingresso su un circuito ExpressRoute, è consigliabile utilizzare un firewall o proxy inverso come ambito connessioni accettate. È possibile utilizzare gli [endpoint di Office 365](https://aka.ms/o365endpoints) per scoprire il diritto FQDN e IP prefissi.
  
### <a name="compliance"></a>Conformità

È non utilizzano il percorso di distribuzione da utilizzare per i controlli di conformità. Indipendentemente dal fatto che la connessione a servizi di Office 365 tramite un circuito ExpressRoute o internet, non modificare i controlli di conformità. È consigliabile consultare i livelli di certificazione di protezione per Office 365 stabilire la soluzione ideale per soddisfare le esigenze dell'organizzazione e di conformità diversa.
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Argomenti correlati

[Reti per la distribuzione di contenuti](content-delivery-networks.md)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gestione di endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[ExpressRoute Azure per la formazione su Office 365](https://channel9.msdn.com/series/aer)
