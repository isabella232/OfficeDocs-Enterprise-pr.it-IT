---
title: Monitorare la connettività di Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Una volta distribuito Office 365, è possibile mantenere la connettività di Office 365 usando alcune delle tecniche e degli strumenti seguenti. È consigliabile leggere le linee guida ufficiali sull'integrità e la continuità dei servizi, oltre alle procedure consigliate per l'uso di Office 365 in una rete lenta. È inoltre opportuno acquisire l'app di amministrazione di Office 365 e aggiungere ai preferiti la nostra guida Office 365 per le aziende - Guida per amministratori.
ms.openlocfilehash: 385aef73173ea6bab421fae6d10622d7a8fe3c80
ms.sourcegitcommit: 9c39ba0c21fbe86343f825bb589a108ec5f176bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "37931694"
---
# <a name="monitor-office-365-connectivity"></a><span data-ttu-id="df1ca-105">Monitorare la connettività di Office 365</span><span class="sxs-lookup"><span data-stu-id="df1ca-105">Monitor Office 365 connectivity</span></span>

<span data-ttu-id="df1ca-p102">Una volta distribuito Office 365, è possibile mantenere la connettività di Office 365 usando alcune delle tecniche e degli strumenti seguenti. È consigliabile leggere le linee guida ufficiali sull'[integrità e la continuità dei servizi](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity), oltre alle [procedure consigliate per l'uso di Office 365](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) in una rete lenta. È inoltre opportuno acquisire l'[app di amministrazione di Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) e aggiungere ai preferiti la nostra guida [Office 365 per le aziende - Guida per amministratori](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span><span class="sxs-lookup"><span data-stu-id="df1ca-p102">Once you've deployed Office 365, you can maintain Office 365 connectivity using some of the tools and techniques below. You'll want to understand the official [Service Health and Continuity](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) guidelines as well as our [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). You'll also want to grab the [Office 365 admin app](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) and bookmark our [Office 365 for business - Admin Help](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).</span></span>
  
## <a name="monitoring-office-365-connectivity"></a><span data-ttu-id="df1ca-109">Monitoraggio della connettività di Office 365</span><span class="sxs-lookup"><span data-stu-id="df1ca-109">Monitoring Office 365 Connectivity</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="df1ca-110">**Ricevere notifiche sui nuovi endpoint di Office 365**</span><span class="sxs-lookup"><span data-stu-id="df1ca-110">**Getting notified of new Office 365 endpoints**</span></span> <br/> |<span data-ttu-id="df1ca-p103">Se si [gestiscono gli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) e si desidera ricevere notifiche quando ne vengono pubblicati di nuovi, è possibile sottoscrivere il nostro feed RSS usando un lettore RSS a scelta. Ecco come [effettuare la sottoscrizione tramite Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o [ricevere gli aggiornamenti del feed RSS tramite posta elettronica](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span><span class="sxs-lookup"><span data-stu-id="df1ca-p103">If you're [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), you'll want to receive notifications when we publish new endpoints, you can subscribe to our RSS feed using your favorite RSS reader. Here is how to [subscribe via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) or you can [have the RSS feed updates emailed to you](https://go.microsoft.com/fwlink/p/?LinkId=532417).  </span></span><br/> |
|<span data-ttu-id="df1ca-113">**Usare System Center per monitorare Office 365**</span><span class="sxs-lookup"><span data-stu-id="df1ca-113">**Use System Center to Monitor Office 365**</span></span> <br/> |<span data-ttu-id="df1ca-p104">Se si usa Microsoft System Center, è possibile scaricare il [Management Pack di System Center per Office 365](https://www.microsoft.com/download/details.aspx?id=43708) per iniziare subito a monitorare Office 365. Per indicazioni più dettagliate, vedere la guida operativa del Management Pack o il post di blog sul [monitoraggio di Office365 tramite System Center Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx).</span><span class="sxs-lookup"><span data-stu-id="df1ca-p104">If you're using Microsoft System Center, you can download the [System Center Management Pack for Office 365](https://www.microsoft.com/download/details.aspx?id=43708) to begin monitoring Office 365 today. For more detailed guidance, please see the management pack operations guide or this blog post [Office365 Monitoring using System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx)</span></span> <br/> |
|<span data-ttu-id="df1ca-116">**Monitorare l'integrità di Azure ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="df1ca-116">**Monitoring the health of Azure ExpressRoute**</span></span> <br/> |<span data-ttu-id="df1ca-117">Se ci si connette a Office 365 con Azure ExpressRoute per Office 365, è consigliabile assicurarsi di usare il dashboard per l'integrità dei servizi di Office 365 e consultare l'articolo sulla [riduzione delle tempistiche per la risoluzione di problemi con Integrità risorse di Azure](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span><span class="sxs-lookup"><span data-stu-id="df1ca-117">If you are connecting to Office 365 using Azure ExpressRoute for Office 365, you'll want to ensure that you're using both the Office 365 Service Health Dashboard as well as the Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)</span></span> <br/> |
|<span data-ttu-id="df1ca-118">**Usare Azure AD Connect Health con AD FS**</span><span class="sxs-lookup"><span data-stu-id="df1ca-118">**Using Azure AD Connect Health with AD FS**</span></span> <br/> |<span data-ttu-id="df1ca-119">Se si usa AD FS per Single Sign-On con Office 365, per iniziare, [usare Azure AD Connect Health per monitorare l'infrastruttura AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span><span class="sxs-lookup"><span data-stu-id="df1ca-119">If you're using AD FS for Single Sign-On with Office 365, you'll want to begin [using Azure AD Connect Health to monitor your AD FS infrastructure](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).</span></span>  <br/> |
|<span data-ttu-id="df1ca-120">**Monitorare Office 365 a livello di programmazione**</span><span class="sxs-lookup"><span data-stu-id="df1ca-120">**Programmatically monitor Office 365**</span></span> <br/> |<span data-ttu-id="df1ca-121">Vedere le indicazioni sull'[API di gestione di Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span><span class="sxs-lookup"><span data-stu-id="df1ca-121">Refer to our guidance on the [Office 365 Management API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).</span></span>  <br/> |

<span data-ttu-id="df1ca-122">Ecco un collegamento breve per tornare alla pagina: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span><span class="sxs-lookup"><span data-stu-id="df1ca-122">Here's a short link you can use to come back: [hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="df1ca-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="df1ca-123">See also</span></span>

[<span data-ttu-id="df1ca-124">Configurare le applicazioni e i servizi di Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="df1ca-124">Configure Office 365 Enterprise services and applications</span></span>](configure-services-and-applications.md)
  
[<span data-ttu-id="df1ca-125">Preparare l'organizzazione per Office 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="df1ca-125">Get your organization ready for Office 365 Enterprise</span></span>](get-your-organization-ready-for-office-365.md)
  
[<span data-ttu-id="df1ca-126">Pianificazione della rete e ottimizzazione delle prestazioni per Office 365</span><span class="sxs-lookup"><span data-stu-id="df1ca-126">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="df1ca-127">Integrazione di Office 365 con ambienti locali</span><span class="sxs-lookup"><span data-stu-id="df1ca-127">Office 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
[<span data-ttu-id="df1ca-128">Gestione degli endpoint di Office 365</span><span class="sxs-lookup"><span data-stu-id="df1ca-128">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
