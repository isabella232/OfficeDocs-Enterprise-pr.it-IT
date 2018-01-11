---
title: Ambiente di sviluppo/test della configurazione di base
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Riepilogo: Creare una rete intranet semplificata come un ambiente di sviluppo e di testing in Microsoft Azure.'
ms.openlocfilehash: f61490ea9ee9ee23df2b2fd13df1097d183a8de7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2018
---
# <a name="base-configuration-devtest-environment"></a>Ambiente di sviluppo/test della configurazione di base

 **Riepilogo:** Creare una rete intranet semplificata come un ambiente di sviluppo e di testing in Microsoft Azure.
  
In questo articolo vengono fornite istruzioni dettagliate per creare il seguente ambiente di sviluppo/test della configurazione di base in Azure:
  
**Nella figura 1: Configurazione di Base dev/ambiente di testing**

![Fase 4 della configurazione base in Azure con la macchina virtuale CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
L'ambiente di sviluppo/test della configurazione di base nella figura 1 è costituito dalla subnet Corpnet in una rete virtuale di Azure basata solo su cloud denominata TestLab, che simula una intranet privata semplificata connessa a Internet. Contiene tre macchine virtuali Azure che eseguono Windows Server 2016:
  
- DC1 è configurato come un controller di dominio intranet e server Domain Name System (DNS)
    
- APP1 è configurato come un’applicazione generale e server Web
    
- 	CLIENT1 agisce come client intranet
    
Questa configurazione consente a DC1 APP1, CLIENT1 e altri computer subnet Corpnet di essere:  
  
- Connessione a Internet per installare gli aggiornamenti, accedere alle risorse Internet in tempo reale e partecipare alle tecnologie di cloud pubblici, ad esempio Microsoft Office 365 e altri servizi di Azure.
    
- 	Gestiti in remoto tramite connessioni da desktop remoto dal proprio computer connesso a Internet o alla rete dell'organizzazione.
    
È possibile utilizzare l'ambiente di test risultante:
  
- Per lo sviluppo di applicazioni e test.
    
- Come la configurazione iniziale di un ambiente di test esteso del progetto che include macchine virtuali aggiuntive, servizi di Azure o altre offerte cloud Microsoft, ad esempio Office 365 e la sicurezza aziendale + dispositivi mobili.
    
Esistono quattro fasi per configurare l'ambiente di testing di configurazione di base in Azure:
  
1. 	Creare la rete virtuale.
    
2. 	Configurare DC1.
    
3. 	Configurare APP1.
    
4. 	Configurare CLIENT1.
    
Se non si dispone già di una sottoscrizione di Azure, è possibile iscriversi per una versione di valutazione gratuita a [Provare Azure](https://azure.microsoft.com/pricing/free-trial/). Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [credito Azure mensile per i sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
> [!NOTE]
> Macchine virtuali di Azure comportano un costo corso quando sono in esecuzione. Il costo calcolato rispetto all'abbonamento MSDN prova, gratuito o sottoscrizione a pagamento. Per ulteriori informazioni sui costi delle macchine virtuali Azure, vedere [Informazioni sul prezzo macchine virtuali](https://azure.microsoft.com/pricing/details/virtual-machines/) e [Azure prezzi calcolatrice](https://azure.microsoft.com/pricing/calculator/). Per mantenere i costi verso il basso, vedere [ridurre al minimo i costi delle macchine virtuali ambiente di testing in Azure](base-configuration-dev-test-environment.md#mincost). 
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-create-the-virtual-network"></a>Fase 1: Creare la rete virtuale

Per prima cosa, avviare un prompt di Azure PowerShell.
  
> [!NOTE]
> Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Accedere al proprio account Azure con il seguente comando.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) per ottenere un file di testo che contiene tutti i comandi di PowerShell in questo articolo.
  
Ottenere il nome della sottoscrizione utilizzando il comando seguente.
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Impostare la sottoscrizione di Azure. Sostituire tutto il testo racchiuso tra virgolette, compresi i caratteri < e >, con il nome corretto.
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

In seguito, creare un nuovo gruppo di risorse per il lab di test di configurazione di base. Per determinare un nome del gruppo di risorse univoco, utilizzare questo comando per creare un elenco dei gruppi di risorse esistenti.
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Creare il nuovo gruppo di risorse con questi comandi. Sostituire tutto il testo racchiuso tra virgolette, compresi i caratteri < e >, con i nomi corretti.
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

Successivamente, è possibile creare la rete virtuale TestLab che ospiterà la subnet Corpnet della configurazione di base, proteggendola con un gruppo di sicurezza di rete.
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

Questa è la configurazione corrente.
  
![Fase 1 della configurazione base in Azure con la rete virtuale e subnet](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>Fase 2: Configurare DC1

Nella fase successiva verrà creata la macchina virtuale DC1 e verrà configurata come controller di dominio per il dominio di Windows Server Active Directory (AD) corp.contoso.com e un server DNS per le macchine virtuali della rete virtuale TestLab.
  
Per creare una macchina virtuale Azure per DC1, immettere il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Verrà richiesto nome utente e password dell'account Administrator locale su DC1. Utilizzare una password complessa e annotare nome e password in una posizione sicura.
  
Eseguire quindi la connessione alla macchina virtuale DC1.
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>Connettersi a DC1 usando le credenziali dell'account Administrator locale

1. Nel [portale di Azure](https://portal.azure.com), fare clic su **gruppi di risorse >** <the name of your new resource group> **> DC1 > Connetti**.
    
2. Aprire il file DC1.rdp che può essere scaricato e quindi fare clic su **Connetti**.
    
3. Specificare il nome dell'account amministratore locale DC1:
    
  - Per Windows 7:
    
    Nella finestra di dialogo **Protezione di Windows** , fare clic su **utilizza un altro account**. In **nome utente**digitare **DC1\\**[nome dell'account amministratore locale].
    
  - Per Windows 8 o Windows 10:
    
    Nella finestra di dialogo **Protezione di Windows** , fare clic su **ulteriori opzioni**e quindi fare clic su **Usa un account diverso**. In **nome utente**digitare **DC1\\**[nome dell'account amministratore locale].
    
4. Nella casella **Password**digitare la password dell'account di amministratore locale e quindi fare clic su **OK**.
    
5. Quando richiesto, fare clic su **Sì**.
    
Aggiungere un ulteriore disco dati come nuovo volume con lettera di unità F: immettendo questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore in DC1.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Configurare quindi DC1 come controller di dominio e il server DNS per il dominio corp.contoso.com. Eseguire questi comandi al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

Sarà necessario specificare una password di amministratore in modalità provvisoria. Archiviare la password in un percorso sicuro.
  
Si tenga presente che il completamento di questi comandi potrebbe richiedere alcuni minuti.
  
Dopo il riavvio di DC1, riconnettersi al computer virtuale DC1.
  
### <a name="connect-to-dc1-using-domain-credentials"></a>Connettersi a DC1 usando le credenziali di dominio

1. Nel [portale di Azure](https://portal.azure.com), fare clic su **gruppi di risorse >** <your resource group name> **> DC1 > Connetti**.
    
2. Eseguire il file DC1.rdp che può essere scaricato e quindi fare clic su **Connetti**.
    
3. **Protezione di Windows**, fare clic su **utilizza un altro account**. In **nome utente**digitare **CORP\\**[nome dell'account amministratore locale].
    
4. Nella casella **Password**digitare la password dell'account di amministratore locale e quindi fare clic su **OK**.
    
5. Quando richiesto, fare clic su **Sì**.
    
Successivamente, creare un account utente in Active Directory che verrà utilizzato quando si accede a computer membri del dominio CORP. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Tenere presente che questo comando chiede di specificare la password dell'account User1. Poiché questo account verrà utilizzato per le connessioni desktop remote per tutti i computer membri del dominio CORP, scegliere una password complessa. Registrare la password dell'account User1 e archiviarla in una posizione sicura.
  
Configurare quindi il nuovo account User1 come amministratore dell'organizzazione. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

Chiudere la sessione di Desktop remoto con DC1 e quindi riconnettersi utilizzando il CORP\\account User1.
  
Successivamente, per consentire il traffico per lo strumento Ping, eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Questa è la configurazione corrente.
  
![Fase 2 della configurazione base in Azure con la macchina virtuale DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>Fase 3: Configurare APP1

APP1 fornisce servizi Web e di condivisione file.
  
Per creare una macchina virtuale Azure per APP1, inserire il nome del gruppo di risorse, la posizione di Azure e il nome dell’account di archiviazione, quindi eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Successivamente, connettersi alla macchina virtuale APP1 usando il nome e la password dell'account Administrator locale di APP1, quindi aprire un prompt dei comandi di Windows PowerShell.
  
Per verificare la comunicazione nome di soluzione e di rete tra APP1 e DC1, eseguire il comando **ping dc1.corp.contoso.com** e verificare che non vi sono quattro risposte.
  
Unire quindi la macchina virtuale APP1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Si noti che è necessario fornire il CORP\\le credenziali dell'account di dominio User1 dopo aver eseguito il comando **Aggiungi Computer** .
  
Dopo il riavvio di APP1, connettersi tramite il CORP\\account User1 e aprire un livello di amministratore di Windows PowerShell Prompt dei comandi.
  
Successivamente, modificare APP1 in server Web con questo comando al prompt dei comandi di Windows PowerShell in APP1.
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Creare quindi una cartella condivisa e un file di testo all'interno della cartella in APP1 con i comandi di PowerShell.
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

Questa è la configurazione corrente.
  
![Fase 3 della configurazione base in Azure con la macchina virtuale APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>Fase 4: Configurare CLIENT1

CLIENT1 agisce come un portatile, tablet o computer desktop tipico sulla intranet Contoso.
  
> [!NOTE]
> Il set di comando seguente consente di creare CLIENT1 che esegue Windows Server 2016 Datacenter, che può essere eseguita per tutti i tipi di sottoscrizioni di Azure. Se si dispone di una sottoscrizione di Azure basate su Visual Studio, è possibile creare CLIENT1 in esecuzione Windows 10, Windows 8 o Windows 7 con il [portale di Azure](https://portal.azure.com). 
  
Per creare una macchina virtuale Azure per CLIENT1, inserire il nome del gruppo di risorse, la posizione di Azure e il nome dell’account di archiviazione, quindi eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale.
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Successivamente, connettersi alla macchina virtuale CLIENT1 usando il nome e la password dell'account Administrator locale di CLIENT1, quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.
  
Per verificare la comunicazione nome di soluzione e di rete tra CLIENT1 e DC1, al prompt dei comandi di Windows PowerShell eseguire il comando **ping dc1.corp.contoso.com** e verificare che non vi sono quattro risposte.
  
Unire quindi la macchina virtuale CLIENT1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

Si noti che è necessario fornire il CORP\\le credenziali dell'account di dominio User1 dopo aver eseguito il comando **Aggiungi Computer** .
  
Dopo il riavvio del CLIENT1, connettersi tramite il CORP\\User1 nome dell'account e password e quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.
  
Successivamente, verificare che sia possibile accedere alle risorse Web e di condivisione file in APP1 da CLIENT1.
  
### <a name="verify-client-access-to-app1"></a>Verificare l'accesso CLIENT ad APP1

1. In Server Manager, nel riquadro dell'albero, fare clic su **Server locale**.
    
2. Nelle **proprietà di CLIENT1**, fare clic **su** Avanti per **La protezione avanzata di Internet Explorer**.
    
3. **Protezione avanzata di Internet Explorer**, fare clic su **Disattiva** per **amministratori** e **utenti**e quindi fare clic su **OK**.
    
4. Nella schermata Start, fare clic su **Internet Explorer**e quindi fare clic su **OK**.
    
5. Nella barra degli indirizzi digitare **http://app1.corp.contoso.com/**e quindi premere INVIO. È consigliabile vedere la pagina web di Internet Information Services predefinita per APP1.
    
6. Dalla barra delle applicazioni del desktop, fare clic sull'icona Esplora File.
    
7. Nella barra degli indirizzi digitare ** \\ \\app1\\file**, e quindi premere INVIO. Verrà visualizzata una finestra della cartella con il contenuto della cartella condivisa.
    
8. Nella finestra della cartella condivisa **i file** , fare doppio clic sul file di **esempio. txt** . È consigliabile visualizzare il contenuto del file di esempio. txt.
    
9. Chiudere l' **esempio. txt - il blocco note** e le finestre della cartella **file** condivisi.
    
Questa è la configurazione finale.
  
![Fase 4 della configurazione base in Azure con la macchina virtuale CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
La configurazione di Base in Azure è pronta per lo sviluppo di applicazioni e i test o per la creazione di ambienti di testing aggiuntivi. 
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Ridurre al minimo i costi delle macchine virtuali nell’ambiente di testing in Azure
<a name="mincost"> </a>

Per ridurre al minimo i costi dell'esecuzione di macchine virtuali in ambiente di testing, è possibile eseguire una delle operazioni seguenti:
  
- Creare l'ambiente di testing ed effettuare il test e la dimostrazione necessari al più presto possibile. Al termine, eliminare il gruppo di risorse per l'ambiente di testing.
    
- 	Arrestare le macchine virtuali nell’ambiente di testing in uno stato deallocato.
    
Per arrestare le macchine virtuali con Azure PowerShell, immettere il nome del gruppo di risorse ed eseguire questi comandi.
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

Per verificare il corretto funzionamento delle macchine virtuali al loro avvio dallo stato Arrestato (Deallocato), è necessario avviarle nell'ordine seguente:
  
1. DC1
    
2. APP1
    
3. CLIENT1
    
Per avviare le macchine virtuali con Azure PowerShell, immettere il nome del gruppo di risorse ed eseguire questi comandi.
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>Vedere anche

<a name="mincost"> </a>

[Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
  
[DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
  
[Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


