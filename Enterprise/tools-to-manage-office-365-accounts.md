---
title: Strumenti per gestire gli account di Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
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
description: "Informazioni sugli strumenti da utilizzare per gestire gli utenti di Microsoft 365 e sul modo in cui è possibile utilizzare la gestione delle identità dell'utente. "
ms.openlocfilehash: c382006fe8cb46342548b7533148e760c103bf50
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906218"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>Strumenti per gestire gli account di Microsoft 365

È possibile gestire gli utenti di Microsoft 365 in vari modi, a seconda della configurazione. È possibile gestire gli utenti nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com), Windows PowerShell, la directory locale o nel portale di amministrazione di Azure Active Directory.

Non appena si acquista Microsoft 365, è possibile utilizzare l'interfaccia di amministrazione e Windows PowerShell per gestire gli account. Quando si gestiscono le identità cloud ogni persona dell'organizzazione dispone di un ID utente e di una password distinti per Microsoft 365. Se si desidera eseguire l'integrazione con l'infrastruttura locale e gli account utente vengono sincronizzati con Microsoft 365, è possibile utilizzare Azure Active Directory Connect per fornire la sincronizzazione delle identità e facoltativamente fornire la sincronizzazione delle password o la funzionalità Single Sign-on completa.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Pianificare la posizione e la modalità di gestione degli account utente

Il percorso e la modalità di gestione degli account utente dipendono dal modello di identità che si desidera utilizzare per l'abbonamento a Microsoft 365. I due modelli complessivi sono autenticazione del cloud e autenticazione federata.
  
### <a name="cloud-authentication"></a>Autenticazione del cloud

- [Microsoft 365 Identity](about-office-365-identity.md) -creare e gestire gli utenti nell'interfaccia di amministrazione, è anche possibile utilizzare Windows PowerShell o Azure Active Directory per gestire gli utenti.
- [Sincronizzazione hash delle password con Single Sign-on senza soluzione di continuità](about-office-365-identity.md) : il modo più semplice per abilitare l'autenticazione per gli oggetti directory locali in Azure ad. Con la sincronizzazione degli hash delle password (pH), è possibile sincronizzare gli oggetti dell'account utente di Active Directory locale con Microsoft 365 e gestire gli utenti in locale. 
- [Autenticazione pass-through con Single Sign-on senza soluzione di continuità](about-office-365-identity.md) -fornisce una semplice convalida delle password per i servizi di autenticazione di Azure ad utilizzando un agente software in esecuzione su uno o più server locali per convalidare gli utenti direttamente con Active Directory locale. 

### <a name="federated-authentication"></a>Autenticazione federata

- [Identità microsoft 365](about-office-365-identity.md) -principalmente per organizzazioni di grandi dimensioni con requisiti di autenticazione più complessi, gli oggetti directory locali vengono sincronizzati con Microsoft 365 e gli account utente vengono gestiti in locale. 
- [Autenticazione di terze parti e provider di identità](about-office-365-identity.md) -gli oggetti directory locali possono essere sincronizzati con Microsoft 365 e l'accesso alle risorse cloud è gestito principalmente da un provider di identità di terze parti. 

## <a name="managing-accounts"></a>Gestione degli account

Quando si decide in che modo l'organizzazione creerà e gestirà gli account, prendere in considerazione quanto segue:
  
- Il software di sincronizzazione della directory deve essere installato nei server all'interno dell'ambiente locale per connettere le identità tra Microsoft 365 e la directory locale.
- Qualsiasi opzione di sincronizzazione della directory, incluse le opzioni SSO, richiede che gli attributi di directory locali soddisfino gli standard. Le specifiche di quali attributi vengono utilizzate nella directory e quali operazioni di pulizia (se presenti) sono necessarie sono descritte in [Prepare to provisioning users through Directory Synchronization to Microsoft 365](prepare-for-directory-synchronization.md). Per informazioni su come utilizzare IdFix per automatizzare la pulizia della directory, vedere [scaricare ed eseguire lo strumento Microsoft 365 IdFix](install-and-run-idfix.md) . 

## <a name="plan-how-you-are-going-to-create-microsoft-365-accounts"></a>Pianificare la modalità di creazione di account Microsoft 365

Nella tabella seguente sono elencati i diversi strumenti di gestione degli account:

|**Opzione**|**Note**|
|:-----|:-----|
|**Interfaccia di amministrazione** | - [Aggiungere gli utenti singolarmente o in blocco a Microsoft 365-Guida per gli amministratori](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br> -Fornisce una semplice interfaccia Web per aggiungere e modificare gli account utente. <br> -Non può essere utilizzato per modificare gli utenti se la sincronizzazione della directory è abilitata (è possibile impostare il percorso e l'assegnazione delle licenze). <br> -Non può essere utilizzato con le opzioni SSO. <br> |
|**Windows PowerShell** | - [Gestire Microsoft 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br> -Consente di aggiungere utenti in blocco tramite uno script di Windows PowerShell. <br> -Può essere utilizzato per assegnare posizioni e licenze agli account, indipendentemente dal modo in cui vengono creati gli account. <br> |
|**Importazione in blocco** | - [Aggiungere più utenti contemporaneamente a Microsoft 365-Guida per gli amministratori](add-several-users-at-the-same-time.md) <br> -Consente di importare un file CSV per aggiungere un gruppo di utenti a Microsoft 365. <br> -Non può essere utilizzato con le opzioni SSO. <br> |
|**Azure Active Directory** | -Si ottiene una versione gratuita di Azure Active Directory con l'abbonamento a Microsoft 365. -È possibile eseguire funzioni quali la reimpostazione della password in modalità self-service per gli utenti cloud e la personalizzazione delle pagine di accesso e del riquadro di Access tramite la versione gratuita. <br> -Per ottenere funzionalità avanzate, è possibile eseguire l'aggiornamento a base Edition o all'edizione Premium. Vedere [edizioni di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) per l'elenco delle funzionalità supportate. <br> |
|**Sincronizzazione della directory** | - [Integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br> -Per la sincronizzazione della directory con o senza sincronizzazione delle password, utilizzare [Azure ad Connect con le impostazioni Express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br>  -Per più foreste e opzioni SSO, utilizzare l' [installazione personalizzata di Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430). <br> -Fornisce l'infrastruttura necessaria per abilitare SSO. <br> -Obbligatorio per molti scenari ibridi (migrazione in fasi, Exchange ibrido) <br> -Sincronizza la sicurezza e i gruppi abilitati alla posta elettronica dalla directory locale. <br> |

Indipendentemente dal modo in cui si intende aggiungere gli account utente a Microsoft 365, è necessario gestire diverse funzionalità dell'account, ad esempio l'assegnazione di licenze, la specifica del percorso e così via. Queste funzionalità possono essere gestite a lungo termine dall'interfaccia di amministrazione oppure è anche possibile [creare account utente con Microsoft 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).

Se si sceglie di aggiungere e gestire tutti gli utenti tramite l'interfaccia di amministrazione, è possibile specificare il percorso e assegnare le licenze contemporaneamente alla creazione dell'account Microsoft 365. Di conseguenza, non è necessaria una pianificazione eccessiva.

> [!IMPORTANT]
> La creazione di account in Microsoft 365 senza assegnare una licenza (ad esempio a SharePoint Online) significa che il proprietario dell'account può visualizzare l'interfaccia di amministrazione di Microsoft 365 ma non è in grado di accedere ad alcuno dei servizi all'interno della sottoscrizione dell'azienda. Dopo aver assegnato un percorso e la licenza, l'account viene replicato nel servizio o nei servizi assegnati. L'utente può accedere al proprio account e utilizzare i servizi assegnati.