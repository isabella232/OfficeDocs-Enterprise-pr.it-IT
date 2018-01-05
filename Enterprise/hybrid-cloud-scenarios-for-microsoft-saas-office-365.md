---
title: Scenari per il cloud ibrido per SaaS Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Sintesi: Comprendere l''architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365.'
ms.openlocfilehash: 5f50573376b70ad94b3b1cd4b86ce3ef1fdc67dd
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="79950-103">Scenari per il cloud ibrido per SaaS Microsoft (Office 365)</span><span class="sxs-lookup"><span data-stu-id="79950-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="79950-104">**Sintesi:** Comprendere l'architettura ibrida e gli scenari delle offerte cloud basate sul software distribuito come servizio Microsoft (SaaS) in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="79950-105">Combina le distribuzioni locali di Exchange, SharePoint o Skype for Business con le rispettive controparti in Office 365 come parte di una migrazione cloud o di una strategia di integrazione a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="79950-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="79950-106">Architettura per scenario ibrido in SaaS Microsoft</span><span class="sxs-lookup"><span data-stu-id="79950-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="79950-107">La figura 1 mostra l'architettura di scenari ibridi Microsoft basati su SaaS in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="79950-108">**Figura 1: scenari ibridi Microsoft basati su SaaS per Office 365**</span><span class="sxs-lookup"><span data-stu-id="79950-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Scenari ibridi Microsoft basati su SaaS per Office 365](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="79950-110">Per ogni livello dell'architettura:</span><span class="sxs-lookup"><span data-stu-id="79950-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="79950-111">App e scenari</span><span class="sxs-lookup"><span data-stu-id="79950-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="79950-112">Esiste una serie di scenari ibridi basati su SaaS, che si allineano ai prodotti server Office e alle rispettive controparti in Office 365:</span><span class="sxs-lookup"><span data-stu-id="79950-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="79950-113">Exchange Server combinato con Exchange Online (Exchange Server ibrido)</span><span class="sxs-lookup"><span data-stu-id="79950-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="79950-114">Skype for Business Server combinato con Skype for Business Online e i nuovi scenari con Cloud PBX e la versione del connettore cloud</span><span class="sxs-lookup"><span data-stu-id="79950-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="79950-115">SharePoint Server 2016 o SharePoint Server 2013 combinati con SharePoint Online (scenari multipli)</span><span class="sxs-lookup"><span data-stu-id="79950-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="79950-116">Esiste anche Exchange Online con Skype for Business Server locale, uno scenario ibrido di prodotto incrociato.</span><span class="sxs-lookup"><span data-stu-id="79950-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="79950-117">Identità</span><span class="sxs-lookup"><span data-stu-id="79950-117">Identity</span></span>
    
    <span data-ttu-id="79950-p101">Può includere la sincronizzazione della directory con Windows Server AD locale. In alternativa, è possibile configurare Azure AD in modo da attuare federazione con provider di identità di terze parti.</span><span class="sxs-lookup"><span data-stu-id="79950-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="79950-120">Rete</span><span class="sxs-lookup"><span data-stu-id="79950-120">Network</span></span>
    
    <span data-ttu-id="79950-121">È costituito dalla pipe Internet esistente o da una connessione ExpressRoute con il peering Microsoft per Office 365 o Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="79950-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="79950-122">Locale</span><span class="sxs-lookup"><span data-stu-id="79950-122">On-premises</span></span>
    
    <span data-ttu-id="79950-p102">Può essere costituito da server esistenti di Exchange, SharePoint e Skype for Business, che devono essere aggiornati alle versioni più recenti. È quindi possibile combinarli con le rispettive controparti in Office 365 per gli scenari ibridi.</span><span class="sxs-lookup"><span data-stu-id="79950-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="79950-125">Impostare l'[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="79950-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="79950-126">Skype for Business 2015 ibrido</span><span class="sxs-lookup"><span data-stu-id="79950-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="79950-p103">Skype for Business 2015 ibrido consente di combinare una distribuzione locale esistente con Skype for Business Online. Alcuni utenti sono ospitati in locale e alcuni sono ospitati online; tuttavia, condividono lo stesso dominio SIP (Session Initiation Protocol), come contoso.com. Puoi usare questa configurazione ibrida per migrare dall'ambiente locale a Office 365 in base alle esigenze di pianificazione. È possibile integrare Skype for Business 2015 con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="79950-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="79950-130">**Figura 2: configurazione ibrida di Skype for Business 2015**</span><span class="sxs-lookup"><span data-stu-id="79950-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Configurazione ibrida di Skype for Business 2015](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="79950-132">Nella figura 2 viene mostrata la configurazione ibrida di Skype for Business 2015, la quale comprende il pool Front End di Skype for Business 2015 locale e il server perimetrale che comunica con Skype for Business Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="79950-133">Per ulteriori informazioni, vedere:</span><span class="sxs-lookup"><span data-stu-id="79950-133">For more information, see:</span></span>
  
- <span data-ttu-id="79950-134">[Pianificare la connettività ibrida tra Skype for Business Server e Skype for Business Online]((https://technet.microsoft.com/library/jj205403.aspx))</span><span class="sxs-lookup"><span data-stu-id="79950-134">[Plan hybrid connectivity between Skype for Business Server and Skype for Business Online]((https://technet.microsoft.com/library/jj205403.aspx))</span></span>
    
- <span data-ttu-id="79950-135">[Configurazione ibride supportate per Skype for Business Server 2015]((https://technet.microsoft.com/library/jj945633.aspx))</span><span class="sxs-lookup"><span data-stu-id="79950-135">[Supported hybrid configurations for Skype for Business Server 2015]((https://technet.microsoft.com/library/jj945633.aspx))</span></span>
    
- <span data-ttu-id="79950-136">[Versione ibrida di Skype for Business]((http://hybrid.office.com/skype-for-business/))</span><span class="sxs-lookup"><span data-stu-id="79950-136">[Skype for Business Hybrid]((http://hybrid.office.com/skype-for-business/))</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="79950-137">Cloud PBX con Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="79950-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="79950-138">Cloud PBX con Skype for Business Server consente di trasferire una distribuzione locale di Skype for Business Server esistente in una topologia con connettività PSTN (Public Switched Telephone Network). </span><span class="sxs-lookup"><span data-stu-id="79950-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="79950-139">**Figura 3: cloud PBX con Skype for Business Server**</span><span class="sxs-lookup"><span data-stu-id="79950-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Cloud PBX con Skype for Business Server](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="79950-141">Nella figura 3 viene mostrata la configurazione di Cloud PBX con Skype for Business Server, che comprende un gateway PBX o Telco locale, uno Skype for Business Server e il PSTN connesso al Cloud PBX di Microsoft in Office 365, che include Skype for Business Online.</span><span class="sxs-lookup"><span data-stu-id="79950-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="79950-142">Gli utenti nell'organizzazione ospitati nel cloud possono ricevere servizi PBX (Private Branch eXchange) dal cloud Microsoft che includono segnalazione e segreteria telefonica; tuttavia, la connettività PSTN (segnale di linea) viene fornita mediante VoIP aziendale dalla distribuzione di Skype for Business Server locale.</span><span class="sxs-lookup"><span data-stu-id="79950-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="79950-p104">È un ottimo esempio di configurazione ibrida che permette di effettuare gradualmente la migrazione a un servizio basato sul cloud. È possibile mantenere le funzionalità vocali degli utenti non appena vengono trasferiti su Skype for Business Online. È possibile trasferire gli utenti al proprio ritmo, sapendo che le funzionalità vocali saranno comunque disponibili a prescindere da dove sono ospitate.</span><span class="sxs-lookup"><span data-stu-id="79950-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="79950-146">Per ulteriori informazioni, vedere [Pianificare la connettività ibrida tra Skype for Business Server e Skype for Business Online o Lync Server 2013]((https://technet.microsoft.com/library/jj205403.aspx)).</span><span class="sxs-lookup"><span data-stu-id="79950-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013]((https://technet.microsoft.com/library/jj205403.aspx)).</span></span>
  
<span data-ttu-id="79950-147">Se non disponi già di una distribuzione di Lync Server o Skype for Business Server esistente, puoi usare la versione del connettore cloud di Skype for Business, un set di macchine virtuali in pacchetto che implementano la connettività PSTN locale con Cloud PBX.</span><span class="sxs-lookup"><span data-stu-id="79950-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="79950-148">Per ulteriori informazioni, vedere [Piano per Skype for Business Cloud Connector Edition]((https://technet.microsoft.com/library/mt605227.aspx)).</span><span class="sxs-lookup"><span data-stu-id="79950-148">For more information, see [Plan for Skype for Business Cloud Connector Edition]((https://technet.microsoft.com/library/mt605227.aspx)).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="79950-149">Ambiente ibrido di SharePoint</span><span class="sxs-lookup"><span data-stu-id="79950-149">SharePoint Hybrid</span></span>

<span data-ttu-id="79950-150">SharePoint ibrido combina SharePoint Online in Office 365 con la farm di SharePoint locale per un'esperienza ottimale che consenta di usufruire del meglio di entrambi i mondi.</span><span class="sxs-lookup"><span data-stu-id="79950-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="79950-151">**Figura 4: configurazione ibrida di SharePoint**</span><span class="sxs-lookup"><span data-stu-id="79950-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![configurazione ibrida di SharePoint](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="79950-153">Nella figura 4 viene mostrata la configurazione ibrida di SharePoint, che comprende una farm di SharePoint locale che comunica con SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="79950-154">Scenari ibridi di SharePoint:</span><span class="sxs-lookup"><span data-stu-id="79950-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="79950-155">Versione ibrida di OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="79950-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="79950-156">Versione ibrida dei siti del team</span><span class="sxs-lookup"><span data-stu-id="79950-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- <span data-ttu-id="79950-157">[Soluzione Extranet B2B ibrida]((https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037))</span><span class="sxs-lookup"><span data-stu-id="79950-157">[Hybrid Extranet B2B]((https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037))</span></span>
    
- [<span data-ttu-id="79950-158">Ricerca ibrida</span><span class="sxs-lookup"><span data-stu-id="79950-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- <span data-ttu-id="79950-159">[Profili ibridi]((https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4))</span><span class="sxs-lookup"><span data-stu-id="79950-159">[Hybrid profiles]((https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4))</span></span>
    
- <span data-ttu-id="79950-160">[Selezione ibrida]((https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c))</span><span class="sxs-lookup"><span data-stu-id="79950-160">[Hybrid Picker]((https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c))</span></span>
    
    <span data-ttu-id="79950-161">È facile abilitare gli scenari ibridi con le procedure guidate che rendono automatica la configurazione ibrida, disponibili dall'interfaccia di amministrazione di SharePoint Online in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- <span data-ttu-id="79950-162">[Icona di avvio delle app estendibile ibrida]((https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91))</span><span class="sxs-lookup"><span data-stu-id="79950-162">[Extensible hybrid app launcher]((https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91))</span></span>
    
    <span data-ttu-id="79950-163">Consente agli utenti di visualizzare e usare i video in Office 365 e le app e le esperienze Delve nelle pagine della relativa farm di SharePoint locale.</span><span class="sxs-lookup"><span data-stu-id="79950-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="79950-164">Tutti questi scenari ibridi di SharePoint, ad eccezione dell'icona di avvio delle app ibrida estensibile, sono disponibili per gli utenti di SharePoint 2016 e SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="79950-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="79950-165">Per ulteriori informazioni, vedere [SharePoint ibrido]((http://hybrid.office.com/sharepoint/)).</span><span class="sxs-lookup"><span data-stu-id="79950-165">For more information, see [SharePoint Hybrid]((http://hybrid.office.com/sharepoint/)).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="79950-166">Exchange Server 2016 ibrido</span><span class="sxs-lookup"><span data-stu-id="79950-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="79950-167">Con Exchange Server 2016 ibrido, puoi ottenere i vantaggi di Exchange Online in Office 365 per gli utenti online, mentre gli utenti locali continuano a usare l'infrastruttura di Exchange Server esistente.</span><span class="sxs-lookup"><span data-stu-id="79950-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="79950-168">**Figura 5: configurazione ibrida di Exchange 2016**</span><span class="sxs-lookup"><span data-stu-id="79950-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Configurazione ibrida di Exchange 2016](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="79950-170">La figura 5 mostra la configurazione ibrida di Exchange 2016, formata da server Cassette postali di Exchange che comunicano con Exchange Online Protection e con le cassette postali di Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="79950-171">Alcuni utenti hanno un server di posta elettronica locale, altri usano Exchange Online; tuttavia, condividono tutti lo stesso spazio di indirizzi di posta elettronica. </span><span class="sxs-lookup"><span data-stu-id="79950-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="79950-172">Questa configurazione ibrida:</span><span class="sxs-lookup"><span data-stu-id="79950-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="79950-173">Sfrutta l'infrastruttura di Exchange Server esistente durante la migrazione a Exchange Online in base alle esigenze di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="79950-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="79950-174">Consente di supportare i siti remoti senza influire sull'infrastruttura per la gestione delle filiali.</span><span class="sxs-lookup"><span data-stu-id="79950-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="79950-175">Consente di instradare la posta elettronica Internet in arrivo tramite Exchange Online Protection in Office 365.</span><span class="sxs-lookup"><span data-stu-id="79950-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="79950-176">Risponde alle esigenze delle organizzazioni multinazionali con filiali per le quali è necessario che i dati siano conservati in locale.</span><span class="sxs-lookup"><span data-stu-id="79950-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="79950-177">Puoi anche integrare questa configurazione ibrida con altre applicazioni di Microsoft Office 365, tra cui Skype for Business Online e SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="79950-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="79950-178">Per ulteriori informazioni, vedere [Distribuzioni ibride di Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) e [Versione ibrida di Exchange]((http://hybrid.office.com/exchange/)).</span><span class="sxs-lookup"><span data-stu-id="79950-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and[Exchange Hybrid]((http://hybrid.office.com/exchange/)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="79950-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="79950-179">See Also</span></span>

[<span data-ttu-id="79950-180">Cloud ibrido Microsoft per Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="79950-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="79950-181">Risorse sull'architettura IT del cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="79950-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="79950-182">[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="79950-182">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>



