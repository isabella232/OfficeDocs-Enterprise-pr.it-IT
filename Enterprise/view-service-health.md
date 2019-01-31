---
title: Come verificare l'integrità dei servizi di Office 365
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
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651189"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="11c72-103">Come verificare l'integrità dei servizi di Office 365</span><span class="sxs-lookup"><span data-stu-id="11c72-103">How to check Office 365 service health</span></span>

<span data-ttu-id="11c72-p101">È possibile visualizzare l'integrità di Office 365, Yammer, Microsoft Dynamics CRM e servizi cloud Microsoft Intune nella pagina interfaccia di amministrazione di Office 365 **dell'integrità del servizio** . Se si riscontrano problemi con un servizio cloud, è possibile controllare l'integrità dei servizi per determinare se si tratta di un problema noto con una risoluzione in corso prima di chiamare il supporto o dedicare tempo di risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="11c72-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="11c72-106">Se non è possibile accedere al portale del servizio, è possibile utilizzare la [pagina stato del servizio](https://status.office365.com) per controllare i problemi noti che impediscono l'accesso al tenant.</span><span class="sxs-lookup"><span data-stu-id="11c72-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="11c72-107">Come verificare l'integrità dei servizi</span><span class="sxs-lookup"><span data-stu-id="11c72-107">How to check service health</span></span>

1. <span data-ttu-id="11c72-108">Passare a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e accedere con un account di amministratore.</span><span class="sxs-lookup"><span data-stu-id="11c72-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="11c72-p102">Gli utenti a cui è assegnato il ruolo di amministratore globale o amministratore del servizio possono visualizzare le informazioni sull'integrità dei servizi. Per consentire agli amministratori di Exchange, SharePoint e Skype for Business di visualizzare tali informazioni, è necessario assegnare anche a loro il ruolo di amministratore del servizio.</span><span class="sxs-lookup"><span data-stu-id="11c72-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="11c72-p103">Per aprire l'integrità dei servizi, nell'interfaccia di amministrazione, passare a **integrità** > **integrità dei servizi**, oppure fare clic sulla **scheda dello stato del servizio** nel **dashboard di Home**. Nella scheda dashboard indica se esiste un problema di servizio active e collegamenti alla pagina dello stato dettagliato service.</span><span class="sxs-lookup"><span data-stu-id="11c72-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="11c72-114">Lo stato di integrità di ogni servizio cloud viene visualizzato in formato tabulare ed è contraddistinto da un'icona che ne indica i possibili stati.</span><span class="sxs-lookup"><span data-stu-id="11c72-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="11c72-115">È anche possibile usare l'[app Amministrazione di Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) in un dispositivo mobile per visualizzare Integrità del servizio, uno strumento ideale per tenersi aggiornati con le notifiche push.</span><span class="sxs-lookup"><span data-stu-id="11c72-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="11c72-116">Visualizzare i dettagli delle informazioni pubblicate sull'integrità dei servizi</span><span class="sxs-lookup"><span data-stu-id="11c72-116">View details of posted service health</span></span>

<span data-ttu-id="11c72-p104">Nella visualizzazione predefinita, vengono visualizzati tutti i servizi e il relativo stato di integrità corrente. Per filtrare la visualizzazione a causa di un evento imprevisto services, selezionare **risolte** barra relativa a sinistra. Selezionare **gli avvisi** verranno visualizzati solo i servizi che attualmente presentano facoltativa registrato. Dalla visualizzazione **tutti i servizi** , fare clic sullo stato del servizio visualizzato verrà aperto una visualizzazione Riepilogo del bollettino o evento imprevisto.</span><span class="sxs-lookup"><span data-stu-id="11c72-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="11c72-122">Il riepilogo dell'avviso o dell'evento imprevisto include le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="11c72-122">The advisory or incident summary provides the following information:</span></span> 
  
![Cattura di schermata etichette campi bollettino un servizio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="11c72-124">Un identificativo del problema e una frase riepilogativa del problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="11c72-p105">Lo stato corrente. Per una spiegazione dei possibili stati, vedere le definizioni di stato in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="11c72-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="11c72-127">Una descrizione del possibile impatto del problema sugli utenti.</span><span class="sxs-lookup"><span data-stu-id="11c72-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="11c72-p106">L'ora in cui è stato riscontrato inizialmente il problema e l'ora dell'ultimo aggiornamento del messaggio sull'integrità dei servizi. Finché il problema non viene risolto, vengono spesso pubblicati messaggi per informare l'utente sullo stato di risoluzione del problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="11c72-130">Selezionare il collegamento **Mostra dettagli** per visualizzare maggiori dettagli sul problema, inclusa la cronologia di tutti i messaggi pubblicati durante le fasi di risoluzione del problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="11c72-131">Tradurre le informazioni sull'integrità dei servizi</span><span class="sxs-lookup"><span data-stu-id="11c72-131">Translate service health details</span></span>

<span data-ttu-id="11c72-p107">Le spiegazioni sull'integrità dei servizi vengono pubblicate in tempo reale, di conseguenza non vengono tradotte automaticamente nelle varie lingue e i dettagli di un evento del servizio sono disponibili solo in inglese. Per tradurre la spiegazione, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="11c72-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="11c72-134">Passare a [Translator](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="11c72-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="11c72-p108">Nella pagina **Integrità dei servizi** selezionare un evento imprevisto o un avviso. In **Mostra dettagli** copiare il testo relativo al problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="11c72-137">In Translator incollare il testo e quindi scegliere **Traduci**.</span><span class="sxs-lookup"><span data-stu-id="11c72-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="11c72-138">Definizioni</span><span class="sxs-lookup"><span data-stu-id="11c72-138">Definitions</span></span>

<span data-ttu-id="11c72-p109">La maggior parte dei servizi è visualizzata come integra senza ulteriori informazioni. Un problema che si verificato in un servizio viene identificato come avviso o evento imprevisto ed è contraddistinto dallo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="11c72-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="11c72-p110">Nelle informazioni sull'integrità dei servizi non vengono visualizzati gli eventi di manutenzione pianificata. Per tenere traccia degli eventi di manutenzione pianificata, è possibile consultare le informazioni aggiornate del **Centro messaggi**. Filtrare in base ai messaggi classificati come pianificati per la modifica per scoprire quando avrà luogo la modifica, quale sarà il suo effetto e come prepararsi. Per maggiori dettagli, vedere [Centro messaggi in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093).</span><span class="sxs-lookup"><span data-stu-id="11c72-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="11c72-145">Eventi imprevisti e avvisi</span><span class="sxs-lookup"><span data-stu-id="11c72-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="11c72-p111">Se per un servizio è visualizzato un avviso, si tratta di un problema noto che interessa alcuni utenti, ma il servizio è ancora disponibile. In un avviso è spesso inclusa una soluzione alternativa del problema. Il problema potrebbe inoltre essere intermittente o limitato in termini di ambito e impatto sugli utenti.</span><span class="sxs-lookup"><span data-stu-id="11c72-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="11c72-p112">Se per un servizio è visualizzato un incidente attivo, si tratta di un problema critico, di conseguenza il servizio o una funzione principale del servizio risulta non disponibile. Gli utenti potrebbero, ad esempio, non riuscire a inviare e ricevere posta elettronica o a eseguire l'accesso. Gli incidenti avranno un notevole impatto sugli utenti. Quando è in corso un incidente, nel dashboard per l'integrità dei servizi vengono fornite informazioni aggiornate sullo stato dell'analisi del problema, le operazioni eseguite per contenerlo e la conferma della risoluzione.</span><span class="sxs-lookup"><span data-stu-id="11c72-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="11c72-154">Definizioni degli stati</span><span class="sxs-lookup"><span data-stu-id="11c72-154">Status definitions</span></span>

|<span data-ttu-id="11c72-155">**Stato**</span><span class="sxs-lookup"><span data-stu-id="11c72-155">**Status**</span></span>|<span data-ttu-id="11c72-156">**Definizione**</span><span class="sxs-lookup"><span data-stu-id="11c72-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="11c72-157">**In analisi**</span><span class="sxs-lookup"><span data-stu-id="11c72-157">**Investigating**</span></span> | <span data-ttu-id="11c72-158">Si tratta di un potenziale problema noto per il quale il team Microsoft sta raccogliendo ulteriori informazioni sul comportamento e sulla portata dell'impatto.</span><span class="sxs-lookup"><span data-stu-id="11c72-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="11c72-159">**Riduzione del servizio**</span><span class="sxs-lookup"><span data-stu-id="11c72-159">**Service degradation**</span></span> | <span data-ttu-id="11c72-p113">È stato confermato che si tratta di un problema che potrebbe influire sull'uso di un servizio o di una funzionalità. Questo stato potrebbe essere visualizzato se, ad esempio, si verificano rallentamenti in un servizio, ci sono interruzioni intermittenti oppure se una funzionalità non funziona.</span><span class="sxs-lookup"><span data-stu-id="11c72-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="11c72-162">**Interruzione del servizio**</span><span class="sxs-lookup"><span data-stu-id="11c72-162">**Service interruption**</span></span> | <span data-ttu-id="11c72-p114">Questo stato viene visualizzato se è stato stabilito che un problema non consente agli utenti di accedere al servizio. In questo caso, il problema è importante e può essere riprodotto più volte.</span><span class="sxs-lookup"><span data-stu-id="11c72-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="11c72-165">**Ripristino del servizio in corso**</span><span class="sxs-lookup"><span data-stu-id="11c72-165">**Restoring service**</span></span> | <span data-ttu-id="11c72-166">La causa del problema è stata identificata, l'azione correttiva è nota e il servizio verrà ripristinato a breve.</span><span class="sxs-lookup"><span data-stu-id="11c72-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="11c72-167">**Ripristino esteso**</span><span class="sxs-lookup"><span data-stu-id="11c72-167">**Extended recovery**</span></span> | <span data-ttu-id="11c72-p115">Questo stato indica che è in corso un'azione correttiva per ripristinare il servizio per la maggior parte degli utenti, ma il ripristino di tutti i sistemi interessati potrebbe richiedere più tempo. Questo stato viene visualizzato anche se è stata applicata una soluzione temporanea per limitare l'impatto in attesa di una correzione permanente.</span><span class="sxs-lookup"><span data-stu-id="11c72-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="11c72-170">**Analisi sospesa**</span><span class="sxs-lookup"><span data-stu-id="11c72-170">**Investigation suspended**</span></span> | <span data-ttu-id="11c72-p116">Questo stato viene visualizzato se, in seguito all'analisi dettagliata di un potenziale problema, il team di supporto deve richiedere maggiori informazioni ai clienti. In tal caso, il team comunicherà all'utente quali dati e log sono necessari.</span><span class="sxs-lookup"><span data-stu-id="11c72-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="11c72-173">**Servizio ripristinato**</span><span class="sxs-lookup"><span data-stu-id="11c72-173">**Service restored**</span></span> | <span data-ttu-id="11c72-p117">È stato verificato che l'azione correttiva ha consentito di risolvere il problema sottostante e il servizio è stato ripristinato. Per scoprire la causa dell'errore, visualizzare i dettagli del problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="11c72-176">**Post-incidente report pubblicati**</span><span class="sxs-lookup"><span data-stu-id="11c72-176">**Post-incident report published**</span></span> | <span data-ttu-id="11c72-177">È stato pubblicato un rapporto operazioni non consentite Post per un problema specifico che include informazioni sulla causa principale e passaggi successivi per garantire che un problema analogo non si ripresenta.</span><span class="sxs-lookup"><span data-stu-id="11c72-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="11c72-178">Cronologia</span><span class="sxs-lookup"><span data-stu-id="11c72-178">History</span></span>

<span data-ttu-id="11c72-p118">Integrità dei servizi consente di controllare lo stato di integrità corrente e di visualizzare la cronologia di tutti gli eventi imprevisti e gli avvisi relativi ai servizi riscontrati negli ultimi 30 giorni. Per visualizzare le informazioni passate sull'integrità di tutti i servizi, selezionare **Visualizza cronologia** nella pagina **Integrità dei servizi**.</span><span class="sxs-lookup"><span data-stu-id="11c72-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="11c72-182">Viene visualizzato un elenco di tutti i messaggi di integrità dei servizi pubblicati nell'intervallo di tempo selezionato, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="11c72-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="11c72-p119">È possibile visualizzare la cronologia di integrità per l'ultimi 7 giorni o ultimi 30 giorni. Selezionare qualsiasi riga per visualizzare ulteriori dettagli su tale problema.</span><span class="sxs-lookup"><span data-stu-id="11c72-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="11c72-186">Per ulteriori informazioni sull'impegno per il tempo di attività, vedere [operations trasparente da Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="11c72-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="11c72-187">Feedback</span><span class="sxs-lookup"><span data-stu-id="11c72-187">Leave feedback</span></span>

<span data-ttu-id="11c72-p120">Obiettivo di Microsoft è garantire che le informazioni fornite agli utenti su un problema riscontrato siano accurate, tempestive e utili. Per comunicare a Microsoft il proprio gradimento, è possibile inviare una valutazione. Oltre ad assegnare un punteggio da 1 a 5 stelle, è possibile fornire feedback su aspetti specifici. Il feedback inviato verrà usato da Microsoft per ottimizzare il sistema di integrità dei servizi.</span><span class="sxs-lookup"><span data-stu-id="11c72-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="11c72-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="11c72-193">See also</span></span>

[<span data-ttu-id="11c72-194">Report attività nell'interfaccia di amministrazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="11c72-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

