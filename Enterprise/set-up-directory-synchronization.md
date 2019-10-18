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
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162479"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="8c4f6-103">Configurare la sincronizzazione della directory per Office 365</span><span class="sxs-lookup"><span data-stu-id="8c4f6-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="8c4f6-104">Office 365 usa un tenant di Azure Active Directory (Azure AD) per archiviare e gestire le identità per l'autenticazione e le autorizzazioni per accedere alle risorse basate sul cloud.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="8c4f6-105">Se si usa Active Directory Domain Services (AD DS), è possibile sincronizzare gli account utente, i gruppi e i contatti di Active Directory con il tenant di Azure AD dell'abbonamento a Office 365.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="8c4f6-106">Questa corrisponde all'identità ibrida per Office 365,</span><span class="sxs-lookup"><span data-stu-id="8c4f6-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="8c4f6-107">i cui componenti sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="8c4f6-108">Azure AD Connect viene eseguito in un server locale e consente di sincronizzare il servizio AD DS con il tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="8c4f6-109">Oltre alla sincronizzazione della directory, è anche possibile specificare le opzioni di autenticazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="8c4f6-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="8c4f6-110">Sincronizzazione dell'hash delle password (PHS)</span><span class="sxs-lookup"><span data-stu-id="8c4f6-110">Password hash synchronization</span></span>

  <span data-ttu-id="8c4f6-111">L'autenticazione viene eseguita direttamente da Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="8c4f6-112">Autenticazione pass-through (PTA)</span><span class="sxs-lookup"><span data-stu-id="8c4f6-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="8c4f6-113">L'autenticazione di Azure AD viene eseguita da AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="8c4f6-114">Autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="8c4f6-114">Federated authentication</span></span>

  <span data-ttu-id="8c4f6-115">Azure AD reindirizza il computer client richiedendo l'autenticazione per contattare un altro provider di identità.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="8c4f6-116">Per altre informazioni, vedere [Identità ibride](plan-for-directory-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="8c4f6-117">1. Esaminare i prerequisiti per Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="8c4f6-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="8c4f6-118">Con l'abbonamento a Office 365 è inclusa una sottoscrizione gratuita di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="8c4f6-119">Quando si configura la sincronizzazione della directory, si installa Azure AD Connect in uno dei server locali.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="8c4f6-120">Per Office 365 è necessario:</span><span class="sxs-lookup"><span data-stu-id="8c4f6-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="8c4f6-121">Verificare il dominio locale.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-121">Verify your domain</span></span> <span data-ttu-id="8c4f6-122">La procedura guidata di Azure AD Connect illustra i passaggi necessari per questa operazione.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="8c4f6-123">Ottenere i nomi utente e le password per gli account di amministrazione del tenant di Office 365 e di AD DS.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="8c4f6-124">Per il server locale in cui si installa Azure AD Connect, sono necessari:</span><span class="sxs-lookup"><span data-stu-id="8c4f6-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="8c4f6-125">**Sistema operativo server**</span><span class="sxs-lookup"><span data-stu-id="8c4f6-125">**Server OS**</span></span>|<span data-ttu-id="8c4f6-126">**Altro software**</span><span class="sxs-lookup"><span data-stu-id="8c4f6-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8c4f6-127">Windows Server 2012 R2 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="8c4f6-127">Windows Server 2012 R2 and 2012</span></span> | <span data-ttu-id="8c4f6-128">- PowerShell viene installato per impostazione predefinita, pertanto non è richiesta alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="8c4f6-129">- .NET 4.5.1 e versioni successive sono disponibili tramite Windows Update.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="8c4f6-130">Assicurarsi di aver installato gli aggiornamenti più recenti di Windows Server nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="8c4f6-131">Windows Server 2008 R2 con Service Pack 1 (SP1)\*\* o Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8c4f6-131">SQL Server 2008 R2 with Service Pack 1 (SP1) or SQL Server 2012</span></span> | <span data-ttu-id="8c4f6-132">- La versione più recente di PowerShell è disponibile in Windows Management Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="8c4f6-133">Cercarla nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="8c4f6-134">- .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="8c4f6-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="8c4f6-135">Windows Server 2008</span></span> | <span data-ttu-id="8c4f6-136">- La versione supportata più recente di PowerShell è disponibile in Windows Management Framework 3.0, scaricabile dall'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="8c4f6-137">- .NET 4.5.1 e versioni successive sono disponibili nell'[Area download Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="8c4f6-138">Per informazioni dettagliate sui requisiti hardware, software, per account e autorizzazioni e certificati SSL e sui limiti degli oggetti per Azure AD Connect, vedere [Prerequisiti di Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="8c4f6-139">È anche possibile esaminare la [cronologia di rilascio delle versioni](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) di Azure AD Connect per vedere cosa include e quali problemi sono stati risolti in ogni versione.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="8c4f6-140">2. Installare Azure AD Connect e configurare la sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="8c4f6-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="8c4f6-141">Prima di iniziare, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8c4f6-141">Before you begin, make sure you have the following:</span></span>

- <span data-ttu-id="8c4f6-142">Assicurarsi di disporre del nome utente e della password di un amministratore globale di Office 365</span><span class="sxs-lookup"><span data-stu-id="8c4f6-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="8c4f6-143">Assicurarsi di disporre del nome utente e della password di un amministratore del dominio di AD DS</span><span class="sxs-lookup"><span data-stu-id="8c4f6-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="8c4f6-144">Scegliere il metodo di autenticazione, tra PHS, PTA e federata</span><span class="sxs-lookup"><span data-stu-id="8c4f6-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="8c4f6-145">Indicare se si intende usare [Accesso Single Sign-On facile di Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="8c4f6-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="8c4f6-146">Eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="8c4f6-146">Follow these steps:</span></span>

1. <span data-ttu-id="8c4f6-147">Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com) e scegliere **Utenti** \> **Utenti attivi** nel riquadro di spostamento sinistro.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="8c4f6-148">Nella pagina **Utenti attivi** dell'interfaccia di amministrazione scegliere **Altro** \> **Sincronizzazione della directory**.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-148">In the admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![Nel menu Altro scegliere Sincronizzazione della directory](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="8c4f6-150">Nella pagina **Preparazione di Active Directory** selezionare il collegamento **Scaricare lo strumento Microsoft Azure Active Directory Connect** per iniziare.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-150">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="8c4f6-151">Seguire la procedura in [Roadmap di installazione di Azure AD Connect e Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="8c4f6-152">3. Completare la configurazione dei domini</span><span class="sxs-lookup"><span data-stu-id="8c4f6-152">3. Finish setting up domains</span></span>

<span data-ttu-id="8c4f6-153">Seguire la procedura descritta in [Creare record DNS per Office 365 quando si gestiscono i record DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) per completare la configurazione dei domini.</span><span class="sxs-lookup"><span data-stu-id="8c4f6-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="8c4f6-154">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="8c4f6-154">Next step</span></span>

<span data-ttu-id="8c4f6-155">[Assegnare licenze agli account utente](assign-licenses-to-user-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="8c4f6-155">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md)</span></span>
