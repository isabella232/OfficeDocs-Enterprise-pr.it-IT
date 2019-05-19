---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 1798c54854bc5ecc82481aaabca3690e7212e135
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162479"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="f42b0-103">Configurare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="f42b0-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="f42b0-104">Office 365 utilizza un tenant di Azure Active Directory (Azure AD) per l'archiviazione e la gestione delle identità per l'autenticazione e le autorizzazioni per l'accesso alle risorse basate su cloud.</span><span class="sxs-lookup"><span data-stu-id="f42b0-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="f42b0-105">Se si dispone di servizi di dominio Active Directory (AD DS) locali, è possibile sincronizzare gli account utente, i gruppi e i contatti di AD DS con il tenant di Azure AD della sottoscrizione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f42b0-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="f42b0-106">Si tratta dell'identità ibrida per Office 365.</span><span class="sxs-lookup"><span data-stu-id="f42b0-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="f42b0-107">Di seguito vengono ripartiti i componenti.</span><span class="sxs-lookup"><span data-stu-id="f42b0-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="f42b0-108">Azure AD Connect viene eseguito su un server locale e sincronizza i servizi di dominio Active Directory con il tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="f42b0-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="f42b0-109">Insieme alla sincronizzazione della directory, è anche possibile specificare queste opzioni di autenticazione:</span><span class="sxs-lookup"><span data-stu-id="f42b0-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="f42b0-110">Sincronizzazione degli hash delle password (pH)</span><span class="sxs-lookup"><span data-stu-id="f42b0-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="f42b0-111">Azure AD esegue l'autenticazione stessa.</span><span class="sxs-lookup"><span data-stu-id="f42b0-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="f42b0-112">Autenticazione pass-through</span><span class="sxs-lookup"><span data-stu-id="f42b0-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="f42b0-113">Azure AD ha servizi di dominio Active Directory per eseguire l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="f42b0-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="f42b0-114">Autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="f42b0-114">Federated authentication</span></span>

  <span data-ttu-id="f42b0-115">Azure AD reindirizza il computer client che richiede l'autenticazione per contattare un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="f42b0-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="f42b0-116">Per ulteriori informazioni, vedere [identità ibride](plan-for-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="f42b0-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="f42b0-117">1. rivedere i prerequisiti per Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="f42b0-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="f42b0-118">È possibile ottenere una sottoscrizione gratuita AD Azure AD con l'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="f42b0-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="f42b0-119">Quando si configura la sincronizzazione della directory, si installerà Azure AD Connect su uno dei server locali.</span><span class="sxs-lookup"><span data-stu-id="f42b0-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="f42b0-120">Per Office 365 è necessario:</span><span class="sxs-lookup"><span data-stu-id="f42b0-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="f42b0-121">Verificare il dominio locale.</span><span class="sxs-lookup"><span data-stu-id="f42b0-121">Verify your on-premises domain.</span></span> <span data-ttu-id="f42b0-122">Nella procedura guidata di Azure AD Connect è possibile eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="f42b0-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="f42b0-123">Ottenere i nomi utente e le password per gli account di amministrazione del tenant di Office 365 e servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f42b0-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="f42b0-124">Per il server locale in cui si installa Azure AD Connect, è necessario quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f42b0-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="f42b0-125">**Sistema operativo del server**</span><span class="sxs-lookup"><span data-stu-id="f42b0-125">**Server OS**</span></span>|<span data-ttu-id="f42b0-126">**Altro software**</span><span class="sxs-lookup"><span data-stu-id="f42b0-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f42b0-127">Windows Server 2012 R2 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="f42b0-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="f42b0-128">-PowerShell è installato per impostazione predefinita, non è necessaria alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="f42b0-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="f42b0-129">-NET 4.5.1 e versioni successive sono disponibili tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f42b0-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="f42b0-130">Assicurarsi di aver installato gli aggiornamenti più recenti su Windows Server nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="f42b0-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="f42b0-131">Windows Server 2008 R2 con Service Pack 1 (SP1) \* \* o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f42b0-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="f42b0-132">-La versione più recente di PowerShell è disponibile in Windows Management Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="f42b0-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="f42b0-133">Cercarlo nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="f42b0-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="f42b0-134">-.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="f42b0-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="f42b0-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="f42b0-135">Windows Server 2008</span></span> | <span data-ttu-id="f42b0-136">-La versione più recente supportata di PowerShell è disponibile in Windows Management Framework 3,0, disponibile nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="f42b0-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="f42b0-137">-.NET 4.5.1 e versioni successive sono disponibili nell' [area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="f42b0-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="f42b0-138">Per informazioni dettagliate sui requisiti hardware, software, account e autorizzazioni, sui requisiti dei certificati SSL e sui limiti degli oggetti per Azure AD Connect, vedere [prerequisiti per Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) .</span><span class="sxs-lookup"><span data-stu-id="f42b0-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="f42b0-139">È inoltre possibile esaminare la [cronologia delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure ad Connect versione per vedere cosa è incluso e risolto in ogni versione.</span><span class="sxs-lookup"><span data-stu-id="f42b0-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="f42b0-140">2. installare Azure AD Connect e configurare la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="f42b0-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="f42b0-141">Prima di iniziare, verificare di disporre di:</span><span class="sxs-lookup"><span data-stu-id="f42b0-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="f42b0-142">Il nome utente e la password di un amministratore globale di Office 365</span><span class="sxs-lookup"><span data-stu-id="f42b0-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="f42b0-143">Il nome utente e la password di un amministratore di dominio AD DS</span><span class="sxs-lookup"><span data-stu-id="f42b0-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="f42b0-144">Quale metodo di autenticazione (pH, PTA, federato)</span><span class="sxs-lookup"><span data-stu-id="f42b0-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="f42b0-145">Se si desidera utilizzare l' [accesso Single Sign-on (SSO) di Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="f42b0-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="f42b0-146">Eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="f42b0-146">Follow these steps:</span></span>

1. <span data-ttu-id="f42b0-147">Accedere all'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e scegliere **gli** \> utenti **attivi** degli utenti sulla barra di spostamento a sinistra.</span><span class="sxs-lookup"><span data-stu-id="f42b0-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="f42b0-148">Nell'interfaccia di amministrazione, nella pagina **utenti attivi** , scegliere **altre** \> **sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="f42b0-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Nel menu altro, scegliere sincronizzazione directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="f42b0-150">Nella pagina **preparazione di Active Directory** selezionare il collegamento **Scarica Microsoft Azure Active Directory Connect Tool** per iniziare.</span><span class="sxs-lookup"><span data-stu-id="f42b0-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="f42b0-151">Seguire la procedura descritta in [Azure ad Connect e Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="f42b0-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="f42b0-152">3. terminare la configurazione dei domini</span><span class="sxs-lookup"><span data-stu-id="f42b0-152">3. Finish setting up domains</span></span>

<span data-ttu-id="f42b0-153">Seguire la procedura descritta in [create DNS Records for Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare la configurazione dei domini.</span><span class="sxs-lookup"><span data-stu-id="f42b0-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="f42b0-154">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="f42b0-154">Next step</span></span>

<span data-ttu-id="f42b0-155">[Assegnare le licenze agli account utente](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="f42b0-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
