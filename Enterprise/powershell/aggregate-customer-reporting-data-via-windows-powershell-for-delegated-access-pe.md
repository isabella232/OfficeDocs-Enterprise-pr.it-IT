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
ms.custom: DecEntMigration
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 'Riepilogo: utilizzare Windows PowerShell per Office 365 per recuperare i report su tutti i tenancy dei clienti e aggregare i dati in un unico percorso.'
ms.openlocfilehash: 89651971424d1b9a494335572d2654d8402ec146
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="32f08-103">Aggregare i dati di report dei clienti tramite Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="32f08-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="32f08-104">**Riepilogo:** Utilizzare Windows PowerShell per Office 365 recuperare i rapporti in tutti i contratti d'affitto cliente e aggrega i dati in un'unica posizione.</span><span class="sxs-lookup"><span data-stu-id="32f08-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="32f08-p101">Per impostazione predefinita, Windows PowerShell per Office 365 non dispone di un'aggregazione integrata dei dati di report dai tenancy di più clienti. Tuttavia, è possibile utilizzare questo script di Windows PowerShell per Office 365 di esempio per eseguire l'iterazione tramite tutti i tenancy dei clienti in modo da recuperare un singolo report per ogni cliente e aggregare i dati di report in un unico percorso. In questo modo si otterrà un unico report per tutti i tenant dei clienti.</span><span class="sxs-lookup"><span data-stu-id="32f08-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="32f08-p102">I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP). Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende. Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti. Quando vendono una sottoscrizione a Office 365, ricevono automaticamente le autorizzazioni Amministra per conto terzi per itenancy cliente, al fine di gestire ed eseguire segnalazioni per tutti i tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="32f08-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="32f08-112">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="32f08-112">Before you begin</span></span>

<span data-ttu-id="32f08-113">Per utilizzare questo script, sostituire i valori particolari per le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="32f08-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="32f08-p103">**$UserName**: è il nome utente dell'amministratore del partner. Queste credenziali verranno utilizzate per connettersi a tutti i tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="32f08-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="32f08-116">**$OutputFile**: è il file con valori delimitati da virgole al quale verranno aggregati i dati di report.</span><span class="sxs-lookup"><span data-stu-id="32f08-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="32f08-117">**$ErrorFile**: è il file di log di testo per gli errori.</span><span class="sxs-lookup"><span data-stu-id="32f08-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="32f08-p104">**$ScriptBlock**: questo script di esempio utilizza **Get-MailboxActivityReport** e parametri (come le date di inizio e di fine) per fornire all'utente un modo per iniziare. Se si desiderano altri report, sostituire il nome del report e i parametri necessari per **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="32f08-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="32f08-120">Aprire una sessione remota di Windows PowerShell in Exchange Online seguendo la procedura in [Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="32f08-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="32f08-121">Utilizzare Windows PowerShell per aggregare i report dei tenant dei clienti in un unico percorso</span><span class="sxs-lookup"><span data-stu-id="32f08-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="32f08-122">Copiare e incollare lo script seguente nel Blocco note.</span><span class="sxs-lookup"><span data-stu-id="32f08-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

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

2. <span data-ttu-id="32f08-p105">Salvare lo script come GetMailboxActivityReport.ps1 in un percorso facile da trovare. Ad esempio, il file è salvato in C:\\O365 Scripts.</span><span class="sxs-lookup"><span data-stu-id="32f08-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="32f08-125">Eseguire lo script in Windows PowerShell remoto mediante la seguente sintassi.</span><span class="sxs-lookup"><span data-stu-id="32f08-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="32f08-126">Nello script di esempio il report aggregato è collocato nel file ReportOutput.csv.</span><span class="sxs-lookup"><span data-stu-id="32f08-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="32f08-127">See also</span><span class="sxs-lookup"><span data-stu-id="32f08-127">See also</span></span>

#### 

[<span data-ttu-id="32f08-128">Guida per partner</span><span class="sxs-lookup"><span data-stu-id="32f08-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="32f08-129">Servizio Web per la creazione di report di Office 365</span><span class="sxs-lookup"><span data-stu-id="32f08-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="32f08-130">Cmdlet per la creazione di report in Exchange online</span><span class="sxs-lookup"><span data-stu-id="32f08-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

