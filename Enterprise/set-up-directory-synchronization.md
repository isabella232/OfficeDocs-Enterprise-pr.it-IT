---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Informazioni su come configurare la sincronizzazione della directory tra Office 365 e Active Directory locale.
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085265"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="81f3e-103">Configurare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="81f3e-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="81f3e-p101">Office 365 utilizza il servizio di gestione delle identità utente basato sul cloud per gestire gli utenti. È inoltre possibile integrare Active Directory locale con Azure AD sincronizzando l'ambiente locale con Office 365. Dopo aver configurato la sincronizzazione, è possibile decidere di fare in modo che l'autenticazione dell'utente avvenga all'interno di Azure AD o all'interno della directory locale.</span><span class="sxs-lookup"><span data-stu-id="81f3e-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="81f3e-107">Sincronizzazione della directory di Office 365</span><span class="sxs-lookup"><span data-stu-id="81f3e-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="81f3e-p102">È possibile utilizzare l'identità sincronizzata o l'identità federata tra l'organizzazione locale e Office 365. Con l'identità sincronizzata, è possibile gestire gli utenti in locale e vengono autenticati da Azure AD quando utilizzano la stessa password nel cloud come in locale. Questo è lo scenario di sincronizzazione della directory più comune. Autenticazione pass-through o identità federata, consente di gestire gli utenti in locale e vengono autenticati dalla directory locale. L'identità federata richiede una configurazione aggiuntiva e consente agli utenti di accedere solo una volta. Per informazioni dettagliate, vedere [understandIng Office 365 Identity e Azure Active Directory](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="81f3e-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="81f3e-114">Si desidera eseguire l'aggiornamento da Windows Azure Active Directory Sync (DirSync) ad Azure Active Directory Connect?</span><span class="sxs-lookup"><span data-stu-id="81f3e-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="81f3e-115">Se si sta attualmente utilizzando DirSync e si desidera eseguire l'aggiornamento, passare a [Azure.com](https://azure.com) per [istruzioni sull'aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="81f3e-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="81f3e-116">Prerequisiti per Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="81f3e-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="81f3e-p103">È possibile ottenere una sottoscrizione gratuita ad Azure AD con l'abbonamento a Office 365. Quando si configura la sincronizzazione della directory, si installerà Azure Active Directory Connect su uno dei server locali.</span><span class="sxs-lookup"><span data-stu-id="81f3e-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="81f3e-119">Per Office 365 sarà necessario:</span><span class="sxs-lookup"><span data-stu-id="81f3e-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="81f3e-120">Verificare il dominio locale (la procedura vi guiderà in questo modo).</span><span class="sxs-lookup"><span data-stu-id="81f3e-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="81f3e-121">[Assegnare ruoli di amministratore in office 365 per](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) le autorizzazioni aziendali per il tenant di Office 365 e Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="81f3e-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="81f3e-122">Per il server locale in cui si installa Azure AD Connect, è necessario il software seguente:</span><span class="sxs-lookup"><span data-stu-id="81f3e-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="81f3e-123">**SISTEMA operativo del server**</span><span class="sxs-lookup"><span data-stu-id="81f3e-123">**Server OS**</span></span>|<span data-ttu-id="81f3e-124">**Altro software**</span><span class="sxs-lookup"><span data-stu-id="81f3e-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="81f3e-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="81f3e-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="81f3e-126">-PowerShell è installato per impostazione predefinita, non è necessaria alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="81f3e-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="81f3e-p104">-NET 4.5.1 e versioni successive sono disponibili tramite Windows Update. Assicurarsi di aver installato gli aggiornamenti più recenti su Windows Server nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="81f3e-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="81f3e-129">**Windows server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="81f3e-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="81f3e-p105">-La versione più recente di PowerShell è disponibile in Windows Management Framework 4,0. Cercarlo nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="81f3e-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="81f3e-132">-.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="81f3e-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="81f3e-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="81f3e-133">**Windows Server 2008**</span></span> | <span data-ttu-id="81f3e-134">-La versione più recente supportata di PowerShell è disponibile in Windows Management Framework 3,0, disponibile nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="81f3e-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="81f3e-135">-.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="81f3e-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="81f3e-p106">Se si utilizza Azure Active Directory DirSync, il numero massimo di membri del gruppo di distribuzione che è possibile sincronizzare da Active Directory locale ad Azure Active Directory è 15.000. Per Azure AD Connect, il numero è 50.000.</span><span class="sxs-lookup"><span data-stu-id="81f3e-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="81f3e-138">Per esaminare più accuratamente i requisiti hardware, software, account e autorizzazioni, i requisiti per i certificati SSL e i limiti degli oggetti per Azure AD Connect, leggere [i prerequisiti per Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span><span class="sxs-lookup"><span data-stu-id="81f3e-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="81f3e-139">È inoltre possibile esaminare la [cronologia delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure ad Connect versione per vedere cosa è incluso e risolto in ogni versione.</span><span class="sxs-lookup"><span data-stu-id="81f3e-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="81f3e-140">Per configurare la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="81f3e-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="81f3e-141">accedere all'interfaccia di amministrazione di Office 365 e scegliere \*\*\*\* \> utenti **attivi** per gli utenti sulla barra di spostamento a sinistra.</span><span class="sxs-lookup"><span data-stu-id="81f3e-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="81f3e-142">nell'interfaccia di amministrazione di Office 365, nella pagina **utenti attivi** , scegliere **altre** \> **sincronizzazione della Directory**.</span><span class="sxs-lookup"><span data-stu-id="81f3e-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="81f3e-p107">Nella pagina **preparazione di Active Directory** selezionare il collegamento **Scarica Microsoft Azure Active Directory Connect Tool** per iniziare. Per ulteriori informazioni sul processo di installazione di Azure Active Directory Connect, vedere [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="81f3e-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="81f3e-146">Assegnare licenze agli utenti sincronizzati</span><span class="sxs-lookup"><span data-stu-id="81f3e-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="81f3e-p108">Dopo aver sincronizzato gli utenti in Office 365, vengono creati ma è necessario assegnare loro le licenze in modo che possano utilizzare le funzionalità di Office 365, ad esempio la posta elettronica. Per istruzioni, vedere [assegnare licenze agli utenti in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span><span class="sxs-lookup"><span data-stu-id="81f3e-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="81f3e-149">Terminare la configurazione dei domini</span><span class="sxs-lookup"><span data-stu-id="81f3e-149">Finish setting up domains</span></span>

<span data-ttu-id="81f3e-150">Seguire la procedura descritta in [create DNS Records for Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare la configurazione dei domini.</span><span class="sxs-lookup"><span data-stu-id="81f3e-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>