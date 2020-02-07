---
title: Diagramma accessibile-integrazione di rete dei prodotti di Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: Questo articolo è una versione di testo accessibile del diagramma denominato Network Integration of Microsoft Office Server Products.
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843867"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagramma accessibile-integrazione di rete dei prodotti di Microsoft Office Server

**Riepilogo:** Questo articolo è una versione di testo accessibile del diagramma denominato Network Integration of Microsoft Office Server Products.
  
In questo poster è illustrata in generale l'ambiente di rete che include Lync Server 2013, SharePoint 2013 ed Exchange Server 2013. Vengono illustrati anche gli elementi di rete seguenti che sono comuni tra questi prodotti: accesso remoto e interno, autenticazione, traffico client e routing del traffico tramite dispositivi condivisi. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Concetti di alto livello per Lync, Exchange, SharePoint Server e Office Web Apps

### <a name="about-the-design"></a>Informazioni sulla progettazione

#### <a name="streamlined-network-design"></a>Progettazione della rete semplificata

Questa topologia illustra una distribuzione di rete locale di SharePoint 2013, Exchange Server 2013 e Lync Server 2013. Viene inoltre illustrato l'utilizzo del servizio basato sul cloud Microsoft, Exchange Online Protection, che fornisce protezione da posta indesiderata e malware per il traffico SMTP (Simple Mail Transfer Protocol) in ingresso da Internet. 
  
La progettazione della rete è semplificata per un insieme minimo di funzionalità di rete. La progettazione non tiene conto di altre funzionalità di sicurezza o infrastruttura che potrebbero essere necessarie per alcune organizzazioni. 
  
Diagramma seguente: 
  
- Viene fornita una topologia di rete di esempio che illustra il traffico in ingresso e in uscita attraverso un router gateway e il bilanciamento del carico del traffico delle sessioni client (esterno e interno) ai livelli di SharePoint, Exchange e Lync Server appropriato. 
    
- Viene illustrato l'utilizzo di server di accesso remoto opzionali, ad esempio un gateway VPN di terze parti o un server DirectAccess, per fornire comunicazioni sicure per i dipendenti in roaming o in remoto. 
    
- Informazioni dettagliate sul flusso di traffico di SharePoint, Exchange e Lync dal client al livello di ogni server della piattaforma. 
    
- Identifica il tipo di connessione di accesso remoto o interno basato sul client (ad esempio, un partner o un dipendente) e il metodo di autenticazione utilizzato. 
    
- Suddivide le piattaforme SharePoint, Exchange e Lync in base ai ruoli del server necessari, identificando il front-end, l'applicazione, il database e altri livelli. 
    
L'architettura utilizzata in questo articolo per SharePoint, Lync e Exchange non suggerisce un modo preferito per implementare queste piattaforme. Questo è un semplice esempio, in quanto le topologie differiscono in base ai requisiti di rete e alle considerazioni di sicurezza univoci. 
  
#### <a name="gateway-router"></a>Router gateway

Per questa topologia, il router del gateway si trova al bordo della rete e instrada tutto il traffico in ingresso e in uscita da e verso la Intranet. In alternativa, possono essere presenti anche altri componenti che colmano la distanza tra il router gateway e il bilanciamento del carico visualizzato, ad esempio più livelli di firewall. Questa topologia rappresenta un solo modo per distribuire la rete da molti. In questa configurazione, il gateway è configurato con gli elenchi di controllo di accesso (ACL, Access Control List) per consentire il traffico IP in ingresso e in uscita molto specifico sulle interfacce del router. Gli elenchi ACL, controllo avanzato o NAT (Network Address Translation) possono essere eseguiti anche su altri dispositivi, ad esempio i firewall, in tutta la rete. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Dispositivi di bilanciamento del carico e proxy inversi

È possibile utilizzare soluzioni di bilanciamento del carico hardware o software per reindirizzare il traffico per i segmenti, inclusi i server Web front-end di SharePoint e i server Accesso client di Exchange (CASs). In alcuni casi, è consigliabile utilizzare un dispositivo di bilanciamento del carico basato su hardware Layer 7 per i requisiti di persistenza, in quanto è possibile ottenere risultati migliori utilizzando le informazioni contenute nella richiesta, ad esempio cookie o intestazioni. Tuttavia, fattori quali costo e aumento dell'utilizzo e del carico di lavoro da una soluzione di questo tipo potrebbero non essere auspicabili per le specifiche esigenze. Tenere in considerazione i seguenti punti per il bilanciamento del carico tra SharePoint, Exchange e Lync: 
  
- SharePoint-per SharePoint 2013, non è necessario abilitare l'affinità per i server Web front-end. In genere, questo verrebbe utilizzato per creare sessioni adesive ed evitare più richieste di autenticazione dai client a ogni server Web front-end. Il nuovo servizio di cache distribuita in SharePoint 2013 archivia e distribuisce i token di accesso tra i server Web della farm di SharePoint. 
    
- Exchange-in Exchange 2013, il ruolo CAS è stato creato per l'utilizzo del bilanciamento del carico Layer 4, distribuendo le richieste a livello di trasporto. Questo può ridurre significativamente l'utilizzo del bilanciamento del carico e il carico di lavoro. 
    
- Il bilanciamento del carico DNS (Domain Name System) di Lync è consigliato per il traffico SIP (Session Initiation Protocol) per i pool Lync. Il bilanciamento del carico hardware (HLB) è necessario per il traffico di Lync Web (HTTPS). 
    
### <a name="remote-access-options"></a>Opzioni di accesso remoto

Sono disponibili diverse opzioni che consentono di pubblicare risorse Intranet per i partner su Internet o di fornire un accesso remoto sicuro per i dipendenti remoti o in roaming. Esempi di questo tipo sono proxy inversi, DirectAccess e gateway VPN di terze parti. Le soluzioni di accesso remoto descritte più avanti in questa sezione sono possibili per SharePoint, Lync ed Exchange oppure per qualsiasi combinazione di questi server in una distribuzione locale. Tuttavia, alcune opzioni remote potrebbero non funzionare con una soluzione specifica. 
  
Proxy inverso-un proxy inverso supporta la crittografia del traffico, ad esempio SSL (Secure Sockets Layer) e con essa è possibile pubblicare applicazioni Intranet e risorse Web per utenti e partner autenticati su Internet. Un esempio è Microsoft Forefront Unified Access Gateway (UAG). Molti dispositivi di bilanciamento del carico hardware supportano anche la funzionalità proxy inverso. Tuttavia, esistono ancora scenari validi per l'utilizzo di una soluzione autonoma in base alle esigenze e ai requisiti, ad esempio l'isolamento del traffico, la sicurezza compartimentazione e l'ottimizzazione delle prestazioni. 
  
Considerazioni e vantaggi del proxy inverso: 
  
- Fornisce l'accesso protetto e autenticato per i partner o gli utenti che accedono alle risorse Intranet (utilizza SSL (TCP 443) tra il client e il server proxy inverso). 
    
- Per Exchange, un vantaggio dell'utilizzo di un proxy inverso, ad esempio Forefront UAG, è la preautenticazione prima di accedere al server Accesso client di Exchange. Gli utenti di accesso remoto che utilizzano applicazioni pubblicate come Outlook Web Access (OWA) sono in grado di eseguire l'autenticazione con i metodi di base, NTLM o Kerberos prima che raggiungano la rete interna. 
    
- Per Exchange e SharePoint, le soluzioni come Forefront UAG possono terminare le connessioni SSL e ridurre il carico del server delle risorse Intranet fornendo un unico punto di gestione per i certificati. 
    
- Per Lync, il traffico Web (HTTPS) passa attraverso il proxy inverso (TCP 443) per la comunicazione client. Il proxy inverso inoltra la connessione HTTPS ai servizi Web Lync, alle autorità di certificazione di Exchange e a Office Web Apps. Lync Server 2013 non supporta UAG. 
    
DirectAccess-una tecnologia di accesso remoto che si basa su IPsec (Internet Protocol Security) per l'autenticazione e la crittografia del traffico tra il client e il server DirectAccess. DirectAccess fornisce l'accesso simultaneo alle risorse Internet e Intranet per i dipendenti mobili e remoti senza dover avviare una connessione. 
  
Punti DirectAccess da prendere in considerazione: 
  
- DirectAccess utilizza il traffico protetto con IPsec (protocollo 50 e 51 e UDP 500) tra il client e il server DirectAccess. 
    
- DirectAccess per Windows Server 2012 e Windows 8 non necessita di una distribuzione di infrastruttura a chiave pubblica (PKI) per l'autenticazione del server e del client. 
    
- Si consiglia di non utilizzare DirectAccess con Lync Server 2013 a causa di problemi di latenza audio e video associati alla crittografia e alla decrittografia IPsec. 
    
    Gateway VPN-i gateway VPN tipici offrono una connessione di accesso remoto in cui un computer client di accesso remoto viene progettato logicamente sulla rete Intranet tramite una connessione a tunnel e avviata dall'utente. È possibile utilizzare l'accesso remoto unificato in Windows Server 2012 o diverse soluzioni di terze parti per fornire l'accesso protetto alla rete Intranet per i dipendenti in roaming o in remoto. La VPN non è consigliata per Lync. Il traffico Lync remoto deve utilizzare i server perimetrali e suddividere il tunneling. 
    
### <a name="domain-name-system-dns-considerations"></a>Considerazioni su DNS (Domain Name System)

È necessario pianificare il set di record DNS che consentono agli utenti di Internet e Intranet di risolvere i nomi DNS negli indirizzi IP corretti. 
  
- Per i partner basati su Internet e il roaming o i dipendenti remoti, i record DNS registrati con i server DNS Internet offrono una soluzione all'insieme di indirizzi IP pubblici che corrispondono al router gateway, al server perimetrale di Lync, all'insieme di indirizzi IP virtuali (VIP) su il bilanciamento del carico e il gateway DirectAccess o VPN in base alle esigenze. 
    
- Per gli utenti basati su Intranet, i record DNS registrati con i server DNS Intranet offrono una soluzione all'insieme di indirizzi IP virtuali (VIP) del servizio di bilanciamento del carico per l'accesso alle risorse di SharePoint, Lync e Exchange. 
    
- I client DirectAccess utilizzano i server DNS Intranet per i nomi corrispondenti allo spazio del nome DNS Intranet e ai server DNS Internet per i nomi che non lo fanno. Per semplificare l'operazione di DirectAccess, prendere in considerazione l'utilizzo di un'implementazione DNS suddivisa che utilizza spazi dei nomi DNS diversi per i nomi Intranet e basati su Internet. Ad esempio, utilizzare contoso.com per lo spazio dei nomi Internet e corp.contoso.com per lo spazio dei nomi Intranet. 
    
- Exchange utilizza un modello DNS suddiviso in cui la risoluzione host-IP è diversa per il traffico pubblico instradato da quello della rete aziendale. È necessario disporre almeno dei record DNS per OWA, individuazione automatica, URL ActiveSync per il traffico client e un record MX per la posta in ingresso. 
    
- Se si utilizza Exchange Online Protection (EOP), il record MX punta a tale servizio invece che alla farm di Exchange. 
    
- Per Exchange, è necessario un record TXT relativo alla proprietà nel DNS pubblico e un ID org federativo per configurare la condivisione federata. 
    
- I client VPN di accesso remoto possono essere configurati per l'utilizzo di solo server DNS Intranet quando la connessione VPN di accesso remoto è attiva. 
    
### <a name="diagram-description"></a>Descrizione diagramma

Questo diagramma fornisce un esempio di topologia di rete che illustra il traffico in ingresso e in uscita attraverso un router gateway e il bilanciamento del carico del traffico delle sessioni client (esterno e interno) ai livelli di SharePoint, Exchange e Lync Server appropriato. La descrizione di questo diagramma è suddivisa in due parti: 
  
- Descrizione dei componenti illustrati nel diagramma 
    
- Descrizione del modo in cui il traffico passa attraverso i componenti ai livelli del server SharePoint, Exchange, Lync e Office Web Apps. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Descrizione dei componenti illustrati nel diagramma

#### <a name="user-types"></a>Tipi di utenti

Esistono quattro diversi tipi di utenti, tre all'esterno della rete e dei servizi cloud e uno interno, che include: 
  
- Aziende partner (business-to-business)-esterne 
    
- Partner singoli (SharePoint e Anonymous (Lync))-esterni 
    
- Gestione del roaming e dipendenti remoti-esterni 
    
- Dipendenti interni 
    
#### <a name="cloud-based-email-traffic"></a>Traffico di posta elettronica basato sul cloud

È presente un componente basato sul cloud per il traffico di posta elettronica basato su SMTP, ovvero host di posta Internet o Exchange Online Protection. 
  
#### <a name="authentication-for-external-access"></a>Autenticazione per l'accesso esterno

È presente un insieme specifico di procedure di autenticazione per Lync, SharePoint e Exchange per ognuno dei tipi di utenti. Sono descritte più avanti in questo documento. 
  
#### <a name="gateway-router-with-acls"></a>Router gateway con ACL

Il router del gateway si trova al bordo della rete e instrada tutto il traffico in ingresso e in uscita da e verso la Intranet. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Server di accesso remoto per Lync e SharePoint

Questa topologia include un server perimetrale di Lync e un gateway VPN di SharePoint o un server DirectAccess. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Dispositivo di bilanciamento del carico e proxy inverso

È possibile utilizzare soluzioni di bilanciamento del carico hardware o software per reindirizzare il traffico per i segmenti, inclusi i server Web front-end di SharePoint e i server Accesso client di Exchange (CASs). Questa topologia Visualizza Lync VIP, SharePoint VIP e i componenti VIP di Exchange nel bilanciamento del carico. 
  
#### <a name="servers"></a>Servers

Sono disponibili quattro server: Lync, SharePoint, Exchange e il server Office Web Apps. Ogni server può disporre di tre livelli: un livello front-end, client-Access, un livello applicazione e un livello di database/archiviazione.
  
#### <a name="front-end-client-access-tier"></a>Livello front-end, client-Access

Questo livello include componenti su tutti e quattro i server: 
  
- Pool Lync (front-end). Nel diagramma vengono visualizzati due database di Lync. 
    
- SharePoint front-end e cache distribuita. Nel diagramma sono visualizzati tre database di SharePoint. 
    
- Autorità di certificazione di Exchange. Nel diagramma sono visualizzati due database di Exchange. 
    
- Server Office Web Apps. Nel diagramma sono visualizzati due database di Office Web Apps. 
    
#### <a name="application-tier"></a>Livello applicazione

Questo livello include componenti solo in SharePoint Server: 
  
- Ricerca (query, index, admin). Nel diagramma sono visualizzati tre database di SharePoint. 
    
- Elaborazione batch. Nel diagramma sono visualizzati tre database di SharePoint. 
    
#### <a name="databasestorage-tier"></a>Livello di database/archiviazione

Questo livello include componenti nei server Lync, SharePoint e Exchange: 
  
- Database Lync (back-end). Nel diagramma sono visualizzati tre database di Lync. 
    
- Database di SharePoint. Nel diagramma sono visualizzati tre database di SharePoint. 
    
- Server cassette postali di Exchange. Nel diagramma sono visualizzati due server cassette postali di Exchange. 
    
Per ulteriori informazioni sui componenti installati in ogni ruolo del server di SharePoint, vedere [topologie semplificate per sharepoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Descrizione del modo in cui il traffico passa attraverso i componenti ai diversi livelli del server

In questa sezione viene descritto in che modo le richieste degli utenti passano attraverso la topologia di rete 
  
#### <a name="authentication-and-routing-for-external-access"></a>Autenticazione e routing per l'accesso esterno

Sono disponibili tre diversi tipi di client all'esterno della rete e dei servizi cloud, tra cui: 
  
- Aziende partner (business-to-business)-esterne 
    
- Partner singoli (SharePoint e Anonymous (Lync))-esterni 
    
- Gestione del roaming e dipendenti remoti-esterni 
    
Il processo di autenticazione e routing per ogni tipo di utente esterno viene descritto singolarmente. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Società partner (business-to-business) (https://partnerweb.contoso.com)

- Lync: la relazione di trust federativa con altre organizzazioni, Skype e la connettività per la messaggistica istantanea pubblica (PIC) con AOL. Il traffico federativo di Lync passa attraverso il router gateway al server perimetrale Lync, al VIP Lync (server di bilanciamento del carico/proxy inverso) e quindi al server Lync. 
    
- SharePoint: provider di identità di partner attendibile con autenticazione SAML. Il traffico client di SharePoint passa attraverso il router gateway al VIP di SharePoint (server di bilanciamento del carico/proxy inverso) e quindi al server di SharePoint. 
    
- Exchange: Mutual AUTH TLS per il traffico di posta, autenticazione SAML per la condivisione federata. Il traffico del client di Exchange passa attraverso il router gateway al VIP di Exchange (server di bilanciamento del carico/proxy inverso) e quindi al server di Exchange. 
    
- Il traffico SMTP passa attraverso il router gateway e tramite il VIP di Exchange (server di bilanciamento del carico/proxy inverso) al server di Exchange. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Partner singoli (SharePoint) e Anonymous (Lync) (https://partnerweb.contoso.com ehttps://meet.contoso.com)

- Lync: gli utenti anonimi possono partecipare solo alle riunioni di Lync organizzate dai dipendenti. Il traffico federativo di Lync passa attraverso il router gateway al server perimetrale Lync, al VIP Lync (server di bilanciamento del carico/proxy inverso) e quindi al server Lync. 
    
- SharePoint: provider di identità di partner attendibile con autenticazione SAML o autenticazione basata su moduli. Il traffico client di SharePoint passa attraverso il router gateway al VIP di SharePoint (server di bilanciamento del carico/proxy inverso) e quindi al server di SharePoint. 
    
- Exchange: non applicabile. 
    
- Il traffico Web Lync passa attraverso il router gateway al server perimetrale di Lync, al VIP Lync (server di bilanciamento del carico/proxy inverso), a un dispositivo di bilanciamento del carico hardware, necessario per il traffico HTTPS e quindi al server Lync. 
    
#### <a name="roaming-and-remote-employees"></a>Gestione del roaming e dipendenti remoti

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* L'URL di Exchange include le seguenti directory virtuali: individuazione automatica, ECP, EWS, Microsoft-Server-ActiveSync, Rubrica offline, OWA, PowerShell 
  
- Lync: TLS-DSK o autenticazione NTLM. Il traffico client di Lync passa attraverso il router gateway al server perimetrale Lync, al VIP Lync (server di bilanciamento del carico/proxy inverso) e quindi al server Lync. 
    
- SharePoint: Servizi di dominio Active Directory (AD DS), autenticazione basata su moduli o autenticazione SAML. Il traffico client di SharePoint passa attraverso il gateway VPN o il server DirectAccess al VIP di SharePoint (server di bilanciamento del carico/proxy inverso) e quindi al server di SharePoint. 
    
- Exchange: autenticazione di base su SSL (ActiveSync, individuazione automatica), autenticazione basata su form (OWA). Il traffico del client di Exchange passa attraverso il router gateway al VIP di Exchange (server di bilanciamento del carico/proxy inverso) e quindi al server di Exchange. 
    
- Il traffico client di Lync passa attraverso il router gateway al VIP di Lync (server di bilanciamento del carico/proxy inverso) a un dispositivo di bilanciamento del carico hardware, necessario per il traffico HTTPS e quindi al server Lync. 
    
#### <a name="authentication-for-internal-access"></a>Autenticazione per l'accesso interno

#### <a name="internal-employees"></a>Dipendenti interni

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- Lync: Kerberos, TLS-DSK o autenticazione NTLM. Il traffico client di Lync passa a Lync VIP (server di bilanciamento del carico/proxy inverso) e quindi al server Lync. 
    
- SharePoint: Servizi di dominio Active Directory (AD DS), autenticazione basata su moduli o autenticazione SAML. Il traffico client di SharePoint passa al VIP di SharePoint (server di bilanciamento del carico/proxy inverso) e quindi al server di SharePoint. 
    
- Exchange: Servizi di dominio Active Directory, autenticazione basata su moduli. Il traffico client di Exchange passa al VIP di Exchange (server di bilanciamento del carico/proxy inverso) e quindi al server di Exchange. 
    
- Il traffico client di Lync passa al VIP di Lync (server di bilanciamento del carico/proxy inverso) a un dispositivo di bilanciamento del carico hardware, necessario per il traffico HTTPS e quindi al server Lync. 
    
#### <a name="cloud-based-email-traffic"></a>Traffico di posta elettronica basato sul cloud

Il componente basato sul cloud per il traffico di posta elettronica basato su SMTP è costituito da host di posta Internet o Exchange Online Protection.
  
Questi componenti spostano il traffico della posta elettronica sulla rete tramite SMTP. Il traffico passa attraverso il router gateway al VIP di Exchange (server di bilanciamento del carico/proxy inverso) e quindi al server di Exchange. 
  
### <a name="network-traffic-legend"></a>Legenda del traffico di rete

La casella Legenda Visualizza graficamente i diversi tipi di traffico rappresentati sul grafico in linee colorate diverse, come indicato di seguito: 
  
- Linea verde: traffico SIP Lync 
    
- Riga blu: traffico Web Lync 
    
- Riga viola: traffico client di SharePoint 
    
- Linea arancione: traffico client di Exchange 
    
- Linea grigia: traffico del server di posta di Exchange tra Exchange locale ed Exchange Online Protection. 
    
I diversi tipi di traffico e le porte che utilizzano sono descritti anche nella casella Legenda. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Traffico SIP Lync e traffico Web Lync

Lync Edge Server utilizza le porte seguenti per la comunicazione con gli utenti esterni: 
  
- Signaling/traffico IM (SIP/SIMPLE): porta TCP 443 (aperta per il traffico in ingresso) 
    
- Traffico Web Conferencing (PSOM): TCP 443 (aperto per il traffico in ingresso) 
    
- Traffico A/V (SRTP): TCP 443, UDP 3478 e TCP 50000-59999 (facoltativo) (aperto per il traffico in ingresso e in uscita) 
    
Lync Edge Server utilizza le seguenti porte per la comunicazione federativa: 
  
- Porte TCP 5061 (SIP), 5269 (XMPP), 443 e UDP 3478 (SRTP) (aperto per il traffico in ingresso e in uscita) 
    
#### <a name="sharepoint-client-traffic"></a>Traffico client di SharePoint

SharePoint può utilizzare la porta TCP 443 (SSL) per la comunicazione crittografata tra il client e il bilanciamento del carico. Per l'accesso esterno da Internet, è necessario che questa porta venga aperta per il traffico in ingresso e in uscita sul router gateway (o sul firewall esterno). 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Traffico del server di posta elettronica di Exchange e traffico di Exchange

Exchange utilizza la porta TCP 25 (SMTP) per le comunicazioni da server a server. La maggior parte del traffico client (OWA, ActiveSync, individuazione automatica, Outlook via Internet) viene gestito tramite la porta 443 (HTTPS). Se si dispone di client POP o IMAP, le porte 110 (POP3), 995 (POP3 crittografato), 143 (IMAP4), 993 (IMAP4 crittografato) e 587 (SMTP) vengono utilizzati anche per supportare questi client. 
  
#### <a name="more-on-lync-network-traffic"></a>Altre informazioni sul traffico di rete di Lync?

Informazioni su come Lync Server può aiutare l'organizzazione a fornire messaggistica istantanea, Web Conferencing, condivisione applicazioni e comunicazioni vocali. Per ulteriori informazioni, vedere [poster dei carichi di lavoro del protocollo Microsoft Lync Server 2013](https://aka.ms/G5jzjo). 
  
Nel poster è incluso anche un codice QR che consente di accedere a queste informazioni. 
  

