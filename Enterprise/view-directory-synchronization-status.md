---
title: Visualizzare lo stato della sincronizzazione della directory in Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Informazioni su come disattivare la sincronizzazione della directory. È anche possibile visualizzarne lo stato.
ms.openlocfilehash: 74e2eee0086e4f8098221f4aaa30d408091a6a0f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840983"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Visualizzare lo stato della sincronizzazione della directory in Office 365

Se è stata integrata Active Directory locale con Azure AD sincronizzando l'ambiente locale con Office 365, è anche possibile controllare lo stato della sincronizzazione.
  
## <a name="view-directory-synchronization-status"></a>Visualizzare lo stato della sincronizzazione della directory

- Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) e scegliere **stato dirsync** nella Home page.
- In \> alternativa, è possibile accedere agli utenti **attivi** **degli utenti** , quindi nella pagina **utenti attivi** scegliere **altre** \> **sincronizzazione della directory**. Nel riquadro di **sincronizzazione della directory** scegliere **Vai a gestione dirsync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Informazioni sulla pagina Gestisci sincronizzazione directory

Nella tabella seguente sono elencate le funzionalità che consentono di ottenere informazioni sulla pagina.
  
Se si verifica un problema con la sincronizzazione della directory, anche gli errori sono elencati in questa pagina. Per ulteriori informazioni sui diversi errori che potrebbero verificarsi, vedere [identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).
  
|**Elemento**|**Scopo**|
|:-----|:-----|
|**Domini verificati** | Numero di domini del tenant di Office 365 che sono stati verificati. |
|**Domini non verificati** | Domini che sono stati aggiunti, ma non sono stati verificati. |
|**Sincronizzazione della directory attivata** |True o false. Specifica se è stata abilitata la sincronizzazione della directory. |
|**Sincronizzazione della directory più recente** | Ultima esecuzione della sincronizzazione della directory. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa. |
|**Sincronizzazione password attivata** | True o false. Specifica se si dispone della sincronizzazione hash della password tra il tenant locale e quello Office 365. |
|**Sincronizzazione ultima password** | L'ultima volta che è stata eseguita la sincronizzazione hash password. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa. |
|**Versione client di sincronizzazione della directory** | Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure AD Connect. |
|**Strumento IDFix** | Scaricare il collegamento a [IDFix](install-and-run-idfix.md), uno strumento che è possibile utilizzare per verificare l'utilizzo di Active Directory locale. |
|**Account del servizio di sincronizzazione della directory** | Visualizza il nome dell'account del servizio di sincronizzazione della directory di Office 365. |