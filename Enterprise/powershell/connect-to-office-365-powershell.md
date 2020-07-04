---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando.
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997422"
---
# <a name="connect-to-office-365-powershell"></a>Connettersi a PowerShell di Office 365

Office 365 PowerShell lets you manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization. 

Sono disponibili due versioni del modulo di PowerShell da utilizzare per connettersi a Office 365 e gestire gli account utente, i gruppi e le licenze:

- Azure Active Directory PowerShell per Graph (i cmdlet includono **AzureAD** nel nome)
- Modulo di Microsoft Azure Active Directory per Windows PowerShell (i cmdlet includono **MSol** nel nome) 

As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

È possibile utilizzare le seguenti versioni di Windows:
    
  - Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1

    > [!NOTE]
    > Per il modulo Azure Active Directory PowerShell per Graph, è necessario usare PowerShell versione 5.1 o successive. Per il modulo di Microsoft Azure Active Directory per Windows PowerShell, è necessario usare PowerShell versione 5.1 o successive fino alla versione 6. Non è possibile usare la versione 7 di PowerShell. Per Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2 SP1, scaricare e installare [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616). 
    
    > [!NOTE]
    > Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.
    
These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Connettersi con il modulo di Azure Active Directory PowerShell per Graph

I comandi nel modulo di Azure Active Directory PowerShell per Graph hanno **AzureAD** nel nome del cmdlet. È possibile installare il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) o [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1).

Per le procedure che necessitano di nuovi cmdlet nel modulo di Azure Active Directory PowerShell per Graph, eseguire questi passaggi per installare il modulo e connettersi alla sottoscrizione di Office 365.

>[!Note]
>Vedere [Modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) per informazioni sul supporto per le altre versioni di Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Passaggio 1: installare il software necessario

These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.
  
1. Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).
    
2. Nella finestra di comando **Amministratore: Windows PowerShell**, eseguire il comando seguente:
    
  ```powershell
  Install-Module -Name AzureAD
  ```

Se viene richiesto di installare un modulo da un archivio non attendibile, digitare **Y** e premere INVIO.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365

Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'autenticazione a più fattori (MFA), eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).

|||
|:-------|:-----|
| **Cloud di Office 365** | **Comando** |
| Office 365 internazionale (+GCC) | `Connect-AzureAD` |
| Office 365 gestito da 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365 | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.

Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.

Dopo aver eseguito la connessione, è possibile utilizzare i cmdlet per il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Connettersi con il Modulo di Microsoft Azure Active Directory per Windows PowerShell

I comandi nel Modulo di Microsoft Azure Active Directory per Windows PowerShell hanno **MSol** nel nome del cmdlet.

PowerShell versione 7 e successive non supportano il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per PowerShell versione 7 e successive, è necessario usare il modulo Azure Active Directory PowerShell per Graph o Azure PowerShell.

PowerShell Core non supporta il modulo di Microsoft Azure Active Directory per Windows PowerShell e i cmdlet con **MSOL** all'interno del nome. Per continuare a usare i cmdlet, è necessario eseguirli in Windows PowerShell. 
    
### <a name="step-1-install-required-software"></a>Passaggio 1: installare il software necessario

These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.
  
1.  Se non si esegue Windows 10, installare la versione a 64 bit dell'assistente per l'accesso ai Microsoft Online Services: [Assistente per l'accesso ai Microsoft Online Services per professionisti IT RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installare il Modulo di Microsoft Azure Active Directory per Windows PowerShell con la procedura seguente:
    
  - Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).
  - Eseguire il comando **Install-Module MSOnline**.
  - Se viene richiesto di installare il provider NuGet, digitare **Y** e premere INVIO.
  - Se viene richiesto di installare il modulo da PSGallery, digitare **Y** e premere INVIO.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365

Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'autenticazione a più fattori (MFA), eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).

|||
|:-------|:-----|
| **Cloud di Office 365** | **Comando** |
| Office 365 internazionale (+GCC) | `Connect-MsolService` |
| Office 365 gestito da 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365 | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.

Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.

### <a name="how-do-you-know-this-worked"></a>Come verificare se l'operazione ha avuto esito positivo

If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.
  
Se non vengono visualizzati errori, controllare i requisiti seguenti:
  
- **A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.
    
- **The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:
    
  - Per Windows Server 2012 o Windows Server 2012 R2, vedere [Abilitare .NET Framework 3.5 con Aggiunta guidata ruoli e funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Per Windows 7 o Windows Server 2008 R2, vedere [Impossibile aprire il Modulo di Azure Active Directory per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Per Windows 10, Windows 8.1 e Windows 8, vedere [Installare .NET Framework 3.5 in Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)

  
- **Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il modulo di Microsoft Azure Active Directory per Windows PowerShell e installarlo dal passaggio 1.

- **Se viene visualizzato un errore di connessione, vedere l'argomento:** [Errore "La connessione-MsolService: eccezione di tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
- **Se viene visualizzato un messaggio di errore "Get-Item: impossibile trovare il percorso", usare questo comando:** 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a>Vedere anche

- [Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
- [Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
- [Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
