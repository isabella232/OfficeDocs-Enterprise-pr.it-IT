---
title: Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
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
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541188"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="4cb75-103">Risoluzione dei problemi relativi alla sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="4cb75-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="4cb75-p101">Con la sincronizzazione delle directory, è possibile continuare a gestire utenti e gruppi in locale e sincronizzare aggiunte, eliminazioni e le modifiche nel cloud. Ma il programma di installazione è complicato e in alcuni casi può risultare difficile identificare l'origine dei problemi. Sono disponibili risorse per individuare possibili problemi e correggerli.</span><span class="sxs-lookup"><span data-stu-id="4cb75-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="4cb75-107">Come sapere se si verificano problemi?</span><span class="sxs-lookup"><span data-stu-id="4cb75-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="4cb75-108">Il primo segnale del fatto che si verificano problemi è la porzione di stato di DirSync nell'interfaccia di amministrazione di Office 365 indicato che si è verificato un problema:</span><span class="sxs-lookup"><span data-stu-id="4cb75-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![Lo stato di DirSync affiancate nella visualizzazione Anteprima di amministrazione centrale](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="4cb75-p102">Inoltre, verrà visualizzato un messaggio di posta (per il posta elettronica alternativi e per la posta elettronica admin) da Office 365 che indica che il tenant ha rilevato errori di sincronizzazione della directory. Per ulteriori informazioni, vedere [gli errori di sincronizzazione directory di identità in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="4cb75-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="4cb75-112">Come ottenere strumento connettersi Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4cb75-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="4cb75-p103">Nell'interfaccia di amministrazione di Office 365 accedere a * * utenti * * \> **utenti attivi**. Fare clic sul menu **altre** e seleziona **la sincronizzazione delle Directory**.</span><span class="sxs-lookup"><span data-stu-id="4cb75-p103">In the Office 365 admin center, navigate to ** Users ** \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Nel menu di più, scegliere la sincronizzazione delle Directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="4cb75-116">Nell'interfaccia di amministrazione di Office 365 precedente, accedere a **utenti** \> **Utenti attivi**e selezionare **impostare** accanto a **sincronizzazione di Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="4cb75-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Scegli Configura accanto a sincronizzazione di Active Directory](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="4cb75-118">Seguire le [istruzioni della procedura guidata](set-up-directory-synchronization.md) per scaricare Connetti Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="4cb75-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="4cb75-119">Se si sta ancora utilizzando Azure sincronizzazione di Active Directory (DirSync), dare uno sguardo le modalità [di risoluzione dei problemi relativi a messaggi di errore di configurazione guidata in Office 365 e Azure Active Directory Sync Tool installazione](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema per l'installazione dirsync, le autorizzazioni che necessarie e come risolvere gli errori più comuni.</span><span class="sxs-lookup"><span data-stu-id="4cb75-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="4cb75-120">Per aggiornare di sincronizzazione di Azure Active Directory Connetti Azure Active Directory, vedere [le istruzioni per l'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="4cb75-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="4cb75-121">Risoluzione dei comuni causa dei problemi relativi alla sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="4cb75-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="4cb75-122">**Oggetti sincronizzati non vengono visualizzate o si aggiorna in linea o ricezione di segnalazioni di errori di sincronizzazione dal servizio.**</span><span class="sxs-lookup"><span data-stu-id="4cb75-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="4cb75-123">Resilienza dei attributo duplicati e sincronizzazione delle identità</span><span class="sxs-lookup"><span data-stu-id="4cb75-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="4cb75-124">**Si dispone di un avviso nell'interfaccia di amministrazione di Office 365 o riceve automatizzate messaggi di posta elettronica non è stato un evento di sincronizzazione di recente**</span><span class="sxs-lookup"><span data-stu-id="4cb75-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="4cb75-125">Risoluzione dei problemi di connettività di Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="4cb75-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="4cb75-126">Autorizzazioni e gli account di Active Directory connettersi Azure</span><span class="sxs-lookup"><span data-stu-id="4cb75-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="4cb75-127">Sincronizzazione di Active Directory Connetti Azure: come gestire l'account del servizio di Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4cb75-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="4cb75-128">Sincronizzazione di directory di interruzioni di Azure Active Directory o si sta avvisati che sincronizzazione non è registrato in più di un giorno</span><span class="sxs-lookup"><span data-stu-id="4cb75-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="4cb75-129">**Non sono sincronizzare gli hash password o vengono visualizzati gli avvisi in interfaccia di amministrazione di Office 365 non è stata una sincronizzazione hash password recenti**</span><span class="sxs-lookup"><span data-stu-id="4cb75-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="4cb75-130">Implementazione della sincronizzazione hash password con sincronizzazione di Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="4cb75-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="4cb75-131">**Vengono visualizzati un avviso di quota oggetto superato**</span><span class="sxs-lookup"><span data-stu-id="4cb75-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="4cb75-p104">È disponibile una quota di un oggetto incorporato per proteggere il servizio. Se si dispone di un numero eccessivo di oggetti nella directory che è necessario eseguire la sincronizzazione a Office 365, è necessario a [contatti di supporto per i prodotti di business](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per aumentare la quota.</span><span class="sxs-lookup"><span data-stu-id="4cb75-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="4cb75-134">**Devo sapere quali attributi vengono sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="4cb75-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="4cb75-135">È possibile trovare un elenco di tutti gli attributi sincronizzati tra organizzazioni locali e cloud [destra di seguito](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="4cb75-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="4cb75-136">**Non è possibile gestire o rimuovere gli oggetti che sono stati sincronizzati con il cloud**</span><span class="sxs-lookup"><span data-stu-id="4cb75-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="4cb75-p105">Sei pronto a gestire gli oggetti in solo nel cloud? O un valore object che è stato eliminato in locale, ma è bloccato nel cloud? Esaminare questo [Risoluzione degli errori durante la sincronizzazione](https://go.microsoft.com/fwlink/p/?linkid=842044) e [supportare articolo](https://go.microsoft.com/fwlink/p/?LinkId=396720) per istruzioni su come risolvere questi problemi.</span><span class="sxs-lookup"><span data-stu-id="4cb75-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="4cb75-140">**Ho ricevuto un messaggio di errore che mi informa che la mia azienda ha superato il numero di oggetti che possono essere sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="4cb75-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="4cb75-141">È possibile leggere ulteriori informazioni su questo problema [di seguito](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="4cb75-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="4cb75-142">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="4cb75-142">Other resources</span></span>

- [<span data-ttu-id="4cb75-143">Script per risolvere i nomi delle entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="4cb75-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="4cb75-144">Come preparare un dominio non instradabili (ad esempio domain Local) per la sincronizzazione delle directory</span><span class="sxs-lookup"><span data-stu-id="4cb75-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="4cb75-145">Script per il conteggio totali oggetti sincronizzati</span><span class="sxs-lookup"><span data-stu-id="4cb75-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="4cb75-146">Risoluzione dei problemi relativi AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="4cb75-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="4cb75-147">Utilizzare PowerShell per correggere gli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica</span><span class="sxs-lookup"><span data-stu-id="4cb75-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="4cb75-148">Utilizzare PowerShell per correggere UPN duplicati</span><span class="sxs-lookup"><span data-stu-id="4cb75-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="4cb75-149">Utilizzare PowerShell per correggere gli indirizzi di posta elettronica duplicati</span><span class="sxs-lookup"><span data-stu-id="4cb75-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="4cb75-150">Strumenti di diagnostica</span><span class="sxs-lookup"><span data-stu-id="4cb75-150">Diagnostic tools</span></span>

<span data-ttu-id="4cb75-p106">[Strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene utilizzato per eseguire l'individuazione e risoluzione dei problemi di oggetti identity e i relativi attributi in un ambiente Active Directory locale in preparazione per la migrazione a Office 365. IDFix è progettato per gli amministratori di Active Directory responsabili della DirSync con il servizio Office 365.</span><span class="sxs-lookup"><span data-stu-id="4cb75-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="4cb75-153">[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4cb75-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>