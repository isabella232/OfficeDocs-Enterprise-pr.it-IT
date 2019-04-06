---
title: Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Vengono descritte le cause più comuni di problemi relativi alla sincronizzazione della directory in Office 365 e vengono forniti alcuni metodi per risolvere il problema e risolverli.
ms.openlocfilehash: a5c4b58dd856158b00605f39d8a66b48488086b2
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001839"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365

Con la sincronizzazione della directory, puoi continuare a gestire gli utenti e gruppi locali e sincronizzare aggiunte, eliminazioni e modifiche nel cloud. Tuttavia, la configurazione è un po' complicata e a volte può essere difficile identificare l'origine dei problemi. Sono disponibili risorse utili per identificare i potenziali problemi e correggerli.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Come si fa a sapere se c'è qualcosa di sbagliato?

La prima indicazione che qualcosa è errato è quando il riquadro Stato DirSync nell'interfaccia di amministrazione di Microsoft 365 indica che si è verificato un problema:
  
![Riquadro di stato DirSync nell'anteprima dell'interfaccia di amministrazione](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Riceverà anche una mail (alla posta elettronica alternativa e alla posta elettronica di amministrazione) da Office 365 che indica che il tenant ha riscontrato errori di sincronizzazione della directory. Per ulteriori informazioni, vedere [identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Come si ottiene lo strumento di Azure Active Directory Connect?

nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com), passare a * * users \> * * **Active users**. Fare clic sul menu **altro** e selezionare **sincronizzazione directory**. 
  
![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Seguire le istruzioni riportate [nella procedura guidata](set-up-directory-synchronization.md) per scaricare Azure ad Connect. 
  
Se si sta ancora utilizzando Azure Active Directory Sync (DirSync), vedere [come risolvere i problemi relativi all'installazione dello strumento di sincronizzazione di Azure Active Directory e ai messaggi di errore della procedura guidata di configurazione in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema da installare dirsync, le autorizzazioni necessarie e come risolvere gli errori più comuni. 
  
Per eseguire l'aggiornamento da Azure Active Directory Sync ad Azure AD Connect, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Risoluzione delle cause comuni dei problemi relativi alla sincronizzazione della directory in Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Gli oggetti sincronizzati non vengono visualizzati o aggiornati online oppure ricevo segnalazioni di errori di sincronizzazione dal servizio.**

- [Sincronizzazione delle identità e resilienza degli attributi duplicati](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Ho un avviso nell'interfaccia di amministrazione o ricevo messaggi di posta elettronica automatici che non sono stati riferiti a un evento di sincronizzazione recente**
- [Risoluzione dei problemi relativi alla connettività con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Account e autorizzazioni di Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Sincronizzazione di Azure AD Connect: informazioni su come gestire l'account di servizio di Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [La sincronizzazione della directory in Azure Active Directory si interrompe o si avverte che la sincronizzazione non è registrata in più di un giorno.](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Gli hash delle password non sono sincronizzati oppure viene visualizzato un avviso nell'interfaccia di amministrazione che non è stata eseguita una sincronizzazione degli hash delle password recente**
- [Implementazione della sincronizzazione degli hash delle password con Azure AD Connect Sync](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Viene visualizzato un avviso che ha superato la quota oggetto**
- Esiste una quota di oggetti integrata per proteggere il servizio. Se nella directory sono presenti troppi oggetti che devono essere sincronizzati con Office 365, è necessario contattare il [supporto per i prodotti aziendali](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per aumentare la quota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Devo sapere quali attributi vengono sincronizzati**
- È possibile trovare un elenco di tutti gli attributi sincronizzati tra l'ambiente locale e il cloud [direttamente qui](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Non è possibile gestire o rimuovere gli oggetti che sono stati sincronizzati nel cloud**
- Sei pronto a gestire gli oggetti solo nel cloud? Oppure c'è un oggetto che è stato eliminato in locale, ma è bloccato nel cloud? Esaminare gli [errori di risoluzione dei problemi durante](https://go.microsoft.com/fwlink/p/?linkid=842044) l'articolo relativo alla sincronizzazione e al [supporto tecnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) per informazioni su come risolvere questi problemi.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Ho ricevuto un messaggio di errore che mi informa che la mia azienda ha superato il numero di oggetti che possono essere sincronizzati**
- È possibile leggere altre informazioni su questo problema [qui](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Altre risorse

- [Script per correggere i nomi dell'entità utente duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script per contare gli oggetti totali sincronizzati](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Risoluzione dei problemi di ADFS 2,0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Utilizzo di PowerShell per correggere gli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Utilizzo di PowerShell per correggere l'UPN duplicato](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Utilizzo di PowerShell per correggere gli indirizzi di posta elettronica duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Strumenti di diagnostica

[Lo strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene utilizzato per eseguire l'individuazione e la correzione degli oggetti Identity e dei relativi attributi in un ambiente Active Directory locale in preparazione per la migrazione a Office 365. IDFix è destinato agli amministratori di Active Directory responsabili di DirSync con il servizio Office 365. 

[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'area download Microsoft.