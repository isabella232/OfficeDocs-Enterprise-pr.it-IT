---
title: Risoluzione dei problemi relativi alla sincronizzazione della directory per Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Descrive le cause comuni dei problemi di sincronizzazione della directory in Office 365 e fornisce alcuni metodi per individuarli e risolverli.
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998034"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="95f82-103">Risoluzione dei problemi relativi alla sincronizzazione della directory per Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="95f82-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="95f82-104">Con la sincronizzazione della directory, puoi continuare a gestire gli utenti e gruppi locali e sincronizzare aggiunte, eliminazioni e modifiche nel cloud.</span><span class="sxs-lookup"><span data-stu-id="95f82-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="95f82-105">Tuttavia, la configurazione è un po' complicata e a volte può essere difficile identificare l'origine dei problemi.</span><span class="sxs-lookup"><span data-stu-id="95f82-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="95f82-106">Sono disponibili risorse per consentire di individuare e risolvere potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="95f82-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="95f82-107">Come si fa a sapere se si è verificato un problema?</span><span class="sxs-lookup"><span data-stu-id="95f82-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="95f82-108">La prima indicazione che qualcosa è errato è quando il riquadro di stato DirSync nell'interfaccia di amministrazione di Microsoft 365 indica che si è verificato un problema.</span><span class="sxs-lookup"><span data-stu-id="95f82-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="95f82-109">Riceverà anche una mail (alla posta elettronica alternativa e alla posta elettronica di amministrazione) da Microsoft 365 che indica che il tenant ha riscontrato errori di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="95f82-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="95f82-110">Per ulteriori informazioni, vedere [identificare gli errori di sincronizzazione della directory in Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="95f82-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="95f82-111">Come si ottiene lo strumento Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="95f82-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="95f82-112">Nell'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com), passare **a utenti** \> **attivi**.</span><span class="sxs-lookup"><span data-stu-id="95f82-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="95f82-113">Fare clic sul menu **altro** (tre punti) e selezionare **sincronizzazione directory**.</span><span class="sxs-lookup"><span data-stu-id="95f82-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="95f82-114">Seguire le [istruzioni della procedura guidata](set-up-directory-synchronization.md) per scaricare Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="95f82-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="95f82-115">Se si sta ancora utilizzando Azure Active Directory (Azure AD) Sync (DirSync), vedere [come risolvere i problemi relativi all'installazione dello strumento di sincronizzazione di Azure Active Directory e ai messaggi di errore della configurazione guidata in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema per l'installazione di dirsync, le autorizzazioni necessarie e la risoluzione dei problemi relativi agli errori comuni.</span><span class="sxs-lookup"><span data-stu-id="95f82-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="95f82-116">Per eseguire l'aggiornamento da Azure AD Sync ad Azure AD Connect, vedere [le istruzioni relative all'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="95f82-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="95f82-117">Risoluzione delle cause comuni dei problemi relativi alla sincronizzazione della directory in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="95f82-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="95f82-118">**Gli oggetti sincronizzati non vengono visualizzati o aggiornati online oppure si riceve un errore di sincronizzazione dal servizio.**</span><span class="sxs-lookup"><span data-stu-id="95f82-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="95f82-119">Sincronizzazione delle identità e resilienza degli attributi duplicati</span><span class="sxs-lookup"><span data-stu-id="95f82-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="95f82-120">**Nell'interfaccia di amministrazione è presente un avviso oppure si ricevono messaggi di posta elettronica automatici che informano che non ci sono stati eventi di sincronizzazione recenti**</span><span class="sxs-lookup"><span data-stu-id="95f82-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="95f82-121">Risolvere i problemi di connettività con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="95f82-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="95f82-122">Azure AD Connect: account e autorizzazioni</span><span class="sxs-lookup"><span data-stu-id="95f82-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="95f82-123">Servizio di sincronizzazione Azure AD Connect: come gestire l'account del servizio Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="95f82-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="95f82-124">La sincronizzazione della directory in Azure Active Directory viene interrotta oppure viene visualizzato un avviso che indica che la sincronizzazione non è stata registrata per più di un giorno</span><span class="sxs-lookup"><span data-stu-id="95f82-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="95f82-125">**Gli hash delle password non vengono sincronizzati oppure nell'interfaccia di amministrazione è presente un avviso che informa che di recente non è stata eseguita la sincronizzazione degli hash delle password**</span><span class="sxs-lookup"><span data-stu-id="95f82-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="95f82-126">Implementazione della sincronizzazione dell'hash delle password con la sincronizzazione di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="95f82-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="95f82-127">**Viene visualizzato un avviso relativo al superamento della quota per gli oggetti**</span><span class="sxs-lookup"><span data-stu-id="95f82-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="95f82-128">Per proteggere il servizio, è prevista una quota predefinita per gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="95f82-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="95f82-129">Se nella directory sono presenti troppi oggetti che devono essere sincronizzati con Microsoft 365, è necessario contattare il [supporto per i prodotti aziendali](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) per aumentare la quota.</span><span class="sxs-lookup"><span data-stu-id="95f82-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="95f82-130">**Si desidera sapere quali attributi sono sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="95f82-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="95f82-131">L'elenco di tutti gli attributi sincronizzati tra l'ambiente locale e il cloud è disponibile [qui](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="95f82-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="95f82-132">**Non è possibile gestire o rimuovere oggetti sincronizzati con il cloud**</span><span class="sxs-lookup"><span data-stu-id="95f82-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="95f82-133">Sei pronto a gestire gli oggetti solo nel cloud?</span><span class="sxs-lookup"><span data-stu-id="95f82-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="95f82-134">Oppure c'è un oggetto che è stato eliminato in locale, ma è bloccato nel cloud?</span><span class="sxs-lookup"><span data-stu-id="95f82-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="95f82-135">Per indicazioni su come risolvere questi problemi, vedere [Risoluzione degli problemi durante la sincronizzazione](https://go.microsoft.com/fwlink/p/?linkid=842044) e l'[articolo del supporto](https://go.microsoft.com/fwlink/p/?LinkId=396720).</span><span class="sxs-lookup"><span data-stu-id="95f82-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="95f82-136">**Si è ricevuto un messaggio di errore che indica che è stato superato il numero di oggetti che è possibile sincronizzare**</span><span class="sxs-lookup"><span data-stu-id="95f82-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="95f82-137">Altre informazioni su questo problema sono disponibili [qui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="95f82-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="95f82-138">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="95f82-138">Other resources</span></span>

- [<span data-ttu-id="95f82-139">Script per correggere i nomi dell'entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="95f82-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="95f82-140">Come preparare un dominio non instradabile, ad esempio un dominio .local, per la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="95f82-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="95f82-141">Script per il conteggio degli oggetti sincronizzati</span><span class="sxs-lookup"><span data-stu-id="95f82-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="95f82-142">Risoluzione dei problemi di AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="95f82-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="95f82-143">Usare PowerShell per risolvere il problema degli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica</span><span class="sxs-lookup"><span data-stu-id="95f82-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="95f82-144">Usare PowerShell per correggere i nomi dell'entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="95f82-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="95f82-145">Usare PowerShell per correggere gli indirizzi di posta elettronica duplicati</span><span class="sxs-lookup"><span data-stu-id="95f82-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="95f82-146">Strumenti di diagnostica</span><span class="sxs-lookup"><span data-stu-id="95f82-146">Diagnostic tools</span></span>

<span data-ttu-id="95f82-147">[Lo strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene utilizzato per eseguire l'individuazione e la correzione degli oggetti Identity e dei relativi attributi in un ambiente Active Directory locale in preparazione per la migrazione a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95f82-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="95f82-148">IDFix è destinato agli amministratori di Active Directory responsabili della sincronizzazione della directory con il servizio Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="95f82-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="95f82-149">[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'Area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="95f82-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>