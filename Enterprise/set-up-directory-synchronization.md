---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Informazioni su come configurare la sincronizzazione della directory tra Office 365 e Active Directory locale.
ms.openlocfilehash: 5cd56eb90e6421d530ff0c2b8739bd13be238eae
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814594"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurare la sincronizzazione della directory per Office 365

*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.

Office 365 usa un tenant di Azure Active Directory (Azure AD) per archiviare e gestire le identità per l'autenticazione e le autorizzazioni per accedere alle risorse basate sul cloud. 

Se si usa Active Directory Domain Services (AD DS), è possibile sincronizzare gli account utente, i gruppi e i contatti di Active Directory con il tenant di Azure AD dell'abbonamento a Office 365. Questa corrisponde all'identità ibrida per Office 365, i cui componenti sono descritti di seguito.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect viene eseguito in un server locale e consente di sincronizzare il servizio AD DS con il tenant di Azure AD. Oltre alla sincronizzazione della directory, è anche possibile specificare le opzioni di autenticazione seguenti:

- Sincronizzazione dell'hash delle password (PHS)

  L'autenticazione viene eseguita direttamente da Azure AD.

- Autenticazione pass-through (PTA)

  L'autenticazione di Azure AD viene eseguita da AD DS.

- Autenticazione federata

  Azure AD reindirizza il computer client richiedendo l'autenticazione per contattare un altro provider di identità.

Per altre informazioni, vedere [Identità ibride](plan-for-directory-synchronization.md).
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Esaminare i prerequisiti per Azure AD Connect

Con l'abbonamento a Office 365 è inclusa una sottoscrizione gratuita di Azure AD. Quando si configura la sincronizzazione della directory, si installa Azure AD Connect in uno dei server locali.
  
Per Office 365 è necessario:
  
- Verificare il dominio locale. La procedura guidata di Azure AD Connect illustra i passaggi necessari per questa operazione.
- Ottenere i nomi utente e le password per gli account di amministrazione del tenant di Office 365 e di AD DS.

Per il server locale in cui si installa Azure AD Connect, sono necessari:
  
|**Sistema operativo server**|**Altro software**|
|:-----|:-----|
|Windows Server 2012 R2 e versioni successive | - PowerShell viene installato per impostazione predefinita, pertanto non è richiesta alcuna azione.  <br> - .NET 4.5.1 e versioni successive sono disponibili tramite Windows Update. Assicurarsi di aver installato gli aggiornamenti più recenti di Windows Server nel Pannello di controllo. |
|Windows Server 2008 R2 con Service Pack 1 (SP1)** o Windows Server 2012 | - La versione più recente di PowerShell è disponibile in Windows Management Framework 4.0. Cercarla nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | - La versione supportata più recente di PowerShell è disponibile in Windows Management Framework 3.0, scaricabile dall'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Per informazioni dettagliate sui requisiti hardware, software, per account e autorizzazioni e certificati SSL e sui limiti degli oggetti per Azure AD Connect, vedere [Prerequisiti di Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).
  
È anche possibile esaminare la [cronologia di rilascio delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure AD Connect per vedere cosa include e quali problemi sono stati risolti in ogni versione.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installare Azure AD Connect e configurare la sincronizzazione della directory

Prima di iniziare, eseguire le operazioni seguenti:

- Assicurarsi di disporre del nome utente e della password di un amministratore globale di Office 365
- Assicurarsi di disporre del nome utente e della password di un amministratore del dominio di AD DS
- Scegliere il metodo di autenticazione, tra PHS, PTA e federata
- Indicare se si intende usare [Accesso Single Sign-On facile di Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Eseguire la procedura seguente:

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e scegliere **Utenti** \> **Utenti attivi** nel riquadro di spostamento sinistro.
2. Nella pagina **utenti attivi** , scegliere **altro** (tre punti) \> **sincronizzazione della directory**.
  
3. Nella pagina **preparazione di Azure Active Directory** selezionare l' **area download per ottenere il collegamento dello strumento Azure ad Connect** per iniziare. 
4. Seguire la procedura in [Roadmap di installazione di Azure AD Connect e Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Completare la configurazione dei domini

Seguire la procedura descritta in [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) per completare la configurazione dei domini.

## <a name="next-step"></a>Passaggio successivo

[Assegnare licenze agli account utente](assign-licenses-to-user-accounts.md).
