---
title: Integrazione di Office 365 con ambienti locali
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
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Informazioni su come effettuare l'integrazione di Office 365 con i servizi di directory esistenti.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541278"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Integrazione di Office 365 con ambienti locali

È possibile integrare Office 365 con i servizi di directory esistenti e di un'installazione locale di Exchange Server, Skype per Business Server 2015 o SharePoint Server 2013.
  
 - Quando si integra con i servizi directory, è possibile sincronizzare e gestione degli account utente per entrambi gli ambienti. È inoltre possibile aggiungere la sincronizzazione delle password hash o single sign-on (SSO) in modo che gli utenti possono accedere a entrambi gli ambienti con le credenziali locali.
 - Quando si integra con i prodotti server locale, si crea un ambiente ibrido. Di eseguire la migrazione degli utenti o le informazioni per Office 365 oppure è possibile continuare a sono alcuni utenti o alcune informazioni locali e alcuni nel cloud può aiutare a un ambiente ibrido. Per ulteriori informazioni sugli ambienti ibridi, vedere [Cenni preliminari sulle soluzioni di Office 365 ibrida cloud](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

È inoltre possibile utilizzare i consulenti Azure Active Directory per istruzioni di installazione personalizzata:
- [Azure Active Directory Connetti advisor](https://aka.ms/aadconnectpwsync)
- [Preparazione di Active Directory FS distribuzione](https://aka.ms/adfsguidance)
- [Distribuzione guidata di RMS Azure](https://aka.ms/azuremsguidance)
- [Istruzioni di installazione Azure Active Directory Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Informazioni preliminari
Prima di integrare un ambiente locale e Office 365, è necessario anche partecipare alla [pianificazione della rete e ottimizzazione delle prestazioni per Office 365](network-planning-and-performance.md). È inoltre possibile acquisire familiarità con i [modelli di identità](about-office-365-identity.md) disponibili in Office 365. 

Vedere [dove per gestire Office 365 utente account](manage-office-365-accounts.md) per un elenco di strumenti che utilizzabili per gestire gli account e gli utenti di Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrazione di Office 365 con servizi directory
Se si dispone di account utente esistenti in una directory locale, non si desidera ricreare tutti gli account in Office 365 e dei rischi introduzione differenze o errori tra gli ambienti. La sincronizzazione delle directory consente di eseguire il mirroring tali account tra la linea e ambienti locali. Con la sincronizzazione delle directory, gli utenti non sono necessario ricordare le nuove informazioni per ogni ambiente e non è necessario creare o aggiornare gli account di due volte. È necessario per la [Preparazione della directory locale](prepare-for-directory-synchronization.md) per la sincronizzazione delle directory, è possibile eseguire questa operazione manualmente o utilizzare lo [strumento IdFix](install-and-run-idfix.md) (IdFix tool funziona solo con Active Directory). 
  
![Utilizzare la sincronizzazione delle directory per mantenere sincronizzate le informazioni account utente in linea e locale](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Se si desidera che gli utenti siano in grado di accedere a Office 365 con le proprie credenziali in locale, è inoltre possibile configurare SSO. Con funzionalità SSO, in Office 365 è configurato per considerare attendibile l'ambiente locale per l'autenticazione degli utenti.
  
![Con single sign-on, è disponibile in ambienti online e locale lo stesso account utente](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Tecniche di gestione account utente diverso offrono un'esperienza diversa per gli utenti, come illustrato nella tabella seguente.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Sincronizzazione della directory con o senza hash sincronizzazione o pass-through l'autenticazione tramite password**
Un utente accede al proprio ambiente locale con l'account utente (DOMINIO\nome utente). Quando accedono a Office 365, è necessario accedere nuovamente con il proprio account di lavoro o della scuola (user@domain.com). Il nome utente è la stessa in entrambi gli ambienti. Quando si aggiunta sincronizzazione delle password hash o autenticazione pass-through, l'utente ha la stessa password per entrambi gli ambienti, ma sarà necessario fornire nuovamente le credenziali per l'accesso a Office 365. Sincronizzazione della directory con sincronizzazione delle password hash è lo scenario di sincronizzazione directory più comunemente utilizzate.

Per configurare la sincronizzazione delle directory, utilizzare la connessione di Azure Active Directory. Per ulteriori informazioni, leggere [Configura la sincronizzazione delle directory per Office 365](set-up-directory-synchronization.md)e [Azure utilizza Active Directory Connetti con impostazioni express](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Ulteriori informazioni sulla [Preparazione per il provisioning degli utenti tramite la sincronizzazione delle directory per Office 365](prepare-for-directory-synchronization.md) e [sull'integrazione di identificare con Azure Active Directory locale](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Sincronizzazione della directory con SSO**
Un utente accede al proprio ambiente locale con l'account utente. Quando accedono a Office 365, sono costituiti connessi automaticamente o accedono con le stesse credenziali utilizzati per l'ambiente locale (dominio\nomeutente).

Per impostare SSO è inoltre possibile utilizzare Connect Azure Active Directory. Per ulteriori informazioni, leggere [utilizzo Azure Active Directory Connetti con impostazioni personalizzate](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Ulteriori informazioni [sull'accesso alle applicazioni e single sign-on con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure Active Directory Connetti sostituisce le versioni precedenti di strumenti di integrazione di identità, ad esempio DirSync e sincronizzazione di Azure Active Directory. Per ulteriori informazioni, vedere [integrazione le identità in locale con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Se si desidera aggiornare di sincronizzazione di Azure Active Directory Connetti Azure Active Directory, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240). Vedere un'architettura di soluzioni creata per [Office 365 la sincronizzazione delle Directory (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).