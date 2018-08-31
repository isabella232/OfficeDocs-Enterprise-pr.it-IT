---
title: Supporto di NAT con Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: "Riepilogo: In questo articolo vengono fornite informazioni dettagliate su come calcolare il numero approssimativo di client che è possibile utilizzare per ciascun indirizzo IP all'interno dell'organizzazione utilizzando NAT (Network Address Translation)."
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541100"
---
# <a name="nat-support-with-office-365"></a>Supporto di NAT con Office 365

 **Riepilogo:** In questo articolo vengono fornite informazioni dettagliate su come calcolare il numero approssimativo di client che è possibile utilizzare per ciascun indirizzo IP all'interno dell'organizzazione utilizzando NAT (Network Address Translation). 
  
Indicazioni suggerito in precedenza, che il numero massimo di client di Exchange per ogni indirizzo IP da utilizzare per connettersi a Office 365 è stata client circa 2.000 per porta di rete.
  
## <a name="why-use-nat"></a>Perché utilizzare NAT?

Tramite NAT migliaia di persone in una rete aziendale può "condividere" pochi indirizzi IP instradabili pubblicamente.
  
La maggior parte delle reti aziendali utilizza spazio degli indirizzi IP privato (RFC1918). Lo spazio degli indirizzi IP privato viene assegnato dalla Internet Assigned Numbers Authority (IANA) ed è destinato esclusivamente alle reti che non indirizzano direttamente a e da Internet globale.
  
Per fornire l'accesso a Internet per i dispositivi in uno spazio di indirizzi IP privato, le organizzazioni utilizzare tecnologie gateway come firewall e proxy che forniscono (NAT) network address translation o porta address translation (PAT) servizi. Questi gateway verificare il traffico dall'interno ai dispositivi di Internet (tra Office 365) sembrano provenire da uno o più indirizzi IP instradabili pubblicamente. Ogni connessione in uscita dal dispositivo interno viene convertita in una porta TCP origine diversa l'indirizzo IP pubblico. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Perché è necessario presenti numerose eccessivo di connessioni aperte a Office 365 contemporaneamente?

Outlook potrebbe aprire otto o più connessioni (in situazioni dove sono presenti componenti aggiuntivi, calendari condivisi, cassette postali e così via). Poiché esistono massimo 64.000 porte disponibili in un dispositivo NAT basato su Windows, possono esistere massimo 8000 utenti dietro un indirizzo IP prima che le porte si esauriscano. Tenere presente che se i clienti utilizzano dispositivi basati su sistema operativo diverso da Windows, il numero di porte disponibili dipenderà dal dispositivo NAT o dal software utilizzato. In questo scenario, il numero massimo di porte potrebbe essere inferiore a 64.000. La disponibilità delle porte è inoltre influenzata da altri fattori, come ad esempio la limitazione da parte di Windows di 4.000 porte a suo uso esclusivo, che riduce il numero totale di porte disponibili a 60.000. Potrebbero esistere altre applicazioni, come ad esempio Internet Explorer, che potrebbero connettersi contemporaneamente, richiedendo porte aggiuntive.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcolare il numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico con Office 365

Per determinare il numero massimo di dispositivi dietro un unico indirizzo IP pubblico, è necessario monitorare il traffico di rete per determinare il consumo di picco porta per ogni client. Inoltre, un fattore di picco deve essere utilizzato per l'utilizzo di porta (minimo 4). 
  
 **Per calcolare il numero di dispositivi supportati per ogni indirizzo IP, utilizzare la formula seguente:**
  
Numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000 - porte riservate) / (picco di consumo Dell porte + fattore di picco)
  
 **Se ad esempio le operazioni seguenti sono stati true:**
  
- **Porte riservate:** 4.000 per il sistema operativo 
    
- **Consumo Dell porte picco:** 6 per ogni dispositivo 
    
- **Fattore di picco:** 4 
    
Quindi, il numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000 4.000) / (6 + 4) = 6.000
  
Con la versione di Office 365 Service pack, inclusi gli aggiornamenti di settembre 2011 per Microsoft Office Outlook 2007 o novembre 2011 per Microsoft Outlook 2010 o un aggiornamento successivo, il numero di connessioni di Outlook (entrambe Office Outlook 2007 con il servizio di hosting Service Pack 2 e Outlook 2010) per Exchange può essere il minor numero 2. È necessario tenere in considerazione i sistemi operativi diversi, comportamenti degli utenti, e così via per determinare il numero minimo e massimo di porte necessarie al picco della rete.
  
Se si desidera supportare più dispositivi dietro un unico indirizzo IP pubblico, seguire i passaggi indicati per determinare il numero massimo di dispositivi supportabili:
  
Monitorare il traffico di rete per determinare consumo Dell porte punta al client. È consigliabile raccogliere questi dati:
  
- Da più posizioni
    
- Da più dispositivi
    
- In più momenti
    
Utilizzare la formula precedente per calcolare il numero massimo di utenti per indirizzo IP che può essere supportato nel proprio ambiente.
  
Esistono diversi metodi per la distribuzione di client carico tra gli indirizzi IP pubblici aggiuntivi. Strategie disponibili variano a seconda delle funzionalità della soluzione aziendale gateway. La soluzione più semplice è segmentare lo spazio degli indirizzi di utenti e assegnare in modo statico"" un numero di indirizzi IP per ogni gateway. In alternativa che offrono molti dispositivi gateway è la possibilità di utilizzare un pool di indirizzi IP. Il vantaggio del pool di indirizzi è è molto più dinamico e riduce la probabilità che richiedere la regolazione man mano che aumenta la base di utenti.
  
## <a name="see-also"></a>Vedere anche

[Gestione di endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

