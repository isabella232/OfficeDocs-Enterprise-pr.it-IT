---
title: Supporto delle app client di Office 365-accesso condizionale
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
description: Informazioni sul supporto delle app client di Office 365 per l'accesso condizionale
ms.openlocfilehash: c5c94a1ed7d87a625599c37e5652911109afec33
ms.sourcegitcommit: b1a32e8df403143fb34eaddf116aed3595228c8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2019
ms.locfileid: "36817289"
---
# <a name="office-365-client-app-support--conditional-access"></a>Supporto delle app client di Office 365-accesso condizionale

Nei luoghi di lavoro moderni, gli utenti possono accedere alle risorse dell'organizzazione utilizzando vari dispositivi e app da qualsiasi luogo. Di conseguenza, solo concentrarsi su chi può accedere a una risorsa non è più sufficiente. L'organizzazione deve anche supportare la modalità e la posizione di accesso a una risorsa nell'infrastruttura di controllo di accesso.

Con il dispositivo Azure AD, la posizione e l'accesso condizionale basato sull'autenticazione a più fattori, è possibile rispondere a questo nuovo requisito. L'accesso condizionale è una funzionalità di Azure Active Directory che consente di applicare i controlli sull'accesso alle app nel proprio ambiente, tutti basati su condizioni specifiche e gestite da una posizione centrale.

Ulteriori informazioni sull' [accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/).

## <a name="supported-platforms"></a>Piattaforme supportate

 - Desktop di Windows 10
 - App di Windows 10 moderne
 - Web browser
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

Per ulteriori informazioni sul supporto delle piattaforme in Office 365, vedere [requisiti di sistema per office 365](https://products.office.com/office-system-requirements).

## <a name="supported-clients"></a>Client supportati

Le versioni più recenti dei client seguenti supportano l'accesso condizionale:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icona di Azure](media/o365-azure-64x64.png) <br> [Portale di <br> Azure ad](https://azure.microsoft.com/features/azure-portal/) | ![Icona di accesso](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Icona portale aziendale](media/o365-microsoft-64x64.png) <br> [Portale <br> aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Icona di approfondimento](media/o365-delve-64x64.png) <br> [Approfondire<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Icona Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![Icona del server perimetrale](media/o365-edge-64x64.png) <br> [Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Icona di Exchange](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Icona Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icona flusso](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icona moduli](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Icona Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icona Office.com](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Icona dell'obiettivo](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Icona di amministrazione di Office 365](media/o365-o365admin-64x64.png) <br> [Amministratore di <br> Office 365](https://products.office.com/business/manage-office-365-admin-app) | ![Icona di OneDrive for business](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![Icona di OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icona di Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icona Planner](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icona PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icona PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Icona del progetto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icona editore](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![Icona di SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Icona di Skype for business](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![Icona note adesive](media/o365-stickynotes-64x64.png) <br> [Sticky Notes](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| ![Icona flusso](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icona ondeggiamento](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icona Teams](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icona da fare](media/o365-todo-64x64.png) <br> [da fare](https://todo.microsoft.com) | ![Icona di Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) 
| ![Icona Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icona Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>Moduli di PowerShell supportati

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icona di Azure](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icona di SharePoint](media/o365-sharepoint-64x64.png) <br> [PowerShell di <br> SharePoint Online](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup> supporto per approfondimenti su Android disponibili a breve. <br>
> <sup>2</sup> supporto per OneDrive su MacOS disponibile a breve.
