---
title: Gestire i gruppi di Office 365 PowerShell
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: In questo articolo viene illustrato come eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell.
ms.openlocfilehash: 23dfb7f871496b33bf9c34937977b98dc13cea6d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541357"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="5c61f-103">Gestire i gruppi di Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c61f-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="5c61f-104">*Ultimo aprile 18 aggiornato, 2018*</span><span class="sxs-lookup"><span data-stu-id="5c61f-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="5c61f-p101">In questo articolo viene illustrato come eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell. Inoltre, sono elencati i cmdlet di PowerShell per i gruppi. Per informazioni sulla gestione dei siti di SharePoint, vedere [siti di gestire SharePoint Online mediante PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span><span class="sxs-lookup"><span data-stu-id="5c61f-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87.aspx).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="5c61f-108">Attività comuni per la gestione dei gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="5c61f-109">Elenchi di distribuzione dell'aggiornamento a Office 365 gruppi</span><span class="sxs-lookup"><span data-stu-id="5c61f-109">Upgrade distribution lists to Office 365 Groups</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f.aspx)
    
- [<span data-ttu-id="5c61f-110">Gestione di utenti autorizzati a creare gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618.aspx)
    
- [<span data-ttu-id="5c61f-111">Gestire l'accesso guest ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96.aspx)
    
- [<span data-ttu-id="5c61f-112">Gestire i gruppi in modo dinamico in Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5c61f-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="5c61f-113">Aggiungere centinaia o migliaia di utenti ai gruppi di Office 365, utilizzare il [cmdlet Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span><span class="sxs-lookup"><span data-stu-id="5c61f-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="5c61f-114">Collegarsi alle linee guida sull'utilizzo di gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="5c61f-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-115"></span></span>

<span data-ttu-id="5c61f-p102">Quando gli utenti in [creare o modificare un gruppo in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), è possibile mostrare loro un collegamento a indicazioni per l'utilizzo dell'organizzazione. Ad esempio, se si richiede un prefisso specifico o suffisso da aggiungere al nome di un gruppo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="5c61f-p103">Utilizzare Azure Active Directory PowerShell per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365. Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) ed eseguire la procedura in **Create le impostazioni a livello di directory** per definire il collegamento ipertestuale alle linee guida sull'utilizzo. Una volta eseguire il cmdlet AAD, dell'utente verrà visualizzato il collegamento alle istruzioni quando creare o modificare un gruppo di Outlook.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Creare un nuovo gruppo con un utilizzo linee guida per il collegamento](media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Linee guida per gruppi di istruzioni per l'uso fare clic su gruppo per visualizzare le organizzazioni di Office 365](media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="5c61f-123">Consentire agli utenti di inviare il gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="5c61f-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-124"></span></span>

<span data-ttu-id="5c61f-p104">È possibile ottenere questo risultato anche nell'interfaccia di amministrazione di Exchange. [Consenti ai membri di "Invia come" o "Invia" per conto di un gruppo di Office 365](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx), vedere.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p104">You can also do this in the Exchange Admin Center. See [Allow members to "Send as" or "Send on behalf of" an Office 365 Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590.aspx).</span></span>
  
<span data-ttu-id="5c61f-p105">Se si desidera abilitare i gruppi di Office 365 a "Invia come", utilizzare il cmdlet [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) e [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) per configurare questa impostazione. Una volta che si attiva questa impostazione, gli utenti di Office 365 group consentono Outlook o Outlook sul web per inviare e rispondere al messaggio di posta elettronica del gruppo di Office 365. Gli utenti possono accedere al gruppo di creare un nuovo messaggio di posta elettronica e modificare il campo "Invia come" all'indirizzo di posta elettronica del gruppo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5c61f-130">È necessario aggiungere l'indirizzo di posta elettronica del gruppo nel campo **Cc** durante la composizione di posta elettronica "Invia come" in modo che il messaggio viene inviato al gruppo e viene visualizzato nelle conversazioni di gruppo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="5c61f-131">In questa fase, l'unico modo per aggiornare il criterio cassetta postale è tramite [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span><span class="sxs-lookup"><span data-stu-id="5c61f-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="5c61f-132">Utilizzare questo comando per impostare l'alias di gruppo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="5c61f-133">Utilizzare questo comando per impostare l'alias di utente.</span><span class="sxs-lookup"><span data-stu-id="5c61f-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="5c61f-134">Utilizzare questo comando per passare il groupalias al cmdlet Get-Recipient per ottenere i dettagli del destinatario.</span><span class="sxs-lookup"><span data-stu-id="5c61f-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="5c61f-p106">Quindi il nome del destinatario di destinazione (nome del gruppo) dovrà essere passati al cmdlet Add-RecipientPermission. Il parametro useralias per i quali l'autorizzazione sendas verrà assegnato al ruolo verrà assegnato al parametro - Trustee.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="5c61f-137">Una volta che viene eseguito il cmdlet, gli utenti possono accedere a Outlook o Outlook sul web per inviare il gruppo, aggiungendo l'indirizzo di posta elettronica del gruppo nel campo **da** .</span><span class="sxs-lookup"><span data-stu-id="5c61f-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="5c61f-138">Creare le classificazioni per i gruppi di Office all'interno dell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="5c61f-138">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="5c61f-p107">È possibile creare le classificazioni che gli utenti dell'organizzazione possono impostare durante la creazione di un gruppo di Office 365. Ad esempio, è possibile consentire agli utenti di impostare "Standard", "Secret" e "Top Secret" nella creazione di gruppi. Classificazioni gruppo non sono specificate per impostazione predefinita e si desidera creare in modo che gli utenti per l'impostazione. Utilizzare PowerShell di Azure Active Directory per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="5c61f-143">Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) e seguire i passaggi descritti in **Crea impostazioni a livello di directory** per definire la classificazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5c61f-143">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="5c61f-144">Per associare una descrizione per ciascuna delle quali che è possibile utilizzare le impostazioni dell'attributo *ClassificationDescriptions* per definire.</span><span class="sxs-lookup"><span data-stu-id="5c61f-144">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="5c61f-145">Esempio:</span><span class="sxs-lookup"><span data-stu-id="5c61f-145">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="5c61f-146">Dopo aver eseguito il cmdlet di Azure Active Directory sopra per impostare la classificazione, eseguire il cmdlet [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) se si desidera impostare la classificazione per un gruppo specifico.</span><span class="sxs-lookup"><span data-stu-id="5c61f-146">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="5c61f-147">Oppure creare un nuovo gruppo con una classificazione.</span><span class="sxs-lookup"><span data-stu-id="5c61f-147">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="5c61f-148">Per ulteriori informazioni sull'utilizzo di Exchange Online PowerShell, verificare [l'Utilizzo di PowerShell con Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) e [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) .</span><span class="sxs-lookup"><span data-stu-id="5c61f-148">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="5c61f-149">Dopo che queste impostazioni sono abilitate, il proprietario del gruppo saranno in grado di scegliere una classificazione da Outlook sul Web e Outlook dal menu a discesa e salvarlo nella pagina **Modifica** gruppo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-149">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Scegliere la classificazione di gruppo di Office 365](media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="5c61f-151">Nascondere gruppi di Office 365 dall'elenco indirizzi globale</span><span class="sxs-lookup"><span data-stu-id="5c61f-151">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="5c61f-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-152"></span></span>

<span data-ttu-id="5c61f-p108">È possibile specificare se un gruppo di Office 365 viene visualizzato nell'elenco indirizzi globale (GAL) e altri elenchi all'interno dell'organizzazione. Se si dispone di un gruppo di reparto legale che non si desidera venga visualizzata nell'elenco di indirizzi, ad esempio, è possibile interrompere gruppo vengano visualizzate nell'elenco indirizzi globale. Eseguire il cmdlet gruppo Set-Unified per nascondere il gruppo dall'elenco di indirizzi simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="5c61f-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="5c61f-156">Consentire solo gli utenti interni inviare messaggi al gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-156">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="5c61f-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-157"></span></span>

<span data-ttu-id="5c61f-p109">Se non si desidera agli utenti di altre organizzazioni di inviare posta elettronica a un gruppo di Office 365, è possibile modificare le impostazioni per tale gruppo. Sarà possibile solo gli utenti interni inviare un messaggio di posta elettronica al gruppo. Utente esterno tenta di inviare messaggi a tale gruppo verranno rifiutati.</span><span class="sxs-lookup"><span data-stu-id="5c61f-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="5c61f-161">Eseguire il cmdlet Set-UnifiedGroup per aggiornare questa impostazione, simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="5c61f-161">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="5c61f-162">Aggiungere i suggerimenti per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-162">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="5c61f-163"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-163"></span></span>

<span data-ttu-id="5c61f-164">Ogni volta che un mittente tenta di inviare un messaggio di posta elettronica a un gruppo di Office 365, è possibile visualizzare un suggerimento messaggio a quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="5c61f-164">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="5c61f-165">Eseguire il cmdlet gruppo Set-Unified per aggiungere un suggerimento per il gruppo:</span><span class="sxs-lookup"><span data-stu-id="5c61f-165">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="5c61f-p110">Insieme suggerimento, è inoltre possibile impostare MailTipTranslations, che consente di specificare ulteriori lingue per il suggerimento. Si supponga che si desidera avere la traduzione spagnola, quindi eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5c61f-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="5c61f-168">Modificare il nome visualizzato del gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-168">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="5c61f-p111">DisplayName specifica il nome del gruppo di Office 365. È possibile visualizzare il nome specificato in exchange admin center o Office 365 admin portale. È possibile modificare il nome visualizzato del gruppo o assegnare un nome visualizzato per un gruppo di Office 365 esistente eseguendo il comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="5c61f-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="5c61f-172">Gestire le foto utente nei gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-172">Manage user photos in Office 365 Groups</span></span>

|<span data-ttu-id="5c61f-173">**Nome cmdlet**</span><span class="sxs-lookup"><span data-stu-id="5c61f-173">**Cmdlet name**</span></span>|<span data-ttu-id="5c61f-174">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="5c61f-174">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="5c61f-175">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5c61f-175">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="5c61f-p112">Consente di visualizzare le informazioni relative alle foto utente associata a un account. Foto dell'utente vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="5c61f-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="5c61f-178">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5c61f-178">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="5c61f-p113">Consente di associare una foto utente con un account. Foto dell'utente vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="5c61f-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="5c61f-181">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="5c61f-181">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="5c61f-182">Rimuovere la foto di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-182">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="5c61f-183">Modificare l'impostazione predefinita dei gruppi di Office 365 per Outlook pubblici o privati</span><span class="sxs-lookup"><span data-stu-id="5c61f-183">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="5c61f-184"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="5c61f-184"></span></span>

<span data-ttu-id="5c61f-p114">Office 365 gruppi in Outlook vengono creati come privati per impostazione predefinita. Se l'organizzazione intende Office 365 gruppi venga creata come pubblico per impostazione predefinita (o su Private), utilizzare la sintassi seguente cmdlet PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5c61f-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="5c61f-187">Per impostare su privata:</span><span class="sxs-lookup"><span data-stu-id="5c61f-187">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="5c61f-188">Per verificare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="5c61f-188">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="5c61f-189">Per ulteriori informazioni, vedere [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) e [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span><span class="sxs-lookup"><span data-stu-id="5c61f-189">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="5c61f-190">Cmdlet per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-190">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="5c61f-p115">I cmdlet seguenti sono stati recentemente rese disponibili per gruppi di Office 365. Se non si è in grado di utilizzare tali, la sottoscrizione a Office 365 non aggiornata con questa funzionalità ancora. Controllare il centro di messaggi e la [Roadmap di Office 365](http://roadmap.office.com/en-us).</span><span class="sxs-lookup"><span data-stu-id="5c61f-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
|<span data-ttu-id="5c61f-194">**Nome cmdlet**</span><span class="sxs-lookup"><span data-stu-id="5c61f-194">**Cmdlet name**</span></span>|<span data-ttu-id="5c61f-195">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="5c61f-195">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="5c61f-196">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5c61f-196">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="5c61f-197">Utilizzare questo cmdlet per cercare i gruppi di esistenti Office 365 e per visualizzare le proprietà dell'oggetto group</span><span class="sxs-lookup"><span data-stu-id="5c61f-197">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="5c61f-198">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5c61f-198">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="5c61f-199">Aggiornare le proprietà di uno specifico gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-199">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5c61f-200">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5c61f-200">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="5c61f-p116">Creare un nuovo gruppo di Office 365. Questo cmdlet fornisce un insieme minimo di parametri, per impostazione valori per le proprietà estese utilizzano Set-UnifiedGroup dopo aver creato il nuovo gruppo</span><span class="sxs-lookup"><span data-stu-id="5c61f-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="5c61f-203">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="5c61f-203">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="5c61f-204">Eliminare un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-204">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5c61f-205">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5c61f-205">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="5c61f-206">Recuperare informazioni sui appartenenze e il proprietario di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-206">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5c61f-207">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5c61f-207">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="5c61f-208">Aggiungere centinaia o migliaia di utenti o nuovi proprietari, a un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-208">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="5c61f-209">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="5c61f-209">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="5c61f-210">Rimuovere membri e proprietari da un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-210">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="5c61f-211">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="5c61f-211">For more information</span></span>

[<span data-ttu-id="5c61f-212">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="5c61f-212">Manage Office 365 with Office 365 PowerShell</span></span>](powershell/manage-office-365-with-office-365-powershell.md)
