---
title: Connettersi a PowerShell di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "Riepilogo: Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di Office 365 admin center dalla riga di comando."
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a>Connettersi a PowerShell di Office 365

 **Riepilogo:** Connettersi all'organizzazione Office 365 con Office 365 PowerShell per eseguire attività di amministrazione di Office 365 dalla riga di comando.
  
Office 365 PowerShell consente di gestire le impostazioni di Office 365 dalla riga di comando. Connessione a Office 365 PowerShell è una semplice tre passaggi cui installare il software necessario, eseguire il software necessario e quindi connettersi all'organizzazione Office 365. 

  
> [!TIP]
> **Nuovo PowerShell?** Visualizzare una [Panoramica video di PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)per offerto da Learning LinkedIn. 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>Che cosa è necessario sapere prima di iniziare

- Tempo stimato per il completamento: 5 minuti
    
- È possibile utilizzare le seguenti versioni di Windows:
    
  - 10 Windows, Windows 8.1, Windows 8 o Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >Utilizzare una versione a 64 bit di Windows. È stato rimosso il supporto per la versione a 32 bit di Microsoft Azure Active Directory Module per Windows PowerShell ottobre del 2014.
    
-  Queste procedure sono progettate per gli utenti che sono membri di un ruolo di amministrazione di Office 365. Per ulteriori informazioni, vedere [ruoli di amministratore su Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532367).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Connessione con il modulo di Microsoft Azure Active Directory per Windows PowerShell

I comandi di Microsoft Azure Active Directory Module per Windows PowerShell dispongono **Msol** nel loro nome del cmdlet.
    
### <a name="step-1-install-required-software"></a>Passaggio 1: Installazione del software necessario

È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.
  
1.  Installare la versione a 64 bit dell'Assistente di accesso a Microsoft Online Services: [Microsoft Online Services Assistente per l'accesso per RTW i professionisti IT](https://go.microsoft.com/fwlink/p/?LinkId=286152).
    
2. Installare il Microsoft Azure Active Directory Module per Windows PowerShell con la procedura seguente:
    
  - Aprire un prompt dei comandi di PowerShell di livello amministrativo.
  - Eseguire il comando **Install-modulo MSOnline** .
  - Se viene richiesto di installare il provider NuGet, digitare **s** e premere INVIO.
  - Se viene richiesto di installare il modulo da PSGallery, digitare **s** e premere INVIO.
  - Dopo l'installazione, chiudere la finestra di comando PowerShell.
    
### <a name="step-2-connect-to-your-office-365-subscription"></a>Passaggio 2: Connessione per la sottoscrizione a Office 365
<a name="step3"> </a>

Per la connessione con solo un *nome di account e password*:
  
1. Eseguire un prompt dei comandi di Windows PowerShell.
2. Nella finestra di comando **Windows PowerShell** , eseguire i comandi seguenti:
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.
    
Per la connessione con *l'autenticazione a più fattori (MFA)*:
  
1. Eseguire un prompt dei comandi di Windows PowerShell.
2. Nella finestra di comando **Microsoft Azure Active Directory Module per Windows PowerShell** eseguire il comando seguente.
    
```
Connect-MsolService
```

3. Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.
    
4. Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.
    
### <a name="how-do-you-know-this-worked"></a>Come verificare se l'operazione ha avuto esito positivo
<a name="step3"> </a>

Se non di errori, l'utente connesso correttamente. Una prova veloce consiste nell'eseguire un cmdlet di Office 365, ad esempio, **Get-MsolUser** - e visualizzare i risultati.
  
Se non vengono visualizzati errori, controllare i requisiti seguenti:
  
- **Un problema comune è una password non corretta**. Eseguire di nuovo passaggio 3. e prestare particolare attenzione per il nome utente e la password che immessi.
    
- * *The Microsoft Azure Active Directory Module per Windows PowerShell è necessario Microsoft .NET Framework 3.5.* funzione x * è abilitata per il computer * *. È probabile che il computer sia installata una versione più recente (ad esempio, 4 o 4.5.* x *), ma con le versioni precedenti la compatibilità con le versioni precedenti di .NET Framework può essere attivata o disattivata. Per ulteriori informazioni, vedere gli argomenti seguenti:
    
  - Per Windows Server 2012 o Windows Server 2012 R2, vedere [abilitare .NET Framework 3.5 con l'aggiunta di ruoli e guidata funzionalità](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - Per Windows 8 o Windows 8.1, vedere [installazione di .NET Framework 3.5 in Windows 8 o 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - Per Windows 7 o Windows Server 2008 R2, vedere [non è possibile aprire il Azure Active Directory Module per Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **La versione del Microsoft Azure Active Directory Module per Windows PowerShell potrebbe non essere aggiornata.** Per controllare, eseguire il comando seguente in Office 365 PowerShell o il Microsoft Azure Active Directory Module per Windows PowerShell:
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Se il numero di versione restituito è inferiore al valore 1.0.8070.2, disinstallare il Microsoft Azure Active Directory Module per Windows PowerShell e installare la versione più recente dal collegamento al passaggio 1.
    
- **Se si riceve un errore di connessione, vedere l'argomento:** ["Connect-MsolService: eccezione di tipo" errore](https://go.microsoft.com/fwlink/p/?LinkId=532377).
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Collegarsi con Azure Active Directory PowerShell modulo grafico
<a name="ConnectV2"> </a>

I comandi descritti in Azure Active Directory PowerShell modulo grafico dispongono "AzureAD" nel loro nome del cmdlet.

Per le procedure necessarie per i nuovi cmdlet di Azure Active Directory PowerShell modulo grafico, utilizzare la procedura seguente per installare il modulo ed eseguire la connessione alla sottoscrizione Office 365.

>[!Note]
>Per informazioni sul supporto per diverse versioni di Microsoft Windows, vedere [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) .
>

### <a name="step-1-install-required-software"></a>Passaggio 1: Installazione del software necessario

È sufficiente effettuare questa procedura solo una volta, non ogni volta che ci si connette. Tuttavia, probabilmente sarà necessario installare periodicamente le versioni più recenti del software.

  
1. Aprire un prompt dei comandi di Windows PowerShell con privilegi elevati (eseguire Windows PowerShell come amministratore).
    
2. Nella **amministratore: Windows PowerShell** finestra prompt dei comandi eseguita il comando seguente:
    
  ```
  Install-Module -Name AzureAD 
  ```

Se richiesto sull'installazione di un modulo da un archivio non attendibile, digitare **s** e premere INVIO.


### <a name="step-2-connect-to-office-365"></a>Passaggio 2: Connettersi a Office 365

Per connettersi alla sottoscrizione Office 365 con un *nome di account e password*:
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **OK**.
    
Per connettersi alla sottoscrizione Office 365 con *l'autenticazione a più fattori (MFA)*:

```
Connect-AzureAD
```

Nella finestra di dialogo **Azure Active Directory PowerShell** digitare il lavoro di Office 365 o nome utente dell'account scuola e la password e quindi fare clic su **Accedi**.
    
Seguire le istruzioni nella finestra di dialogo **Azure Active Directory PowerShell** per fornire ulteriori informazioni di autenticazione, ad esempio un codice di verifica e quindi fare clic su **Accedi**.
    
Dopo la connessione, è possibile utilizzare i cmdlet di nuovi per [Azure Active Directory PowerShell modulo grafico](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).
  
## <a name="see-also"></a>Vedere anche

- [Gestire Office 365 con PowerShell di Office 365](manage-office-365-with-office-365-powershell.md)
- [Guida introduttiva a PowerShell di Office 365](getting-started-with-office-365-powershell.md)
- [Effettuare la connessione a tutti i servizi Office 365 in un'unica finestra di Windows PowerShell](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Ottieni credenziali](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connettere-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

