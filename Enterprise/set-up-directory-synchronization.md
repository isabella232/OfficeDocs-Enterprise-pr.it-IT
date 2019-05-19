---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162479"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurare la sincronizzazione della directory per Office 365

Office 365 utilizza un tenant di Azure Active Directory (Azure AD) per l'archiviazione e la gestione delle identità per l'autenticazione e le autorizzazioni per l'accesso alle risorse basate su cloud. 

Se si dispone di servizi di dominio Active Directory (AD DS) locali, è possibile sincronizzare gli account utente, i gruppi e i contatti di AD DS con il tenant di Azure AD della sottoscrizione di Office 365. Si tratta dell'identità ibrida per Office 365. Di seguito vengono ripartiti i componenti.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect viene eseguito su un server locale e sincronizza i servizi di dominio Active Directory con il tenant di Azure AD. Insieme alla sincronizzazione della directory, è anche possibile specificare queste opzioni di autenticazione:

- Sincronizzazione degli hash delle password (pH)

  Azure AD esegue l'autenticazione stessa.

- Autenticazione pass-through

  Azure AD ha servizi di dominio Active Directory per eseguire l'autenticazione.

- Autenticazione federata

  Azure AD reindirizza il computer client che richiede l'autenticazione per contattare un altro provider di identità.

Per ulteriori informazioni, vedere [identità ibride](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. rivedere i prerequisiti per Azure AD Connect

È possibile ottenere una sottoscrizione gratuita AD Azure AD con l'abbonamento a Office 365. Quando si configura la sincronizzazione della directory, si installerà Azure AD Connect su uno dei server locali.
  
Per Office 365 è necessario:
  
- Verificare il dominio locale. Nella procedura guidata di Azure AD Connect è possibile eseguire questa operazione.
- Ottenere i nomi utente e le password per gli account di amministrazione del tenant di Office 365 e servizi di dominio Active Directory.

Per il server locale in cui si installa Azure AD Connect, è necessario quanto segue:
  
|**Sistema operativo del server**|**Altro software**|
|:-----|:-----|
|Windows Server 2012 R2 e versioni successive | -PowerShell è installato per impostazione predefinita, non è necessaria alcuna azione.  <br> -NET 4.5.1 e versioni successive sono disponibili tramite Windows Update. Assicurarsi di aver installato gli aggiornamenti più recenti su Windows Server nel pannello di controllo. |
|Windows Server 2008 R2 con Service Pack 1 (SP1) * * o Windows Server 2012 | -La versione più recente di PowerShell è disponibile in Windows Management Framework 4,0. Cercarlo nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | -La versione più recente supportata di PowerShell è disponibile in Windows Management Framework 3,0, disponibile nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Per informazioni dettagliate sui requisiti hardware, software, account e autorizzazioni, sui requisiti dei certificati SSL e sui limiti degli oggetti per Azure AD Connect, vedere [prerequisiti per Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) .
  
È inoltre possibile esaminare la [cronologia delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure ad Connect versione per vedere cosa è incluso e risolto in ogni versione.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. installare Azure AD Connect e configurare la sincronizzazione della directory

Prima di iniziare, verificare di disporre di:

- Il nome utente e la password di un amministratore globale di Office 365
- Il nome utente e la password di un amministratore di dominio AD DS
- Quale metodo di autenticazione (pH, PTA, federato)
- Se si desidera utilizzare l' [accesso Single Sign-on (SSO) di Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Eseguire la procedura seguente:

1. Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e scegliere **gli** \> utenti **attivi** degli utenti sulla barra di spostamento a sinistra.
2. Nell'interfaccia di amministrazione, nella pagina **utenti attivi** , scegliere **altre** \> **sincronizzazione della directory**.

    ![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Nella pagina **preparazione di Active Directory** selezionare il collegamento **Scarica Microsoft Azure Active Directory Connect Tool** per iniziare. 
4. Seguire la procedura descritta in [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. terminare la configurazione dei domini

Seguire la procedura descritta in [create DNS Records for Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare la configurazione dei domini.

## <a name="next-step"></a>Passaggio successivo

[Assegnare le licenze agli account utente](assign-licenses-to-user-accounts.md).
