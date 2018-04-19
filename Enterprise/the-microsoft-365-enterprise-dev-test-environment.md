---
title: Ambiente di sviluppo e di testing di Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che include Office 365 E5, mobilità aziendale + E5 di sicurezza (EMS) e un computer che esegue Windows 10 Enterprise.'
ms.openlocfilehash: 9ef1c13d7ae194ff4ba31abaf379529220ffa14f
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="b3b91-103">Ambiente di sviluppo/test di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b3b91-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="b3b91-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che include Office 365 E5, mobilità aziendale + E5 di sicurezza (EMS) e un computer che esegue Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="b3b91-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="b3b91-105">In questo articolo vengono fornite istruzioni dettagliate per creare un ambiente semplificato per testare le funzionalità di [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="b3b91-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="b3b91-106">Fase 1: creare la sottoscrizione di Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="b3b91-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="b3b91-107">Seguire i passaggi della fase 2 e la fase 3 dell' [ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md) per creare un ambiente di sviluppo e di testing lightweight Office 365, come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="b3b91-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="b3b91-108">**Nella figura 1: La sottoscrizione di Office 365 E5 con il relativo account utente e tenant di Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="b3b91-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Fase 1 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="b3b91-p101">La sottoscrizione di valutazione di Office 365 E5 è 30 giorni, che possono essere facilmente esteso a 60 giorni. Per un ambiente di sviluppo e di testing permanente, creare una nuova con un numero limitato di licenze di sottoscrizione a pagamento.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p101">The Office 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="b3b91-112">Fase 2: aggiungere EMS</span><span class="sxs-lookup"><span data-stu-id="b3b91-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="b3b91-113">In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di EMS E5 e aggiungerla alla stessa organizzazione della sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="b3b91-113">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="b3b91-114">Innanzitutto, aggiungere la sottoscrizione di prova EMS E5 e assegna una licenza EMS all'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="b3b91-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="b3b91-p102">Con un'istanza privata di un browser, accedere al portale di Office 365 con le credenziali dell'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="b3b91-p102">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="b3b91-117">Scegliere il riquadro **Amministrazione**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="b3b91-118">Nella scheda **Interfaccia di amministrazione di Office** del browser fare clic su **Fatturazione > Servizi di acquisto** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="b3b91-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="b3b91-p103">Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="b3b91-121">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="b3b91-122">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="b3b91-123">Nella scheda **Interfaccia di amministrazione di Office 365** del browser fare clic su **Utenti > Utenti attivi** nel riquadro di spostamento di sinistra.</span><span class="sxs-lookup"><span data-stu-id="b3b91-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="b3b91-124">Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-124">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="b3b91-125">Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="b3b91-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="b3b91-p104">La sottoscrizione di valutazione Enterprise Mobility + Security E5 è valida per 90 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="b3b91-128">***Se sono state completate fase 3 del*** [Ambiente di sviluppo e di testing di office 365](office-365-dev-test-environment.md), ripetere i passaggi 8 e 9 della procedura precedente per tutti gli altri account (utente 2, 3 utente, utente 4 e 5 utente).</span><span class="sxs-lookup"><span data-stu-id="b3b91-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="b3b91-129">A questo punto, l'ambiente di sviluppo/di testing dispone di:</span><span class="sxs-lookup"><span data-stu-id="b3b91-129">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="b3b91-130">Office 365 Enterprise E5 ed EMS E5 sottoscrizioni di valutazione condivisione stesso tenant di Azure Active Directory con l'elenco di account utente.</span><span class="sxs-lookup"><span data-stu-id="b3b91-130">Office 365 E5 Enterprise and EMS E5 trial subscriptions sharing the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="b3b91-131">Tutti gli account utente appropriati (solo l'amministratore globale o tutti gli account utente cinque) sono abilitati all'utilizzo di Office 365 E5 ed EMS E5.</span><span class="sxs-lookup"><span data-stu-id="b3b91-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="b3b91-132">La figura 2 mostra la configurazione risultante che consente di aggiungere EMS.</span><span class="sxs-lookup"><span data-stu-id="b3b91-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="b3b91-133">**Figura 2: Aggiunta di sottoscrizione di prova EMS**</span><span class="sxs-lookup"><span data-stu-id="b3b91-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Fase 2 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="b3b91-135">Fase 3: creare un computer con Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b3b91-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="b3b91-136">In questa fase, si crea un computer autonomo che esegue Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="b3b91-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="b3b91-137">Computer fisico</span><span class="sxs-lookup"><span data-stu-id="b3b91-137">Physical computer</span></span>

<span data-ttu-id="b3b91-p105">Ottenere un personal computer e installare Windows 10 Enterprise su di esso. È possibile scaricare il Windows 10 Enterprise versione di valutazione [di seguito](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="b3b91-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="b3b91-140">Macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="b3b91-140">Virtual machine</span></span>

<span data-ttu-id="b3b91-p106">Creare una macchina virtuale utilizzando hypervisor desiderato e installare Windows 10 Enterprise su di esso. È possibile scaricare il Windows 10 Enterprise versione di valutazione [di seguito](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="b3b91-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="b3b91-143">Macchina virtuale in Azure</span><span class="sxs-lookup"><span data-stu-id="b3b91-143">Virtual machine in Azure</span></span>

<span data-ttu-id="b3b91-p107">Per creare una macchina virtuale Windows 10 in Microsoft Azure, ***è necessario disporre di una sottoscrizione di Visual Studio***, che dispone dell'accesso per l'immagine per Windows 10 Enterprise. Altri tipi di sottoscrizioni di Azure, ad esempio le sottoscrizioni di valutazione e a pagamento, non hanno accesso all'immagine.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b3b91-p108">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Compilazione di set di una macchina virtuale Windows 10 Enterprise questi comandi denominati WIN10 e tutti i relativi infrastruttura necessaria, tra cui un gruppo di risorse, un account di archiviazione e una rete virtuale. Se si ha già familiarità con i servizi di infrastruttura, adattare queste istruzioni per l'infrastruttura appropriata.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="b3b91-150">Innanzitutto, avviare un prompt di Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3b91-150">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="b3b91-151">Accedere al proprio account Azure con il seguente comando.</span><span class="sxs-lookup"><span data-stu-id="b3b91-151">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="b3b91-152">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="b3b91-152">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="b3b91-p109">Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p109">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="b3b91-p110">Quindi, creare un nuovo gruppo di risorse. Per definire un nome del gruppo di risorse univoco, utilizzare questo comando per creare un elenco di gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="b3b91-p111">Creare il nuovo gruppo di risorse con questi comandi. Sostituire tutte le virgolette, incluse le \< e > caratteri con i nomi corretti.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p111">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="b3b91-p112">Successivamente, creare una nuova rete virtuale e la macchina virtuale con WIN10 con questi comandi. Quando richiesto, fornire il nome e la password dell'account Administrator locale per WIN10 e archiviare questi elementi in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="b3b91-161">Fase 4: aggiungere il proprio computer con Windows 10 ad Azure AD</span><span class="sxs-lookup"><span data-stu-id="b3b91-161">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="b3b91-162">Dopo aver creata la macchina virtuale con Windows 10 Enterprise o computer fisici, accedere con un account amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="b3b91-162">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b3b91-p113">Per una macchina virtuale in Azure, eseguire la connessione con [le relative istruzioni](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Accedere con le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="b3b91-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="b3b91-165">Successivamente, aggiungere il computer WIN10 al tenant di Azure AD delle sottoscrizioni di Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="b3b91-165">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="b3b91-166">Il desktop del computer WIN10, fare clic su **Start > Impostazioni > account > accesso ufficio o scuola > Connetti**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-166">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="b3b91-167">Nella finestra di dialogo **Configura un account di lavoro o della scuola** , fare clic su **Partecipa alla periferica di Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-167">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="b3b91-168">In **lavoro o scuola account**, digitare il nome dell'account amministratore globale della sottoscrizione a Office 365 e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-168">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="b3b91-169">Nella casella **Immettere la password**, digitare la password per l'account amministratore globale e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-169">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="b3b91-170">Quando richiesto per assicurarsi che si tratta dell'organizzazione, fare clic su **Partecipa**e quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-170">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="b3b91-171">Chiudere la finestra delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="b3b91-171">Close the settings window.</span></span>
    
<span data-ttu-id="b3b91-172">Installare quindi 2016 Office nel computer WIN10.</span><span class="sxs-lookup"><span data-stu-id="b3b91-172">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="b3b91-p114">Aprire il browser Microsoft Edge e accedere al portale di Office 365 con le credenziali dell'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="b3b91-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="b3b91-175">Nella scheda **Microsoft Office Home**, fare clic su **Installa Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-175">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="b3b91-176">Quando richiesto con operazioni da eseguire, fare clic su **Esegui**e quindi fare clic su **Sì** per il **Controllo dell'Account utente**.</span><span class="sxs-lookup"><span data-stu-id="b3b91-176">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="b3b91-p115">Attendere di Office completare l'installazione. Quando viene visualizzato **sei tutte impostate!**, fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="b3b91-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="b3b91-179">La Figura 3 mostra l'ambiente risultante, che include il computer WIN10 aggiunto al tenant di Azure AD delle sottoscrizioni di Office 365 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="b3b91-179">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="b3b91-180">**Figura 3: Aggiungere l'account del computer WIN10 al tenant Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="b3b91-180">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Fase 4 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="b3b91-182">A questo punto si è pronti acquisire familiarità con le funzionalità aggiuntive di [365 Microsoft Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="b3b91-182">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="b3b91-183">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b3b91-183">Next steps</span></span>

<span data-ttu-id="b3b91-184">Utilizzare questi articoli aggiuntivi per esplorare le funzionalità di Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="b3b91-184">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="b3b91-185">Aggiungere criteri di gestione (MAM) applicazione per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="b3b91-185">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="b3b91-186">Registrare iOS e dispositivi Android</span><span class="sxs-lookup"><span data-stu-id="b3b91-186">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="b3b91-187">Configurare e gestire la sicurezza avanzata di test</span><span class="sxs-lookup"><span data-stu-id="b3b91-187">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="b3b91-188">Configurare e testare avanzate Threat Protection</span><span class="sxs-lookup"><span data-stu-id="b3b91-188">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="b3b91-189">Concetti</span><span class="sxs-lookup"><span data-stu-id="b3b91-189">See Also</span></span>

- [<span data-ttu-id="b3b91-190">Documentazione Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b3b91-190">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- [<span data-ttu-id="b3b91-191">Distribuire Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b3b91-191">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [<span data-ttu-id="b3b91-192">L'ambiente di sviluppo e di testing uno Cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="b3b91-192">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="b3b91-193">Test Lab Guide (TLG) di adozione cloud </span><span class="sxs-lookup"><span data-stu-id="b3b91-193">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
