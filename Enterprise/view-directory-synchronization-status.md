---
title: Visualizzare lo stato di sincronizzazione della directory in Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
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
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Informazioni su come disattivare la sincronizzazione della directory. È anche possibile visualizzarne lo stato.
ms.openlocfilehash: d6f3a9f1f4e069716501f58e188daedacbf7e597
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906199"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="c0b65-104">Visualizzare lo stato di sincronizzazione della directory in Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c0b65-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="c0b65-105">Se è stata integrata Active Directory locale con Azure AD sincronizzando l'ambiente locale con Microsoft 365, è anche possibile controllare lo stato della sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="c0b65-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="c0b65-106">Visualizzare lo stato della sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="c0b65-106">View directory synchronization status</span></span>

- <span data-ttu-id="c0b65-107">Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) e scegliere **stato dirsync** nella Home page.</span><span class="sxs-lookup"><span data-stu-id="c0b65-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="c0b65-108">In alternativa, è possibile accedere agli utenti attivi **degli utenti** \> **Active users**, quindi nella pagina **utenti attivi** scegliere **altre** \> **sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="c0b65-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="c0b65-109">Nel riquadro di **sincronizzazione della directory** scegliere **Vai a gestione dirsync**.</span><span class="sxs-lookup"><span data-stu-id="c0b65-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="c0b65-110">Informazioni sulla pagina Gestisci sincronizzazione directory</span><span class="sxs-lookup"><span data-stu-id="c0b65-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="c0b65-111">Nella tabella seguente sono elencate le funzionalità che consentono di ottenere informazioni sulla pagina.</span><span class="sxs-lookup"><span data-stu-id="c0b65-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="c0b65-112">Se si verifica un problema con la sincronizzazione della directory, anche gli errori sono elencati in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="c0b65-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="c0b65-113">Per ulteriori informazioni sui diversi errori che potrebbero verificarsi, vedere [identificare gli errori di sincronizzazione della directory in Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="c0b65-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="c0b65-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c0b65-114">**Item**</span></span>|<span data-ttu-id="c0b65-115">**Scopo**</span><span class="sxs-lookup"><span data-stu-id="c0b65-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c0b65-116">**Domini verificati**</span><span class="sxs-lookup"><span data-stu-id="c0b65-116">**Domains verified**</span></span> | <span data-ttu-id="c0b65-117">Il numero di domini nel tenant Microsoft 365 verificato che si è proprietari.</span><span class="sxs-lookup"><span data-stu-id="c0b65-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="c0b65-118">**Domini non verificati**</span><span class="sxs-lookup"><span data-stu-id="c0b65-118">**Domains not verified**</span></span> | <span data-ttu-id="c0b65-119">Domini che sono stati aggiunti, ma non sono stati verificati.</span><span class="sxs-lookup"><span data-stu-id="c0b65-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="c0b65-120">**Sincronizzazione della directory attivata**</span><span class="sxs-lookup"><span data-stu-id="c0b65-120">**Directory sync enabled**</span></span> |<span data-ttu-id="c0b65-121">True o false.</span><span class="sxs-lookup"><span data-stu-id="c0b65-121">True or False.</span></span> <span data-ttu-id="c0b65-122">Specifica se è stata abilitata la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="c0b65-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="c0b65-123">**Sincronizzazione della directory più recente**</span><span class="sxs-lookup"><span data-stu-id="c0b65-123">**Latest directory sync**</span></span> | <span data-ttu-id="c0b65-124">Ultima esecuzione della sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="c0b65-124">Last time directory sync ran.</span></span> <span data-ttu-id="c0b65-125">Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="c0b65-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c0b65-126">**Sincronizzazione password attivata**</span><span class="sxs-lookup"><span data-stu-id="c0b65-126">**Password sync enabled**</span></span> | <span data-ttu-id="c0b65-127">True o false.</span><span class="sxs-lookup"><span data-stu-id="c0b65-127">True or False.</span></span> <span data-ttu-id="c0b65-128">Specifica se si dispone della sincronizzazione hash delle password tra il tenant locale e quello Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c0b65-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="c0b65-129">**Sincronizzazione ultima password**</span><span class="sxs-lookup"><span data-stu-id="c0b65-129">**Last Password Sync**</span></span> | <span data-ttu-id="c0b65-130">L'ultima volta che è stata eseguita la sincronizzazione hash password.</span><span class="sxs-lookup"><span data-stu-id="c0b65-130">Last time password hash sync ran.</span></span> <span data-ttu-id="c0b65-131">Verrà visualizzato un messaggio di avviso e un collegamento a uno strumento per la risoluzione dei problemi se l'ultima sincronizzazione è stata più di tre giorni fa.</span><span class="sxs-lookup"><span data-stu-id="c0b65-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c0b65-132">**Versione client di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="c0b65-132">**Directory sync client version**</span></span> | <span data-ttu-id="c0b65-133">Contiene un collegamento di download se è stata rilasciata una nuova versione di Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c0b65-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="c0b65-134">**Strumento IDFix**</span><span class="sxs-lookup"><span data-stu-id="c0b65-134">**IDFix Tool**</span></span> | <span data-ttu-id="c0b65-135">Scaricare il collegamento a [IDFix](install-and-run-idfix.md), uno strumento che è possibile utilizzare per verificare l'utilizzo di Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="c0b65-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="c0b65-136">**Account del servizio di sincronizzazione della directory**</span><span class="sxs-lookup"><span data-stu-id="c0b65-136">**Directory sync service account**</span></span> | <span data-ttu-id="c0b65-137">Visualizza il nome dell'account del servizio di sincronizzazione della directory Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c0b65-137">Displays the name of your Microsoft 365 directory sync service account.</span></span> |