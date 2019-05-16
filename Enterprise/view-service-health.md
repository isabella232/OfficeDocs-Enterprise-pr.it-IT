---
title: Come verificare l'integrità dei servizi di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Visualizzare lo stato di integrità dei servizi di Office 365 prima di contattare il supporto per verificare se è presente un'interruzione del servizio attiva
ms.openlocfilehash: 67595bddaed23222d09c0e7f6f5353b764722f83
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071222"
---
# <a name="how-to-check-office-365-service-health"></a>Come verificare l'integrità dei servizi di Office 365

È possibile visualizzare l'integrità dei servizi cloud di Office 365, Yammer, Microsoft Dynamics CRM e Microsoft Intune nella pagina integrità del **servizio** di Office 365 nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com). If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting. 

Se non si è in grado di accedere al portale del servizio, è possibile utilizzare la [pagina stato del servizio](https://status.office365.com) per verificare la disponibilità di problemi noti che impediscono l'accesso al tenant.
  
### <a name="how-to-check-service-health"></a>Come verificare l'integrità dei servizi

1. Passare a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e accedere con un account di amministratore. 
    
    > [!NOTE]
    > Gli utenti a cui è assegnato il ruolo di amministratore globale o amministratore del servizio possono visualizzare le informazioni sull'integrità dei servizi. Per consentire agli amministratori di Exchange, SharePoint e Skype for Business di visualizzare tali informazioni, è necessario assegnare anche a loro il ruolo di amministratore del servizio.
  
2. Per aprire integrità dei servizi, nell'interfaccia di amministrazione passare a integrità del**servizio** **integrità** > oppure fare clic sulla **scheda integrità del servizio** nel **dashboard principale**. La scheda del dashboard indica se è presente un problema relativo ai servizi attivi e include i collegamenti alla pagina delle informazioni dettagliate sull'integrità dei servizi.
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. Lo stato di integrità di ogni servizio cloud viene visualizzato in formato tabulare ed è contraddistinto da un'icona che ne indica i possibili stati.
    
> [!TIP]
> È anche possibile usare l'[app Amministrazione di Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) in un dispositivo mobile per visualizzare Integrità del servizio, uno strumento ideale per tenersi aggiornati con le notifiche push. 
  
### <a name="view-details-of-posted-service-health"></a>Visualizzare i dettagli delle informazioni pubblicate sull'integrità dei servizi

Nella visualizzazione predefinita vengono visualizzati tutti i servizi e le relative informazioni sullo stato di integrità corrente. Per filtrare la visualizzazione per i servizi che stanno vivendo un incidente, selezionare **incidenti** dalla barra ombreggiata a sinistra. Se si selezionano gli **avvisi** , verranno visualizzati solo i servizi a cui è attualmente inviato un avviso. Nella visualizzazione **tutti i servizi** , facendo clic sullo stato del servizio visualizzato, verrà aperta una visualizzazione di riepilogo dell'avviso o dell'evento imprevisto. 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
Il riepilogo dell'avviso o dell'evento imprevisto include le informazioni seguenti: 
  
![Schermata che etichetta i campi di un'Advisory dei servizi](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Un identificativo del problema e una frase riepilogativa del problema.
    
2. Lo stato corrente. Per una spiegazione dei possibili stati, vedere le definizioni di stato in questo articolo.
    
3. Una descrizione del possibile impatto del problema sugli utenti.
    
4. L'ora in cui è stato riscontrato inizialmente il problema e l'ora dell'ultimo aggiornamento del messaggio sull'integrità dei servizi. Finché il problema non viene risolto, vengono spesso pubblicati messaggi per informare l'utente sullo stato di risoluzione del problema.
    
5. Selezionare il collegamento **Mostra dettagli** per visualizzare maggiori dettagli sul problema, inclusa la cronologia di tutti i messaggi pubblicati durante le fasi di risoluzione del problema. 
    
### <a name="translate-service-health-details"></a>Tradurre le informazioni sull'integrità dei servizi

Le spiegazioni sull'integrità dei servizi vengono pubblicate in tempo reale, di conseguenza non vengono tradotte automaticamente nelle varie lingue e i dettagli di un evento del servizio sono disponibili solo in inglese. Per tradurre la spiegazione, seguire questa procedura:
  
1. Passare a [Translator](https://www.bing.com/translator/).
    
2. Nella pagina **Integrità dei servizi** selezionare un evento imprevisto o un avviso. In **Mostra dettagli** copiare il testo relativo al problema.
    
3. In Translator incollare il testo e quindi scegliere **Traduci**.
    
### <a name="definitions"></a>Definizioni

La maggior parte dei servizi è visualizzata come integra senza ulteriori informazioni. Un problema che si verificato in un servizio viene identificato come avviso o evento imprevisto ed è contraddistinto dallo stato corrente.
  
> [!TIP]
> Nelle informazioni sull'integrità dei servizi non vengono visualizzati gli eventi di manutenzione pianificata. Per tenere traccia degli eventi di manutenzione pianificata, è possibile consultare le informazioni aggiornate del **Centro messaggi**. Filtrare in base ai messaggi classificati come pianificati per la modifica per scoprire quando avrà luogo la modifica, quale sarà il suo effetto e come prepararsi. Per maggiori dettagli, vedere [Centro messaggi in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093). 
  
### <a name="incidents-and-advisories"></a>Eventi imprevisti e avvisi

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Se per un servizio è visualizzato un avviso, si tratta di un problema noto che interessa alcuni utenti, ma il servizio è ancora disponibile. In un avviso è spesso inclusa una soluzione alternativa del problema. Il problema potrebbe inoltre essere intermittente o limitato in termini di ambito e impatto sugli utenti.  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Se per un servizio è visualizzato un incidente attivo, si tratta di un problema critico, di conseguenza il servizio o una funzione principale del servizio risulta non disponibile. Gli utenti potrebbero, ad esempio, non riuscire a inviare e ricevere posta elettronica o a eseguire l'accesso. Gli incidenti avranno un notevole impatto sugli utenti. Quando è in corso un incidente, nel dashboard per l'integrità dei servizi vengono fornite informazioni aggiornate sullo stato dell'analisi del problema, le operazioni eseguite per contenerlo e la conferma della risoluzione.  <br/> |
   
### <a name="status-definitions"></a>Definizioni degli stati

|**Stato**|**Definizione**|
|:-----|:-----|
|**In analisi** | Si tratta di un potenziale problema noto per il quale il team Microsoft sta raccogliendo ulteriori informazioni sul comportamento e sulla portata dell'impatto. |
|**Riduzione del servizio** | È stato confermato che si tratta di un problema che potrebbe influire sull'uso di un servizio o di una funzionalità. Questo stato potrebbe essere visualizzato se, ad esempio, si verificano rallentamenti in un servizio, ci sono interruzioni intermittenti oppure se una funzionalità non funziona. |
|**Interruzione del servizio** | Questo stato viene visualizzato se è stato stabilito che un problema non consente agli utenti di accedere al servizio. In questo caso, il problema è importante e può essere riprodotto più volte. |
|**Ripristino del servizio in corso** | La causa del problema è stata identificata, l'azione correttiva è nota e il servizio verrà ripristinato a breve. |
|**Ripristino esteso** | Questo stato indica che è in corso un'azione correttiva per ripristinare il servizio per la maggior parte degli utenti, ma il ripristino di tutti i sistemi interessati potrebbe richiedere più tempo. Questo stato viene visualizzato anche se è stata applicata una soluzione temporanea per limitare l'impatto in attesa di una correzione permanente. |
|**Analisi sospesa** | Questo stato viene visualizzato se, in seguito all'analisi dettagliata di un potenziale problema, il team di supporto deve richiedere maggiori informazioni ai clienti. In tal caso, il team comunicherà all'utente quali dati e log sono necessari. |
|**Servizio ripristinato** | È stato verificato che l'azione correttiva ha consentito di risolvere il problema sottostante e il servizio è stato ripristinato. Per scoprire la causa dell'errore, visualizzare i dettagli del problema. |
|**Rapporto post-evento pubblicato** | È stato pubblicato un rapporto post-evento per un problema specifico che include informazioni sulla causa principale e i passaggi successivi per garantire che un problema simile non venga rigenerato. |
   
## <a name="history"></a>Cronologia

L'integrità del servizio consente di esaminare lo stato di integrità corrente e di visualizzare la cronologia di eventuali avvisi e incidenti di servizio che hanno avuto un impatto sul tenant negli ultimi 30 giorni. Per visualizzare le informazioni passate sull'integrità di tutti i servizi, selezionare **Visualizza cronologia** nella pagina **Integrità dei servizi**. 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Viene visualizzato un elenco di tutti i messaggi di integrità dei servizi pubblicati nell'intervallo di tempo selezionato, come illustrato di seguito:
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
È possibile visualizzare la cronologia dell'integrità relativa agli ultimi sette giorni o agli ultimi 30 giorni. Selezionare una riga per visualizzare ulteriori dettagli sul problema.
  
Per ulteriori informazioni sul nostro impegno per il tempo di attività, vedere Transparent [Operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Feedback

Obiettivo di Microsoft è garantire che le informazioni fornite agli utenti su un problema riscontrato siano accurate, tempestive e utili. Per comunicare a Microsoft il proprio gradimento, è possibile inviare una valutazione. Oltre ad assegnare un punteggio da 1 a 5 stelle, è possibile fornire feedback su aspetti specifici. Il feedback inviato verrà usato da Microsoft per ottimizzare il sistema di integrità dei servizi.
  
## <a name="see-also"></a>Vedere anche

[Report attività nell'interfaccia di amministrazione di Microsoft 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)