---
title: Come verificare l'integrità dei servizi Office 365
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
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
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541179"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="d9f51-103">Come verificare l'integrità dei servizi Office 365</span><span class="sxs-lookup"><span data-stu-id="d9f51-103">How to check Office 365 service health</span></span>

<span data-ttu-id="d9f51-p101">È possibile visualizzare l'integrità di Office 365, Yammer, Microsoft Dynamics CRM e servizi cloud Microsoft Intune in Office 365 * * dello stato del servizio * * pagina nell'interfaccia di amministrazione. Se si riscontrano problemi con un servizio cloud, è possibile controllare l'integrità dei servizi per determinare se si tratta di un problema noto con una risoluzione in corso prima di chiamare il supporto o dedicare tempo di risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="d9f51-106">Come verificare l'integrità dei servizi</span><span class="sxs-lookup"><span data-stu-id="d9f51-106">How to check service health</span></span>

1. <span data-ttu-id="d9f51-107">Accedere a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e accedere con un account di amministratore.</span><span class="sxs-lookup"><span data-stu-id="d9f51-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="d9f51-p102">Persone che sono assegnate amministratore globale o il ruolo di amministratore del servizio possono visualizzare l'integrità dei servizi. Per consentire a Exchange, SharePoint e Skype per gli amministratori aziendali visualizzare l'integrità dei servizi, è necessario anche assegnare il ruolo di amministratore del servizio.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="d9f51-p103">Per aprire l'integrità dei servizi, nell'interfaccia di amministrazione, passare a **integrità** \> **dell'integrità del servizio**oppure fare clic sull'integrità dei servizi di schede nel dashboard di Home. Nella scheda dashboard indica se esiste un problema di servizio active e collegamenti alla pagina dello stato dettagliato service.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Scheda di dashboard per l'integrità dei servizi](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="d9f51-113">Lo stato di integrità di ogni servizio cloud viene visualizzato in formato tabella con un'icona per indicare i possibili stati.</span><span class="sxs-lookup"><span data-stu-id="d9f51-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="d9f51-114">È inoltre possibile utilizzare l' [app di amministrazione di Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) nel dispositivo mobile per visualizzare l'integrità dei servizi, ovvero la soluzione ideale per essere sempre aggiornati con le notifiche push.</span><span class="sxs-lookup"><span data-stu-id="d9f51-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="d9f51-115">Visualizzare i dettagli di integrità del servizio registrato</span><span class="sxs-lookup"><span data-stu-id="d9f51-115">View details of posted service health</span></span>

<span data-ttu-id="d9f51-p104">Nella visualizzazione predefinita, vengono visualizzati tutti i servizi e il relativo stato di integrità corrente. Per filtrare la visualizzazione a causa di un evento imprevisto services, selezionare **risolte** barra relativa a sinistra. Selezionare **gli avvisi** verranno visualizzati solo i servizi che attualmente presentano facoltativa registrato. Dalla visualizzazione **tutti i servizi** , fare clic sullo stato del servizio visualizzato verrà aperto una visualizzazione Riepilogo del bollettino o evento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Visualizzazione dei problemi di integrità dei servizi](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="d9f51-121">Il bollettino o incidente riepilogo vengono fornite le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d9f51-121">The advisory or incident summary provides the following information:</span></span> 
  
![Cattura di schermata etichette campi bollettino un servizio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="d9f51-123">Un problema riepilogo e identificatore istruzione del problema.</span><span class="sxs-lookup"><span data-stu-id="d9f51-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="d9f51-p105">Lo stato corrente. Vedere le relative descrizioni in questo articolo per una spiegazione di ogni stato possibile.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="d9f51-126">Una descrizione di come questo problema può influire su utenti.</span><span class="sxs-lookup"><span data-stu-id="d9f51-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="d9f51-p106">Momento in cui il problema è stato avviato e l'ultima volta che è stato aggiornato il messaggio di integrità del servizio. Per tutta la durata di un problema è inserire messaggi frequenti per informare l'utente lo stato di avanzamento stiamo facendo nell'applicazione di una soluzione.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="d9f51-129">Fare clic sul collegamento **Mostra dettagli** per visualizzare ulteriori dettagli su questo problema, incluse la cronologia di tutti i messaggi inviati mentre si lavora in una soluzione.</span><span class="sxs-lookup"><span data-stu-id="d9f51-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="d9f51-130">Tradurre i dettagli dello stato di servizio</span><span class="sxs-lookup"><span data-stu-id="d9f51-130">Translate service health details</span></span>

<span data-ttu-id="d9f51-p107">Poiché ogni settimana vengono postate spiegazioni dello stato del servizio in tempo reale, non vengono convertiti automaticamente alla lingua e i dettagli di un evento di servizio sono solo in inglese. Per convertire la spiegazione, procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="d9f51-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="d9f51-133">Passare al [convertitore](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="d9f51-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="d9f51-p108">Nella pagina **integrità dei servizi** selezionare un evento imprevisto o avviso. Nella casella **Mostra dettagli**, copiare il testo sul problema.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="d9f51-136">In Translator, incollare il testo e scegliere **Traduci**.</span><span class="sxs-lookup"><span data-stu-id="d9f51-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="d9f51-137">Definizioni</span><span class="sxs-lookup"><span data-stu-id="d9f51-137">Definitions</span></span>

<span data-ttu-id="d9f51-p109">La maggior parte dei servizi in verrà visualizzato come integra senza ulteriori informazioni. Quando un servizio è verificato un problema, il problema viene identificato come facoltativa o un evento imprevisto e visualizzato lo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="d9f51-p110">La manutenzione degli eventi non vengono visualizzati in integrità dei servizi pianificata. È possibile registrare gli eventi di manutenzione pianificate per mantenere aggiornati con il **Centro di messaggi**. Applicare un filtro ai messaggi classificati come pianificare per scoprire se le modifiche verranno eseguite, degli effetti e sulla preparazione per la modifica. Per ulteriori informazioni, vedere [Centro messaggi di Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .</span><span class="sxs-lookup"><span data-stu-id="d9f51-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="d9f51-144">Operazioni non consentite e gli avvisi</span><span class="sxs-lookup"><span data-stu-id="d9f51-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Icona informazioni per bollettino](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="d9f51-p111">Se un servizio è facoltativa mostrato, siamo a conoscenza di un problema che interessa alcuni utenti, ma il servizio è ancora disponibile. In un bollettino, è spesso una soluzione del problema e il problema potrebbe essere intermittente o limitato nell'ambito e dell'impatto.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Icona punto esclamativo per operazione non consentita](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="d9f51-p112">Se un servizio dispone di un evento imprevisto attivo illustrato, è un problema critico e il servizio o una funzione principale del servizio non è disponibile. Ad esempio utenti potrebbe non essere possibile inviare e ricevere posta elettronica o grado di accesso. risolte avrà un impatto significativo per gli utenti. Se esiste un problema di protezione in corso, verrà fornito aggiornamenti relativi l'indagini, sforzi di attenuazione e la conferma della soluzione nel dashboard di integrità del servizio.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="d9f51-153">Definizioni di stato</span><span class="sxs-lookup"><span data-stu-id="d9f51-153">Status definitions</span></span>

<span data-ttu-id="d9f51-154">| |</span><span class="sxs-lookup"><span data-stu-id="d9f51-154"></span></span>
|<span data-ttu-id="d9f51-155">**Stato**</span><span class="sxs-lookup"><span data-stu-id="d9f51-155">**Status**</span></span>|<span data-ttu-id="d9f51-156">**Definizione**</span><span class="sxs-lookup"><span data-stu-id="d9f51-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d9f51-157">Analisi dei</span><span class="sxs-lookup"><span data-stu-id="d9f51-157">Investigating</span></span>  <br/> |<span data-ttu-id="d9f51-158">Si sia consapevole dell'esistenza di un problema potenziale e la raccolta di ulteriori informazioni sulle novità, e l'ambito dell'impatto.</span><span class="sxs-lookup"><span data-stu-id="d9f51-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="d9f51-159">Riduzione del servizio</span><span class="sxs-lookup"><span data-stu-id="d9f51-159">Service degradation</span></span>  <br/> |<span data-ttu-id="d9f51-p113">È stato confermato che esiste un problema che può influire sull'utilizzo di un servizio o una caratteristica. È possibile che questo stato se un servizio esegue rallentamento, sono disponibili le interruzioni intermittenti, o se una caratteristica non funziona, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="d9f51-162">Interruzione del servizio</span><span class="sxs-lookup"><span data-stu-id="d9f51-162">Service interruption</span></span>  <br/> |<span data-ttu-id="d9f51-p114">Verrà visualizzato questo stato viene determinato che un problema riguarda la possibilità per gli utenti di accedere al servizio. In questo caso, il problema è importante e può essere riprodotto in modo coerente.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="d9f51-165">Ripristino del servizio</span><span class="sxs-lookup"><span data-stu-id="d9f51-165">Restoring service</span></span>  <br/> |<span data-ttu-id="d9f51-166">La causa del problema è stata individuata, è possibile sapere quale azione correttiva intraprendere e in fase di portare il servizio di uno stato integro.</span><span class="sxs-lookup"><span data-stu-id="d9f51-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="d9f51-167">Ripristino esteso</span><span class="sxs-lookup"><span data-stu-id="d9f51-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="d9f51-p115">Questo stato indica che un'azione correttiva è in corso per ripristinare il servizio per la maggior parte degli utenti, ma può richiedere tempo per raggiungere tutti i sistemi interessati. È possibile visualizzare lo stato se è stato reso una variabile temporanea correggere per ridurre l'impatto mentre è in attesa per applicare una correzione permanente.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="d9f51-170">Indagini in sospeso</span><span class="sxs-lookup"><span data-stu-id="d9f51-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="d9f51-p116">Se la ricerca condotta dettagliata di un problema potenziale dei risultati di una richiesta di informazioni aggiuntive dai clienti per consentire di eseguire un'analisi approfondita, verrà visualizzato questo stato. Se è necessario che funga, viene concesso all'utente sui dati e registri è necessario conoscere.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="d9f51-173">Servizio ripristinato.</span><span class="sxs-lookup"><span data-stu-id="d9f51-173">Service restored</span></span>  <br/> |<span data-ttu-id="d9f51-p117">È stato confermato che un'azione correttiva ha risolto il problema e il servizio è stato ripristinato in uno stato integro. Per individuare i quali è stato un problema, visualizzare i dettagli del problema.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="d9f51-176">Cronologia</span><span class="sxs-lookup"><span data-stu-id="d9f51-176">History</span></span>

<span data-ttu-id="d9f51-p118">Integrità dei servizi consente di esaminare lo stato di integrità corrente e visualizzare la cronologia di tutti gli avvisi di servizio e risolte negli ultimi 30 giorni. Per visualizzare l'integrità di tutti i servizi precedente, selezionare **Visualizza cronologia** nella pagina **integrità dei servizi** .</span><span class="sxs-lookup"><span data-stu-id="d9f51-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Mostra il collegamento alla cronologia di integrità](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="d9f51-180">Viene visualizzato un elenco di tutti i messaggi di integrità del servizio registrato nell'intervallo di tempo selezionato, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d9f51-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Visualizzare la cronologia di integrità del servizio](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="d9f51-p119">È possibile visualizzare la cronologia di integrità per l'ultimi 7 giorni o ultimi 30 giorni. Selezionare qualsiasi riga per visualizzare ulteriori dettagli su tale problema.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="d9f51-184">Per ulteriori informazioni sull'impegno per il tempo di attività, vedere [operations trasparente da Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="d9f51-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="d9f51-185">Lasciare commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="d9f51-185">Leave feedback</span></span>

<span data-ttu-id="d9f51-p120">L'obiettivo è quello di verificare che le informazioni che Microsoft fornisce all'utente relativa a un problema in corso siano tempestivamente, accurati e utili. Per commenti come ci si limita, selezionare una classificazione. Dopo aver concesso Usa un punteggio da 1 a 5 stelle, è possibile fornire commenti e suggerimenti su tutti i dettagli specifici. Utilizzeremo commenti e suggerimenti per ottimizzare il sistema di integrità servizi.</span><span class="sxs-lookup"><span data-stu-id="d9f51-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Modulo di commenti e suggerimenti per problemi di integrità del servizio](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="d9f51-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d9f51-191">See also</span></span>

[<span data-ttu-id="d9f51-192">Rapporti di attività nell'interfaccia di amministrazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="d9f51-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

