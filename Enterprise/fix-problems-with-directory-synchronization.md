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
ms.openlocfilehash: e83ca495ca96ac41fb2f79775c3d5970a6b538fb
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085395"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="a4e75-103">Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="a4e75-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="a4e75-p101">Con la sincronizzazione della directory, è possibile continuare a gestire gli utenti e i gruppi locali e sincronizzare aggiunte, eliminazioni e modifiche al cloud. Tuttavia, il programma di installazione è un po' complicato e a volte può essere difficile identificare l'origine dei problemi. Sono disponibili risorse utili per identificare i potenziali problemi e correggerli.</span><span class="sxs-lookup"><span data-stu-id="a4e75-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="a4e75-107">Come si fa a sapere se c'è qualcosa di sbagliato?</span><span class="sxs-lookup"><span data-stu-id="a4e75-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="a4e75-108">La prima indicazione che qualcosa è errato è quando il riquadro Stato DirSync nell'interfaccia di amministrazione di Office 365 indica che si è verificato un problema:</span><span class="sxs-lookup"><span data-stu-id="a4e75-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Riquadro di stato DirSync nell'anteprima dell'interfaccia di amministrazione](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="a4e75-p102">Riceverà anche una mail (alla posta elettronica alternativa e alla posta elettronica di amministrazione) da Office 365 che indica che il tenant ha riscontrato errori di sincronizzazione della directory. Per ulteriori informazioni, vedere [identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="a4e75-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="a4e75-112">Come si ottiene lo strumento di Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="a4e75-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="a4e75-p103">nell'interfaccia di amministrazione di Office 365, passare a \* \* users \> \* \* **Active users**. Fare clic sul menu **altro** e selezionare **sincronizzazione directory**.</span><span class="sxs-lookup"><span data-stu-id="a4e75-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="a4e75-116">nella vecchia interfaccia di amministrazione di Office 365, passare \*\*\*\* \> a utenti **attivi**e selezionare **configura** accanto a sincronizzazione di **active Directory**.</span><span class="sxs-lookup"><span data-stu-id="a4e75-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Scegliere Configura accanto a sincronizzazione di Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="a4e75-118">Seguire le istruzioni riportate [nella procedura guidata](set-up-directory-synchronization.md) per scaricare Azure ad Connect.</span><span class="sxs-lookup"><span data-stu-id="a4e75-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="a4e75-119">Se si sta ancora utilizzando Azure Active Directory Sync (DirSync), vedere [come risolvere i problemi relativi all'installazione dello strumento di sincronizzazione di Azure Active Directory e ai messaggi di errore della procedura guidata di configurazione in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema da installare dirsync, le autorizzazioni necessarie e come risolvere gli errori più comuni.</span><span class="sxs-lookup"><span data-stu-id="a4e75-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="a4e75-120">Per eseguire l'aggiornamento da Azure Active Directory Sync ad Azure AD Connect, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="a4e75-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="a4e75-121">Risoluzione delle cause comuni dei problemi relativi alla sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="a4e75-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="a4e75-122">**Gli oggetti sincronizzati non vengono visualizzati o aggiornati online oppure ricevo segnalazioni di errori di sincronizzazione dal servizio.**</span><span class="sxs-lookup"><span data-stu-id="a4e75-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="a4e75-123">Sincronizzazione delle identità e resilienza degli attributi duplicati</span><span class="sxs-lookup"><span data-stu-id="a4e75-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="a4e75-124">**Ho un avviso nell'interfaccia di amministrazione di Office 365 o ricevo messaggi di posta elettronica automatici che non è stato verificato un evento di sincronizzazione recente**</span><span class="sxs-lookup"><span data-stu-id="a4e75-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="a4e75-125">Risoluzione dei problemi relativi alla connettività con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="a4e75-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="a4e75-126">Account e autorizzazioni di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="a4e75-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="a4e75-127">Sincronizzazione di Azure AD Connect: informazioni su come gestire l'account di servizio di Azure AD</span><span class="sxs-lookup"><span data-stu-id="a4e75-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="a4e75-128">La sincronizzazione della directory in Azure Active Directory si interrompe o si avverte che la sincronizzazione non è registrata in più di un giorno.</span><span class="sxs-lookup"><span data-stu-id="a4e75-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="a4e75-129">**Gli hash delle password non sono sincronizzati oppure viene visualizzato un avviso nell'interfaccia di amministrazione di Office 365 che non è stata eseguita una sincronizzazione degli hash delle password recente**</span><span class="sxs-lookup"><span data-stu-id="a4e75-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="a4e75-130">Implementazione della sincronizzazione degli hash delle password con Azure AD Connect Sync</span><span class="sxs-lookup"><span data-stu-id="a4e75-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="a4e75-131">**Viene visualizzato un avviso che ha superato la quota oggetto**</span><span class="sxs-lookup"><span data-stu-id="a4e75-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="a4e75-p104">È presente una quota dell'oggetto integrata che consente di proteggere il servizio. Se nella directory sono presenti troppi oggetti che devono essere sincronizzati con Office 365, è necessario contattare il [supporto per i prodotti aziendali](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per aumentare la quota.</span><span class="sxs-lookup"><span data-stu-id="a4e75-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="a4e75-134">**Devo sapere quali attributi vengono sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="a4e75-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="a4e75-135">È possibile trovare un elenco di tutti gli attributi sincronizzati tra l'ambiente locale e il cloud [direttamente qui](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="a4e75-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="a4e75-136">**Non è possibile gestire o rimuovere gli oggetti che sono stati sincronizzati nel cloud**</span><span class="sxs-lookup"><span data-stu-id="a4e75-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="a4e75-p105">Si è pronti per la gestione degli oggetti solo nel cloud? Oppure esiste un oggetto che è stato eliminato in locale, ma è bloccato nel cloud? Esaminare gli [errori di risoluzione dei problemi durante](https://go.microsoft.com/fwlink/p/?linkid=842044) l'articolo relativo alla sincronizzazione e al [supporto tecnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) per informazioni su come risolvere questi problemi.</span><span class="sxs-lookup"><span data-stu-id="a4e75-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="a4e75-140">**Ho ricevuto un messaggio di errore che mi informa che la mia azienda ha superato il numero di oggetti che possono essere sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="a4e75-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="a4e75-141">È possibile leggere altre informazioni su questo problema [qui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="a4e75-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="a4e75-142">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="a4e75-142">Other resources</span></span>

- [<span data-ttu-id="a4e75-143">Script per correggere i nomi dell'entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="a4e75-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="a4e75-144">Come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="a4e75-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="a4e75-145">Script per contare gli oggetti totali sincronizzati</span><span class="sxs-lookup"><span data-stu-id="a4e75-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="a4e75-146">Risoluzione dei problemi di ADFS 2,0</span><span class="sxs-lookup"><span data-stu-id="a4e75-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="a4e75-147">Utilizzo di PowerShell per correggere gli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica</span><span class="sxs-lookup"><span data-stu-id="a4e75-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="a4e75-148">Utilizzo di PowerShell per correggere l'UPN duplicato</span><span class="sxs-lookup"><span data-stu-id="a4e75-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="a4e75-149">Utilizzo di PowerShell per correggere gli indirizzi di posta elettronica duplicati</span><span class="sxs-lookup"><span data-stu-id="a4e75-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="a4e75-150">Strumenti di diagnostica</span><span class="sxs-lookup"><span data-stu-id="a4e75-150">Diagnostic tools</span></span>

<span data-ttu-id="a4e75-p106">[Lo strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene utilizzato per eseguire l'individuazione e la correzione degli oggetti Identity e dei relativi attributi in un ambiente Active Directory locale in preparazione per la migrazione a Office 365. IDFix è destinato agli amministratori di Active Directory responsabili di DirSync con il servizio Office 365.</span><span class="sxs-lookup"><span data-stu-id="a4e75-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="a4e75-153">[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4e75-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>