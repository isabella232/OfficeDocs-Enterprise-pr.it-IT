---
title: Automatizzare la raccolta file per eDiscovery
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 'Riepilogo: informazioni su come automatizzare la raccolta di file dai computer degli utenti per eDiscovery.'
ms.openlocfilehash: 0133da6eecb229ad999043c9dfcb15d98a732829
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030490"
---
# <a name="automate-file-collection-for-ediscovery"></a>Automatizzare la raccolta file per eDiscovery

 **Riepilogo:** Informazioni su come automatizzare la raccolta di file dai computer degli utenti per eDiscovery.
  
Tutte le aziende affrontano le potenzialità di azioni legali o di altro tipo. Mentre i reparti legali lavorano per ridurre tale esposizione, la controversia legale è una realtà aziendale. Quando una società affronta un'azione legale, è necessario, tramite il processo di individuazione legale, fornire tutti i materiali documentario rilevanti alla Corte e opporsi ai consulenti legali. 
  
eDiscovery è il processo in base al quale le aziende inventario, ricerca, identificare, preservare, filtrare e rendere disponibili i materiali documentario rilevanti che esistono in formato elettronico. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online ed Exchange Online possono contenere grandi quantità di contenuto documentario. A seconda della versione, questi prodotti possono supportare eDiscovery e sul posto (Lync tramite Exchange Server), rendendo più semplice per i team legali indicizzare, identificare, conservare e filtrare i contenuti più rilevanti per un determinato caso.
  
Molti documenti vengono archiviati nei computer locali degli utenti (depositari), non in una posizione centralizzata. Ciò rende sostanzialmente impossibile per SharePoint 2013 per la ricerca e, se non è possibile eseguire una ricerca, non può essere incluso in eDiscovery. Questa soluzione illustra come utilizzare gli script di accesso, l'orchestratore di sistema System Center 2012 R2 e Windows PowerShell per Exchange Server per automatizzare l'identificazione e la raccolta dei materiali documentari dai computer degli utenti.
  
## <a name="what-this-solution-does"></a>Cosa fa questa soluzione

Questa soluzione utilizza un gruppo di sicurezza globale, criteri di gruppo e uno script di Windows PowerShell per individuare, inventariare e raccogliere contenuto e file PST (Outlook Personal Store) dagli utenti dei computer locali a una condivisione di file nascosta. Da qui, i file PST possono essere importati in Exchange Server 2013 o Exchange Online. Tutti i file vengono quindi spostati utilizzando un orchestratore di System Center 2012 R2 Runbook in un'altra condivisione file in Microsoft Azure per l'archiviazione a lungo termine e l'indicizzazione da parte di SharePoint 2013. È quindi possibile utilizzare i centri di eDiscovery nella distribuzione di SharePoint 2013 locale o in SharePoint Online come si farebbe regolarmente per eseguire eDiscovery. 
  
> [!IMPORTANT]
> Questa soluzione utilizza Robocopy per copiare i file dai computer di custode in una condivisione file centralizzata. Poiché Robocopy non copia i file aperti o bloccati, tutti i file, inclusi i file PST, che il custode ha aperto non verranno raccolti. Sarà necessario raccoglierli manualmente. Questa soluzione fornisce un elenco che identifica in modo esplicito i file che non è in grado di copiare e il percorso completo di ogni file. 
  
Nel diagramma seguente vengono illustrati tutti i passaggi e gli elementi della soluzione.
  
![Panoramica della soluzione di raccolta di file automatizzata](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|Legenda * * * *||
|:-----|:-----|
|![callout Magenta 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|Creare un oggetto Criteri di gruppo e associarlo allo script di accesso all'insieme.  <br/> |
|![callout Magenta 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| Configurare il filtro di sicurezza per l'oggetto Criteri di gruppo per applicare solo il criterio di associazione ai gruppi depositari. <br/> |
|![callout Magenta 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Un custode accede e l'oggetto Criteri di gruppo viene eseguito, chiamando lo script di accesso all'insieme.  <br/> |
|![callout Magenta 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|Lo script di accesso all'insieme consente di inventariare tutte le unità collegate localmente nel computer dei depositari, cercando i file desiderati e registrando la propria posizione.  <br/> |
|![callout Magenta 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|Lo script di accesso all'insieme copia i file inventariati in una condivisione file nascosta nel server di gestione temporanea.  <br/> |
|![chiamata Magenta verso l'esterno 6](media/99589726-0c7e-406b-a276-44301a135768.png)| (Opzione A) Eseguire manualmente lo script di importazione PST per importare i file PST raccolti in Exchange Server 2013. <br/> |
|![callout magenta 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|(Opzione B) Utilizzando lo strumento di importazione di Office 365 e il processo, importare i file PST raccolti in Exchange Online.  <br/> |
|![callout Magenta 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|Spostare tutti i file raccolti in una condivisione di file di Azure per l'archiviazione a lungo termine con l'orchestratore di MoveToColdStorage System Center 2012 R2 Runbook. <br/> |
|![callout magenta 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|Indicizzare i file nella condivisione file di archiviazione frigorifera con SharePoint 2013.  <br/> |
|![callout Magenta 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|Eseguire eDiscovery sul contenuto nell'archiviazione frigorifera e nel server Exchange locale 2013.  <br/> |
|![callout Magenta 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|Eseguire eDiscovery sul contenuto di Office 365.  <br/> |
   
## <a name="prerequisites"></a>Prerequisiti

La configurazione di questa soluzione richiede molti elementi, la maggior parte dei quali è probabile che sia sul posto e configurati se si pensa a eDiscovery. Per gli elementi che non possono essere presenti o che richiedono una configurazione specifica, verranno forniti i collegamenti necessari per creare la configurazione di base. Prima di configurare la soluzione, è necessario disporre della configurazione di base.
  
### <a name="base-configuration"></a>Configurazione di base

|**Elemento**|**Collegamenti**|
|:-----|:-----|
|Dominio di servizi di dominio Active Directory (AD DS)  <br/> ||
|Connettività Internet dalla rete locale  <br/> ||
|SQL Server 2012 per il supporto di SharePoint 2013 e dell'orchestratore di System Center 2012 R2  <br/> |[Distribuzione di orchestratore di System Center-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| SharePoint 2013 locale o basato su Azure per eDiscovery (obbligatorio per l'opzione A) <br/> ||
|Server di condivisione file locale per la gestione temporanea  <br/> ||
|Exchange Server 2013 locale per l'opzione A PST Import  <br/> |CU5 (15.913.22) è disponibile su [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[Distribuzione di orchestratore di System Center-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 (Piano E3) con Exchange Online e SharePoint Online (obbligatorio per l'opzione B)  <br/> |Per iscriversi a un abbonamento a Office 365 E3, vedere [abbonamento a office 365 E3](https://go.microsoft.com/fwlink/p/?LinkId=613504).  <br/> |
|Sottoscrizione di Azure con una macchina virtuale  <br/> |Per iscriversi a un Azure, vedere [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|Una connessione VPN tra la rete locale e la sottoscrizione di Azure  <br/> |Per impostare un tunnel VPN tra la sottoscrizione di Azure e la rete locale, vedere [connettere una rete locale a una rete virtuale di Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=613507).  <br/> |
|SharePoint 2013 eDiscovery configurata per la ricerca in SharePoint e Exchange Server 2013 e, facoltativamente, Lync Server 2013  <br/> |Per configurare eDiscovery in questo modo, vedere [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows file Shares Lab test](https://go.microsoft.com/fwlink/p/?LinkId=393130).  <br/> |
|eDiscovery in Office 365 per SharePoint Online ed Exchange Online  <br/> |Per configurare eDiscovery in Office 365, vedere [configurare un centro eDiscovery in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).  <br/> |
   
## <a name="configure-the-environment"></a>Configurare l'ambiente

Dopo aver posizionato la configurazione di base, è possibile procedere alla configurazione della soluzione. 
  
### <a name="staging-file-share"></a>Condivisione file di gestione temporanea

1. Nel dominio locale, creare un gruppo di sicurezza globale denominato depositari.
    
2. Creare una condivisione file nascosta per i file raccolti dai computer depositari. Deve trovarsi in un server locale. Ad esempio, in un server denominato staging, creare una condivisione file denominata Cases $. L' **$** è necessario per renderla una condivisione nascosta.
    
3. Impostare le autorizzazioni di condivisione seguenti:
    
  - Depositari: modifica, lettura
    
  - Amministratori: controllo completo
    
  - Sottosistema attendibile di Exchange: modifica, lettura
    
4. Aprire la scheda **sicurezza** , aggiungere il gruppo depositari e fare clic su **Avanzate**. Impostare le autorizzazioni seguenti per il gruppo depositari:
    
  - **Digitare: Deny**
    
  - **Si applica a: cartella, sottocartelle e file**
    
5. Fare clic su **autorizzazioni avanzate** e selezionare le opzioni seguenti:
    
  - **Attributi di lettura**
    
  - **Leggere gli attributi estesi**
    
  - **Autorizzazioni di lettura**
    
6. Verificare l'accesso ai casi $ condivisione file eseguendo le operazioni seguenti:
    
1. Aggiungere un utente al gruppo depositari.
    
2. Inserire un file nella cartella Cases $.
    
3. Come utente, passare al server di gestione temporanea, ad esempio passare alla \\ \\condivisione di gestione temporanea per vedere quali condivisioni sono disponibili. Non dovrebbero essere visualizzati i **casi $** Share elencato.
    
4. Digitare manualmente il percorso completo per la condivisione dei casi $ in Esplora. Questo dovrebbe aprire la condivisione dei casi $.
    
5. Provare ad aprire il file precedentemente inserito nella condivisione. Questo errore dovrebbe essere esito negativo.
    
### <a name="logon-script"></a>Script di accesso

1. Copiare e incollare lo script di Windows PowerShell nel blocco note:
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. Salvare lo script sopra riportato come CollectionScript. ps1 in una posizione facile da trovare, ad esempio C:\\AFCScripts.
    
3. Utilizzare la funzionalità Vai a in blocco note. Apportare le modifiche seguenti, in base alle esigenze:
    
|**Riga #**|**Operazioni necessarie per la modifica**|**Obbligatorio/facoltativo**|
|:-----|:-----|:-----|
|71  <br/> |Variabile **$FileTypes** . Includere tutte le estensioni di file che si desidera vengano inventariate dallo script e che vengano raccolte nella variabile di tipo Array. <br/> |Facoltativo  <br/> |
|76 e 77  <br/> |Modificare il modo in cui viene creata la variabile **$CaseNo** in base alle proprie esigenze. Lo script acquisisce la data e l'ora correnti e aggiunge il nome dell'utente. <br/> |Facoltativo  <br/> |
|80  <br/> |**$CaseRootLocation** variabile deve essere impostata sulla condivisione file della raccolta dei server di gestione temporanea, ad esempio ** \\ \\per i casi di gestione temporanea\\$**. <br/> |Obbligatorio  <br/> |
   
4. Inserire il file CollectionScript. ps1 nella condivisione file Netlogon in un controller di dominio. 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>Configurare l'oggetto Criteri di gruppo per lo script di accesso e i gruppi di depositari

1. Configurare uno script di accesso per il gruppo depositari seguendo la sezione "come assegnare gli script di accesso degli utenti" nell'argomento [utilizzo degli script di avvio, arresto, accesso e disconnessione in criteri di gruppo](https://go.microsoft.com/fwlink/p/?LinkId=614844).
    
2. Rimuovere gli utenti autenticati dai **filtri di sicurezza**e aggiungere il gruppo depositari.
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>Opzione di importazione PST A, script per Exchange Server 2013

1.  Copiare e incollare lo script di Windows PowerShell seguente nel blocco note:
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Salvare lo script come PSTImportScript. ps1 in una posizione facile da trovare. Ad esempio, per semplificare l'utilizzo, creare una cartella nel server di gestione \\ \\temporanea\\denominato staging AFCScripts e salvarla.
    
3. Utilizzare la funzionalità Vai a in blocco note e apportare le modifiche seguenti, in base alle esigenze:
    
|**Riga #**|**Operazioni necessarie per la modifica**|**Obbligatorio/facoltativo**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** tag le cartelle di cassette postali in cui vengono importati PST. Se necessario, modificare l'operazione. <br/> |Facoltativo  <br/> |
|17   <br/> |**$ConnectionURI** necessario impostare il proprio server. <br/> > [!IMPORTANT]> verificare che il **$ConnectionURI** punti a una posizione http, non a HTTPS. Non funzionerà con https:.          |Obbligatorio  <br/> |
   
4. Verificare che l'account di sottosistema attendibile di Exchange disponga delle autorizzazioni di lettura, scrittura \\ \\ed\\esecuzione per i casi di gestione temporanea $ share.
    
5. Lo script di importazione PST richiede i due parametri di input seguenti:
    
  - **$SourcePath** La posizione dei file PST da importare, ad esempio \\ \\i casi di\\gestione temporanea $.
    
  - **$MailboxAlias** L'alias della cassetta postale di destinazione che riceverà gli elementi di posta elettronica importati.
    
6. Ad esempio, se si desidera importare tutti i file PST dal percorso \\Staging\Cases $ in una cassetta postale con l'alias eDiscoveryMailbox, è necessario eseguire lo script in questo `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`modo.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opzione di importazione PST B, per Exchange Online

-  Creare la struttura delle cassette postali in cui inserire i file PST importati. Per ulteriori informazioni su come creare una cassetta postale utente in Exchange Online, vedere[creare cassette postali utente in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>Archiviazione frigorifera

1. Creare una condivisione file nella macchina virtuale di Azure, in cui verranno posizionati tutti i file raccolti, ad esempio \\ \\AZFile1\\ContentColdStorage.
    
2. Concedere all'account di accesso al contenuto predefinito almeno le autorizzazioni di lettura per la condivisione e tutte le sottocartelle e i file. Per ulteriori informazioni sulla configurazione della ricerca di SharePoint 2013, vedere [creare e configurare un'applicazione del servizio di ricerca in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. Se si prevede di importare i file pst \\ \\da\\AZFile1 ContentColdStorage, concedere al sottosistema attendibile di Exchange le autorizzazioni di lettura, scrittura ed esecuzione per la condivisione.
    
### <a name="orchestrator"></a>Orchestrator

1. Scaricare la[ Runbook di MoveToColdStorage](https://go.microsoft.com/fwlink/?LinkId=616095) dall'area download Microsoft.
    
2. Aprire la **finestra di progettazione di Runbook**, nel riquadro **connessioni** , fare clic sulla cartella in cui si desidera importare i Runbook. Fare clic sul menu **azioni** e fare clic su **Importa**. Verrà visualizzata la finestra di dialogo **Importa** .
    
3. Nella casella **percorso file** Digitare il percorso e il nome del file di Runbook che si desidera importare oppure fare clic sui puntini di sospensione ( **...**) per passare al file che si desidera importare. 
    
4. Selezionare **Importa Runbook** e **importare i dati crittografati dell'orchestratore**. Cancellare **contatori**, **pianificazioni**, **variabili**, **gruppi di computer**, **importare configurazioni globali**e **sovrascrivere le configurazioni globali esistenti**.
    
5. Fare clic su **Fine**.
    
6. Modificare la runbook di **MoveFilesToColdStorage** come indicato di seguito:
    
1. **Spostamento attività file** : impostare il percorso del **file di origine** per la condivisione file di raccolta \\ \\,\\ad esempio i casi di gestione temporanea $. Impostare la **cartella di destinazione** sulla condivisione file di archiviazione fredda in Azure, ad \\ \\esempio\\AZFile1 ContentColdStorage. Selezionare **Crea un file con un nome univoco**.
    
2. **Elimina attività cartella** -impostare il **percorso:** per la condivisione file di raccolta, ad \\ \\esempio\\per i\\casi di gestione temporanea $ *, e selezionare **Elimina tutti i file e le sottocartelle**. 
    
7. Distribuire la runbook di **MoveToColdStorage** utilizzando le procedure descritte in[Deploying Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120).
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>Ricerca di SharePoint locale per l'archiviazione frigorifera

1. Creare una nuova origine di contenuto nella farm di SharePoint 2013 per la condivisione di archiviazione frigorifera in Azure \\ \\,\\ad esempio AZFile1 ContentColdStorage. Per ulteriori informazioni sulla gestione delle origini di contenuto, vedere [aggiungere, modificare o eliminare un'origine di contenuto in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Avviare una ricerca per indicizzazione completa. Per ulteriori informazioni, vedere, [avviare, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>Utilizzo della soluzione

Sono disponibili cinque passaggi principali per l'utilizzo di questa soluzione, presupponendo che non si desideri importare i file PST in Exchange Server 2013 ed Exchange Online. In questa sezione vengono fornite le procedure per tutti. L'interazione principale con la soluzione consiste nell'eseguire le operazioni seguenti:
  
1. Gestire l'appartenenza degli utenti al gruppo depositari.
    
2. Esaminare i file di registro generati dallo script di accesso. FileCopyErrors. log elenca tutti i file che non sono stati copiati correttamente. È necessario decidere cosa si vuole fare con loro
    
3. Gestione del processo di importazione PST.
    
4. Spostamento dei file di raccolta nell'archiviazione frigorifera.
    
Tutti gli altri passaggi non sono specifici di questa soluzione. Si tratta di attività amministrative standard eseguite in SharePoint 2013 e Office 365 e Azure. Vi sono elementi che questa soluzione non fornisce indicazioni che è necessario risolvere in base alle esigenze dell'azienda, ad esempio:
  
1. Verifica dei casi di eDiscovery e quali custodi sono associati a questo caso.
    
2. Verifica dei set di raccolte di file associate a un caso di eDiscovery.
    
3. Coordinando la tempistica dei passaggi di importazione e spostamento a freddo.
    
4. Gestione dello spazio dei file utilizzato in Azure.
    
5. Gestione delle cassette postali in cui vengono importati PST.
    
6. Backup e ripristino di tutti i dati locali.
    
### <a name="custodian-management"></a>Gestione dei depositari

- Per avviare il processo di raccolta automatica dei file per un singolo utente, aggiungerli al gruppo depositari. La volta successiva che l'utente accede, viene eseguito lo script di accesso assegnato al gruppo depositari tramite criteri di gruppo. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>Monitorare i file raccolti e controllare i file di registro

1. Guardare la condivisione file di raccolta, ad \\ \\esempio\\i casi\\di gestione temporanea $ *, per la cartella dell'insieme dall'utente. Il nome della cartella verrà formattato in questo modo: *yyyyMMddHHmm_UserName* .
    
2. Al termine dell'insieme, aprire la cartella della raccolta e passare alla cartella _Log. Nella cartella _Log verranno visualizzati gli elementi seguenti:
    
  - Un file XML per ogni unità locale nel computer dell'utente, ad esempio **a. XML**, **C. XML**. Questi file contengono le unità inventariali che sono denominate dopo e vengono utilizzate per l'operazione Robocopy.
    
    > [!NOTE]
    > Lo script di raccolta creerà solo una voce nel file di inventario per i tipi di file definiti nello script stesso. Non verrà creata una voce di inventario per ogni file nel computer dell'utente. 
  
  - Un file di registro denominato FileCopyErrors. log per ogni esecuzione della raccolta. Questo file contiene un elenco dei file che Robocopy non è stato in grado di copiare nella condivisione di raccolta file, \\ \\ad\\esempio i\\casi di gestione temporanea $ *. Sarà necessario esaminare questo e decidere quali azioni eseguire per questi file mancanti. In genere, è necessario raccoglierli manualmente se lo si desidera oppure è possibile decidere che non sono obbligatori e pertanto possono essere omessi dall'insieme.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Opzione di importazione PST A per Exchange Server 2013

1. Accedere al server che ospita la condivisione file di raccolta, ad esempio la **gestione temporanea**e l'apertura di Windows PowerShell. Per ulteriori informazioni sull'avvio di Windows PowerShell, vedere[avvio di Windows PowerShell su Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Impostare il criterio di esecuzione su Unrestricted. Digita `Set-ExecutionPolicy Unrestricted -Scope Process` in Windows PowerShell e premi INVIO.
    
3. Eseguire il file PSTImportScript. ps1 e fornire i parametri **$SourcePath** e **$MailboxAlias** . Per ulteriori informazioni sull'esecuzione di script di Windows PowerShell, vedere[Running scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. Esaminare l'output per individuare eventuali errori.
    
5. Prima di tentare di importare un file PST con nome identico nella stessa cassetta postale, è necessario rimuovere la richiesta di importazione delle cassette postali. Eseguire il seguente comando per eseguire le operazioni `Get-MailboxImportRequest | Remove-MailboxImportRequest`seguenti:. Verrà richiesto di rimuovere ogni singola richiesta dalla coda. Rispondere in base alle esigenze.
    
### <a name="pst-import-option-b-for-exchange-online"></a>Opzione di importazione PST B, per Exchange Online

- Per inserire i file PST raccolti in Exchange Online, seguire le procedure riportate nella sezione Import files into Office 365 through the network upload section of [office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).
    
### <a name="move-to-cold-storage"></a>Passare a archiviazione frigorifera

1. Eseguire la runbook di **MoveToColdStorage** utilizzando le procedure descritte in[Running Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123).
    
2. Guardare la condivisione di file di Azure in uso per l'archiviazione a lungo termine \\ \\,\\ad esempio AZFile1 ContentColdStorage e la condivisione di file di raccolta locale \\ \\,\\ad esempio i casi di gestione temporanea $. I file e le cartelle devono essere visualizzati nella condivisione file di archiviazione frigorifera e scompaiono dalla condivisione file di raccolta.
    
### <a name="ediscovery"></a>eDiscovery

1. Consente di eseguire la ricerca per indicizzazione completa della condivisione file di archiviazione frigorifera come pianificazioni oppure di avviare una ricerca per indicizzazione. Per ulteriori informazioni sull'avvio di ricerche per indicizzazione complete o incrementali, vedere [avviare, sospendere, riprendere o interrompere una ricerca per indicizzazione in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. Creare un caso di eDiscovery in SharePoint 2013 se è stata utilizzata l'opzione A per un file PST Import o creare un caso di eDiscovery in SharePoint Online se è stata utilizzata l'opzione B.
    

