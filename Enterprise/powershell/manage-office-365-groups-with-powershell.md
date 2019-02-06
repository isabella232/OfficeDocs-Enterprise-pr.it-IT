---
title: Gestire Gruppi di Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Ultimo aprile 18 aggiornato, 2018
ms.openlocfilehash: 518f845099a72d9addac13388d1b281ca63ee408
ms.sourcegitcommit: e56f830ccff8d74d9edbff4a46a9ee1d613291ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2019
ms.locfileid: "29741219"
---
# <a name="manage-office-365-groups-with-powershell"></a>Gestire Gruppi di Office 365 con PowerShell

 *Ultimo aprile 18 aggiornato, 2018* 
  
In questo articolo viene illustrato come eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell. Inoltre, sono elencati i cmdlet di PowerShell per i gruppi. Per informazioni sulla gestione dei siti di SharePoint, vedere [Manage siti del team e siti di comunicazione tramite PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).
  
## <a name="common-tasks-for-managing-office-365-groups"></a>Attività comuni per la gestione dei gruppi di Office 365

- [Aggiornare le liste di distribuzione a Gruppi di Office 365 in Outlook](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [Gestire chi può creare gruppi di Office 365](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [Gestire l'accesso degli utenti guest ai gruppi di Office 365](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [Gestire i gruppi in modo dinamico in Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=847632)
    
- Aggiungere centinaia o migliaia di utenti ai gruppi di Office 365, utilizzare il [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a>Collegarsi alle linee guida sull'utilizzo di gruppi di Office 365
<a name="BK_LinkToGuideLines"> </a>

Quando gli utenti di [creare un gruppo in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), è possibile mostrare loro un collegamento a indicazioni per l'utilizzo dell'organizzazione. Ad esempio, se si richiede un prefisso specifico o suffisso da aggiungere al nome di un gruppo.
  
Utilizzare Azure Active Directory PowerShell per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365. Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) ed eseguire la procedura in **Create le impostazioni a livello di directory** per definire il collegamento ipertestuale alle linee guida sull'utilizzo. Una volta eseguire il cmdlet AAD, dell'utente verrà visualizzato il collegamento alle istruzioni quando creare o modificare un gruppo di Outlook. 
  
![Creare un nuovo gruppo con un utilizzo linee guida per il collegamento](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Linee guida per gruppi di istruzioni per l'uso fare clic su gruppo per visualizzare le organizzazioni di Office 365](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a>Consentire agli utenti di inviare il gruppo di Office 365
<a name="BK_LinkToGuideLines"> </a>

È possibile ottenere questo risultato anche nell'interfaccia di amministrazione di Exchange. [Consenti ai membri di inviare come o Invia per conto di un gruppo](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590), vedere.
  
Se si desidera abilitare i gruppi di Office 365 a "Invia come", utilizzare il cmdlet [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) e [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) per configurare questa impostazione. Una volta che si attiva questa impostazione, gli utenti di Office 365 group consentono Outlook o Outlook sul web per inviare e rispondere al messaggio di posta elettronica del gruppo di Office 365. Gli utenti possono accedere al gruppo di creare un nuovo messaggio di posta elettronica e modificare il campo "Invia come" all'indirizzo di posta elettronica del gruppo. 
  
> [!NOTE]
> È necessario aggiungere l'indirizzo di posta elettronica del gruppo nel campo **Cc** durante la composizione di posta elettronica "Invia come" in modo che il messaggio viene inviato al gruppo e viene visualizzato nelle conversazioni di gruppo. 
  
In questa fase, l'unico modo per aggiornare il criterio cassetta postale è tramite [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).
  
- Utilizzare questo comando per impostare l'alias di gruppo.
    
  ```
  $groupAlias = "TestSendAs"
  ```

- Utilizzare questo comando per impostare l'alias di utente.
    
  ```
  $userAlias = "User"
  ```

- Utilizzare questo comando per passare il groupalias al cmdlet Get-Recipient per ottenere i dettagli del destinatario.
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- Quindi il nome del destinatario di destinazione (nome del gruppo) dovrà essere passati al cmdlet Add-RecipientPermission. Il parametro useralias per i quali l'autorizzazione sendas verrà assegnato al ruolo verrà assegnato al parametro - Trustee.
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- Una volta che viene eseguito il cmdlet, gli utenti possono accedere a Outlook o Outlook sul web per inviare il gruppo, aggiungendo l'indirizzo di posta elettronica del gruppo nel campo **da** . 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a>Creare le classificazioni per i gruppi di Office all'interno dell'organizzazione
<a name="BKMK_CreateClassification"> </a>

È possibile creare le classificazioni che gli utenti dell'organizzazione possono impostare durante la creazione di un gruppo di Office 365. Ad esempio, è possibile consentire agli utenti di impostare "Standard", "Secret" e "Top Secret" nella creazione di gruppi. Classificazioni gruppo non sono specificate per impostazione predefinita e si desidera creare in modo che gli utenti per l'impostazione. Utilizzare PowerShell di Azure Active Directory per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365.
  
Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) e seguire i passaggi descritti in **Crea impostazioni a livello di directory** per definire la classificazione per i gruppi di Office 365. 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Per associare una descrizione per ciascuna delle quali che è possibile utilizzare le impostazioni dell'attributo *ClassificationDescriptions* per definire. 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

Ad esempio:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Dopo aver eseguito il cmdlet di Azure Active Directory sopra per impostare la classificazione, eseguire il cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) se si desidera impostare la classificazione per un gruppo specifico. 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

Oppure creare un nuovo gruppo con una classificazione.
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Per altri dettagli sull'uso di PowerShell di Exchange Online vedere [Uso di PowerShell con Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) e [Connettersi a PowerShell di Exchange Online](https://go.microsoft.com/fwlink/?LinkID=722415). 
  
Dopo che queste impostazioni sono abilitate, il proprietario del gruppo saranno in grado di scegliere una classificazione da Outlook sul Web e Outlook dal menu a discesa e salvarlo nella pagina **Modifica** gruppo. 
  
![Scegliere la classificazione di gruppo di Office 365](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a>Nascondere gruppi di Office 365 dall'elenco indirizzi globale
<a name="BKMK_CreateClassification"> </a>

È possibile specificare se un gruppo di Office 365 viene visualizzato nell'elenco indirizzi globale (GAL) e altri elenchi all'interno dell'organizzazione. Se si dispone di un gruppo di reparto legale che non si desidera venga visualizzata nell'elenco di indirizzi, ad esempio, è possibile interrompere gruppo vengano visualizzate nell'elenco indirizzi globale. Eseguire il cmdlet gruppo Set-Unified per nascondere il gruppo dall'elenco di indirizzi simile alla seguente:
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Consentire solo gli utenti interni inviare messaggi al gruppo di Office 365
<a name="BKMK_CreateClassification"> </a>

Se non si desidera agli utenti di altre organizzazioni di inviare posta elettronica a un gruppo di Office 365, è possibile modificare le impostazioni per tale gruppo. Sarà possibile solo gli utenti interni inviare un messaggio di posta elettronica al gruppo. Utente esterno tenta di inviare messaggi a tale gruppo verranno rifiutati.
  
Eseguire il cmdlet Set-UnifiedGroup per aggiornare questa impostazione, simile alla seguente:
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a>Aggiungere i suggerimenti per i gruppi di Office 365
<a name="BKMK_CreateClassification"> </a>

Ogni volta che un mittente tenta di inviare un messaggio di posta elettronica a un gruppo di Office 365, è possibile visualizzare un suggerimento messaggio a quest'ultimo.
  
Eseguire il cmdlet gruppo Set-Unified per aggiungere un suggerimento per il gruppo:
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Insieme suggerimento, è inoltre possibile impostare MailTipTranslations, che consente di specificare ulteriori lingue per il suggerimento. Si supponga che si desidera avere la traduzione spagnola, quindi eseguire il comando seguente:
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a>Modificare il nome visualizzato del gruppo di Office 365
<a name="BKMK_CreateClassification"> </a>

DisplayName specifica il nome del gruppo di Office 365. È possibile visualizzare il nome specificato in exchange admin center o Office 365 admin portale. È possibile modificare il nome visualizzato del gruppo o assegnare un nome visualizzato per un gruppo di Office 365 esistente eseguendo il comando Set-UnifiedGroup:
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a>Gestire le foto utente nei gruppi di Office 365
<a name="BKMK_CreateClassification"> </a>

| |
|**Nome cmdlet**|**Descrizione**|
|:-----|:-----|
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Consente di visualizzare le informazioni relative alle foto utente associata a un account. Foto dell'utente vengono archiviate in Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Consente di associare una foto utente con un account. Foto dell'utente vengono archiviate in Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Rimuovere la foto di un gruppo di Office 365  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Modificare l'impostazione predefinita dei gruppi di Office 365 per Outlook pubblici o privati
<a name="BKMK_CreateClassification"> </a>

Office 365 gruppi in Outlook vengono creati come privati per impostazione predefinita. Se l'organizzazione intende Office 365 gruppi venga creata come pubblico per impostazione predefinita (o su Private), utilizzare la sintassi seguente cmdlet PowerShell:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Per impostare su privata:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
Per verificare l'impostazione: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
Per ulteriori informazioni, vedere [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) e [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).
  
## <a name="office-365-groups-cmdlets"></a>Cmdlet per i gruppi di Office 365

I cmdlet seguenti sono stati recentemente rese disponibili per gruppi di Office 365. Se non si è in grado di utilizzare tali, la sottoscrizione a Office 365 non aggiornata con questa funzionalità ancora. Controllare il centro di messaggi e la [Roadmap di Office 365](http://roadmap.office.com/en-us).
  
| |
|**Nome cmdlet**|**Descrizione**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Utilizzare questo cmdlet per cercare i gruppi di esistenti Office 365 e per visualizzare le proprietà dell'oggetto group  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Aggiornare le proprietà di uno specifico gruppo di Office 365  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Creare un nuovo gruppo di Office 365. Questo cmdlet fornisce un insieme minimo di parametri, per impostazione valori per le proprietà estese utilizzano Set-UnifiedGroup dopo aver creato il nuovo gruppo  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Eliminare un gruppo di esistente Office 365  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Recuperare informazioni sui appartenenze e il proprietario di un gruppo di Office 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Aggiungere centinaia o migliaia di utenti o nuovi proprietari, a un gruppo di esistente Office 365  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Rimuovere membri e proprietari da un gruppo di esistente Office 365  <br/> |
   
## <a name="for-more-information"></a>Ulteriori informazioni

- [Utilizzo di PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [Applicazione o rimozione di un criterio cassetta postale di Outlook Web App in una cassetta postale](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [Criterio di assegnazione dei gruppi di Office 365](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

