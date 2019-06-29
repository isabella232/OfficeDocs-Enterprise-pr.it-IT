---
title: Come richiedere lo spostamento dati
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 06/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: Gli attuali clienti di Office 365 dovranno inviare una richiesta prima della data di scadenza per il proprio paese, in modo che i dati del cliente dei servizi di Office 365 partecipanti vengano spostati nel nuovo geografico.
ms.openlocfilehash: 7558e65672afdb1fa91b8a958472eab00fb89d0c
ms.sourcegitcommit: aca382b615ce79c9f707f74cda6d90fbe87bb626
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "35392356"
---
# <a name="how-to-request-your-data-move"></a>Come richiedere lo spostamento dati

> [!NOTE]
> Le informazioni contenute in questa pagina sono valide solo per i clienti che avevano già inquilini di Office 365 prima che i nuovi datacenter venissero avviati in Geo. 
  
I clienti di Office 365 esistenti sono idonei a richiedere la migrazione anticipata per i dati del cliente principale dell'intera organizzazione a riposo.  
  
## <a name="when-can-i-request-a-move"></a>Quando è possibile richiedere un trasferimento?

|**Clienti con indirizzo di fatturazione in**|**Inizio del periodo di richiesta**|**Scadenza richieste**|
|:-----|:-----|:-----|
|Giappone  <br/> |2016 agosto 1  <br/> |31 ottobre 2016  <br/> |
|Australia, Nuova Zelanda, Figi  <br/> |2016 agosto 1  <br/> |31 ottobre 2016  <br/> |
|India  <br/> |2016 agosto 1  <br/> |31 ottobre 2016  <br/> |
|Canada  <br/> |2016 agosto 1  <br/> |31 ottobre 2016  <br/> |
|Regno Unito  <br/> |15 marzo 2017  <br/> |15 settembre 2017  <br/> |
|Sud Corea  <br/> |1 maggio 2017  <br/> |31 ottobre 2017  <br/> |
|Francia  <br/> |14 marzo 2018  <br/> |15 settembre 2018  <br/> |
|Emirati Arabi Uniti  <br/> |Pianificata  <br/> |Pianificata  <br/> |
|Sudafrica  <br/> |Pianificata  <br/> |Pianificata  <br/> |
   
## <a name="how-to-request-a-move"></a>Come richiedere uno spostamento

I clienti idonei vedranno una pagina nell'interfaccia di [amministrazione di Office 365](https://aka.ms/365admin), che consentirà loro di richiedere di spostare i dati di base dei clienti nella nuova area del datacenter.  
  
Per accedere alla pagina nell'interfaccia di amministrazione di Office 365, nel riquadro di spostamento a sinistra espandere **Impostazioni**e quindi fare clic su **profilo organizzazione**.
  
![Menu Impostazioni con il profilo aziendale evidenziato](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
Nella pagina **profilo organizzazione** scorrere verso il basso fino alla sezione **opzione di residenza dei dati** . 
  
![Scheda di residenza dati](media/fdb02cd0-825d-4d9e-bb35-6f806282884f.png)
  
**È possibile che questa sezione non venga visualizzata se si applica una delle opzioni seguenti**:
- Il tenant non è idoneo per il programma di spostamento.  L'eleggibilità è determinata dal paese di iscrizione del tenant.
- Tutti i dati sono già presenti nel nuovo Geo (vedere la sezione relativa alla posizione dei dati della pagina). 
  
Se nell'organizzazione sono presenti requisiti di residenza dei dati ed è necessario richiedere la migrazione anticipata, fare clic su **modifica** in alto a destra della sezione. Sul lato destro dello schermo viene visualizzata una nuova sezione in cui vengono illustrati i dettagli del programma di spostamento. Selezionare il pulsante Toggle accanto al testo che indica **Sì, l'organizzazione ha requisiti di residenza dei dati**. Fare quindi clic su **Salva**.
  
![Schermata di operazione di consenso per il datacenter](media/f97ab8d2-b0e1-49bf-9d6b-bf75f3081233.png)
  
Verrà visualizzato il testo nella sezione **opzione di residenza dei dati** cambiare per indicare che **l'organizzazione ha chiesto di spostare i dati di base dei clienti.** Nel centro messaggi verrà visualizzato anche un messaggio di conferma. Questo conferma che la richiesta di spostamento è stata eseguita correttamente. 


  
## <a name="what-happens-after-requesting-a-move"></a>Cosa succede dopo aver richiesto uno spostamento?

Dopo aver richiesto uno spostamento, si prevede di spostarla rapidamente come i vincoli operativi consentono. A causa della natura imprevedibile di molti vincoli, non è possibile condividere una data o un intervallo di tempo specifico per gli spostamenti. Dopo aver completato lo spostamento, verrà visualizzata una notifica.
  
Gli spostamenti possono richiedere fino a 24 mesi dalla data di scadenza richiesta per il completamento del paese.
  
## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft teams non supporta ancora la migrazione del contenuto dei clienti a riposo dall'interno ai data center nazionali in cui è disponibile la residenza dei dati per Microsoft teams.  Di conseguenza, solo i nuovi clienti disporranno di tutti i dati archiviati all'interno di un paese nelle nuove aree geografiche in cui Microsoft teams supporta la residenza dei dati.  Per ulteriori informazioni sulla residenza dei dati di Office 365 per la posizione dell'azienda in [cui si trovano i dati?](https://products.office.com/where-is-your-data-located)   

## <a name="optional-actions-before-you-request-a-move"></a>Azioni facoltative prima di richiedere uno spostamento

Eseguire i passaggi seguenti in base alle esigenze.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Se si utilizza un firewall basato su IP, aggiungere le regole Consenti per i nuovi indirizzi IP

È consigliabile utilizzare il filtro DNS per i firewall anziché gli indirizzi IP. Non sono necessarie nuove voci DNS.
  
Se si utilizza un firewall basato su IP per la connettività Internet, è necessario aggiungere le regole Allow per i nuovi indirizzi IP per il datacenter di destinazione Geo. Gli indirizzi IP per il nuovo datacenter GEOS oltre ai nuovi server vengono continuamente aggiunti agli [intervalli di indirizzi IP e URL di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=229631).
  
Consultare la documentazione del firewall per informazioni su come aggiungere regole di autorizzazione (note anche come whitelist).
  
Dopo aver aggiunto gli indirizzi IP, potrebbe essere necessario testare la connettività al nuovo Data Center Geo. A tale scopo, si consiglia di creare un nuovo tenant di [prova gratuito di 30 giorni](https://go.microsoft.com/fwlink/?LinkId=522463) non appena il nuovo datacenter Geo è disponibile. 
  
### <a name="test-using-a-new-tenant"></a>Verificare l'utilizzo di un nuovo tenant

Se si desidera testare la connettività prima dello spostamento, è possibile configurare un [nuovo tenant di prova gratuito di 30 giorni](https://go.microsoft.com/fwlink/?LinkId=522463) dopo che è disponibile il nuovo Data Center Geo e utilizzarlo per l'esperienza di Office 365 ospitato nel nuovo datacenter Geo. 
  
Il tenant di valutazione non può essere combinato con il tenant esistente:
  
- Gli utenti devono utilizzare un account di prova separato per il testing.
    
- Non esiste alcun modo per spostare i dati tra i tenant.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Notificare agli utenti di aggiornare le impostazioni di Exchange obsolete nei dispositivi mobili

Se gli utenti dispongono di un dispositivo mobile con il server Exchange impostato su **m.Outlook.com** o **podxxxxx.Outlook.com**, è consigliabile passare a **Outlook.office365.com**, seguendo le istruzioni riportate in [configurare un dispositivo mobile per la sincronizzazione con il tuo account](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Argomenti correlati

[Spostamento dei dati di base in un nuovo datacenter di Office 365 GEOS](moving-data-to-new-datacenter-geos.md)

[Domande frequenti sullo spostamento dati](data-move-faq.md)

[Nuovo datacenter GEOS per Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servizi di Azure in base all'area geografica](https://azure.microsoft.com/en-us/regions/)
  

