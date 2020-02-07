---
title: Gestione degli endpoint di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 1/24/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: Alcune reti aziendali limitano l'accesso a percorsi Internet generici o includono una sostanziale backhaul o l'elaborazione del traffico di rete. Per garantire che i computer su reti come queste possano accedere a Office 365, gli amministratori di rete e proxy devono gestire l'elenco di nomi FQDN, URL e indirizzi IP che compongono l'elenco degli endpoint di Office 365. Queste necessità devono essere aggiunte alla route diretta, al bypass proxy e/o alle regole del firewall e ai file PAC per garantire che le richieste di rete siano in grado di raggiungere Office 365.
ms.openlocfilehash: f1e614412c1ef789ba5f0b81e124fdfebf361f94
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845037"
---
# <a name="managing-office-365-endpoints"></a>Gestione degli endpoint di Office 365

La maggior parte delle organizzazioni aziendali che dispongono di più percorsi di Office e di una rete WAN di connessione dovrà richiedere la configurazione di Office 365. È possibile ottimizzare la rete inviando tutte le richieste di rete di Office 365 attendibili direttamente tramite il firewall, ignorando tutti i controlli o l'elaborazione del livello di pacchetti aggiuntivi. Questo riduce la latenza e i requisiti di capacità del perimetro. Identificare il traffico di rete di Office 365 è il primo passaggio per garantire prestazioni ottimali per gli utenti. Per ulteriori informazioni sulla connettività di rete di Office 365, vedere [principi di connettività di rete di office 365](office-365-network-connectivity-principles.md).

Microsoft consiglia di accedere agli endpoint di rete di Office 365 e di modificarli utilizzando l' [indirizzo IP e il servizio Web URL di office 365](office-365-ip-web-service.md).

Indipendentemente da come gestire il traffico di rete vitale di Office 365, Office 365 richiede la connettività Internet. Gli altri endpoint di rete in cui è richiesta la connettività sono elencati in altri [endpoint non inclusi nel servizio Web indirizzo IP e URL di Office 365](additional-office365-ip-addresses-and-urls.md).

La modalità di utilizzo degli endpoint di rete di Office 365 dipenderà dall'architettura di rete dell'organizzazione aziendale. In questo articolo vengono illustrati diversi modi in cui le architetture di rete aziendale possono essere integrate con gli URL e gli indirizzi IP di Office 365. Il modo più semplice per scegliere quali richieste di rete è attendibile consiste nell'utilizzare i dispositivi di SDWAN che supportano la configurazione automatizzata di Office 365 in ognuna delle posizioni di Office.

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a>SDWAN per l'uscita di branch locali del traffico di rete vitale di Office 365

In ogni percorso di succursale, è possibile fornire un dispositivo di SDWAN configurato per instradare il traffico per la categoria di endpoint di Office 365 Optimize, oppure ottimizzare e consentire categorie direttamente alla rete di Microsoft. Altre informazioni sul traffico di rete, tra cui il traffico del centro dati locale, il traffico dei siti Web Internet generale e il traffico verso gli endpoint di categoria predefiniti di Office 365 vengono inviati a un altro percorso in cui si dispone di un perimetro di rete più sostanziale.

Microsoft sta lavorando con i provider di SDWAN per abilitare la configurazione automatizzata. Per ulteriori informazioni, vedere [Office 365 networking Partner Program](office-365-networking-partner-program.md).

<a name="pacfiles"> </a>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a>Utilizzo di un file PAC per il routing diretto del traffico vitale di Office 365

Utilizzare i file PAC o WPAD per gestire le richieste di rete associate a Office 365 ma che non dispongono di un indirizzo IP. Le richieste di rete tipiche inviate tramite un proxy o un dispositivo perimetrale aumentano la latenza. Mentre l'interruzione e la verifica SSL consentono di creare la maggiore latenza, altri servizi quali l'autenticazione proxy e la ricerca di reputazione possono causare prestazioni insufficienti e un'esperienza utente errata. Inoltre, questi dispositivi di rete perimetrale richiedono una capacità sufficiente per elaborare tutte le richieste di connessione di rete. Si consiglia di ignorare i dispositivi proxy o di ispezione per le richieste di rete di Office 365.
  
La [raccolta di PowerShell Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) è uno script di PowerShell in cui vengono letti gli endpoint di rete più recenti dal servizio Web indirizzo IP e URL di Office 365 e viene creato un file PAC di esempio. È possibile modificare lo script in modo che si integri con la gestione dei file PAC esistente.

![Connessione a Office 365 tramite firewall e proxy.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

**Figura 1-perimetro della rete aziendale semplice**

Il file PAC viene distribuito ai Web browser al punto 1 della figura 1. Quando si utilizza un file PAC per l'uscita diretta del traffico di rete vitale di Office 365, è inoltre necessario consentire la connettività agli indirizzi IP dietro questi URL sul firewall perimetrale di rete. A tale scopo, vengono recuperati gli indirizzi IP per le stesse categorie di endpoint di Office 365 specificate nel file PAC e la creazione di ACL del firewall in base a tali indirizzi. Il firewall è il punto 3 della figura 1.

Separatamente se si sceglie di eseguire il routing diretto solo per gli endpoint di categoria Optimize, gli eventuali endpoint di categoria consentiti da inviare al server proxy dovranno essere elencati nel server proxy per ignorare l'ulteriore elaborazione. Ad esempio, la rottura SSL e il controllo e l'autenticazione proxy sono incompatibili con gli endpoint di categoria optimize e Allow. Il server proxy è il punto 2 nella figura 1.

La configurazione comune è quella di consentire senza l'elaborazione di tutto il traffico in uscita dal server proxy per gli indirizzi IP di destinazione per il traffico di rete di Office 365 che raggiunge il server proxy. Per informazioni sui problemi relativi all'interruzione e alla verifica di SSL, vedere [using the Third-Party Network Devices or Solutions on Office 365 Traffic](https://support.microsoft.com/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).

Sono disponibili due tipi di file PAC che verranno generati dallo script Get-PacFile.

|**Tipo**|**Descrizione**|
|:-----|:-----|
|**1** <br/> |Send Optimize endpoint Traffic Direct e tutto il resto del server proxy. <br/> |
|**2** <br/> |Send optimize and allow endpoint Traffic Direct e tutto il resto del server proxy. Questo tipo può essere utilizzato anche per inviare tutti i ExpressRoute supportati per il traffico di Office 365 ai segmenti di rete di ExpressRoute e tutto il resto al server proxy. <br/> |

Di seguito è riportato un semplice esempio di chiamata allo script di PowerShell:

```powershell
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

Sono disponibili diversi parametri che è possibile passare allo script:

|**Parametro**|**Descrizione**|
|:-----|:-----|
|**ClientRequestId** <br/> |Questo è necessario ed è un GUID passato al servizio Web che rappresenta il computer client che effettua la chiamata. <br/> |
|**Instance** <br/> |L'istanza di servizio di Office 365 che viene impostata come predefinita in tutto il mondo. Passata anche al servizio Web. <br/> |
|**TenantName** <br/> |Nome del tenant di Office 365. Passata al servizio Web e utilizzata come parametro sostitutivo in alcuni URL di Office 365. <br/> |
|**Tipo** <br/> |Tipo di file PAC del proxy che si desidera generare. <br/> |

Di seguito è riportato un altro esempio di chiamata dello script PowerShell con parametri aggiuntivi:

```powershell
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a>Server proxy bypassare l'elaborazione del traffico di rete di Office 365

Se i file PAC non vengono utilizzati per il traffico in uscita diretto, è comunque necessario ignorare l'elaborazione nel perimetro della rete configurando il server proxy. Alcuni fornitori di server proxy hanno abilitato la configurazione automatizzata di questa operazione come descritto nel [programma partner di rete di Office 365](office-365-networking-partner-program.md).

Se si esegue questa operazione manualmente, sarà necessario ottenere i dati di categoria ottimizzazione e Consenti endpoint dal servizio Web indirizzo IP e URL di Office 365 e configurare il server proxy per ignorare l'elaborazione. È importante evitare interruzioni SSL e controllare l'autenticazione proxy per gli endpoint di categoria optimize and allow.
  
<a name="bkmk_changes"> </a>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a>Change Management per gli indirizzi IP e gli URL di Office 365

Oltre a selezionare la configurazione appropriata per il perimetro della rete, è importante adottare un processo di gestione delle modifiche per gli endpoint di Office 365. Tali endpoint cambiano regolarmente e, se non vengono gestite le modifiche, è possibile finire con gli utenti bloccati o con prestazioni insufficienti dopo l'aggiunta di un nuovo indirizzo IP o URL.

Le modifiche apportate agli indirizzi IP e agli URL di Office 365 vengono in genere pubblicate vicino all'ultimo giorno di ogni mese. A volte una modifica verrà pubblicata al di fuori di quella pianificazione a causa di requisiti operativi, di supporto o di sicurezza.

Quando viene pubblicata una modifica che richiede l'intervento di un indirizzo IP o di un URL, è necessario aspettarsi di ricevere un avviso di 30 giorni dal momento in cui si pubblica la modifica finché non è presente un servizio di Office 365 su quell'endpoint. Anche se si intende questo periodo di notifica, potrebbe non essere sempre possibile a causa di requisiti operativi, di supporto o di sicurezza. Le modifiche che non richiedono un'azione immediata per mantenere la connettività, ad esempio gli indirizzi IP o gli URL rimossi o le modifiche meno significative, non includono la notifica anticipata. Indipendentemente dalla notifica fornita, viene elencata la data di attivazione del servizio previsto per ogni modifica.

### <a name="change-notification-using-the-web-service"></a>Modificare la notifica tramite il servizio Web

È possibile utilizzare l'indirizzo IP e il servizio Web URL di Office 365 per ottenere la notifica delle modifiche. Si consiglia di chiamare il metodo Web **/Version** una volta all'ora per controllare la versione degli endpoint che si sta utilizzando per la connessione a Office 365. Se questa versione cambia rispetto alla versione in uso, è consigliabile ottenere i dati dell'endpoint più recenti dal metodo Web **/endpoints** e, facoltativamente, ottenere le differenze dal metodo Web **/changes** . Non è necessario chiamare i metodi Web **/endpoints** o **/changes** se non sono state apportate modifiche alla versione trovata.

Per ulteriori informazioni, vedere [Office 365 IP address and URL Web Service](office-365-ip-web-service.md).

### <a name="change-notification-using-rss-feeds"></a>Modificare la notifica tramite feed RSS

L'indirizzo IP e il servizio Web URL di Office 365 offrono un feed RSS che è possibile sottoscrivere in Outlook. Sono presenti collegamenti agli URL RSS su ognuna delle pagine specifiche dell'istanza di servizio di Office 365 per gli indirizzi IP e gli URL. Per ulteriori informazioni, vedere [Office 365 IP address and URL Web Service](office-365-ip-web-service.md).

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a>Modificare la notifica e la revisione dell'approvazione tramite Microsoft Flow

Si capisce che potrebbe essere ancora necessario l'elaborazione manuale per le modifiche all'endpoint di rete che passano ogni mese. È possibile utilizzare Microsoft Flow per creare un flusso che invia una notifica tramite posta elettronica e, facoltativamente, esegue un processo di approvazione per le modifiche apportate agli endpoint di rete di Office 365. Dopo aver completato la revisione, è possibile fare in modo che il flusso invii automaticamente le modifiche al team di gestione del firewall e del server proxy.

Per informazioni su un modello e un esempio di flusso Microsoft, vedere [use Microsoft Flow to receive an mail for changes to Office 365 IP address and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651).
  
<a name="FAQ"> </a>
## <a name="office-365-network-endpoints-faq"></a>Domande frequenti sugli endpoint di rete di Office 365

Domande frequenti sull'amministratore sulla connettività di Office 365:
  
### <a name="how-do-i-submit-a-question"></a>Come si invia una domanda?

Fare clic sul collegamento nella parte inferiore per indicare se l'articolo è stato utile o meno e inviare altre domande. Monitoriamo i commenti e aggiorniamo le domande qui con le più frequenti.
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a>Come si determina la posizione del tenant?

 La **posizione del tenant** è meglio determinata usando la mappa del [datacenter](https://aka.ms/datamaps).
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>Si tratta di un peering appropriato con Microsoft?

 Le **posizioni di peering** sono descritte in modo più dettagliato in [peering with Microsoft](https://www.microsoft.com/peering).
  
Con oltre 2500 relazioni di peering ISP a livello globale e 70 punti di presenza, ottenere dalla rete alla nostra dovrebbe essere senza problemi. Non può far male spendere qualche minuto assicurandosi che il rapporto di peering dell'ISP sia il più ottimale, [Ecco alcuni esempi](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) di buoni e non così buoni peering per la nostra rete.
  
<a name="bkmk_MissingIP"> </a>
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>Per visualizzare le richieste di rete agli indirizzi IP non presenti nell'elenco pubblicato, è necessario fornire loro l'accesso?

Gli indirizzi IP vengono forniti solo per i server di Office 365 che è necessario indirizzare direttamente a. Non si tratta di un elenco completo di tutti gli indirizzi IP in cui verranno visualizzate le richieste di rete. Verranno visualizzate le richieste di rete per gli indirizzi IP di Microsoft e di terze parti, inediti e di proprietà. Questi indirizzi IP vengono generati dinamicamente o gestiti in modo da impedire l'avviso tempestivo quando cambiano. Se il firewall non è in grado di consentire l'accesso in base ai nomi FQDN per queste richieste di rete, utilizzare un file PAC o WPAD per gestire le richieste.
  
Per ulteriori informazioni, vedere un indirizzo IP associato a Office 365.
  
1. Controllare se l'indirizzo IP è incluso in un intervallo di pubblicazione più grande tramite una calcolatrice CIDR, ad esempio per [IPv4](https://www.ipaddressguide.com/cidr) o [IPv6](https://www.ipaddressguide.com/ipv6-cidr). Ad esempio, 40.96.0.0/13 include l'indirizzo IP 40.103.0.1 nonostante 40,96 non corrispondente a 40,103.
2. Vedere se un partner possiede l'indirizzo IP con una [query WHOIS](https://dnsquery.org/). Se è di proprietà di Microsoft, può trattarsi di un partner interno. Molti endpoint di rete partner sono elencati come appartenenti alla categoria _predefinita_ , per i quali gli indirizzi IP non vengono pubblicati.
3. L'indirizzo IP potrebbe non essere parte di Office 365 o di una dipendenza. La pubblicazione di endpoint di rete di Office 365 non include tutti gli endpoint di rete Microsoft.
4. Controllare il certificato, in un browser connettersi all'indirizzo IP utilizzando *https://\<ip_address\> * controllare i domini elencati nel certificato per comprendere quali domini sono associati all'indirizzo IP. Se si tratta di un indirizzo IP di proprietà di Microsoft e non dell'elenco degli indirizzi IP di Office 365, è probabile che l'indirizzo IP sia associato a una rete CDN Microsoft, ad esempio *MSOCDN.NET* o un altro dominio Microsoft senza informazioni IP pubblicate. Se si trova il dominio sul certificato è quello in cui pretendiamo di elencare l'indirizzo IP, fatecelo sapere.

<a name="bkmk_cname"> </a>
### <a name="some-office-365-urls-point-to-cname-records-instead-of-a-records-in-the-dns-what-do-i-have-to-do-with-the-cname-records"></a>Alcuni URL di Office 365 puntano ai record CNAME invece che a record nel DNS. Che cosa è necessario fare con i record CNAME?

Per i computer client è necessario un record a o AAAA DNS che includa uno o più indirizzi IP da connettere a un servizio cloud. Alcuni URL inclusi in Office 365 mostrano i record CNAME invece dei record A o AAAA. Questi record CNAME sono intermediario e possono essere presenti più di una catena. Verranno sempre risolti a un record a o AAAA per un indirizzo IP. Si consideri, ad esempio, la serie di record DNS seguente, che si risolve nell'indirizzo IP _IP_1_:

```
serviceA.office.com -> CNAME: serviceA.domainA.com -> CNAME: serviceA.domainB.com -> A: IP_1
```

Questi reindirizzamenti CNAME sono una parte normale del DNS e sono trasparenti al computer client e trasparenti nei server proxy. Vengono utilizzati per il bilanciamento del carico, le reti di distribuzione del contenuto, la disponibilità elevata e la riduzione degli incidenti di servizio. Microsoft non pubblica i record CNAME intermedi, sono soggetti a modifiche in qualsiasi momento e non è necessario configurarli come consentito nel server proxy.

Un server proxy convalida l'URL iniziale che nell'esempio precedente è serviceA.office.com e questo URL verrebbe incluso nella pubblicazione di Office 365. Il server proxy richiede la risoluzione DNS di tale URL a un indirizzo IP e riceverà IP_1 di nuovo. Non consente di convalidare i record di reindirizzamento CNAME intermediario.

Le configurazioni hardcoded o la whitelist in base ai nomi FQDN indiretti di Office 365 non sono consigliate, non sono supportate da Microsoft ed è noto che causano problemi di connettività dei clienti. Le soluzioni DNS che bloccano il reindirizzamento CNAME o che altrimenti risolvono erroneamente le voci DNS di Office 365 possono essere risolte tramite l'inoltro condizionale DNS (ambito per gli FQDN di Office 365 direttamente usati) con la ricorsione DNS abilitata. Molti prodotti perimetrali di rete di terze parti integrano in modo nativo la whitelist raccomandata di Office 365 endpoint nella loro configurazione utilizzando l' [indirizzo IP e il servizio Web URL di office 365](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

<a name="bkmk_akamai"> </a>
### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>Perché vengono visualizzati nomi quali nsatc.net o akadns.net nei nomi di dominio Microsoft?

Office 365 e altri servizi Microsoft utilizzano diversi servizi di terze parti, ad esempio Akamai e MarkMonitor, per migliorare l'esperienza di Office 365. Per continuare a fornire le migliori esperienze possibili, è possibile modificare questi servizi in futuro. I domini di terze parti possono ospitare contenuto, ad esempio una rete CDN, oppure possono ospitare un servizio, ad esempio un servizio di gestione del traffico geografico. Alcuni dei servizi attualmente in uso includono:
  
[MarkMonitor](https://www.markmonitor.com/) è in uso quando vengono visualizzate le richieste che includono * \*. nsatc.NET* . Questo servizio fornisce la protezione del nome di dominio e il monitoraggio per proteggersi da comportamenti dannosi.
  
[ExactTarget](https://www.marketingcloud.com/) è in uso quando si visualizzano le richieste a * \*. ExactTarget.com* . Questo servizio fornisce la gestione e il monitoraggio del collegamento tramite posta elettronica rispetto a comportamenti dannosi.
  
[Akamai](https://www.akamai.com/) è in uso quando vengono visualizzate le richieste che includono uno dei seguenti FQDN. Questo servizio offre servizi di rete per la distribuzione di contenuti e Geo-DNS.
  
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

<a name="bkmk_thirdparty"> </a>
### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a>È necessario avere la connettività minima possibile per Office 365

Poiché Office 365 è una famiglia di servizi creata per funzionare tramite Internet, le promesse di affidabilità e disponibilità si basano su numerosi servizi Internet standard disponibili. Ad esempio, i servizi Internet standard quali DNS, CRL e reti CDN devono essere raggiungibili per l'utilizzo di Office 365 così come devono essere raggiungibili per utilizzare i servizi Internet più moderni.

La famiglia di prodotti Office 365 è suddivisa in aree di servizio principali. Questi possono essere abilitati in modo selettivo per la connettività ed è presente un'area comune che è una dipendenza per tutti ed è sempre necessaria.

|**Area di servizio**|**Descrizione**|
|:-----|:-----|
|**Exchange** <br/> |Exchange Online e Exchange Online Protection <br/> |
|**SharePoint** <br/> |SharePoint Online e OneDrive for Business <br/> |
|**Skype for Business Online e Microsoft Teams** <br/> |Skype for business e Microsoft Teams <br/> |
|**Comune** <br/> |Office 365 Pro Plus, Office in un browser, Azure AD e altri endpoint di rete comuni <br/> |

Oltre ai servizi Internet di base, esistono servizi di terze parti che vengono utilizzati solo per integrare la funzionalità. Anche se questi sono necessari per l'integrazione, sono contrassegnati come facoltativi nell'articolo endpoint di Office 365 che indica che la funzionalità di base del servizio continuerà a funzionare se l'endpoint non è accessibile. Qualsiasi endpoint di rete necessario avrà l'attributo obbligatorio impostato su true. Qualsiasi endpoint di rete facoltativo avrà l'attributo obbligatorio impostato su false e l'attributo Notes fornirà informazioni dettagliate sulla funzionalità mancante che è necessario prevedere se la connettività è bloccata.
  
Se si sta tentando di utilizzare Office 365 e i servizi di terze parti non sono accessibili, è necessario assicurarsi che tutti i nomi [FQDN contrassegnati come necessari o facoltativi in questo articolo siano consentiti tramite il proxy e il firewall](urls-and-ip-address-ranges.md).
  
<a name="bkmk_consumer"> </a>
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>Come si blocca l'accesso ai servizi consumer di Microsoft?

La limitazione dell'accesso ai servizi consumer dovrebbe essere condotta a proprio rischio. L'unico modo affidabile per bloccare i servizi consumer è limitare l'accesso all'FQDN di *login.Live.com* . Questo nome di dominio completo viene utilizzato da un ampio insieme di servizi, tra cui servizi non consumer quali MSDN, TechNet e altri. Questo FQDN è utilizzato anche dal programma di Exchange file sicuro del supporto tecnico Microsoft ed è necessario trasferire i file per semplificare la risoluzione dei problemi per i prodotti Microsoft.  La limitazione dell'accesso a questo FQDN può comportare la necessità di includere anche eccezioni alla regola per le richieste di rete associate a questi servizi.
  
Tenere presente che bloccare l'accesso solo ai servizi consumer di Microsoft non impedirà la possibilità per gli utenti della rete di exfiltrate le informazioni utilizzando un tenant di Office 365 o un altro servizio.

<a name="bkmk_IPOnlyFirewall"> </a>
### <a name="my-firewall-requires-ip-addresses-and-cannot-process-urls-how-do-i-configure-it-for-office-365"></a>Il firewall richiede indirizzi IP e non è in grado di elaborare gli URL. Come configurarlo per Office 365?

Office 365 non fornisce gli indirizzi IP di tutti gli endpoint di rete richiesti. Alcuni sono forniti solo come URL e sono categorizzati come predefiniti. Gli URL nella categoria predefinita necessari devono essere consentiti tramite un server proxy. Se non si dispone di un server proxy, esaminare come sono state configurate le richieste Web per gli URL che gli utenti digitano nella barra degli indirizzi di un Web browser. l'utente non fornisce nemmeno un indirizzo IP. Gli URL di categoria predefiniti di Office 365 che non forniscono indirizzi IP devono essere configurati nello stesso modo.

## <a name="related-topics"></a>Argomenti correlati

[Servizio Web per URL e indirizzi IP di Office 365](office-365-ip-web-service.md)

[Intervalli IP del data center di Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Spazio IP pubblico di Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Requisiti dell'infrastruttura di rete per Microsoft Intune](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[ExpressRoute e Power BI](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[URL e intervalli di indirizzi IP per Office 365](urls-and-ip-address-ranges.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Principi della connettività di rete di Office 365](office-365-network-connectivity-principles.md)
