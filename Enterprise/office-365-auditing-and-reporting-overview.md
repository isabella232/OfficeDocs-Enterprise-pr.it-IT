---
title: Controllo e creazione di report nei servizi cloud Microsoft
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- M365-analytics
description: Panoramica delle funzionalità di controllo e Reporting all'interno di Office 365, Microsoft 365 e Service Assurance.
ms.openlocfilehash: 545c1224a5c7fc181028be555b14deeff6048ca9
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035636"
---
# <a name="auditing-and-reporting-in-microsoft-cloud-services"></a>Controllo e creazione di report nei servizi cloud Microsoft

## <a name="introduction"></a>Introduzione

I servizi cloud Microsoft includono diverse funzionalità di controllo e Reporting che è possibile utilizzare per monitorare l'attività dell'utente e dell'amministrazione all'interno del tenant, gli esempi includono le modifiche apportate alle impostazioni di configurazione del tenant di Exchange Online e di SharePoint Online e modifiche apportate dagli utenti ai documenti e ad altri elementi. È possibile utilizzare le informazioni di controllo e i report disponibili nei servizi cloud di Microsoft per gestire in modo più efficace l'esperienza utente, attenuare i rischi e soddisfare gli obblighi di conformità.

## <a name="security--compliance-centers"></a>Centro sicurezza & Compliance

Il Centro sicurezza [& conformità di Office 365](https://protection.office.com), il centro [sicurezza Microsoft 365](https://security.microsoft.com)e il [centro conformità Microsoft 365](https://compliance.microsoft.com) sono portali One-Stop per la protezione dei dati nell'organizzazione e comprendono numerose funzionalità di controllo e creazione di report. Questi centri consentono di soddisfare le esigenze di protezione dei dati o conformità e di controllare l'attività dell'utente e dell'amministratore. È possibile accedere a questi centri utilizzando l'account di amministratore della sottoscrizione.

Questi centri includono i riquadri di spostamento per accedere a diverse funzionalità:

- **Avvisi:** Consente di gestire gli avvisi, visualizzare gli avvisi relativi alla sicurezza e gestire gli avvisi avanzati tramite [Office 365 cloud app Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).
- **Autorizzazioni:** Consente di [assegnare autorizzazioni](https://support.office.com/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76) quali amministratore della conformità, eDiscovery Manager e altre persone all'interno dell'organizzazione in modo che possano eseguire attività in questi centri. È possibile assegnare le autorizzazioni per la maggior parte delle funzionalità di ogni centro, ma è necessario configurare altre autorizzazioni utilizzando l'interfaccia di amministrazione di Exchange e l'interfaccia di amministrazione di SharePoint.
- **Gestione delle minacce:** Consente di creare e applicare criteri di gestione dei dispositivi tramite la [gestione dei dispositivi mobili di Office 365](https://support.office.com/article/Overview-of-Mobile-Device-Management-for-Office-365-faa7d8e5-645d-4d59-839c-c8d4c1869e4a), di impostare i criteri di [prevenzione della perdita di dati](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e) (DLP) per l'organizzazione, di configurare il filtro della posta elettronica, l'antimalware, la posta identificata di DomainKeys (DKIM), gli allegati sicuri, i collegamenti sicuri e le app OAuth.
- **Governance dei dati:** Consente di [importare i dati di posta elettronica o di SharePoint da altri sistemi in Office 365](https://support.office.com/article/Import-PST-files-or-SharePoint-data-to-Office-365-ba688e0a-0fcb-4bd7-8e57-2b669564ea84), [configurare le cassette postali di archiviazione](https://support.office.com/article/Enable-archive-mailboxes-in-the-Office-365-Security-Compliance-Center-268a109e-7843-405b-bb3d-b9393b2342ce)e impostare i criteri di [conservazione](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) per la posta elettronica e altri contenuti all'interno dell'organizzazione.
- **Indagine & di ricerca:** Fornisce gli strumenti di [Ricerca contenuti](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a), [log di controllo](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c), quarantena e [gestione dei casi di eDiscovery](https://support.office.com/article/Manage-eDiscovery-cases-in-the-Office-365-Security-Compliance-Center-edea80d6-20a7-40fb-b8c4-5e8c8395f6da) per eseguire rapidamente le attività tra cassette postali, gruppi e cartelle pubbliche di Exchange Online, SharePoint Online e OneDrive for business.
- **Report:** Consente di accedere rapidamente ai [report](https://support.office.com/article/Reports-in-the-Office-365-Security-Compliance-Center-7acd33ce-1ec8-49fb-b625-43bac7b58c5a) di SharePoint Online, OneDrive for business, Exchange Online e Azure ad.
- **Garanzia del servizio:** Vengono fornite informazioni su come Microsoft mantiene la sicurezza, la privacy e la conformità agli standard globali per Office 365, Azure, Microsoft Dynamics CRM Online, Microsoft Intune e altri servizi cloud. Include inoltre l'accesso ai report di controllo ISO, SOC e di altro tipo, nonché ai controlli controllati, che forniscono informazioni dettagliate sui vari controlli che sono stati testati e verificati da revisori di terze parti di Office 365.

## <a name="service-assurance"></a>Garanzia del servizio

Molte organizzazioni nelle industrie regolamentate sono soggette a requisiti di conformità estensivi. Per eseguire le proprie valutazioni sui rischi, i clienti hanno spesso bisogno di informazioni approfondite su come Office 365 gestisce la sicurezza e la privacy dei propri dati. Microsoft si impegna a garantire la sicurezza e la privacy dei dati del cliente nei suoi servizi cloud e a guadagnare la fiducia dei clienti fornendo una visione trasparente delle sue operazioni e un facile accesso ai rapporti di conformità e alle valutazioni indipendenti.

Service Assurance fornisce la trasparenza delle operazioni e delle informazioni su come Microsoft mantiene la sicurezza, la privacy e la conformità dei dati del cliente in Office 365. Include i report di controllo di terze parti insieme a una raccolta di white paper, domande frequenti e altri materiali su Office 365 argomenti quali la crittografia dei dati, la resilienza dei dati, la gestione degli incidenti di sicurezza e altro ancora. I clienti possono utilizzare queste informazioni per eseguire le proprie valutazioni dei rischi normativi. I responsabili della conformità possono assegnare il ruolo "utente di servizio Assurance" per fornire agli utenti l'accesso al servizio Assurance. L'amministratore tenant può anche fornire agli utenti esterni, ad esempio i revisori indipendenti, la possibilità di accedere alle informazioni nel dashboard di Assurance del servizio tramite il [Cloud Service Trust Portal](https://aka.ms/STP) (STP) di Microsoft. Per informazioni dettagliate su come accedere a STP, visitare [Introduzione al Service Trust Portal per le sottoscrizioni di Office 365 for business, Azure e Dynamics CRM Online](https://aka.ms/STPHelp).

## <a name="onedrive-for-business-admin-center"></a>Interfaccia di amministrazione di OneDrive for business

L'interfaccia di amministrazione di Microsoft OneDrive consente di gestire rapidamente e facilmente le impostazioni di OneDrive for business dell'organizzazione in un'unica posizione. Per utilizzare l'interfaccia di amministrazione di OneDrive, è necessario accedere a onedrive.com. È inoltre necessario essere un amministratore globale per l'organizzazione o un amministratore personalizzato con il ruolo di amministratore di SharePoint. Accedere all'interfaccia di amministrazione di OneDrive for [https://admin.onedrive.com](https://admin.onedrive.com/)business all'indirizzo.

Le caratteristiche principali includono un'area di conformità che consente agli amministratori di accedere al centro di gestione appropriato per scenari chiave come la ricerca nel registro di controllo, l'utilizzo di DLP, la conservazione, la eDiscovery e gli avvisi.

## <a name="related-links"></a>Collegamenti correlati

- [Funzionalità di ricerca e di eDiscovery](office-365-ediscovery-and-search-features.md)
- [Funzionalità di reporting di Office 365](office-365-reporting-features.md)
- [API Office 365 Management Activity](office-365-management-activity-api.md)
- [Migrazioni delle cassette postali di Office 365](office-365-mailbox-migrations.md)
- [Log interni per Office 365 Engineering](office-365-internal-logging.md)