---
title: Visualizzare lo stato di sincronizzazione della directory in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Informazioni su come disattivare la sincronizzazione delle directory. È inoltre possibile visualizzare lo stato.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541425"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Visualizzare lo stato di sincronizzazione della directory in Office 365
Se è stata integrata di Active Directory locale con Azure Active Directory da sincronizzare l'ambiente locale con Office 365, è inoltre possibile controllare lo stato della sincronizzazione.
  
## <a name="view-directory-synchronization-status"></a>Visualizzare lo stato di sincronizzazione della directory
- Accedere all'interfaccia di amministrazione di Office 365 e scegliere **Stato DirSync** nella home page. 
- In alternativa, è possibile accedere ai **utenti** \> **utenti attivi**e nella pagina **utenti attivi** , fare clic su **ulteriori** \> **la sincronizzazione delle Directory**. Nel riquadro di **Sincronizzazione della Directory** , scegliere **andare a gestione DirSync**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Nella pagina Gestisci directory synchronization informazioni

Nella tabella seguente sono elencate le caratteristiche è possibile ottenere informazioni nella pagina.
  
Se si verifica un problema con la sincronizzazione della directory, in anche questa pagina sono riportati gli errori. Per ulteriori informazioni su errori che possono verificarsi, vedere [gli errori di sincronizzazione directory di identità in Office 365](identify-directory-synchronization-errors.md).
  
|**Elemento**|**Novità per**|
|:-----|:-----|
|**Verificata i domini** | Numero di domini in Office 365 tenant che si sono verificati è proprietario. |
|**Domini non verificati** | Domini sono aggiunti ma non verificato. |
|**Sincronizzazione di directory attivata** |True o False. Specifica se è stata abilitata la sincronizzazione di directory. |
|**Ultima sincronizzazione della directory** | Ora ultima esecuzione della sincronizzazione della directory. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento di risoluzione dei problemi se l'ultima sincronizzazione risalgono a più di tre giorni fa. |
|**Sincronizzazione delle password abilitata** | True o False. Specifica se si dispone di sincronizzazione delle password hash tra i locali e il tenant di Office 365. |
|**Ultima sincronizzazione delle Password** | Ora ultima esecuzione della sincronizzazione delle password hash. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento di risoluzione dei problemi se l'ultima sincronizzazione risalgono a più di tre giorni fa. |
|**Versione del client di sincronizzazione directory** | Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure Active Directory Connetti. |
|**Strumento IDFix** | Collegamento di download per [lo strumento IDFix](install-and-run-idfix.md), uno strumento è possibile utilizzare per controllare Active Directory locale. |
|**Account del servizio di sincronizzazione directory** | Visualizza il nome dell'account del servizio di sincronizzazione delle directory di Office 365 è. |