---
title: Monitorare la connettività di Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: Dopo aver distribuito Microsoft 365, è possibile mantenere la connettività Microsoft 365 utilizzando alcuni degli strumenti e delle tecniche seguenti. È consigliabile comprendere le linee guida per l'integrità e la continuità dei servizi ufficiali, nonché le procedure consigliate per l'utilizzo di Microsoft 365 su una rete lenta.
ms.openlocfilehash: aa47ff76f70e48285c6ca5f21ffdf30f1db52521
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571009"
---
# <a name="monitor-microsoft-365-connectivity"></a>Monitorare la connettività di Microsoft 365

Dopo aver distribuito Microsoft 365, è possibile mantenere la connettività Microsoft 365 utilizzando alcuni degli strumenti e delle tecniche seguenti. È consigliabile comprendere le linee guida per l' [integrità e la continuità dei servizi](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) ufficiali, nonché le [procedure consigliate per l'utilizzo di Microsoft 365 su una rete lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Si vorrà anche prendere l' [app microsoft 365 admin](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) e aggiungere un segnalibro a [Microsoft 365 for Business-Guida per gli amministratori](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Monitoraggio della connettività di Microsoft 365

|||
|:-----|:-----|
|**Ottenere la notifica dei nuovi endpoint di Microsoft 365** <br/> |Se si [gestiscono gli endpoint di Microsoft 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), è necessario ricevere notifiche quando si pubblicano nuovi endpoint, è possibile sottoscrivere un feed RSS usando il lettore RSS preferito. Ecco come effettuare la [sottoscrizione tramite Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) oppure è possibile che [gli aggiornamenti del feed RSS vengano inviati tramite posta elettronica](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Utilizzare System Center per monitorare Microsoft 365** <br/> |Se si utilizza Microsoft System Center, è possibile scaricare [System Center Management Pack per Office 365](https://www.microsoft.com/download/details.aspx?id=43708) per avviare il monitoraggio di Microsoft 365 oggi. Per informazioni più dettagliate, vedere la Guida alle operazioni del Management Pack o questo post di Blog sul [monitoraggio di Office365 tramite System Centre Operations Manager](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**Monitorare l'integrità di Azure ExpressRoute** <br/> |Se si sta effettuando la connessione a Microsoft 365 utilizzando Azure ExpressRoute per Microsoft 365, è necessario assicurarsi di utilizzare sia il dashboard di integrità del servizio Microsoft 365 che la riduzione del [tempo di risoluzione dei problemi con Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Usare Azure AD Connect Health con AD FS** <br/> |Se si usa AD FS per Single Sign-on con Microsoft 365, si vorrà iniziare a [usare Azure ad Connect Health per monitorare l'infrastruttura ad FS](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/).  <br/> |
|**Monitorare a livello di programmazione Microsoft 365** <br/> |Fare riferimento alle indicazioni sull' [API di gestione Microsoft 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Ecco un collegamento breve per tornare alla pagina: [https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>Vedere anche

[Configurare le applicazioni e i servizi Microsoft 365 Enterprise](configure-services-and-applications.md)
  
[Preparare la propria organizzazione per Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Pianificazione della rete e ottimizzazione delle prestazioni per Microsoft 365](network-planning-and-performance.md)
  
[Integrazione di Microsoft 365 con ambienti locali](office-365-integration.md)
  
[Gestione degli endpoint di Microsoft 365](managing-office-365-endpoints.md)
