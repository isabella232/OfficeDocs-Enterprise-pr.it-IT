---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
ms.openlocfilehash: 03f824da6feb41791e12818d8da2e298dc633f4e
ms.sourcegitcommit: 7814d01db4d7618fc2f9381faef1a6a45ea063fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2019
ms.locfileid: "30492946"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurare la sincronizzazione della directory per Office 365

Office 365 utilizza il servizio di gestione delle identità utente basato sul cloud per gestire gli utenti. È inoltre possibile integrare Active Directory locale con Azure AD sincronizzando l'ambiente locale con Office 365. Dopo aver configurato la sincronizzazione, è possibile decidere di fare in modo che l'autenticazione dell'utente avvenga all'interno di Azure AD o all'interno della directory locale.
  
## <a name="office-365-directory-synchronization"></a>Sincronizzazione della directory di Office 365

È possibile utilizzare l'identità sincronizzata o l'identità federata tra l'organizzazione locale e Office 365. Con l'identità sincronizzata, è possibile gestire gli utenti in locale e vengono autenticati da Azure AD quando utilizzano la stessa password nel cloud come in locale. Questo è lo scenario di sincronizzazione della directory più comune. Autenticazione pass-through o identità federata, consente di gestire gli utenti in locale e vengono autenticati dalla directory locale. L'identità federata richiede una configurazione aggiuntiva e consente agli utenti di accedere solo una volta. Per informazioni dettagliate, vedere [understandIng Office 365 Identity e Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Si desidera eseguire l'aggiornamento da Windows Azure Active Directory Sync (DirSync) ad Azure Active Directory Connect?

Se si sta attualmente utilizzando DirSync e si desidera eseguire l'aggiornamento, passare a [Azure.com](https://azure.com) per [istruzioni sull'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Prerequisiti per Azure AD Connect

È possibile ottenere una sottoscrizione gratuita ad Azure AD con l'abbonamento a Office 365. Quando si configura la sincronizzazione della directory, si installerà Azure Active Directory Connect su uno dei server locali.
  
Per Office 365 sarà necessario:
  
- Verificare il dominio locale (la procedura vi guiderà in questo modo).
- [Assegnare ruoli di amministratore in office 365 per](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) le autorizzazioni aziendali per il tenant di Office 365 e Active Directory locale.

Per il server locale in cui si installa Azure AD Connect, è necessario il software seguente:
  
|**SISTEMA operativo del server**|**Altro software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell è installato per impostazione predefinita, non è necessaria alcuna azione.  <br> -NET 4.5.1 e versioni successive sono disponibili tramite Windows Update. Assicurarsi di aver installato gli aggiornamenti più recenti su Windows Server nel pannello di controllo. |
|**Windows server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012** | -La versione più recente di PowerShell è disponibile in Windows Management Framework 4,0. Cercarlo nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -La versione più recente supportata di PowerShell è disponibile in Windows Management Framework 3,0, disponibile nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Se si utilizza Azure Active Directory DirSync, il numero massimo di membri del gruppo di distribuzione che è possibile sincronizzare da Active Directory locale ad Azure Active Directory è 15.000. Per Azure AD Connect, il numero è 50.000. 
  
Per esaminare più accuratamente i requisiti hardware, software, account e autorizzazioni, i requisiti per i certificati SSL e i limiti degli oggetti per Azure AD Connect, leggere [i prerequisiti per Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).
  
È inoltre possibile esaminare la [cronologia delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure ad Connect versione per vedere cosa è incluso e risolto in ogni versione.

## <a name="to-set-up-directory-synchronization"></a>Per configurare la sincronizzazione della directory

1. accedere all'interfaccia di amministrazione di Office 365 e scegliere **** \> utenti **attivi** per gli utenti sulla barra di spostamento a sinistra.
2. nell'interfaccia di amministrazione di Office 365, nella pagina **utenti attivi** , scegliere **altre** \> **sincronizzazione della Directory**.

    ![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Nella pagina **preparazione di Active Directory** selezionare il collegamento **Scarica Microsoft Azure Active Directory Connect Tool** per iniziare. Per ulteriori informazioni sul processo di installazione di Azure Active Directory Connect, vedere [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Assegnare licenze agli utenti sincronizzati

Dopo aver sincronizzato gli utenti in Office 365, vengono creati ma è necessario assegnare loro le licenze in modo che possano utilizzare le funzionalità di Office 365, ad esempio la posta elettronica. Per istruzioni, vedere [assegnare licenze agli utenti in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Terminare la configurazione dei domini

Seguire la procedura descritta in [create DNS Records for Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare la configurazione dei domini.