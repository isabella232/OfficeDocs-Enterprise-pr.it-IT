---
title: Gestione degli endpoint di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Alcune reti aziendali limitano l'accesso a posizioni generiche internet o che includono backhaul sostanziale o l'elaborazione del traffico di rete. Per verificare che i computer nelle reti come queste possono accedere a Office 365, gli amministratori di rete e proxy necessarie per gestire l'elenco dei nomi di dominio completo, gli URL e gli indirizzi IP che costituiscono l'elenco degli endpoint di Office 365. Le necessità da aggiungere alla route diretta, ignorare il proxy, e/o le regole del firewall e file PAC per garantire che le richieste di rete siano in grado di raggiungere Office 365.
ms.openlocfilehash: 480d2fa1b55507187f9150d02907849178a451b5
ms.sourcegitcommit: d93f7a51e8cdefdfc9933cdf1f9e413b013bb367
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "25719020"
---
# <a name="managing-office-365-endpoints"></a>Gestione degli endpoint di Office 365

È necessario che la maggior parte delle organizzazioni aziendali che dispongono di più posizioni di office e una connessione WAN necessità di configurazione per la connettività di rete di Office 365. È possibile ottimizzare la rete per l'invio di che tutte le attendibili le richieste di rete di Office 365 direttamente attraverso il firewall, escludendo tutti controllo livello dei pacchetti aggiuntivi o di elaborazione. Consente di ridurre la latenza e i requisiti di capacità perimetrale. Che identifica il traffico di rete di Office 365 è il primo passaggio per offrire prestazioni ottimali per gli utenti. Per ulteriori informazioni sulla connettività di rete di Office 365, vedere [Principi di connettività di rete di Office 365](office-365-network-connectivity-principles.md)

Si consiglia di che accedere alle modifiche a tali utilizzando l' [indirizzo IP di Office 365 e il servizio Web di URL](office-365-ip-web-service.md) e gli endpoint di rete di Office 365

Indipendentemente dalla modalità di gestione del traffico di rete fondamentale Office 365, Office 365 richiedono la connettività Internet. Altri endpoint di rete cui è necessaria la connettività sono elencati [altri](additional-office365-ip-addresses-and-urls.md) endpoint non inclusa in indirizzo IP di Office 365 e URL servizio Web

Utilizzo endpoint di rete di Office 365 dipende l'architettura di rete dell'organizzazione aziendale. In questo articolo vengono illustrate le architetture di rete aziendale può essere integrato con indirizzi IP di Office 365 e gli URL in diversi modi. Il modo più semplice per scegliere di rete che le richieste di attendibilità consiste nell'utilizzare dispositivi SDWAN che supportano la configurazione di Office 365 automatizzata ciascuno dei percorsi di office. 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN di uscita locale branch fondamentale Office 365 del traffico di rete

In ciascuna sede succursale, è possibile fornire un dispositivo SDWAN che è configurato per instradare il traffico di Office 365 ottimizzare categoria di endpoint o Ottimizza e consentire le categorie, direttamente alla rete Microsoft. Traffico di rete, inclusi traffico datacenter in locale, il traffico di siti web Internet generale e traffico agli endpoint categorie predefinite di Office 365 verrà inviato a un'altra posizione in cui si dispone un perimetro della rete più importanti.

Microsoft è impegnata con i provider SDWAN per attivare la configurazione automatica. Per ulteriori informazioni, vedere [Applicazione Partner di rete di Office 365](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utilizzare un file PAC per il routing diretto del traffico fondamentale Office 365

PAC o WPAD file utilizzati per gestire le richieste di rete siano associate a Office 365, ma non dispongono di un indirizzo IP. Le richieste di rete tipici inviate attraverso un dispositivo proxy o perimetrale incrementare la latenza. Interrompere SSL e Inspect consente di creare la latenza più grande, altri servizi ad esempio ricerca reputazione e l'autenticazione proxy può causare la riduzione delle prestazioni e un'esperienza utente non valida. Questi dispositivi di rete perimetrale è inoltre necessario capacità sufficiente per l'elaborazione di tutte le richieste di connessione di rete. È consigliabile ignorare i dispositivi proxy o un controllo per le richieste di rete dirette Office 365.
  
[Raccolta di PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) è uno script di PowerShell che legge gli endpoint di rete più recenti dal servizio Web di URL e indirizzo IP di Office 365 e consente di creare un file di esempio PAC. È possibile modificare lo script in modo che si integra con la gestione dei file PAC esistente. 

![Connessione a Office 365 mediante firewall e proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Nella figura 1 - perimetro della rete aziendale semplice**

Il file PAC viene distribuito per i web browser in corrispondenza del punto 1 nella figura 1. Quando si utilizza un file PAC per uscita diretto del traffico di rete di Office 365 fondamentale, è necessario anche per la connettività a indirizzi IP controllati da tali URL nel firewall di rete perimetrale. A tale scopo, recuperare gli indirizzi IP per le stesse Office 365 endpoint categorie come specificato nel file PAC e creazione firewall ACL in base a tali indirizzi. Il firewall è punto 3 nella figura 1. 

Separatamente se si sceglie di solo indirizzamento diretto per gli endpoint di categoria Ottimizza qualsiasi Consenti necessari gli endpoint di categoria che si invia al server proxy, saranno necessario elencato nel server proxy per un'ulteriore elaborazione di bypass. Ad esempio, un'interruzione SSL e l'autenticazione Proxy e Inspect incompatibili con Ottimizza sia Consenti endpoint di categoria. Il server proxy è punto 2 nella figura 1.

Configurazione comune consiste nel consentire senza elaborazione tutto il traffico in uscita dal server proxy per gli indirizzi IP di destinazione per il traffico di rete di Office 365 che accede al server proxy. Per informazioni sui problemi con SSL interrompere e Inspect, vedere [utilizzo dei dispositivi di rete di terze parti o le soluzioni sul traffico di Office 365](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Esistono due tipi di file PAC che genera lo script Get-PacFile.

|**Tipo**|**Descrizione**|
|:-----|:-----|
|**1** <br/> |Inviare Optimize endpoint il traffico diretto e tutti gli altri elementi al server proxy. <br/> |
|**2** <br/> |Inviare Ottimizza e Consenti endpoint il traffico diretto e tutti gli altri elementi al server proxy. Questo tipo può essere utilizzato anche per inviare che expressroute tutte supportate per il traffico di Office 365 ai segmenti di rete ExpressRoute e tutte le altre al server proxy. <br/> |

Ecco un semplice esempio di chiamata dello script di PowerShell:

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Sono disponibili diversi parametri che è possibile passare allo script:

|**Parametro**|**Descrizione**|
|:-----|:-----|
|**ClientRequestId** <br/> |Ciò è obbligatorio e viene passato un GUID per il servizio web che rappresenta il computer client che effettua la chiamata. <br/> |
|**Instance** <br/> |L'istanza del servizio Office 365 che per impostazione predefinita in tutto il mondo. Inoltre, passate al servizio web. <br/> |
|**TenantName** <br/> |Il nome del tenant Office 365. Il servizio web e viene utilizzata come parametro sostituibile in alcuni URL di Office 365. <br/> |
|**Type** <br/> |Il tipo di file del proxy PAC che si desidera generare. <br/> |

Ecco un altro esempio di chiamata dello script di PowerShell con parametri aggiuntivi.

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Server proxy bypass elaborazione del traffico di rete di Office 365 

File PAC non vengono utilizzati per indirizzare il traffico in uscita, in cui si desidera ignorare l'elaborazione sul perimetro della rete mediante la configurazione del server proxy. Alcuni fornitori di server proxy è sono abilitata la configurazione automatica di questa come descritto nel [Programma Partner accesso remoto di Office 365](office-365-networking-partner-program.md). 

Se si sta eseguendo questa manualmente è necessario ottenere l'Ottimizza e Consenti endpoint categoria dati dall'indirizzo IP di Office 365 e del servizio Web di URL e configurare il server proxy venga ignorato elaborazione per questi. È importante evitare interruzioni SSL e Inspect e autenticazione Proxy per l'ottimizzazione e consentire gli endpoint di categoria. 
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Gestione delle modifiche per gli URL e indirizzi IP di Office 365

Oltre a selezionare configurazione appropriata per il perimetro della rete, è importante che si adotta un processo di gestione per gli endpoint di Office 365. Modificare gli endpoint con regolarità e se non si gestiscono le modifiche, è possibile che venga con gli utenti bloccati o con riduzione delle prestazioni dopo un indirizzo IP nuovo indirizzo o l'URL viene aggiunto. 

In genere la pubblicazione delle modifiche per l'URL e indirizzi IP di Office 365 quasi l'ultimo giorno del mese. In alcuni casi verrà pubblicata una modifica all'esterno di tale pianificazione causa operativa, supporto o i requisiti di sicurezza.

Quando viene pubblicata una modifica che richiede di agire perché è stato aggiunto un URL o l'indirizzo IP, è necessario prevedere di ricevere notifiche di 30 giorni dal momento in cui che è pubblicare le modifiche fino a quando non è un servizio di Office 365 in tale endpoint. Anche se siamo per il periodo di notifica, potrebbe non essere sempre possibile causa operativa, supporto o i requisiti di sicurezza. Le modifiche che non richiedono un intervento immediato per garantire la connettività, ad esempio gli indirizzi IP o URL è stato rimosso o meno modifiche significative, non includono preavviso. Indipendentemente dal quale notifica viene fornita, è elencare la data di attivazione servizio previsti per ogni modifica.

### <a name="change-notification-using-the-web-service"></a>Modifica della notifica tramite il servizio Web

È possibile utilizzare l'indirizzo IP di Office 365 e il servizio Web di URL per ottenere la notifica delle modifiche. È consigliabile che si chiama il metodo web **/version** una volta all'ora per controllare la versione di endpoint utilizzato per connettersi a Office 365. Se questa versione cambia quando rispetto alla versione con in uso, si dovrebbe ottenere i dati di endpoint più recenti dal metodo web **/endpoints** e se lo si desidera ottenere le differenze dal metodo web **/changes** . Non è necessario chiamare il **/endpoints** o **/changes** metodi web se non è stata alcun cambiamento alla versione trovato. 

Per ulteriori informazioni, vedere [indirizzo IP di Office 365 e il servizio Web di URL](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Notifica di modifica tramite feed RSS

L'indirizzo IP di Office 365 e il servizio Web URL fornisce un feed RSS che è possibile effettuare la sottoscrizione a Outlook. Sono disponibili collegamenti a URL e gli URL RSS in ogni delle pagine specifiche dell'istanza del servizio Office 365 per gli indirizzi IP. Per ulteriori informazioni, vedere [indirizzo IP di Office 365 e il servizio Web di URL](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Notifica di modifica e approvazione esaminare utilizzando Microsoft Flow

Sono informazioni che si potrebbe richiedere ancora elaborazione manuale delle modifiche di endpoint di rete tramite ogni mese. È possibile utilizzare Microsoft Flow per creare un flusso di notifica tramite posta elettronica e facoltativamente viene eseguito un processo di approvazione per le modifiche quando gli endpoint di rete di Office 365 sono state modificate. Dopo aver completata la revisione, è possibile impostare il flusso di posta elettronica automaticamente le modifiche al proprio team di gestione dei server proxy e firewall. 

Per informazioni su un esempio di Microsoft Flow e un modello, vedere [Utilizzo del flusso di Microsoft per ricevere un messaggio di posta elettronica per le modifiche a URL e indirizzi IP di Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Domande frequenti sugli endpoint di rete di Office 365

Domande frequenti amministratore sulla connettività di Office 365:
  
### <a name="how-do-i-submit-a-question"></a>Modalità di invio di una domanda

Fare clic sul collegamento nella parte inferiore per indicare se l'articolo sono risultate utile o non e invio di domande aggiuntive. È monitorare i commenti e suggerimenti e aggiornare le domande qui con domande più frequenti.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Come è possibile determinare la posizione del personale tenant?

 **Percorso tenant** dipende meglio utilizzando il [mapping datacenter](http://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>È peering correttamente con Microsoft?

 **Percorsi peering** sono descritte più dettagliatamente nelle [peering con Microsoft](https://www.microsoft.com/peering).
  
Con oltre 2500 relazioni peering ISP a livello globale e 70 punti di presenza, Guida dalla rete a nostra deve essere eseguito. Non è verificheranno ripercussioni per pochi minuti, assicurandosi che relazione peering dell'ISP è la più ottimale, [dell'Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) di una buona e non in modo ottimale peering mano scelte da operare per la rete. 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>È possibile visualizzare le richieste di rete per gli indirizzi IP non presenti nell'elenco pubblicato, è necessario fornire l'accesso a tali?
<a name="bkmk_MissingIP"> </a>

Microsoft fornisce solo gli indirizzi IP per i server di Office 365 a che si consiglia di distribuire direttamente. Questo non è un elenco completo di tutti gli indirizzi IP che verrà visualizzato per le richieste di rete. Verrà visualizzato le richieste di rete di Microsoft e gli indirizzi IP posseduti, annullamento della pubblicazione, di terze parti. Tali indirizzi IP sono dinamicamente generati o gestiti in modo tempestivo avviso quando vengono modificate. Se il firewall non può consentire l'accesso basato su nomi FQDN per queste richieste di rete, utilizzare un file PAC o WPAD per gestire le richieste.
  
Visualizzare che un indirizzo IP associato a Office 365 che si desidera includere ulteriori informazioni?
  
1. Controllare se l'indirizzo IP è inclusa in un intervallo pubblicato superiore con una [Calcolatrice CIDR](http://jodies.de/ipcalc).
2. Vedere se un partner proprietario IP con una [query whois](https://dnsquery.org/). Se si tratta di Microsoft e di proprietà, potrebbe essere un partner interno.
3. Verificare che il certificato, in un browser si connettono all'indirizzo IP tramite *HTTPS://\<indirizzo IP\> * , controllare i domini elencati sul certificato per acquisire familiarità con i domini associati l'indirizzo IP. Se si tratta di una proprietà dell'indirizzo IP di Microsoft e non presenti nell'elenco di indirizzi IP di Office 365, è probabile che l'indirizzo IP è associato un CDN Microsoft, ad esempio *MSOCDN.NET* o un altro dominio Microsoft senza informazioni pubblicate sul IP. Se che il dominio nel certificato è uno dove è attestazione visualizzare l'elenco indirizzi IP, inviaci i tuoi suggerimenti.

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Il motivo per cui vengono visualizzati i nomi, ad esempio nsatc.net o akadns.net nei nomi di dominio Microsoft?
<a name="bkmk_akamai"> </a>

Office 365 e altri servizi Microsoft utilizzano diversi servizi di terze parti, ad esempio Akamai e MarkMonitor per ottimizzare le prestazioni di Office 365. Per mantenere avendo la migliore esperienza possibile, apportare modifiche questi servizi in futuro. In questo modo, è spesso pubblicare il record CNAME che punta a un terzo dominio posseduto, un record o indirizzo IP. Domini di terze parti possono ospitare contenuto, ad esempio un CDN o può ospitare un servizio, ad esempio un servizio di gestione del traffico geografiche. Nel caso di connessioni a tali terze parti, è sotto forma di un reindirizzamento o riferimento, non una richiesta iniziale dal client. Alcuni clienti devono verificare che il modulo di riferimento e il reindirizzamento può passare senza aggiungere in modo esplicito che può utilizzare lungo elenco di servizi di terze parti potenziali FQDN.
  
L'elenco dei servizi è soggetta a modifiche in qualsiasi momento. Alcuni dei servizi attualmente in uso:
  
[MarkMonitor](https://www.markmonitor.com/) è in uso quando viene visualizzato richieste che includono * \*. nsatc.net* . Questo servizio fornisce la protezione dei nomi di dominio e il monitoraggio per proteggere il comportamento dannoso.
  
[ExactTarget](https://www.marketingcloud.com/) è in uso quando viene visualizzato le richieste per * \*. exacttarget.com* . Questo servizio fornisce posta elettronica collegamento Gestione e monitoraggio con comportamento dannoso.
  
[Akamai](https://www.akamai.com/) è in uso quando viene visualizzato le richieste di includono uno dei seguenti FQDN. Questo servizio offre geo DNS e servizi di rete di distribuzione del contenuto.
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>È necessario disporre della connettività minima possibile per Office 365
<a name="bkmk_thirdparty"> </a>

Office 365 è un gruppo di servizi sviluppati alla funzione tramite internet, la promessa l'affidabilità e la disponibilità basata su molti servizi internet standard disponibile. Ad esempio servizi internet standard, ad esempio DNS, CRL e CDN devono essere raggiungibili a utilizzare Office 365 esattamente come devono essere raggiungibili utilizzare più moderni servizi internet.

La famiglia di prodotti Office 365 è suddivisa in aree principali di servizio. È possibile abilitare in modo selettivo per la connettività e vi sarà un'area comune di una dipendenza per tutti ed è sempre necessario.

|**Area dei servizi**|**Descrizione**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online ed Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online e OneDrive for Business <br/> |
|**Skype** <br/> |Skype per le aziende e team di Microsoft <br/> |
|**Comuni** <br/> |Office 365 Professional Plus, Office Online, Azure Active Directory e altri endpoint di rete comune <br/> |

Oltre ai servizi internet di base, sono disponibili servizi di terze parti che vengono utilizzati solo per integrare funzionalità. Quando queste informazioni sono necessarie per l'integrazione sono contrassegnati come facoltativi nell'articolo Office 365 endpoint che indica che le funzionalità principali di servizio continuerà a funzionare se il punto finale non è accessibile. Qualsiasi endpoint di rete che è necessario avrà required attributo impostato su true. Qualsiasi endpoint di rete facoltativo disporranno dell'attributo obbligatorio impostato su false e l'attributo note verrà descritte funzionalità mancanti che si otterranno probabilmente se la connettività è bloccata.
  
Se si sta tentando di utilizzare Office 365 e si stanno scoprendo servizi di terze parti non sono accessibili è necessario [verificare che tutti i nomi FQDN è contrassegnato come obbligatorio o facoltativo in questo articolo sono consentiti attraverso il proxy e firewall](urls-and-ip-address-ranges.md).
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Come bloccare l'accesso ai servizi consumer di Microsoft
<a name="bkmk_consumer"> </a>

Limitazione dell'accesso ai servizi offerti consumer deve essere eseguita a proprio esclusivo rischio, l'unico modo affidabile ai servizi consumer blocco per limitare l'accesso a *login.live.com* nome di dominio completo. Questo FQDN viene utilizzato da un'ampia gamma di servizi, quali servizi professionali, ad esempio MSDN e TechNet altri utenti. Limitazione dell'accesso a questo FQDN può comportare la necessità di includere anche le eccezioni alla regola per le richieste di rete associati a questi servizi.
  
Tenere presente che bloccando l'accesso ai servizi consumer Microsoft soli non impedisce la possibilità di una persona nella rete alle informazioni exfiltrate utilizzando un tenant di Office 365 o altri servizi.
  
## <a name="related-topics"></a>Argomenti correlati

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Intervalli IP del data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Spazio IP pubblico di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisiti dell'infrastruttura di rete per Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)
