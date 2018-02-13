---
title: Ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Riepilogo: Utilizzare questa guida dei laboratori di testing per creare una sottoscrizione di prova di Office 365 per la valutazione o sviluppo e di testing.'
ms.openlocfilehash: b3c9e83dfab3aaf02ad598021e11965657e877bb
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365

 **Riepilogo:** Utilizzare questa guida dei laboratori di testing per creare una sottoscrizione di prova di Office 365 per la valutazione o sviluppo e di testing.
  
È possibile utilizzare una sottoscrizione di valutazione di Office 365 e creare un ambiente di sviluppo/test di Office 365 per le applicazioni o per illustrare le caratteristiche e funzionalità di Office 365. Sono disponibili due versioni:
  
- L'ambiente di sviluppo/test di Office 365 semplificato è costituito da una sottoscrizione di valutazione di Office 365 che richiede l'accesso dal computer principale.
    
    Utilizzare questo ambiente quando si desidera illustrare rapidamente una funzionalità. Per l'ambiente di sviluppo/test di Office 365 semplificato, completare le fasi 2 e 3 del presente articolo.
    
- L'ambiente di sviluppo/test di Office 365 dell'azienda simulata è composto da una sottoscrizione di valutazione di Office 365 e da una intranet di un'organizzazione semplificata connessa a Internet, che è ospitata nei servizi infrastruttura di Microsoft Azure. È possibile compilare questa configurazione completamente nel cloud Microsoft.
    
    Utilizzare questo ambiente per illustrare una funzionalità o un'app in un ambiente simile a una rete di un'organizzazione tipica connessa a Internet o per le funzionalità che richiedono questo tipo di ambiente. Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, completare le fasi 1, 2 e 3 di questo articolo.
    
> [!NOTE]
> Si consiglia di stampare questo articolo per registrare i valori specifici necessari per questo ambiente nei 30 giorni della sottoscrizione di valutazione di Office 365. È possibile estendere la sottoscrizione di valutazione per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze. 
  
![Guide dei laboratori di testing nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Fase 1: creare la configurazione di base in Azure

Seguire le istruzioni [nell'ambiente di sviluppo/test di configurazione di Base](base-configuration-dev-test-environment.md).
  
È necessario una sottoscrizione di Azure. È possibile utilizzare la [Versione di valutazione gratuita di Azure](https://azure.microsoft.com/pricing/free-trial/) per questa configurazione. Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [credito Azure mensile per i sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Di seguito è riportata la configurazione risultante.
  
![Ambiente di sviluppo e di testing della configurazione di base in Azure](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
Questa configurazione è costituita dalle macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Fase 2: creare una sottoscrizione di valutazione di Office 365

Per avviare la sottoscrizione di valutazione di Office 365 E5, è necessario innanzitutto un nome di società fittizia e un nuovo account Microsoft.
  
1. È consigliabile che si utilizza un valore variant il nome di società Contoso per il nome della società è una società fittizia utilizzata nel contenuto di esempio di Microsoft, ma non obbligatorio. Registrare il proprio nome società fittizia: ___
    
2. Per l'iscrizione per un nuovo account di Microsoft, passare a [https://outlook.com](https://outlook.com) e creare un account con un nuovo account di posta elettronica e l'indirizzo. Iscriviti a Office 365 si utilizzerà questo account.
    
  - Registrare il nome e cognome del nuovo account qui: _______________________________
    
  - Registrare l'indirizzo e-mail del nuovo account qui: _____________________________@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Registrare una sottoscrizione di valutazione di Office 365 E5

1. Per l'ambiente di sviluppo e di testing di Office 365 leggero, aprire il browser Internet nel computer e passare a [https://aka.ms/e5trial](https://aka.ms/e5trial). 
    
    Per l'ambiente di sviluppo e di testing simulato enterprise di Office 365:
    
  - Dal [portale di Azure](https://portal.azure.com), la connessione a CLIENT1 con la CORP\\account User1.
    
  - Aprire un prompt dei comandi di Windows PowerShell a livello di amministratore ed eseguire questi comandi:
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > Fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) per ottenere un file di testo che contiene tutti i comandi di PowerShell in questo articolo.
  
  - Nella schermata Start fare clic su **Internet Explorer** e passare a [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Nella pagina **iniziale, possiamo conoscere è** specificare:
    
  - La posizione fisica dell'utente
    
  - Nome e cognome del nuovo account Microsoft
    
  - Il nuovo indirizzo di account di posta elettronica
    
  - Un numero di telefono dell'ufficio
    
  - Il nome dell'azienda fittizia
    
  - Dimensioni dell'organizzazione comprese tra 250-999 persone
    
3. Fare clic su **solo uno più passaggio**.
    
4. Nella pagina **Crea l'ID utente** digitare un nome utente con il nuovo indirizzo di posta elettronica, la società fittizia dopo il simbolo @ (rimuovere tutti gli spazi nel nome), quindi (due volte) una password per il nuovo Office 365 per gli account.
    
    Annotare la password in un posto sicuro.
    
    Registrare il nome della società fittizia per fare riferimento come **nome dell'organizzazione**, qui: ___
    
5. Fare clic su **Crea account personale**.
    
6. Nella **dimostrazione. È possibile aprire. Non. R. robot.** pagina, digitare il numero di telefono del telefono in grado di testo e quindi fare clic su **testo me**.
    
7. Digitare il codice di verifica dal messaggio di testo ricevuto e quindi fare clic su **Avanti**.
    
8. Registrare l'URL della pagina di accesso qui (selezionare e copiare): ___________________________________________
    
9. Registrare l'ID utente qui (selezionare e copiare): ___________________________________________.onmicrosoft.com
    
    Questo valore verrà considerato il **nome dell'amministratore globale di Office 365**.
    
10. Quando si **pronti iniziare**, fare clic.
    
11. Nella pagina successiva, attendere che Office 365 completi la configurazione e che siano disponibili tutti i riquadri.
    
Dovrebbe essere visualizzata la pagina principale del portale di Office 365 dalla quale è possibile accedere ai servizi di Office Online e all'interfaccia di amministrazione di Office 365.
  
Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, ecco la configurazione risultante.
  
![Ambiente di sviluppo e di testing Office 365](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Questa configurazione è costituita da: 
  
- Le macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.
    
- Una sottoscrizione di valutazione di Office 365 E5.
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Fase 3: configurazione di una sottoscrizione di valutazione di Office 365

In questa fase, configurare la sottoscrizione a Office 365 con altri utenti e i siti del team di SharePoint Online.
  
Innanzitutto, aggiungere quattro nuovi utenti e assegnare loro le licenze E5.
  
Utilizzare le istruzioni riportate in [connessione a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) per installare i moduli di PowerShell e connettersi a tua nuova sottoscrizione di Office 365 da:
  
- Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).
    
- Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).
    
 Nella finestra di dialogo richiesta credenziali di Windows PowerShell digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e una password.
  
Immettere il nome dell'organizzazione (ad esempio: contosotoycompany), il prefisso internazionale a due caratteri e quindi eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 2 e registrarlo in un percorso sicuro.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

Visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 3 e registrare in un percorso sicuro.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 4 e registrarlo in un percorso sicuro.
  
Eseguire i comandi seguenti dal prompt Modulo Microsoft Azure Active Directory per Windows PowerShell:
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

La visualizzazione del comando **New-MsolUser** , annotare la password generata per l'account utente 5 e registrarlo in un percorso sicuro.
  
Successivamente, creare tre nuovi siti del team di SharePoint Online per i reparti Vendite, Produzione e Supporto tecnico.
  
### <a name="create-three-new-sharepoint-online-team-sites"></a>Creare tre nuovi siti del team di SharePoint Online

1. Installare [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (il x64 versione).
    
2. Fare clic su **Start**, digitare **sharepoint**e quindi fare clic su **SharePoint Online Management Shell**.
    
3. Immettere il nome dell'organizzazione (esempio: contosotoycompany), quindi eseguire comandi seguenti dal prompt di SharePoint Online Management Shell per connettersi al servizio SharePoint Online
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. Nella finestra di dialogo **Microsoft SharePoint Online Management Shell** , digitare il nome di amministratore globale di Office 365 (esempio: jdoe@contosotoycompany.onmicrosoft.com) e una password, quindi fare clic su **Accedi**.
    
5. Per creare tre nuovi siti del team (vendite, produzione e supporto tecnico), immettere il nome di amministratore globale di Office 365 e quindi eseguire i comandi seguenti dalla riga di SharePoint Online Management Shell:
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. Eseguire questo comando per elencare gli URL dei nuovi siti:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. In Internet Explorer, immettere l'URL del sito Produzione per visualizzare il sito del team di SharePoint Online predefinito per il reparto di produzione.
    
## <a name="record-values-for-future-reference"></a>Registrare i valori per consultarli in futuro

Registrare questi valori per utilizzarli o distribuire altre guide di lab di test nell'ambiente di test di distribuzione:
  
- Nome amministratore globale di Office 365: ____________________________________.onmicrosoft.com (dal passaggio 9 della fase 2)
    
    Annotare anche la password dell'account in una posizione sicura.
    
- Nome dell'organizzazione della sottoscrizione di valutazione:_______________________________________________ onmicrosoft.com (dal passaggio 4 della fase 2)
    
- Per elencare gli account di User 2, User 3, User 4, e User 5, eseguire i comandi seguenti dal modulo di Microsoft Azure Active Directory per il prompt di Windows PowerShell:
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Registrare i nomi degli account qui:
    
  - Nome account utente User 2: user2@_______________________________________________.onmicrosoft.com
    
  - Nome account utente User 3: user3@_______________________________________________.onmicrosoft.com
    
  - Nome account utente User 4: user4@_______________________________________________.onmicrosoft.com
    
  - Nome account utente User 5: user5@_______________________________________________.onmicrosoft.com
    
    Annotare anche le password degli account in una posizione sicura.
    
- Per elencare gli URL dei siti dei team Vendite, Produzione e Supporto tecnico, eseguire il comando seguente dal prompt di SharePoint Online Management Shell:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - URL del sito di produzione: https://___.sharepoint.com/sites/production
    
  - URL del sito Vendite: https://______________________________________________.sharepoint.com/sites/sales
    
  - URL del sito Supporto tecnico: https://______________________________________________.sharepoint.com/sites/support
    
## <a name="next-steps"></a>Passaggi successivi

Utilizzare questi articoli aggiuntivi nell'ambiente di sviluppo/test di Office 365:
  
- [DirSync per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Autenticazione a più fattori per l'ambiente di sviluppo e di testing di Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [EDiscovery avanzate per l'ambiente di sviluppo e di testing di Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Protezione dei file riservati nell'ambiente di sviluppo e di testing di Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Ambiente isolato di sviluppo e di testing di sito del team SharePoint Online](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Classificazione dei dati ed etichette nell'ambiente di sviluppo e di testing di Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
Estendere l'ambiente di sviluppo/testing di Office 365 per includere ulteriori offerte cloud di Microsoft:
  
- [L'ambiente di sviluppo e di testing Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>Vedere anche

[Test Lab Guide (TLG) di adozione cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
[Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
[Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


