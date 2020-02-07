---
title: Supporto NAT con Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: "Riepilogo: In questo articolo vengono fornite informazioni dettagliate su come calcolare il numero approssimativo di client che è possibile utilizzare per ciascun indirizzo IP all'interno dell'organizzazione utilizzando NAT (Network Address Translation)."
ms.openlocfilehash: 6140cf664a08701e9491c241d5754d51196e3922
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844567"
---
# <a name="nat-support-with-office-365"></a>Supporto NAT con Office 365

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

In precedenza, le indicazioni suggerivano che il numero massimo di client di Exchange da utilizzare per l'indirizzo IP per la connessione a Office 365 era di circa 2.000 client per porta di rete.
  
## <a name="why-use-nat"></a>Perché utilizzare NAT?

Utilizzando NAT, migliaia di persone in una rete aziendale possono "condividere" alcuni indirizzi IP instradabili pubblicamente.
  
La maggior parte delle reti aziendali utilizza spazio degli indirizzi IP privato (RFC1918). Lo spazio degli indirizzi IP privato viene assegnato dalla Internet Assigned Numbers Authority (IANA) ed è destinato esclusivamente alle reti che non indirizzano direttamente a e da Internet globale.
  
Per offrire accesso Internet ai dispositivi nello spazio degli indirizzi IP privato, le organizzazioni utilizzano tecnologie gateway come firewall e proxy che offrono servizi di conversione degli indirizzi di rete (NAT) o di porta (PAT). Questi gateway fanno in modo che il traffico proveniente da dispositivi interni a Internet (incluso Office 365) venga visualizzato da uno o più indirizzi IP instradabili pubblicamente. Ogni connessione esterna da un dispositivo interno traduce in una diversa porta TCP di origine nell'indirizzo IP pubblico. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Perché è necessario disporre di un numero elevato di connessioni aperte contemporaneamente a Office 365?

Outlook può aprire otto o più connessioni (in situazioni in cui sono presenti componenti aggiuntivi, calendari condivisi, cassette postali e così via). Poiché vi sono un massimo di 64.000 porte disponibili su un dispositivo NAT basato su Windows, può essere presente un massimo di 8.000 utenti dietro un indirizzo IP prima che le porte siano esaurite. Si noti che se i clienti utilizzano dispositivi non basati su sistema operativo Windows per NAT, le porte totali disponibili dipendono dal dispositivo o dal software di NAT utilizzato. In questo scenario, il numero massimo di porte potrebbe essere inferiore a 64.000. La disponibilità delle porte è anche soggetta ad altri fattori, come le finestre che limitano le porte a 4.000 per il proprio utilizzo, riducendo il numero totale di porte disponibili a 60.000. possono essere presenti altre applicazioni, ad esempio Internet Explorer, che potrebbero connettersi contemporaneamente , che richiede ulteriori porte.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Calcolo del numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico con Office 365

Per determinare il numero massimo di dispositivi dietro un unico indirizzo IP pubblico, è necessario monitorare il traffico di rete per determinare i picchi di consumo delle porte per client. Inoltre, utilizzare un fattore di picco per l'utilizzo delle porte (minimo 4). 
  
 **Utilizzare la formula seguente per calcolare il numero di dispositivi supportati per ogni indirizzo IP:**
  
Numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000-porte limitate)/(picco di consumo porta + fattore di picco)
  
 **Ad esempio, se si verificano le condizioni seguenti:**
  
- **Porte limitate:** 4.000 per il sistema operativo

- **Consumi delle porte di picco:** 6 per dispositivo

- **Fattore di picco:** 4

Successivamente, il numero massimo di dispositivi supportati dietro un unico indirizzo IP pubblico = (64.000-4000)/(6 + 4) = 6.000
  
Con il rilascio di Office 365 Hosting Pack, incluso negli aggiornamenti a partire da settembre 2011 per Microsoft Office Outlook 2007 o novembre 2011 per Microsoft Outlook 2010 o un aggiornamento successivo, il numero di connessioni da Outlook (sia Office Outlook 2007 che Service Pack 2 e Outlook 2010) per Exchange possono essere di almeno 2. Sarà necessario fattorizzare i diversi sistemi operativi, i comportamenti degli utenti e così via per determinare il numero minimo e massimo di porte che la rete richiederà al massimo.
  
Se si desidera supportare più dispositivi dietro un unico indirizzo IP pubblico, seguire la procedura descritta per valutare il numero massimo di dispositivi che possono essere supportati:
  
Monitorare il traffico di rete per determinare il picco di consumo delle porte per client. È consigliabile raccogliere i dati seguenti:
  
- Da più posizioni
    
- Da più dispositivi
    
- In più momenti
    
Utilizzare la formula precedente per calcolare il numero massimo di utenti per indirizzo IP che può essere supportato nel proprio ambiente.
  
Esistono diversi metodi per distribuire carico sul client attraverso ulteriori indirizzi IP pubblici. Le strategie disponibili dipendono dalle funzionalità della soluzione gateway aziendale. La soluzione più semplice consiste nel segmentare lo spazio degli indirizzi degli utenti e "assegnare" una serie di indirizzi IP a ogni gateway. Un'altra alternativa che molti dispositivi gateway offrono è la capacità di utilizzare un pool di indirizzi IP. Il vantaggio del pool di indirizzi è che è molto più dinamico e probabilmente saranno necessari minori adattamenti man mano che la base di utenti cresce.
  
## <a name="see-also"></a>Vedere anche

[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Domande frequenti sugli endpoint di Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
