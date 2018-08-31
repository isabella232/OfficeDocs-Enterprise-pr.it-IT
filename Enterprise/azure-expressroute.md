---
title: Azure ExpressRoute per Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Informazioni su come ExpressRoute Azure viene utilizzato con Office 365 e come pianificare il progetto di implementazione di rete che verrà richiesto se si sta distribuendo ExpressRoute Azure per l'utilizzo con Office 365.
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541154"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute per Office 365

Informazioni su come ExpressRoute Azure viene utilizzato con Office 365 e come pianificare il progetto di implementazione di rete che verrà richiesto se si sta distribuendo ExpressRoute Azure per l'utilizzo con Office 365. Piattaforma e all'infrastruttura servizi in esecuzione in Azure utilizzeranno spesso risolvendo considerazioni sull'architettura e le prestazioni di rete. In questi casi è consigliabile ExpressRoute per Azure. Software come le offerte di servizi come in Office 365 e Dynamics 365 sono stati realizzati per essere utilizzate in modo sicuro e affidabile tramite Internet. Di conseguenza, è consigliabile solo ExpressRoute per tali applicazioni in scenari specifici. È possibile leggere sulla sicurezza e prestazioni di Internet e se può essere opportuno ExpressRoute Azure per Office 365 nell'articolo della [connettività di rete per Office 365](network-connectivity.md).

> [!NOTE]
> Avvio del 31 luglio 2017, è possibile abilitare Peering Microsoft direttamente dalla console di amministrazione di Azure o utilizzo di PowerShell. Dopo aver abilitato Peering Microsoft, è possibile creare filtri di route per la ricezione di annunci di route BGP specifici. È necessario autorizzazione alla creazione di filtri per Office 365 e creare filtri di applicazioni (precedentemente note come CRM Online) Dynamics 365 Engagement per i clienti in qualsiasi momento. Parlare con il team di Account Microsoft sul processo per ottenere l'autorizzazione per creare filtri di route di Office 365. Sottoscrizioni non autorizzate tenta di creare filtri di route per Office 365 verranno visualizzato un [messaggio di errore](https://support.microsoft.com/kb/3181709)

È ora possibile aggiungere una connessione diretta alla rete a Office 365 per il traffico di rete di Office 365 selezionato. ExpressRoute Azure offre una connessione diretta, le prestazioni prevedibile e con un tempo di attività SLA di 99,95% per i componenti di rete di Microsoft. È ancora sarà necessaria una connessione internet per i servizi che non sono supportati su Azure ExpressRoute.

## <a name="planning-azure-expressroute-for-office-365"></a>Pianificazione ExpressRoute Azure per Office 365

Oltre a connettività internet, è possibile instradare un sottoinsieme del traffico di rete di Office 365 tramite una connessione diretta che offre la prevedibilità e un SLA uptime 99,95% per i componenti di rete di Microsoft. Azure ExpressRoute viene fornita con la connessione di rete dedicata a Office 365 e altri servizi cloud Microsoft.

Indipendentemente dalla presenza di una WAN MPLS esistente, è possibile aggiungere ExpressRoute per l'architettura di rete in uno dei tre modi; tramite un provider di posizione condivisa exchange cloud supportato, un provider di connessione point-to-Ethernet, o un provider di connessione MPLS. Verificare il [provider sono disponibili nel proprio paese](https://azure.microsoft.com/documentation/articles/expressroute-locations/). La connessione diretta ExpressRoute abiliterà la connettività per le applicazioni illustrati in [servizi quali Office 365 sono inclusi?](azure-expressroute.md#BKMK_WhatDoIGet) sotto. Traffico di rete per tutte le altre applicazioni e servizi continua attraversare internet.

Prendere in considerazione nel diagramma di rete di livello elevato seguente che mostra un tipico cliente di Office 365 la connessione al datacenter Microsoft tramite internet per l'accesso a tutte le applicazioni di Microsoft, ad esempio Office 365, Windows Update e TechNet. Clienti di utilizzano un percorso di rete simile indipendentemente dal fatto connette da una rete locale o da una connessione internet indipendenti.

![Connettività di rete di Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Esaminare il diagramma aggiornato che raffigura un cliente di Office 365 che utilizzano internet ed ExpressRoute per la connessione a Office 365. Si noti che alcune connessioni, ad esempio nodi DNS pubblico e rete CDN richiedono ancora la connessione pubblica a internet. Inoltre, gli utenti del cliente che non si trovano nella loro ExpressRoute building connesse si connettono tramite Internet.

![Connettività di Office 365 con ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Ancora si desiderano ulteriori informazioni? Informazioni su come [gestire il traffico di rete con ExpressRoute Azure per Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) e informazioni su come [configurare ExpressRoute Azure per Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). Sono state registrate anche una serie di [ExpressRoute Azure per la formazione su Office 365](https://channel9.msdn.com/series/aer) 10 parti su Channel 9 per illustrare i concetti in modo più.

([ExpressRoute azure per Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>Sono inclusi i servizi di Office 365?
<a name="BKMK_WhatDoIGet"> </a>

Nella tabella seguente sono elencati i servizi di Office 365 supportati su ExpressRoute. Leggere l' [articolo gli endpoint di Office 365](https://aka.ms/o365endpoints) per comprendere quali le richieste di rete per queste applicazioni richiedono la connettività internet.

|**Applicazioni incluse**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Approfondire<sup>1</sup> <br/> |
|Skype per Business Online<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portale e condivise<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD connettersi<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> Ognuna di queste applicazioni sono previsti requisiti di connettività internet non è supportati su ExpressRoute, vedere l' [articolo gli endpoint di Office 365](https://aka.ms/o365endpoints) per ulteriori informazioni.

I servizi che non sono inclusi in ExpressRoute per Office 365 sono download per client di Office 365 ProPlus, accesso aggiuntivo per Provider di identità in locale e il servizio Office 365 (gestito dal Vianet 21) in Cina.

([ExpressRoute azure per Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Implementazione di ExpressRoute per Office 365

L'implementazione di ExpressRoute richiede il coinvolgimento dei proprietari di rete e delle applicazioni e ne viene implementato attentamente determinare la nuova [architettura del routing di rete](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), i requisiti di larghezza di banda, cui verranno sicurezza, la disponibilità elevata E così via. Per implementare ExpressRoute, sarà necessario:

1. Valutare la necessità che expressroute soddisfa durante la pianificazione del servizio di integrazione applicativa Office 365. Acquisire familiarità con le applicazioni utilizzeranno internet o ExpressRoute e completamente pianificare la capacità della rete, sicurezza e la disponibilità elevata è necessario nel contesto dell'utilizzo di internet ed ExpressRoute per Office 365 traffico.

2. Determinare i servizi esterni e le posizioni peering per internet e di traffico ExpressRoute<sup>1</sup>.

3. Determinare la capacità richiesta su internet e connessioni ExpressRoute.

4. Definire un piano di implementazione della protezione e altri controlli perimetrale standard<sup>1</sup>.

5. Disporre di un account Microsoft Azure valido per effettuare la sottoscrizione ExpressRoute.

6. Selezionare un modello di integrazione applicativa e un [provider approvati](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Tenere presente i clienti possono selezionare più modelli di integrazione applicativa o partner e il partner non deve essere lo stesso provider di rete esistente.

7. Convalida della distribuzione di indirizzare il traffico verso ExpressRoute.

8. Se lo si desidera [implementare QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) e valutare l'espansione regionale.

<sup>1</sup> Considerazioni importanti sulle prestazioni. Decisioni qui possono incidere sensibilmente sulla latenza che è importante per le applicazioni, ad esempio Skype per le aziende.

Per ulteriori informazioni, utilizzare la [Guida alla distribuzione](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) oltre a [documentazione ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Per acquistare ExpressRoute per Office 365, è necessario per l'utilizzo con uno o più [approvato provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/) per fornire il numero desiderato e circuiti dimensioni con una sottoscrizione ExpressRoute Premium. Non esistono licenze aggiuntive per l'acquisto di Office 365.

Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

Prepararsi per l'abbonamento a per [ExpressRoute per Office 365](https://aka.ms/ert)?

([ExpressRoute azure per Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Argomenti correlati
<a name="BKMK_End"> </a>

[Connettività di rete con Office 365](network-connectivity.md)

[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)

[Routing con ExpressRoute per Office 365](routing-with-expressroute.md)

[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)

[Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)

[Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365 (preview)](bgp-communities-in-expressroute.md)

[Qualità multimediale e le prestazioni di connettività di rete in Skype for Business in linea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)

[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)

[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Ottimizzazione delle prestazioni e rete di Office 365](network-planning-and-performance.md)
