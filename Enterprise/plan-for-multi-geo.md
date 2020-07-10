---
title: Piano per Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Informazioni su Microsoft 365 Multi-Geo, come funziona Multi-Geo e quali posizioni geografiche sono disponibili per l'archiviazione dei dati.
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052459"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Piano per Microsoft 365 Multi-Geo

Questa guida è utile agli amministratori di società multinazionali che stanno preparando l'espansione del tenant di Microsoft 365 in altre aree geografiche in base alla presenza dell'azienda per soddisfare i requisiti di residenza dei dati.

In una configurazione multi-geo, il tenant di Microsoft 365 è costituito da una posizione centrale e una o più posizioni satellite. Si tratta di un singolo tenant che si estende su più località geografiche. Le informazioni di tenant, tra cui la località geografica, vengono gestite in Azure Active Directory (Azure AD).

Ecco un glossario dei termini principali per facilitare la comprensione della configurazione multi-geografica:

-   **Tenant**: rappresentazione di un'organizzazione in Microsoft 365 che in genere contiene uno o più domini associati ad essa ad esempio, https://contoso.sharepoint.com). 

-   **Posizioni geografiche**: le località geografiche disponibili per ospitare i dati in un tenant di Microsoft 365.

-   **Posizioni satellite**: posizioni geografica aggiuntive configurate per ospitare dati nel tenant di Microsoft 365. I tenant multi-geo si estendono su più di una posizione geografica, ad esempio, America del Nord ed Europa.

-   **Percorso dati preferito (PDL)**: la posizione geografica in cui sono memorizzati i dati di Exchange e di OneDrive di un singolo utente. Questo può essere impostato dall'amministratore per una delle posizioni geografiche che sono state configurate per il tenant. Si noti che se si cambia il PDL di un utente che ha già un sito di OneDrive, i dati di OneDrive non vengono spostati nella nuova posizione geografica automaticamente. Vedere[Spostare una libreria OneDrive in un'altra posizione geo](move-onedrive-between-geo-locations.md) per più informazioni. Se si dispone di una cassetta postale di Exchange, la cassetta postale viene spostata automaticamente nella nuova posizione dati preferita dati.

Per abilitare Multi-Geo sono necessarie quattro attività:

1.  Collaborare con il team responsabile dell'account per aggiungere il piano di servizio _Multi-Geo Capabilities in Microsoft 365_.

2.  Scegliere le posizioni satellite desiderate e aggiungerle al tenant.

3.  Impostare la posizione di dati preferita dagli utenti nella posizione satellite desiderata. Quando viene effettuato il provisioning in un nuovo sito di OneDrive o di una cassetta postale di Exchange per un utente, viene eseguito il provisioning al suo PDL.

4.  Eseguire la migrazione dei siti di OneDrive esistenti dalla posizione centrale alla posizione dati preferita in base alle esigenze. (Le cassette postali di Exchange vengono trasferite automaticamente quando si imposta PDL di un utente.)

Vedere [Configurare Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md) per informazioni dettagliate su ognuno di questi passaggi.

> [!IMPORTANT]
> Si noti che Microsoft 365 Multi-Geo non è progettato principalmente per ottimizzare le prestazioni, ma per soddisfare i requisiti di residenza dei dati. Per informazioni sull'ottimizzazione delle prestazioni di Microsoft 365, vedere [Pianificazione della rete e ottimizzazione delle prestazioni per Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o contattare il gruppo di supporto.

È possibile configurare una delle seguenti località come posizioni satellite in cui è possibile ospitare OneDrive, siti di SharePoint e cassette postali di Exchange. Durante la pianificazione di multi-geo, creare un elenco di posizioni da aggiungere al tenant di Microsoft 365. È consigliabile iniziare con una o due posizioni satellite e gradualmente espandere in più posizioni geografiche, se necessario.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.

## <a name="best-practices"></a>Procedure consigliate

È consigliabile creare un utente test in Microsoft 365 per eseguire alcune prove iniziali. È possibile eseguire alcune procedure di test e verifica associati a questo utente prima di procedere agli utenti di produzione integrata in Microsoft 365 Multi-Geo.

Dopo aver completato i test con l'utente test, selezionare un gruppo pilota, ad esempio il proprio dipartimento IT, prima di usare OneDrive e Exchange in una nuova posizione geografica. Per il primo gruppo, selezionare gli utenti che non dispongono ancora di un OneDrive. È consigliabile non inserire non più di cinque persone nel gruppo iniziale, ma espanderlo gradualmente seguendo un approccio di distribuzione in blocco.

Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.

Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

Se gli utenti vengono sincronizzati da un sistema di Active Directory locale con Azure Active Directory, è necessario impostare la posizione preferita dati come attributo di Active Directory e sincronizzarla con Azure Active Directory Connect. Non è possibile configurare direttamente la posizione dati consigliata per gli utenti sincronizzati con Azure AD PowerShell. La procedura per configurare PDL in Active Directory e la sincronizzazione è descritta in[Sincronizzazione di Azure Active Directory Connect: configurare il percorso di dati consigliato per le risorse di Microsoft 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.

Leggere [Esperienza utente in un ambiente multi-geografico](multi-geo-user-experience.md) per i dettagli riguardanti l'esperienza degli utenti finali in un ambiente multi-geografico.

Per informazioni dettagliate sull'esperienza di Teams in un tenant Microsoft 365 Multi-Geo, vedere [Esperienza di Teams in un tenant con Microsoft 365 OneDrive e SharePoint Online Multi-Geo.](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)

Per iniziare a configurare Microsoft 365 Multi-Geo, vedere [Configurare Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

Dopo aver completato la configurazione, è necessario [eseguire la migrazione delle raccolte OneDrive dell'utente](move-onedrive-between-geo-locations.md) per consentire agli utenti di lavorare dalla propria posizione dati preferita.
