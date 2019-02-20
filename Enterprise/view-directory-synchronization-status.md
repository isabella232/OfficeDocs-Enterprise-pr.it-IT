---
title: Visualizzare lo stato di sincronizzazione della directory in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Informazioni su come disattivare la sincronizzazione della directory. È anche possibile visualizzarne lo stato.
ms.openlocfilehash: 4803cbadd17dbc1ee23d019f39144ff1ffaefd9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085055"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="cc24d-104">Visualizzare lo stato di sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="cc24d-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="cc24d-105">Se è stata integrata Active Directory locale con Azure AD sincronizzando l'ambiente locale con Office 365, è anche possibile controllare lo stato della sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="cc24d-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="cc24d-106">Visualizzazione dello stato di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="cc24d-106">View directory synchronization status</span></span>
- <span data-ttu-id="cc24d-107">Accedere all'interfaccia di amministrazione di Office 365 e scegliere **stato dirsync** nella Home page.</span><span class="sxs-lookup"><span data-stu-id="cc24d-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="cc24d-p102">In alternativa, è possibile \*\*\*\* \> accedere agli utenti **attivi**degli utenti, quindi nella pagina **utenti attivi** scegliere **altre** \> **sincronizzazione della directory**. Nel riquadro di **sincronizzazione della directory** scegliere **Vai a gestione dirsync**.</span><span class="sxs-lookup"><span data-stu-id="cc24d-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="cc24d-110">Informazioni sulla pagina Gestisci sincronizzazione directory</span><span class="sxs-lookup"><span data-stu-id="cc24d-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="cc24d-111">Nella tabella seguente sono elencate le funzionalità che consentono di ottenere informazioni sulla pagina.</span><span class="sxs-lookup"><span data-stu-id="cc24d-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="cc24d-p103">Se si verifica un problema con la sincronizzazione della directory, anche gli errori sono elencati in questa pagina. Per ulteriori informazioni sui diversi errori che potrebbero verificarsi, vedere [identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="cc24d-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="cc24d-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cc24d-114">**Item**</span></span>|<span data-ttu-id="cc24d-115">**Funzione**</span><span class="sxs-lookup"><span data-stu-id="cc24d-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="cc24d-116">**Domini verificati**</span><span class="sxs-lookup"><span data-stu-id="cc24d-116">**Domains verified**</span></span> | <span data-ttu-id="cc24d-117">Numero di domini del tenant di Office 365 che sono stati verificati.</span><span class="sxs-lookup"><span data-stu-id="cc24d-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="cc24d-118">**Domini non verificati**</span><span class="sxs-lookup"><span data-stu-id="cc24d-118">**Domains not verified**</span></span> | <span data-ttu-id="cc24d-119">Domini che sono stati aggiunti, ma non sono stati verificati.</span><span class="sxs-lookup"><span data-stu-id="cc24d-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="cc24d-120">**Sincronizzazione della directory attivata**</span><span class="sxs-lookup"><span data-stu-id="cc24d-120">**Directory sync enabled**</span></span> |<span data-ttu-id="cc24d-p104">True o false. Specifica se è stata abilitata la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="cc24d-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="cc24d-123">**Sincronizzazione della directory più recente**</span><span class="sxs-lookup"><span data-stu-id="cc24d-123">**Latest directory sync**</span></span> | <span data-ttu-id="cc24d-p105">Ultima esecuzione della sincronizzazione della directory. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="cc24d-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="cc24d-126">**Sincronizzazione password attivata**</span><span class="sxs-lookup"><span data-stu-id="cc24d-126">**Password sync enabled**</span></span> | <span data-ttu-id="cc24d-p106">True o false. Specifica se si dispone della sincronizzazione hash della password tra il tenant locale e quello Office 365.</span><span class="sxs-lookup"><span data-stu-id="cc24d-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="cc24d-129">**Sincronizzazione ultima password**</span><span class="sxs-lookup"><span data-stu-id="cc24d-129">**Last Password Sync**</span></span> | <span data-ttu-id="cc24d-p107">L'ultima volta che è stata eseguita la sincronizzazione hash password. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="cc24d-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="cc24d-132">**Versione client di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="cc24d-132">**Directory sync client version**</span></span> | <span data-ttu-id="cc24d-133">Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="cc24d-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="cc24d-134">**Strumento IDFix**</span><span class="sxs-lookup"><span data-stu-id="cc24d-134">**IDFix Tool**</span></span> | <span data-ttu-id="cc24d-135">Scaricare il collegamento a [IDFix](install-and-run-idfix.md), uno strumento che è possibile utilizzare per verificare l'utilizzo di Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="cc24d-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="cc24d-136">**Account del servizio di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="cc24d-136">**Directory sync service account**</span></span> | <span data-ttu-id="cc24d-137">Visualizza il nome dell'account del servizio di sincronizzazione della directory di Office 365.</span><span class="sxs-lookup"><span data-stu-id="cc24d-137">Displays the name of you Office 365 directory sync service account.</span></span> |