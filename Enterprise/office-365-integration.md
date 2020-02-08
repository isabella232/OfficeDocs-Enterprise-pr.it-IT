---
title: Integrazione di Office 365 con ambienti locali
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Informazioni su come integrare Office 365 con i servizi directory esistenti.
ms.openlocfilehash: 61feabb4d62b4b67538f45a3f827c746197b55d3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844497"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="3db3c-103">Integrazione di Office 365 con ambienti locali</span><span class="sxs-lookup"><span data-stu-id="3db3c-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="3db3c-104">*Questo articolo si applica sia a Office 365 Enterprise che a Microsoft 365 Enterprise*.</span><span class="sxs-lookup"><span data-stu-id="3db3c-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="3db3c-105">È possibile integrare Office 365 con i servizi directory esistenti e con un'installazione locale di Exchange Server, Skype for Business Server 2015 o SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="3db3c-105">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server.</span></span>
  
 - <span data-ttu-id="3db3c-106">Eseguendo l'integrazione con i servizi directory, è possibile sincronizzare e gestire gli account utente di entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="3db3c-106">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="3db3c-107">È anche possibile aggiungere la sincronizzazione dell'hash delle password o Single Sign-On (SSO) per consentire agli utenti di accedere a entrambi gli ambienti con le proprie credenziali locali.</span><span class="sxs-lookup"><span data-stu-id="3db3c-107">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="3db3c-108">Mediante l'integrazione con i prodotti server locali viene creato un ambiente ibrido.</span><span class="sxs-lookup"><span data-stu-id="3db3c-108">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="3db3c-109">Un ambiente ibrido può facilitare la migrazione completa di utenti o informazioni in Office 365, ma si può anche continuare a tenere parte degli utenti o delle informazioni in locale e parte nel cloud.</span><span class="sxs-lookup"><span data-stu-id="3db3c-109">A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="3db3c-110">Per altre informazioni sugli ambienti ibridi, vedere [Panoramica sul cloud ibrido](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span><span class="sxs-lookup"><span data-stu-id="3db3c-110">For more information about hybrid environments, see [Hybrid cloud overview](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span></span>

<span data-ttu-id="3db3c-111">È anche possibile usare gli Advisor di Azure Active Directory (Azure AD) per istruzioni sulla configurazione personalizzata (è necessario aver effettuato l'accesso a Office 365):</span><span class="sxs-lookup"><span data-stu-id="3db3c-111">You can also use the Azure Active Directory (Azure AD) advisors for customized setup guidance (you must be signed in to Office 365):</span></span>

- [<span data-ttu-id="3db3c-112">Advisor di Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3db3c-112">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="3db3c-113">Assistente distribuzione di AD FS</span><span class="sxs-lookup"><span data-stu-id="3db3c-113">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="3db3c-114">Guida alla configurazione di Azure AD Premium</span><span class="sxs-lookup"><span data-stu-id="3db3c-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="3db3c-115">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="3db3c-115">Before you begin</span></span>

<span data-ttu-id="3db3c-116">Prima di integrare Office 365 e un ambiente locale, è anche necessario occuparsi della [pianificazione della rete e ottimizzazione delle prestazioni](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="3db3c-116">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning](network-planning-and-performance.md).</span></span> <span data-ttu-id="3db3c-117">È anche opportuno conoscere i [modelli di identità](about-office-365-identity.md).</span><span class="sxs-lookup"><span data-stu-id="3db3c-117">You will also want to understand the available [identity models](about-office-365-identity.md).</span></span> 

<span data-ttu-id="3db3c-118">Vedere [Dove gestire gli account di Office 365](manage-office-365-accounts.md) per un elenco degli strumenti che è possibile usare per gestire utenti e account di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3db3c-118">See [where to manage Office 365 accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="3db3c-119">Integrare Office 365 con i servizi directory</span><span class="sxs-lookup"><span data-stu-id="3db3c-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="3db3c-120">Se si dispone di account utente in una directory locale, non è auspicabile ricreali tutti in Office 365, rischiando di introdurre incoerenze o errori tra gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="3db3c-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="3db3c-121">La sincronizzazione della directory consente di eseguire il mirroring degli account tra l'ambiente online e quello locale.</span><span class="sxs-lookup"><span data-stu-id="3db3c-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="3db3c-122">La sincronizzazione della directory evita agli utenti la necessità di ricordare nuove informazioni per ogni ambiente e all'amministratore di creare o aggiornare gli account due volte.</span><span class="sxs-lookup"><span data-stu-id="3db3c-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="3db3c-123">Sarà necessario [preparare la directory locale](prepare-for-directory-synchronization.md) per la sincronizzazione della directory. Questa operazione può essere eseguita manualmente o usando lo [strumento IdFix](install-and-run-idfix.md) (lo strumento IdFix funziona solo con Active Directory Domain Services).</span><span class="sxs-lookup"><span data-stu-id="3db3c-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory Domain Services [AD DS]).</span></span> 
  
![Usare la sincronizzazione della directory per mantenere sincronizzate le informazioni degli account locali e di quelli online](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="3db3c-125">Se si vuole consentire agli utenti di accedere a Office 365 con le proprie credenziali locali, è anche possibile configurare SSO.</span><span class="sxs-lookup"><span data-stu-id="3db3c-125">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="3db3c-126">Con SSO, Office 365 viene configurato in modo da considerare attendibile l'ambiente locale per l'autenticazione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="3db3c-126">With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![Con Single Sign-On, lo stesso account è disponibile sia nell'ambiente locale che nell'ambiente online](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="3db3c-128">Tecniche di gestione degli account utente diverse offrono agli utenti esperienze diverse, come illustrato nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="3db3c-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="3db3c-129">Sincronizzazione della directory con o senza sincronizzazione dell'hash delle password o autenticazione pass-through</span><span class="sxs-lookup"><span data-stu-id="3db3c-129">Directory synchronization with or without password hash synchronization or pass-through authentication</span></span>

<span data-ttu-id="3db3c-130">Un utente accede all'ambiente locale con il proprio account utente (dominio\nomeutente).</span><span class="sxs-lookup"><span data-stu-id="3db3c-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="3db3c-131">Quando passa a Office 365, deve eseguire nuovamente l'accesso con l'account aziendale o dell'Istituto di istruzione (utente@dominio.com).</span><span class="sxs-lookup"><span data-stu-id="3db3c-131">When they go to Office 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="3db3c-132">Il nome utente è lo stesso in entrambi gli ambienti.</span><span class="sxs-lookup"><span data-stu-id="3db3c-132">The user name is the same in both environments.</span></span> <span data-ttu-id="3db3c-133">Quando si aggiunge la sincronizzazione dell'hash delle password o l'autenticazione pass-through, l'utente ha la stessa password per entrambi gli ambienti, ma dovrà specificare di nuovo queste credenziali quando accede a Office 365.</span><span class="sxs-lookup"><span data-stu-id="3db3c-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365.</span></span> <span data-ttu-id="3db3c-134">La sincronizzazione della directory con la sincronizzazione dell'hash delle password è lo scenario più di frequente.</span><span class="sxs-lookup"><span data-stu-id="3db3c-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="3db3c-135">Per configurare la sincronizzazione della directory, usare Azure Active Directory Connect.</span><span class="sxs-lookup"><span data-stu-id="3db3c-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="3db3c-136">Per le istruzioni, vedere [Configurare la sincronizzazione della directory per Office 365](set-up-directory-synchronization.md) e [Azure AD Connect con impostazioni rapide](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span><span class="sxs-lookup"><span data-stu-id="3db3c-136">For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="3db3c-137">Per saperne di più, vedere gli argomenti relativi alla [preparazione per la sincronizzazione della directory con Office 365](prepare-for-directory-synchronization.md) e all'[integrazione delle identità locali con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span><span class="sxs-lookup"><span data-stu-id="3db3c-137">Learn more about [preparing for directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="3db3c-138">Sincronizzazione della directory con SSO</span><span class="sxs-lookup"><span data-stu-id="3db3c-138">Directory synchronization with SSO</span></span>

<span data-ttu-id="3db3c-139">Un utente accede all'ambiente locale con il proprio account utente.</span><span class="sxs-lookup"><span data-stu-id="3db3c-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="3db3c-140">Quando passa a Office 365, viene connesso automaticamente oppure accede con le stesse credenziali usate per l'ambiente locale (dominio\nomeutente).</span><span class="sxs-lookup"><span data-stu-id="3db3c-140">When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="3db3c-141">Per configurare SSO si usa anche Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="3db3c-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="3db3c-142">Per le istruzioni, vedere [Installazione personalizzata di Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span><span class="sxs-lookup"><span data-stu-id="3db3c-142">For instructions, read [Custom installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="3db3c-143">Vedere [Accesso Single Sign-On alle applicazioni in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span><span class="sxs-lookup"><span data-stu-id="3db3c-143">Learn more about [single sign-on to applications in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="3db3c-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="3db3c-144">Azure AD Connect</span></span>

<span data-ttu-id="3db3c-145">Azure AD Connect sostituisce le precedenti versioni di strumenti di integrazione delle identità come DirSync e Azure AD Sync. Per altre informazioni, vedere [Che cos'è l'identità ibrida con Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span><span class="sxs-lookup"><span data-stu-id="3db3c-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [What is hybrid identity with Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="3db3c-146">Per eseguire l'aggiornamento da Azure Active Directory Sync ad Azure AD Connect, vedere le [istruzioni di aggiornamento](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span><span class="sxs-lookup"><span data-stu-id="3db3c-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> 

<span data-ttu-id="3db3c-147">Vedere anche [Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span><span class="sxs-lookup"><span data-stu-id="3db3c-147">Also see [Deploy Office 365 Directory Synchronization in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>

## <a name="see-also"></a><span data-ttu-id="3db3c-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3db3c-148">See also</span></span>

[<span data-ttu-id="3db3c-149">Panoramica di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="3db3c-149">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
