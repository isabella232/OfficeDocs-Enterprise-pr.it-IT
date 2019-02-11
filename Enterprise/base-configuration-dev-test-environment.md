---
title: Ambiente di sviluppo/test della configurazione di base
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Riepilogo: creare una intranet semplificata come ambiente di sviluppo e di testing in Microsoft Azure.'
ms.openlocfilehash: 71470a20586a0d1992cfafd35f213ec80286419b
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897379"
---
# <a name="base-configuration-devtest-environment"></a>Ambiente di sviluppo/test della configurazione di base

 **Riepilogo:** creare una intranet semplificata come ambiente di sviluppo e di testing in Microsoft Azure.
  
In questo articolo vengono fornite istruzioni per creare il seguente ambiente di sviluppo/test della configurazione di base in Azure:
  
![Configurazione di base in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
**Figura 1: ambiente di sviluppo/test della configurazione di base**

L'ambiente di sviluppo/test della configurazione di base nella figura 1 è costituito dalla subnet Corpnet in una rete virtuale di Azure basata solo su cloud denominata TestLab, che simula una intranet privata semplificata connessa a Internet. Contiene tre macchine virtuali Azure che eseguono Windows Server 2016:
  
- DC1 è configurato come un controller di dominio intranet e server Domain Name System (DNS)
    
- APP1 è configurato come un’applicazione generale e server Web
    
- CLIENT1 agisce come client intranet
    
Questa configurazione consente a DC1 APP1, CLIENT1 e altri computer subnet Corpnet di essere: 
  
- Connessi a Internet per installare gli aggiornamenti, accedere alle risorse Internet in tempo reale e partecipare alle tecnologie basate su cloud pubblico, come Microsoft Office 365 e altri servizi di Azure.
    
- Gestiti in remoto tramite connessioni da desktop remoto dal proprio computer connesso a Internet o alla rete dell'organizzazione.
    
È possibile utilizzare l'ambiente di test risultante:
  
- Per lo sviluppo di applicazioni e test.
    
- Come la configurazione iniziale di un ambiente di testing esteso del progetto che include altre macchine virtuali, servizi di Azure o altre offerte cloud Microsoft, ad esempio Office 365 e Enterprise Mobility + Security (EMS).
    
Esistono due metodi per la creazione di questo ambiente:

1. Un modello di Azure Resource Manager
2. Azure Powershell

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Metodo 1: creare una rete intranet simulata con un modello di Azure Resource Manager

Con questo metodo si utilizza un modello Azure Resource Manager (ARM) per creare la rete intranet simulata. I modelli ARM contengono tutte le istruzioni per creare e configurare l’infrastruttura di rete Azure e le macchine virtuali.

Prima di distribuire il modello, consultare la [pagina Leggimi del modello](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) e avere a disposizione le informazioni seguenti:

- Il nome dell’abbonamento di Azure. È necessario immettere l'etichetta nel campo **Abbonamento** della pagina **Distribuzione personalizzata**.
- Il nome del gruppo di risorse di Azure. È necessario immettere l'etichetta nel campo **Gruppo di risorse** della pagina **Distribuzione personalizzata**.
- Un prefisso etichetta DNS per gli URL degli indirizzi IP pubblici delle macchine virtuali. È necessario immettere l'etichetta nel campo **Prefisso etichetta DNS** della pagina **Distribuzione personalizzata**.

Dopo aver letto con le istruzioni, fare clic su **Distribuisci in Azure** nella [pagina Leggimi del modello](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) per iniziare.

>[!Note]
>La rete intranet simulata creata dal modello ARM richiede una sottoscrizione a pagamento ad Azure.
>

Ecco la configurazione una volta completato il modello.

![Configurazione di base in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Metodo 2: creare la rete intranet simulata con Azure PowerShell

Con questo metodo si utilizza Windows PowerShell e il modulo di Azure PowerShell per creare l'infrastruttura di rete, le macchine virtuali e la loro configurazione.

Utilizzare questo metodo per acquisire esperienza nella creazione di elementi dell'infrastruttura di Azure un blocco comandi alla volta con PowerShell. È quindi possibile personalizzare i blocchi di comandi di PowerShell per una distribuzione personalizzata delle altre macchine virtuali in Azure.

Esistono quattro passaggi per configurare l'ambiente di testing di configurazione di base con Azure PowerShell:
  
1. Creare la rete virtuale.
    
2. Configurare DC1.
    
3. Configurare APP1.
    
4. Configurare CLIENT1.
    
Se non si dispone già di un abbonamento Azure, è possibile iscriversi per una versione di valutazione gratuita nella pagina [Crea subito il tuo account Azure gratuito](https://azure.microsoft.com/pricing/free-trial/). Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [Credito Azure mensile per sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
> [!NOTE]
> Le macchine virtuali di Azure in esecuzione comportano un costo. Questo costo viene fatturato in base a sottoscrizione di valutazione, sottoscrizione a MSDN gratuita o a pagamento. Per ulteriori informazioni sui costi dell'esecuzione delle macchine virtuali di Azure, vedere [Prezzi di Macchine virtuali](https://azure.microsoft.com/pricing/details/virtual-machines/) e [Calcolatore prezzi di Azure](https://azure.microsoft.com/pricing/calculator/). Per contenere i costi, vedere [Ridurre al minimo i costi delle macchine virtuali nell’ambiente di testing in Azure](base-configuration-dev-test-environment.md#mincost). 
  
![Test Lab Guide nel cloud Microsoft](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi al Test Lab Guide di One Microsoft Cloud.
  
### <a name="step-1-create-the-virtual-network"></a>Passaggio 1: creare la rete virtuale

In questo passaggio, viene creata la rete virtuale TestLab in Azure.

Per prima cosa, avviare un prompt di Azure PowerShell.
  
> [!NOTE]
> I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell. Vedere [Panoramica dei cmdlet di Azure PowerShell](https://docs.microsoft.com/it-IT/powershell/azureps-cmdlets-docs/). 
  
Accedere al proprio account Azure con il seguente comando.
  
```
Login-AzureRMAccount
```

> [!TIP]
> Per un file di testo contenente tutti i comandi di PowerShell riportati in questo articolo, fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d).
  
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
  
![Passaggio 1 della configurazione di base in Azure con la rete virtuale e subnet](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a>Passaggio 2: configurare DC1

In questo passaggio, verrà creata la macchina virtuale DC1 e verrà configurata come controller di dominio per il dominio di Windows Server Active Directory (AD) corp.contoso.com e un server DNS per le macchine virtuali della rete virtuale TestLab.

> [!NOTE]
> Prima di eseguire il blocco di comandi seguenti, verificare che l'area di Azure (posizione) scelta supporti le dimensioni della macchina virtuale di Azure, che per impostazione predefinita sono impostate su Standard_A1. Fare clic [qui](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) per vedere le informazioni più recenti sulle dimensioni e posizioni della macchina virtuale di Azure.
  
Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per DC1.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Verrà richiesto nome utente e password dell'account Administrator locale su DC1. Utilizzare una password complessa e annotare nome e password in una posizione sicura.
  
Eseguire quindi la connessione alla macchina virtuale DC1.
  
1. Nel [Portale di Azure](https://portal.azure.com), fare clic su **Gruppi di risorse >** [nome del nuovo gruppo di risorse] **> DC1 > Connetti**.
    
2. Nel riquadro aperto, fare clic su **Scarica file RDP**. Aprire il file DC1.rdp che viene scaricato e quindi fare clic su **Connetti**.
    
3. Specificare il nome dell'account Administrator locale DC1:
    
  - Per Windows 7:
    
    Nella finestra di dialogo **Protezione di Windows**, fare clic su **Utilizza un altro account**. In **Nome utente**, digitare **DC1\\**[nome dell'account Administrator locale].
    
  - Per Windows 8 o Windows 10:
    
    Nella finestra di dialogo **Sicurezza di Windows**, fare clic su **Ulteriori scelte**, quindi fare clic su **Utilizzare un altro account**. In **Nome utente**, digitare **DC1\\**[nome dell'account Administrator locale].
    
4. In **Password**, digitare la password dell’account Administrator locale, quindi fare clic su **OK**.
    
5. Quando viene richiesto, fare clic su **Sì**.
    
Aggiungere un ulteriore disco dati come nuovo volume con lettera di unità F: immettendo questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore in DC1.
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Configurare quindi DC1 come controller di dominio e il server DNS per il dominio corp.contoso.com. Eseguire questi comandi al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Sarà necessario specificare una password di amministratore in modalità provvisoria. Archiviare la password in un percorso sicuro.
  
Si tenga presente che il completamento di questi comandi potrebbe richiedere alcuni minuti.
  
Dopo il riavvio di DC1, riconnettersi alla macchina virtuale DC1 con le credenziali del dominio.
  
1. Nel [Portale di Azure](https://portal.azure.com), fare clic su **Gruppi di risorse >** [nome del nuovo gruppo di risorse] **> DC1 > Connetti**.
    
2. Eseguire il file DC1.rdp che viene scaricato e quindi fare clic su **Connetti**.
    
3. In **Sicurezza di Windows**, fare clic su **Utilizza un altro account**. In **Nome utente**, digitare **CORP\\**[nome dell'account Administrator locale].
    
4. In **Password**, digitare la password dell’account Administrator locale, quindi fare clic su **OK**.
    
5. Quando viene richiesto, fare clic su **Sì**.
    
Successivamente, creare un account utente in Active Directory che verrà utilizzato quando si accede a computer membri del dominio CORP. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Tenere presente che questo comando chiede di specificare la password dell'account User1. Poiché questo account verrà utilizzato per le connessioni desktop remote per tutti i computer membri del dominio CORP, scegliere una password complessa. Registrare la password dell'account User1 e archiviarla in una posizione sicura.
  
Configurare quindi il nuovo account User1 come amministratore dell'organizzazione. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

Chiudere la sessione Desktop remoto con DC1, quindi riconnettersi usando l'account CORP\\User1.
  
Successivamente, per consentire il traffico per lo strumento Ping, eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Questa è la configurazione corrente.
  
![Passaggio 2 della configurazione base in Azure con la macchina virtuale DC1](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a>Passaggio 3: configurare APP1

In questo passaggio, si crea e configura APP1, che fornisce servizi di condivisione file e Web.

> [!NOTE]
> Prima di eseguire il blocco di comandi seguenti, verificare che l'area di Azure (posizione) scelta supporti le dimensioni della macchina virtuale di Azure, che per impostazione predefinita sono impostate su Standard_A1. Fare clic [qui](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) per vedere le informazioni più recenti sulle dimensioni e posizioni della macchina virtuale di Azure.
  
Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per APP1.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Successivamente, connettersi alla macchina virtuale APP1 usando il nome e la password dell'account Administrator locale di APP1, quindi aprire un prompt dei comandi di Windows PowerShell.
  
Per controllare la risoluzione del nome e la comunicazione della rete tra APP1 e DC1, eseguire il comando **ping dc1.corp.contoso.com** e verificare che siano presenti quattro risposte.
  
Unire quindi la macchina virtuale APP1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

È necessario fornire le credenziali di un account di dominio CORP\\User1 dopo aver eseguito il comando **Add-Computer**.
  
Dopo il riavvio di APP1, connettersi utilizzando l'account CORP\\User1 e quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.
  
Successivamente, modificare APP1 in server Web con questo comando al prompt dei comandi di Windows PowerShell in APP1.
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Creare quindi una cartella condivisa e un file di testo all'interno della cartella in APP1 con i comandi di PowerShell.
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

Questa è la configurazione corrente.
  
![Passaggio 3 della configurazione di base in Azure con la macchina virtuale APP1](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a>Passaggio 4: configurare CLIENT1.

In questo passaggio, viene creato e configurato CLIENT1 che si comporta come un tipico portatile, tablet o computer desktop nella rete intranet di Contoso.

> [!NOTE]  
> Il seguente set di comandi crea CLIENT1 che esegue Windows Server 2016 Data Center. Tale operazione è possibile per tutti i tipi di sottoscrizioni di Azure. Se si dispone di una sottoscrizione di Azure basata su Visual Studio, è possibile creare CLIENT1 che esegue Windows 10 con il [Portale di Azure](https://portal.azure.com). 
  

> [!NOTE]
> Prima di eseguire il blocco di comandi seguenti, verificare che l'area di Azure (posizione) scelta supporti le dimensioni della macchina virtuale di Azure, che per impostazione predefinita sono impostate su Standard_A1. Fare clic [qui](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) per vedere le informazioni più recenti sulle dimensioni e posizioni della macchina virtuale di Azure.
  
Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per CLIENT1.
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Successivamente, connettersi alla macchina virtuale CLIENT1 usando il nome e la password dell'account Administrator locale di CLIENT1, quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.
  
Per controllare la risoluzione del nome e la comunicazione della rete tra CLIENT1 e DC1, eseguire il comando **ping dc1.corp.contoso.com** al prompt dei comandi di Windows PowerShell e verificare che siano presenti quattro risposte.
  
Unire quindi la macchina virtuale CLIENT1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

È necessario fornire le credenziali di un account di dominio CORP\\User1 dopo aver eseguito il comando **Add-Computer**.
  
Dopo il riavvio di CLIENT1, connettersi utilizzando nome e password dell'account CORP\\User1 e quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.
  
Successivamente, verificare che sia possibile accedere alle risorse Web e di condivisione file in APP1 da CLIENT1.
  
1. In Server Manager, nel riquadro della struttura, fare clic su **Server locale**.
    
2. In **Proprietà per CLIENT1**, fare clic su **Attiva** accanto a **Configurazione sicurezza avanzata IE**.
    
3. In **Configurazione sicurezza avanzata IE**, fare clic su **Disattiva** per **Amministratori** e **Utenti**, quindi fare clic su **OK**.
    
4. Dalla schermata Start, fare clic su **Internet Explorer**, quindi fare clic su **OK**.
    
5. Nella barra degli indirizzi digitare **http:\//app1.corp.contoso.com/**, quindi premere INVIO. Dovrebbe essere possibile visualizzare la pagina Web predefinita di Internet Information Services per APP1.
    
6. Dalla barra delle applicazioni del desktop, fare clic sull'icona Esplora File.
    
7. Nella barra degli indirizzi, digitare **\\\\app1\\Files**, quindi premere INVIO. Verrà visualizzata una finestra della cartella con il contenuto della cartella File condivisi.
    
8. Nella finestra della cartella **File** condivisi, fare doppio clic sul file **Example.txt**. Verrà visualizzato il contenuto del file Example.txt.
    
9. Chiudere **example.txt - Blocco note** e la finestra della cartella **File** condivisi.
    
Questa è la configurazione finale.
  
![Fase 4 della configurazione di base in Azure con la macchina virtuale CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
La configurazione di base di Azure è ora pronta per lo sviluppo e test delle applicazioni o per la creazione di ulteriori ambienti di testing. 
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>Ridurre al minimo i costi delle macchine virtuali nell’ambiente di testing in Azure

Per ridurre al minimo i costi dell'esecuzione di macchine virtuali in ambiente di testing, è possibile eseguire una delle operazioni seguenti:
  
- Creare l'ambiente di testing ed effettuare il test e la dimostrazione necessari al più presto possibile. Al termine, eliminare il gruppo di risorse per l'ambiente di testing.
    
- Arrestare le macchine virtuali nell’ambiente di testing in uno stato deallocato.
    
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

- [Ambiente di sviluppo/test di Office 365](office-365-dev-test-environment.md)
- [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
- [Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)
