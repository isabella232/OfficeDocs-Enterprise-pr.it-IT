---
title: Disponibilità elevata federati controller di dominio fase 2 configurare l'autenticazione
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "Riepilogo: Configurare il controller di dominio e il server di DirSync per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure."
ms.openlocfilehash: 80846025af82810f63087aafd1a3b3a1213212d1
ms.sourcegitcommit: a337ac253054f571a8304e18e426f74bcd385857
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>Fase 2 dell'autenticazione federata a disponibilità elevata: configurare i controller di dominio

 **Riepilogo:** Configurare il controller di dominio e il server di DirSync per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure.
  
In questa fase di distribuzione di disponibilità elevata per l'autenticazione federata di Office 365 nei servizi dell'infrastruttura di Azure, si configurano due controller di dominio e il server DirSync nella rete virtuale Azure. Le richieste Web client per l'autenticazione possono quindi essere autenticate nella rete virtuale di Azure, anziché inviare tale traffico di autenticazione tramite la connessione VPN da sito a sito alla rete locale.
  
> [!NOTE]
> In Active Directory Federation Services (AD FS) non è possibile utilizzare Azure Active Directory Domain Services al posto dei controller di dominio di Windows Server AD. 
  
È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 3: configurare i server ADFS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Creare le macchine virtuali dei controller di dominio in Azure

Innanzitutto, è necessario compilare la colonna **nome della macchina virtuale** di tabella M e modificare le dimensioni delle macchine virtuali in base alle esigenze nella colonna **dimensione minima** .
  
|**Elemento**|**Nome della macchina virtuale**|**Galleria**|**Tipo di archiviazione**|**Dimensione minima**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![](./images/Common_Images/TableLine.png)(primo controller di dominio, esempio DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![](./images/Common_Images/TableLine.png)(secondo controller di dominio, esempio DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![](./images/Common_Images/TableLine.png)(Server DirSync esempio DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![](./images/Common_Images/TableLine.png)(server di ADFS prima, esempio ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![](./images/Common_Images/TableLine.png)(secondo ADFS server esempio ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![](./images/Common_Images/TableLine.png)(prima applicazione server proxy web, esempio WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![](./images/Common_Images/TableLine.png)(seconda applicazione server proxy web, esempio WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
   
 **Tabella M - macchine virtuali per l'autenticazione federata la disponibilità elevata per Office 365 in Azure**
  
Per l'elenco completo delle dimensioni delle macchine virtuali, vedere [dimensioni per le macchine virtuali](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).
  
Il seguente blocco di comandi Azure PowerShell consente di creare le macchine virtuali per i controller di due dominio. Specificare i valori per le variabili, rimuovere il \< e > caratteri. Si noti che questo blocco di comandi Azure PowerShell utilizza valori dalle tabelle riportate di seguito:
  
- Tabella M, per le macchine virtuali
    
- Tabella R, per i gruppi di risorse
    
- Tabella V, per le impostazioni della rete virtuale
    
- Tabella S, per le subnet
    
- Tabella I, per gli indirizzi IP statici
    
- Tabella A, per i set di disponibilità
    
Richiamare una definite tabelle R, V, S, è possibile e A in [la disponibilità elevata federati autenticazione fase 1: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Una volta forniti tutti i valori corretti, eseguire il blocco risultante nel prompt di Azure PowerShell oppure in PowerShell Integrated Script Environment (ISE) nel computer locale.
  
> [!TIP]
> Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Dal momento che queste macchine virtuali sono relative a un'applicazione intranet, non vengono assegnati un indirizzo IP pubblico o un'etichetta nome di dominio DNS ed esposti a Internet. Tuttavia, ciò significa inoltre che non è possibile connettersi a tali dal portale di Azure. Quando si visualizzano le proprietà della macchina virtuale non è disponibile l'opzione **Connetti** . Utilizzare accessorio connessione Desktop remoto o un altro strumento di Desktop remoto per la connessione alla macchina virtuale con privata IP address o intranet nome DNS.
  
## <a name="configure-the-first-domain-controller"></a>Configurare il primo controller di dominio

Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del primo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.
  
Successivamente, aggiungere il disco dati aggiuntivi per il primo controller di dominio con il comando da un Windows PowerShell al prompt dei comandi **nella macchina virtuale prima di controller di dominio**:
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Quindi, verificare la connettività del primo controller di dominio nei percorsi della rete dell'organizzazione utilizzando il comando **ping** per eseguire il ping dei nomi e gli indirizzi IP delle risorse di rete dell'organizzazione.
  
Questa procedura assicura che la risoluzione dei nomi DNS funziona correttamente (che la macchina virtuale è configurata correttamente con i server DNS locali) e che possono essere inviati pacchetti da e verso la rete virtuale cross-premise. Se il test ha esito negativo, contattare il proprio reparto IT per risolvere i problemi relativi alla risoluzione del nome DNS e al recapito dei pacchetti.
  
Successivamente, dal prompt dei comandi di Windows PowerShell nel primo controller di dominio, eseguire i comandi seguenti:
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred
```

Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.
  
## <a name="configure-the-second-domain-controller"></a>Configurare il secondo controller di dominio

Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del secondo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.
  
È necessario aggiungere il disco dati aggiuntivi al secondo controller di dominio con il comando da un Windows PowerShell al prompt dei comandi **nella seconda macchina virtuale controller di dominio**:
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Quindi, eseguire i seguenti comandi:
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred

```

Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.
  
È necessario aggiornare i server DNS per la rete virtuale in modo che tale Azure assegna macchine virtuali gli indirizzi IP di due nuovi controller di dominio da utilizzare come server DNS. Compilare le variabili e quindi eseguire questi comandi dal prompt dei comandi di Windows PowerShell nel computer locale:
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

Si noti che i due controller di dominio vengono riavviati in modo che non siano configurati con i server DNS locali come server DNS. Trattandosi di due server DNS, sono stati configurati automaticamente con i server DNS locali come server d'inoltro quando sono stati promossi a controller di dominio.
  
Successivamente, è necessario creare un sito di replica di Active Directory per assicurarsi che i server della rete virtuale di Azure utilizzino i controller di dominio locali. Connettersi a uno dei due controller di dominio con un account di amministratore di dominio ed eseguire i comandi seguenti dal prompt dei comandi di Windows PowerShell a livello di amministratore:
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a>Configurare il server DirSync

Utilizzare il client desktop remoto desiderato e creare una connessione desktop remoto alla macchina virtuale server DirSync. Utilizzare il nome DNS o computer intranet e le credenziali dell'account di amministratore locale.
  
Successivamente, aggiungerlo al dominio di Windows Server AD appropriato con questi comandi nel prompt dei comandi di Windows PowerShell.
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.
  
**Fase 2: Controller di dominio e server DirSync per l'infrastruttura di autenticazione federativa la disponibilità elevata in Azure**

![Fase 2 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con controller di dominio](images/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>Passaggio successivo

Utilizzare [la disponibilità elevata federati autenticazione fase 3: configurare i server ADFS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) per continuare a configurare questo carico di lavoro.
  
## <a name="see-also"></a>Vedere anche

[Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)

[Identità federata per Office 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


