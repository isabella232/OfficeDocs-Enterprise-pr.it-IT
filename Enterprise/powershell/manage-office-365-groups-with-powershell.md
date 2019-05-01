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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491760"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="00f16-103">Gestire Gruppi di Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="00f16-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="00f16-104">*Ultimo aggiornamento: 18 aprile 2018*</span><span class="sxs-lookup"><span data-stu-id="00f16-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="00f16-105">In questo articolo vengono illustrati i passaggi per eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00f16-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="00f16-106">Vengono inoltre elencati i cmdlet di PowerShell per i gruppi.</span><span class="sxs-lookup"><span data-stu-id="00f16-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="00f16-107">Per informazioni sulla gestione dei siti di SharePoint, vedere [gestire i siti di SharePoint Online tramite PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="00f16-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="00f16-108">Collegamento alle linee guida per l'utilizzo dei gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="00f16-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-109"></span></span>

<span data-ttu-id="00f16-110">Quando gli utenti [creano o modificano un gruppo in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), è possibile mostrargli un collegamento alle linee guida per l'utilizzo dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="00f16-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="00f16-111">Ad esempio, se si necessita di un prefisso o di un suffisso specifico da aggiungere al nome di un gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="00f16-112">Utilizzare PowerShell di Azure Active Directory per indirizzare gli utenti alle linee guida sull'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-112">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="00f16-113">Estrarre i [cmdlet di Azure Active Directory per la configurazione delle impostazioni di gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) e seguire la procedura descritta in **creare le impostazioni a livello di directory** per definire il collegamento ipertestuale linee guida per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="00f16-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="00f16-114">Dopo aver eseguito il cmdlet AAD, il collegamento alle linee guida verrà visualizzato dall'utente quando si crea o si modifica un gruppo in Outlook.</span><span class="sxs-lookup"><span data-stu-id="00f16-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Creare un nuovo gruppo con linee guida di utilizzo collegamento](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Fare clic su linee guida sull'utilizzo di gruppi per visualizzare le linee guida sui gruppi di Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="00f16-117">Consenti agli utenti di inviare messaggi come gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="00f16-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-118"></span></span>
  
<span data-ttu-id="00f16-119">Se si desidera abilitare i gruppi di Office 365 su "Invia come", utilizzare i cmdlet [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) e [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) per configurarlo.</span><span class="sxs-lookup"><span data-stu-id="00f16-119">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="00f16-120">Dopo aver abilitato questa impostazione, gli utenti di Office 365 Group possono utilizzare Outlook o Outlook sul Web per inviare e rispondere alla posta elettronica come gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-120">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="00f16-121">Gli utenti possono accedere al gruppo, creare un nuovo messaggio di posta elettronica e cambiare il campo "Invia come" all'indirizzo di posta elettronica del gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="00f16-122">([È possibile eseguire questa operazione anche nell'interfaccia di amministrazione di Exchange](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="00f16-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="00f16-123">Utilizzare lo script seguente, sostituendo \* \<GroupAlias\> \* con l'alias del gruppo che si desidera aggiornare e \* \<userAlias\> \* con l'alias dell'utente a cui si desidera concedere permssions.</span><span class="sxs-lookup"><span data-stu-id="00f16-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions.</span></span> <span data-ttu-id="00f16-124">[Connettersi a PowerShell di Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) per eseguire questo script.</span><span class="sxs-lookup"><span data-stu-id="00f16-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="00f16-125">Dopo l'esecuzione del cmdlet, gli utenti possono accedere a Outlook o Outlook sul Web per l'invio come gruppo, aggiungendo l'indirizzo di posta elettronica del gruppo al campo **da** .</span><span class="sxs-lookup"><span data-stu-id="00f16-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="00f16-126">Creare classificazioni per i gruppi di Office nell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="00f16-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="00f16-127">È possibile creare classificazioni che gli utenti dell'organizzazione possono impostare quando creano un gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-127">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="00f16-128">Ad esempio, è possibile consentire agli utenti di impostare "standard", "segreto" e "Top Secret" sui gruppi creati.</span><span class="sxs-lookup"><span data-stu-id="00f16-128">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="00f16-129">Le classificazioni di gruppo non vengono impostate per impostazione predefinita ed è necessario crearla affinché gli utenti lo configurano.</span><span class="sxs-lookup"><span data-stu-id="00f16-129">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="00f16-130">Utilizzare PowerShell di Azure Active Directory per indirizzare gli utenti alle linee guida per l'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-130">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="00f16-131">Estrarre i [cmdlet di Azure Active Directory per la configurazione delle impostazioni di gruppo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) e seguire la procedura descritta in **create settings at the directory Level** per definire la classificazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="00f16-132">Per associare una descrizione a ogni classificazione, è possibile utilizzare l'attributo Settings *ClassificationDescriptions* per definire.</span><span class="sxs-lookup"><span data-stu-id="00f16-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="00f16-133">dove la classificazione corrisponde alle stringhe presenti nella classificazione.</span><span class="sxs-lookup"><span data-stu-id="00f16-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="00f16-134">Esempio:</span><span class="sxs-lookup"><span data-stu-id="00f16-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="00f16-135">Dopo aver eseguito il cmdlet sopra Azure Active Directory per impostare la classificazione, eseguire il cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) se si desidera impostare la classificazione per un gruppo specifico.</span><span class="sxs-lookup"><span data-stu-id="00f16-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="00f16-136">O creare un nuovo gruppo con una classificazione.</span><span class="sxs-lookup"><span data-stu-id="00f16-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="00f16-137">Per altri dettagli sull'uso di PowerShell di Exchange Online vedere [Uso di PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) e [Connettersi a PowerShell di Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="00f16-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="00f16-138">Dopo aver abilitato queste impostazioni, il proprietario del gruppo sarà in grado di scegliere una classificazione dal menu a discesa in Outlook sul Web e Outlook e salvarla dalla pagina **modifica** gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Scegliere la classificazione di gruppo di Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="00f16-140">Nascondere i gruppi di Office 365 dall'elenco indirizzi globale</span><span class="sxs-lookup"><span data-stu-id="00f16-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="00f16-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-141"></span></span>

<span data-ttu-id="00f16-142">È possibile specificare se un gruppo di Office 365 viene visualizzato nell'elenco indirizzi globale (GAL) e negli altri elenchi nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="00f16-142">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="00f16-143">Ad esempio, se si dispone di un gruppo di reparto legale che non si desidera visualizzare nell'elenco degli indirizzi, è possibile impedire che il gruppo venga visualizzato in GAL.</span><span class="sxs-lookup"><span data-stu-id="00f16-143">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="00f16-144">Eseguire il cmdlet Set-Unified Group per nascondere l'elenco indirizzi di gruppo in questo modo:</span><span class="sxs-lookup"><span data-stu-id="00f16-144">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="00f16-145">Consenti solo agli utenti interni di inviare messaggi al gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="00f16-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-146"></span></span>

<span data-ttu-id="00f16-147">Se non si desidera che gli utenti di altre organizzazioni possano inviare messaggi di posta elettronica a un gruppo di Office 365, è possibile modificare le impostazioni per il gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-147">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="00f16-148">Permetterà solo agli utenti interni di inviare un messaggio di posta elettronica al gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-148">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="00f16-149">Se l'utente esterno tenta di inviare un messaggio al gruppo, verrà rifiutato.</span><span class="sxs-lookup"><span data-stu-id="00f16-149">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="00f16-150">Eseguire il cmdlet Set-UnifiedGroup per aggiornare questa impostazione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="00f16-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="00f16-151">Aggiungere suggerimenti messaggio ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="00f16-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-152"></span></span>

<span data-ttu-id="00f16-153">Ogni volta che un mittente tenta di inviare un messaggio di posta elettronica a un gruppo di Office 365, è possibile mostrargli un avviso messaggio.</span><span class="sxs-lookup"><span data-stu-id="00f16-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="00f16-154">Eseguire il cmdlet Set-Unified Group per aggiungere un avviso messaggio al gruppo:</span><span class="sxs-lookup"><span data-stu-id="00f16-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="00f16-155">Insieme a avviso messaggio, è anche possibile impostare MailTipTranslations, che specifica altre lingue per il avviso messaggio.</span><span class="sxs-lookup"><span data-stu-id="00f16-155">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="00f16-156">Si supponga di voler disporre della traduzione spagnola, quindi eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="00f16-156">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="00f16-157">Modificare il nome visualizzato del gruppo Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="00f16-158">Nome visualizzato consente di specificare il nome del gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-158">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="00f16-159">È possibile visualizzare questo nome nell'interfaccia di amministrazione di Exchange o nel portale di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-159">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="00f16-160">È possibile modificare il nome visualizzato del gruppo o assegnare un nome visualizzato a un gruppo di Office 365 esistente eseguendo il comando set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="00f16-160">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="00f16-161">Modificare l'impostazione predefinita dei gruppi di Office 365 per Outlook su pubblico o privato</span><span class="sxs-lookup"><span data-stu-id="00f16-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="00f16-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="00f16-162"></span></span>

<span data-ttu-id="00f16-163">I gruppi di Office 365 in Outlook vengono creati come privati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="00f16-163">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="00f16-164">Se l'organizzazione desidera che i gruppi di Office 365 vengano creati come pubblici per impostazione predefinita o di nuovo su privato, utilizzare la sintassi del cmdlet di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00f16-164">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="00f16-165">Per impostare su privato:</span><span class="sxs-lookup"><span data-stu-id="00f16-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="00f16-166">Per verificare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="00f16-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="00f16-167">Per ulteriori informazioni, vedere [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) e [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="00f16-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="00f16-168">Cmdlet per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="00f16-169">I cmdlet seguenti possono essere utilizzati con i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="00f16-170">**Nome cmdlet**</span><span class="sxs-lookup"><span data-stu-id="00f16-170">**Cmdlet name**</span></span>|<span data-ttu-id="00f16-171">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="00f16-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="00f16-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="00f16-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="00f16-173">Utilizzare questo cmdlet per cercare i gruppi di Office 365 esistenti e per visualizzare le proprietà dell'oggetto Group.</span><span class="sxs-lookup"><span data-stu-id="00f16-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="00f16-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="00f16-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="00f16-175">Aggiornare le proprietà di uno specifico gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="00f16-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="00f16-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="00f16-177">Creare un nuovo gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="00f16-177">Create a new Office 365 group.</span></span> <span data-ttu-id="00f16-178">Questo cmdlet fornisce un set di parametri minimo, per impostare i valori per le proprietà estese, utilizzare set-UnifiedGroup dopo aver creato il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="00f16-178">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="00f16-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="00f16-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="00f16-180">Eliminare un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="00f16-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="00f16-181">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="00f16-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="00f16-182">Recuperare le informazioni sull'appartenenza e sul proprietario di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="00f16-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="00f16-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="00f16-184">Aggiungere centinaia o migliaia di utenti o nuovi proprietari a un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="00f16-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="00f16-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="00f16-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="00f16-186">Rimuovere proprietari e membri da un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="00f16-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="00f16-187">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="00f16-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="00f16-188">Utilizzato per visualizzare le informazioni sulla foto utente associata a un account.</span><span class="sxs-lookup"><span data-stu-id="00f16-188">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="00f16-189">Le foto degli utenti vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="00f16-189">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="00f16-190">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="00f16-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="00f16-191">Utilizzato per associare una foto utente a un account.</span><span class="sxs-lookup"><span data-stu-id="00f16-191">Used to associate a user photo with an account.</span></span> <span data-ttu-id="00f16-192">Le foto degli utenti vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="00f16-192">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="00f16-193">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="00f16-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="00f16-194">Rimuovere la foto per un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="00f16-195">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="00f16-195">Related topics</span></span>

[<span data-ttu-id="00f16-196">Aggiornare le liste di distribuzione a gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="00f16-197">Gestire gli utenti autorizzati a creare gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="00f16-198">Gestire l'accesso degli utenti guest ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="00f16-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="00f16-199">Modificare l'appartenenza al gruppo statico in Dynamic in</span><span class="sxs-lookup"><span data-stu-id="00f16-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
