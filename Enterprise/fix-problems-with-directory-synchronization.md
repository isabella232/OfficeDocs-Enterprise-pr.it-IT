---
title: Risoluzione dei problemi di sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: Descrive le cause comuni dei problemi di sincronizzazione della directory in Office 365 e fornisce alcuni metodi per individuarli e risolverli.
ms.openlocfilehash: 3a1cf63122be84dc3e1c60e84a9a3a488f81bc0f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067672"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="3a4a7-103">Risoluzione dei problemi di sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="3a4a7-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="3a4a7-104">Con la sincronizzazione della directory, puoi continuare a gestire gli utenti e gruppi locali e sincronizzare aggiunte, eliminazioni e modifiche nel cloud.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="3a4a7-105">Tuttavia, la configurazione è un po' complicata e a volte può essere difficile identificare l'origine dei problemi.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="3a4a7-106">Sono disponibili risorse per consentire di individuare e risolvere potenziali problemi.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-106">We have resources to help you hunt down potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="3a4a7-107">Come si fa a sapere se si è verificato un problema?</span><span class="sxs-lookup"><span data-stu-id="3a4a7-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="3a4a7-108">La prima segnalazione di un problema viene visualizzata nel riquadro Stato DirSync dell'interfaccia di amministrazione di Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="3a4a7-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem:</span></span>
  
![Riquadro Stato DirSync nell'anteprima dell'interfaccia di amministrazione](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="3a4a7-110">Office 365 invia anche un messaggio di posta elettronica, all'indirizzo di posta elettronica alternativo e a quello di amministrazione, per segnalare che nel tenant si sono verificati errori di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-110">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="3a4a7-111">Per informazioni dettagliate, vedere [Identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-111">[Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md)</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="3a4a7-112">Come si ottiene lo strumento Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="3a4a7-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="3a4a7-113">Nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com), passare a \*\* Utenti \*\* \> **Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-113">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to \*\* Users \*\* \> **Active users**.</span></span> <span data-ttu-id="3a4a7-114">Fare clic sul menu **Altro** e scegliere **Sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-114">Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![Nel menu Altro scegliere Sincronizzazione della directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="3a4a7-116">Seguire le [istruzioni della procedura guidata](set-up-directory-synchronization.md) per scaricare Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-116">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="3a4a7-117">Se si usa ancora Azure Active Directory Sync (DirSync), vedere [Come risolvere i problemi di installazione dello strumento di sincronizzazione di Azure Active Directory e i messaggi di errore della Configurazione guidata in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) per informazioni sui requisiti di sistema per l'installazione di DirSync, sulle autorizzazioni necessarie e sulla risoluzione dei problemi comuni.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-117">Take a look at  How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365 http://go.microsoft.com/fwlink/p/?LinkId=396717  for information about the system requirements to install WindowsAzureActiveDirectorySyncTool, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="3a4a7-118">Per eseguire l'aggiornamento da Azure Active Directory Sync ad Azure AD Connect, vedere le [istruzioni di aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-118">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="3a4a7-119">Risoluzione delle cause comuni dei problemi relativi alla sincronizzazione delle directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="3a4a7-119">Common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="3a4a7-120">**Gli oggetti sincronizzati non vengono visualizzati o aggiornati online oppure si riceve un errore di sincronizzazione dal servizio.**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-120">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="3a4a7-121">Sincronizzazione delle identità e resilienza degli attributi duplicati</span><span class="sxs-lookup"><span data-stu-id="3a4a7-121">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="3a4a7-122">**Nell'interfaccia di amministrazione è presente un avviso oppure si ricevono messaggi di posta elettronica automatici che informano che non ci sono stati eventi di sincronizzazione recenti**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-122">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="3a4a7-123">Risolvere i problemi di connettività con Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3a4a7-123">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="3a4a7-124">Azure AD Connect: account e autorizzazioni</span><span class="sxs-lookup"><span data-stu-id="3a4a7-124">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="3a4a7-125">Servizio di sincronizzazione Azure AD Connect: come gestire l'account del servizio Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="3a4a7-125">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="3a4a7-126">La sincronizzazione della directory in Azure Active Directory viene interrotta oppure viene visualizzato un avviso che indica che la sincronizzazione non è stata registrata per più di un giorno</span><span class="sxs-lookup"><span data-stu-id="3a4a7-126">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="3a4a7-127">**Gli hash delle password non vengono sincronizzati oppure nell'interfaccia di amministrazione è presente un avviso che informa che di recente non è stata eseguita la sincronizzazione degli hash delle password**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-127">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- <span data-ttu-id="3a4a7-128">[Implementazione della sincronizzazione dell'hash delle password con la sincronizzazione di Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)</span><span class="sxs-lookup"><span data-stu-id="3a4a7-128">For more information, see [Implement password hash synchronization with Azure AD Connect sync](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).</span></span>

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="3a4a7-129">**Viene visualizzato un avviso relativo al superamento della quota per gli oggetti**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-129">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="3a4a7-130">Per proteggere il servizio, è prevista una quota predefinita per gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-130">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="3a4a7-131">Se la directory contiene troppi oggetti da sincronizzare con Office 365, per aumentare la quota, è necessario [contattare il supporto per i prodotti per le aziende](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-131">If you have too many objects in your directory that need to sync to Office 365, you’ll have to contact Support to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="3a4a7-132">**Si desidera sapere quali attributi sono sincronizzati**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-132">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="3a4a7-133">L'elenco di tutti gli attributi sincronizzati tra l'ambiente locale e il cloud è disponibile [qui](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-133">You can find a list of all the attributes that are synced between on-premises and the cloud [right herehttp://go.microsoft.com/fwlink/p/?LinkId=396719](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="3a4a7-134">**Non è possibile gestire o rimuovere oggetti sincronizzati con il cloud**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-134">**I can’t manage or remove objects that were synced to the cloud**</span></span>
- <span data-ttu-id="3a4a7-135">Sei pronto a gestire gli oggetti solo nel cloud?</span><span class="sxs-lookup"><span data-stu-id="3a4a7-135">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="3a4a7-136">Oppure c'è un oggetto che è stato eliminato in locale, ma è bloccato nel cloud?</span><span class="sxs-lookup"><span data-stu-id="3a4a7-136">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="3a4a7-137">Per indicazioni su come risolvere questi problemi, vedere [Risoluzione degli problemi durante la sincronizzazione](https://go.microsoft.com/fwlink/p/?linkid=842044) e l'[articolo del supporto](https://go.microsoft.com/fwlink/p/?LinkId=396720).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-137">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="3a4a7-138">**Si è ricevuto un messaggio di errore che indica che è stato superato il numero di oggetti che è possibile sincronizzare**</span><span class="sxs-lookup"><span data-stu-id="3a4a7-138">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="3a4a7-139">Altre informazioni su questo problema sono disponibili [qui](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span><span class="sxs-lookup"><span data-stu-id="3a4a7-139">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="3a4a7-140">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="3a4a7-140">Other resources</span></span>

- [<span data-ttu-id="3a4a7-141">Script per correggere i nomi dell'entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="3a4a7-141">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="3a4a7-142">Come preparare un dominio non instradabile, ad esempio un dominio .local, per la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="3a4a7-142">How to prepare a non-routable domain for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="3a4a7-143">Script per il conteggio degli oggetti sincronizzati</span><span class="sxs-lookup"><span data-stu-id="3a4a7-143">Script to count total synchronized objectshttp://go.microsoft.com/fwlink/p/?LinkId=396726</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="3a4a7-144">Risoluzione dei problemi di AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="3a4a7-144">AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="3a4a7-145">Usare PowerShell per risolvere il problema degli attributi DisplayName vuoti per i gruppi abilitati alla posta elettronica</span><span class="sxs-lookup"><span data-stu-id="3a4a7-145">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="3a4a7-146">Usare PowerShell per correggere i nomi dell'entità utente duplicati</span><span class="sxs-lookup"><span data-stu-id="3a4a7-146">How to use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="3a4a7-147">Usare PowerShell per correggere gli indirizzi di posta elettronica duplicati</span><span class="sxs-lookup"><span data-stu-id="3a4a7-147">Use PowerShell to fix duplicate email addresseshttp://go.microsoft.com/fwlink/p/?LinkId=396731</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="3a4a7-148">Strumenti di diagnostica</span><span class="sxs-lookup"><span data-stu-id="3a4a7-148">Diagnostic tools</span></span>

<span data-ttu-id="3a4a7-149">Lo [strumento IDFix](prepare-directory-attributes-for-synch-with-idfix.md) viene usato per l'individuazione e la correzione di oggetti identità e dei relativi attributi in un ambiente Active Directory locale per la preparazione della migrazione a Office 365.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-149">IdFix is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="3a4a7-150">IDFix è destinato agli amministratori di Active Directory responsabili dell'esecuzione di DirSync con il servizio di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-150">IdFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="3a4a7-151">[Scaricare lo strumento IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) dall'Area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a4a7-151">[Download the IDFix toolhttp://go.microsoft.com/fwlink/p/?LinkId=396718](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>