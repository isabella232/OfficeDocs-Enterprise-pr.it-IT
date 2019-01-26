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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Informazioni su come configurare la sincronizzazione delle directory tra Office 365 e Active Directory locale.
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555442"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurare la sincronizzazione della directory per Office 365

Office 365 utilizza il servizio di gestione delle identità utente basata su cloud Azure Active Directory per gestire gli utenti. È inoltre possibile integrare Active Directory locale con Azure Active Directory da sincronizzare l'ambiente locale con Office 365. Dopo avere impostato la sincronizzazione è possibile avere loro l'autenticazione degli utenti venga eseguita all'interno di Azure Active Directory o la directory locale.
  
## <a name="office-365-directory-synchronization"></a>Sincronizzazione delle directory di Office 365

È possibile utilizzare identità sincronizzati o identità federata tra l'organizzazione locale e Office 365. Con identità sincronizzati, per gestire gli utenti locale e vengono autenticati per Azure Active Directory quando si utilizza la stessa password nel cloud come locale. Questo è lo scenario di sincronizzazione della directory più comune. Autenticazione pass-through o l'identità federate, consente di gestire i propri utenti locali e vengono autenticati dalla directory locale. Identità federata richiede configurazioni aggiuntive e consente agli utenti per l'accesso solo una volta. Per ulteriori informazioni, leggere [Understanding Office 365 identità e Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Eseguire l'aggiornamento da sincronizzazione di Windows Azure Active Directory (DirSync) per la connessione di Azure Active Directory?

Se si stanno attualmente utilizzando DirSync e si desidera aggiornare, visitare in anche [azure.com](https://azure.com) per [le istruzioni di aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Connettono i prerequisiti per Azure Active Directory

Viene visualizzato un abbonamento gratuito per Azure Active Directory con la sottoscrizione a Office 365. Quando si imposta la sincronizzazione delle directory, si installerà la connessione di Azure Active Directory in uno dei server locale.
  
Per Office 365 è necessario:
  
- Verificare il dominio locale (la procedura viene illustrato come tramite questo).
- Disporre delle autorizzazioni di [assegnazione dei ruoli di amministratore in Office 365 per aziende](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) per il tenant di Office 365 e Active Directory locale.

Per il server locale in cui si installa Connetti Azure Active Directory sono necessari i componenti software seguenti:
  
|**Sistema operativo server**|**Altro software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell viene installato per impostazione predefinita, è necessaria alcuna azione.  <br> -Net 4.5.1 e versioni successive offerte tramite Windows Update. Assicurarsi che siano installati gli aggiornamenti più recenti per Windows Server nel Pannello di controllo. |
|**Windows Server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012** | -La versione più recente di PowerShell è disponibile in Windows Management Framework 4.0. Effettuare una ricerca [nell'Area Download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -Sono disponibili in [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).net 4.5.1 e versioni successive. |
|**Windows Server 2008** | -La versione supportata più recente di PowerShell è disponibile in Windows Management Framework 3.0, disponibile [nell'Area Download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -Sono disponibili in [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).net 4.5.1 e versioni successive. |

> [!NOTE]
> Se si sta utilizzando Azure Active Directory DirSync, il numero massimo di membri del gruppo di distribuzione che è possibile sincronizzare da Active Directory locale per Azure Active Directory è 15.000. Per Azure Active Directory Connect, tale numero è 50.000. 
  
Per controllare più attentamente hardware, software, account e requisiti delle autorizzazioni, requisiti dei certificati SSL e limiti di oggetto di Azure Active Directory Connect, leggeranno [i prerequisiti per la connessione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
È anche possibile esaminare il Azure Active Directory Connect [versione cronologia delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) per vedere che cos'è incluso e risolti in ogni versione.

## <a name="to-set-up-directory-synchronization"></a>Per configurare la sincronizzazione delle directory

1. Accedere all'interfaccia di amministrazione di Office 365 e fare clic su **utenti** \> **Utenti attivi** nel riquadro di spostamento sinistro.
2. Nell'interfaccia di amministrazione di Office 365, nella pagina **utenti attivi** , scegliere **ulteriori** \> **la sincronizzazione delle Directory**.

    ![Nel menu di più, scegliere la sincronizzazione delle Directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Nella pagina **Preparazione di Active Directory** , selezionare il collegamento di **Download Microsoft Azure Active Directory connessione dello strumento** per iniziare. Per ulteriori informazioni sul processo di installazione di connettere Azure Active Directory, vedere [roadmap di installazione di Active Directory Connect e Azure Active Directory connettersi integrità Azure](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Assegnare licenze agli utenti sincronizzati

Dopo aver sincronizzato agli utenti di Office 365, in cui vengono creati, ma è necessario assegnare licenze ad essi in modo che utilizzino le funzionalità di Office 365, ad esempio posta. Per ulteriori informazioni, vedere [assegnare licenze agli utenti di Office 365 per aziende](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Completare l'impostazione domini

Seguire i passaggi della [creazione di record DNS per Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare l'installazione i domini.