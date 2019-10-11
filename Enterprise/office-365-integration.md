---
title: Integrazione di Office 365 con ambienti locali
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
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
ms.openlocfilehash: f6e29207dfb1175df8af480942484ece39e249b7
ms.sourcegitcommit: 2e6fadb5b2b16619ad141b6293d3466460720cb4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "37428121"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Integrazione di Office 365 con ambienti locali

*Questo articolo si applica a Office 365 Enterprise e Microsoft 365 Enterprise*

È possibile integrare Office 365 con i servizi directory esistenti e con un'installazione locale di Exchange Server, Skype for Business Server 2015 o SharePoint Server.
  
 - Eseguendo l'integrazione con i servizi directory, è possibile sincronizzare e gestire gli account utente di entrambi gli ambienti. È anche possibile aggiungere la sincronizzazione dell'hash delle password o Single Sign-On (SSO) per consentire agli utenti di accedere a entrambi gli ambienti con le proprie credenziali locali.
 - Mediante l'integrazione con i prodotti server locali viene creato un ambiente ibrido. Un ambiente ibrido può facilitare la migrazione completa di utenti o informazioni in Office 365, ma si può anche continuare a tenere parte degli utenti o delle informazioni in locale e parte nel cloud. Per altre informazioni sugli ambienti ibridi, vedere [Panoramica sul cloud ibrido](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).

È anche possibile usare gli Advisor di Azure Active Directory (Azure AD) per istruzioni sulla configurazione personalizzata (è necessario aver effettuato l'accesso a Office 365):

- [Advisor di Azure AD Connect](https://aka.ms/aadconnectpwsync)
- [Assistente distribuzione di AD FS](https://aka.ms/adfsguidance)
- [Guida alla configurazione di Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Prima di iniziare

Prima di integrare Office 365 e un ambiente locale, è anche necessario occuparsi della [pianificazione della rete e ottimizzazione delle prestazioni](network-planning-and-performance.md). È anche opportuno conoscere i [modelli di identità](about-office-365-identity.md). 

Vedere [Dove gestire gli account di Office 365](manage-office-365-accounts.md) per un elenco degli strumenti che è possibile usare per gestire utenti e account di Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrare Office 365 con i servizi directory
Se si dispone di account utente in una directory locale, non è auspicabile ricreali tutti in Office 365, rischiando di introdurre incoerenze o errori tra gli ambienti. La sincronizzazione della directory consente di eseguire il mirroring degli account tra l'ambiente online e quello locale. La sincronizzazione della directory evita agli utenti la necessità di ricordare nuove informazioni per ogni ambiente e all'amministratore di creare o aggiornare gli account due volte. Sarà necessario [preparare la directory locale](prepare-for-directory-synchronization.md) per la sincronizzazione della directory. Questa operazione può essere eseguita manualmente o usando lo [strumento IdFix](install-and-run-idfix.md) (lo strumento IdFix funziona solo con Active Directory Domain Services). 
  
![Usare la sincronizzazione della directory per mantenere sincronizzate le informazioni degli account locali e di quelli online](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Se si vuole consentire agli utenti di accedere a Office 365 con le proprie credenziali locali, è anche possibile configurare SSO. Con SSO, Office 365 viene configurato in modo da considerare attendibile l'ambiente locale per l'autenticazione degli utenti.
  
![Con Single Sign-On, lo stesso account è disponibile sia nell'ambiente locale che nell'ambiente online](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Tecniche di gestione degli account utente diverse offrono agli utenti esperienze diverse, come illustrato nella tabella seguente.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>Sincronizzazione della directory con o senza sincronizzazione dell'hash delle password o autenticazione pass-through

Un utente accede all'ambiente locale con il proprio account utente (dominio\nomeutente). Quando passa a Office 365, deve eseguire nuovamente l'accesso con l'account aziendale o dell'Istituto di istruzione (utente@dominio.com). Il nome utente è lo stesso in entrambi gli ambienti. Quando si aggiunge la sincronizzazione dell'hash delle password o l'autenticazione pass-through, l'utente ha la stessa password per entrambi gli ambienti, ma dovrà specificare di nuovo queste credenziali quando accede a Office 365. La sincronizzazione della directory con la sincronizzazione dell'hash delle password è lo scenario più di frequente.

Per configurare la sincronizzazione della directory, usare Azure Active Directory Connect. Per le istruzioni, vedere [Configurare la sincronizzazione della directory per Office 365](set-up-directory-synchronization.md) e [Azure AD Connect con impostazioni rapide](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Per saperne di più, vedere gli argomenti relativi alla [preparazione per la sincronizzazione della directory con Office 365](prepare-for-directory-synchronization.md) e all'[integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>Sincronizzazione della directory con SSO

Un utente accede all'ambiente locale con il proprio account utente. Quando passa a Office 365, viene connesso automaticamente oppure accede con le stesse credenziali usate per l'ambiente locale (dominio\nomeutente).

Per configurare SSO si usa anche Azure AD Connect. Per le istruzioni, vedere [Installazione personalizzata di Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Vedere [Accesso Single Sign-On alle applicazioni in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect sostituisce le precedenti versioni di strumenti di integrazione delle identità come DirSync e Azure AD Sync. Per altre informazioni, vedere [Che cos'è l'identità ibrida con Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969). Per eseguire l'aggiornamento da Azure Active Directory Sync ad Azure AD Connect, vedere le [istruzioni di aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240). 

Vedere anche [Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).

## <a name="see-also"></a>Vedere anche

[Panoramica di Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
