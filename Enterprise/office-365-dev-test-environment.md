---
title: Ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per creare una sottoscrizione di prova di Office 365 per la valutazione o sviluppo e di testing.'
ms.openlocfilehash: 12de8b5dbd468d292e824e5ed3245fc2141cc65c
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="f01fa-103">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="f01fa-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per creare una sottoscrizione di prova di Office 365 per la valutazione o sviluppo e di testing.</span><span class="sxs-lookup"><span data-stu-id="f01fa-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="f01fa-p101">È possibile utilizzare una sottoscrizione di valutazione di Office 365 e creare un ambiente di sviluppo/test di Office 365 per le applicazioni o per illustrare le caratteristiche e funzionalità di Office 365. Sono disponibili due versioni:</span><span class="sxs-lookup"><span data-stu-id="f01fa-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="f01fa-107">L'ambiente di sviluppo/test di Office 365 semplificato è costituito da una sottoscrizione di valutazione di Office 365 che richiede l'accesso dal computer principale.</span><span class="sxs-lookup"><span data-stu-id="f01fa-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="f01fa-p102">Per illustrare rapidamente una caratteristica, eseguire questo ambiente. Per l'ambiente di sviluppo e di testing leggero Office 365, eseguire solo le fasi 2 e 3 di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="f01fa-p103">L'ambiente di sviluppo/test di Office 365 dell'azienda simulata è composto da una sottoscrizione di valutazione di Office 365 e da una intranet di un'organizzazione semplificata connessa a Internet, che è ospitata nei servizi infrastruttura di Microsoft Azure. È possibile compilare questa configurazione completamente nel cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="f01fa-p104">Utilizzare questo ambiente per illustrare una funzionalità o un'app in un ambiente simile a una rete di un'organizzazione tipica connessa a Internet o per le funzionalità che richiedono questo tipo di ambiente. Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, completare le fasi 1, 2 e 3 di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f01fa-p105">Si consiglia di stampare questo articolo per registrare i valori specifici necessari per questo ambiente nei 30 giorni della sottoscrizione di valutazione di Office 365. È possibile estendere la sottoscrizione di valutazione per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="f01fa-118">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f01fa-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="f01fa-119">Fase 1: creare la configurazione di base in Azure</span><span class="sxs-lookup"><span data-stu-id="f01fa-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="f01fa-120">Seguire le istruzioni [nell'ambiente di sviluppo/test di configurazione di Base](base-configuration-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="f01fa-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f01fa-p106">È necessario una sottoscrizione di Azure. È possibile utilizzare la [Versione di valutazione gratuita di Azure](https://azure.microsoft.com/pricing/free-trial/) per questa configurazione. Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [credito Azure mensile per i sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="f01fa-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="f01fa-124">Di seguito è riportata la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="f01fa-124">Here is the resulting configuration.</span></span>
  
![Ambiente di sviluppo e di testing della configurazione di base in Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="f01fa-126">Questa configurazione è costituita dalle macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="f01fa-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="f01fa-127">Fase 2: creare una sottoscrizione di valutazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="f01fa-128">Per avviare la sottoscrizione di valutazione di Office 365 E5, è necessario innanzitutto un nome di società fittizia e un nuovo account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f01fa-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="f01fa-p107">È consigliabile che si utilizza un valore variant il nome di società Contoso per il nome della società è una società fittizia utilizzata nel contenuto di esempio di Microsoft, ma non obbligatorio. Registrare il proprio nome società fittizia:![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="f01fa-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="f01fa-p108">Per l'iscrizione per un nuovo account di Microsoft, passare a [https://outlook.com](https://outlook.com) e creare un account con un nuovo account di posta elettronica e l'indirizzo. Iscriviti a Office 365 si utilizzerà questo account.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="f01fa-133">Registrare il nome e il cognome del nuovo account di seguito:![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="f01fa-133">Record the first and last name of your new account here: ![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="f01fa-134">Registrare l'indirizzo account nuovo messaggio di posta elettronica: ![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-134">Record the new email account address here: ![](./images/Common_Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="f01fa-135">Registrare una sottoscrizione di valutazione di Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="f01fa-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="f01fa-136">Per l'ambiente di sviluppo e di testing di Office 365 leggero, aprire il browser Internet nel computer e passare a [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="f01fa-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="f01fa-137">Per l'ambiente di sviluppo e di testing simulato enterprise di Office 365:</span><span class="sxs-lookup"><span data-stu-id="f01fa-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="f01fa-138">Dal [portale di Azure](https://portal.azure.com), la connessione a CLIENT1 con la CORP\\account User1.</span><span class="sxs-lookup"><span data-stu-id="f01fa-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="f01fa-139">Aprire un prompt dei comandi di Windows PowerShell a livello di amministratore ed eseguire questi comandi:</span><span class="sxs-lookup"><span data-stu-id="f01fa-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="f01fa-140">Fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) per ottenere un file di testo che contiene tutti i comandi di PowerShell in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="f01fa-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="f01fa-141">Nella schermata Start fare clic su **Internet Explorer** e passare a [https://aka.ms/e5trial](https://aka.ms/e5trial).</span><span class="sxs-lookup"><span data-stu-id="f01fa-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="f01fa-142">Nella pagina **iniziale, possiamo conoscere è** specificare:</span><span class="sxs-lookup"><span data-stu-id="f01fa-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="f01fa-143">La posizione fisica dell'utente</span><span class="sxs-lookup"><span data-stu-id="f01fa-143">Your physical location</span></span>
    
  - <span data-ttu-id="f01fa-144">Nome e cognome del nuovo account Microsoft</span><span class="sxs-lookup"><span data-stu-id="f01fa-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="f01fa-145">Il nuovo indirizzo di account di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="f01fa-145">Your new email account address</span></span>
    
  - <span data-ttu-id="f01fa-146">Un numero di telefono dell'ufficio</span><span class="sxs-lookup"><span data-stu-id="f01fa-146">A business phone number</span></span>
    
  - <span data-ttu-id="f01fa-147">Il nome dell'azienda fittizia</span><span class="sxs-lookup"><span data-stu-id="f01fa-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="f01fa-148">Dimensioni dell'organizzazione comprese tra 250-999 persone</span><span class="sxs-lookup"><span data-stu-id="f01fa-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="f01fa-149">Fare clic su **solo uno più passaggio**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="f01fa-150">Nella pagina **Crea l'ID utente** digitare un nome utente con il nuovo indirizzo di posta elettronica, la società fittizia dopo il simbolo @ (rimuovere tutti gli spazi nel nome), quindi (due volte) una password per il nuovo Office 365 per gli account.</span><span class="sxs-lookup"><span data-stu-id="f01fa-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="f01fa-151">Annotare la password in un posto sicuro.</span><span class="sxs-lookup"><span data-stu-id="f01fa-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="f01fa-152">Registrare il nome della società fittizia per fare riferimento come **nome dell'organizzazione**, di seguito:![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="f01fa-152">Record your fictional company name, to be referred to as the **organization name**, here: ![](./images/Common_Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="f01fa-153">Fare clic su **Crea account personale**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="f01fa-p109">Nella **dimostrazione. È possibile aprire. Non. R. robot.** pagina, digitare il numero di telefono del telefono in grado di testo e quindi fare clic su **testo me**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="f01fa-156">Digitare il codice di verifica dal messaggio di testo ricevuto e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="f01fa-157">Registrare l'URL pagina di accesso di seguito (selezionare e copia):![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="f01fa-157">Record the sign-in page URL here (select and copy): ![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="f01fa-158">Registrare l'ID utente di seguito (selezionare e copia): ![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-158">Record the user ID here (select and copy): ![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="f01fa-159">Questo valore verrà considerato il **nome dell'amministratore globale di Office 365**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="f01fa-160">Quando si **pronti iniziare**, fare clic.</span><span class="sxs-lookup"><span data-stu-id="f01fa-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="f01fa-161">Nella pagina successiva, attendere che Office 365 completi la configurazione e che siano disponibili tutti i riquadri.</span><span class="sxs-lookup"><span data-stu-id="f01fa-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="f01fa-162">Dovrebbe essere visualizzata la pagina principale del portale di Office 365 dalla quale è possibile accedere ai servizi di Office Online e all'interfaccia di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="f01fa-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="f01fa-163">Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, ecco la configurazione risultante.</span><span class="sxs-lookup"><span data-stu-id="f01fa-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Ambiente di sviluppo e di testing Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="f01fa-165">Questa configurazione è costituita da:</span><span class="sxs-lookup"><span data-stu-id="f01fa-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="f01fa-166">Le macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.</span><span class="sxs-lookup"><span data-stu-id="f01fa-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="f01fa-167">Una sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="f01fa-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="f01fa-168">Fase 3: configurazione di una sottoscrizione di valutazione di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="f01fa-169">In questa fase, configurare la sottoscrizione a Office 365 con altri utenti e i siti del team di SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="f01fa-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="f01fa-170">Innanzitutto, aggiungere quattro nuovi utenti e assegnare loro le licenze E5.</span><span class="sxs-lookup"><span data-stu-id="f01fa-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="f01fa-171">Utilizzare le istruzioni riportate in [connessione a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell e connettersi a tua nuova sottoscrizione di Office 365 da:</span><span class="sxs-lookup"><span data-stu-id="f01fa-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="f01fa-172">Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).</span><span class="sxs-lookup"><span data-stu-id="f01fa-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="f01fa-173">Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).</span><span class="sxs-lookup"><span data-stu-id="f01fa-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="f01fa-174">Nella finestra di dialogo richiesta credenziali di Windows PowerShell digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e una password.</span><span class="sxs-lookup"><span data-stu-id="f01fa-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="f01fa-175">Immettere il nome dell'organizzazione (ad esempio: contosotoycompany), il prefisso internazionale a due caratteri e quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="f01fa-176">La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 2 e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="f01fa-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="f01fa-177">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="f01fa-178">Visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 3 e registrare in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="f01fa-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="f01fa-179">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="f01fa-180">La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 4 e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="f01fa-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="f01fa-181">Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="f01fa-182">La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 5 e registrarlo in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="f01fa-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="f01fa-183">Successivamente, creare tre nuovi siti del team di SharePoint Online per i reparti Vendite, Produzione e Supporto tecnico.</span><span class="sxs-lookup"><span data-stu-id="f01fa-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="f01fa-184">Creare tre nuovi siti del team di SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f01fa-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="f01fa-185">Installare [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (il x64 versione).</span><span class="sxs-lookup"><span data-stu-id="f01fa-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="f01fa-186">Fare clic su **Start**, digitare **sharepoint**e quindi fare clic su **SharePoint Online Management Shell**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="f01fa-187">Immettere il nome dell'organizzazione (esempio: contosotoycompany), quindi eseguire comandi seguenti dal prompt di SharePoint Online Management Shell per connettersi al servizio SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f01fa-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="f01fa-188">Nella finestra di dialogo **Microsoft SharePoint Online Management Shell** , digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e una password, quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="f01fa-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="f01fa-189">Per creare tre nuovi siti del team (vendite, produzione e supporto tecnico), immettere il nome di amministratore globale di Office 365 e quindi eseguire i comandi seguenti dalla riga di SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="f01fa-190">Eseguire questo comando per elencare gli URL dei nuovi siti:</span><span class="sxs-lookup"><span data-stu-id="f01fa-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="f01fa-191">In Internet Explorer, immettere l'URL del sito Produzione per visualizzare il sito del team di SharePoint Online predefinito per il reparto di produzione.</span><span class="sxs-lookup"><span data-stu-id="f01fa-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="f01fa-192">Registrare i valori per consultarli in futuro</span><span class="sxs-lookup"><span data-stu-id="f01fa-192">Record values for future reference</span></span>

<span data-ttu-id="f01fa-193">Registrare questi valori per utilizzarli o distribuire altre guide di lab di test nell'ambiente di test di distribuzione:</span><span class="sxs-lookup"><span data-stu-id="f01fa-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="f01fa-194">Nome dell'amministratore globale di Office 365: ![](./images/Common_Images/TableLine.png). onmicrosoft.com (nel passaggio 9 della fase 2)</span><span class="sxs-lookup"><span data-stu-id="f01fa-194">Office 365 global administrator name: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="f01fa-195">Annotare anche la password dell'account in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="f01fa-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="f01fa-196">Il nome dell'organizzazione sottoscrizione di prova: ![](./images/Common_Images/TableLine.png) (dal passaggio 4 della fase 2)</span><span class="sxs-lookup"><span data-stu-id="f01fa-196">Your trial subscription organization name: ![](./images/Common_Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="f01fa-197">Per elencare gli account di User 2, User 3, User 4, e User 5, eseguire i comandi seguenti dal modulo di Microsoft Azure Active Directory per il prompt di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="f01fa-198">Registrare i nomi degli account qui:</span><span class="sxs-lookup"><span data-stu-id="f01fa-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="f01fa-199">Nome dell'account utente 2: user2 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-199">User 2 account name: user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="f01fa-200">Nome dell'account utente 3: user3 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-200">User 3 account name: user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="f01fa-201">Nome dell'account utente 4: user4 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-201">User 4 account name: user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="f01fa-202">Nome dell'account utente 5: user5 @![](./images/Common_Images/TableLine.png). onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="f01fa-202">User 5 account name: user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="f01fa-203">Annotare anche le password degli account in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="f01fa-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="f01fa-204">Per elencare gli URL dei siti dei team Vendite, Produzione e Supporto tecnico, eseguire il comando seguente dal prompt di SharePoint Online Management Shell:</span><span class="sxs-lookup"><span data-stu-id="f01fa-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="f01fa-205">URL del sito di produzione: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="f01fa-205">Production site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="f01fa-206">URL sito vendite: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="f01fa-206">Sales site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="f01fa-207">URL del sito del supporto tecnico: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="f01fa-207">Support site URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="f01fa-208">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="f01fa-208">Next steps</span></span>

<span data-ttu-id="f01fa-209">Utilizzare questi articoli aggiuntivi nell'ambiente di sviluppo/test di Office 365:</span><span class="sxs-lookup"><span data-stu-id="f01fa-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="f01fa-210">Sincronizzazione delle directory per l'ambiente di sviluppo e di testing di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-210">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-211">Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365. </span><span class="sxs-lookup"><span data-stu-id="f01fa-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-212">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-213">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-214">Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-215">Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-216">Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-217">Sito del team SharePoint Online isolato nell'ambiente di sviluppo/test</span><span class="sxs-lookup"><span data-stu-id="f01fa-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-218">Classificazione e assegnazione di etichette ai dati nell'ambiente di sviluppo/test di Office 365 </span><span class="sxs-lookup"><span data-stu-id="f01fa-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="f01fa-219">Estendere l'ambiente di sviluppo/testing di Office 365 per includere ulteriori offerte cloud di Microsoft:</span><span class="sxs-lookup"><span data-stu-id="f01fa-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="f01fa-220">Ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f01fa-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="f01fa-221">Ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="f01fa-222">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f01fa-222">See Also</span></span>

- [<span data-ttu-id="f01fa-223">Test Lab Guide (TLG) di adozione cloud</span><span class="sxs-lookup"><span data-stu-id="f01fa-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="f01fa-224">Ambiente di sviluppo/test di Office 365 e Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="f01fa-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
 - [<span data-ttu-id="f01fa-225">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="f01fa-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


