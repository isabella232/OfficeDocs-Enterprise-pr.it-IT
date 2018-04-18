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
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="d400b-103">Funzionalità multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d400b-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="d400b-p101">Le funzionalità multi-Geo in Office 365 consentono di un singolo tenant possono estendersi su più aree geografiche (Geos). Quando è abilitata la Multi-Geo, i clienti possono selezionare il percorso del contenuto delle cassette postali Exchange Online (dati statici) singoli per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="d400b-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="d400b-p102">La posizione di tenant iniziale (noto come "predefinita" o "centralmente") è determinata in base all'indirizzo fatturazione. Quando è abilitata la Multi-Geo, è possibile effettuare le cassette postali in percorsi aggiuntivi "satellitari" da:</span><span class="sxs-lookup"><span data-stu-id="d400b-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="d400b-108">Creazione di una nuova cassetta postale di Exchange Online direttamente in un satellitari.</span><span class="sxs-lookup"><span data-stu-id="d400b-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="d400b-109">Spostamento di una cassetta postale di Exchange Online in una satellitari.</span><span class="sxs-lookup"><span data-stu-id="d400b-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="d400b-110">Onboarding una cassetta postale da un'organizzazione di Exchange locale direttamente in un satellitari.</span><span class="sxs-lookup"><span data-stu-id="d400b-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="d400b-111">Sono disponibili per l'utilizzo in una configurazione Multi-Geo Geos seguenti:</span><span class="sxs-lookup"><span data-stu-id="d400b-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="d400b-112">Asia Pacifico</span><span class="sxs-lookup"><span data-stu-id="d400b-112">Asia Pacific</span></span>

- <span data-ttu-id="d400b-113">Australia</span><span class="sxs-lookup"><span data-stu-id="d400b-113">Australia</span></span>

- <span data-ttu-id="d400b-114">Canada</span><span class="sxs-lookup"><span data-stu-id="d400b-114">Canada</span></span>

- <span data-ttu-id="d400b-115">Unione Europea</span><span class="sxs-lookup"><span data-stu-id="d400b-115">European Union</span></span>

- <span data-ttu-id="d400b-116">India (attualmente disponibili solo per i clienti con indirizzi fatturazione in India)</span><span class="sxs-lookup"><span data-stu-id="d400b-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="d400b-117">Giappone</span><span class="sxs-lookup"><span data-stu-id="d400b-117">Japan</span></span>

- <span data-ttu-id="d400b-118">Corea</span><span class="sxs-lookup"><span data-stu-id="d400b-118">Korea</span></span>

- <span data-ttu-id="d400b-119">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="d400b-119">United Kingdom</span></span>

- <span data-ttu-id="d400b-120">Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="d400b-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="d400b-121">Configurazione dei prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d400b-121">Prerequisite configuration</span></span>
<span data-ttu-id="d400b-p103">Prima di iniziare a utilizzare funzionalità Multi-Geo di Exchange Online, Microsoft è necessario configurare il tenant di Exchange Online per il supporto Multi-Geo. Questo processo di configurazione occasionale viene attivato quando si ordina Multi-Geo licenze e devono adottare in genere meno di 30 giorni per il completamento.</span><span class="sxs-lookup"><span data-stu-id="d400b-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="d400b-p104">Si riceverà le notifiche nel [Centro messaggi di Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) durante la configurazione è stato avviato e completato. Configurazione viene attivata automaticamente quando si acquistare le licenze Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="d400b-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="d400b-126">Spostamenti e la posizione della cassetta postale</span><span class="sxs-lookup"><span data-stu-id="d400b-126">Mailbox placement and moves</span></span>
<span data-ttu-id="d400b-127">Al termine di prerequisito passaggi di configurazione di Multi-Geo, Microsoft Exchange Online rispetta l'attributo **PreferredDataLocation** per gli oggetti utente in Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d400b-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="d400b-p105">Exchange Online Sincronizza la proprietà **PreferredDataLocation** di Azure Active Directory nella proprietà **MailboxRegion** nel servizio directory di Exchange Online. Il valore di **MailboxRegion** determina geografica in cui verranno inserite cassette postali degli utenti e le cassette postali di archiviazione associato. Non è possibile configurare principale delle cassette postali e archivi cassette postali dell'utente di cui si trovano in Geos diversi. È possibile configurare un solo livello geografico per ogni oggetto utente.</span><span class="sxs-lookup"><span data-stu-id="d400b-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="d400b-132">Quando **PreferredDataLocation** è configurato su un utente con una cassetta postale esistente, la cassetta postale verrà automaticamente spostata Geo specificato.</span><span class="sxs-lookup"><span data-stu-id="d400b-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="d400b-133">Quando **PreferredDataLocation** è configurato su un utente senza una cassetta postale esistente, la cassetta postale di cui eseguire il provisioning in Geo specificato.</span><span class="sxs-lookup"><span data-stu-id="d400b-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="d400b-134">Se non viene specificato alcun livello geografico, verrà effettuata la cassetta postale nel livello geografico predefinito.</span><span class="sxs-lookup"><span data-stu-id="d400b-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="d400b-p106">**Nota**: funzionalità Multi-Geo e Skype per le riunioni Online Business regionale ospitata utilizzare la proprietà **PreferredDataLocation** per gli oggetti utente per individuare i servizi. Se si configurano i valori **PreferredDataLocation** per gli oggetti utente per le riunioni regionale ospitate, la cassetta postale e OneDrive per gli utenti verranno automaticamente spostati in Geo specificato dopo Multi-Geo è abilitato nel tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="d400b-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox and OneDrive for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="d400b-137">Limitazioni per le funzionalità per la Multi-Geo in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d400b-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="d400b-p107">Solo cassette postali degli utenti, cassette postali delle risorse (sale e attrezzature cassette postali) e le cassette postali condivise supportano funzionalità Multi-Geo. È possibile inserire le cassette postali di cartelle pubbliche e gruppi di Office 365 in geografica principale del cliente.</span><span class="sxs-lookup"><span data-stu-id="d400b-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="d400b-p108">Sicurezza e conformità caratteristiche (ad esempio, il controllo ed eDiscovery) disponibili nell'interfaccia di amministrazione di Exchange (EAC) non sono disponibili nelle organizzazioni con più Geo. In realtà, è necessario utilizzare [centro conformità e sicurezza di Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) per configurare le caratteristiche di sicurezza e conformità.</span><span class="sxs-lookup"><span data-stu-id="d400b-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="d400b-p109">Outlook per gli utenti Mac potrebbero verificarsi una perdita temporanea di accesso alla cartella di archivio Online durante lo spostamento delle relative cassette postali in un nuovo Geo. Questa condizione si verifica quando il primario dell'utente e cassette postali di archiviazione si trovano nella Geos diversi, perché spostamenti delle cassette postali tra Geo possono completare in momenti diversi.</span><span class="sxs-lookup"><span data-stu-id="d400b-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="d400b-p110">Gli utenti non possono condividere *cartelle delle cassette postali* tra Geos in Outlook sul web (precedentemente noto come Outlook Web App o OWA). Ad esempio, un utente nell'Unione europea non può utilizzare Outlook sul web per aprire una cartella condivisa in una cassetta postale che si trova negli Stati Uniti. Tuttavia, Outlook sugli utenti web possibile aprire *altre cassette postali* in Geos diversi utilizzando una finestra separata del browser, come descritto in [aprire la cassetta postale di un'altra persona in una finestra separata del browser in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span><span class="sxs-lookup"><span data-stu-id="d400b-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="d400b-147">**Nota**: la condivisione delle cartelle delle cassette postali tra Geo è supportata in Outlook in Windows.</span><span class="sxs-lookup"><span data-stu-id="d400b-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="d400b-p111">Delega di calendario tra Geo attualmente non è supportata in Outlook sul web. Delega di calendario tra Geo è supportata in Outlook in Windows.</span><span class="sxs-lookup"><span data-stu-id="d400b-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="d400b-150">Amministrazione</span><span class="sxs-lookup"><span data-stu-id="d400b-150">Administration</span></span> 
<span data-ttu-id="d400b-p112">Per visualizzare e configurare le proprietà correlate Geo nell'ambiente Office 365, è necessario remote PowerShell. Per ulteriori informazioni sui vari moduli PowerShell utilizzati per gestire Office 365, vedere [gestione di Office 365 ed Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span><span class="sxs-lookup"><span data-stu-id="d400b-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="d400b-p113">È necessario il [Modulo di PowerShell di Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o versioni successive in V1. x per visualizzare la proprietà **PreferredDataLocation** per gli oggetti utente. Per connettersi a PowerShell di Azure Active Directory, vedere [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="d400b-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="d400b-155">Per connettersi a Exchange Online PowerShell, vedere [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span><span class="sxs-lookup"><span data-stu-id="d400b-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="d400b-156">Connettersi direttamente a un livello geografico specifico tramite Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="d400b-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="d400b-p114">In genere, Exchange Online PowerShell si connetterà a livello geografico predefinito. Tuttavia, è inoltre possibile connettere direttamente a Geos non predefinito. A causa dei miglioramenti delle prestazioni, è consigliabile la connessione direttamente a Geo non predefinito quando si gestiscono solo gli utenti di tale livello geografico.</span><span class="sxs-lookup"><span data-stu-id="d400b-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="d400b-p115">Per connettersi a un determinato livello geografico, il parametro *ConnectionUri* è diverso da quello istruzioni connessione regolari. Il resto dei comandi e i valori sono gli stessi. I passaggi sono:</span><span class="sxs-lookup"><span data-stu-id="d400b-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="d400b-163">Nel computer locale, aprire Windows PowerShell ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="d400b-164">Nella finestra di dialogo **Richiesta credenziali di Windows PowerShell** digitare il lavoro o scuola account e la password e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="d400b-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="d400b-p116">Sostituire `<emailaddress>` con l'indirizzo di posta elettronica di **qualsiasi** cassetta postale di destinazione Geo e utilizzare il seguente comando. Le autorizzazioni per la cassetta postale e relazione con le proprie credenziali nel passaggio 1 non sono un fattore; l'indirizzo di posta elettronica semplicemente indica a Exchange Online where per la connessione.</span><span class="sxs-lookup"><span data-stu-id="d400b-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="d400b-167">Ad esempio, se olga@contoso.onmicrosoft.com è l'indirizzo di posta elettronica di una cassetta postale valida in geografica a cui connettersi, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="d400b-168">Eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="d400b-169">Requisiti di versione Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="d400b-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="d400b-p117">Connettere AAD versione 1.1.524.0 o versione successivo è l'unico metodo supportato per l'impostazione della proprietà **PreferredDataLocation** per gli oggetti utente che vengono sincronizzati da Active Directory locale. Per istruzioni dettagliate, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="d400b-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="d400b-172">Codici geo</span><span class="sxs-lookup"><span data-stu-id="d400b-172">Geo Codes</span></span>
<span data-ttu-id="d400b-p118">I codici tre lettere per specificare il livello geografico nella proprietà **PreferredDataLocation** . Nella tabella seguente sono elencati i codici di Geos disponibili:</span><span class="sxs-lookup"><span data-stu-id="d400b-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="d400b-175">Geo</span><span class="sxs-lookup"><span data-stu-id="d400b-175">Geo</span></span> |<span data-ttu-id="d400b-176">Codice</span><span class="sxs-lookup"><span data-stu-id="d400b-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="d400b-177">Asia/Pacifico</span><span class="sxs-lookup"><span data-stu-id="d400b-177">Asia/Pacific</span></span> |<span data-ttu-id="d400b-178">APC</span><span class="sxs-lookup"><span data-stu-id="d400b-178">APC</span></span> |
|<span data-ttu-id="d400b-179">Australia</span><span class="sxs-lookup"><span data-stu-id="d400b-179">Australia</span></span> |<span data-ttu-id="d400b-180">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="d400b-180">AUS</span></span> |
|<span data-ttu-id="d400b-181">Canada</span><span class="sxs-lookup"><span data-stu-id="d400b-181">Canada</span></span> |<span data-ttu-id="d400b-182">POSSIBILE</span><span class="sxs-lookup"><span data-stu-id="d400b-182">CAN</span></span> |
|<span data-ttu-id="d400b-183">Unione Europea</span><span class="sxs-lookup"><span data-stu-id="d400b-183">European Union</span></span> |<span data-ttu-id="d400b-184">EUR</span><span class="sxs-lookup"><span data-stu-id="d400b-184">EUR</span></span> |
|<span data-ttu-id="d400b-185">India</span><span class="sxs-lookup"><span data-stu-id="d400b-185">India</span></span> |<span data-ttu-id="d400b-186">RICERCA</span><span class="sxs-lookup"><span data-stu-id="d400b-186">IND</span></span> |
|<span data-ttu-id="d400b-187">Giappone</span><span class="sxs-lookup"><span data-stu-id="d400b-187">Japan</span></span> |<span data-ttu-id="d400b-188">GIAPPONESE</span><span class="sxs-lookup"><span data-stu-id="d400b-188">JPN</span></span> |
|<span data-ttu-id="d400b-189">Corea</span><span class="sxs-lookup"><span data-stu-id="d400b-189">Korea</span></span> |<span data-ttu-id="d400b-190">(COREANO)</span><span class="sxs-lookup"><span data-stu-id="d400b-190">KOR</span></span> |
|<span data-ttu-id="d400b-191">Regno Unito</span><span class="sxs-lookup"><span data-stu-id="d400b-191">United Kingdom</span></span> |<span data-ttu-id="d400b-192">GBR</span><span class="sxs-lookup"><span data-stu-id="d400b-192">GBR</span></span> |
|<span data-ttu-id="d400b-193">Stati Uniti</span><span class="sxs-lookup"><span data-stu-id="d400b-193">United States</span></span> |<span data-ttu-id="d400b-194">NOME</span><span class="sxs-lookup"><span data-stu-id="d400b-194">NAM</span></span> |

<span data-ttu-id="d400b-p119">**Nota**: le proprietà **PreferredDataLocation** e **MailboxRegion** sono stringhe con alcun controllo degli errori. Se si immette un valore non valido (ad esempio NAN) della cassetta postale verrà inserita nel livello geografico predefinito.</span><span class="sxs-lookup"><span data-stu-id="d400b-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="d400b-197">Visualizzazione Geos disponibili configurati nell'organizzazione Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d400b-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="d400b-198">Per visualizzare l'elenco dei Geos configurati nell'organizzazione Exchange Online, eseguire il seguente comando in Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d400b-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="d400b-199">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="d400b-199">The output of the command looks like this:</span></span>

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

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="d400b-200">Individuare la posizione geografica di una cassetta postale</span><span class="sxs-lookup"><span data-stu-id="d400b-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="d400b-201">Il cmdlet **Get-Mailbox** in Exchange Online PowerShell vengono visualizzate le proprietà relative al livello geografico seguenti per le cassette postali:</span><span class="sxs-lookup"><span data-stu-id="d400b-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="d400b-202">**Database**: le prime 3 lettere del nome del database corrispondono al codice Geo, che fornisce le informazioni della cassetta postale in cui attualmente si trova.</span><span class="sxs-lookup"><span data-stu-id="d400b-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="d400b-203">**MailboxRegion**: specificare il codice Geo è stato impostato dall'amministratore (sincronizzato da **PreferredDataLocation** in Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="d400b-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="d400b-204">**MailboxRegionLastUpdateTime**: indica MailboxRegion dell'ultimo aggiornamento (automaticamente o manualmente).</span><span class="sxs-lookup"><span data-stu-id="d400b-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="d400b-205">Per visualizzare le proprietà per una cassetta postale, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="d400b-206">Ad esempio, per visualizzare le informazioni di livello geografico per chris@contoso.onmicrosoft.com cassetta postale, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="d400b-207">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="d400b-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="d400b-208">Se il codice Geo nel nome del database non corrisponde a quello **MailboxRegion** , la cassetta postale verrà spostata in Geo specificato dal valore **MailboxRegion** (Exchange Online Cerca una mancata corrispondenza tra i valori delle proprietà).</span><span class="sxs-lookup"><span data-stu-id="d400b-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="d400b-209">Spostare una cassetta postale cloud esistente a un livello geografico specifico</span><span class="sxs-lookup"><span data-stu-id="d400b-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="d400b-210">Utilizzare il cmdlet **Get-MsolUser** e **Set-MsolUser** nel modulo Azure Active Directory per Windows PowerShell per visualizzare o specificare geografica in cui verrà archiviata cassetta postale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d400b-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="d400b-211">Per visualizzare il valore **PreferredDataLocation** per un utente, utilizzare la seguente sintassi in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d400b-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="d400b-212">Ad esempio, per visualizzare il valore **PreferredDataLocation** michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="d400b-213">L'output del comando avrà questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="d400b-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="d400b-214">Per modificare il valore **PreferredDataLocation** per un oggetto utente solo cloud, utilizzare la sintassi seguente in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d400b-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="d400b-215">Ad esempio, per impostare il valore **PreferredDataLocation** per l'Unione europea (EUR) per michelle@contoso.onmicrosoft.com utente, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="d400b-216">**Note**:</span><span class="sxs-lookup"><span data-stu-id="d400b-216">**Notes**:</span></span>

- <span data-ttu-id="d400b-p120">Come accennato in precedenza per gli oggetti utente sincronizzato da Active Directory locale, è possibile utilizzare questa procedura. È necessario modificare il valore **PreferredDataLocation** utilizzando AAD Connect. Per ulteriori informazioni, vedere [connettersi Azure Active Directory sync: configurare la posizione dei dati preferito per le risorse di Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="d400b-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="d400b-220">Il tempo impiegato per spostare una cassetta postale dipende da diversi fattori:</span><span class="sxs-lookup"><span data-stu-id="d400b-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="d400b-221">La dimensione e tipo di cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="d400b-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="d400b-222">Il numero di cassette postali da spostare.</span><span class="sxs-lookup"><span data-stu-id="d400b-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="d400b-223">Disponibilità delle risorse di spostamento.</span><span class="sxs-lookup"><span data-stu-id="d400b-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="d400b-224">Spostamento disabilitate le cassette postali presenti conservazione per controversia legale</span><span class="sxs-lookup"><span data-stu-id="d400b-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="d400b-p121">Disabilitate le cassette postali conservazione per controversia legale che vengono conservate per scopi non possono essere spostati modificando i valori **PreferredDataLocation** nello stato disabilitato eDiscovery. Per spostare una cassetta postale disabilitata sulla conservazione per controversia legale:</span><span class="sxs-lookup"><span data-stu-id="d400b-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="d400b-227">Assegnare temporaneamente una licenza per la cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="d400b-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="d400b-228">Modificare **PreferredDataLocation**.</span><span class="sxs-lookup"><span data-stu-id="d400b-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="d400b-229">Rimuovere la licenza dalla cassetta postale dopo che è stata spostata in Geo selezionato per rimetterlo in stato disabilitato.</span><span class="sxs-lookup"><span data-stu-id="d400b-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="d400b-230">Creare nuove cassette postali cloud in un determinato livello geografico</span><span class="sxs-lookup"><span data-stu-id="d400b-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="d400b-231">Per creare una nuova cassetta postale in un determinato livello geografico, è necessario eseguire una della procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="d400b-232">Configurare il valore **PreferredDataLocation** come descritto nella precedente sezione *prima* viene creata la cassetta postale di Exchange Online (ad esempio configurando il valore **PreferredDataLocation** su un utente prima di assegnare una licenza).</span><span class="sxs-lookup"><span data-stu-id="d400b-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="d400b-233">Assegnare una licenza contemporaneamente che si imposta il valore **PreferredDataLocation** .</span><span class="sxs-lookup"><span data-stu-id="d400b-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="d400b-234">Per creare un nuovo solo cloud con licenza utente (non AAD connessione sincronizzati) in un livello geografico specifico, utilizzare la sintassi seguente in Azure Active Directory PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d400b-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="d400b-235">In questo esempio crea un nuovo account utente per Elizabeth Brunner con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="d400b-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="d400b-236">Nome dell'entità utente: ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d400b-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="d400b-237">Nome: Elizabeth</span><span class="sxs-lookup"><span data-stu-id="d400b-237">First name: Elizabeth</span></span>

- <span data-ttu-id="d400b-238">Cognome: Brunner</span><span class="sxs-lookup"><span data-stu-id="d400b-238">Last name: Brunner</span></span>

- <span data-ttu-id="d400b-239">Nome visualizzato Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="d400b-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="d400b-240">Password: generato casualmente e illustrate nei risultati del comando (dal momento che non viene utilizzato il parametro *Password* )</span><span class="sxs-lookup"><span data-stu-id="d400b-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="d400b-241">Licenza: contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="d400b-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="d400b-242">Percorso di 3: Australia (Australia)</span><span class="sxs-lookup"><span data-stu-id="d400b-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="d400b-243">Per ulteriori informazioni sulla creazione di nuovi account utente e la ricerca di valori LicenseAssignment in PowerShell di Azure Active Directory, vedere [creare gli account utente con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) e [le licenze di visualizzazione e dei servizi con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span><span class="sxs-lookup"><span data-stu-id="d400b-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="d400b-p122">Se si utilizza Exchange PowerShell per abilitare una cassetta postale e la cassetta postale da creare direttamente in Geo specificato in **PreferredDataLocation**è necessario, è necessario utilizzare un cmdlet di Exchange Online, ad esempio **Enable-Mailbox** o **New-Mailbox** direttamente in base al servizio cloud. Se si utilizza il cmdlet di Exchange locale **Enable-RemoteMailbox** , verrà creata la cassetta postale in Geo predefinito.</span><span class="sxs-lookup"><span data-stu-id="d400b-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="d400b-246">Esistenti incorporato cassette postali locali in un determinato livello geografico</span><span class="sxs-lookup"><span data-stu-id="d400b-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="d400b-247">È possibile utilizzare gli strumenti di onboarding standard e i processi per eseguire la migrazione di una cassetta postale da un'organizzazione di Exchange locale a Exchange Online, tra cui il [dashboard di migrazione in EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)e il cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) di Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d400b-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="d400b-p123">Il primo passaggio consiste nel verificare che un oggetto utente esiste per ciascuna cassetta postale essere onboarded e verificare che il valore **PreferredDataLocation** corretto è configurato in Azure Active Directory. Gli strumenti di on-boarding rispettano il valore **PreferredDataLocation** e verranno eseguita la migrazione di cassette postali direttamente a Geo specificato.</span><span class="sxs-lookup"><span data-stu-id="d400b-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="d400b-250">In alternativa, è possibile utilizzare la procedura seguente per le cassette postali incorporate direttamente in un Geo specifico utilizzando il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d400b-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="d400b-p124">Verificare l'oggetto utente per ciascuna cassetta postale da onboarded e che **PreferredDataLocation** sia impostata sul valore desiderato in Azure Active Directory. Il valore di **PreferredDataLocation** verrà sincronizzato con l'attributo **MailboxRegion** dell'oggetto utente di posta elettronica corrispondente in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="d400b-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="d400b-253">Connettersi direttamente a satellitari specifico Geo utilizzando le istruzioni di connessione da più indietro in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="d400b-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="d400b-254">In Exchange Online PowerShell, archiviare le credenziali di amministratore locale che viene utilizzato per eseguire una migrazione delle cassette postali in una variabile eseguendo il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d400b-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="d400b-255">In Exchange Online PowerShell, creare un nuovo **New-MoveRequest** simile a quello riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d400b-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="d400b-256">Ripetere il passaggio #4 per ogni cassetta postale che è necessario eseguire la migrazione di Exchange locale a satellitari Geo attualmente si è connessi.</span><span class="sxs-lookup"><span data-stu-id="d400b-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="d400b-257">Se è necessario eseguire la migrazione di cassette postali aggiuntive a un altro satellitari Geo, ripetere i passaggi da 2 a 4 per ogni satellitari specifico Geo.</span><span class="sxs-lookup"><span data-stu-id="d400b-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="d400b-258">Creazione di report multi-Geo</span><span class="sxs-lookup"><span data-stu-id="d400b-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="d400b-p125">**Report di utilizzo della Multi-Geo** nell'interfaccia di amministrazione di Office 365 viene visualizzato il numero di utenti da Geo. Il rapporto viene visualizzato distribuzione degli utenti per il mese corrente e vengono forniti dati cronologici per gli ultimi 6 mesi.</span><span class="sxs-lookup"><span data-stu-id="d400b-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
