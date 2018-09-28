---
title: Come verificare l'integrità dei servizi Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Visualizzare lo stato di integrità dei servizi di Office 365 prima di chiamare il supporto per verificare se si verifica un'interruzione del servizio active
ms.openlocfilehash: f4bdc0f4b6faa7a3ae86580596e28e6391167340
ms.sourcegitcommit: 09985cb7894725289ef1fc8ddd90b569c285c09e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "24976566"
---
# <a name="how-to-check-office-365-service-health"></a>Come verificare l'integrità dei servizi Office 365

È possibile visualizzare l'integrità di Office 365, Yammer, Microsoft Dynamics CRM e servizi cloud Microsoft Intune nella pagina interfaccia di amministrazione di Office 365 **dell'integrità del servizio** . Se si riscontrano problemi con un servizio cloud, è possibile controllare l'integrità dei servizi per determinare se si tratta di un problema noto con una risoluzione in corso prima di chiamare il supporto o dedicare tempo di risoluzione dei problemi. 
  
### <a name="how-to-check-service-health"></a>Come verificare l'integrità dei servizi

1. Accedere a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e accedere con un account di amministratore. 
    
    > [!NOTE]
    > Persone che sono assegnate amministratore globale o il ruolo di amministratore del servizio possono visualizzare l'integrità dei servizi. Per consentire a Exchange, SharePoint e Skype per gli amministratori aziendali visualizzare l'integrità dei servizi, è necessario anche assegnare il ruolo di amministratore del servizio. 
  
2. Per aprire l'integrità dei servizi, nell'interfaccia di amministrazione, passare a **integrità** > **integrità dei servizi**, oppure fare clic sulla **scheda dello stato del servizio** nel **dashboard di Home**. Nella scheda dashboard indica se esiste un problema di servizio active e collegamenti alla pagina dello stato dettagliato service.
    
    ![Scheda di dashboard per l'integrità dei servizi](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. Lo stato di integrità di ogni servizio cloud viene visualizzato in formato tabella con un'icona per indicare i possibili stati.
    
> [!TIP]
> È inoltre possibile utilizzare l' [app di amministrazione di Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) nel dispositivo mobile per visualizzare l'integrità dei servizi, ovvero la soluzione ideale per essere sempre aggiornati con le notifiche push. 
  
### <a name="view-details-of-posted-service-health"></a>Visualizzare i dettagli di integrità del servizio registrato

Nella visualizzazione predefinita, vengono visualizzati tutti i servizi e il relativo stato di integrità corrente. Per filtrare la visualizzazione a causa di un evento imprevisto services, selezionare **risolte** barra relativa a sinistra. Selezionare **gli avvisi** verranno visualizzati solo i servizi che attualmente presentano facoltativa registrato. Dalla visualizzazione **tutti i servizi** , fare clic sullo stato del servizio visualizzato verrà aperto una visualizzazione Riepilogo del bollettino o evento imprevisto. 
  
![Visualizzazione dei problemi di integrità dei servizi](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
Il bollettino o incidente riepilogo vengono fornite le informazioni seguenti: 
  
![Cattura di schermata etichette campi bollettino un servizio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Un problema riepilogo e identificatore istruzione del problema.
    
2. Lo stato corrente. Vedere le relative descrizioni in questo articolo per una spiegazione di ogni stato possibile.
    
3. Una descrizione di come questo problema può influire su utenti.
    
4. Momento in cui il problema è stato avviato e l'ultima volta che è stato aggiornato il messaggio di integrità del servizio. Per tutta la durata di un problema è inserire messaggi frequenti per informare l'utente lo stato di avanzamento stiamo facendo nell'applicazione di una soluzione.
    
5. Fare clic sul collegamento **Mostra dettagli** per visualizzare ulteriori dettagli su questo problema, incluse la cronologia di tutti i messaggi inviati mentre si lavora in una soluzione. 
    
### <a name="translate-service-health-details"></a>Tradurre i dettagli dello stato di servizio

Poiché ogni settimana vengono postate spiegazioni dello stato del servizio in tempo reale, non vengono convertiti automaticamente alla lingua e i dettagli di un evento di servizio sono solo in inglese. Per convertire la spiegazione, procedere come segue:
  
1. Passare al [convertitore](https://www.bing.com/translator/).
    
2. Nella pagina **integrità dei servizi** selezionare un evento imprevisto o avviso. Nella casella **Mostra dettagli**, copiare il testo sul problema.
    
3. In Translator, incollare il testo e scegliere **Traduci**.
    
### <a name="definitions"></a>Definizioni

La maggior parte dei servizi in verrà visualizzato come integra senza ulteriori informazioni. Quando un servizio è verificato un problema, il problema viene identificato come facoltativa o un evento imprevisto e visualizzato lo stato corrente.
  
> [!TIP]
> La manutenzione degli eventi non vengono visualizzati in integrità dei servizi pianificata. È possibile registrare gli eventi di manutenzione pianificate per mantenere aggiornati con il **Centro di messaggi**. Applicare un filtro ai messaggi classificati come pianificare per scoprire se le modifiche verranno eseguite, degli effetti e sulla preparazione per la modifica. Per ulteriori informazioni, vedere [Centro messaggi di Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) . 
  
### <a name="incidents-and-advisories"></a>Operazioni non consentite e gli avvisi

|||
|:-----|:-----|
|![Icona informazioni per bollettino](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Se un servizio è facoltativa mostrato, siamo a conoscenza di un problema che interessa alcuni utenti, ma il servizio è ancora disponibile. In un bollettino, è spesso una soluzione del problema e il problema potrebbe essere intermittente o limitato nell'ambito e dell'impatto.  <br/> |
|![Icona punto esclamativo per operazione non consentita](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Se un servizio dispone di un evento imprevisto attivo illustrato, è un problema critico e il servizio o una funzione principale del servizio non è disponibile. Ad esempio utenti potrebbe non essere possibile inviare e ricevere posta elettronica o grado di accesso. risolte avrà un impatto significativo per gli utenti. Se esiste un problema di protezione in corso, verrà fornito aggiornamenti relativi l'indagini, sforzi di attenuazione e la conferma della soluzione nel dashboard di integrità del servizio.  <br/> |
   
### <a name="status-definitions"></a>Definizioni di stato

|**Stato**|**Definizione**|
|:-----|:-----|
|**Analisi dei** | Si sia consapevole dell'esistenza di un problema potenziale e la raccolta di ulteriori informazioni sulle novità, e l'ambito dell'impatto. |
|**Riduzione del servizio** | È stato confermato che esiste un problema che può influire sull'utilizzo di un servizio o una caratteristica. È possibile che questo stato se un servizio esegue rallentamento, sono disponibili le interruzioni intermittenti, o se una caratteristica non funziona, ad esempio. |
|**Interruzione del servizio** | Verrà visualizzato questo stato viene determinato che un problema riguarda la possibilità per gli utenti di accedere al servizio. In questo caso, il problema è importante e può essere riprodotto in modo coerente. |
|**Ripristino del servizio** | La causa del problema è stata individuata, è possibile sapere quale azione correttiva intraprendere e in fase di portare il servizio di uno stato integro. |
|**Ripristino esteso** | Questo stato indica che un'azione correttiva è in corso per ripristinare il servizio per la maggior parte degli utenti, ma può richiedere tempo per raggiungere tutti i sistemi interessati. È possibile visualizzare lo stato se è stato reso una variabile temporanea correggere per ridurre l'impatto mentre è in attesa per applicare una correzione permanente. |
|**Indagini in sospeso** | Se la ricerca condotta dettagliata di un problema potenziale dei risultati di una richiesta di informazioni aggiuntive dai clienti per consentire di eseguire un'analisi approfondita, verrà visualizzato questo stato. Se è necessario che funga, viene concesso all'utente sui dati e registri è necessario conoscere. |
|**Servizio ripristinato.** | È stato confermato che un'azione correttiva ha risolto il problema e il servizio è stato ripristinato in uno stato integro. Per individuare i quali è stato un problema, visualizzare i dettagli del problema. |
|**Post-incidente report pubblicati** | È stato pubblicato un rapporto operazioni non consentite Post per un problema specifico che include informazioni sulla causa principale e passaggi successivi per garantire che un problema analogo non si ripresenta. |
   
## <a name="history"></a>Cronologia

Integrità dei servizi consente di esaminare lo stato di integrità corrente e visualizzare la cronologia di tutti gli avvisi di servizio e risolte negli ultimi 30 giorni. Per visualizzare l'integrità di tutti i servizi precedente, selezionare **Visualizza cronologia** nella pagina **integrità dei servizi** . 
  
![Mostra il collegamento alla cronologia di integrità](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Viene visualizzato un elenco di tutti i messaggi di integrità del servizio registrato nell'intervallo di tempo selezionato, come illustrato di seguito:
  
![Visualizzare la cronologia di integrità del servizio](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
È possibile visualizzare la cronologia di integrità per l'ultimi 7 giorni o ultimi 30 giorni. Selezionare qualsiasi riga per visualizzare ulteriori dettagli su tale problema.
  
Per ulteriori informazioni sull'impegno per il tempo di attività, vedere [operations trasparente da Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Lasciare commenti e suggerimenti

L'obiettivo è quello di verificare che le informazioni che Microsoft fornisce all'utente relativa a un problema in corso siano tempestivamente, accurati e utili. Per commenti come ci si limita, selezionare una classificazione. Dopo aver concesso Usa un punteggio da 1 a 5 stelle, è possibile fornire commenti e suggerimenti su tutti i dettagli specifici. Utilizzeremo commenti e suggerimenti per ottimizzare il sistema di integrità servizi.
  
![Modulo di commenti e suggerimenti per problemi di integrità del servizio](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>Vedere anche

[Rapporti di attività nell'interfaccia di amministrazione di Office 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

