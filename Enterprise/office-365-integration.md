---
title: Usare il dominio per integrare la posta elettronica locale, ad esempio, tramite servizi directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Informazioni su come integrare Office 365 con i servizi directory esistenti.
ms.openlocfilehash: 112f543a9c647ea850d5e43bc14483308da0b2c7
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085335"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Usare il dominio per integrare la posta elettronica locale, ad esempio, tramite servizi directory

È possibile integrare Office 365 con i servizi directory esistenti e con un'installazione locale di Exchange Server, Skype for Business Server 2015 o SharePoint Server 2013.
  
 - Quando si esegue l'integrazione con i servizi directory, è possibile sincronizzare e gestire gli account utente per entrambi gli ambienti. È inoltre possibile aggiungere la sincronizzazione hash delle password o Single Sign-on (SSO), in modo che gli utenti possano accedere a entrambi gli ambienti con le credenziali locali.
 - Quando si esegue l'integrazione con i prodotti server locali, si crea un ambiente ibrido. Un ambiente ibrido può essere di aiuto durante la migrazione di utenti o informazioni a Office 365 oppure è possibile continuare ad avere alcuni utenti o alcune informazioni in locale e altre nel cloud. Per ulteriori informazioni sugli ambienti ibridi, vedere [Panoramica di Office 365 Hybrid Cloud Solutions](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

È inoltre possibile utilizzare i consulenti di Azure AD per le indicazioni di installazione personalizzate:
- [Advisor di Azure AD Connect](https://aka.ms/aadconnectpwsync)
- [Advisor per la distribuzione di ADFS](https://aka.ms/adfsguidance)
- [Distribuzione guidata di Azure RMS](https://aka.ms/azuremsguidance)
- [Guida alla configurazione di Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Informazioni preliminari
Prima di integrare Office 365 e un ambiente locale, è inoltre necessario partecipare alla [pianificazione della rete e all'ottimizzazione delle prestazioni per office 365](network-planning-and-performance.md). Sarà inoltre necessario comprendere i [modelli di identità](about-office-365-identity.md) disponibili in Office 365. 

Vedere [dove gestire gli account utente di office 365](manage-office-365-accounts.md) per un elenco di strumenti che è possibile utilizzare per gestire gli account e gli utenti di Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrazione di Office 365 con i servizi directory
Se si dispone di account utente esistenti in una directory locale, non si vuole ricreare tutti gli account in Office 365 e rischiare di introdurre differenze o errori tra gli ambienti. La sincronizzazione della directory consente di rispecchiare gli account tra gli ambienti online e locali. Con la sincronizzazione della directory, gli utenti non devono ricordare nuove informazioni per ogni ambiente e non è necessario creare o aggiornare due volte gli account. Sarà necessario [preparare la directory locale](prepare-for-directory-synchronization.md) per la sincronizzazione della directory, è possibile eseguire questa operazione manualmente o utilizzare lo [strumento IdFix](install-and-run-idfix.md) (lo strumento IdFix funziona solo con Active Directory). 
  
![Utilizzare la sincronizzazione della directory per mantenere sincronizzate le informazioni sugli account utente locali e online](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Se si desidera che gli utenti siano in grado di accedere a Office 365 con le credenziali locali, è anche possibile configurare SSO. Con SSO, Office 365 è configurato per considerare attendibile l'ambiente locale per l'autenticazione degli utenti.
  
![Con Single Sign-on, lo stesso account è disponibile sia negli ambienti locali che in quelli online](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Le diverse tecniche di gestione degli account utente offrono esperienze diverse per gli utenti, come illustrato nella tabella seguente.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Sincronizzazione della directory con o senza la sincronizzazione dell'hash delle password o l'autenticazione pass-through**
Un utente accede all'ambiente locale con il proprio account utente (dominio\nomeutente). Quando si accede a Office 365, è necessario eseguire di nuovo l'accesso con l'account aziendale o dell'Istituto di istruzione (user@domain.com). Il nome utente è lo stesso in entrambi gli ambienti. Quando si aggiunge l'autenticazione hash della password o pass-through, l'utente ha la stessa password per entrambi gli ambienti, ma sarà necessario fornire tali credenziali quando si accede a Office 365. La sincronizzazione della directory con la sincronizzazione hash delle password è lo scenario di sincronizzazione della directory più comunemente utilizzato.

Per configurare la sincronizzazione della directory, utilizzare Azure Active Directory Connect. Per istruzioni, leggere [configurare la sincronizzazione della directory per Office 365](set-up-directory-synchronization.md)e [utilizzare Azure ad Connect con le impostazioni Express](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Per ulteriori informazioni, vedere [preparazione per il provisioning degli utenti tramite la sincronizzazione della directory in Office 365](prepare-for-directory-synchronization.md) e [l'integrazione delle identificazioni locali con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Sincronizzazione della directory con SSO**
Un utente accede all'ambiente locale con il proprio account utente. Quando si accede a Office 365, sono connessi automaticamente oppure eseguono l'accesso utilizzando le stesse credenziali utilizzate per l'ambiente locale (dominio\nomeutente).

Per configurare SSO, è inoltre possibile utilizzare Azure AD Connect. Per istruzioni, leggere [utilizzare Azure ad Connect con impostazioni personalizzate](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Per ulteriori informazioni [, vedere Accesso alle applicazioni e Single Sign-on con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD Connect sostituisce le versioni precedenti degli strumenti di integrazione delle identità, come DirSync e Azure AD Sync. Per ulteriori informazioni, vedere [integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Se si desidera eseguire l'aggiornamento dalla sincronizzazione di Azure Active Directory ad Azure AD Connect, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240). Vedere un'architettura della soluzione creata per la [sincronizzazione della directory di Office 365 (dirsync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).