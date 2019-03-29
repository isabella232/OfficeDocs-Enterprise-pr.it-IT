---
title: Amministrazione delle cassette postali di Exchange Online in un ambiente multi-geografico
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informazioni sull'amministrazione delle impostazioni multi-geografiche di Exchange Online con PowerShell di Microsoft.
ms.openlocfilehash: 5e1108c946ab1d9588ad5d1d41f21799e8254257
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934018"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="73ab4-103">Amministrazione delle cassette postali di Exchange Online in un ambiente multi-geografico</span><span class="sxs-lookup"><span data-stu-id="73ab4-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="73ab4-104">È richiesta la Sessione remota di PowerShell per visualizzare e configurare le proprietà multi-geografiche nell’ambiente di Office 365.</span><span class="sxs-lookup"><span data-stu-id="73ab4-104">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment.</span></span> <span data-ttu-id="73ab4-105">Per informazioni su come connettersi a PowerShell per Exchange Online, vedere [Connettersi a PowerShell per Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="73ab4-105">To connect to Exchange Online using remote PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="73ab4-106">È necessario il [modulo di PowerShell di Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o versione successiva in V1. x per visualizzare la proprietà**PreferredDataLocation** sugli oggetti utente.</span><span class="sxs-lookup"><span data-stu-id="73ab4-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="73ab4-107">Gli oggetti utente sincronizzati con AAD Connect in AAD non possono contenere i valori **PreferredDataLocation** modificati direttamente tramite ADD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73ab4-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="73ab4-108">Gli oggetti utente solo cloud possono essere modificati tramite AAD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73ab4-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="73ab4-109">Per connettersi a PowerShell di Azure Active Directory, vedere [Connettersi a PowerShell di Office 365](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="73ab4-109">To connect to Security & Compliance Center PowerShell, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="73ab4-110">È possibile connettersi direttamente a una posizione geografica con PowerShell di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73ab4-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>
<span data-ttu-id="73ab4-111">In genere, PowerShell di Exchange Online si connetterà alla posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="73ab4-111">Typically, Exchange Online PowerShell will connect to the central location.</span></span> <span data-ttu-id="73ab4-112">Tuttavia, è anche possibile connettersi alla posizioni satellitari.</span><span class="sxs-lookup"><span data-stu-id="73ab4-112">But, you can also connect directly to satellite locations.</span></span> <span data-ttu-id="73ab4-113">Per una migliore prestazione, è consigliabile connettersi direttamente alla posizione satellitare quando si gestiscono solo gli utenti in una specifica posizione geografica.</span><span class="sxs-lookup"><span data-stu-id="73ab4-113">Because of performance improvements, we recommend connecting directly to the satellite location when you only manage users in that geo location.</span></span>

<span data-ttu-id="73ab4-114">Per connettersi a una posizione geografica specifica, il parametro *ConnectionUri* è diversa dalle ordinarie istruzioni di connessione.</span><span class="sxs-lookup"><span data-stu-id="73ab4-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="73ab4-115">Il resto dei comandi e i valori sono uguali.</span><span class="sxs-lookup"><span data-stu-id="73ab4-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="73ab4-116">Ecco come procedere:</span><span class="sxs-lookup"><span data-stu-id="73ab4-116">The steps are as follows:</span></span>

1. <span data-ttu-id="73ab4-117">Nel computer locale, aprire Windows PowerShell ed eseguire il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="73ab4-117">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="73ab4-118">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare l'account e la password aziendale o dell'istituto di istruzione, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="73ab4-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="73ab4-119">Sostituire `<emailaddress>` con l'indirizzo di posta elettronica di **eventuali** cassette postali nella specifica posizione geografica e eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="73ab4-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="73ab4-120">Le autorizzazioni per la cassetta postale e la relazione con le credenziali nel passaggio 1 non sono un fattore; l'indirizzo di posta elettronica indica semplicemente a Exchange Online dove connettersi.</span><span class="sxs-lookup"><span data-stu-id="73ab4-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="73ab4-121">Ad esempio, se olga@contoso.onmicrosoft.com è l'indirizzo di posta elettronica di una cassetta postale valida nella posizione geografica a cui si desidera connettersi, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="73ab4-122">Eseguire il comando riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="73ab4-122">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```


## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="73ab4-123">Visualizzare le posizioni geografiche disponibili configurate nella propria organizzazione di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="73ab4-123">View the available geo locations that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="73ab4-124">Per visualizzare l'elenco di località geografiche configurate in Office 365 Multi-Geo, eseguire il comando seguente in PowerShell di Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="73ab4-124">To see the list of configured geo locations in Office 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-location-for-your-exchange-online-organization"></a><span data-ttu-id="73ab4-125">Visualizzare la posizione centrale per la propria organizzazione di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="73ab4-125">View the central location for your Exchange Online organization</span></span>
<span data-ttu-id="73ab4-126">Per visualizzare la posizione centrale del proprio tenant, eseguire il comando seguente in PowerShell di Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="73ab4-126">To view your tenant's central location, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="73ab4-127">Individuare la posizione geografica di una cassetta postale</span><span class="sxs-lookup"><span data-stu-id="73ab4-127">Find the geo location of a mailbox</span></span>
<span data-ttu-id="73ab4-128">La cmdlet **Get-Mailbox** in PowerShell di Exchange Online mostra le seguenti proprietà multi-geografica relative alle cassette postali:</span><span class="sxs-lookup"><span data-stu-id="73ab4-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="73ab4-129">**Database**: le prime 3 lettere del nome del database corrispondono al codice geografico, che indica dove la cassetta postale è attualmente ubicata.</span><span class="sxs-lookup"><span data-stu-id="73ab4-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="73ab4-130">Per cassette postali di archiviazione Online, sarà necessario usare le proprietà di **ArchiveDatabase**.</span><span class="sxs-lookup"><span data-stu-id="73ab4-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="73ab4-131">**MailboxRegion**: specifica il codice posizione geografica impostato dall'amministratore (sincronizzato da **PreferredDataLocation** in Azure AD).</span><span class="sxs-lookup"><span data-stu-id="73ab4-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="73ab4-132">**MailboxRegionLastUpdateTime**: indica quando MailboxRegion è stato aggiornato l’ultima volta (automaticamente o manualmente).</span><span class="sxs-lookup"><span data-stu-id="73ab4-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="73ab4-133">Per visualizzare le proprietà di una cassetta postale, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-133">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="73ab4-134">Ad esempio, per visualizzare le informazioni geografiche della cassetta postale chris@contoso.onmicrosoft.com, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-134">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="73ab4-135">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="73ab4-135">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="73ab4-136">**Nota:** se il codice della posizione geografica nel nome del database non corrisponde al valore **MailboxRegion**, la cassetta postale verrà automaticamente verrà inserita in una coda di trasferimento e spostata nella posizione geografica specificata dal valore del \*\* MailboxRegion\*\*(Exchange Online controlla se esiste una mancata corrispondenza tra questi valori di proprietà).</span><span class="sxs-lookup"><span data-stu-id="73ab4-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="73ab4-137">Spostare una cassetta postale esistente solo nel cloud in una posizione geografica specifica</span><span class="sxs-lookup"><span data-stu-id="73ab4-137">Move an existing cloud-only mailbox to a specific geo location</span></span>
<span data-ttu-id="73ab4-138">Un utente solo cloud è un utente non sincronizzato nel tenant tramite AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="73ab4-138">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect.</span></span> <span data-ttu-id="73ab4-139">Tale utente è stato creato direttamente in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="73ab4-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="73ab4-140">Usare il cmdlet**Get-MsolUser** e **Set-MsolUser** nel modulo di Azure Active Directory per Windows PowerShell per visualizzare o specificare la geografica in cui verrà archiviata cassetta postale dell'utente solo cloud.</span><span class="sxs-lookup"><span data-stu-id="73ab4-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="73ab4-141">Per visualizzare i valori **PreferredDataLocation** di un utente, utilizzare la sintassi in Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73ab4-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="73ab4-142">Ad esempio, per visualizzare i valori **PreferredDataLocation** dell’utente michelle@contoso.onmicrosoft.com, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="73ab4-143">Per modificare il valore**PreferredDataLocation** per un utente solo cloud, utilizzare la sintassi seguente in Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73ab4-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="73ab4-144">Ad esempio, per impostare i valori **PreferredDataLocation** sulla geografica dell’Unione Europea per l’utente michelle@contoso.onmicrosoft.com, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="73ab4-145">**Note**:</span><span class="sxs-lookup"><span data-stu-id="73ab4-145">**Notes**:</span></span>

- <span data-ttu-id="73ab4-146">Come già accennato in precedenza non è possibile usare questa procedura per gli oggetti utente sincronizzati dalla Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="73ab4-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="73ab4-147">È necessario modificare il valore **PreferredDataLocation** in Active Directory e sincronizzarlo con AAD Connect.</span><span class="sxs-lookup"><span data-stu-id="73ab4-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="73ab4-148">Per ulteriori informazioni, vedere [Sincronizzazione di Azure Active Directory Connect: configurare il percorso di dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="73ab4-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="73ab4-149">Il tempo necessario per spostare una cassetta postale in una nuova posizione geografica dipende da diversi fattori:</span><span class="sxs-lookup"><span data-stu-id="73ab4-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="73ab4-150">Le dimensioni e tipo di cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="73ab4-150">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="73ab4-151">Il numero totale di cassette postali di cui eseguire la migrazione.</span><span class="sxs-lookup"><span data-stu-id="73ab4-151">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="73ab4-152">La disponibilità delle risorse di spostamento.</span><span class="sxs-lookup"><span data-stu-id="73ab4-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="73ab4-153">Disattivazione della migrazione per cassette postali in blocco per controversia legale</span><span class="sxs-lookup"><span data-stu-id="73ab4-153">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="73ab4-154">Le cassette postali in blocco per controversia legale che vengono conservate per eDiscovery non possono essere spostate modificando i valori **PreferredDataLocation** dal loro stato di disattivazione.</span><span class="sxs-lookup"><span data-stu-id="73ab4-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="73ab4-155">Per spostare una cassetta postale disabilitata in blocco per controversia legale:</span><span class="sxs-lookup"><span data-stu-id="73ab4-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="73ab4-156">Assegnare una licenza temporanea alla cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="73ab4-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="73ab4-157">Modificare il **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="73ab4-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="73ab4-158">Rimuovere la licenza dalla cassetta postale dopo che è stata spostata nella posizione geografica selezionata per ripristinare la disattivazione.</span><span class="sxs-lookup"><span data-stu-id="73ab4-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="73ab4-159">Creare nuove cassette postali nel cloud in una posizione geografica specifica</span><span class="sxs-lookup"><span data-stu-id="73ab4-159">Create new cloud mailboxes in a specific geo location</span></span>
<span data-ttu-id="73ab4-160">Per creare una nuova cassetta postale in una posizione geografica specifica, è necessario procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="73ab4-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="73ab4-161">Configurare il valore **PreferredDataLocation** come descritto nella sezione precedente *prima che* venga creata la cassetta postale in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73ab4-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="73ab4-162">Ad esempio, configurare il valore **PreferredDataLocation** per un utente prima di assegnare una licenza.</span><span class="sxs-lookup"><span data-stu-id="73ab4-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="73ab4-163">Assegnare una licenza contemporaneamente all’impostazione del valore **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="73ab4-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="73ab4-164">Per creare un nuovo utente solo cloud con licenza (non sincronizzato con AAD Connect) in un determinata posizione geografica, usare la sintassi seguente in Azure AD PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73ab4-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="73ab4-165">In questo esempio crea un nuovo account utente per Elizabeth Brunner con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="73ab4-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="73ab4-166">Nome dell'entità utente: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="73ab4-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="73ab4-167">Nome: entrambe</span><span class="sxs-lookup"><span data-stu-id="73ab4-167">First name: Elizabeth</span></span>

- <span data-ttu-id="73ab4-168">Cognome: Brunner</span><span class="sxs-lookup"><span data-stu-id="73ab4-168">Last name: Brunner</span></span>

- <span data-ttu-id="73ab4-169">Visualizzare nome Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="73ab4-169">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="73ab4-170">Password: generata casualmente e visualizzata nei risultati del comando (in quanto non vengono usati i parametri della *Password*)</span><span class="sxs-lookup"><span data-stu-id="73ab4-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="73ab4-171">Licenza: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="73ab4-171">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="73ab4-172">Posizione: Australia (AUS)</span><span class="sxs-lookup"><span data-stu-id="73ab4-172">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="73ab4-173">Per ulteriori informazioni sulla creazione di nuovi account utente e la ricerca di valori di LicenseAssignment in Azure AD PowerShell, vedere [Creare account utente con PowerShell di Office 365](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [Visualizzare le licenze e i servizi con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="73ab4-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="73ab4-174">**Nota:** se si sta utilizzando PowerShell di Exchange Online per abilitare una cassetta postale si desidera che questa sia creata direttamente nella posizione geografica specificata in **PreferredDataLocation**, è necessario utilizzare un cmdlet di Exchange Online come **Enable-Mailbox** o **New-Mailbox** direttamente con il servizio di cloud.</span><span class="sxs-lookup"><span data-stu-id="73ab4-174">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="73ab4-175">Se si usa il cmdlet di Exchange locale**Enable-RemoteMailbox**, la cassetta postale verrà creata nella posizione centrale.</span><span class="sxs-lookup"><span data-stu-id="73ab4-175">If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the central location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="73ab4-176">Effettuare l’integrazione di cassette postali locali esistenti in una posizione geografica specifica</span><span class="sxs-lookup"><span data-stu-id="73ab4-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>
<span data-ttu-id="73ab4-177">È possibile usare i processi e gli strumenti standard di integrazione per eseguire la migrazione di una cassetta postale di un'organizzazione di Exchange locale a Exchange Online, tra cui la [Dashboard di migrazione nell'interfaccia](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e il cmdlet [New-MigrationBatch ](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) in PowerShell di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73ab4-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="73ab4-178">Il primo passaggio consiste nel verificare che esista un oggetto utente per ogni cassetta postale su cui effettuare l’integrazione e verificare che sia configurato il corretto valore della **PreferredDataLocation** in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="73ab4-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="73ab4-179">Gli strumenti di integrazione rispetteranno il valore **PreferredDataLocation** e verrà eseguita la migrazione delle cassette postali direttamente alla posizione geografica specificata.</span><span class="sxs-lookup"><span data-stu-id="73ab4-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="73ab4-180">Oppure, la procedura seguente consente di aggiungere cassette postali direttamente a una posizione geografica specifica tramite il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in PowerShell di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73ab4-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="73ab4-181">Verificare che esista un oggetto utente per ogni cassetta postale su cui effettuare l’integrazione e che la **PreferredDataLocation** sia impostata sul valore desiderato in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="73ab4-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="73ab4-182">Il valore di **PreferredDataLocation** sarà sincronizzato con l’attributo di**MailboxRegion** del corrispondente oggetto utente di posta in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="73ab4-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="73ab4-183">Connettersi direttamente a specifici posizioni geografiche satellitari seguendo le istruzioni di connessione dei passaggi precedenti di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="73ab4-183">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="73ab4-184">Nella finestra di PowerShell di Exchange Online, archiviare le credenziali di amministratore locale usate per eseguire la migrazione delle cassette postali in una variabile, eseguendo il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="73ab4-185">Su PowerShell di Exchange Online, creare una nuova **New-MoveRequest** simile all’esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="73ab4-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="73ab4-186">Ripetere il passaggio #4 per ogni cassetta postale che per necessario eseguire la migrazione dall’Exchange locale alla posizione satellitare con cui si è attualmente connessi.</span><span class="sxs-lookup"><span data-stu-id="73ab4-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="73ab4-187">Se è necessario eseguire la migrazione di altre cassette postali a un percorso satellitare differente, ripetere i passaggi da 2 a 4 per ogni località satellite specifica.</span><span class="sxs-lookup"><span data-stu-id="73ab4-187">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="73ab4-188">Creazione di report multi-geografici</span><span class="sxs-lookup"><span data-stu-id="73ab4-188">Multi-geo reporting</span></span>
<span data-ttu-id="73ab4-189">**I report sull'utilizzo di Multi-Geo** nell’interfaccia di amministrazione di Microsoft 365 mostrano il numero di utenti in base alla località geografica.</span><span class="sxs-lookup"><span data-stu-id="73ab4-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="73ab4-190">Il report mostra la distribuzione degli utenti per il mese corrente e fornisce i dati cronologici dagli ultimi 6 mesi.</span><span class="sxs-lookup"><span data-stu-id="73ab4-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="73ab4-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73ab4-191">See also</span></span>

[<span data-ttu-id="73ab4-192">Gestione di Office 365 ed Exchange Online con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="73ab4-192">Managing Office 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)