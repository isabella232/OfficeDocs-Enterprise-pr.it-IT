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
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Vengono descritte le cause comuni dei problemi relativi alla sincronizzazione della directory in Office 365 e vengono forniti alcuni metodi per risolverli.
ms.openlocfilehash: 2d567daa370d651a6eb9180db2f729d09b380226
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897309"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365

Con la sincronizzazione delle directory, è possibile continuare a gestire utenti e gruppi in locale e sincronizzare aggiunte, eliminazioni e le modifiche nel cloud. Ma il programma di installazione è complicato e in alcuni casi può risultare difficile identificare l'origine dei problemi. Sono disponibili risorse per individuare possibili problemi e correggerli.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Come sapere se si verificano problemi?

Il primo segnale del fatto che si verificano problemi è la porzione di stato di DirSync nell'interfaccia di amministrazione di Office 365 indicato che si è verificato un problema:
  
![Lo stato di DirSync affiancate nella visualizzazione Anteprima di amministrazione centrale](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Inoltre, verrà visualizzato un messaggio di posta (per il posta elettronica alternativi e per la posta elettronica admin) da Office 365 che indica che il tenant ha rilevato errori di sincronizzazione della directory. Per ulteriori informazioni, vedere [gli errori di sincronizzazione directory di identità in Office 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Come ottenere strumento connettersi Azure Active Directory

Nell'interfaccia di amministrazione di Office 365 accedere a * * utenti * * \> **utenti attivi**. Fare clic sul menu **altre** e seleziona **la sincronizzazione delle Directory**. 
  
![Nel menu di più, scegliere la sincronizzazione delle Directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
Nell'interfaccia di amministrazione di Office 365 precedente, accedere a **utenti** \> **Utenti attivi**e selezionare **impostare** accanto a **sincronizzazione di Active Directory**. 
  
![Scegli Configura accanto a sincronizzazione di Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Seguire le [istruzioni della procedura guidata](set-up-directory-synchronization.md) per scaricare Connetti Azure Active Directory. 
  
Se si sta ancora utilizzando Azure sincronizzazione di Active Directory (DirSync), dare uno sguardo le modalità [di risoluzione dei problemi relativi a messaggi di errore di configurazione guidata in Office 365 e Azure Active Directory Sync Tool installazione](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema per l'installazione dirsync, le autorizzazioni che necessarie e come risolvere gli errori più comuni. 
  
Per aggiornare di sincronizzazione di Azure Active Directory Connetti Azure Active Directory, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Risoluzione dei comuni causa dei problemi relativi alla sincronizzazione della directory in Office 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Oggetti sincronizzati non vengono visualizzate o si aggiorna in linea o ricezione di segnalazioni di errori di sincronizzazione dal servizio.**

- [Resilienza dei attributo duplicati e sincronizzazione delle identità](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Si dispone di un avviso nell'interfaccia di amministrazione di Office 365 o riceve automatizzate messaggi di posta elettronica non è stato un evento di sincronizzazione di recente**
- [Risoluzione dei problemi di connettività di Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Autorizzazioni e gli account di Active Directory connettersi Azure](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Sincronizzazione di Active Directory Connetti Azure: come gestire l'account del servizio di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Sincronizzazione di directory di interruzioni di Azure Active Directory o si sta avvisati che sincronizzazione non è registrato in più di un giorno](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Non sono sincronizzare gli hash password o vengono visualizzati gli avvisi in interfaccia di amministrazione di Office 365 non è stata una sincronizzazione hash password recenti**
- [Implementazione della sincronizzazione hash password con sincronizzazione di Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Vengono visualizzati un avviso di quota oggetto superato**
- È disponibile una quota di un oggetto incorporato per proteggere il servizio. Se si dispone di un numero eccessivo di oggetti nella directory che è necessario eseguire la sincronizzazione a Office 365, è necessario a [contatti di supporto per i prodotti di business](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per aumentare la quota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Devo sapere quali attributi vengono sincronizzati**
- È possibile trovare un elenco di tutti gli attributi sincronizzati tra organizzazioni locali e cloud [destra di seguito](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**Non è possibile gestire o rimuovere gli oggetti che sono stati sincronizzati con il cloud**
- Sei pronto a gestire gli oggetti in solo nel cloud? O un valore object che è stato eliminato in locale, ma è bloccato nel cloud? Esaminare questo [Risoluzione degli errori durante la sincronizzazione](https://go.microsoft.com/fwlink/p/?linkid=842044) e [supportare articolo](https://go.microsoft.com/fwlink/p/?LinkId=396720) per istruzioni su come risolvere questi problemi.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**Ho ricevuto un messaggio di errore che mi informa che la mia azienda ha superato il numero di oggetti che possono essere sincronizzati**
- È possibile leggere ulteriori informazioni su questo problema [di seguito](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Altre risorse

- [Script per correggere i nomi dell'entità utente duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Come preparare un dominio non instradabili (ad esempio domain Local) per la sincronizzazione delle directory](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script per il conteggio totali oggetti sincronizzati](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Risoluzione dei problemi relativi AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Utilizzare PowerShell per correggere gli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Utilizzare PowerShell per correggere UPN duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Utilizzare PowerShell per correggere gli indirizzi di posta elettronica duplicati](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Strumenti di diagnostica

[Strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene utilizzato per eseguire l'individuazione e risoluzione dei problemi di oggetti identity e i relativi attributi in un ambiente Active Directory locale in preparazione per la migrazione a Office 365. IDFix è progettato per gli amministratori di Active Directory responsabili della DirSync con il servizio Office 365. 

[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'area download Microsoft.