---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Riepilogo: connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando."
ms.openlocfilehash: d9bee7060f599120d2d6036c45b44e485ea9a0bd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849892"
---
# <a name="connect-to-office-365-powershell"></a>Connettersi a PowerShell di Office 365

 **Riepilogo:** connettersi all'organizzazione di Office 365 con PowerShell di Office 365 per eseguire le attività dell'interfaccia di amministrazione dalla riga di comando.
  
PowerShell di Office 365 consente di gestire le impostazioni di Office 365 dalla riga di comando. Connettersi a PowerShell di Office 365 è un processo semplice che consiste nell'installare il software necessario e successivamente connettersi all'organizzazione di Office 365. 

Sono disponibili due versioni del modulo di PowerShell da utilizzare per connettersi a Office 365 e gestire gli account utente, i gruppi e le licenze:

- Azure Active Directory PowerShell per Graph (i cmdlet includono **AzureAD** nel nome) 
- Modulo di Microsoft Azure Active Directory per Windows PowerShell (i cmdlet includono **MSol** nel nome) 

A partire dalla data di pubblicazione di questo articolo, il modulo di Azure Active Directory PowerShell per Graph non sostituisce completamente le funzionalità nei cmdlet del Modulo di Microsoft Azure Active Directory per Windows PowerShell per l'amministrazione utenti, gruppi e licenze. In molti casi, è necessario usare entrambe le versioni. È possibile installare in modo sicuro entrambe le versioni sullo stesso computer.

> [!TIP]
> **Nuovo utente di PowerShell?** È disponibile una [Panoramica video di PowerShell](https://support.office.com/it-IT/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), grazie a LinkedIn Learning. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

- Tempo stimato per il completamento: 5 minuti
    
- È possibile utilizzare le seguenti versioni di Windows:
    
  - Windows 10, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Usare una versione a 64 bit di Windows. A ottobre del 2014 è stato sospeso il supporto per la versione a 32 bit del Modulo di Microsoft Azure Active Directory per Windows PowerShell.
    
-  Queste procedure sono destinate agli utenti che sono membri di un ruolo di amministratore di Office 365. Per ulteriori informazioni, vedere [Informazioni sui ruoli di amministratore di Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Connettersi con il modulo di Azure Active Directory PowerShell per Graph

I comandi nel modulo di [Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) hanno **AzureAD** nel nome del cmdlet.

Per le procedure che necessitano di nuovi cmdlet nel modulo di Azure Active Directory PowerShell per Graph, eseguire questi passaggi per installare il modulo e connettersi alla sottoscrizione di Office 365.

>[!Note]
>Vedere [Modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) per informazioni sul supporto per le altre versioni di Microsoft Windows.
>

### <a name="step-1-install-required-software"></a>Passaggio 1: installare il software necessario

È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.
  
1. Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).
    
2. Nella finestra di comando **Amministratore: Windows PowerShell**, eseguire il comando seguente:
    
  ```
  Install-Module -Name AzureAD
  ```

Se viene richiesto di installare un modulo da un archivio non attendibile, digitare **Y** e premere INVIO.

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365

Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'*autenticazione a più fattori (MFA)*, eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).

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


Dopo aver eseguito la connessione, è possibile utilizzare i nuovi cmdlet per il [modulo di Azure Active Directory PowerShell per Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Connettersi con il Modulo di Microsoft Azure Active Directory per Windows PowerShell

I comandi nel Modulo di Microsoft Azure Active Directory per Windows PowerShell hanno **MSol** nel nome del cmdlet.
    
### <a name="step-1-install-required-software"></a>Passaggio 1: installare il software necessario

È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.
  
1.  Installare la versione a 64 bit dell'Assistente per l'accesso ai Microsoft Online Services: [Assistente per l'accesso ai Microsoft Online Services per professionisti IT - RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installare il Modulo di Microsoft Azure Active Directory per Windows PowerShell con la procedura seguente:
    
  - Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).
  - Eseguire il comando **Install-Module MSOnline**.
  - Se viene richiesto di installare il provider NuGet, digitare **Y** e premere INVIO.
  - Se viene richiesto di installare il modulo da PSGallery, digitare **Y** e premere INVIO.
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>Passaggio 2: connettersi ad Azure AD per la sottoscrizione a Office 365

Per connettersi ad Azure AD per la sottoscrizione a Office 365 con un nome dell'account e una password o con l'*autenticazione a più fattori (MFA)*, eseguire uno di questi comandi da un prompt dei comandi di Windows PowerShell (che non sia con privilegi elevati).

|||
|:-------|:-----|
| **Cloud di Office 365** | **Comando** |
| Office 365 internazionale (+GCC) | `Connect-MsolService` |
| Office 365 gestito da 21 Vianet | `Connect-MsolService -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironmentName AzureGermanyCloud` |
| U.S. Government DoD di Office 365 e U.S. Government GCC High di Office 365 | `Connect-MsolService -AzureEnvironmentName USGovernment` |
|||

Nella finestra di dialogo per **accedere all'account**, digitare nome utente e password dell'account dell'istituto di istruzione o aziendale di Office 365, quindi fare clic su **OK**.

Se si utilizza l'autenticazione a più fattori, seguire le istruzioni nelle finestre di dialogo aggiuntive per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica.

### <a name="how-do-you-know-this-worked"></a>Come verificare se l'operazione ha avuto esito positivo

Se non vengono visualizzati errori vuol dire che la connessione è stata eseguita correttamente. Un breve test consiste nell'eseguire un cmdlet di Office 365 (ad esempio, **Get-MsolUser**) e vedere i risultati.
  
Se non vengono visualizzati errori, controllare i requisiti seguenti:
  
- **Un problema comune è rappresentato da una password errata**. Ripetere il passaggio 2 e prestare particolare attenzione al nome utente e alla password immessi.
    
- **Il Modulo di Microsoft Azure Active Directory per Windows PowerShell richiede che la funzione Microsoft .NET Framework 3.5.* x* sia attiva sul computer in uso. È probabile che il computer disponga di una versione più recente (ad esempio, 4 o 4.5.* x*), ma la compatibilità con le versioni precedenti di .NET Framework può essere abilitata o disabilitata. Per ulteriori informazioni, vedere i seguenti argomenti:
    
  - Per Windows Server 2012 o Windows Server 2012 R2, vedere [Abilitare .NET Framework 3.5 con Aggiunta guidata ruoli e funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Per Windows 7 o Windows Server 2008 R2, vedere [Impossibile aprire il Modulo di Azure Active Directory per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - Per Windows 10, Windows 8.1 e Windows 8, vedere [Installare .NET Framework 3.5 in Windows 10, Windows 8.1 e Windows 8](https://docs.microsoft.com/it-IT/dotnet/framework/install/dotnet-35-windows-10)

  
- **La versione del Modulo di Microsoft Azure Active Directory per Windows PowerShell potrebbe essere scaduta.** Per verificare, eseguire il comando seguente in PowerShell di Office 365 o nel Modulo di Microsoft Azure Active Directory per Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se il numero della versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Modulo di Microsoft Azure Active Directory per Windows PowerShell e installare la versione più recente dal collegamento indicato nel passaggio 1.
    
- **Se viene visualizzato un errore di connessione, vedere l'argomento:** [Errore "La connessione-MsolService: eccezione di tipo"](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    

## <a name="see-also"></a>Vedere anche

- [Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
- [Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
- [Effettuare la connessione a tutti i servizi di Office 365 in un'unica finestra di Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

