---
title: Ambiente di sviluppo/test di Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
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
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 'Riepilogo: usare la seguente guida al lab test per creare una sottoscrizione di valutazione di Office 365 per valutazione o sviluppo/test.'
ms.openlocfilehash: a49ba10ab9ddded36f21ca9cc92f0482cbe7a4fb
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038031"
---
# <a name="office-365-devtest-environment"></a>Ambiente di sviluppo/test di Office 365

 **Riepilogo:** usare la seguente guida al lab test per creare una sottoscrizione di valutazione di Office 365 per valutazione o sviluppo/test.
  
È possibile utilizzare una sottoscrizione di valutazione di Office 365 e creare un ambiente di sviluppo/test di Office 365 per le applicazioni o per illustrare le caratteristiche e funzionalità di Office 365. Sono disponibili due versioni:
  
- L'ambiente di sviluppo/test di Office 365 semplificato è costituito da una sottoscrizione di valutazione di Office 365 che richiede l'accesso dal computer principale.
    
    Utilizzare questo ambiente quando si desidera illustrare rapidamente una funzionalità. Per l'ambiente di sviluppo/test di Office 365 semplificato, completare solamente le fasi 2 e 3 del presente articolo.
    
- L'ambiente di sviluppo/test di Office 365 dell'azienda simulata è composto da una sottoscrizione di valutazione di Office 365 e da una intranet di un'organizzazione semplificata connessa a Internet, che è ospitata nei servizi infrastruttura di Microsoft Azure. È possibile compilare questa configurazione completamente nel cloud Microsoft.
    
    Utilizzare questo ambiente per illustrare una funzionalità o un'app in un ambiente simile a una rete di un'organizzazione tipica connessa a Internet o per le funzionalità che richiedono questo tipo di ambiente. Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, completare le fasi 1, 2 e 3 di questo articolo.
    
> [!NOTE]
> Si consiglia di stampare questo articolo per registrare i valori specifici necessari per questo ambiente nei 30 giorni della sottoscrizione di valutazione di Office 365. È possibile estendere la sottoscrizione di valutazione per altri 30 giorni. Per un ambiente di sviluppo/test permanente, creare una nuova sottoscrizione a pagamento con un numero limitato di licenze. 
  
![Guide al lab test in Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida al lab test di One Microsoft Cloud.
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>Fase 1: creare la configurazione di base in Azure

Seguire le istruzioni riportate in [Ambiente di sviluppo/test della configurazione di base](base-configuration-dev-test-environment.md).
  
È necessario disporre di una sottoscrizione ad Azure. È possibile utilizzare [la versione di prova di Azure](https://azure.microsoft.com/pricing/free-trial/) per tale configurazione. Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [Credito Azure mensile per sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).
  
Di seguito è riportata la configurazione risultante.
  
![Ambiente di sviluppo/test della configurazione di base in Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
Questa configurazione è costituita dalle macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>Fase 2: creare una sottoscrizione di valutazione di Office 365

Per avviare la sottoscrizione di valutazione di Office 365 E5, è necessario innanzitutto un nome di società fittizia e un nuovo account Microsoft.
  
1. Si consiglia di utilizzare una variante del nome aziendale Contoso per il nome dell'azienda, che è un nome aziendale fittizio utilizzato nel contenuto di esempio di Microsoft, ma non è obbligatorio. Registrare il nome della società fittizia qui: ![](./media/Common-Images/TableLine.png)
    
2. Per registrare un nuovo account Microsoft, andare su [https://outlook.com](https://outlook.com) e creare un account con un nuovo account di posta elettronica e indirizzo. Utilizzare questo account per iscriversi a Office 365.
    
  - Registrare il nome e cognome del nuovo account qui: ![](./media/Common-Images/TableLine.png)
    
  - Registrare l'indirizzo e-mail del nuovo account qui: ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Registrare una sottoscrizione di valutazione di Office 365 E5

1. Per l'ambiente di sviluppo/test semplificato di Office 365, aprire il browser Internet sul computer e andare su [https://aka.ms/e5trial](https://aka.ms/e5trial). 
    
    Per l'ambiente di sviluppo/test aziendale simulato di Office 365, connettersi a CLIENT1 con l'account CORP\User1 dal portale di Azure.

    Dalla schermata Start, eseguire Microsoft Edge e andare su [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Nella pagina **Benvenuto, vogliamo conoscerti meglio**, specificare:
    
  - La posizione fisica dell'utente
    
  - Nome e cognome del nuovo account Microsoft
    
  - Il nuovo indirizzo di account di posta elettronica
    
  - Un numero di telefono dell'ufficio
    
  - Il nome dell'azienda fittizia
    
  - Dimensioni dell'organizzazione comprese tra 250-999 persone
    
3. Fare clic su **Ultimo passaggio**.
    
4. Nella pagina **Crea ID utente**, digitare un nome utente in base al nuovo indirizzo di posta elettronica, il nome della società fittizia dopo il segno @ (rimuovere tutti gli spazi nel nome), quindi una password (due volte) del nuovo account di Office 365. 
    
    Annotare la password in un posto sicuro.
    
    Registrare il nome della società fittizia, a cui fare riferimento con **nome dell'organizzazione**, qui: ![](./media/Common-Images/TableLine.png)
    
5. Fare clic su **Crea account**.
    
6. Nella pagina **Dimostra che non sei un robot**, digitare il numero di telefono di un telefono che riceve SMS, quindi fare clic su **Inviami un SMS**.
    
7. Immettere il codice di verifica del messaggio di testo ricevuto, quindi fare clic su **Avanti**.
    
8. Registrare l'URL della pagina di accesso qui (selezionare e copiare): ![](./media/Common-Images/TableLine.png)
    
9. Registrare l'ID utente qui (selezionare e copiare): ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Questo valore verrà denominato **Nome amministratore globale di Office 365**.
    
10. Quando viene visualizzato **Sei pronto per partire**, selezionarlo.
    
11. Nella pagina successiva, attendere che Office 365 completi la configurazione e che siano disponibili tutti i riquadri.
    
Dovrebbe essere visualizzata la pagina principale del portale di Office 365 dalla quale è possibile accedere ai servizi di Office Online e all'interfaccia di amministrazione di Microsoft 365.
  
Per l'ambiente di sviluppo/test di Office 365 dell'azienda simulata, ecco la configurazione risultante.
  
![Ambiente di sviluppo/test di Office 365](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
Questa configurazione è costituita da: 
  
- Le macchine virtuali DC1, APP1 e CLIENT1 in una subnet di una rete virtuale Azure.
    
- Una sottoscrizione di valutazione di Office 365 E5.
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>Fase 3: configurazione di una sottoscrizione di valutazione di Office 365

In questa fase, configurare la sottoscrizione a Office 365 con altri utenti e i assegnare loro le licenze di Office 365 E5.
  
Seguire le istruzioni in [Connettersi a Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) per connettersi all'abbonamento a Office 365 con Azure Active Directory PowerShell per il modulo grafico da:
  
- Dal computer (per l'ambiente di sviluppo/test di Office 365 leggero).
    
- Dalla macchina virtuale CLIENT1 (per l'ambiente di sviluppo/test di Office 365 aziendale simulato).
    
 Nella finestra di dialogo Richiesta credenziali di Windows PowerShell, digitare il nome dell'amministratore globale Office 365 (ad esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password.
  
Immettere il nome dell'organizzazione (ad esempio: contosotoycompany), il prefisso internazionale a due caratteri, una password comune di account e quindi eseguire i comandi seguenti dal prompt di PowerShell:

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a>Fase 4: Creare tre nuovi siti del team di SharePoint Online (facoltativo)

In questa fase configurare un set di siti del team di SharePoint Online.
  
1. Installare [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (versione x64).
    
2. Nella schermata **Start** digitare **sharepoint**, quindi fare clic su **SharePoint Online Management Shell**.
    
3. Immettere il nome dell'organizzazione (esempio: contosotoycompany), quindi eseguire comandi seguenti dal prompt di SharePoint Online Management Shell per connettersi al servizio SharePoint Online
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. Nella finestra di dialogo **SharePoint Online Management Shell di Microsoft**, digitare il nome dell'amministratore globale di Office 365 (ad esempio: jdoe@contosotoycompany.onmicrosoft.com) e la password, quindi fare clic su **Accedi**.
    
5. Per creare tre nuovi siti del team (Vendite, Produzione e Supporto tecnico), inserire il nome di un amministratore globale di Office 365, quindi eseguire i comandi seguenti dal prompt di SharePoint Online Management Shell:
    
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

Registrare questi valori per utilizzarli o distribuire altre guide al lab test nell'ambiente di test di distribuzione:
  
- Nome amministratore globale di Office 365: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (dal passaggio 9 della fase 2)
    
    Annotare anche la password dell'account in una posizione sicura.
    
- Nome dell'organizzazione della sottoscrizione di valutazione: ![](./media/Common-Images/TableLine.png) onmicrosoft.com (dal passaggio 4 della fase 2)
    
- Per elencare gli account di User 2, User 3, User 4, e User 5, eseguire i comandi seguenti dal modulo di Microsoft Azure Active Directory per il prompt di Windows PowerShell:
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Registrare i nomi degli account qui:
    
  - Nome account utente User 2: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nome account utente User 3: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nome account utente User 4: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nome account utente User 5: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Annotare anche le password degli account in una posizione sicura.
    
- (Facoltativo) Per elencare gli URL dei siti dei team Vendite, Produzione e Supporto tecnico, eseguire il comando seguente dal prompt di SharePoint Online Management Shell:
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - URL del sito Produzione: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production
    
  - URL del sito Vendite: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales
    
  - URL del sito Supporto tecnico: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>Passaggi successivi

Utilizzare questi articoli aggiuntivi nell'ambiente di sviluppo/test di Office 365:
  
- [Sincronizzazione della directory per l'ambiente di sviluppo/test di Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Autenticazione a più fattori per l'ambiente di sviluppo/test di Office 365. ](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Identità federata per l'ambiente di sviluppo/test di Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Cloud App Security per l'ambiente di sviluppo/test di Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Advanced eDiscovery per l'ambiente di sviluppo/test di Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Protezione dei file sensibili nell’ambiente di sviluppo/test di Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Sito del team SharePoint Online isolato nell'ambiente di sviluppo/test](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Classificazione e assegnazione di etichette ai dati nell'ambiente di sviluppo/test di Office 365 ](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
Estendere l'ambiente di sviluppo/test di Office 365 per includere ulteriori offerte cloud di Microsoft:
  
- [Ambiente di sviluppo/test di Microsoft 365 Enterprise](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>Vedere anche

- [Guida al lab test (TLG) per adozione del cloud](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Ambiente di sviluppo/test di Office 365 e Dynamics 365](office-365-and-dynamics-365-dev-test-environment.md)
  
- [Adozione del cloud e soluzioni ibride](cloud-adoption-and-hybrid-solutions.md)


