---
title: Visualizzare lo stato della sincronizzazione della directory in Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.openlocfilehash: a38b723db6f5bafe246e774972ca89c65bc9c846
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492102"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="b2caa-104">Visualizzare lo stato della sincronizzazione della directory in Office 365</span><span class="sxs-lookup"><span data-stu-id="b2caa-104">View directory synchronization status in Office 365</span></span>

<span data-ttu-id="b2caa-105">Se è stata integrata Active Directory locale con Azure AD sincronizzando l'ambiente locale con Office 365, è anche possibile controllare lo stato della sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="b2caa-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="b2caa-106">Visualizzazione dello stato di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="b2caa-106">View directory synchronization status</span></span>

- <span data-ttu-id="b2caa-107">Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) e scegliere **stato dirsync** nella Home page.</span><span class="sxs-lookup"><span data-stu-id="b2caa-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="b2caa-108">In alternativa, è possibile \*\*\*\* \> accedere agli utenti **attivi**degli utenti, quindi nella pagina **utenti attivi** scegliere **altre** \> **sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="b2caa-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="b2caa-109">Nel riquadro di **sincronizzazione della directory** scegliere **Vai a gestione dirsync**.</span><span class="sxs-lookup"><span data-stu-id="b2caa-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="b2caa-110">Informazioni sulla pagina Gestisci sincronizzazione directory</span><span class="sxs-lookup"><span data-stu-id="b2caa-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="b2caa-111">Nella tabella seguente sono elencate le funzionalità che consentono di ottenere informazioni sulla pagina.</span><span class="sxs-lookup"><span data-stu-id="b2caa-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="b2caa-112">Se si verifica un problema con la sincronizzazione della directory, anche gli errori sono elencati in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="b2caa-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="b2caa-113">Per ulteriori informazioni sui diversi errori che potrebbero verificarsi, vedere [identificare gli errori di sincronizzazione della directory in Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="b2caa-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="b2caa-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b2caa-114">**Item**</span></span>|<span data-ttu-id="b2caa-115">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="b2caa-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b2caa-116">**Domini verificati**</span><span class="sxs-lookup"><span data-stu-id="b2caa-116">**Domains verified**</span></span> | <span data-ttu-id="b2caa-117">Numero di domini del tenant di Office 365 che sono stati verificati.</span><span class="sxs-lookup"><span data-stu-id="b2caa-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="b2caa-118">**Domini non verificati**</span><span class="sxs-lookup"><span data-stu-id="b2caa-118">**Domains not verified**</span></span> | <span data-ttu-id="b2caa-119">Domini che sono stati aggiunti, ma non sono stati verificati.</span><span class="sxs-lookup"><span data-stu-id="b2caa-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="b2caa-120">**Sincronizzazione della directory attivata**</span><span class="sxs-lookup"><span data-stu-id="b2caa-120">**Directory sync enabled**</span></span> |<span data-ttu-id="b2caa-121">True o false.</span><span class="sxs-lookup"><span data-stu-id="b2caa-121">True or False.</span></span> <span data-ttu-id="b2caa-122">Specifica se è stata abilitata la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="b2caa-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="b2caa-123">**Sincronizzazione della directory più recente**</span><span class="sxs-lookup"><span data-stu-id="b2caa-123">**Latest directory sync**</span></span> | <span data-ttu-id="b2caa-124">Ultima esecuzione della sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="b2caa-124">Last time directory sync ran.</span></span> <span data-ttu-id="b2caa-125">Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="b2caa-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="b2caa-126">**Sincronizzazione password attivata**</span><span class="sxs-lookup"><span data-stu-id="b2caa-126">**Password sync enabled**</span></span> | <span data-ttu-id="b2caa-127">True o false.</span><span class="sxs-lookup"><span data-stu-id="b2caa-127">True or False.</span></span> <span data-ttu-id="b2caa-128">Specifica se si dispone della sincronizzazione hash della password tra il tenant locale e quello Office 365.</span><span class="sxs-lookup"><span data-stu-id="b2caa-128">Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="b2caa-129">**Sincronizzazione ultima password**</span><span class="sxs-lookup"><span data-stu-id="b2caa-129">**Last Password Sync**</span></span> | <span data-ttu-id="b2caa-130">L'ultima volta che è stata eseguita la sincronizzazione hash password.</span><span class="sxs-lookup"><span data-stu-id="b2caa-130">Last time password hash sync ran.</span></span> <span data-ttu-id="b2caa-131">Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="b2caa-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="b2caa-132">**Versione client di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="b2caa-132">**Directory sync client version**</span></span> | <span data-ttu-id="b2caa-133">Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="b2caa-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="b2caa-134">**Strumento IDFix**</span><span class="sxs-lookup"><span data-stu-id="b2caa-134">**IDFix Tool**</span></span> | <span data-ttu-id="b2caa-135">Scaricare il collegamento a [IDFix](install-and-run-idfix.md), uno strumento che è possibile utilizzare per verificare l'utilizzo di Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="b2caa-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="b2caa-136">**Account del servizio di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="b2caa-136">**Directory sync service account**</span></span> | <span data-ttu-id="b2caa-137">Visualizza il nome dell'account del servizio di sincronizzazione della directory di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b2caa-137">Displays the name of you Office 365 directory sync service account.</span></span> |