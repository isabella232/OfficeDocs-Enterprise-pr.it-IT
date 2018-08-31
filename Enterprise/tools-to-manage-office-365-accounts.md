---
title: Strumenti per gestire gli account di Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Informazioni su quali sono gli strumenti da utilizzare per gestire gli utenti di Office 365 e in che modo è possibile utilizzare dipende sulla gestione delle identità utente. '
ms.openlocfilehash: 62467fb031090a521d0b9e067582b56fabe9e5fd
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541184"
---
# <a name="tools-to-manage-office-365-accounts"></a>Strumenti per gestire gli account di Office 365

È possibile gestire gli utenti di Office 365 in diversi modi, a seconda della configurazione. È possibile gestire gli utenti in Office 365 interfaccia di amministrazione di Windows PowerShell, la directory locale, o nel portale di amministrazione di Azure Active Directory. 

Non appena si acquistare Office 365, l'interfaccia di amministrazione e Windows PowerShell utilizzabile per gestire gli account. Durante la gestione delle identità cloud tutte le persone all'interno dell'organizzazione hanno un ID utente separate e una password per Office 365. Se si desidera integrare con l'infrastruttura locale e dispongono di account utente sincronizzato con Office 365, è possibile utilizzare la connessione di Azure Active Directory per la sincronizzazione delle identità e se lo si desidera fornire la sincronizzazione delle password o completa funzionalità Single sign-on.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Pianificare dove e come gestire gli account utente

Dove e come è possibile gestire gli account utente dipende dal modello di identità da utilizzare per Office 365. I due modelli globali sono cloud autenticazione e l'autenticazione federata.
  
### <a name="cloud-authentication"></a>Autenticazione cloud

<<<<<<< HEAD
- [Autenticazione cloud](about-office-365-identity.md#cloud-authentication) - creare e gestire gli utenti nell'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti. 
    
=======
- [Office 365 identità](about-office-365-identity.md) - creare e gestire gli utenti nell'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti.
>>>>>>> conversione robmazz
- [Sincronizzare il valore hash password con single sign-on agevole](about-office-365-identity.md) - il modo più semplice per abilitare l'autenticazione per gli oggetti directory locale in Azure Active Directory. Con sincronizzazione delle hash password (PHS), sincronizzare gli oggetti di account utente di Active Directory locale con Office 365 e gestire gli utenti locale. 
- [Autenticazione pass-through con single sign-on agevole](about-office-365-identity.md) - fornisce una convalida password semplice per i servizi di autenticazione Azure AD utilizzando un agente di software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con i Active Directory locale. 
    
### <a name="federated-authentication"></a>Autenticazione federata

<<<<<<< HEAD
- [Autenticazione pass-through con single sign-on agevole](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on) - principalmente per le organizzazioni di grandi imprese con requisiti di autenticazione più complessi, locali oggetti directory sono sincronizzati con Office 365 e gestiti gli account utente in locale. 
    
=======
- [Office 365 identità](about-office-365-identity.md) - principalmente per le organizzazioni di grandi imprese con requisiti di autenticazione più complessi, locale oggetti directory sono sincronizzati con Office 365 e gli account utente sono gestiti in locale. 
>>>>>>> conversione robmazz
- [Provider di autenticazione e identità di terze parti](about-office-365-identity.md) -nella directory locale oggetti possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud principalmente gestito da un provider di identità di terze parti (IdP). 
    
## <a name="managing-accounts"></a>Gestione degli account

Prima di decidere quale modo in cui l'organizzazione verrà creare e gestire gli account, considerare quanto segue:
  
- Il software di sincronizzazione della directory deve essere installato nei server all'interno dell'ambiente locale per connettere le identità tra Office 365 e le directory locale.
- Qualsiasi opzione di sincronizzazione della directory, incluse le opzioni SSO, è necessario che soddisfino agli attributi di directory locale. Vengono descritte le specifiche per gli attributi utilizzati nella directory e quali pulitura (se esistenti) è necessario in [Prepare to provision utenti mediante la sincronizzazione delle directory per Office 365](prepare-for-directory-synchronization.md). Per istruzioni su come utilizzare lo strumento IdFix per automatizzare la pulitura directory, vedere [installare ed eseguire lo strumento IdFix di Office 365](install-and-run-idfix.md) . 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a>Pianificare come si intende creare gli account di Office 365
Nella tabella seguente sono elencati gli strumenti di gestione account diversi:
    
|**Opzione**|**Note**|
|:-----|:-----|
|**interfaccia di amministrazione di Office 365** | - [Aggiungere utenti singolarmente o in massa a Office 365 - della Guida di amministrazione](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -Fornisce un'interfaccia web semplice per aggiungere e modificare gli account utente. <br> -Non può essere utilizzato per modificare gli utenti se la sincronizzazione delle directory è abilitata (può essere impostato posizione e assegnazione di licenze). <br> -Non può essere utilizzato con le opzioni SSO. <br> |
|**Windows PowerShell** | - [Gestione di Office 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Consente di aggiungere gli utenti in utenti in blocco tramite uno script di Windows PowerShell. <br> -Può essere utilizzato per assegnare posizione e licenze agli account, indipendentemente dalla modalità di creazione di account. <br> |
|**Importazione in blocco** | - [Aggiungere più utenti contemporaneamente a Office 365 - della Guida di amministrazione](add-several-users-at-the-same-time.md) <br> -Consente di importare un file CSV per aggiungere un gruppo di utenti a Office 365. <br> -Non può essere utilizzato con le opzioni SSO. <br> |
|**Azure Active Directory** | -Viene generata una versione gratuita di Azure Active Directory con la sottoscrizione a Office 365. -È possibile eseguire funzioni come self-service la reimpostazione della password per gli utenti di cloud e la personalizzazione delle pagine di accesso e Pannello di accesso utilizzando l'edizione libero.<br> -Per ottenere maggiori funzionalità, è possibile aggiornare l'edizione di base o l'edizione premium. Per l'elenco delle caratteristiche supportate, vedere [le edizioni di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) .<br> |
|**Sincronizzazione della directory** | - [Le identità locale l'integrazione con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -Sincronizzazione della directory con o senza la sincronizzazione delle password, utilizzare la [connessione AD Azure con impostazioni express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br>  -Per più foreste e le opzioni SSO, utilizzare la [connessione AD installazione personalizzata di Azure](https://go.microsoft.com/fwlink/p/?LinkId=698430). <br> -Fornisce l'infrastruttura necessaria abilitare SSO. <br> -Obbligatorio per molti scenari ibridi (migrazione in fasi, distribuzione ibrida di Exchange) <br> -Sincronizza i gruppi di sicurezza e abilitati alla posta elettronica dalla directory locale. <br> |
   
Indipendentemente dal modo si intende aggiungere gli account utente a Office 365, è necessario gestire molte funzionalità di account, ad esempio assegnazione delle licenze, che specifica la posizione e così via. Tali caratteristiche possono essere gestite a lungo termine dall'interfaccia di amministrazione di Office 365 o è inoltre possibile [creare account utente con Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
Se si sceglie di aggiungere e gestire tutti gli utenti tramite l'interfaccia di amministrazione di Office 365, si verrà specificare il percorso e assegnare licenze contemporaneamente come la creazione dell'account di Office 365. Di conseguenza, è necessaria non quantità di pianificazione.
    
> [!IMPORTANT]
> Creazione di account in Office 365 senza assegnazione di una licenza (per SharePoint Online, ad esempio) significa che il proprietario dell'account può visualizzare lo, ma il portale Office 365 non possono accedere a tutti i servizi all'interno di sottoscrizione della società. Dopo aver assegnato un percorso e la licenza, l'account viene replicato i servizi che è assegnato. L'utente può accedere al proprio account e utilizzare i servizi assegnati a loro.