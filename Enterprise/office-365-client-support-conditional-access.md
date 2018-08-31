---
title: Supporto per applicazioni Client Office 365 - accesso condizionale
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: Acquisire familiarità con il supporto di applicazioni client di Office 365 per access condizionale
ms.openlocfilehash: 215b97daf532e22eb37618d66779378e37accb31
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915301"
---
# <a name="office-365-client-app-support---conditional-access"></a>Supporto per applicazioni Client Office 365 - accesso condizionale

Nell'area di lavoro moderno, gli utenti possono accedere a risorse dell'organizzazione utilizzando un'ampia gamma di dispositivi e applicazioni praticamente da qualsiasi posizione. Di conseguenza, concentrarsi soltanto su chi può accedere a una risorsa non è sufficiente diversi. L'organizzazione deve supportare anche come e dove una risorsa è in uso nell'infrastruttura di controllo di accesso. Con Azure Active Directory dispositivo, posizione e a più fattori basato sull'autenticazione condizionale l'accesso, è possibile soddisfare questo requisito nuovo. Accesso condizionato è una funzionalità di Azure Active Directory che consente di applicare ai controlli di accesso alle App nell'ambiente, a seconda del condizioni specifiche e gestiti da una posizione centrale. 

Ulteriori informazioni sulle [basati su dispositivo](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications), [basate su percorso](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)e l'accesso condizionale [basata su MFA](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups) .

## <a name="supported-platforms"></a>Piattaforme supportate

 - Desktop Windows 10
 - App di moderno Windows 10
 - Web browser
 - Android
 - iOS
 - Mac OS<sup>1</sup>

## <a name="supported-clients"></a>Client supportati

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Informazioni dettagliate sull'icona](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Icona Excel](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Icona di flusso](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![Icona di moduli](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Icona Kaizala](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Icona di amministrazione di Office 365](media/o365-o365admin-64x64.png) <br> [Office 365 <br> amministrazione](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive per icona Business](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![Icona di OneNote](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Icona di Outlook](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Icona di pianificazione](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![Icona PowerBI](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![Icona PowerPoint](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Icona progetto](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Icona di SharePoint](media/o365-sharepoint-64x64.png) <br> [SharePoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype per icona Business](media/o365-skypeforbusiness-64x64.png) <br> [Skype per <br> Business](https://www.skype.com/business/) 
| ![Icona StaffHub](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![Icona di flusso](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Icona sway](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Icona di team](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![Icona da fare](media/o365-todo-64x64.png) <br> [To-Do](https://todo.microsoft.com) 
| ![Icona Visio](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Icona Word](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Icona di Yammer](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup> app SharePoint supporta in Mac OS saranno presto disponibili.