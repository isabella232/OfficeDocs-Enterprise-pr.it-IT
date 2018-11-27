---
title: Preparare un dominio non instradabili per la sincronizzazione delle directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Informazioni su come procedere se si dispone di un dominio non routale associato agli utenti in locale prima di sincronizzarlo con Office 365.
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674440"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Preparare un dominio non instradabili per la sincronizzazione delle directory
Durante la sincronizzazione della directory locali con Office 365 è necessario disporre di un dominio verificato in Azure Active Directory. Verranno visualizzati solo i nomi UPN (User Principal) associati al dominio locale. Tuttavia, qualsiasi UPN che contiene un dominio non instradabili, ad esempio Local (ad esempio billa@contoso.local), verranno sincronizzate con un. dominio onmicrosoft.com (ad esempio billa@contoso.onmicrosoft.com). 

Se si utilizza attualmente un dominio Local per gli account utente in Active Directory, è consigliabile modificare in modo da utilizzare un dominio verificato (ad esempio billa@contoso.com) per poter eseguire correttamente la sincronizzazione con il dominio di Office 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Se solo dispongo di un dominio locale. Local.

Lo strumento più recente che è possibile utilizzare per la sincronizzazione di Active Directory in Azure Active Directory denominato Connect Azure Active Directory. Per ulteriori informazioni, vedere [integrazione le identità in locale con Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure Active Directory Connetti Sincronizza UPN degli utenti e password in modo che gli utenti possono accedere con le stesse credenziali utilizzano locale. Tuttavia, Azure Active Directory Connetti Sincronizza solo agli utenti di domini che sono confermati da Office 365. Ciò significa che il dominio inoltre viene verificato da Azure Active Directory poiché le identità di Office 365 sono gestite da Azure Active Directory. In altre parole, il dominio deve essere un dominio Internet valido (ad esempio. com,. org, .net, us e così via). Se Active Directory interno utilizza solo un dominio non instradabili (ad esempio Local), questo eventualmente non può corrispondere al dominio verificato è che Office 365. Per risolvere questo problema modificando il dominio primario nei locale in Active Directory o tramite l'aggiunta di uno o più suffissi UPN.
  
### <a name="change-your-primary-domain"></a>**Modificare il dominio primario**

Modificare il dominio primario di un dominio verificato in Office 365, ad esempio contoso.com. Tutti gli utenti con contoso. Local dominio viene quindi aggiornato a contoso.com. Per ulteriori informazioni, vedere [Dominio rinominare funzionamento](https://go.microsoft.com/fwlink/p/?LinkId=624174). Tuttavia, si tratta di un processo molto attivo e una soluzione più semplice consiste nell' [aggiungere UPN suffissi e aggiornare gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register), come illustrato nella sezione seguente.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**Aggiungere suffissi UPN e aggiornare gli utenti**

È possibile risolvere il problema Local registrando nuovo suffisso UPN o suffissi in Active Directory in modo che corrisponda al dominio (o domini) verificate in Office 365. Dopo aver registrato il nuovo suffisso, aggiornare l'utente UPN per sostituire il Local con il nuovo nome di dominio, ad esempio, in modo che un account utente simile billa@contoso.com.
  
Dopo aver aggiornato l'UPN per l'utilizzo al dominio verificato, si è pronti per la sincronizzazione di Active Directory locale con Office 365.
  
 **Passaggio 1: Aggiungere il nuovo suffisso UPN**
  
1. Nel server che esegue in servizi di dominio Active Directory (AD DS), in Server Manager scegliere **gli strumenti di** \> **e trust di Active Directory**.
    
    **Oppure, se non si dispone di Windows Server 2012**
    
    Premere **il tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare domain. msc e quindi fare clic su **OK**.
    
    ![Scegliere il trust e domini di Active Directory.](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Nella finestra **e trust di Active Directory** , destro **e trust di Active Directory**e quindi scegliere **proprietà**.
    
    ![Il pulsante destro ActiveDirectory domini e trust e scegliere Proprietà](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Nella scheda **Suffissi UPN** , digitare nella casella **Suffissi UPN alternativi** il suffisso UPN nuovo o suffissi e quindi fare clic su **Aggiungi** \> **Applica**.
    
    ![Aggiungere un suffisso UPN nuovo](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Fare clic su **OK** al termine suffissi aggiunta. 
    
 **Passaggio 2: Modificare il suffisso UPN per gli utenti esistenti**
  
1. Nel server che esegue in servizi di dominio Active Directory (AD DS), in Server Manager scegliere **gli strumenti di** \> **e computer di Active Directory Active Directory degli utenti**.
    
    **Oppure, se non si dispone di Windows Server 2012**
    
    Premere **il tasto Windows + R** per aprire la finestra di dialogo **Esegui** e quindi digitare dsa. msc e quindi fare clic su **OK**
    
2. Selezionare un utente pulsante destro del mouse, quindi scegliere **proprietà**.
    
3. Nella scheda **Account** nell'elenco a discesa suffisso UPN, fare clic sul suffisso UPN nuovo e quindi fare clic su **OK**.
    
    ![Aggiunta di nuovo suffisso UPN per un utente](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Completare questi passaggi per ogni utente.
    
    In alternativa è possibile in blocco aggiornamento l'UPN suffissi [è inoltre possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh).
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**È inoltre possibile utilizzare Windows PowerShell per modificare il suffisso UPN per tutti gli utenti**

Se si dispongono di numerosi utenti per l'aggiornamento, è più semplice utilizzare Windows PowerShell. Nell'esempio seguente viene utilizzato il cmdlet [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) e [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) per modificare tutti i suffissi di Contoso. Local in contoso.com. 

Eseguire i seguenti comandi di Windows PowerShell per aggiornare tutti i suffissi di Contoso. Local per contoso.com:
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
Per ulteriori informazioni sull'utilizzo di Windows PowerShell in Active Directory, vedere [Active Directory Windows PowerShell modulo](https://go.microsoft.com/fwlink/p/?LinkId=624314) . 

