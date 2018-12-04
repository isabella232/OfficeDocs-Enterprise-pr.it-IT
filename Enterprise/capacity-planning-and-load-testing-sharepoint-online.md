---
title: Capacità di pianificazione test di carico e SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: In questo articolo viene descritto come distribuire in SharePoint Online senza eseguire il test di carico tradizionale poiché non è consentito.
ms.openlocfilehash: 490d05598c42cd5d94f61dd21ee5a11701d4b4a7
ms.sourcegitcommit: 033156d46ac0fb5f05d2b1a594d5ef368b93b893
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2018
ms.locfileid: "27134671"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="0b55b-103">Capacità di pianificazione test di carico e SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="0b55b-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="0b55b-104">In questo articolo viene descritto come distribuire in SharePoint Online senza eseguire il test di carico tradizionale poiché è sconsigliata.</span><span class="sxs-lookup"><span data-stu-id="0b55b-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is strongly discouraged.</span></span>
  
<span data-ttu-id="0b55b-105">Anche se active load test su SharePoint Online è sconsigliata, esistono altri modi che è possibile verificare che un sito non genererà un'esperienza utente scadente quando si avvia il sito.</span><span class="sxs-lookup"><span data-stu-id="0b55b-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="0b55b-p101">Con SharePoint Online non è necessario eseguire la pianificazione della capacità, come questa operazione viene eseguita automaticamente come parte di questo servizio. Con ambienti locali, il test di carico consente di convalidare i presupposti scala e infine individuare il punto di interruzione di una farm. per la saturazione a carico. Con SharePoint Online è necessario eseguire operazioni in modo diverso. Da un ambiente multi-tenant, è necessario proteggere tenant tutti nella stessa farm in modo che si verranno automaticamente limitare i test di carico. In questo modo si riceverà deludente e potenzialmente fuorvianti risultati se si tenta di caricare l'ambiente di testing.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="0b55b-p102">Uno dei principali vantaggi di SharePoint Online in una distribuzione locale è la flessibilità della cloud. Ambiente su larga scala è configurato per servizio milioni di utenti a intervalli giornalieri pertanto importante è gestire in modo efficace della capacità, espandendo automaticamente le farm come e quando necessario. In questo articolo viene illustrato come si prevede di aumento di capacità e la scala con sul posto. L'articolo vengono inoltre illustrate approcci per l'utilizzo che non coinvolgono il test di carico.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="0b55b-115">Modalità di Office 365 stima del carico e si espande la capacità</span><span class="sxs-lookup"><span data-stu-id="0b55b-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="0b55b-116">SharePoint Online lavoro gestione della capacità del server viene eseguita utilizzando due metodi:</span><span class="sxs-lookup"><span data-stu-id="0b55b-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="0b55b-117">Previsione della capacità</span><span class="sxs-lookup"><span data-stu-id="0b55b-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="0b55b-118">Bilanciamento del carico nelle farm di server singolo</span><span class="sxs-lookup"><span data-stu-id="0b55b-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="0b55b-p103">A differenza di pianificazione per un ambiente locale, per la previsione della capacità in SharePoint Online, è in grado di compilare le statistiche e grafico potenziali requisiti di qualsiasi gruppo di server specificato. Potrebbe essere simile le richieste di domanda di aggregazione nell'area (in un'area è un gruppo di farm di SharePoint) linea crescita nell'immagine riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="0b55b-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Grafico della capacità predittiva: previsione](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="0b55b-p104">Mentre si trova in una farm di qualsiasi imprevisto la crescita, la somma aggregata delle richieste in un'area è prevedibile. Identificare le tendenze di crescita in SharePoint Online, è possibile pianificare l'espansione futura.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="0b55b-p105">Per poter utilizzare la capacità in modo efficiente e in relazione ai fattori di crescita imprevisti, qualsiasi farm, si dispone di automazione che tiene traccia del carico front-end e garantisce la scalabilità verticale sul posto, quando necessario. La metrica principale che viene utilizzato come un segnale per implementare la scalabilità di front end server è il carico della CPU. L'obiettivo è mantenere il carico della CPU di picco in 40%. Si tratta per avere sufficiente buffer di assorbire picchi imprevisti. Come carico approcci 40% stabile, si aggiungere server front-end alla farm.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Grafico della capacità predittiva: gestione delle farm](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="0b55b-130">Ulteriori server è possibile aggiungere rapidamente a una farm con quelli che sono stati aggiunti in precedenza all'area tramite l'utilizzo di previsione.</span><span class="sxs-lookup"><span data-stu-id="0b55b-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="0b55b-131">Come pianificare avvia un sito?</span><span class="sxs-lookup"><span data-stu-id="0b55b-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="0b55b-p106">È necessario attendere che la farm in cui viene aperto il nuovo sito verrà automaticamente monitorata in modo che vengano aggiunti nuovi server front-end, come descritto in precedenza. Per questo motivo, non è necessario alcuna notifica per il lancio del nuovo sito.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="0b55b-134">In seguito altre procedure consigliate per una singola pagina di SharePoint Online è improbabile che avvia un sito nuovo in anche 100.000 utenti avrà effetto alla farm.</span><span class="sxs-lookup"><span data-stu-id="0b55b-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="0b55b-p107">Esistono alcune strategie per la pianificazione per una versione di un nuovo sito di SharePoint Online. Come illustrato nella figura seguente, spesso la quantità di utenti che sono invitati è significativamente superiore a quelle che utilizzano effettivamente il sito. In questa immagine viene illustrata una strategia su come distribuire una versione precedente. Questo metodo non solo utile durante il caricamento delle prestazioni, ma consente inoltre di identificare informazioni su come migliorare il sito di SharePoint prima di grandi dimensioni dalla maggior parte degli utenti vederla.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Grafico degli utenti invitati e attivi](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="0b55b-p108">Nella fase pilota, è consigliabile ottenere commenti e suggerimenti degli utenti che l'organizzazione considera attendibile e SA will essere impegnati. In questo modo è possibile misurare come il sistema viene utilizzato, nonché alle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="0b55b-p109">A questo punto, inizia un (in inglese) fuori a tutti gli utenti nelle onde; come ottenere commenti ed esaminare periodicamente le prestazioni. Il vantaggio di presentazione del sistema e apportare miglioramenti come sistema ottenuto utilizzo più lentamente. In questo modo di reagire all'aumento del carico come è stato implementato il sito a più utenti.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="0b55b-p110">Infine, durante i test di carico sono consentiti, i clienti possibile impostare periodica ping al servizio misura disponibilità e latenza. Si identifica una linea di base per il proprio sito. Tuttavia, queste devono essere conservate a bassa frequenza per evitare problemi descritti in precedenza di limitazione.</span><span class="sxs-lookup"><span data-stu-id="0b55b-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

