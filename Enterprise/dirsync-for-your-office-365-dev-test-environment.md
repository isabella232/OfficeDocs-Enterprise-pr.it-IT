---
title: Sincronizzazione della directory per l'ambiente di sviluppo e di testing di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "Riepilogo: Configurare la sincronizzazione di directory per l'ambiente di sviluppo e di testing di Office 365."
ms.openlocfilehash: 0b51e3cb6c348c5c6f9bb1a6d818a18fb123e1b6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067762"
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a><span data-ttu-id="b2274-103">Sincronizzazione della directory per l'ambiente di sviluppo e di testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="b2274-103">Directory synchronization for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="b2274-104">**Riepilogo:** Configurare la sincronizzazione di directory per l'ambiente di sviluppo e di testing di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b2274-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="b2274-p101">Molte organizzazioni usano Azure AD Connect e la sincronizzazione delle directory per sincronizzare il set di account della foresta Dominio di Active Directory (AD DS) locale per il set di account in Office 365. In questo articolo viene illustrato come aggiungere la sincronizzazione della directory con la sincronizzazione hash delle password per l'ambiente di sviluppo e di testing di Office 365, determinando la configurazione seguente.</span><span class="sxs-lookup"><span data-stu-id="b2274-p101">Many organizations use Azure AD Connect and directory synchronization to synchronize the set of accounts in their on-premises Active Directory Domain Services (AD DS) forest to the set of accounts in Office 365. This article describes how you can add directory synchronization with password hash synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![Ambiente di sviluppo e di testing Office 365 con sincronizzazione della directory](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="b2274-108">Questa configurazione è costituita da:</span><span class="sxs-lookup"><span data-stu-id="b2274-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="b2274-109">Una sottoscrizione di valutazione di Office 365 E5 che scade dopo 30 giorni dalla creazione.</span><span class="sxs-lookup"><span data-stu-id="b2274-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
- <span data-ttu-id="b2274-p102">Una intranet dell'organizzazione semplificata connessa a Internet e costituita da tre macchine virtuali in una sottorete di una rete virtuale Azure (DC1 APP1 e CLIENT1). Microsoft Azure Active Directory Connect viene eseguito su APP1 per sincronizzare il dominio di Windows Server AD con Office 365.</span><span class="sxs-lookup"><span data-stu-id="b2274-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the AD DS domain to Office 365.</span></span>
    
<span data-ttu-id="b2274-112">Le fasi principali della configurazione dell'ambiente di sviluppo e di testing sono tre:</span><span class="sxs-lookup"><span data-stu-id="b2274-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="b2274-113">Creare l'ambiente di sviluppo e di testing di Office 365 (le macchine virtuali DC1, APP1 e CLIENT1 in una rete virtuale Azure con una sottoscrizione di valutazione di Office 365 E5).</span><span class="sxs-lookup"><span data-stu-id="b2274-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
2. <span data-ttu-id="b2274-114">Installare e configurare Azure AD Connect su APP1.</span><span class="sxs-lookup"><span data-stu-id="b2274-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="b2274-115">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli nella serie di guide dei lab di test di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b2274-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="b2274-116">Fase 1: creare l'ambiente di sviluppo e di testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="b2274-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="b2274-p103">Seguire le istruzioni nelle fasi 1, 2 e 3 dell'articolo [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md). Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="b2274-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Ambiente di sviluppo e di testing Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="b2274-120">Questa configurazione è costituita da:</span><span class="sxs-lookup"><span data-stu-id="b2274-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="b2274-121">Una sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="b2274-121">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="b2274-122">Una intranet dell’organizzazione semplificata connessa a Internet e costituita dalle macchine virtuali DC1 APP1 e CLIENT1 in una sottorete di una rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="b2274-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="b2274-123">Fase 2: Installare Azure AD Connect su APP1</span><span class="sxs-lookup"><span data-stu-id="b2274-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="b2274-p104">Una volta installato e configurato, Azure AD Connect sincronizza il set di account del dominio CORP AD DS con il set di account nella sottoscrizione di valutazione di Office 365. Nella procedura seguente è decritta l'installazione di Azure AD Connect su APP1 e la verifica del corretto funzionamento.</span><span class="sxs-lookup"><span data-stu-id="b2274-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP AD DS domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and checking that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="b2274-126">Installare e configurare Azure AD Connect su APP1</span><span class="sxs-lookup"><span data-stu-id="b2274-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="b2274-127">Dal [portale Azure](https://portal.azure.com), connettersi ad APP1 con l'account CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="b2274-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="b2274-128">Da APP1, aprire un prompt dei comandi di Windows PowerShell a livello di amministratore ed eseguire questi comandi:</span><span class="sxs-lookup"><span data-stu-id="b2274-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="b2274-129">Dalla barra delle applicazioni, fare clic su **Internet Explorer** e accedere a [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span><span class="sxs-lookup"><span data-stu-id="b2274-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="b2274-130">Nella pagina Microsoft Azure Active Directory Connect, fare clic su **Download** e quindi su **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="b2274-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="b2274-131">Nella pagina di **Benvenuto in Azure Active Directory Connect**, fare clic su **Accetto** e quindi su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="b2274-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="b2274-132">Nella pagina **Impostazioni rapide**, fare clic su **Usa impostazioni rapide**.</span><span class="sxs-lookup"><span data-stu-id="b2274-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="b2274-133">Nella pagina **Connessione ad Azure AD**, digitare il nome dell'account amministratore globale in **Nome utente**, digitare la password in **Password** e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b2274-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="b2274-134">Nella pagina **Connessione ad AD DS**, digitare **CORP\\User1** in **Nome utente**, digitare la relativa password in **Password** e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b2274-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="b2274-135">Nella pagina **Configurazione dell'accesso ad Azure AD**, fare clic su **Continua senza domini verificati**, quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b2274-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="b2274-136">Nella pagina **Pronto per la configurazione** fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="b2274-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="b2274-137">Nella pagina **Configurazione completata**, fare clic su **Esci**.</span><span class="sxs-lookup"><span data-stu-id="b2274-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="b2274-138">In Internet Explorer accedere all'interfaccia di amministrazione di Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) e quindi all'abbonamento di valutazione di Office 365 con l'account di amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="b2274-138">In Internet Explorer, go to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="b2274-139">Dalla pagina principale del portale, fare clic su **Admin**.</span><span class="sxs-lookup"><span data-stu-id="b2274-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="b2274-140">Nel riquadro di spostamento sinistro fare clic su **Utenti > Utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="b2274-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="b2274-p105">Si noti l'account denominato **User1**. Questo account deriva dal dominio CORP AD DS ed è la prova che la sincronizzazione della directory ha funzionato.</span><span class="sxs-lookup"><span data-stu-id="b2274-p105">Note the account named **User1**. This account is from the CORP AD DS domain and is proof that directory synchronization has worked.</span></span>
    
15. <span data-ttu-id="b2274-p106">Fare clic sull'account **User1**. Per le licenze di prodotti, fare clic su **Modifica**.</span><span class="sxs-lookup"><span data-stu-id="b2274-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="b2274-p107">In **Licenze di prodotti**, selezionare il paese e fare clic sul controllo **Disattiva** per **Office 365 Enterprise E5** (passando ad **Attiva**). Fare clic su **Salva** nella parte inferiore della pagina e selezionare **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="b2274-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="b2274-147">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="b2274-147">This is the resulting configuration.</span></span>
  
![Ambiente di sviluppo e di testing Office 365 con sincronizzazione della directory](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="b2274-149">Questa configurazione è costituita da:</span><span class="sxs-lookup"><span data-stu-id="b2274-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="b2274-150">Una sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="b2274-150">An Office 365 E5 Trial Subscription.</span></span>
- <span data-ttu-id="b2274-p108">Una intranet dell'organizzazione semplificata connessa a Internet e costituita dalle macchine virtuali DC1 APP1 e CLIENT1 in una sottorete di una rete virtuale Azure. Microsoft Azure Active Directory Connect viene eseguito su APP1 per sincronizzare il dominio CORP AD DS con Office 365 ogni 30 minuti.</span><span class="sxs-lookup"><span data-stu-id="b2274-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP AD DS domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b2274-153">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="b2274-153">Next Step</span></span>

<span data-ttu-id="b2274-154">Quando si è pronti per distribuire la sincronizzazione della directory nella propria organizzazione, vedere [Distribuire la sincronizzazione della directory di Office 365 in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span><span class="sxs-lookup"><span data-stu-id="b2274-154">When you are ready to deploy directory synchronization for your organization, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2274-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b2274-155">See Also</span></span>

[<span data-ttu-id="b2274-156">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="b2274-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="b2274-157">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="b2274-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)

[<span data-ttu-id="b2274-158">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="b2274-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)

[<span data-ttu-id="b2274-159">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="b2274-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="b2274-160">Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="b2274-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="b2274-161">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="b2274-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




