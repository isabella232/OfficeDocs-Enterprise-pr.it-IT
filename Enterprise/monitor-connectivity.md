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
ms.openlocfilehash: 93fbc9448ce25ef3d5d3f1d577c6d1c23ae4472a
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721967"
---
# <a name="monitor-office-365-connectivity"></a>Monitorare la connettività di Office 365

Una volta distribuito Office 365, è possibile mantenere la connettività di Office 365 usando alcune delle tecniche e degli strumenti seguenti. È consigliabile leggere le linee guida ufficiali sull'[integrità e la continuità dei servizi](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity), oltre alle [procedure consigliate per l'uso di Office 365](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) in una rete lenta. È inoltre opportuno acquisire l'[app di amministrazione di Office 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) e aggiungere ai preferiti la nostra guida [Office 365 per le aziende - Guida per amministratori](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-office-365-connectivity"></a>Monitoraggio della connettività di Office 365

|||
|:-----|:-----|
|**Ricevere notifiche sui nuovi endpoint di Office 365** <br/> |Se si [gestiscono gli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) e si desidera ricevere notifiche quando ne vengono pubblicati di nuovi, è possibile sottoscrivere il nostro feed RSS usando un lettore RSS a scelta. Ecco come [effettuare la sottoscrizione tramite Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) o [ricevere gli aggiornamenti del feed RSS tramite posta elettronica](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Usare System Center per monitorare Office 365** <br/> |Se si usa Microsoft System Center, è possibile scaricare il [Management Pack di System Center per Office 365](https://www.microsoft.com/download/details.aspx?id=43708) per iniziare subito a monitorare Office 365. Per indicazioni più dettagliate, vedere la guida operativa del Management Pack o il post di blog sul [monitoraggio di Office365 tramite System Center Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx). <br/> |
|**Monitorare l'integrità di Azure ExpressRoute** <br/> |Se ci si connette a Office 365 con Azure ExpressRoute per Office 365, è consigliabile assicurarsi di usare il dashboard per l'integrità dei servizi di Office 365 e consultare l'articolo sulla [riduzione delle tempistiche per la risoluzione di problemi con Integrità risorse di Azure](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Usare Azure AD Connect Health con AD FS** <br/> |Se si usa AD FS per Single Sign-On con Office 365, per iniziare, [usare Azure AD Connect Health per monitorare l'infrastruttura AD FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).  <br/> |
|**Monitorare Office 365 a livello di programmazione** <br/> |Vedere le indicazioni sull'[API di gestione di Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>Vedere anche

[Configurare le applicazioni e i servizi di Office 365 Enterprise](configure-services-and-applications.md)
  
[Preparare l'organizzazione per Office 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Pianificazione della rete e ottimizzazione delle prestazioni per Office 365](network-planning-and-performance.md)
  
[Integrazione di Office 365 con ambienti locali](office-365-integration.md)
  
[Gestione degli endpoint di Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
