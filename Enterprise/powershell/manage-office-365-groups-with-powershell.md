---
title: Gestire Gruppi di Office 365 con PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords: CSH
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
ms.openlocfilehash: 7ebb3cfdfc6375cbc340c1fc3be37d59bcd9d4c8
ms.sourcegitcommit: c758588cf2b68de9291a362fd73ec9dc721d04d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2020
ms.locfileid: "44411063"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="30bd8-103">Gestire Gruppi di Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="30bd8-103">Manage Office 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="30bd8-104">In questo articolo vengono illustrati i passaggi per eseguire attività di gestione comuni per i gruppi di Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30bd8-104">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="30bd8-105">Vengono inoltre elencati i cmdlet di PowerShell per i gruppi.</span><span class="sxs-lookup"><span data-stu-id="30bd8-105">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="30bd8-106">Per informazioni sulla gestione dei siti di SharePoint, vedere [gestire i siti di SharePoint Online tramite PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span><span class="sxs-lookup"><span data-stu-id="30bd8-106">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="30bd8-107">Collegamento alle linee guida per l'utilizzo dei gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-107">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="30bd8-108"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-108"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="30bd8-109">Quando gli utenti [creano o modificano un gruppo in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), è possibile mostrargli un collegamento alle linee guida per l'utilizzo dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="30bd8-109">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="30bd8-110">Ad esempio, se si necessita di un prefisso o di un suffisso specifico da aggiungere al nome di un gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-110">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="30bd8-111">Utilizzare PowerShell di Azure Active Directory per indirizzare gli utenti alle linee guida sull'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-111">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span> <span data-ttu-id="30bd8-112">Estrarre i [cmdlet di Azure Active Directory per la configurazione delle impostazioni di gruppo](https://go.microsoft.com/fwlink/?LinkID=827484) e seguire la procedura descritta in **creare le impostazioni a livello di directory** per definire il collegamento ipertestuale linee guida per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-112">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="30bd8-113">Dopo aver eseguito il cmdlet AAD, il collegamento alle linee guida verrà visualizzato dall'utente quando si crea o si modifica un gruppo in Outlook.</span><span class="sxs-lookup"><span data-stu-id="30bd8-113">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![Creare un nuovo gruppo con linee guida di utilizzo collegamento](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![Fare clic su linee guida sull'utilizzo di gruppi per visualizzare le linee guida sui gruppi di Office 365](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="30bd8-116">Consenti agli utenti di inviare messaggi come gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-116">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="30bd8-117"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-117"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="30bd8-118">Se si desidera abilitare i gruppi di Office 365 su "Invia come", utilizzare i cmdlet [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) e [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) per configurarlo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-118">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="30bd8-119">Dopo aver abilitato questa impostazione, gli utenti di Office 365 Group possono utilizzare Outlook o Outlook sul Web per inviare e rispondere alla posta elettronica come gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-119">Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group.</span></span> <span data-ttu-id="30bd8-120">Gli utenti possono accedere al gruppo, creare un nuovo messaggio di posta elettronica e cambiare il campo "Invia come" all'indirizzo di posta elettronica del gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-120">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="30bd8-121">([È possibile eseguire questa operazione anche nell'interfaccia di amministrazione di Exchange](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).</span><span class="sxs-lookup"><span data-stu-id="30bd8-121">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="30bd8-122">Utilizzare lo script seguente, sostituendo *\<GroupAlias\>* con l'alias del gruppo che si desidera aggiornare e *\<UserAlias\>* con l'alias dell'utente a cui si desidera concedere le autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="30bd8-122">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="30bd8-123">[Connettersi a PowerShell di Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) per eseguire questo script.</span><span class="sxs-lookup"><span data-stu-id="30bd8-123">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="30bd8-124">Dopo l'esecuzione del cmdlet, gli utenti possono accedere a Outlook o Outlook sul Web per l'invio come gruppo, aggiungendo l'indirizzo di posta elettronica del gruppo al campo **da** .</span><span class="sxs-lookup"><span data-stu-id="30bd8-124">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="30bd8-125">Creare classificazioni per i gruppi di Office nell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="30bd8-125">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="30bd8-126">È possibile creare etichette di riservatezza che gli utenti dell'organizzazione possono impostare quando creano un gruppo di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-126">You can create sensitivity labels that the users in your organization can set when they create an Microsoft 365 Group.</span></span> <span data-ttu-id="30bd8-127">Se si desidera classificare i gruppi, è consigliabile utilizzare le etichette di riservatezza anziché la caratteristica classificazione gruppi precedenti.</span><span class="sxs-lookup"><span data-stu-id="30bd8-127">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="30bd8-128">Per informazioni sull'utilizzo di etichette di riservatezza, vedere [use Sensitivity labels to protect content in Microsoft teams, microsoft 365 Groups e SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span><span class="sxs-lookup"><span data-stu-id="30bd8-128">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30bd8-129">Se attualmente si utilizzano le etichette di classificazione, non saranno più disponibili per gli utenti che creano gruppi una volta abilitate le etichette di riservatezza.</span><span class="sxs-lookup"><span data-stu-id="30bd8-129">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="30bd8-130">È comunque possibile utilizzare la caratteristica classificazione gruppi precedenti.</span><span class="sxs-lookup"><span data-stu-id="30bd8-130">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="30bd8-131">È possibile creare classificazioni che gli utenti dell'organizzazione possono impostare quando creano un gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-131">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="30bd8-132">Ad esempio, è possibile consentire agli utenti di impostare "standard", "segreto" e "Top Secret" sui gruppi creati.</span><span class="sxs-lookup"><span data-stu-id="30bd8-132">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="30bd8-133">Le classificazioni di gruppo non vengono impostate per impostazione predefinita ed è necessario crearla affinché gli utenti lo configurano.</span><span class="sxs-lookup"><span data-stu-id="30bd8-133">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="30bd8-134">Utilizzare PowerShell di Azure Active Directory per indirizzare gli utenti alle linee guida per l'utilizzo dell'organizzazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-134">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="30bd8-135">Estrarre i [cmdlet di Azure Active Directory per la configurazione delle impostazioni di gruppo](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) e seguire la procedura descritta in **create settings at the directory Level** per definire la classificazione per i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-135">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="30bd8-136">Per associare una descrizione a ogni classificazione, è possibile utilizzare l'attributo Settings *ClassificationDescriptions* per definire.</span><span class="sxs-lookup"><span data-stu-id="30bd8-136">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="30bd8-137">dove la classificazione corrisponde alle stringhe presenti nella classificazione.</span><span class="sxs-lookup"><span data-stu-id="30bd8-137">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="30bd8-138">Esempio:</span><span class="sxs-lookup"><span data-stu-id="30bd8-138">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="30bd8-139">Dopo aver eseguito il cmdlet sopra Azure Active Directory per impostare la classificazione, eseguire il cmdlet [set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) se si desidera impostare la classificazione per un gruppo specifico.</span><span class="sxs-lookup"><span data-stu-id="30bd8-139">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="30bd8-140">O creare un nuovo gruppo con una classificazione.</span><span class="sxs-lookup"><span data-stu-id="30bd8-140">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="30bd8-141">Per altri dettagli sull'uso di PowerShell di Exchange Online vedere [Uso di PowerShell con Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) e [Connettersi a PowerShell di Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="30bd8-141">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="30bd8-142">Dopo aver abilitato queste impostazioni, il proprietario del gruppo sarà in grado di scegliere una classificazione dal menu a discesa in Outlook sul Web e Outlook e salvarla dalla pagina **modifica** gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-142">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Scegliere la classificazione di gruppo di Office 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="30bd8-144">Nascondere i gruppi di Office 365 dall'elenco indirizzi globale</span><span class="sxs-lookup"><span data-stu-id="30bd8-144">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="30bd8-145"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-145"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="30bd8-146">È possibile specificare se un gruppo di Office 365 viene visualizzato nell'elenco indirizzi globale (GAL) e negli altri elenchi nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="30bd8-146">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="30bd8-147">Ad esempio, se si dispone di un gruppo di reparto legale che non si desidera visualizzare nell'elenco degli indirizzi, è possibile impedire che il gruppo venga visualizzato in GAL.</span><span class="sxs-lookup"><span data-stu-id="30bd8-147">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="30bd8-148">Eseguire il cmdlet Set-Unified Group per nascondere l'elenco indirizzi di gruppo in questo modo:</span><span class="sxs-lookup"><span data-stu-id="30bd8-148">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="30bd8-149">Consenti solo agli utenti interni di inviare messaggi al gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-149">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="30bd8-150"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-150"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="30bd8-151">Se non si desidera che gli utenti di altre organizzazioni possano inviare messaggi di posta elettronica a un gruppo di Office 365, è possibile modificare le impostazioni per il gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-151">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="30bd8-152">Permetterà solo agli utenti interni di inviare un messaggio di posta elettronica al gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-152">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="30bd8-153">Se l'utente esterno tenta di inviare un messaggio al gruppo, verrà rifiutato.</span><span class="sxs-lookup"><span data-stu-id="30bd8-153">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="30bd8-154">Eseguire il cmdlet Set-UnifiedGroup per aggiornare questa impostazione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="30bd8-154">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="30bd8-155">Aggiungere suggerimenti messaggio ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-155">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="30bd8-156"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-156"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="30bd8-157">Ogni volta che un mittente tenta di inviare un messaggio di posta elettronica a un gruppo di Office 365, è possibile mostrargli un avviso messaggio.</span><span class="sxs-lookup"><span data-stu-id="30bd8-157">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="30bd8-158">Eseguire il cmdlet Set-Unified Group per aggiungere un avviso messaggio al gruppo:</span><span class="sxs-lookup"><span data-stu-id="30bd8-158">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="30bd8-159">Insieme a avviso messaggio, è anche possibile impostare MailTipTranslations, che specifica altre lingue per il avviso messaggio.</span><span class="sxs-lookup"><span data-stu-id="30bd8-159">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="30bd8-160">Si supponga di voler disporre della traduzione spagnola, quindi eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="30bd8-160">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="30bd8-161">Modificare il nome visualizzato del gruppo Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-161">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="30bd8-162">Nome visualizzato consente di specificare il nome del gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-162">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="30bd8-163">È possibile visualizzare questo nome nell'interfaccia di amministrazione di Exchange o nel portale di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-163">You can see this name in your exchange admin center or Office 365 admin portal.</span></span> <span data-ttu-id="30bd8-164">È possibile modificare il nome visualizzato del gruppo o assegnare un nome visualizzato a un gruppo di Office 365 esistente eseguendo il comando set-UnifiedGroup:</span><span class="sxs-lookup"><span data-stu-id="30bd8-164">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="30bd8-165">Modificare l'impostazione predefinita dei gruppi di Office 365 per Outlook su pubblico o privato</span><span class="sxs-lookup"><span data-stu-id="30bd8-165">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="30bd8-166"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="30bd8-166"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="30bd8-167">I gruppi di Office 365 in Outlook vengono creati come privati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="30bd8-167">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="30bd8-168">Se l'organizzazione desidera che i gruppi di Office 365 vengano creati come pubblici per impostazione predefinita o di nuovo su privato, utilizzare la sintassi del cmdlet di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="30bd8-168">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="30bd8-169">Per impostare su privato:</span><span class="sxs-lookup"><span data-stu-id="30bd8-169">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="30bd8-170">Per verificare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="30bd8-170">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="30bd8-171">Per ulteriori informazioni, vedere [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) e [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span><span class="sxs-lookup"><span data-stu-id="30bd8-171">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="30bd8-172">Cmdlet per i gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-172">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="30bd8-173">I cmdlet seguenti possono essere utilizzati con i gruppi di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-173">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="30bd8-174">**Nome cmdlet**</span><span class="sxs-lookup"><span data-stu-id="30bd8-174">**Cmdlet name**</span></span>|<span data-ttu-id="30bd8-175">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="30bd8-175">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="30bd8-176">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="30bd8-176">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="30bd8-177">Utilizzare questo cmdlet per cercare i gruppi di Office 365 esistenti e per visualizzare le proprietà dell'oggetto Group.</span><span class="sxs-lookup"><span data-stu-id="30bd8-177">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="30bd8-178">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="30bd8-178">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="30bd8-179">Aggiornare le proprietà di uno specifico gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-179">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-180">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="30bd8-180">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="30bd8-181">Creare un nuovo gruppo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="30bd8-181">Create a new Office 365 group.</span></span> <span data-ttu-id="30bd8-182">Questo cmdlet fornisce un set di parametri minimo, per impostare i valori per le proprietà estese, utilizzare set-UnifiedGroup dopo aver creato il nuovo gruppo.</span><span class="sxs-lookup"><span data-stu-id="30bd8-182">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-183">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="30bd8-183">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="30bd8-184">Eliminare un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="30bd8-184">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-185">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="30bd8-185">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="30bd8-186">Recuperare le informazioni sull'appartenenza e sul proprietario di un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-186">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-187">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="30bd8-187">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="30bd8-188">Aggiungere centinaia o migliaia di utenti o nuovi proprietari a un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="30bd8-188">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-189">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="30bd8-189">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="30bd8-190">Rimuovere proprietari e membri da un gruppo di Office 365 esistente</span><span class="sxs-lookup"><span data-stu-id="30bd8-190">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="30bd8-191">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="30bd8-191">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="30bd8-192">Utilizzato per visualizzare le informazioni sulla foto utente associata a un account.</span><span class="sxs-lookup"><span data-stu-id="30bd8-192">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="30bd8-193">Le foto degli utenti vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="30bd8-193">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="30bd8-194">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="30bd8-194">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="30bd8-195">Utilizzato per associare una foto utente a un account.</span><span class="sxs-lookup"><span data-stu-id="30bd8-195">Used to associate a user photo with an account.</span></span> <span data-ttu-id="30bd8-196">Le foto degli utenti vengono archiviate in Active Directory</span><span class="sxs-lookup"><span data-stu-id="30bd8-196">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="30bd8-197">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="30bd8-197">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="30bd8-198">Rimuovere la foto per un gruppo di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-198">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="30bd8-199">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="30bd8-199">Related topics</span></span>

[<span data-ttu-id="30bd8-200">Aggiornare le liste di distribuzione a gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-200">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="30bd8-201">Gestire gli utenti autorizzati a creare gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-201">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="30bd8-202">Gestire l'accesso degli utenti guest ai gruppi di Office 365</span><span class="sxs-lookup"><span data-stu-id="30bd8-202">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="30bd8-203">Modificare l'appartenenza al gruppo statico in Dynamic in</span><span class="sxs-lookup"><span data-stu-id="30bd8-203">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
