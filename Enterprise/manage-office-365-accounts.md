---
title: Strumenti per gestire gli account di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: "Informazioni sugli strumenti da utilizzare per la gestione degli utenti di Office 365 e sul modo in cui è possibile utilizzare dipende dalla modalità di gestione delle identità dell'utente. "
ms.openlocfilehash: 0cfb1496dd97eb932afc4e90a6d9469289332c2d
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843717"
---
# <a name="tools-to-manage-office-365-accounts"></a>Strumenti per gestire gli account di Office 365

È possibile gestire gli utenti di Office 365 in diversi modi, a seconda della configurazione. È possibile gestire gli utenti nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com), Windows PowerShell, la directory locale o nel portale di amministrazione di Azure Active Directory. Non appena si acquista Office 365, è possibile utilizzare l'interfaccia di amministrazione e Windows PowerShell per gestire gli account. Quando si gestiscono le identità cloud ogni persona dell'organizzazione dispone di un ID utente e di una password distinti per Office 365. Se si desidera eseguire l'integrazione con l'infrastruttura locale e fare in modo che gli account utente siano sincronizzati con Office 365, è possibile utilizzare Azure Active Directory Connect per fornire la sincronizzazione delle identità e facoltativamente fornire la sincronizzazione delle password o la versione completa funzionalità Single Sign-on.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Pianificare la posizione e la modalità di gestione degli account utente

Il percorso e la modalità di gestione degli account utente dipendono dal modello di identità che si desidera utilizzare per Office 365. I due modelli complessivi sono autenticazione del cloud e autenticazione federata.
  
### <a name="cloud-authentication"></a>Autenticazione del cloud

- Autenticazione cloud: creare e gestire gli utenti nell'interfaccia di amministrazione, è anche possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti. 
    
- Sincronizzazione hash delle password con Single Sign-on senza soluzione di continuità: il modo più semplice per abilitare l'autenticazione per gli oggetti directory locali in Azure AD. Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli oggetti dell'account utente di Active Directory locale con Office 365 e gestire gli utenti in locale. 
    
- Autenticazione pass-through con Single Sign-on senza soluzione di continuità-fornisce una semplice convalida delle password per i servizi di autenticazione di Azure AD utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con il proprio attivo locale Directory. 
    
### <a name="federated-authentication"></a>Autenticazione federata

- Opzioni di autenticazione federata-principalmente per organizzazioni di grandi dimensioni con requisiti di autenticazione più complessi, gli oggetti directory locali vengono sincronizzati con Office 365 e gli account utente vengono gestiti in locale. 
    
- [Autenticazione di terze parti e provider di identità](about-office-365-identity.md) -gli oggetti directory locali possono essere sincronizzati con Office 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti. 
    
## <a name="managing-accounts"></a>Gestione degli account

Quando si decide in che modo l'organizzazione creerà e gestirà gli account, prendere in considerazione quanto segue:
  
- Il software di sincronizzazione della directory deve essere installato nei server all'interno dell'ambiente locale per connettere le identità tra Office 365 e la directory locale.
    
- Qualsiasi opzione di sincronizzazione della directory, incluse le opzioni SSO, richiede che gli attributi di directory locali soddisfino gli standard. Le specifiche di quali attributi vengono utilizzate nella directory e quali operazioni di pulizia (se presenti) sono necessarie sono descritte in [prepararsi a eseguire il provisioning degli utenti tramite la sincronizzazione della directory con Office 365](prepare-for-directory-synchronization.md). Per istruzioni su come utilizzare IdFix per automatizzare la pulizia della directory, vedere [scaricare ed eseguire lo strumento Office 365 IdFix](install-and-run-idfix.md) . 
    
- Pianificare il modo in cui si intende creare gli account di Office 365.
    
    Nella tabella seguente sono elencati i diversi strumenti di gestione degli account.
    
|**Opzione**|**Note**|
|:-----|:-----|
|Interfaccia di amministrazione  <br/> |[Aggiungere gli utenti singolarmente o in blocco a Office 365-Guida per gli amministratori](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Fornisce una semplice interfaccia Web per aggiungere e modificare gli account utente.  <br/>  Non può essere utilizzato per modificare gli utenti se la sincronizzazione della directory è abilitata (è possibile impostare il percorso e l'assegnazione delle licenze).  <br/>  Non può essere utilizzato con le opzioni SSO.  <br/> |
|Windows PowerShell  <br/> |[Gestione di Office 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Consente di aggiungere utenti in blocco tramite uno script di Windows PowerShell.  <br/>  Può essere utilizzato per assegnare posizioni e licenze agli account, indipendentemente dal modo in cui vengono creati gli account.  <br/> |
|Importazione in blocco  <br/> |[Aggiungere più utenti contemporaneamente a Office 365 - Guida per amministratore](add-several-users-at-the-same-time.md) <br/>  Consente di importare un file CSV per aggiungere un gruppo di utenti a Office 365.  <br/>  Non può essere utilizzato con le opzioni SSO.  <br/> |
|Azure Active Directory  <br/> |Si ottiene una versione gratuita di Azure Active Directory con l'abbonamento a Office 365. È possibile eseguire funzioni quali la reimpostazione della password in modalità self-service per gli utenti cloud e la personalizzazione delle pagine di accesso e del riquadro di Access tramite la versione gratuita. Per ottenere funzionalità avanzate, è possibile eseguire l'aggiornamento alla versione di base o all'edizione Premium. Vedere [edizioni di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) per l'elenco delle funzionalità supportate.  <br/> |
|Sincronizzazione della directory  <br/> |[Integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Per la sincronizzazione della directory con o senza la sincronizzazione delle password, utilizzare [Azure ad Connect with Express Settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Per più foreste e opzioni SSO, utilizzare l' [installazione personalizzata di Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Fornisce l'infrastruttura necessaria per abilitare SSO.  <br/>  Necessario per molti scenari ibridi:  <br/>  Migrazione a fasi  <br/>  Exchange ibrido  <br/>  Sincronizza i gruppi di sicurezza e abilitati alla posta elettronica dalla directory locale.  <br/> |
   
- Indipendentemente dal modo in cui si intende aggiungere gli account utente a Office 365, è necessario gestire diverse funzionalità dell'account, ad esempio l'assegnazione di licenze, la specifica del percorso e così via. Queste funzionalità possono essere gestite a lungo termine dall'interfaccia di amministrazione oppure è anche possibile [creare account utente con Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Se si sceglie di aggiungere e gestire tutti gli utenti tramite l'interfaccia di amministrazione, è possibile specificare il percorso e assegnare le licenze contemporaneamente alla creazione dell'account di Office 365. Di conseguenza, non è necessaria una pianificazione eccessiva.
    
    > [!IMPORTANT]
    > La creazione di account in Office 365 senza assegnare una licenza (ad esempio a SharePoint Online) significa che il proprietario dell'account può visualizzare il portale di Office 365 ma non può accedere ad alcuno dei servizi all'interno della sottoscrizione dell'azienda. Dopo aver assegnato un percorso e la licenza, l'account viene replicato nel servizio o nei servizi assegnati. L'utente può accedere al proprio account e utilizzare i servizi assegnati. 
  
## <a name="next-steps"></a>Passaggi successivi

[Integrazione di Office 365 con ambienti locali](office-365-integration.md)
  
## <a name="see-also"></a>Vedere anche

[Gestire gli account utente in Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

