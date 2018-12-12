---
title: Diagramma accessibile - rete integrazione di prodotti Microsoft Office Server
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: In questo articolo è una versione testo accessibile del diagramma denominato rete integrazione di prodotti Microsoft Office Server.
ms.openlocfilehash: 3fa27b99bf0babf00c536057b9d21da784b6d94f
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
ms.locfileid: "17504429"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a>Diagramma accessibile - rete integrazione di prodotti Microsoft Office Server

**Riepilogo:** In questo articolo è una versione testo accessibile del diagramma denominato rete integrazione di prodotti Microsoft Office Server.
  
Questo poster fornisce un'illustrazione generale di un ambiente di rete che include Lync Server 2013, SharePoint 2013 ed Exchange Server 2013. Viene inoltre i seguenti elementi di reti che sono comuni a questi prodotti: access interni e remoti, autenticazione, il traffico client e instradare il traffico dispositivi condivisi. 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a>Concetti generali relativi a Lync, Exchange, SharePoint Server e Office Web Apps

### <a name="about-the-design"></a>Sulla progettazione

#### <a name="streamlined-network-design"></a>Struttura della rete semplificate

Questa topologia viene illustrata una distribuzione di rete locale di SharePoint 2013, Exchange Server 2013 e Lync Server 2013. Viene inoltre illustrato l'utilizzo del servizio di basata sul cloud Microsoft, Exchange Online Protection, che offre una protezione da posta indesiderata e malware per il traffico in ingresso Simple Mail Transfer Protocol (SMTP) da Internet. 
  
Semplificata la progettazione di rete a un insieme minimo di funzionalità della rete. La progettazione non tiene conto protezione o infrastruttura funzionalità aggiuntive che potrebbero richiedere alcune organizzazioni. 
  
Figura: 
  
- Fornisce una topologia di rete di esempio che illustrano il traffico in ingresso e in uscita tramite un gateway router e il bilanciamento del carico di sessione il traffico client (interno ed esterno) per i livelli appropriati di SharePoint, Exchange e Lync server. 
    
- Viene illustrato l'utilizzo dei server di accesso remoto facoltativo, ad esempio un gateway VPN di terze parti o un server DirectAccess, per la comunicazione protetta per i dipendenti remoti o mobili. 
    
- Vengono illustrati il SharePoint, Exchange e Lync flusso di traffico da client a ogni livello di piattaforma server. 
    
- Identifica il tipo di connessione di accesso remoto o interno basato su client (ad esempio partner o dipendenti) e il metodo di autenticazione utilizzato. 
    
- Suddivide le piattaforme di SharePoint, Exchange e Lync per ruoli del server richiesti, che identifica il front-end, applicazione, database e altri livelli. 
    
L'architettura utilizzato qui per SharePoint, Lync ed Exchange non suggerisce un modo migliore per l'implementazione di queste piattaforme. Fornisce un esempio come topologie variano in base alle esigenze di rete univoco e considerazioni sulla protezione. 
  
#### <a name="gateway-router"></a>Router gateway

Per questa topologia router gateway si trova in corrispondenza del bordo della rete e il routing di tutto il traffico in ingresso e in uscita da e verso la rete intranet. In alternativa, si potrebbe essere anche altri componenti di collegano la distanza tra il router gateway e il servizio di bilanciamento del carico indicato, ad esempio più livelli di firewall. Questa topologia rappresenta semplicemente un modo per distribuire la rete tra molti. In questa configurazione, il gateway è configurato con elenchi di controllo di accesso (ACL) per consentire molto specifico traffico in ingresso e in uscita basati su IP nelle interfacce router. ACL, ispezione avanzata o Network Address Translation (NAT) può anche essere eseguito su altri dispositivi, ad esempio firewall attraverso la rete. 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a>Carico bilanciamento e dispositivi proxy inverso

È possibile utilizzare soluzioni di bilanciamento del carico di hardware o software per reindirizzare il traffico per i segmenti inclusi i server web front-end SharePoint e server Accesso Client di Exchange (classi). In alcuni casi è preferibile utilizzare il bilanciamento del carico basata su hardware livello 7 per i requisiti di persistenza come è possibile eseguire meglio utilizzando informazioni nella richiesta, ad esempio i cookie o intestazioni. Tuttavia, quali fattori di costo e l'aumento dell'utilizzo e carico di lavoro da questa soluzione non può essere preferibile per specifiche esigenze. Tenere presente quanto segue per il bilanciamento del carico in SharePoint, Exchange e Lync: 
  
- SharePoint - per SharePoint 2013, è necessario abilitare l'affinità per i server web front-end. In genere, questo verrà utilizzato per la creazione di sessioni permanenti ed evitando più richieste di autenticazione da client a ogni server web front-end. Il nuovo servizio Cache distribuita in SharePoint 2013 archivia e distribuisce i token di accesso tra i server web nella farm di SharePoint. 
    
- Exchange - In Exchange 2013, il ruolo del server accesso client è progettato per utilizzare il bilanciamento del carico di livello 4, la distribuzione richieste il livello di trasporto. Utilizzo del servizio di bilanciamento del carico e il carico di lavoro può ridurre notevolmente. 
    
- Lync - bilanciamento del carico del sistema DNS (Domain Name) è consigliata per il traffico di Strumentazione gestione Windows (SIP, Session Initiation Protocol) per i pool di Lync. (Bilanciamento del carico hardware) di bilanciamento del carico hardware è necessaria per il traffico di Lync Web (HTTPS). 
    
### <a name="remote-access-options"></a>Opzioni di accesso remoto

Sono disponibili diverse opzioni che è possono pubblicare risorse della rete intranet per i partner su Internet o fornire l'accesso remoto protetto per i dipendenti remoti o mobili. Quali ad esempio i proxy inversi, DirectAccess e gateway VPN di terze parti. Le soluzioni di accesso remoto descritte più avanti in questa sezione sono le possibilità di SharePoint, Lync ed Exchange o una combinazione di questi server in una distribuzione locale. Tuttavia, alcune opzioni remote potrebbero non funzionare con una particolare soluzione. 
  
Proxy inverso - proxy inverso supporta la crittografia del traffico, ad esempio Secure Sockets Layer (SSL) e con che è possibile pubblicare le applicazioni intranet e risorse web per l'autenticazione utenti e partner in Internet. Un esempio è Microsoft Forefront Unified Access Gateway (UAG). Molti bilanciamento del carico hardware supporta anche la funzionalità di proxy inverso. Esistono, tuttavia, gli scenari ancora validi per l'utilizzo di una soluzione autonoma in base alle esigenze e i requisiti, ad esempio l'ottimizzazione delle prestazioni, il contesto di sicurezza e isolamento di traffico. 
  
Considerazioni e vantaggi relativi proxy inverso: 
  
- Consente l'accesso autenticato e protetta per i partner o utenti che accedono a risorse della rete intranet (utilizza SSL (TCP 443) tra il client e server proxy inverso). 
    
- Per Exchange, un vantaggio dell'utilizzo di un proxy inverso, ad esempio Forefront UAG è preautenticazione prima di accedere al server Accesso Client di Exchange. Gli utenti remoti mediante pubblicati applicazioni come Outlook Web Access (OWA) possono eseguire l'autenticazione di base, NTLM o Kerberos metodi prima che raggiungano la rete interna. 
    
- Per Exchange e SharePoint soluzioni come Forefront UAG possono terminare le connessioni SSL e ridurre il carico del server di risorse intranet fornendo un singolo punto di gestione per i certificati. 
    
- Per Lync, il traffico Web (HTTPS) passa attraverso il proxy inverso (TCP 443) per la comunicazione client. I proxy di proxy inverso il protocollo HTTPS connessione a servizi Web di Lync, accesso client di Exchange e Office Web Apps. Lync Server 2013 non supporta UAG. 
    
DirectAccess - una tecnologia di accesso remoto che si basa su Internet Protocol security (IPsec) per l'autenticazione e per crittografare il traffico tra l'integrità e il server. DirectAccess consente di accedere contemporaneamente a Internet e intranet risorse per i dipendenti mobili e remoti senza dover avviare una connessione. 
  
DirectAccess aspetti da considerare: 
  
- DirectAccess utilizza il traffico IPsec protetta (protocollo 50 e 51 e UDP 500) tra l'integrità e il server. 
    
- DirectAccess per Windows Server 2012 e Windows 8 non è necessaria una distribuzione di infrastruttura a chiave pubblica (PKI) per l'autenticazione di client e server. 
    
- Si consiglia di base utilizzando DirectAccess con Lync Server 2013 a causa di problemi di latenza audio e video associati a crittografia e decrittografia IPsec. 
    
    Gateway VPN - gateway VPN tipica fornire una connessione di accesso remoto in cui un client di accesso remoto è previsto logicamente nella rete intranet attraverso una connessione tunnel e dall'utente. È possibile utilizzare unificata l'accesso remoto in Windows Server 2012 o diverse soluzioni di terze parti per fornire l'accesso protetto alla rete intranet per dipendenti remoti o mobili. VPN non è consigliata per Lync. Il traffico remoto Lync deve utilizzare i server perimetrali e dividere tunnel. 
    
### <a name="domain-name-system-dns-considerations"></a>Considerazioni per Domain Name System (DNS)

È necessario pianificare per il set di record DNS che consentono agli utenti di Internet e intranet risolvere i nomi DNS per gli indirizzi IP appropriati. 
  
- Per basato su Internet partner e dipendenti remoti o mobili, i record DNS registrati con i server DNS Internet forniscono risoluzione per l'insieme di indirizzi IP pubblici corrispondente al router gateway, il Server perimetrale di Lync, l'insieme di indirizzi IP virtuali (VIP) servizio di bilanciamento del carico e il gateway DirectAccess o una rete VPN in base alle esigenze. 
    
- Per gli utenti basate su intranet, i record DNS registrati con server DNS della rete intranet forniscono risoluzione per l'insieme di indirizzi IP virtuali (VIP) del servizio di bilanciamento del carico per l'accesso alle risorse di SharePoint, Lync ed Exchange. 
    
- Client DirectAccess utilizzano server DNS della rete intranet di nomi che corrispondono ai server DNS Internet per i nomi che non e spazio dei nomi DNS intranet. Per semplificare l'operazione di DirectAccess, prendere in considerazione l'utilizzo di un'implementazione di DNS split che utilizza spazi dei nomi DNS diversi per i nomi basato su Internet e intranet. Utilizzare ad esempio, contoso.com per Internet dello spazio dei nomi e corp.contoso.com per lo spazio dei nomi intranet. 
    
- Exchange utilizza un modello DNS diviso in host per la risoluzione IP diverso sul traffico pubblicamente indirizzato rispetto a quello della rete aziendale. Come minimo, è necessario disporre dei record DNS per OWA, individuazione automatica, ActiveSync URL per il traffico client e un record MX per la posta in ingresso. 
    
- Se si utilizza Exchange Online Protection (EOP), il record MX punta a tale servizio anziché la farm di Exchange. 
    
- Per Exchange, è necessario un modello di prova di proprietà record TXT nel sistema DNS pubblico e un ID di organizzazione federativa impostare condivisione federata. 
    
- Accesso remoto VPN client possono essere configurati per utilizzare solo i server DNS della rete intranet quando è attiva la connessione VPN di accesso remoto. 
    
### <a name="diagram-description"></a>Descrizione diagramma

In questo diagramma viene fornita una topologia di rete di esempio che illustrano il traffico in ingresso e in uscita tramite un gateway router e il bilanciamento del carico di sessione il traffico client (interno ed esterno) per i livelli appropriati di SharePoint, Exchange e Lync server. La descrizione di questo diagramma viene suddiviso in due parti: 
  
- Descrizione dei componenti mostrato nella figura 
    
- Descrizione di come traffico si sposta tra i componenti per i livelli di SharePoint, Exchange, Lync e Office Web Apps server. 
    
#### <a name="description-of-components-shown-in-the-diagram"></a>Descrizione dei componenti mostrato nella figura

#### <a name="user-types"></a>Tipi di utente

Sono disponibili quattro tipi di utenti diversi, tre all'esterno dei servizi cloud e di rete e uno interno, che comprendono: 
  
- Società (business to business) partner-esterno 
    
- Singoli partner (SharePoint e anonimi (Lync))-esterno 
    
- Esterni dipendenti remoti e mobili 
    
- Dipendenti interni 
    
#### <a name="cloud-based-email-traffic"></a>Traffico di posta elettronica basata sul cloud

Non vi è un componente basato su cloud per il traffico di posta elettronica basata su SMTP, ospitate su Internet Mail o Exchange Online Protection. 
  
#### <a name="authentication-for-external-access"></a>Autenticazione per l'accesso esterno

Non esiste un set specifico di procedure di autenticazione per Lync, SharePoint ed Exchange per ognuno dei tipi di utente. Vengono descritte in dettaglio più avanti in questo documento. 
  
#### <a name="gateway-router-with-acls"></a>Router gateway con ACL

Router gateway si trova in corrispondenza del bordo della rete e il routing di tutto il traffico in ingresso e in uscita da e verso la rete intranet. 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a>Server di accesso remoto di Lync e SharePoint

Questa topologia include un server perimetrale di Lync e un gateway VPN SharePoint o server DirectAccess. 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a>Servizio di bilanciamento del carico e il dispositivo proxy inverso

È possibile utilizzare soluzioni di bilanciamento del carico di hardware o software per reindirizzare il traffico per i segmenti inclusi i server web front-end SharePoint e server Accesso Client di Exchange (classi). Questa topologia vengono illustrati i componenti di Lync VIP, SharePoint VIP e indirizzo IP virtuale di Exchange nel servizio di bilanciamento del carico. 
  
#### <a name="servers"></a>Server

Esistono quattro server: Lync, SharePoint, Exchange e Office Web Apps Server. Ogni server può essere associato a tre livelli: front-end, a livelli di accesso client, un livello di applicazione e un livello di database e archivi.
  
#### <a name="front-end-client-access-tier"></a>Front-end, a livelli di accesso client

Questo livello è componenti in tutti i quattro server seguenti: 
  
- Pool di Lync (front-end). Nel diagramma vengono illustrati due database Lync. 
    
- Front-end di SharePoint e cache distribuita. Nel diagramma vengono illustrati tre database di SharePoint. 
    
- Exchange Server accesso client. Nel diagramma vengono illustrati due database di Exchange. 
    
- Office Web Apps Server. Nel diagramma vengono illustrati due database di Office Web Apps. 
    
#### <a name="application-tier"></a>Livello applicazione

Questo livello è componenti solo nel server di SharePoint seguenti: 
  
- Ricerca (query, indicizzazione, amministrazione). Nel diagramma vengono illustrati tre database di SharePoint. 
    
- Elaborazione batch. Nel diagramma vengono illustrati tre database di SharePoint. 
    
#### <a name="databasestorage-tier"></a>Livello di database e archivi

Questo livello con componenti sui server Exchange, Lync e SharePoint: 
  
- Database di Lync (back-end). Nel diagramma vengono illustrati tre database Lync. 
    
- Database di SharePoint. Nel diagramma vengono illustrati tre database di SharePoint. 
    
- Server cassette postali di Exchange. Nel diagramma vengono illustrati due server di cassette postali di Exchange. 
    
Per ulteriori informazioni sui componenti installati in ognuno dei ruoli del server SharePoint, vedere [Topologie semplificate per SharePoint 2013](https://aka.ms/Ma5cgk). 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a>Descrizione di come traffico si sposta tra i componenti a livelli diversi server

In questa sezione viene descritto come spostare le richieste degli utenti tramite la topologia di rete. 
  
#### <a name="authentication-and-routing-for-external-access"></a>Autenticazione e il routing per l'accesso esterno

Esistono tre diversi tipi di client esterni servizi cloud e di rete, che comprendono: 
  
- Società (business to business) partner-esterno 
    
- Singoli partner (SharePoint e anonimi (Lync))-esterno 
    
- Esterni dipendenti remoti e mobili 
    
L'autenticazione e il processo di distribuzione per ogni tipo di utente esterno è descritto singolarmente. 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a>Società partner (business-to-business) (https://partnerweb.contoso.com)

- Lync: trust federativo con altre organizzazioni, Skype e la connettività di messaggistica immediata pubblica (PIC) con AOL. Il traffico della federazione Lync passa attraverso il router gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server. 
    
- SharePoint: Attendibili provider di identità di partner con autenticazione SAML. Il traffico client SharePoint passa attraverso il router Gateway nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint. 
    
- Exchange: Mutual Auth TLS per il traffico di posta elettronica, l'autenticazione SAML per la condivisione federata. Il traffico client di Exchange passa attraverso il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange. 
    
- Il traffico SMTP passa attraverso il router Gateway e l'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) al server di Exchange. 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a>Singoli partner (SharePoint) e anonimi (Lync) (https://partnerweb.contoso.com e https://meet.contoso.com)

- Lync: gli utenti anonimi possono partecipare solo alle riunioni di Lync organizzate in base ai dipendenti. Il traffico della federazione Lync passa attraverso il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server. 
    
- SharePoint: Il provider di identità di partner attendibile con autenticazione basata su moduli o autenticazione SAML. Il traffico client SharePoint passa attraverso il router Gateway nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint. 
    
- Exchange: Non applicabile. 
    
- Lync Web traffico attraversa il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server proxy inverso/del servizio di bilanciamento del carico,) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server. 
    
#### <a name="roaming-and-remote-employees"></a>Dipendenti remoti e mobili

1. https://Intranet.contoso.com 
    
2. https://Teams.contoso.com 
    
3. https://My.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://Mail.contoso.com * 
    
6. https://dial.contoso.com *
    
7. https://Meet.contoso.com *
    
* L'URL di Exchange sono le seguenti directory virtuali: servizio di individuazione automatica, ecp, servizi Web Exchange, Microsoft-Server-ActiveSync, della Rubrica offline, owa, PowerShell 
  
- Lync: L'autenticazione TLS DSK o NTLM. Il traffico client Lync passa attraverso il router Gateway per il Server perimetrale di Lync, all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server. 
    
- SharePoint: Servizi di dominio Active Directory (AD DS), l'autenticazione basata su moduli o autenticazione SAML. Il traffico client SharePoint passa attraverso il gateway VPN o il server DirectAccess nell'indirizzo IP virtuale di SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al server di SharePoint. 
    
- Exchange: L'autenticazione di base su SSL (ActiveSync, individuazione automatica), l'autenticazione basata su moduli (OWA). Il traffico client di Exchange passa attraverso il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange. 
    
- Il traffico client Lync passa attraverso il router Gateway per Lync indirizzo IP virtuale (server di proxy inverso/del servizio di bilanciamento del carico) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server. 
    
#### <a name="authentication-for-internal-access"></a>Autenticazione per l'accesso interno

#### <a name="internal-employees"></a>Dipendenti interni

> https://Intranet.contoso.com 
    
> https://Teams.contoso.com 
    
> https://My.contoso.com
    
> https://partnerweb.contoso.com
    
> https://Mail.contoso.com * 
    
> https://dial.contoso.com 
    
> https://Meet.contoso.com
    
> https://Admin.contoso.com
    
- Lync: Autenticazione Kerberos, TLS DSK o NTLM. Il traffico client Lync passa all'indirizzo VIP Lync (server di proxy inverso/del servizio di bilanciamento del carico) e quindi a Lync Server. 
    
- SharePoint: Servizi di dominio Active Directory (AD DS), l'autenticazione basata su moduli o autenticazione SAML. Il traffico client di SharePoint viene inoltrata all'indirizzo VIP SharePoint (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di SharePoint. 
    
- Exchange: Di dominio Active Directory, l'autenticazione basata su form. Il traffico client di Exchange viene inoltrata nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange. 
    
- Il traffico client Lync passerà a Lync indirizzo IP virtuale (server di proxy inverso/del servizio di bilanciamento del carico) al bilanciamento del carico hardware, che è necessaria per il traffico HTTPS, e quindi a Lync Server. 
    
#### <a name="cloud-based-email-traffic"></a>Traffico di posta elettronica basata sul cloud

Il componente basata su cloud per il traffico di posta elettronica basata su SMTP è costituita da host della posta Internet o Exchange Online Protection.
  
Questi componenti spostare il traffico di posta elettronica tramite la rete tramite SMTP. Il traffico attraversa il router Gateway nell'indirizzo IP virtuale di Exchange (server di proxy inverso/del servizio di bilanciamento del carico) e quindi al Server di Exchange. 
  
### <a name="network-traffic-legend"></a>Legenda del traffico di rete

La casella legenda Mostra graficamente i diversi tipi di traffico illustrato nel grafico nelle diverse righe colorate come indicato di seguito: 
  
- Verde riga: Lync SIP traffico 
    
- Blu riga: il traffico Web di Lync 
    
- Viola riga: il traffico client di SharePoint 
    
- Linea arancione: il traffico client di Exchange 
    
- Grigio riga: il traffico di Exchange Server di posta elettronica tra Exchange in locale ed Exchange Online Protection. 
    
Nella casella legenda inoltre descritti i diversi tipi di traffico e le porte che utilizzano. 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a>Traffico SIP Lync e Lync web

Server perimetrale Lync utilizza le porte seguenti per le comunicazioni degli utenti esterni: 
  
- Il traffico di segnalazione/messaggistica immediata (SIP/semplice): porta TCP 443 (open per il traffico in ingresso) 
    
- Web (PSOM) traffico delle conferenze: TCP 443 (aperto per il traffico in ingresso) 
    
- Un traffico audio / video (SRTP): 443 TCP, UDP 3478 e TCP 50000 a 59999 (facoltativo) (aperto per il traffico in ingresso e in uscita) 
    
Server perimetrale Lync utilizza le porte seguenti per le comunicazioni federate: 
  
- Porte TCP 5061 (SIP) 5269 (XMPP) 443 e UDP 3478 (SRTP) (aperto per il traffico in ingresso e in uscita) 
    
#### <a name="sharepoint-client-traffic"></a>Traffico client di SharePoint

SharePoint è possibile utilizzare la porta TCP 443 (SSL) per la comunicazione crittografata tra il client e il servizio di bilanciamento del carico. Per l'accesso esterno da Internet, è necessario che la porta aperto per il traffico in ingresso e in uscita sul router gateway (o firewall esterno). 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a>Il traffico client di Exchange e il traffico di server di posta elettronica di Exchange

Exchange utilizza la porta TCP 25 (SMTP) per le comunicazioni server-to-server. La maggior parte del traffico dei client (OWA, ActiveSync, individuazione automatica, Outlook via Internet) viene gestito tramite la porta 443 (HTTPS). Se sono presenti client POP o IMAP, le porte 110 (POP3), 995 (POP3 crittografato), 143 (IMAP4), 993 crittografate IMAP4 () e 587 (SMTP) vengono utilizzate anche per supportare tali client. 
  
#### <a name="more-on-lync-network-traffic"></a>Ulteriori in Lync il traffico di rete?

Informazioni su come Lync Server consentono alle organizzazioni forniscono messaggistica immediata, servizi di conferenza web, la condivisione delle applicazioni e le comunicazioni vocali. Per ulteriori informazioni, vedere [Poster dei carichi di lavoro di protocollo di Microsoft Lync Server 2013](https://aka.ms/G5jzjo). 
  
Il poster include inoltre un codice QR per accedere a queste informazioni. 
  

