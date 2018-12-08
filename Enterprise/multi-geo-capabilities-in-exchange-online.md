---
title: Funzionalità multi-Geo in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Espandere la presenza di Office 365 a più aree geografiche con funzionalità multi-geo in Exchange Online.
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200739"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Funzionalità multi-Geo in Exchange Online

Le funzionalità multi-Geo in Office 365 consentono di un singolo tenant possono estendersi su più aree geografiche. Quando è abilitata la multi-geo, i clienti possono selezionare il percorso del contenuto delle cassette postali Exchange Online (dati statici) singoli per ogni utente.

La posizione di tenant iniziale (noto come posizione centrale) è determinata in base all'indirizzo fatturazione. Quando è abilitata la multi-geo, è possibile effettuare le cassette postali nelle posizioni satellitari aggiuntive per:

- Creazione di una nuova cassetta postale di Exchange Online direttamente in una posizione satellitare.

- Spostamento di una cassetta postale di Exchange Online in una posizione satellitare.

- Onboarding una cassetta postale da un'organizzazione di Exchange locale direttamente in una posizione satellitare.

Sono disponibili per l'utilizzo in una configurazione Multi-Geo geo posizioni seguenti:

- Asia Pacifico

- Australia

- Canada

- Unione Europea

- Francia

- India

- Giappone

- Corea

- Regno Unito

- Stati Uniti

## <a name="prerequisite-configuration"></a>Configurazione dei prerequisiti
Prima di iniziare a utilizzare funzionalità Multi-Geo di Exchange Online, Microsoft è necessario configurare il tenant di Exchange Online per il supporto multi-geo. Questo processo di configurazione occasionale viene attivato dopo aver ordinato che multi-Geo di Office 365 e le licenze visualizzata nel tenant. Il processo di configurazione occasionale dovrebbe richiedere in genere meno di 30 giorni per il completamento. Per ordinare Office 365 Multi-Geo, contattare il rappresentante Microsoft. Per ulteriori informazioni, vedere https://aka.ms/Multi-Geo.

Si riceverà le notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) al termine della configurazione. Configurazione viene attivata automaticamente dopo le licenze multi-geo visualizzata nel tenant.

## <a name="mailbox-placement-and-moves"></a>Spostamenti e la posizione della cassetta postale
Al termine di operazioni di configurazione preliminari multi-geo, Microsoft Exchange Online rispetta l'attributo **PreferredDataLocation** per gli oggetti utente in Azure Active Directory.

Exchange Online Sincronizza la proprietà **PreferredDataLocation** di Azure Active Directory nella proprietà **MailboxRegion** nel servizio directory di Exchange Online. Il valore di **MailboxRegion** determina geografica in cui verranno inserite cassette postali degli utenti e le cassette postali di archiviazione associato. Non è possibile configurare primario della cassetta postale e archiviazione cassette postali un utente di cui si trovano in sedi diverse geo. Una sola posizione geografica può essere configurata per ogni oggetto utente.

- Quando **PreferredDataLocation** è configurato su un utente con una cassetta postale esistente, la cassetta postale verrà inserite in una coda di trasferimento e automaticamente spostati nella posizione geografica specificato. 

- Quando **PreferredDataLocation** è configurato su un utente senza una cassetta postale esistente, la cassetta postale di cui eseguire il provisioning in una posizione geografica specificato. 

- Quando si **PreferredDataLocation** non viene specificato un utente, la cassetta postale verrà effettuata nella posizione centrale.

- Se il codice **PreferredDataLocation** non corretto (ad esempio un tipo di NAN anziché nomi), verrà effettuata la cassetta postale nella posizione centrale.

**Nota**: funzionalità multi-geo e Skype per le riunioni Online Business regionale ospitata utilizzare la proprietà **PreferredDataLocation** per gli oggetti utente per individuare i servizi. Se si configurano i valori **PreferredDataLocation** per gli oggetti utente per le riunioni regionale ospitate, la cassetta postale per gli utenti verrà automaticamente spostata nella posizione specificata geo dopo multi-geo è abilitato nel tenant di Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitazioni per le funzionalità per la Multi-Geo in Exchange Online
1. Solo cassette postali degli utenti, cassette postali delle risorse (sale e attrezzature cassette postali) e le cassette postali condivise supportano funzionalità multi-geo. Pubblica cassette postali delle cartelle e i gruppi di Office 365 rimanere nella posizione centrale.
 
2. Sicurezza e conformità caratteristiche (ad esempio, il controllo ed eDiscovery) disponibili nell'interfaccia di amministrazione di Exchange (EAC) non sono disponibili nelle organizzazioni con più geo. In realtà, è necessario utilizzare [centro conformità e sicurezza di Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) per configurare le caratteristiche di sicurezza e conformità.

3. Outlook per gli utenti Mac potrebbero verificarsi una perdita temporanea di accesso alla cartella di archivio Online durante lo spostamento delle relative cassette postali in una nuova posizione geografica. Questa condizione si verifica quando il primario dell'utente e cassette postali di archiviazione si trovano nei percorsi geo diversi, perché spostamenti delle cassette postali tra Geo possono completare in momenti diversi.

4. Gli utenti non possono condividere *cartelle delle cassette postali* tra diverse ubicazioni geo in Outlook sul web (precedentemente noto come Outlook Web App o OWA). Ad esempio, un utente nell'Unione europea non può utilizzare Outlook sul web per aprire una cartella condivisa in una cassetta postale che si trova negli Stati Uniti. Tuttavia, Outlook sul Web users possibile aprire *altre cassette postali* in Geos diversi utilizzando una finestra separata del browser, come descritto in [aprire la cassetta postale di un'altra persona in una finestra separata del browser in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Nota**: la condivisione delle cartelle delle cassette postali tra geo è supportata in Outlook in Windows.

## <a name="administration"></a>Amministrazione 
Per visualizzare e configurare le proprietà geo multi nell'ambiente Office 365, è necessario remote PowerShell. Per ulteriori informazioni sui vari moduli PowerShell utilizzati per gestire Office 365, vedere [gestione di Office 365 ed Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- È necessario il [Modulo di PowerShell di Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o versioni successive in V1. x per visualizzare la proprietà **PreferredDataLocation** per gli oggetti utente. Gli oggetti utente sincronizzati da connettere AAD in AAD non possono avere i valori **PreferredDataLocation** modificati direttamente tramite PowerShell AAD. Gli oggetti utente solo cloud possono essere modificati tramite PowerShell AAD. Per connettersi a PowerShell di Azure Active Directory, vedere [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Per connettersi a Exchange Online PowerShell, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Connettersi direttamente a un livello geografico specifico tramite Exchange Online PowerShell
In genere, Exchange Online PowerShell si connetterà alla posizione geografica predefinita. Tuttavia, è inoltre possibile connettere direttamente in posizioni non predefinite geo. A causa dei miglioramenti delle prestazioni, è consigliabile connettersi direttamente alla posizione geografica non predefinito quando si gestiscono solo gli utenti in tale posizione geografica.

Per connettersi a un determinato livello geografico, il parametro *ConnectionUri* è diverso da quello istruzioni connessione regolari. Il resto dei comandi e i valori sono gli stessi. I passaggi sono:

1. Nel computer locale, aprire Windows PowerShell ed eseguire il comando seguente:
    
    ```
    $UserCredential = Get-Credential
    ```
   Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro o scuola account e la password e quindi fare clic su **OK**.
    
2. Sostituire `<emailaddress>` con l'indirizzo di posta elettronica di **qualsiasi** cassetta postale nella posizione geografica di destinazione e utilizzare il seguente comando. Le autorizzazioni per la cassetta postale e relazione con le proprie credenziali nel passaggio 1 non sono un fattore; l'indirizzo di posta elettronica semplicemente indica a Exchange Online where per la connessione.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Ad esempio, se olga@contoso.onmicrosoft.com è l'indirizzo di posta elettronica di una cassetta postale valida in geografica a cui connettersi, eseguire il comando seguente:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Eseguire il comando riportato di seguito:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisiti di versione Azure Active Directory Connect
Connettere AAD versione 1.1.524.0 o versione successivo è l'unico metodo supportato per l'impostazione della proprietà **PreferredDataLocation** per gli oggetti utente che vengono sincronizzati da Active Directory locale. Gli oggetti utente sincronizzati da connettere AAD in AAD non possono avere i valori **PreferredDataLocation** modificati direttamente tramite PowerShell AAD. Gli oggetti utente solo cloud possono essere modificati tramite PowerShell AAD. Per istruzioni dettagliate, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Codici geo
I codici tre lettere per specificare il livello geografico nella proprietà **PreferredDataLocation** . Nella tabella seguente sono elencati i codici di Geos disponibili:

|Geo |Codice |
|---------|---------|
|Asia/Pacifico |APC |
|Australia |AUS |
|Canada |CAN |
|Unione Europea |EUR |
|Francia |FRA|
|India |RICERCA |
|Giappone |JPN |
|Corea |KOR |
|Regno Unito |GBR |
|Stati Uniti |NAM |

**Nota**: le proprietà **PreferredDataLocation** e **MailboxRegion** sono stringhe con alcun controllo degli errori. Se si immette un valore non valido (ad esempio NAN) della cassetta postale verrà inserita nel livello geografico predefinito.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Visualizzazione Geos disponibili configurati nell'organizzazione Exchange Online
Per visualizzare l'elenco dei Geos configurati nell'organizzazione Exchange Online, eseguire il seguente comando in Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

L'output del comando avrà questo aspetto:

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Visualizzare il valore predefinito Geo per l'organizzazione Exchange Online
Per visualizzare il livello geografico predefinito dell'organizzazione Exchange Online, eseguire il comando seguente in Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

L'output del comando avrà questo aspetto:

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Individuare la posizione geografica di una cassetta postale
Il cmdlet **Get-Mailbox** in Exchange Online PowerShell viene visualizzato il seguente multi-geo relative proprietà per le cassette postali:

- **Database**: le prime 3 lettere del nome del database corrispondono al codice Geo, che fornisce le informazioni della cassetta postale in cui attualmente si trova. Proprietà deve essere utilizzata per cassette postali di archiviazione Online **ArchiveDatabase** .

- **MailboxRegion**: Specifica il codice di ubicazione geografica che è stato impostato dall'amministratore (sincronizzato da **PreferredDataLocation** in Azure Active Directory).

- **MailboxRegionLastUpdateTime**: indica MailboxRegion dell'ultimo aggiornamento (automaticamente o manualmente).

Per visualizzare le proprietà per una cassetta postale, utilizzare la sintassi seguente:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Ad esempio, per visualizzare le informazioni di livello geografico per chris@contoso.onmicrosoft.com cassetta postale, eseguire il comando seguente:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

L'output del comando avrà questo aspetto:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Nota:** Se il codice di posizione geografica nel nome del database non corrisponde a quello **MailboxRegion** , la cassetta postale sarà verrà automaticamente inserito in una coda di trasferimento e spostata la posizione geografica specificato dal parametro valore **MailboxRegion** (Exchange Online Cerca un mancata corrispondenza tra i valori delle proprietà).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Spostare una cassetta postale solo cloud esistente a un livello geografico specifico
Un utente solo cloud è un utente non syncrhonized al tenant tramite la connessione AAD. L'utente è stato creato direttamente in Azure Active Directory. Utilizzare il cmdlet **Get-MsolUser** e **Set-MsolUser** nel modulo Azure Active Directory per Windows PowerShell per visualizzare o specificare geografica in cui verrà archiviata un solo cloud cassetta postale dell'utente.

Per visualizzare il valore **PreferredDataLocation** per un utente, utilizzare la seguente sintassi in Azure Active Directory PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Ad esempio, per visualizzare il valore **PreferredDataLocation** michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

L'output del comando avrà questo aspetto:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Per modificare il valore **PreferredDataLocation** per un oggetto utente solo cloud, utilizzare la sintassi seguente in Azure Active Directory PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Ad esempio, per impostare il valore **PreferredDataLocation** su geo Unione europea (EUR) per michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Note**:

- Come spiegato in precedenza è possibile utilizzare questa procedura per gli oggetti utente sincronizzato da Active Directory locale. È necessario modificare il valore **PreferredDataLocation** utilizzando AAD Connect. Per ulteriori informazioni, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Il tempo necessario per spostare un mailboxfrom che relativa geo corrente nella nuova posizione geografica desiderata dipende da diversi fattori:
 
  - La dimensione e tipo di cassetta postale.
 
  - Il numero di cassette postali da spostare.
 
  - Disponibilità delle risorse di spostamento.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Spostamento disabilitate le cassette postali presenti conservazione per controversia legale
Disabilitate le cassette postali conservazione per controversia legale che vengono conservate per scopi non possono essere spostati modificando i valori **PreferredDataLocation** nello stato disabilitato eDiscovery. Per spostare una cassetta postale disabilitata sulla conservazione per controversia legale:

1. Assegnare temporaneamente una licenza per la cassetta postale.

2. Modificare **PreferredDataLocation**.

3. Rimuovere la licenza dalla cassetta postale dopo che è stata spostata nella posizione geografica selezionato in rimetterlo in stato disabilitato.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Creare nuove cassette postali cloud in un determinato livello geografico 
Per creare una nuova cassetta postale in una posizione geografica specifici, è necessario eseguire una della procedura seguente:

- Configurare il valore **PreferredDataLocation** come descritto nella precedente sezione *prima* che cassetta postale viene creata in Exchange Online. Ad esempio, è possibile configurare il valore **PreferredDataLocation** su un utente prima di assegnare una licenza. 

- Assegnare una licenza contemporaneamente che si imposta il valore **PreferredDataLocation** .

Per creare un nuovo solo cloud con licenza utente (non AAD connessione sincronizzati) in un livello geografico specifico, utilizzare la sintassi seguente in Azure Active Directory PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
In questo esempio crea un nuovo account utente per Elizabeth Brunner con i valori seguenti:

- Nome dell'entità utente: ebrunner@contoso.onmicrosoft.com

- Nome: Elizabeth

- Cognome: Brunner

- Nome visualizzato Elizabeth Brunner

- Password: generato casualmente e illustrate nei risultati del comando (dal momento che non viene utilizzato il parametro *Password* )

- Licenza: contoso:ENTERPRISEPREMIUM (E5)

- Posizione: Australia (Australia)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Per ulteriori informazioni sulla creazione di nuovi account utente e la ricerca di valori LicenseAssignment in PowerShell di Azure Active Directory, vedere [creare gli account utente con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Nota:** Se si utilizza Exchange Online PowerShell per abilitare una cassetta postale e la cassetta postale da creare direttamente in Geo specificato in **PreferredDataLocation**è necessario, è necessario utilizzare un cmdlet di Exchange Online, ad esempio **Enable-Mailbox** o **New-Mailbox **direttamente sul servizio cloud. Se si utilizza il cmdlet di Exchange locale **Enable-RemoteMailbox** , verrà creata la cassetta postale in Geo predefinito.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Esistenti incorporato cassette postali locali in un determinato livello geografico
È possibile utilizzare gli strumenti di onboarding standard e i processi per eseguire la migrazione di una cassetta postale da un'organizzazione di Exchange locale a Exchange Online, tra cui il [dashboard di migrazione in EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e il cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) di Exchange Online PowerShell.

Il primo passaggio consiste nel verificare che un oggetto utente esiste per ciascuna cassetta postale essere onboarded e verificare che il valore **PreferredDataLocation** corretto è configurato in Azure Active Directory. Gli strumenti di on-boarding rispettano il valore **PreferredDataLocation** e verranno eseguita la migrazione di cassette postali direttamente a Geo specificato.

In alternativa, è possibile utilizzare la procedura seguente per le cassette postali incorporate direttamente in una posizione geografica specifico utilizzando il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell.

1. Verificare l'oggetto utente per ciascuna cassetta postale da onboarded e che **PreferredDataLocation** sia impostata sul valore desiderato in Azure Active Directory. Il valore di **PreferredDataLocation** verrà sincronizzato con l'attributo **MailboxRegion** dell'oggetto utente di posta elettronica corrispondente in Exchange Online.

2. Connettersi direttamente a satellitari specifico Geo utilizzando le istruzioni di connessione da più indietro in questo argomento.

3. In Exchange Online PowerShell, archiviare le credenziali di amministratore locale che viene utilizzato per eseguire una migrazione delle cassette postali in una variabile eseguendo il comando seguente:

    ```
    $RC = Get-Credential
    ```

4. In Exchange Online PowerShell, creare un nuovo **New-MoveRequest** simile a quello riportato di seguito: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Ripetere il passaggio #4 per ogni cassetta postale che è necessario eseguire la migrazione da Exchange locale al percorso satellitari che attualmente si è connessi.

6. Se è necessario eseguire la migrazione di cassette postali aggiuntive in un percorso diverso satellitari, ripetere i passaggi da 2 a 4 per ogni località satellitari specifico.

### <a name="multi-geo-reporting"></a>Creazione di report multi-Geo
**Report di utilizzo della Multi-Geo** nell'interfaccia di amministrazione di Office 365 viene visualizzato il numero di utenti dalla posizione geografica. Il rapporto viene visualizzato distribuzione degli utenti per il mese corrente e vengono forniti dati cronologici per gli ultimi 6 mesi.
