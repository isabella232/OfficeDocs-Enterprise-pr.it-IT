---
title: Reti per la distribuzione di contenuti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 0140f704-6614-49bb-aa6c-89b75dcd7f1f
description: Utilizzare queste informazioni per informazioni sulle reti di distribuzione del contenuto (CDN) e come Office 365 in cui le utilizza. CDN assicurano Office 365 veloce e affidabile per gli utenti finali. Con CDN, servizi cloud quali Office 365 rapidamente scaricare contenuto generico, quali icone, al browser degli utenti quando si utilizzano il servizio attraverso un client web.
ms.openlocfilehash: bcbab3256a0c1ce601abaf3f8b80e998db4bcece
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541377"
---
# <a name="content-delivery-networks"></a>Reti per la distribuzione di contenuti

Utilizzare queste informazioni per informazioni sulle reti di distribuzione del contenuto (CDN) e come Office 365 in cui le utilizza. CDN assicurano Office 365 veloce e affidabile per gli utenti finali. Con CDN, servizi cloud quali Office 365 rapidamente scaricare contenuto generico, quali icone, al browser degli utenti quando si utilizzano il servizio attraverso un client web.
  
 **Per eseguire il titolo** [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).
  
## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Come devono configurare la rete in modo che le reti CDN funzionino al meglio con Office 365?

Se si sta pianificando [la connettività di rete per Office 365](network-connectivity.md), è utile comprendere il funzionamento CDN. È inoltre importante tenere presente che non è possibile filtrare la connettività a CDN in base all'indirizzo IP. Offriamo un elenco di sforzo maggiore degli indirizzi IP per i servizi in Office 365, ad esempio Exchange Online. Acquisire familiarità con i suggerimenti per la [gestione di Office 365 endpoint](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="how-do-cdns-make-services-work-faster"></a>In che modo le reti per la distribuzione dei contenuti velocizzano l'esecuzione dei servizi?

Il download in modo continuativo operazioni comuni come icone può richiedere una larghezza di banda di rete che può essere utilizzato meglio per il download dei contenuti personali importanti, come messaggio di posta elettronica o documenti. Perché Office 365 utilizza un'architettura che include CDN la forma di icone, script e altro contenuto generico può essere scaricato dal server più vicino ai computer client, velocizzando i download. Ciò significa un più rapido accesso al contenuto personale, in modo sicuro archiviati nei Data Center di Office 365.
  
## <a name="what-exactly-is-a-cdn"></a>Esattamente, che cos'è esattamente una rete per la distribuzione dei contenuti?

CDN vengono utilizzate per la maggior parte dei servizi cloud dell'organizzazione. Servizi cloud quali Office 365 sono milioni di clienti download una combinazione di proprietario (ad esempio, messaggi di posta elettronica) e di contenuto generico (ad esempio, le icone) alla volta. È più efficiente per inserire immagini che tutti gli utenti vengono utilizzati, come icone, all'incirca nel computer dell'utente possibile. Tuttavia, non validi per ogni servizio cloud creare datacenter CDN cui sono archiviati contenuto generico in ogni area metropolitane o anche in ogni hub Internet principali in tutto il mondo, in modo che alcuni di questi CDN condivisi.
  
CDN può essere pubblica o privata. CDN private sono proprietà e gestite da una singola società e possono utilizzare solo dell'azienda applicazioni e servizi. Pubblica CDN vengono eseguite dalle organizzazioni che hanno il lease dell'utilizzo di più società. A seconda di dove ti trovi, potrebbe risultare più efficiente per Office 365 scaricare immagini generiche automaticamente da un CDN proprietaria di Office 365 e viene eseguito, CDN pubblico o una combinazione delle due configurazioni. Indipendentemente dal tipo di rete CDN viene utilizzato, la procedura seguente per recuperare i dati sono gli stessi.
  
1. Il client richiede i dati da Office 365.

2. Office 365 restituisce i dati direttamente al client o indirizza i client di una rete CDN.

3. Se i dati sono già presente nella cache la rete CDN, il client scarica i dati direttamente dal percorso di rete CDN più vicino al client in internet.

4. Se i dati non viene memorizzato nella cache la rete CDN, il nodo CDN richiede i dati di Office 365 e quindi della cache di dati per un periodo di tempo dopo il download del client per i dati.

CDN estrarre i file e le immagini da più vicino datacenter di Office 365 e a sua volta, il client utilizza i file e le immagini da CDN più vicino. Quando gli utenti accedono a un servizio cloud, ad esempio la lettura di posta elettronica in Outlook Web App, il browser dell'utente tenta di recuperare i file e le immagini da datacenter Office 365. Anziché impiegando una larghezza di banda recapitare i file e l'ora, Office 365 reindirizza il browser per la rete CDN. La rete CDN fascicolazione datacenter più vicino al browser dell'utente e utilizzo del reindirizzamento degli, consente di scaricare le immagini generiche da quest'ultimo. Utilizzando il reindirizzamento CDN è rapido e consente agli utenti un notevole risparmio del tempo di download.
  
## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>Esiste un elenco di tutti i nomi FQDN su CDN?

L'elenco di nomi di dominio completo e come vengono sfruttare CDN cambia nel tempo, vedere il nostro pubblicata [pagina endpoint di Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744) in base al aggiornati i nomi FQDN dei più recenti su CDN.
  
## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>Esiste un elenco di tutte le reti CDN utilizzati da Office 365?

CDN utilizzato da Office 365 sono sempre soggetta a modifiche e in molti casi non vi sono più CDN partner configurate nel caso in cui uno non è disponibile. Due CDN più comuni in uso sono [incluse Akamai](https://www.akamai.com/us/en/cdn.jsp) e [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/). Entrambe queste soluzioni CDN avere un unico globale migliorando la portata del servizio da più angoli del mondo. Il contenuto archiviato non vi sono inclusi script di Office 365 generale, i file e immagini. Ad esempio, quando si accede portal.office.com, le immagini vengono estratti dalla rete CDN più vicino per velocizzare i caricamenti delle pagine. Altri esempi Office 365 ProPlus archiviazione i bit di installazione in una rete CDN per velocizzare la quantità di tempo che necessario per scaricare la versione più recente di Office. È inoltre disponibile parte proprietario del contenuto archiviato nel CDN, ad esempio i file video per Office 365 Video. Dopo aver caricato i video, i file sono crittografati e memorizzati nel formato crittografato con Azure Media Services. Quando il lettore video di Office 365 consente di recuperare il video viene innanzitutto nella cache per la rete CDN più vicina prima di essere scaricato per accelerare la quantità di tempo che necessario per scaricare il video.
  
## <a name="does-office-365-offer-a-cdn-that-i-can-use-for-my-own-files"></a>Office 365 offre un CDN utilizzabili per i propri file?

Sì! A questo punto la sottoscrizione di Office 365 include un CDN distinto dai Azure che è possibile utilizzare in modo specifico per le risorse di SharePoint Online. Per informazioni su come utilizzare la rete CDN di Office 365, vedere [utilizzo della rete di distribuzione del contenuto di Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).
  
## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>È possibile utilizzare i propri contenuti CDN e della cache della rete locale?

Si sta cercando continuamente nuovi modi supportare le esigenze di clienti ed esplorazione di utilizzo della memorizzazione nella cache delle soluzioni di proxy e altre soluzioni CDN locale.
  
## <a name="is-my-data-safe"></a>I dati sono protetti?

È necessario prestare attenzione grande per contribuire a garantire che vengono protetti i dati che esegue un'azienda. Gli elementi memorizzati in partner network distribuzione dei contenuti sia viene crittografato. ad esempio con [Office 365 Video](https://support.office.com/article/2bed67a1-4052-49ff-a4ce-b7e6530eb98e)o non specifico, del cliente ad esempio i file di installazione di Office 365 ProPlus. Testa su [Centro protezione di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=397383) per acquisire familiarità con il prodotto approfondito per proteggere la privacy degli utenti e dei dati.
  
## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Come proteggere la rete con questi servizi parte 3

Sfruttamento di un'ampia gamma di servizi partner consente a Office 365 implementare la scalabilità e soddisfare i requisiti di disponibilità e su come migliorare l'esperienza utente quando si utilizza Office 365. I servizi di terze parti 3 che utilizza Office 365 sono entrambi gli elenchi di revoche; ad esempio crl.microsoft.com o sa.symcb.com e CDN; ad esempio r3.res.outlook.com. Ogni CDN FQDN Office 365 utilizza è un FQDN personalizzato per Office 365, se sta inviato a un nome di dominio completo su richiesta di Office 365 è possibile essere certi che è controllare il nome di dominio completo e di sottostante contenuto in tale posizione.
  
Per i clienti che ancora da separare i richieste destinate a un datacenter Microsoft o di Office 365 dalle richieste destinati a una parte 3 abbiamo scritto di informazioni aggiuntive sugli [endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).
  
## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Utilizzo di ExpressRoute Azure per Office 365, che modifica aspetti?

[ExpressRoute Azure per Office 365](azure-expressroute.md) fornisce una connessione dedicata a infrastruttura di Office 365 è suddivisi da internet pubblico. Ciò significa che sarà ancora necessario client si connettono tramite connessioni non ExpressRoute a cui connettersi CDN e altre un'infrastruttura Microsoft che non è incluso in modo esplicito nell'elenco dei servizi supportati da ExpressRoute. Per ulteriori informazioni su come instradare il traffico specifico, ad esempio le richieste destinate CDN, vedere [la gestione del traffico di rete di Office 365](routing-with-expressroute.md).
  
Questo è un collegamento breve che è possibile utilizzare il ritorno:[https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Vedere anche

[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
