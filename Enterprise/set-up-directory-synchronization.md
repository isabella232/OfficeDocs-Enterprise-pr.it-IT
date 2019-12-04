---
title: Configurare la sincronizzazione della directory per Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
ms.openlocfilehash: 5cd56eb90e6421d530ff0c2b8739bd13be238eae
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814594"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="e7ff1-103">Configurare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="e7ff1-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="e7ff1-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="e7ff1-105">Office 365 usa un tenant di Azure Active Directory (Azure AD) per archiviare e gestire le identità per l'autenticazione e le autorizzazioni per accedere alle risorse basate sul cloud.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="e7ff1-106">Se si usa Active Directory Domain Services (AD DS), è possibile sincronizzare gli account utente, i gruppi e i contatti di Active Directory con il tenant di Azure AD dell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="e7ff1-107">Questa corrisponde all'identità ibrida per Office 365,</span><span class="sxs-lookup"><span data-stu-id="e7ff1-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="e7ff1-108">i cui componenti sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-108">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="e7ff1-109">Azure AD Connect viene eseguito in un server locale e consente di sincronizzare il servizio AD DS con il tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-109">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="e7ff1-110">Oltre alla sincronizzazione della directory, è anche possibile specificare le opzioni di autenticazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="e7ff1-110">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="e7ff1-111">Sincronizzazione dell'hash delle password (PHS)</span><span class="sxs-lookup"><span data-stu-id="e7ff1-111">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="e7ff1-112">L'autenticazione viene eseguita direttamente da Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-112">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="e7ff1-113">Autenticazione pass-through (PTA)</span><span class="sxs-lookup"><span data-stu-id="e7ff1-113">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="e7ff1-114">L'autenticazione di Azure AD viene eseguita da AD DS.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-114">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="e7ff1-115">Autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="e7ff1-115">Federated authentication</span></span>

  <span data-ttu-id="e7ff1-116">Azure AD reindirizza il computer client richiedendo l'autenticazione per contattare un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-116">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="e7ff1-117">Per altre informazioni, vedere [Identità ibride](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-117">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="e7ff1-118">1. Esaminare i prerequisiti per Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="e7ff1-118">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="e7ff1-119">Con l'abbonamento a Office 365 è inclusa una sottoscrizione gratuita di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-119">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="e7ff1-120">Quando si configura la sincronizzazione della directory, si installa Azure AD Connect in uno dei server locali.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-120">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="e7ff1-121">Per Office 365 è necessario:</span><span class="sxs-lookup"><span data-stu-id="e7ff1-121">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="e7ff1-122">Verificare il dominio locale.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-122">Verify your on-premises domain.</span></span> <span data-ttu-id="e7ff1-123">La procedura guidata di Azure AD Connect illustra i passaggi necessari per questa operazione.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-123">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="e7ff1-124">Ottenere i nomi utente e le password per gli account di amministrazione del tenant di Office 365 e di AD DS.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-124">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="e7ff1-125">Per il server locale in cui si installa Azure AD Connect, sono necessari:</span><span class="sxs-lookup"><span data-stu-id="e7ff1-125">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="e7ff1-126">**Sistema operativo server**</span><span class="sxs-lookup"><span data-stu-id="e7ff1-126">**Server OS**</span></span>|<span data-ttu-id="e7ff1-127">**Altro software**</span><span class="sxs-lookup"><span data-stu-id="e7ff1-127">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e7ff1-128">Windows Server 2012 R2 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="e7ff1-128">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="e7ff1-129">- PowerShell viene installato per impostazione predefinita, pertanto non è richiesta alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-129">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="e7ff1-130">- .NET 4.5.1 e versioni successive sono disponibili tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-130">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="e7ff1-131">Assicurarsi di aver installato gli aggiornamenti più recenti di Windows Server nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-131">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="e7ff1-132">Windows Server 2008 R2 con Service Pack 1 (SP1)\*\* o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="e7ff1-132">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="e7ff1-133">- La versione più recente di PowerShell è disponibile in Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-133">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="e7ff1-134">Cercarla nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-134">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="e7ff1-135">- .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="e7ff1-136">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="e7ff1-136">Windows Server 2008</span></span> | <span data-ttu-id="e7ff1-137">- La versione supportata più recente di PowerShell è disponibile in Windows Management Framework 3.0, scaricabile dall'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-137">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="e7ff1-138">- .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-138">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="e7ff1-139">Per informazioni dettagliate sui requisiti hardware, software, per account e autorizzazioni e certificati SSL e sui limiti degli oggetti per Azure AD Connect, vedere [Prerequisiti di Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-139">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="e7ff1-140">È anche possibile esaminare la [cronologia di rilascio delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure AD Connect per vedere cosa include e quali problemi sono stati risolti in ogni versione.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-140">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="e7ff1-141">2. Installare Azure AD Connect e configurare la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="e7ff1-141">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="e7ff1-142">Prima di iniziare, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e7ff1-142">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="e7ff1-143">Assicurarsi di disporre del nome utente e della password di un amministratore globale di Office 365</span><span class="sxs-lookup"><span data-stu-id="e7ff1-143">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="e7ff1-144">Assicurarsi di disporre del nome utente e della password di un amministratore del dominio di AD DS</span><span class="sxs-lookup"><span data-stu-id="e7ff1-144">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="e7ff1-145">Scegliere il metodo di autenticazione, tra PHS, PTA e federata</span><span class="sxs-lookup"><span data-stu-id="e7ff1-145">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="e7ff1-146">Indicare se si intende usare [Accesso Single Sign-On facile di Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="e7ff1-146">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="e7ff1-147">Eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="e7ff1-147">Follow these steps:</span></span>

1. <span data-ttu-id="e7ff1-148">Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e scegliere **Utenti** \> **Utenti attivi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-148">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="e7ff1-149">Nella pagina **utenti attivi** , scegliere **altro** (tre punti) \> **sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-149">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="e7ff1-150">Nella pagina **preparazione di Azure Active Directory** selezionare l' **area download per ottenere il collegamento dello strumento Azure ad Connect** per iniziare.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-150">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="e7ff1-151">Seguire la procedura in [Roadmap di installazione di Azure AD Connect e Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="e7ff1-152">3. Completare la configurazione dei domini</span><span class="sxs-lookup"><span data-stu-id="e7ff1-152">3. Finish setting up domains</span></span>

<span data-ttu-id="e7ff1-153">Seguire la procedura descritta in [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) per completare la configurazione dei domini.</span><span class="sxs-lookup"><span data-stu-id="e7ff1-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="e7ff1-154">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="e7ff1-154">Next step</span></span>

<span data-ttu-id="e7ff1-155">[Assegnare licenze agli account utente](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="e7ff1-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md)</span></span>
