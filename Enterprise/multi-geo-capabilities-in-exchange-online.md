---
title: Funzionalità multi-Geo in Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Espandere la presenza di Office 365 a più aree geografiche con funzionalità multi-geo in Exchange Online.
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Funzionalità multi-Geo in Exchange Online

Le funzionalità multi-Geo in Office 365 consentono di un singolo tenant possono estendersi su più aree geografiche (Geos). Quando è abilitata la Multi-Geo, i clienti possono selezionare il percorso del contenuto delle cassette postali Exchange Online (dati statici) singoli per ogni utente.

La posizione di tenant iniziale (noto come "predefinita" o "centralmente") è determinata in base all'indirizzo fatturazione. Quando è abilitata la Multi-Geo, è possibile effettuare le cassette postali in percorsi aggiuntivi "satellitari" da:

- Creazione di una nuova cassetta postale di Exchange Online direttamente in un satellitari.

- Spostamento di una cassetta postale di Exchange Online in una satellitari.

- Onboarding una cassetta postale da un'organizzazione di Exchange locale direttamente in un satellitari.

Sono disponibili per l'utilizzo in una configurazione Multi-Geo Geos seguenti:

- Asia Pacifico

- Australia

- Canada

- Unione Europea

- India (attualmente disponibili solo per i clienti con indirizzi fatturazione in India)

- Giappone

- Corea

- Regno Unito

- Stati Uniti

## <a name="prerequisite-configuration"></a>Configurazione dei prerequisiti
Prima di iniziare a utilizzare funzionalità Multi-Geo di Exchange Online, Microsoft è necessario configurare il tenant di Exchange Online per il supporto Multi-Geo. Questo processo di configurazione occasionale viene attivato quando si ordina Multi-Geo licenze e devono adottare in genere meno di 30 giorni per il completamento.

Si riceverà le notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) durante la configurazione è stato avviato e completato. Configurazione viene attivata automaticamente quando si acquistare le licenze Multi-Geo.

## <a name="mailbox-placement-and-moves"></a>Spostamenti e la posizione della cassetta postale
Al termine di prerequisito passaggi di configurazione di Multi-Geo, Microsoft Exchange Online rispetta l'attributo **PreferredDataLocation** per gli oggetti utente in Azure Active Directory.

Exchange Online Sincronizza la proprietà **PreferredDataLocation** di Azure Active Directory nella proprietà **MailboxRegion** nel servizio directory di Exchange Online. Il valore di **MailboxRegion** determina geografica in cui verranno inserite cassette postali degli utenti e le cassette postali di archiviazione associato. Non è possibile configurare principale delle cassette postali e archivi cassette postali dell'utente di cui si trovano in Geos diversi. È possibile configurare un solo livello geografico per ogni oggetto utente.

- Quando **PreferredDataLocation** è configurato su un utente con una cassetta postale esistente, la cassetta postale verrà automaticamente spostata Geo specificato. 

- Quando **PreferredDataLocation** è configurato su un utente senza una cassetta postale esistente, la cassetta postale di cui eseguire il provisioning in Geo specificato. 

- Se non viene specificato alcun livello geografico, verrà effettuata la cassetta postale nel livello geografico predefinito.

**Nota**: funzionalità Multi-Geo e Skype per le riunioni Online Business regionale ospitata utilizzare la proprietà **PreferredDataLocation** per gli oggetti utente per individuare i servizi. Se si configurano i valori **PreferredDataLocation** per gli oggetti utente per le riunioni regionale ospitate, la cassetta postale per gli utenti verrà automaticamente spostata nella Geo specificato dopo Multi-Geo è abilitato nel tenant di Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitazioni per le funzionalità per la Multi-Geo in Exchange Online
1. Solo cassette postali degli utenti, cassette postali delle risorse (sale e attrezzature cassette postali) e le cassette postali condivise supportano funzionalità Multi-Geo. È possibile inserire le cassette postali di cartelle pubbliche e gruppi di Office 365 in geografica principale del cliente.
 
2. Sicurezza e conformità caratteristiche (ad esempio, il controllo ed eDiscovery) disponibili nell'interfaccia di amministrazione di Exchange (EAC) non sono disponibili nelle organizzazioni con più Geo. In realtà, è necessario utilizzare [centro conformità e sicurezza di Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) per configurare le caratteristiche di sicurezza e conformità.

3. Outlook per gli utenti Mac potrebbero verificarsi una perdita temporanea di accesso alla cartella di archivio Online durante lo spostamento delle relative cassette postali in un nuovo Geo. Questa condizione si verifica quando il primario dell'utente e cassette postali di archiviazione si trovano nella Geos diversi, perché spostamenti delle cassette postali tra Geo possono completare in momenti diversi.

4. Gli utenti non possono condividere *cartelle delle cassette postali* tra Geos in Outlook sul web (precedentemente noto come Outlook Web App o OWA). Ad esempio, un utente nell'Unione europea non può utilizzare Outlook sul web per aprire una cartella condivisa in una cassetta postale che si trova negli Stati Uniti. Tuttavia, Outlook sugli utenti web possibile aprire *altre cassette postali* in Geos diversi utilizzando una finestra separata del browser, come descritto in [aprire la cassetta postale di un'altra persona in una finestra separata del browser in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Nota**: la condivisione delle cartelle delle cassette postali tra Geo è supportata in Outlook in Windows.

5. Delega di calendario tra Geo attualmente non è supportata in Outlook sul web. Delega di calendario tra Geo è supportata in Outlook in Windows.

## <a name="administration"></a>Amministrazione 
Per visualizzare e configurare le proprietà correlate Geo nell'ambiente Office 365, è necessario remote PowerShell. Per ulteriori informazioni sui vari moduli PowerShell utilizzati per gestire Office 365, vedere [gestione di Office 365 ed Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- È necessario il [Modulo di PowerShell di Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o versioni successive in V1. x per visualizzare la proprietà **PreferredDataLocation** per gli oggetti utente. Per connettersi a PowerShell di Azure Active Directory, vedere [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Per connettersi a Exchange Online PowerShell, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Connettersi direttamente a un livello geografico specifico tramite Exchange Online PowerShell
In genere, Exchange Online PowerShell si connetterà a livello geografico predefinito. Tuttavia, è inoltre possibile connettere direttamente a Geos non predefinito. A causa dei miglioramenti delle prestazioni, è consigliabile la connessione direttamente a Geo non predefinito quando si gestiscono solo gli utenti di tale livello geografico.

Per connettersi a un determinato livello geografico, il parametro *ConnectionUri* è diverso da quello istruzioni connessione regolari. Il resto dei comandi e i valori sono gli stessi. I passaggi sono:

1. Nel computer locale, aprire Windows PowerShell ed eseguire il comando seguente:
    
    ```
    $UserCredential = Get-Credential
    ```
   Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro o scuola account e la password e quindi fare clic su **OK**.
    
2. Sostituire `<emailaddress>` con l'indirizzo di posta elettronica di **qualsiasi** cassetta postale di destinazione Geo e utilizzare il seguente comando. Le autorizzazioni per la cassetta postale e relazione con le proprie credenziali nel passaggio 1 non sono un fattore; l'indirizzo di posta elettronica semplicemente indica a Exchange Online where per la connessione.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Ad esempio, se olga@contoso.onmicrosoft.com è l'indirizzo di posta elettronica di una cassetta postale valida in geografica a cui connettersi, eseguire il comando seguente:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Eseguire il comando seguente:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisiti di versione Azure Active Directory Connect
Connettere AAD versione 1.1.524.0 o versione successivo è l'unico metodo supportato per l'impostazione della proprietà **PreferredDataLocation** per gli oggetti utente che vengono sincronizzati da Active Directory locale. Per istruzioni dettagliate, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Codici geo
I codici tre lettere per specificare il livello geografico nella proprietà **PreferredDataLocation** . Nella tabella seguente sono elencati i codici di Geos disponibili:

|Geo |Codice |
|---------|---------|
|Asia/Pacifico |APC |
|Australia |AUSTRALIA |
|Canada |POSSIBILE |
|Unione Europea |EUR |
|India |RICERCA |
|Giappone |GIAPPONESE |
|Corea |(COREANO) |
|Regno Unito |GBR |
|Stati Uniti |NOME |

**Nota**: le proprietà **PreferredDataLocation** e **MailboxRegion** sono stringhe con alcun controllo degli errori. Se si immette un valore non valido (ad esempio NAN) della cassetta postale verrà inserita nel livello geografico predefinito.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Visualizzazione Geos disponibili configurati nell'organizzazione Exchange Online
Per visualizzare l'elenco dei Geos configurati nell'organizzazione Exchange Online, eseguire il seguente comando in Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

L'output del comando avrà questo aspetto:

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a>Individuare la posizione geografica di una cassetta postale
Il cmdlet **Get-Mailbox** in Exchange Online PowerShell vengono visualizzate le proprietà relative al livello geografico seguenti per le cassette postali:

- **Database**: le prime 3 lettere del nome del database corrispondono al codice Geo, che fornisce le informazioni della cassetta postale in cui attualmente si trova.

- **MailboxRegion**: specificare il codice Geo è stato impostato dall'amministratore (sincronizzato da **PreferredDataLocation** in Azure Active Directory).

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

> [!NOTE]
> Se il codice Geo nel nome del database non corrisponde a quello **MailboxRegion** , la cassetta postale verrà spostata in Geo specificato dal valore **MailboxRegion** (Exchange Online Cerca una mancata corrispondenza tra i valori delle proprietà).

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a>Spostare una cassetta postale cloud esistente a un livello geografico specifico
Utilizzare il cmdlet **Get-MsolUser** e **Set-MsolUser** nel modulo Azure Active Directory per Windows PowerShell per visualizzare o specificare geografica in cui verrà archiviata cassetta postale dell'utente.

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

Ad esempio, per impostare il valore **PreferredDataLocation** per l'Unione europea (EUR) per michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Note**:

- Come accennato in precedenza per gli oggetti utente sincronizzato da Active Directory locale, è possibile utilizzare questa procedura. È necessario modificare il valore **PreferredDataLocation** utilizzando AAD Connect. Per ulteriori informazioni, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Il tempo impiegato per spostare una cassetta postale dipende da diversi fattori:
 
  - La dimensione e tipo di cassetta postale.
 
  - Il numero di cassette postali da spostare.
 
  - Disponibilità delle risorse di spostamento.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Spostamento disabilitate le cassette postali presenti conservazione per controversia legale
Disabilitate le cassette postali conservazione per controversia legale che vengono conservate per scopi non possono essere spostati modificando i valori **PreferredDataLocation** nello stato disabilitato eDiscovery. Per spostare una cassetta postale disabilitata sulla conservazione per controversia legale:

1. Assegnare temporaneamente una licenza per la cassetta postale.

2. Modificare **PreferredDataLocation**.

3. Rimuovere la licenza dalla cassetta postale dopo che è stata spostata in Geo selezionato per rimetterlo in stato disabilitato.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Creare nuove cassette postali cloud in un determinato livello geografico 
Per creare una nuova cassetta postale in un determinato livello geografico, è necessario eseguire una della procedura seguente:

- Configurare il valore **PreferredDataLocation** come descritto nella precedente sezione *prima* viene creata la cassetta postale di Exchange Online (ad esempio configurando il valore **PreferredDataLocation** su un utente prima di assegnare una licenza). 

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

Percorso di 3: Australia (Australia)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Per ulteriori informazioni sulla creazione di nuovi account utente e la ricerca di valori LicenseAssignment in PowerShell di Azure Active Directory, vedere [creare gli account utente con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> [!NOTE]
> Se si utilizza Exchange PowerShell per abilitare una cassetta postale e la cassetta postale da creare direttamente in Geo specificato in **PreferredDataLocation**è necessario, è necessario utilizzare un cmdlet di Exchange Online, ad esempio **Enable-Mailbox** o **New-Mailbox** direttamente in base al servizio cloud. Se si utilizza il cmdlet di Exchange locale **Enable-RemoteMailbox** , verrà creata la cassetta postale in Geo predefinito.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Esistenti incorporato cassette postali locali in un determinato livello geografico
È possibile utilizzare gli strumenti di onboarding standard e i processi per eseguire la migrazione di una cassetta postale da un'organizzazione di Exchange locale a Exchange Online, tra cui il [dashboard di migrazione in EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e il cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) di Exchange Online PowerShell.

Il primo passaggio consiste nel verificare che un oggetto utente esiste per ciascuna cassetta postale essere onboarded e verificare che il valore **PreferredDataLocation** corretto è configurato in Azure Active Directory. Gli strumenti di on-boarding rispettano il valore **PreferredDataLocation** e verranno eseguita la migrazione di cassette postali direttamente a Geo specificato.

In alternativa, è possibile utilizzare la procedura seguente per le cassette postali incorporate direttamente in un Geo specifico utilizzando il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell.

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

5. Ripetere il passaggio #4 per ogni cassetta postale che è necessario eseguire la migrazione di Exchange locale a satellitari Geo attualmente si è connessi.

6. Se è necessario eseguire la migrazione di cassette postali aggiuntive a un altro satellitari Geo, ripetere i passaggi da 2 a 4 per ogni satellitari specifico Geo.

### <a name="multi-geo-reporting"></a>Creazione di report multi-Geo
**Report di utilizzo della Multi-Geo** nell'interfaccia di amministrazione di Office 365 viene visualizzato il numero di utenti da Geo. Il rapporto viene visualizzato distribuzione degli utenti per il mese corrente e vengono forniti dati cronologici per gli ultimi 6 mesi.
 
