---
title: Gestire Gruppi di Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
description: Informazioni su come eseguire attività di gestione comuni per i gruppi di Office 365 in Microsoft PowerShell.
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760058"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="e964c-103">Gestire Gruppi di Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e964c-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="e964c-104">*Ultimo aprile 18 aggiornato, 2018*</span><span class="sxs-lookup"><span data-stu-id="e964c-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="e964c-p101">In questo articolo viene illustrato come eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell. Inoltre, sono elencati i cmdlet di PowerShell per i gruppi. Per informazioni sulla gestione dei siti di SharePoint, vedere [siti di gestire SharePoint Online mediante PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="e964c-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="e964c-108">Collegarsi alle linee guida sull'utilizzo di gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="e964c-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-109"></span></span>

<span data-ttu-id="e964c-p102">Quando gli utenti in [creare o modificare un gruppo in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), è possibile mostrare loro un collegamento a indicazioni per l'utilizzo dell'organizzazione. Ad esempio, se si richiede un prefisso specifico o suffisso da aggiungere al nome di un gruppo.</span><span class="sxs-lookup"><span data-stu-id="e964c-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="e964c-p103">Utilizzare Azure Active Directory PowerShell per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365. Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) ed eseguire la procedura in **Create le impostazioni a livello di directory** per definire il collegamento ipertestuale alle linee guida sull'utilizzo. Una volta eseguire il cmdlet AAD, dell'utente verrà visualizzato il collegamento alle istruzioni quando creare o modificare un gruppo di Outlook.</span><span class="sxs-lookup"><span data-stu-id="e964c-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Creare un nuovo gruppo con un utilizzo linee guida per il collegamento](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Linee guida per gruppi di istruzioni per l'uso fare clic su gruppo per visualizzare le organizzazioni di Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="e964c-117">Consentire agli utenti di inviare il gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="e964c-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-118"></span></span>
  
<span data-ttu-id="e964c-p104">Se si desidera abilitare i gruppi di Office 365 a "Invia come", utilizzare il cmdlet [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) e [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) per configurare questa impostazione. Una volta che si attiva questa impostazione, gli utenti di Office 365 group consentono Outlook o Outlook sul web per inviare e rispondere al messaggio di posta elettronica del gruppo di Office 365. Gli utenti possono accedere al gruppo di creare un nuovo messaggio di posta elettronica e modificare il campo "Invia come" all'indirizzo di posta elettronica del gruppo.</span><span class="sxs-lookup"><span data-stu-id="e964c-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="e964c-122">([È possibile effettuare questa operazione anche nell'interfaccia di amministrazione di Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="e964c-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="e964c-p105">Utilizzare il seguente script, sostituendo \* \<GroupAlias\> \* con l'alias del gruppo che si desidera aggiornare, e \* \<UserAlias\> \* con l'alias dell'utente a cui si desidera concedere le autorizzazioni. [Connessione a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) per eseguire lo script.</span><span class="sxs-lookup"><span data-stu-id="e964c-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="e964c-125">Una volta che viene eseguito il cmdlet, gli utenti possono accedere a Outlook o Outlook sul web per inviare il gruppo, aggiungendo l'indirizzo di posta elettronica del gruppo nel campo **da** .</span><span class="sxs-lookup"><span data-stu-id="e964c-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="e964c-126">Creare le classificazioni per i gruppi di Office all'interno dell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="e964c-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="e964c-p106">È possibile creare le classificazioni che gli utenti dell'organizzazione possono impostare durante la creazione di un gruppo di Office 365. Ad esempio, è possibile consentire agli utenti di impostare "Standard", "Secret" e "Top Secret" nella creazione di gruppi. Classificazioni gruppo non sono specificate per impostazione predefinita e si desidera creare in modo che gli utenti per l'impostazione. Utilizzare PowerShell di Azure Active Directory per associare gli utenti a indicazioni per l'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e964c-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="e964c-131">Estrarre [i cmdlet di Azure Active Directory per la configurazione delle impostazioni del gruppo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) e seguire i passaggi descritti in **Crea impostazioni a livello di directory** per definire la classificazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e964c-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="e964c-132">Per associare una descrizione per ciascuna delle quali che è possibile utilizzare le impostazioni dell'attributo *ClassificationDescriptions* per definire.</span><span class="sxs-lookup"><span data-stu-id="e964c-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="e964c-133">cui classificazione corrisponde le stringhe del ClassificationList.</span><span class="sxs-lookup"><span data-stu-id="e964c-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="e964c-134">Esempio:</span><span class="sxs-lookup"><span data-stu-id="e964c-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="e964c-135">Dopo aver eseguito il cmdlet di Azure Active Directory sopra per impostare la classificazione, eseguire il cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) se si desidera impostare la classificazione per un gruppo specifico.</span><span class="sxs-lookup"><span data-stu-id="e964c-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="e964c-136">Oppure creare un nuovo gruppo con una classificazione.</span><span class="sxs-lookup"><span data-stu-id="e964c-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="e964c-137">Per altri dettagli sull'uso di PowerShell di Exchange Online vedere [Uso di PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) e [Connettersi a PowerShell di Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="e964c-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="e964c-138">Dopo che queste impostazioni sono abilitate, il proprietario del gruppo saranno in grado di scegliere una classificazione da Outlook sul Web e Outlook dal menu a discesa e salvarlo nella pagina **Modifica** gruppo.</span><span class="sxs-lookup"><span data-stu-id="e964c-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Scegliere la classificazione di gruppo di Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="e964c-140">Nascondere gruppi di Office 365 dall'elenco indirizzi globale</span><span class="sxs-lookup"><span data-stu-id="e964c-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="e964c-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-141"></span></span>

<span data-ttu-id="e964c-p107">È possibile specificare se un gruppo di Office 365 viene visualizzato nell'elenco indirizzi globale (GAL) e altri elenchi all'interno dell'organizzazione. Se si dispone di un gruppo di reparto legale che non si desidera venga visualizzata nell'elenco di indirizzi, ad esempio, è possibile interrompere gruppo vengano visualizzate nell'elenco indirizzi globale. Eseguire il cmdlet gruppo Set-Unified per nascondere il gruppo dall'elenco di indirizzi simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="e964c-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="e964c-145">Consentire solo gli utenti interni inviare messaggi al gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="e964c-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-146"></span></span>

<span data-ttu-id="e964c-p108">Se non si desidera agli utenti di altre organizzazioni di inviare posta elettronica a un gruppo di Office 365, è possibile modificare le impostazioni per tale gruppo. Sarà possibile solo gli utenti interni inviare un messaggio di posta elettronica al gruppo. Utente esterno tenta di inviare messaggi a tale gruppo verranno rifiutati.</span><span class="sxs-lookup"><span data-stu-id="e964c-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="e964c-150">Eseguire il cmdlet Set-UnifiedGroup per aggiornare questa impostazione, simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="e964c-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="e964c-151">Aggiungere i suggerimenti per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="e964c-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-152"></span></span>

<span data-ttu-id="e964c-153">Ogni volta che un mittente tenta di inviare un messaggio di posta elettronica a un gruppo di Office 365, è possibile visualizzare un suggerimento messaggio a loro.</span><span class="sxs-lookup"><span data-stu-id="e964c-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="e964c-154">Eseguire il cmdlet gruppo Set-Unified per aggiungere un suggerimento per il gruppo:</span><span class="sxs-lookup"><span data-stu-id="e964c-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="e964c-p109">Insieme suggerimento, è inoltre possibile impostare MailTipTranslations, che consente di specificare ulteriori lingue per il suggerimento. Si supponga che si desidera avere la traduzione spagnola, quindi eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="e964c-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="e964c-157">Modificare il nome visualizzato del gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="e964c-p110">DisplayName specifica il nome del gruppo di Office 365. È possibile visualizzare il nome nell'interfaccia di amministrazione di exchange o del portale di amministrazione di Office 365. È possibile modificare il nome visualizzato del gruppo o assegnare un nome visualizzato per un gruppo di Office 365 esistente eseguendo il comando Set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="e964c-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="e964c-161">Modificare l'impostazione predefinita dei gruppi di Office 365 per Outlook pubblici o privati</span><span class="sxs-lookup"><span data-stu-id="e964c-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="e964c-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="e964c-162"></span></span>

<span data-ttu-id="e964c-p111">Office 365 gruppi in Outlook vengono creati come privati per impostazione predefinita. Se l'organizzazione intende Office 365 gruppi da creare come pubblico per impostazione predefinita (o su Private), utilizzare la sintassi seguente cmdlet PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e964c-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="e964c-165">Per impostare su privata:</span><span class="sxs-lookup"><span data-stu-id="e964c-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="e964c-166">Per verificare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="e964c-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="e964c-167">Per ulteriori informazioni, vedere [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) e [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="e964c-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="e964c-168">Cmdlet per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="e964c-169">I cmdlet seguenti possono essere utilizzati con i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e964c-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="e964c-170">**Nome cmdlet**</span><span class="sxs-lookup"><span data-stu-id="e964c-170">**Cmdlet name**</span></span>|<span data-ttu-id="e964c-171">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="e964c-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="e964c-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e964c-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="e964c-173">Utilizzare questo cmdlet per cercare i gruppi di esistenti Office 365 e per visualizzare le proprietà dell'oggetto group</span><span class="sxs-lookup"><span data-stu-id="e964c-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="e964c-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e964c-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="e964c-175">Aggiornare le proprietà di uno specifico gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e964c-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e964c-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="e964c-p112">Creare un nuovo gruppo di Office 365. Questo cmdlet fornisce un insieme minimo di parametri, per impostazione valori per le proprietà estese utilizzano Set-UnifiedGroup dopo aver creato il nuovo gruppo</span><span class="sxs-lookup"><span data-stu-id="e964c-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="e964c-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="e964c-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="e964c-180">Eliminare un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e964c-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e964c-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="e964c-182">Recuperare informazioni sui appartenenze e il proprietario di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e964c-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e964c-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="e964c-184">Aggiungere centinaia o migliaia di utenti o nuovi proprietari, a un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e964c-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="e964c-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="e964c-186">Rimuovere membri e proprietari da un gruppo di esistente Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="e964c-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e964c-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="e964c-p113">Consente di visualizzare le informazioni relative alle foto utente associata a un account. Foto dell'utente vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="e964c-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e964c-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e964c-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="e964c-p114">Consente di associare una foto utente con un account. Foto dell'utente vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="e964c-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="e964c-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="e964c-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="e964c-194">Rimuovere la foto di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="e964c-195">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="e964c-195">Related topics</span></span>

[<span data-ttu-id="e964c-196">Elenchi di distribuzione dell'aggiornamento a Office 365 gruppi</span><span class="sxs-lookup"><span data-stu-id="e964c-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="e964c-197">Gestire chi può creare gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="e964c-198">Gestire l'accesso degli utenti guest ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="e964c-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="e964c-199">Modificare l'appartenenza al gruppo statico dinamico in</span><span class="sxs-lookup"><span data-stu-id="e964c-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
