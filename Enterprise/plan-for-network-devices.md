---
title: Pianificazione dei dispositivi di rete che si connettono ai servizi di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Riepilogo: vengono illustrate alcune considerazioni relative alla capacità della rete, agli acceleratori WAN e ai dispositivi di bilanciamento del carico utilizzati per la connessione a Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933123"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Pianificazione dei dispositivi di rete che si connettono ai servizi di Office 365

 **Riepilogo**: vengono illustrate alcune considerazioni relative alla capacità della rete, agli acceleratori WAN e ai dispositivi di bilanciamento del carico utilizzati per la connessione a Office 365.
  
Alcuni componenti hardware di rete potrebbe essere limitazioni al numero di sessioni simultanee supportate. Per le organizzazioni con più di 2.000 utenti, è consigliabile che controllano i dispositivi di rete per verificare che siano in grado di gestire il traffico di servizio aggiuntivo di Office 365. SNMP Simple Network Management Protocol () software di monitoraggio consentono di eseguire questa operazione.

||
|:-----|
| In questo articolo fa parte della [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](https://aka.ms/tune).|

Locale in uscita le impostazioni del proxy Internet anche influire sulla connettività ai servizi di Office 365 per le applicazioni client. È inoltre necessario configurare i dispositivi proxy di rete per consentire le connessioni per gli URL di servizi cloud Microsoft e le applicazioni. Ogni organizzazione è diversa. Per avere un'idea per la modalità di gestione di questo processo e la quantità di larghezza di banda in Microsoft si effettua il provisioning, [leggere il case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Skype seguenti per la Guida di Business contiene ulteriori informazioni sulle Skype per le impostazioni di Business:
  
- [Risoluzione dei problemi Skype per errori di accesso Business Online per amministratori](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [È possibile connettersi a Skype per le aziende o per alcune caratteristiche non funzionano, poiché un firewall locale blocca la connessione](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Anche se molte di queste impostazioni sono Skype per aziendali specifici, le informazioni generali sulla configurazione di rete sono utili per tutti i servizi di Office 365.
  
## <a name="determining-network-capacity"></a>Calcolo della capacità della rete

Ogni dispositivo esistente sulla rete ha un limite di capacità. Questo vale per i client e server di rete nonché per le schede, i router, i commutatori e gli hub che li interconnettono. Avere una capacità di rete adeguata significa che nessuno di questi dispositivi di rete è giunto al punto di saturazione. Monitorare l'attività di rete è essenziale per garantire che i carichi effettivi su tutti i dispositivi di rete non superino la capacità massima. La capacità della rete influenza le prestazioni del dispositivo proxy.
  
Nella maggior parte dei casi, della larghezza di banda Internet imposta il limite per la quantità di traffico. Le prestazioni debole durante le ore di punta traffico potrebbe essere dovuta a utilizzo eccessivo del collegamento Internet. Questa situazione si applica anche a filiali, branch office proxy server computer connessi al dispositivo proxy in sede della succursale su collegamenti lenti rete WAN (Wide Area).
  
Per testare la capacità di rete, monitorare l'attività di rete nell'interfaccia di rete proxy. Se è superiore al 75% della larghezza di banda massima di un'interfaccia di rete, è consigliabile aumentare la larghezza di banda dell'infrastruttura di rete che non è sufficiente. In alternativa, è consigliabile utilizzare funzionalità avanzate, ad esempio la compressione HTTP.
  
## <a name="wan-accelerators"></a>Acceleratori WAN

Se l'organizzazione utilizza accessori proxy accelerazione di rete WAN WAN, possono verificarsi problemi quando per accedere ai servizi di Office 365. Potrebbe essere necessario ottimizzare la rete o dispositivi per assicurarsi che gli utenti abbiano un'esperienza coerente quando si accede a Office 365. Ad esempio servizi di Office 365 crittografare alcuni contenuti di Office 365 e l'intestazione TCP. Il dispositivo potrebbe non essere in grado di gestire questo tipo di traffico.
  
Leggere l'informativa supporto [sull'utilizzo di Controller di ottimizzazione della WAN o dispositivi traffico/ispezione con Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Soluzioni hardware e software per il bilanciamento del carico

Nell'organizzazione sarà necessario utilizzare un dispositivo di bilanciamento del carico hardware (HLB) o una soluzione di bilanciamento del carico (Network Load Balancing, NLB) per distribuire le richieste ai server Active Directory Federation Services (AD FS) e/o ai server ibridi di Exchange. I dispositivi di bilanciamento del carico controllano il traffico di rete verso i server locali. Tali server sono fondamentali per garantire la disponibilità di Single Sign-On e delle distribuzioni ibride di Exchange.
  
Offriamo una soluzione di bilanciamento carico di rete basato su software integrata in Windows Server. Office 365 supporta questa soluzione per raggiungere il bilanciamento del carico.
  
## <a name="firewalls-and-proxies"></a>Firewall e proxy

Per ulteriori informazioni sulla configurazione dei firewall e i proxy per la connessione a Office 365, leggere [gli endpoint di gestione di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [la connettività di rete per Office 365](network-connectivity.md)e [gli endpoint di Office 365 domande frequenti](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) per ulteriori informazioni sui dispositivi e selezione a commutazione di circuito.
  
## <a name="see-also"></a>Vedere anche

[Assistenti distribuzione per i servizi di Office 365](deployment-advisors-for-office-365.md)
