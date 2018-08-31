---
title: Routing con ExpressRoute per Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
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
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Per comprendere correttamente il routing del traffico a Office 365 utilizzando Azure ExpressRoute, sarà necessario confermati conoscerli i requisiti di routing ExpressRoute core ed ExpressRoute circuiti e domini di routing. Questi elementi fondamentali per l'utilizzo di ExpressRoute che i clienti di Office 365 si baseranno sul layout.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541164"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routing con ExpressRoute per Office 365

Per comprendere correttamente il routing del traffico a Office 365 utilizzando Azure ExpressRoute, sarà necessario confermati conoscerli principali [requisiti di routing ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) ed [ExpressRoute circuiti e domini di routing](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Questi elementi fondamentali per l'utilizzo di ExpressRoute che i clienti di Office 365 si baseranno sul layout.
  
Alcuni elementi chiavi negli articoli sopra elencati che è necessario comprendere includono:
  
- Circuiti ExpressRoute non vengono mappati a specifiche dell'infrastruttura fisica, ma sono una connessione logica eseguita in una singola posizione peering da Microsoft e un provider peering per conto dell'utente.

- Non esiste un mapping 1:1 tra un circuito ExpressRoute e un tasto s dei clienti.

- Ogni a commutazione di circuito in grado di supportare fino a 3 relazioni peering indipendenti (peering Azure pubblico, peering Azure privata e Microsoft peering); Office 365, è necessario Microsoft peering.

- Ogni circuito ha una larghezza di banda fisso condiviso da tutte le relazioni peering.

- Gli indirizzi IPv4 qualsiasi pubblico e pubblica come numeri che verranno utilizzati per il ExpressRoute a commutazione di circuito deve essere convalidato come fase di proprietà dell'utente o assegnate esclusivamente all'utente per il proprietario dell'intervallo di indirizzi.

- Parte del circuito ExpressRoute virtuale sono ridondanti a livello globale ed eseguire le procedure routing BGP standard. Questo è il motivo per cui è consigliabile due circuiti fisici per ogni uscita per il provider di una configurazione attivo/attivo.

Vedere la [pagina di domande frequenti](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) per ulteriori informazioni sui servizi supportati, i costi e i dettagli di configurazione. Nell'elenco dei provider di connettività che offre supporto peering Microsoft, vedere l' [articolo percorsi ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) per informazioni. Sono state registrate anche una serie di 10 parti [ExpressRoute Azure per Office 365 formazione](https://channel9.msdn.com/series/aer) su Channel 9 per illustrare i concetti in modo più.
  
## <a name="ensuring-route-symmetry"></a>Verifica della route simmetria

Il server front-end di Office 365 sono accessibili su Internet ed ExpressRoute. È preferibile che questi server eseguire il routing su circuiti ExpressRoute quando entrambi sono disponibili. Per questo motivo è la possibilità di asimmetria route, se il traffico dalla rete si desidera eseguire il routing tramite le circuiti Internet. Route asimmetriche costituiscono un problema poiché i dispositivi che eseguono l'ispezione dei pacchetti possono bloccare restituito il traffico che segue un percorso diverso da pacchetti in uscita seguita.
  
Indipendentemente dal fatto che si avvia una connessione a Office 365 tramite Internet o ExpressRoute, l'origine deve essere un indirizzo instradabile pubblicamente. Con molti clienti peering direttamente con Microsoft, con indirizzi privati in cui è possibile tra i clienti duplicazione non è realizzabile.
  
Di seguito sono scenari in cui verranno avviate le comunicazioni da Office 365 alla rete locale. Per semplificare la progettazione di rete, è consigliabile routing queste sul percorso Internet.
  
- ADFS durante la convalida della password per l'accesso.

- [Distribuzioni ibride di Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- La posta da un tenant Exchange Online a un host locale..

- SharePoint Online posta inviare da SharePoint Online a un host locale.

- [SharePoint federati ricerca ibrida](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS ibrido di SharePoint](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype per l'ambiente ibrido di Business](https://technet.microsoft.com/en-us/library/jj205403.aspx) e/o [Skype per la federazione di Business](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype per Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Per Microsoft instradare la rete per i flussi di traffico bidirezionale, le route BGP per i dispositivi in locale devono essere condiviso con Microsoft.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Stabilire quali applicazioni e caratteristiche di eseguire il routing su ExpressRoute

Quando si configura una relazione peering utilizzando il dominio di routing peering Microsoft e approvato per l'accesso appropriato, sarà in grado di visualizzare tutti i modelli PaaS e SaaS servizi disponibili su ExpressRoute. I servizi di Office 365 progettati per ExpressRoute possono essere gestiti con [le community BGP](https://aka.ms/bgpexpressroute365) o [filtri di route](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
Altre applicazioni, ad esempio Video di Office 365, è un'applicazione di Office 365. Tuttavia, Video di Office 365 è costituito da tre diversi componenti, il portale, il servizio di trasmissione e la rete di distribuzione del contenuto. Il portale risiede all'interno di SharePoint Online, streaming agevolare l'utilizzo del servizio all'interno di servizi di supporto Azure, e la rete di distribuzione del contenuto risiede all'interno di CDN Azure. Nella tabella seguente vengono illustrati questi componenti.
  
| |
|**Componente**|**Sottostante dell'applicazione**|**Inclusi in SharePoint Online BGP Community?**|**Utilizzo**|
|:-----|:-----|:-----|:-----|
|Portale di Office 365 Video  <br/> |SharePoint Online  <br/> |Sì  <br/> |Configurazione, caricamento  <br/> |
|Servizio di flusso Video di Office 365  <br/> |Servizi multimediali di Azure  <br/> |No  <br/> |Servizio di trasmissione, utilizzato nel caso in cui il video non è disponibile dalla rete CDN  <br/> |
|Rete di distribuzione del contenuto Video di Office 365  <br/> |CDN Azure  <br/> |No  <br/> |Origine principale dei download/flussi video. [Ulteriori informazioni sulle reti video di Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

Ognuna delle caratteristiche di Office 365 sono disponibili tramite Microsoft peering sono elencati nell' [articolo gli endpoint di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) per tipo di applicazione e il nome di dominio completo. Il nome di dominio completo nelle tabelle vengono utilizzati per consentire agli utenti di gestire il traffico utilizzando i file PAC o altre configurazioni di proxy, vedere la Guida alla [gestione di endpoint di Office 365](https://aka.ms/manageo365endpoints) , ad esempio PAC di file.
  
In alcune situazioni è stato utilizzato un dominio con caratteri jolly in uno o più sub-FQDN vengono inseriti in modo diverso rispetto al dominio con caratteri jolly di livello superiore. Ciò si verifica quando il carattere jolly rappresenta un lungo elenco di server in cui sono tutti annunciato ExpressRoute e Internet, mentre un piccolo gruppo secondaria di destinazioni sono solo annunciato a Internet o viceversa. Fare riferimento a tabelle riportate di seguito per acquisire familiarità con cui sono le differenze.
  
In questa tabella viene visualizzato il carattere jolly FQDN che è stato annunciato a internet e Azure ExpressRoute con il FQDN di sub che pubblicizzato solo a internet.

|**Dominio con caratteri jolly annunciato a circuiti ExpressRoute e Internet**|**Nome di dominio completo Sub annunciato alla solo circuiti Internet**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.email.microsoftonline.com  <br/> https://Portal.microsoftonline.comhttps://Portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> odc.officeapps.Live.com  <br/> odc.officeapps.Live.com  <br/> CDN.odc.officeapps.Live.com  <br/> ols.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> ocws.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

In genere i file PAC hanno lo scopo di inviare richieste di rete a ExpressRoute annunciato endpoint direttamente a circuito e tutte le altre richieste di rete per il proxy. Se si sta configurando un file PAC simile al seguente, comporre il file PAC nell'ordine seguente:
  
1. Includere nomi FQDN sub due nella colonna nella tabella sopra indicata nella parte superiore del file PAC, inviare il traffico verso il proxy. È stato creato un file PAC di esempio per l'utilizzo di questo articolo sulla [gestione di endpoint di Office 365](https://aka.ms/manageexpressroute365).

2. Includere tutti i nomi di dominio completi contrassegnati richiesti per ExpressRoute in [questo articolo](https://aka.ms/o365endpoints) di sotto della prima sezione, l'invio del traffico direttamente per il circuito ExpressRoute.

3. Includere tutti gli altri endpoint di rete o le regole di sotto di questi due voci, inviare il traffico verso il proxy.

In questa tabella vengono visualizzati i domini con caratteri jolly che sono stati annunciati circuiti Internet solo con il FQDN di sub che annunciato per Azure ExpressRoute e circuiti Internet. Per il file PAC precedente, i nomi FQDN nella colonna due la tabella seguente è indicato lo stato viene annunciato a ExpressRoute nel collegamento viene fatto riferimento, pertanto potrebbe essere incluso nel secondo gruppo delle voci del file.

|**Dominio con caratteri jolly annunciato solo circuiti Internet**|**Nome di dominio completo Sub annunciato a circuiti ExpressRoute e Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. office.net  <br/> |Agent.Office.NET  <br/> |
|\*. office365.com  <br/> |Outlook.Office365.com  <br/> SMTP.Office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> servizio di individuazione automatica -\<tenant\>. outlook.com  <br/> |
|\*. windows.net  <br/> |Login.Windows.NET  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routing del traffico Office 365 via Internet ed ExpressRoute

Per eseguire il routing a Office 365 dell'applicazione di propria scelta è necessario determinare una serie di fattori chiave.
  
1. Quanta larghezza di banda sarà necessaria l'applicazione. Il campionamento esistente è il metodo solo affidabile per determinare i all'interno dell'organizzazione.

2. I percorsi di uscita si desidera che il traffico di rete per lasciare la rete da. È consigliabile pianificare per ridurre al minimo la latenza di rete per la connettività a Office 365 come si inciderà sulle prestazioni. Poiché Skype per le aziende utilizza audio e video in tempo reale è particolarmente sensibili alla latenza di rete insufficienti.

3. Se si desidera che tutti o solo un sottoinsieme dei percorsi di rete per sfruttare ExpressRoute.

4. I percorsi di provider di rete scelti offre ExpressRoute da.

Dopo aver determinato le risposte a queste domande, è possibile effettuare il provisioning di un circuito ExpressRoute che soddisfi le esigenze di larghezza di banda e la posizione. Per ulteriori pianificazione assistenza della rete, vedere [case study sulla modalità di punti di manipolazione di Microsoft rete pianificazione delle prestazioni](https://aka.ms/tunemsit)e la [rete di Office 365 ottimizzazione Guida](https://aka.ms/tune) .
  
### <a name="example-1-single-geographic-location"></a>Nell'esempio 1: Unica posizione geografica
  
In questo esempio è uno scenario di una società fittizia denominata Trey Research con un'unica posizione geografica.
  
Dipendenti Trey Research sono consentiti solo per la connessione ai servizi e i siti Web su internet che il reparto sicurezza consente in modo esplicito in coppia di proxy in uscita che risiedono tra la rete aziendale e i provider di servizi Internet.
  
Trey Research prevede di utilizzare ExpressRoute Azure per Office 365 e riconosce che una parte del traffico, ad esempio il traffico destinato a reti di distribuzione del contenuto non sarà in grado di eseguire il routing su ExpressRoute per la connessione a Office 365. In quanto tutto il traffico già route per i dispositivi proxy per impostazione predefinita, queste richieste continueranno a funzionare come prima. Dopo avere Trey Research determinato che soddisfino i requisiti di routing ExpressRoute Azure, è procedere per creare un circuito, configurare il routing e collegare il nuovo circuito ExpressRoute a una rete virtuale. Una volta la configurazione di Azure ExpressRoute fondamentale sul posto, Trey Research utilizza il [file PAC 2 pubblicato](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) per instradare il traffico con i dati specifici dei clienti su ExpressRoute diretto per le connessioni di Office 365.
  
Come illustrato nella figura riportata di seguito, Trey Research è in grado di soddisfare i requisiti per instradare il traffico di Office 365 su internet e un sottoinsieme del traffico su ExpressRoute utilizzando una combinazione di modifiche alla configurazione di proxy di routing e in uscita.
  
1. Utilizzo del [file PAC 2 pubblicato](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) per instradare il traffico a un punto di uscita del internet separato per Azure ExpressRoute per Office 365.

2. I client sono configurati con una route predefinita per raggiungere i proxy Trey Research.

In questo scenario di esempio, Trey Research utilizza un dispositivo proxy in uscita. Analogamente, i clienti che non utilizzano ExpressRoute Azure per Office 365 possibile utilizzare questa tecnica per instradare il traffico in base al costo di controllo del traffico destinato agli endpoint conosciuto volume elevato.
  
Più elevata FQDN per Exchange Online, SharePoint Online e Skype Business online sono i seguenti:
  
![Rete perimetrale cliente ExpressRoute](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.Office365.com, outlook.office.com

- \<nome del tenant\>. sharepoint.com, \<-nome del tenant\>-my.sharepoint.com, \<-nome del tenant\>-\<app\>. sharepoint.com

- \*. Lync.com con gli intervalli IP per il traffico TCP non

- \*broadcast.officeapps.Live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* Word-edit.officeapps.live.com \*word view.officeapps.live.com, office.live.com

Ulteriori informazioni sulla [distribuzione e la gestione delle impostazioni del proxy in Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) e [verifica di Office 365 non è limitato per il proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Con un singolo circuito ExpressRoute, non esiste alcuna disponibilità elevata per Trey Research. Nel caso di esito negativo coppia ridondanti Trey dei dispositivi di edge che servono la connettività ExpressRoute, non è un aggiuntive ExpressRoute a commutazione di circuito di failover in. Ottenendo Trey Research un potrebbe eseguire il failover a internet verrà richiedono la riconfigurazione manuale e in alcuni casi gli indirizzi IP nuovo. Trey si desidera aggiungere la disponibilità elevata, la soluzione più semplice consiste nell'aggiungere ulteriori circuiti ExpressRoute per ogni località e la configurazione del circuito in modo attivo/attivo.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routing ExpressRoute per Office 365 con più posizioni

Nell'ultimo scenario, il routing del traffico di Office 365 tramite ExpressRoute costituisce la base per l'architettura di routing ancora più complessa. Indipendentemente dal numero di posizioni, numero di continenti in cui sono presenti i percorsi, numero di circuiti ExpressRoute e così via, la possibilità instradare il traffico a Internet e una parte del traffico su ExpressRoute saranno necessaria.
  
Le domande aggiuntive per i clienti con più posizioni in più aree geografiche, è necessario rispondere includono:
  
1. È richiesto un ExpressRoute a commutazione di circuito in qualunque posizione? Se si sta utilizzando Skype Business online o in questione con riservatezza latenza per SharePoint Online o Exchange Online, ogni percorso di una coppia di ridondanti del circuito ExpressRoute attivo/attivo. Skype per Business media qualità e rete la connettività Guida per ulteriori informazioni, vedere.

2. Se un circuito ExpressRoute non è disponibile una determinata area, come il traffico di Office 365 indirizzato verranno distribuito?

3. Che cos'è il metodo preferito per il traffico consolidamento nel caso di reti con tutti i percorsi di piccole dimensioni?

Ognuna di queste rappresenta una sfida univoca che è necessario valutare la propria rete, nonché le opzioni offerte da Microsoft.

|**Considerazione**|**Componenti di rete per valutare**|
|:-----|:-----|
|Circuiti in più posizioni  <br/> |È consigliabile almeno del due circuito configurato in modo attivo/attivo.  <br/> Esigenze di costo, la latenza e larghezza di banda devono essere confrontate.  <br/> Utilizzare BGP route costi, i file PAC e NAT per la gestione del routing con più circuiti.  <br/> |
|Routing da posizioni senza un circuito ExpressRoute  <br/> |Si consiglia di uscita e la risoluzione DNS come raggiungere l'utente che ha creato la richiesta per Office 365.  <br/> Consente di inoltro di DNS per consentire a sedi remote individuare l'endpoint appropriato.  <br/> Client in sedi remote deve disporre di una route che consente di accedere a commutazione di circuito ExpressRoute disponibili.  <br/> |
|Consolidamento di ufficio di piccole dimensioni  <br/> |Utilizzo della larghezza di banda e i dati disponibile deve essere confrontato con attenzione.  <br/> |

> [!NOTE]
> Se la route è disponibile indipendentemente dalla posizione fisica, Microsoft preferiscano ExpressRoute tramite internet.
  
Ognuna di queste considerazioni deve essere presi in considerazione per ogni rete univoco. Di seguito è riportato un esempio.
  
### <a name="example-2-multi-geographic-locations"></a>Nell'esempio 2: Più geografiche
  
In questo esempio è uno scenario di una società fittizia denominata enorme assicurativi che dispone di più posizioni geografiche.
  
Assicurazione enorme su più aree geografiche con uffici in tutto il mondo. Che desiderano implementare ExpressRoute Azure per Office 365 mantenere la maggior parte del traffico di Office 365 per le connessioni di rete diretta. Assicurazione enorme include inoltre uffici in due continenti aggiuntivi. I dipendenti in sedi remote in cui non è realizzabile ExpressRoute saranno necessario eseguire il routing a una o entrambe le funzionalità principali per utilizzare una connessione ExpressRoute.
  
Il principio guida consiste nell'eseguire al più presto il traffico destinate a Office 365 per un Data Center Microsoft. In questo esempio enorme assicurativi necessario decidere se le sedi remote devono eseguire il routing tramite Internet per ottenere un Data Center Microsoft qualsiasi connessione più presto possibile o se le sedi remote devono eseguire il routing tramite una rete interna per accedere a un database di Microsoft Data Center con una connessione ExpressRoute al più presto.
  
Centri dati, reti e architettura delle applicazioni di Microsoft sono progettati per eseguire a livello globale diverse comunicazioni e la manutenzione in modo più efficace possibile. Questa è una delle reti di grandi dimensioni in tutto il mondo. Le richieste destinate a Office 365 che restano nelle reti dei clienti più lunga del necessario non saranno in grado di sfruttare questa architettura.
  
Dell'enorme assicurativi operazione, si dovrebbe procedere in base alle applicazioni che intendono utilizzare su ExpressRoute. Ad esempio, se si sta Skype per le aziende Online cliente o si prevede di sfruttare ExpressRoute connettività per la connessione a Skype esterno per le riunioni in linea aziendale, la progettazione consigliata in Skype per la qualità dei supporti Business Online e di rete Guida di integrazione applicativa è effettuare il provisioning di un circuito ExpressRoute aggiuntivo per la terza posizione. È possibile che più costosa dal punto di vista di rete; Tuttavia, il routing delle richieste da un continente a un'altra prima fornitura di un Data Center Microsoft potrebbe causare un'esperienza insufficiente o non può essere utilizzata durante Skype per le comunicazioni e riunioni Online di Business.
  
Se enorme assicurativi non sta utilizzando o non si intende utilizzare Skype Business online in alcun modo, il routing del traffico di rete di Office 365 indirizzato al continente con un ExpressRoute connessione potrebbe essere realizzabili tuttavia può causare latenza non necessario o TCP congestione. In entrambi i casi Internet routing traffico destinato a Internet nel sito locale è consigliato per sfruttare le reti di distribuzione del contenuto da Office 365 utilizza.
  
![ExpressRoute a più aree](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Quando si enorme assicurativi è prevista la propria strategia di più aree, esistono diversi aspetti da considerare intorno a dimensioni di circuito, numero del circuito, il failover e così via.
  
Con ExpressRoute in un'unica posizione con più aree tenta di utilizzare circuito enorme assicurativi si desidera verificare che le connessioni a Office 365 da sedi remote vengano inviate al datacenter di Office 365 più vicino headquarters e ricevute dal sede. A tale scopo, enorme assicurativi implementa inoltro DNS per ridurre il numero di round trip e ricerche DNS necessari per stabilire la connessione con l'ambiente Office 365 più vicino al punto di uscita headquarters internet appropriata. In questo impedisce al client di risoluzione di un server front-end locale e il server front-End a che la persona si connette si trova vicino headquarters dove enorme assicurativi è peering con Microsoft. È inoltre possibile ottenere per [assegnare un server di inoltro condizionale di un nome di dominio](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
In questo scenario, il traffico proveniente da sedi remote potrebbe risolvere l'infrastruttura di front-end di Office 365 in Nord America e utilizzare Office 365 per connettersi ai server back-end in base all'architettura dell'applicazione di Office 365. Ad esempio, Exchange Online verrà chiusa la connessione in Nord America e tali server front-end potrebbe connettersi al server cassette postali back-end ovunque si trova il tenant. Tutti i servizi di dispongano di un servizio distribuito su larga scala porta anteriore comprese unicast e anycast destinazioni.
  
Se Humongous Insurance dispone di uffici principali in più continenti, sono consigliabili almeno del due circuito attivo/attivo per ogni area al fine di ridurre la latenza per le applicazioni riservate, ad esempio Skype Business online. Se tutti gli uffici in un singolo continente o non utilizza collaborazione in tempo reale, con un uscita consolidata o distribuita scegliere è una decisione specifica dei clienti. Quando sono disponibili più circuiti, BGP routing assicura failover non qualsiasi singolo a commutazione di circuito sia più disponibile.
  
Ulteriori informazioni sulle [configurazioni di routing](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) di esempio e [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Selettiva routing con ExpressRoute

Routing selettiva con ExpressRoute potrebbero essere necessari per diversi motivi, ad esempio test, distribuzione ExpressRoute a un sottoinsieme di utenti. Sono disponibili diversi strumenti i clienti possono utilizzare per instradare il traffico di rete di Office 365 in modo selettivo su ExpressRoute:
  
1. **Route filtro/separazione** - consentendo la route BGP a Office 365 in ExpressRoute a un sottoinsieme del router o subnet. In tal modo, in modo selettivo segmento di rete dei clienti o ubicazione dell'ufficio fisico. Si tratta comune per scaglionare implementazione di ExpressRoute per Office 365 e configurato nei dispositivi BGP.

2. **File/URL PAC** - indirizzamento di Office 365 indirizzato il traffico di rete per gli FQDN specifici per il routing su un percorso specifico. In tal modo selettivo dal computer client identificati dalla [distribuzione di file PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Filtraggio delle route** - [filtri Route](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) rappresentano un modo per utilizzare un sottoinsieme dei servizi supportati da tramite Microsoft peering.

4. **Le community BGP** , filtro in base all'utilizzo di [tag community BGP](https://aka.ms/bgpexpressroute365) consente al cliente determinare quali applicazioni di Office 365 attraversato ExpressRoute e quale attraversato internet.

Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Argomenti correlati

[Connettività di rete con Office 365](network-connectivity.md)
  
[Azure ExpressRoute per Office 365](azure-expressroute.md)
  
[Gestione di ExpressRoute per la connettività di Office 365](managing-expressroute-for-connectivity.md)
  
[Pianificazione della rete con ExpressRoute per Office 365](network-planning-with-expressroute.md)
  
[Implementazione di ExpressRoute per Office 365](implementing-expressroute.md)
  
[Qualità multimediale e le prestazioni di connettività di rete in Skype for Business in linea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ottimizzazione della rete per Skype Business online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute e QoS in Skype for Business in linea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flusso di chiamate tramite ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Utilizzo della caratteristica community BGP in ExpressRoute per gli scenari di Office 365](bgp-communities-in-expressroute.md)
  
[Ottimizzazione delle prestazioni di Office 365 mediante l'uso della cronologia delle prestazioni e delle previsioni](performance-tuning-using-baselines-and-history.md)
  
[Piano di risoluzione dei problemi di prestazioni per Office 365](performance-troubleshooting-plan.md)
  
[URL e intervalli di indirizzi IP per Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Ottimizzazione delle prestazioni e rete di Office 365](network-planning-and-performance.md)
