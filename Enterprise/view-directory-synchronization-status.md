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
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Informazioni su come disattivare la sincronizzazione delle directory. È inoltre possibile visualizzare lo stato.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541425"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="e13d2-104">Visualizzare lo stato di sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="e13d2-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="e13d2-105">Se è stata integrata di Active Directory locale con Azure Active Directory da sincronizzare l'ambiente locale con Office 365, è inoltre possibile controllare lo stato della sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="e13d2-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="e13d2-106">Visualizzare lo stato di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="e13d2-106">View directory synchronization status</span></span>
- <span data-ttu-id="e13d2-107">Accedere all'interfaccia di amministrazione di Office 365 e scegliere **Stato DirSync** nella home page.</span><span class="sxs-lookup"><span data-stu-id="e13d2-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="e13d2-p102">In alternativa, è possibile accedere ai **utenti** \> **utenti attivi**e nella pagina **utenti attivi** , fare clic su **ulteriori** \> **la sincronizzazione delle Directory**. Nel riquadro di **Sincronizzazione della Directory** , scegliere **andare a gestione DirSync**.</span><span class="sxs-lookup"><span data-stu-id="e13d2-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="e13d2-110">Nella pagina Gestisci directory synchronization informazioni</span><span class="sxs-lookup"><span data-stu-id="e13d2-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="e13d2-111">Nella tabella seguente sono elencate le caratteristiche è possibile ottenere informazioni nella pagina.</span><span class="sxs-lookup"><span data-stu-id="e13d2-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="e13d2-p103">Se si verifica un problema con la sincronizzazione della directory, in anche questa pagina sono riportati gli errori. Per ulteriori informazioni su errori che possono verificarsi, vedere [gli errori di sincronizzazione directory di identità in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="e13d2-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="e13d2-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e13d2-114">**Item**</span></span>|<span data-ttu-id="e13d2-115">**Novità per**</span><span class="sxs-lookup"><span data-stu-id="e13d2-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e13d2-116">**Verificata i domini**</span><span class="sxs-lookup"><span data-stu-id="e13d2-116">**Domains verified**</span></span> | <span data-ttu-id="e13d2-117">Numero di domini in Office 365 tenant che si sono verificati è proprietario.</span><span class="sxs-lookup"><span data-stu-id="e13d2-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="e13d2-118">**Domini non verificati**</span><span class="sxs-lookup"><span data-stu-id="e13d2-118">**Domains not verified**</span></span> | <span data-ttu-id="e13d2-119">Domini sono aggiunti ma non verificato.</span><span class="sxs-lookup"><span data-stu-id="e13d2-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="e13d2-120">**Sincronizzazione di directory attivata**</span><span class="sxs-lookup"><span data-stu-id="e13d2-120">**Directory sync enabled**</span></span> |<span data-ttu-id="e13d2-p104">True o False. Specifica se è stata abilitata la sincronizzazione di directory.</span><span class="sxs-lookup"><span data-stu-id="e13d2-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="e13d2-123">**Ultima sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="e13d2-123">**Latest directory sync**</span></span> | <span data-ttu-id="e13d2-p105">Ora ultima esecuzione della sincronizzazione della directory. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento di risoluzione dei problemi se l'ultima sincronizzazione risalgono a più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="e13d2-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e13d2-126">**Sincronizzazione delle password abilitata**</span><span class="sxs-lookup"><span data-stu-id="e13d2-126">**Password sync enabled**</span></span> | <span data-ttu-id="e13d2-p106">True o False. Specifica se si dispone di sincronizzazione delle password hash tra i locali e il tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e13d2-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="e13d2-129">**Ultima sincronizzazione delle Password**</span><span class="sxs-lookup"><span data-stu-id="e13d2-129">**Last Password Sync**</span></span> | <span data-ttu-id="e13d2-p107">Ora ultima esecuzione della sincronizzazione delle password hash. Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento di risoluzione dei problemi se l'ultima sincronizzazione risalgono a più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="e13d2-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e13d2-132">**Versione del client di sincronizzazione directory**</span><span class="sxs-lookup"><span data-stu-id="e13d2-132">**Directory sync client version**</span></span> | <span data-ttu-id="e13d2-133">Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure Active Directory Connetti.</span><span class="sxs-lookup"><span data-stu-id="e13d2-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="e13d2-134">**Strumento IDFix**</span><span class="sxs-lookup"><span data-stu-id="e13d2-134">**IDFix Tool**</span></span> | <span data-ttu-id="e13d2-135">Collegamento di download per [lo strumento IDFix](install-and-run-idfix.md), uno strumento è possibile utilizzare per controllare Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="e13d2-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="e13d2-136">**Account del servizio di sincronizzazione directory**</span><span class="sxs-lookup"><span data-stu-id="e13d2-136">**Directory sync service account**</span></span> | <span data-ttu-id="e13d2-137">Visualizza il nome dell'account del servizio di sincronizzazione delle directory di Office 365 è.</span><span class="sxs-lookup"><span data-stu-id="e13d2-137">Displays the name of you Office 365 directory sync service account.</span></span> |