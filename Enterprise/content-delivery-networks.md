---
title: Reti per la distribuzione di contenuti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/14/2019
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
description: Utilizzare queste informazioni per conoscere le reti di distribuzione del contenuto (reti CDN) e il modo in cui Office 365 li utilizza.
ms.openlocfilehash: 50f28e8311a501d9bc5b3f2c709fa84b1633e418
ms.sourcegitcommit: e5598a1220316122b5ed206c2607092ea1eac65c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "30636097"
---
# <a name="content-delivery-networks"></a>Reti per la distribuzione di contenuti

Le informazioni contenute in questo argomento consentiranno di conoscere le reti di distribuzione del contenuto (reti CDN) e le modalità di utilizzo di Office 365.

La Guida di reti CDN consente di mantenere Office 365 veloce e affidabile per gli utenti finali. I servizi cloud come Office 365 utilizzano reti CDN per memorizzare nella cache le risorse statiche più vicino ai browser che richiedono l'accelerazione dei download e la riduzione della latenza. Le reti CDN pubbliche consentono download più rapidi di contenuto generico, ad esempio file JavaScript, icone e immagini, mentre i reti CDN privati possono fornire accesso rapido e sicuro ai contenuti degli utenti, ad esempio video e raccolte documenti di SharePoint Online.
  
 **Tornare alla** pagina [Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).
  
## <a name="what-exactly-is-a-cdn"></a>Esattamente, che cos'è esattamente una rete per la distribuzione dei contenuti?

Reti CDN vengono utilizzati dalla maggior parte dei servizi cloud aziendali. I servizi cloud come Office 365 dispongono di milioni di clienti che scaricano una combinazione di contenuto proprietario (ad esempio messaggi di posta elettronica) e di contenuto generico (ad esempio le icone) contemporaneamente. È più efficiente inserire immagini, come icone, come il più vicino possibile al computer dell'utente. Tuttavia, non è pratico per tutti i servizi cloud creare datacenter della rete CDN che archiviano questo contenuto generico in ogni area metropolitana o anche in tutti i principali hub Internet di tutto il mondo, quindi alcuni di questi reti CDN sono condivisi.
  
Le reti per la distribuzione dei contenuti possono essere di tipo privato o pubblico. Le reti CDN private sono possedute e gestite da una singola società e solo le applicazioni e i servizi di tale società possono utilizzarlo. Quelle pubbliche sono gestite da aziende che ne offrono l'utilizzo in lease ad altre aziende. A seconda della posizione in cui si trova, potrebbe essere più efficiente per Office 365 scaricare le immagini generiche per l'utente da una rete CDN che Office 365 possiede e gestisce, una rete CDN pubblica o una combinazione dei due. Indipendentemente dal tipo di rete CDN utilizzata, la procedura per recuperare i dati è la stessa.
  
1. Il client richiede i dati da Office 365.

2. Office 365 restituisce i dati direttamente al client o indirizza il client a una rete CDN.

3. Se i dati sono già memorizzati nella cache nella rete CDN, il client Scarica i dati direttamente dal percorso CDN più vicino al client su Internet.

4. Se i dati non vengono memorizzati nella cache della rete CDN, il nodo CDN richiede i dati da Office 365 e quindi memorizza nella cache i dati per un determinato periodo di tempo dopo che il client ha eseguito il download dei dati.

Il reti CDN estrae i file e le immagini dal Data Center di Office 365 più vicino e, a sua incirca, il client estrae i file e le immagini dalla rete CDN più vicina. Quando gli utenti accedono a un servizio cloud, ad esempio la lettura della posta elettronica in Outlook Web App, il browser dell'utente tenta di recuperare i file e le immagini dal Data Center di Office 365. Invece di passare il tempo e la larghezza di banda per la distribuzione dei file, Office 365 reindirizza il browser alla rete CDN. La rete CDN calcola il data center più vicino al browser dell'utente e, tramite il reindirizzamento, Scarica le immagini generiche da qui. L'utilizzo del reindirizzamento della rete per la distribuzione dei contenuti consiste in un'operazione rapida e fa risparmiare molto tempo per il download.

## <a name="how-do-cdns-make-services-work-faster"></a>In che modo le reti per la distribuzione dei contenuti velocizzano l'esecuzione dei servizi?

Il download di cose comuni come icone più e più volte può occupare la larghezza di banda della rete che può essere utilizzata per il download di contenuti personali importanti, come la posta elettronica o i documenti. Poiché Office 365 utilizza un'architettura che include reti CDN, le icone, gli script e altri contenuti generici possono essere scaricati da server più vicini ai computer client, rendendo più veloce il download. Questo significa un accesso più rapido ai contenuti personali, che sono archiviati in modo sicuro nei data center di Office 365.

## <a name="how-should-i-set-up-my-network-so-that-cdns-work-best-with-office-365"></a>Come è possibile configurare la rete in modo che reti CDN funzioni meglio con Office 365?

Se si sta pianificando la [connettività di rete a Office 365](network-connectivity.md), è utile comprendere il funzionamento di reti CDN in generale e il modo in cui il traffico di rete CDN deve essere gestito.

Quando si abilita una rete CDN per il tenant di Office 365, si inizia con l'impostazione di criteri che regolano **** le origini di contenuto (denominate Origins nel contesto di reti CDN), le classificazioni dei dati o i tipi di file che si desidera distribuire tramite la rete CDN. Gli utenti che accedono al contenuto specificato verranno reindirizzati alla posizione più vicina del file nella rete CDN. Di conseguenza, è consigliabile utilizzare le procedure consigliate descritte nella [gestione degli endpoint di Office 365](managing-office-365-endpoints.md) per garantire che la configurazione di rete consenta ai browser client di accedere direttamente all'CDN anziché instradare il traffico CDN tramite proxy centrali per evitare Introduzione a latenza non necessaria.

## <a name="is-my-data-safe"></a>I dati sono protetti?

Viene fatto tutto il possibile per proteggere i dati eseguiti dalla azienda dei clienti. I dati specifici del cliente archiviati in reti CDN vengono crittografati sia in transito che a riposo.

> [!NOTE]
> I provider della rete CDN possono avere standard di privacy e conformità che differiscono dagli impegni delineati dal centro protezione di Office 365. I dati memorizzati nella cache tramite il servizio CDN potrebbero non essere conformi ai termini di elaborazione dati di Microsoft e potrebbero essere esterni ai limiti di conformità di Office 365 Trust Center.

Per informazioni approfondite sulla privacy e la protezione dei dati per i provider di servizi di rete CDN di Office 365, visitare i seguenti elementi:  

+ Ulteriori informazioni sulla protezione dei dati e sulla privacy di Office 365 in [Microsoft Trust Center](https://www.microsoft.com/trustcenter)
+ Per ulteriori informazioni sulla privacy e la protezione dei dati di Azure, vedere il Centro sicurezza di [Azure](https://azure.microsoft.com/en-us/overview/trusted-cloud/)
+ Per ulteriori informazioni sulla privacy e la protezione dei dati di Akamai, vedere [Akamai privacy Trust Center](https://www.akamai.com/us/en/about/compliance/data-protection-at-akamai.jsp)

## <a name="how-can-i-secure-my-network-with-all-these-3rd-party-services"></a>Come è possibile proteggere la rete con tutti i servizi di terze parti?

L'utilizzo di una vasta gamma di servizi partner consente a Office 365 di scalare e soddisfare i requisiti di disponibilità, nonché di migliorare l'esperienza utente quando si utilizza Office 365. I servizi di terze parti Office 365 leverages includono entrambi gli elenchi di revoche di certificati. ad esempio crl.microsoft.com o sa.symcb.com e reti CDN; ad esempio R3.res.Outlook.com. Ogni rete CDN FQDN Office 365 utilizza un nome di dominio completo personalizzato per Office 365. Se si è inviati a un FQDN su richiesta di Office 365, è possibile garantire che il provider CDN controlli il nome di dominio completo e il contenuto sottostante in tale percorso.
  
Per i clienti che ancora desiderano separare le richieste destinate a un datacenter Microsoft o Office 365 dalle richieste destinate a terze parti, sono state scritte linee guida per la [gestione degli endpoint di office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

## <a name="is-there-a-list-of-all-the-cdns-that-office-365-uses"></a>È presente un elenco di tutti i reti CDN utilizzati da Office 365?

Le reti CDN in uso da Office 365 sono sempre soggette a modifiche e in molti casi vi sono più partner della rete CDN configurati nell'evento uno non è disponibile. Le reti CDN primarie in uso sono le seguenti:

+ [Office 365 (in particolare per il contenuto di SharePoint Online)](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)
+ [Microsoft Azure](https://azure.microsoft.com/documentation/services/cdn/)
+ [Akamai](https://www.akamai.com/us/en/cdn.jsp)

Queste soluzioni CDN hanno una portata globale che aumenta la portata del servizio a più angoli del mondo. Il contenuto memorizzato include gli script, i file e le immagini generali di Office 365. Ad esempio, quando si effettua l'accesso a portal.office.com, le immagini vengono estratte dalla rete CDN più vicina per velocizzare i tempi di caricamento delle pagine. Altri esempi includono Office 365 ProPlus per l'archiviazione dei bit di installazione su una rete CDN per velocizzare il tempo necessario per scaricare la versione più recente di Office.

Sono presenti anche contenuti proprietari archiviati in reti CDN, ad esempio i file video per il video di Office 365. Dopo aver caricato i video, i file vengono crittografati e quindi archiviati nel formato crittografato con i servizi di Azure Media. Quando il lettore video di Office 365 Recupera il video, viene prima memorizzato nella cache della rete CDN più vicina prima di essere scaricato per velocizzare la quantità di tempo necessaria per scaricare il video.

Per informazioni su come utilizzare la rete CDN di Office 365, vedere [use the office 365 Content Delivery Network with SharePoint Online](use-office-365-cdn-with-spo.md).

## <a name="is-there-a-list-of-all-the-fqdns-that-leverage-cdns"></a>È presente un elenco di tutti i nomi FQDN che sfruttano reti CDN?

L'elenco dei nomi FQDN e la modalità di utilizzo di reti CDN cambiano nel tempo, consultare la pagina degli [URL di Office 365 e degli intervalli di indirizzi IP](https://go.microsoft.com/fwlink/p/?LinkID=293744) pubblicati per essere sempre aggiornati sugli ultimi FQDN che sfruttano reti CDN.

## <a name="can-i-use-my-own-cdn-and-cache-content-on-my-local-network"></a>È possibile utilizzare la rete CDN personale e il contenuto della cache nella propria network locale?

Siamo sempre alla ricerca di nuovi modi per supportare le esigenze dei clienti e stiamo esplorando l'utilizzo delle soluzioni proxy di memorizzazione nella cache e di altre soluzioni CDN locali.

## <a name="im-using-azure-expressroute-for-office-365-does-that-change-things"></a>Sto usando Azure ExpressRoute per Office 365, che cambia le cose?

[Azure ExpressRoute per office 365](azure-expressroute.md) fornisce una connessione dedicata all'infrastruttura di Office 365 che è stata segregata dalla rete Internet pubblica. Questo significa che i client dovranno comunque connettersi tramite connessioni non ExpressRoute per connettersi a reti CDN e ad altre infrastrutture Microsoft che non sono esplicitamente incluse nell'elenco dei servizi supportati da ExpressRoute. Per ulteriori informazioni su come instradare il traffico specifico, ad esempio le richieste destinate a reti CDN, fare riferimento alla [gestione del traffico di rete di Office 365](routing-with-expressroute.md).
  
Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/o365cdns](https://aka.ms/o365cdns)
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://docs.microsoft.com/en-us/office365/enterprise/managing-office-365-endpoints)

[URL e intervalli di indirizzi IP per Office 365](https://go.microsoft.com/fwlink/p/?LinkID=293744)

[Utilizzare la rete di distribuzione dei contenuti di Office 365 con SharePoint Online](https://docs.microsoft.com/en-us/office365/enterprise/use-office-365-cdn-with-spo)

[Centro protezione Microsoft](https://www.microsoft.com/trustcenter)