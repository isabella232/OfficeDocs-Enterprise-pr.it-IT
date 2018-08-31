---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Informazioni su come configurare la sincronizzazione delle directory tra Office 365 e Active Directory locale.
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541149"
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
|**Windows Server 2012 R2** | -PowerShell viene installato per impostazione predefinita, è necessaria alcuna azione.  <br/> -Net 4.5.1 e versioni successive offerte tramite Windows Update. Assicurarsi che siano installati gli aggiornamenti più recenti per Windows Server nel Pannello di controllo. |
|**Windows Server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012** | -La versione più recente di PowerShell è disponibile in Windows Management Framework 4.0. Effettuare una ricerca [nell'Area Download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br/> -Sono disponibili in [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).net 4.5.1 e versioni successive. |
|**Windows Server 2008** | -La versione supportata più recente di PowerShell è disponibile in Windows Management Framework 3.0, disponibile [nell'Area Download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br/> -Sono disponibili in [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).net 4.5.1 e versioni successive. |
   
> [!NOTE]
> Se si sta utilizzando Azure Active Directory DirSync, il numero massimo di membri del gruppo di distribuzione che è possibile sincronizzare da Active Directory locale per Azure Active Directory è 15.000. Per Azure Active Directory Connect, tale numero è 50.000. 
  
Per controllare più attentamente hardware, software, account e requisiti delle autorizzazioni, requisiti dei certificati SSL e limiti di oggetto di Azure Active Directory Connect, leggeranno [i prerequisiti per la connessione di Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
È anche possibile esaminare il Azure Active Directory Connect [versione cronologia delle versioni](https://go.microsoft.com/fwlink/p/?LinkId=733238) per vedere che cos'è incluso e risolti in ogni versione. 

## <a name="to-set-up-directory-synchronization"></a>Per configurare la sincronizzazione delle directory
1. Accedere all'interfaccia di amministrazione di Office 365 e fare clic su **utenti** \> **Utenti attivi** nel riquadro di spostamento sinistro. 
2. Nell'interfaccia di amministrazione di Office 365, nella pagina **utenti attivi** scegliere * * più * * \> **la sincronizzazione delle Directory**.
    
    ![Nel menu di più, scegliere la sincronizzazione delle Directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. Nella * * è sincronizzazione delle directory alle proprie esigenze. * * pagina due scelte prima del **1 a 10**e **11-50** risultato "in base alle dimensioni dell'organizzazione, è consigliabile creare e gestire gli utenti nel cloud. Sincronizzazione delle directory consentirà l'installazione più complessa. Passare a utenti attivi per aggiungere gli utenti." 
    
    - È possibile, tuttavia, continuare la configurazione di sincronizzazione della directory facendo clic su **Continua in questo caso** nella parte inferiore della pagina. 
    
    - Se si seleziona due scelte di quest'ultime, **250 51** o **251 o versione successiva**, l'impostazione della sincronizzazione consiglierà la sincronizzazione delle directory. Scegliere **Avanti** per continuare. 
    
    ![Scegliere Avanti per continuare la sincronizzazione delle directory](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. Nella **sincronizzazione della directory locale con il cloud**, leggere le informazioni e se si desiderano ulteriori informazioni, scegliere le informazioni su ulteriori collegamento che punta al: [Preparazione per garantire agli utenti tramite la sincronizzazione delle directory per Office 365](prepare-for-directory-synchronization.md)e quindi fare clic su Avanti ** **. 
    
5. Nella pagina **possiamo controllo della directory** , esaminare i requisiti per la verifica automatica della directory. Se siano soddisfatti i requisiti, scegliere **Avanti** \> **avviare analisi**. Se non è in grado di soddisfare i requisiti è possibile continuare facendo clic su **Continua manualmente**.
    
    ![Scegliere Avanti o continua manualmente via di esaminare la pagina di directory](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. Se si seleziona per analizzare le directory, scegliere **Avvia analisi** nella pagina di **valutazione di installazione di sincronizzazione della directory** . 
    
    Seguire le istruzioni per scaricare ed eseguire l'analisi.
    
7. Al termine dell'analisi, tornare all'installazione guidata e scegliere **Avanti** per visualizzare i risultati dell'analisi. 
    
8. Verificare i domini come indicato nella pagina **Proprietà verificare i domini** . Per istruzioni dettagliate, vedere [creazione di record DNS per Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).
    
    > [!IMPORTANT]
    > Dopo aver aggiunto un record TXT per verificare che si è proprietari del dominio, non vengano inoltrate al passaggio successivo dell'aggiunta di utenti nella procedura guidata domini. La sincronizzazione della directory verrà aggiungere gli utenti. 
  
    Tornare alla pagina **Il programma di installazione di Office 365** e scegliere **l'aggiornamento**
    
    ![Dopo aver verificato i domini, scegliere l'aggiornamento](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. Nella pagina **pronti i domini** , scegliere **Avanti**.
    
10. Nella pagina **pulizia dell'ambiente** , se lo si desidera seguire le istruzioni per scaricare lo strumento IDFix per controllare Active Directory. Scegliere **Avanti** per continuare. 
    
11. Nella * * eseguire Azure Active Directory connettersi * *, selezionare **Scarica** per l'installazione guidata di Azure Active Directory Connetti. 
    
    > [!NOTE]
    > A questo punto si nella procedura guidata Connetti Azure Active Directory. Verificare che si lascia pagina della procedura guidata di sincronizzazione directory che dell'utente al ultimo all'apertura nel browser, in modo che è possibile restituire a esso dopo che vengono eseguite le operazioni di Azure Active Directory Connetti. 
  
    Dopo l'installazione di Azure Active Directory connessione è stata verrà aperto automaticamente. È inoltre possibile aprire dal desktop, il sito di installazione predefinito. Seguire le istruzioni della procedura guidata in base al proprio scenario:
    
  - Sincronizzazione della directory con la sincronizzazione delle password hash, utilizzare la [connessione AD Azure con impostazioni express](https://go.microsoft.com/fwlink/p/?LinkID=698537).
    
  - Per più foreste, autenticazione pass-through, identità federata e le opzioni SSO, utilizzare la [connessione AD installazione personalizzata di Azure](https://go.microsoft.com/fwlink/p/?LinkId=698430).
    
    Nella pagina **Impostazioni Express** utilizzare queste opzioni, selezionare **Personalizza** . 
    
12. Dopo la creazione guidata Connetti Azure Active Directory, tornare alla procedura guidata di **Configurazione di Office 365** e **verificare che l'opzione sincronizzazione è stata eseguita come previsto pagina**seguire le istruzioni. Scegliere **Avanti** per continuare. 
    
13. Continuare a leggere le istruzioni di * * attiva utenti * * pagina e quindi fare clic su **Avanti**.
    
14. Nella pagina **tutte le impostazioni correnti** , scegliere **Fine** . 
    
## <a name="assign-licences-to-synchronized-users"></a>Assegnare licenze agli utenti sincronizzati
Dopo aver sincronizzato agli utenti di Office 365, in cui vengono creati, ma è necessario assegnare licenze ad essi in modo che utilizzino le funzionalità di Office 365, ad esempio posta. Per ulteriori informazioni, vedere [assegnare licenze agli utenti di Office 365 per aziende](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
    
## <a name="finish-setting-up-domains"></a>Completare l'impostazione domini
Seguire i passaggi della [creazione di record DNS per Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare l'installazione i domini.