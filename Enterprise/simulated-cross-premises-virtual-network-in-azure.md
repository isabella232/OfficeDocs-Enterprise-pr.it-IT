---
title: Rete virtuale tra più sedi simulata in Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 'Riepilogo: Creare una rete virtuale simulato tra locali in Microsoft Azure come un ambiente di sviluppo e di testing.'
ms.openlocfilehash: 4a34126bba4561da621dc3faf37dd30d4dcc9ff3
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Rete virtuale tra più sedi simulata in Azure

 **Riepilogo:** Creare una rete virtuale simulato tra locali in Microsoft Azure come un ambiente di sviluppo e di testing.
  
In questo articolo viene mostrato come creare un ambiente basato su cloud con Microsoft Azure usando due reti virtuali Azure. Di seguito è riportata la configurazione risultante.   
  
![Fase 3 dell'ambiente di sviluppo/testing della rete virtuale cross-premise simulata, con la macchina virtuale DC2 nella rete virtuale XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Questa simula un ambiente di produzione cloud ibrido in IaaS di Azure ed è costituita da:
  
- 	Una rete locale simulata e semplificata, ospitata in una rete virtuale di Azure (la rete virtuale TestLab).
    
- 	Una rete virtuale cross-premise simulata ospitata in Azure (XPrem).
    
- 	Una relazione peering di rete virtuale tra le due reti virtuali.
    
- 	Un controller di dominio secondario nella rete virtuale XPrem.
    
Tale configurazione fornisce una base e un punto di partenza comune da cui è possibile:  
  
- 	Sviluppare e testare applicazioni in un ambiente cloud ibrido simulato in IaaS di Azure.
    
- 	Creare configurazioni di test dei computer, alcune all'interno della rete virtuale TestLab e alcune all'interno della rete virtuale XPrem, per simulare carichi di lavoro IT basati su cloud ibridi.
    
Le fasi principali della configurazione dell'ambiente di sviluppo e testing sono tre:
  
1. 	Configurare la rete virtuale TestLab.
    
2. Creare la rete virtuale cross-premise.
    
3. Configurare DC2.
    
> [!NOTE]
> Questa configurazione richiede una sottoscrizione a pagamento di Azure. 
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>Fase 1: Configurare la rete virtuale TestLab

Utilizzare le istruzioni [nell'ambiente di sviluppo/test di configurazione di Base](base-configuration-dev-test-environment.md) per configurare i computer DC1, APP1 e CLIENT1 nella rete virtuale Azure denominata laboratorio di test.
  
Questa è la configurazione corrente. 
  
![Fase 4 della configurazione base in Azure con la macchina virtuale CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Fase 2: Creare la rete virtuale XPrem

In questa fase, viene creata e configurata la nuova rete virtuale XPrem, viene quindi eseguita la connessione alla rete virtuale TestLab con peering di rete virtuale.
  
Innanzitutto, avviare un prompt dei comandi di Azure PowerShell sul computer locale.
  
> [!NOTE]
> [!NOTA] I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell. Vedere [Panoramica dei cmdlet di Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Accedere al proprio account Azure con il seguente comando.
  
```
Login-AzureRMAccount
```

> [!TIP]
> [!SUGGERIMENTO] Per un file di testo contenente tutti i comandi di PowerShell riportati in questo articolo, fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0).
  
Ottenere il nome della sottoscrizione utilizzando il comando seguente.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Impostare la sottoscrizione di Azure. Sostituire tutte le virgolette, incluse le \< e > caratteri con i nomi corretti.
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

Successivamente, creare la rete virtuale XPrem e proteggerla con un gruppo di sicurezza di rete con questi comandi.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

Creare quindi la relazione peering di rete virtuale tra le reti virtuali TestLab e XPrem con questi comandi.
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Questa è la configurazione corrente. 
  
![Fase 2 dell'ambiente di sviluppo/testing della rete virtuale cross-premise simulata, con la relazione di peering della rete virtuale e la rete virtuale XPrem](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Fase 3: Configurare DC2

In questa fase, viene creata la macchina virtuale DC2 nella rete virtuale XPrem e viene configurata come controller di dominio di replica.
  
Creare innanzitutto una macchina virtuale per DC2. Eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale.
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Collegare alla macchina virtuale DC2 nuova dal [portale di Azure](https://portal.azure.com) utilizzando il nome dell'account amministratore locale e la password.
  
Configurare quindi una regola di Windows Firewall per consentire la verifica di connettività di base del traffico. Eseguire questi comandi in DC2 al prompt dei comandi di Windows PowerShell a livello di amministratore.  
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

Il comando ping dovrebbe produrre quattro risposte dall'indirizzo IP 10.0.0.4. Si tratta di un test del traffico attraverso la relazione peering di rete virtuale.  
  
Successivamente, aggiungere un ulteriore disco dati come nuovo volume con lettera di unità F: con questo comando in DC2 al prompt dei comandi di Windows PowerShell.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Configurare quindi DC2 come controller di dominio di replica per il dominio corp.contoso.com. Eseguire questi comandi in DC2 al prompt dei comandi di Windows PowerShell:
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Si noti che viene richiesto di specificare sia il CORP\\User1 password e una password di ripristino servizi modalità (Directory) e il riavvio DC2. 
  
Ora che la rete virtuale XPrem dispone di un proprio server DNS (DC2), è necessario configurare la rete virtuale XPrem per utilizzarlo. Eseguire questi comandi nel computer locale al prompt dei comandi di Azure PowerShell.
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

Dal portale di Azure nel computer locale, la connessione a DC1 con la CORP\\credenziali User1. Per configurare il dominio in modo che gli utenti e computer utilizzano i controller di dominio locale per l'autenticazione, eseguire questi comandi dal prompt dei comandi di Windows PowerShell livello di amministratore in DC1.
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Questa è la configurazione corrente. 
  
![Fase 3 dell'ambiente di sviluppo/testing della rete virtuale cross-premise simulata, con la macchina virtuale DC2 nella rete virtuale XPrem](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
L’ambiente cloud ibrido di Azure simulato è ora pronto per eseguire test.
  
## <a name="next-step"></a>Passaggio successivo

Utilizzare l'ambiente di sviluppo e di testing per simulare una [farm di SharePoint Server 2016 intranet ospitate in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).
  
## <a name="see-also"></a>Vedere anche

[Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md)
  
[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


