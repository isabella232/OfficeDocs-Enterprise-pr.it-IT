---
title: Aggregare i dati di report dei clienti tramite Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 'Riepilogo: utilizzare Windows PowerShell per Office 365 per recuperare i report su tutti i tenancy dei clienti e aggregare i dati in un unico percorso.'
ms.openlocfilehash: eba2c3be848b878670321485718317b5552b2db3
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
ms.locfileid: "18812107"
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Aggregare i dati di report dei clienti tramite Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)

 **Sintesi:** Utilizzare Windows PowerShell per Office 365 per recuperare i report su tutti i tenancy dei clienti e aggregare i dati in un unico percorso.
  
Per impostazione predefinita, Windows PowerShell per Office 365 non dispone di un'aggregazione integrata dei dati di report dai tenancy di più clienti. Tuttavia, è possibile utilizzare questo script di Windows PowerShell per Office 365 di esempio per eseguire l'iterazione tramite tutti i tenancy dei clienti in modo da recuperare un singolo report per ogni cliente e aggregare i dati di report in un unico percorso. In questo modo si otterrà un unico report per tutti i tenant dei clienti. 
  
I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti. Quando vendono una sottoscrizione a Office 365, ricevono automaticamente le autorizzazioni Amministra per conto terzi per itenancy cliente, al fine di gestire ed eseguire segnalazioni per tutti i tenancy dei clienti.
## <a name="before-you-begin"></a>Prima di iniziare

Per utilizzare questo script, sostituire i valori particolari per le variabili seguenti:
  
- **$UserName**: è il nome utente dell'amministratore del partner. Queste credenziali verranno utilizzate per connettersi a tutti i tenancy dei clienti.
    
- **$OutputFile**: è il file con valori delimitati da virgole al quale verranno aggregati i dati di report.
    
- **$ErrorFile**: è il file di log di testo per gli errori.
    
- **$ScriptBlock**: questo script di esempio utilizza **Get-MailboxActivityReport** e parametri (come le date di inizio e di fine) per fornire all'utente un modo per iniziare. Se si desiderano altri report, sostituire il nome del report e i parametri necessari per **Get-MailboxActivityReport**.
    
- Aprire una sessione remota di Windows PowerShell in Exchange Online seguendo la procedura in [Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Utilizzare Windows PowerShell per aggregare i report dei tenant dei clienti in un unico percorso

1. Copiare e incollare lo script seguente nel Blocco note.
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\ReportOutput.csv"

$ErrorFile = ".\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. Salvare lo script come GetMailboxActivityReport.ps1 in un percorso facile da trovare. Ad esempio, il file è salvato in C:\\O365 Scripts. 
    
3. Eseguire lo script in Windows PowerShell remoto mediante la seguente sintassi.
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

Nello script di esempio il report aggregato è collocato nel file ReportOutput.csv.
  
## <a name="see-also"></a>Vedere anche

#### 

[Guida per partner](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Servizio Web per la creazione di report di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlet per la creazione di report in Exchange online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

