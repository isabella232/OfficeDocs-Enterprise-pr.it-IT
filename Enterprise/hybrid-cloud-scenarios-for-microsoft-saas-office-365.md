---
title: Scenari per il cloud ibrido per SaaS Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "Sintesi: Comprendere l'architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365."
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123413"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="89f2f-103">Scenari per il cloud ibrido per SaaS Microsoft (Office 365)</span><span class="sxs-lookup"><span data-stu-id="89f2f-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="89f2f-104">**Sintesi:** Comprendere l'architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="89f2f-105">Combina le distribuzioni locali di Exchange, SharePoint o Skype for Business con le rispettive controparti in Office 365 come parte di una migrazione cloud o di una strategia di integrazione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="89f2f-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="89f2f-106">Architettura per scenario ibrido in SaaS Microsoft</span><span class="sxs-lookup"><span data-stu-id="89f2f-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="89f2f-107">La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su SaaS in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="89f2f-108">**Figura 1: scenari ibridi Microsoft basati su SaaS per Office 365**</span><span class="sxs-lookup"><span data-stu-id="89f2f-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Scenari ibridi Microsoft basati su SaaS per Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="89f2f-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="89f2f-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="89f2f-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="89f2f-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="89f2f-112">Esiste una serie di scenari ibridi basati su SaaS, che si allineano ai prodotti server Office e alle rispettive controparti in Office 365:</span><span class="sxs-lookup"><span data-stu-id="89f2f-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="89f2f-113">Exchange Server combinato con Exchange Online (Exchange Server ibrido)</span><span class="sxs-lookup"><span data-stu-id="89f2f-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="89f2f-114">Skype for Business Server combinato con Skype for Business Online e i nuovi scenari con Cloud PBX e la versione del connettore cloud</span><span class="sxs-lookup"><span data-stu-id="89f2f-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="89f2f-115">SharePoint Server 2019, 2016 Server SharePoint o SharePoint Server 2013 combinato con SharePoint Online (in diverse situazioni)</span><span class="sxs-lookup"><span data-stu-id="89f2f-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="89f2f-116">Esiste anche Exchange Online con Skype for Business Server locale, uno scenario ibrido di prodotto incrociato.</span><span class="sxs-lookup"><span data-stu-id="89f2f-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="89f2f-117">Identità</span><span class="sxs-lookup"><span data-stu-id="89f2f-117">Identity</span></span>
    
    <span data-ttu-id="89f2f-p101">Può includere la sincronizzazione della directory con Windows Server AD locale. In alternativa, è possibile configurare Azure AD in modo da attuare federazione con provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="89f2f-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="89f2f-120">Rete</span><span class="sxs-lookup"><span data-stu-id="89f2f-120">Network</span></span>
    
    <span data-ttu-id="89f2f-121">È costituito dalla pipe Internet esistente o da una connessione ExpressRoute con il peering Microsoft per Office 365 o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="89f2f-122">Locale</span><span class="sxs-lookup"><span data-stu-id="89f2f-122">On-premises</span></span>
    
    <span data-ttu-id="89f2f-p102">Può essere costituito da server esistenti di Exchange, SharePoint e Skype for Business, che devono essere aggiornati alle versioni più recenti. È quindi possibile combinarli con le rispettive controparti in Office 365 per gli scenari ibridi.</span><span class="sxs-lookup"><span data-stu-id="89f2f-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="89f2f-125">Configurare il proprio ambiente di sviluppo e di testing di Office 365, vedere [Guide dei laboratori di testing di Office 365](cloud-adoption-test-lab-guides-tlgs.md).</span><span class="sxs-lookup"><span data-stu-id="89f2f-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="89f2f-126">Versione ibrida di Skype for Business</span><span class="sxs-lookup"><span data-stu-id="89f2f-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="89f2f-p103">Skype per l'ambiente ibrido Business consente di combinare una distribuzione locale esistente con Skype Business online. Alcuni utenti sono ospitati in locale e alcuni utenti ospitati in linea, ma gli utenti condividono lo stesso dominio protocollo SIP (Session Initiation), ad esempio contoso.com. È possibile utilizzare questa configurazione ibrida per eseguire la migrazione da locale a Office 365 nel tempo, al calendario. Skype per le aziende può inoltre essere integrata con [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span><span class="sxs-lookup"><span data-stu-id="89f2f-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="89f2f-131">**Figura 2: Skype per la configurazione ibrida Business**</span><span class="sxs-lookup"><span data-stu-id="89f2f-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Skype per la configurazione ibrida Business](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="89f2f-133">Nella figura 2 viene Skype per la configurazione ibrida Business, costituito da un Skype locale per pool front end di Business ed edge server per comunicare con Skype Business online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="89f2f-134">Per ulteriori informazioni, vedere [pianificare la connettività ibrida tra Skype per Business Server e Skype Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="89f2f-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="89f2f-135">Cloud PBX con Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="89f2f-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="89f2f-136">Cloud PBX con Skype per Business Server, è possibile effettuare la transizione di un Skype esistente per la distribuzione locale Business Server in una topologia con connettività PSTN Public Switched Telephone Network () locale.</span><span class="sxs-lookup"><span data-stu-id="89f2f-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="89f2f-137">**Figura 3: cloud PBX con Skype for Business Server**</span><span class="sxs-lookup"><span data-stu-id="89f2f-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud PBX con Skype for Business Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="89f2f-139">Nella figura 3 viene mostrata la configurazione di Cloud PBX con Skype for Business Server, che comprende un gateway PBX o Telco locale, uno Skype for Business Server e il PSTN connesso al Cloud PBX di Microsoft in Office 365, che include Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="89f2f-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="89f2f-140">Gli utenti nell'organizzazione ospitati nel cloud possono ricevere servizi PBX (Private Branch eXchange) dal cloud Microsoft che includono segnalazione e segreteria telefonica; tuttavia, la connettività PSTN (segnale di linea) viene fornita mediante VoIP aziendale dalla distribuzione di Skype for Business Server locale.</span><span class="sxs-lookup"><span data-stu-id="89f2f-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="89f2f-p104">Si tratta di un ottimo esempio una configurazione ibrida che consente di eseguire gradualmente la migrazione a un servizio basato su cloud. È possibile mantenere funzionalità vocali degli utenti quando si inizia a spostarli Skype Business online. È possibile spostare gli utenti al proprio ritmo sapere che le funzionalità vocali continuerà no materia cui sono ospitati.</span><span class="sxs-lookup"><span data-stu-id="89f2f-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="89f2f-144">Per ulteriori informazioni, vedere [pianificare la connettività ibrida tra Skype per Business Server e Skype Business online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span><span class="sxs-lookup"><span data-stu-id="89f2f-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="89f2f-145">Se non disponi già di una distribuzione di Lync Server o Skype for Business Server esistente, puoi usare la versione del connettore cloud di Skype for Business, un set di macchine virtuali in pacchetto che implementano la connettività PSTN locale con Cloud PBX.</span><span class="sxs-lookup"><span data-stu-id="89f2f-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="89f2f-146">Per ulteriori informazioni, vedere [Piano per Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span><span class="sxs-lookup"><span data-stu-id="89f2f-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="89f2f-147">Ambiente ibrido di SharePoint</span><span class="sxs-lookup"><span data-stu-id="89f2f-147">SharePoint Hybrid</span></span>

<span data-ttu-id="89f2f-148">SharePoint ibrido combina SharePoint Online in Office 365 con la farm di SharePoint locale per un'esperienza ottimale che consenta di usufruire del meglio di entrambi i mondi.</span><span class="sxs-lookup"><span data-stu-id="89f2f-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="89f2f-149">**Figura 4: configurazione ibrida di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="89f2f-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![configurazione ibrida di SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="89f2f-151">Nella figura 4 viene mostrata la configurazione ibrida di SharePoint, che comprende una farm di SharePoint locale che comunica con SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="89f2f-152">Scenari ibridi di SharePoint:</span><span class="sxs-lookup"><span data-stu-id="89f2f-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="89f2f-153">Versione ibrida di OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="89f2f-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="89f2f-154">Soluzione Extranet B2B ibrida</span><span class="sxs-lookup"><span data-stu-id="89f2f-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="89f2f-155">Ricerca ibrida</span><span class="sxs-lookup"><span data-stu-id="89f2f-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="89f2f-156">Profili ibridi</span><span class="sxs-lookup"><span data-stu-id="89f2f-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="89f2f-157">Selezione ibrida</span><span class="sxs-lookup"><span data-stu-id="89f2f-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="89f2f-158">È facile abilitare gli scenari ibridi con le procedure guidate che rendono automatica la configurazione ibrida, disponibili dall'interfaccia di amministrazione di SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="89f2f-159">Icona di avvio delle app estendibile ibrida</span><span class="sxs-lookup"><span data-stu-id="89f2f-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="89f2f-160">Consente agli utenti di visualizzare e usare i video in Office 365 e le app e le esperienze Delve nelle pagine della relativa farm di SharePoint locale.</span><span class="sxs-lookup"><span data-stu-id="89f2f-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="89f2f-161">Tutti questi scenari ibridi di SharePoint, ad eccezione dell'icona di avvio delle app ibrida estensibile, sono disponibili per gli utenti di SharePoint 2016 e SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="89f2f-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="89f2f-162">Exchange Server 2016 ibrido</span><span class="sxs-lookup"><span data-stu-id="89f2f-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="89f2f-163">Con Exchange Server 2016 ibrido, puoi ottenere i vantaggi di Exchange Online in Office 365 per gli utenti online, mentre gli utenti locali continuano a usare l'infrastruttura di Exchange Server esistente.</span><span class="sxs-lookup"><span data-stu-id="89f2f-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="89f2f-164">**Figura 5: configurazione ibrida di Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="89f2f-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Configurazione ibrida di Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="89f2f-166">La figura 5 mostra la configurazione ibrida di Exchange 2016, formata da server Cassette postali di Exchange che comunicano con Exchange Online Protection e con le cassette postali di Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="89f2f-167">Alcuni utenti hanno un server di posta elettronica locale, altri usano Exchange Online; tuttavia, condividono tutti lo stesso spazio di indirizzi di posta elettronica. </span><span class="sxs-lookup"><span data-stu-id="89f2f-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="89f2f-168">Questa configurazione ibrida:</span><span class="sxs-lookup"><span data-stu-id="89f2f-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="89f2f-169">Sfrutta l'infrastruttura di Exchange Server esistente durante la migrazione a Exchange Online in base alle esigenze di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="89f2f-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="89f2f-170">Consente di supportare i siti remoti senza influire sull'infrastruttura per la gestione delle filiali.</span><span class="sxs-lookup"><span data-stu-id="89f2f-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="89f2f-171">Consente di instradare la posta elettronica Internet in arrivo tramite Exchange Online Protection in Office 365.</span><span class="sxs-lookup"><span data-stu-id="89f2f-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="89f2f-172">Risponde alle esigenze delle organizzazioni multinazionali con filiali per le quali è necessario che i dati siano conservati in locale.</span><span class="sxs-lookup"><span data-stu-id="89f2f-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="89f2f-173">Puoi anche integrare questa configurazione ibrida con altre applicazioni di Microsoft Office 365, tra cui Skype for Business Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="89f2f-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="89f2f-174">Per ulteriori informazioni, vedere [Distribuzioni ibride di Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).</span><span class="sxs-lookup"><span data-stu-id="89f2f-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89f2f-175">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89f2f-175">See Also</span></span>

[<span data-ttu-id="89f2f-176">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="89f2f-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="89f2f-177">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="89f2f-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

