---
title: Supporto per applicazioni Client Office 365 - autenticazione moderno
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Supporto Client App per Office 365 per l'autenticazione moderno.
ms.openlocfilehash: 18ef5b2219c9527594ae8fcff7e29052671d1431
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "29771125"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Supporto per applicazioni Client Office 365 - autenticazione moderno

La funzionalità moderno autenticazione di Microsoft rende basata su Active Directory autenticazione raccolta ADAL sign-in per le applicazioni client di Office piattaforme diverse. In questo modo le funzionalità di accesso, ad esempio l'autenticazione a più fattori (MFA), smart card e l'autenticazione basata su certificati.

Informazioni [sull'autenticazione a più fattori](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication) e [l'autenticazione basata su certificati](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="supported-platforms"></a>Piattaforme supportate

 - Desktop Windows 10
 - App di moderno Windows 10
 - Web browser
 - Android
 - iOS
 - Mac OS

## <a name="supported-clients"></a>Client supportati

Le versioni più recenti dei client seguenti supportano l'autenticazione moderno:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icona di Azure](media/o365-azure-64x64.png) <br> [Azure Active Directory <br> Portal](https://azure.microsoft.com/features/azure-portal/) | ![Icona del portale aziendale](media/o365-microsoft-64x64.png) <br> [Società <br> Portal](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Informazioni dettagliate sull'icona](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icona Dynamics 365](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![Icona Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) |
| ![Icona di flusso](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icona di moduli](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icona Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Icona di amministrazione di Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> amministrazione](https://products.office.com/business/manage-office-365-admin-app) | ![Icona lente](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | 
| ![OneDrive per icona Business](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![Icona di OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icona di Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icona di pianificazione](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![Icona PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)
| ![Icona PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icona progetto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icona di SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint](https://products.office.com/sharepoint) | ![Skype per icona Business](media/o365-skypeforbusiness-64x64.png) <br> [Skype per <br> Business](https://www.skype.com/business/) | ![Icona StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![Le icone di Lotus Notes](media/o365-stickynotes-64x64.png) <br> [Sticky Notes](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Icona di flusso](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icona sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icona di team](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icona da fare](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com)
| ![Icona Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icona Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) |![Icona di Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Icona di Yammer](media/o365-yammer-64x64.png) <br> [Yammer <br> notifica](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>Moduli di PowerShell supportati

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Icona di Azure](media/o365-azure-64x64.png) <br> [Azure Active Directory <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Icona di Exchange](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![Icona di SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)