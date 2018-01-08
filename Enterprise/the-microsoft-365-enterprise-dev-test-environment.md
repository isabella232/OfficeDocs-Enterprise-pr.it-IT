---
title: Ambiente di sviluppo e di testing di Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
- Strat_O365_Enterprise
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: "Riepilogo: Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che include Office 365 E5, mobilità aziendale + E5 di sicurezza (EMS) e un computer che esegue Windows 10 Enterprise."
ms.openlocfilehash: 547662a21733941e3242e9cdd933090a4f53714d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="e9117-103">Ambiente di sviluppo e di testing di Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e9117-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="e9117-104">**Riepilogo:** Utilizzare questa guida dei laboratori di testing per creare un ambiente di sviluppo e di testing che include Office 365 E5, mobilità aziendale + E5 di sicurezza (EMS) e un computer che esegue Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e9117-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="e9117-105">In questo articolo vengono fornite istruzioni dettagliate per creare un ambiente semplificato per testare le funzionalità di [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="e9117-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="e9117-106">Fase 1: creare la sottoscrizione di Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="e9117-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="e9117-107">Seguire i passaggi della fase 2 e la fase 3 [dell'ambiente di sviluppo e di testing di Office 365](office-365-dev-test-environment.md) per creare un ambiente di sviluppo e di testing lightweight Office 365, come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="e9117-107">Follow the steps in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="e9117-108">**Nella figura 1: La sottoscrizione di Office 365 E5 con il relativo account utente e tenant di Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="e9117-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Fase 1 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="e9117-110">Fase 2: aggiungere EMS</span><span class="sxs-lookup"><span data-stu-id="e9117-110">Phase 2: Add EMS</span></span>

<span data-ttu-id="e9117-111">In questa fase, è possibile iscriversi per la sottoscrizione di valutazione di EMS E5 e aggiungerla alla stessa organizzazione della sottoscrizione di valutazione di Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="e9117-111">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="e9117-112">Innanzitutto, aggiungere la sottoscrizione di prova EMS E5 e assegna una licenza EMS all'account amministratore globale.</span><span class="sxs-lookup"><span data-stu-id="e9117-112">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="e9117-p101">Con un'istanza privata di un browser, accedere al portale di Office 365 con le credenziali dell'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e9117-p101">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e9117-115">Fare clic sul riquadro **Amministratore**.</span><span class="sxs-lookup"><span data-stu-id="e9117-115">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e9117-116">Scheda di **interfaccia di amministrazione di Office** nel browser, nel riquadro di spostamento sinistra fare clic su **fatturazione > servizi di acquisto**.</span><span class="sxs-lookup"><span data-stu-id="e9117-116">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e9117-p102">Nella pagina **servizi di acquisto** individuare l'elemento di **sicurezza E5 + mobilità aziendale** . Posizionare il puntatore del mouse su di esso e fare clic su **Start versione di valutazione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="e9117-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e9117-119">Nella pagina **Conferma l'ordine**, fare clic su **Prova adesso**.</span><span class="sxs-lookup"><span data-stu-id="e9117-119">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e9117-120">Nella pagina **Ricevuta ordine**, fare clic su **Continua**.</span><span class="sxs-lookup"><span data-stu-id="e9117-120">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="e9117-121">Nella scheda **Centro di amministrazione di Office 365** nel browser, nel riquadro di spostamento sinistra fare clic su **utenti > utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="e9117-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="e9117-122">Fare clic sull'account di amministratore globale e quindi fare clic su **Modifica** per **le licenze del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="e9117-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="e9117-123">Nel riquadro di **licenze per i prodotti** , attivare la licenza del prodotto per la **mobilità aziendale + E5 di sicurezza** per **in**, fare clic su **Salva** e quindi fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="e9117-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e9117-p103">La sottoscrizione di valutazione Enterprise Mobility + Security E5 è valida per 90 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze.</span><span class="sxs-lookup"><span data-stu-id="e9117-p103">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="e9117-126">***Se sono state completate fase 3 del*** [Ambiente di sviluppo e di testing di office 365](office-365-dev-test-environment.md) , ripetere i passaggi 8 e 9 della procedura precedente per tutti gli altri account (utente 2, 3 utente, utente 4 e 5 utente).</span><span class="sxs-lookup"><span data-stu-id="e9117-126">***If you completed Phase 3 of*** [Office 365 dev/test environment](office-365-dev-test-environment.md) , repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="e9117-127">A questo punto, l'ambiente di sviluppo/di testing dispone di:</span><span class="sxs-lookup"><span data-stu-id="e9117-127">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="e9117-128">Sottoscrizioni di valutazione di Office 365 E5 Enterprise ed EMS che condividono la stessa organizzazione e lo stesso tenant di Azure AD con l'elenco di account utente in uso.</span><span class="sxs-lookup"><span data-stu-id="e9117-128">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="e9117-129">Tutti gli account utente appropriati (solo l'amministratore globale o tutti gli account utente cinque) sono abilitati all'utilizzo di Office 365 E5 ed EMS E5.</span><span class="sxs-lookup"><span data-stu-id="e9117-129">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="e9117-130">La figura 2 mostra la configurazione risultante che consente di aggiungere EMS.</span><span class="sxs-lookup"><span data-stu-id="e9117-130">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="e9117-131">**Figura 2: Aggiunta di sottoscrizione di prova EMS**</span><span class="sxs-lookup"><span data-stu-id="e9117-131">**Figure 2: Adding the EMS trial subscription**</span></span>

![Fase 2 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="e9117-133">Fase 3: creare un computer con Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e9117-133">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="e9117-134">In questa fase, si crea un computer autonomo che esegue Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e9117-134">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="e9117-135">Computer fisico</span><span class="sxs-lookup"><span data-stu-id="e9117-135">Physical computer</span></span>

<span data-ttu-id="e9117-p104">Ottenere un personal computer e installare Windows 10 Enterprise su di esso. È possibile scaricare il Windows 10 Enterprise versione di valutazione [di seguito](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="e9117-p104">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="e9117-138">Macchina virtuale</span><span class="sxs-lookup"><span data-stu-id="e9117-138">Virtual machine</span></span>

<span data-ttu-id="e9117-p105">Creare una macchina virtuale utilizzando hypervisor desiderato e installare Windows 10 Enterprise su di esso. È possibile scaricare il Windows 10 Enterprise versione di valutazione [di seguito](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="e9117-p105">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="e9117-141">Macchina virtuale in Azure</span><span class="sxs-lookup"><span data-stu-id="e9117-141">Virtual machine in Azure</span></span>

<span data-ttu-id="e9117-p106">Per creare una macchina virtuale Windows 10 in Microsoft Azure, ***è necessario disporre di una sottoscrizione di Visual Studio***, che dispone dell'accesso per l'immagine per Windows 10 Enterprise. Altri tipi di sottoscrizioni di Azure, ad esempio le sottoscrizioni di valutazione e a pagamento, non hanno accesso all'immagine.</span><span class="sxs-lookup"><span data-stu-id="e9117-p106">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e9117-p107">I seguenti insiemi di comando utilizzano te versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Compilazione di set di una macchina virtuale Windows 10 Enterprise questi comandi denominati WIN10 e tutti i relativi infrastruttura necessaria, tra cui un gruppo di risorse, un account di archiviazione e una rete virtuale. Se si ha già familiarità con i servizi di infrastruttura, adattare queste istruzioni per l'infrastruttura appropriata.</span><span class="sxs-lookup"><span data-stu-id="e9117-p107">The following command sets use te latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="e9117-148">Innanzitutto, avviare un prompt di Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9117-148">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="e9117-149">Accedere al proprio account Azure con il seguente comando.</span><span class="sxs-lookup"><span data-stu-id="e9117-149">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="e9117-150">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="e9117-150">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="e9117-p108">Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="e9117-p108">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="e9117-p109">Quindi, creare un nuovo gruppo di risorse. Per definire un nome del gruppo di risorse univoco, utilizzare questo comando per creare un elenco di gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="e9117-p109">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="e9117-p110">Creare il nuovo gruppo di risorse con questi comandi. Sostituire tutte le virgolette, incluse le \< e > caratteri con i nomi corretti.</span><span class="sxs-lookup"><span data-stu-id="e9117-p110">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="e9117-p111">Macchine virtuali in base a Gestione risorse richiedono un account di archiviazione basate su Manager delle risorse. È necessario scegliere un nome univoco a livello globale per l'account di archiviazione *che contiene solo numeri e lettere minuscole* . È possibile utilizzare questo comando per elencare gli account di archiviazione esistente.</span><span class="sxs-lookup"><span data-stu-id="e9117-p111">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account  *that contains only lowercase letters and numbers*  . You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort StorageAccountName | Select StorageAccountName
```

<span data-ttu-id="e9117-160">Utilizzare questo comando per verificare se un nome dell'account di archiviazione proposto è univoco.</span><span class="sxs-lookup"><span data-stu-id="e9117-160">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="e9117-161">Creare un nuovo account di archiviazione per il nuovo ambiente di testing con questi comandi.</span><span class="sxs-lookup"><span data-stu-id="e9117-161">Create a new storage account for your new test environment with these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$saName="<storage account name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="e9117-p112">Successivamente, creare una nuova rete virtuale e la macchina virtuale con WIN10 con questi comandi. Quando richiesto, fornire il nome e la password dell'account Administrator locale per WIN10 e archiviare questi elementi in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="e9117-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
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
$storageAcc=Get-AzureRMStorageAccount -ResourceGroupName $rgName -Name $saName
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftVisualStudio -Offer Windows -Skus Windows-10-N-x64 -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$osDiskUri=$storageAcc.PrimaryEndpoints.Blob.ToString() + "vhds/WIN10-TestLab-OSDisk.vhd"
$vm=Set-AzureRMVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -VhdUri $osDiskUri -CreateOption fromImage
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="e9117-164">Fase 4: aggiungere il proprio computer con Windows 10 ad Azure AD</span><span class="sxs-lookup"><span data-stu-id="e9117-164">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="e9117-165">Dopo che la macchina virtuale o fisica è stata creata, configurata con Windows 10 Enterprise ed è in esecuzione, accedere con un account Administrator locale.</span><span class="sxs-lookup"><span data-stu-id="e9117-165">After the physical or virtual machine is created, configured with Windows 10 Enterprise, and is running, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e9117-p113">Per una macchina virtuale in Azure, eseguire la connessione con [le relative istruzioni](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Accedere con le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="e9117-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="e9117-168">Successivamente, aggiungere il computer WIN10 al tenant di Azure AD delle sottoscrizioni di Office 365 e EMS.</span><span class="sxs-lookup"><span data-stu-id="e9117-168">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="e9117-169">Il desktop del computer WIN10, fare clic su **Start > Impostazioni > account > accesso ufficio o scuola > Connetti**.</span><span class="sxs-lookup"><span data-stu-id="e9117-169">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="e9117-170">Nella finestra di dialogo **Configura un account di lavoro o della scuola** , fare clic su **Partecipa alla periferica di Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="e9117-170">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="e9117-171">In **lavoro o scuola account**, digitare il nome dell'account amministratore globale della sottoscrizione a Office 365 e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e9117-171">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="e9117-172">Nella casella **Immettere la password**, digitare la password per l'account amministratore globale e quindi fare clic su **Accedi**.</span><span class="sxs-lookup"><span data-stu-id="e9117-172">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="e9117-173">Quando richiesto per assicurarsi che si tratta dell'organizzazione, fare clic su **Partecipa**e quindi fare clic su **Fine**.</span><span class="sxs-lookup"><span data-stu-id="e9117-173">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="e9117-174">Chiudere la finestra delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="e9117-174">Close the settings window.</span></span>
    
<span data-ttu-id="e9117-175">Successivamente, installare Office 2016 nel computer WIN10</span><span class="sxs-lookup"><span data-stu-id="e9117-175">Next, install Office 2016 on the WIN10 computer</span></span>
  
1. <span data-ttu-id="e9117-p114">Aprire il browser Microsoft Edge e accedere al portale di Office 365 con le credenziali dell'account amministratore globale. Per ulteriori informazioni, vedere [la posizione in cui eseguire l'accesso a Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e9117-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e9117-178">Nella scheda **Microsoft Office Home**, fare clic su **Installa Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="e9117-178">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="e9117-179">Quando richiesto con operazioni da eseguire, fare clic su **Esegui**e quindi fare clic su **Sì** per il **Controllo dell'Account utente**.</span><span class="sxs-lookup"><span data-stu-id="e9117-179">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="e9117-p115">Attendere di Office completare l'installazione. Quando viene visualizzato **sei tutte impostate!**, fare doppio clic su **Chiudi** .</span><span class="sxs-lookup"><span data-stu-id="e9117-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="e9117-182">La Figura 3 mostra l'ambiente risultante, che include il computer WIN10 aggiunto al tenant di Azure AD delle sottoscrizioni di Office 365 ed EMS.</span><span class="sxs-lookup"><span data-stu-id="e9117-182">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="e9117-183">**Figura 3: Aggiungere l'account del computer WIN10 al tenant Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="e9117-183">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Fase 4 dell’ambiente di sviluppo/test Microsoft 3656 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="e9117-185">A questo punto si è pronti acquisire familiarità con le funzionalità aggiuntive di [365 Microsoft Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="e9117-185">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="e9117-186">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="e9117-186">Next steps</span></span>

<span data-ttu-id="e9117-187">Utilizzare questi articoli aggiuntivi per esplorare le funzionalità di Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="e9117-187">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="e9117-188">Aggiungere criteri di gestione (MAM) applicazione per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="e9117-188">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="e9117-189">Registrare iOS e dispositivi Android</span><span class="sxs-lookup"><span data-stu-id="e9117-189">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="e9117-190">Configurare e gestire la sicurezza avanzata di test</span><span class="sxs-lookup"><span data-stu-id="e9117-190">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="e9117-191">Configurare e testare avanzate Threat Protection</span><span class="sxs-lookup"><span data-stu-id="e9117-191">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="e9117-192">See Also</span><span class="sxs-lookup"><span data-stu-id="e9117-192">See Also</span></span>

[<span data-ttu-id="e9117-193">L'ambiente di sviluppo e di testing uno Cloud Microsoft</span><span class="sxs-lookup"><span data-stu-id="e9117-193">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)

[<span data-ttu-id="e9117-194">Documentazione Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="e9117-194">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)



