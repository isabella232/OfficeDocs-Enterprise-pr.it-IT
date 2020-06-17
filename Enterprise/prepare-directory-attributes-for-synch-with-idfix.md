---
title: Preparare gli attributi della directory per la sincronizzazione con Microsoft 365 mediante lo strumento IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Vengono fornite istruzioni sull'utilizzo di IdFix per preparare e pulire la directory locale prima di eseguire la sincronizzazione con Microsoft 365.
ms.openlocfilehash: cae1df048e58c65a3203ea39df18beb986adb0c8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736004"
---
# <a name="prepare-directory-attributes-for-synchronization-with-microsoft-365-by-using-the-idfix-tool"></a>Preparare gli attributi della directory per la sincronizzazione con Microsoft 365 mediante lo strumento IdFix

*Questo articolo si applica sia a Microsoft 365 Enterprise che a Office 365 Enterprise.*

Questo argomento contiene istruzioni dettagliate sull'esecuzione dello strumento IdFix, alcuni errori comuni che è possibile riscontrare, correzioni consigliate, esempi e procedure consigliate per le operazioni da eseguire se si dispone di un numero elevato di errori.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correzione degli errori nella directory utilizzando l'interfaccia grafica di IdFix

[Eseguire lo strumento Microsoft 365 IdFix](install-and-run-idfix.md) per cercare i problemi nella directory e quindi correggere gli errori nella GUI come descritto in questo argomento. Se lo strumento restituisce una tabella vuota, non vengono individuati errori. Nel caso vi siano molti problemi nella directory, questa potrebbe sovraccaricarsi quando lo strumento restituisce gli errori. Un modo per evitare questo problema è risolvere prima gli errori dello stesso tipo e poi quelli diversi. 
  
1. Prima di iniziare ad apportare modifiche, esaminare i consigli presentati da IdFix.
    
2. Look over the list of errors that IdFix has returned. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types. If more than one error is associated with a single attribute, the errors are combined into one row. Where possible, IdFix presents a recommendation for a fix in the **UPDATE** column. The fix is based on a check of other attributes associated with an object. While these are usually better than what is already in the directory, only you can decide what is really accurate. 
    
3. Se IdFix ha un suggerimento per una correzione per un errore di duplicazione, la correzione è identificata da uno dei tre flag all'inizio del valore nella colonna **Update** , ad esempio `[E]john.doe@contoso.com` . Se il suggerimento viene accettato, quando si applica la modifica, il flag non viene inserito nella directory. Solo il valore che segue il flag del suggerimento verrà applicato, ad esempio, `john.doe@contoso.com` . Se si desidera accettare il suggerimento, selezionare l'azione corrispondente dalla colonna**ACTION**. I flag indicano le operazioni nel modo seguente: 
    
 - **[C]** Suggested action **COMPLETE**. The value does not need to be edited.
    
 - **[E]** Suggested action **EDIT**. The value should be changed to avoid conflict with another value in the directory.
    
 - **[R]** Suggested action **REMOVE**. The value is an SMTP proxy on a non-mail enabled object and can probably be safely removed.
    
4. Dopo aver letto e compreso gli errori, aggiornare la voce nella colonna **Aggiorna** con le modifiche e quindi nella colonna **azione** Selezionare gli elementi che si desidera IdFix per implementare la modifica. Ad esempio, due utenti possono essere `proxyAddress` identificati come duplicati. Solo un utente può utilizzare il `proxyAddress` per il recapito della posta. Per correggere questo problema, contrassegnare la colonna **ACTION** come **COMPLETE** per l'utente con il valore corretto e contrassegnare la colonna **ACTION** come **REMOVE** per l'altro utente. Questo consente di rimuovere l' `proxyAddress` attributo dall'utente a cui `proxyAddress` non appartiene e non apporta alcuna modifica all'utente per il quale `proxyAddress` è corretta.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Errori comuni e correzioni rilevati da IdFix
Nella seguente tabella vengono descritti gli errori rilevati da IdFix, vengono fornite le risoluzioni più comuni dalla strumento e, in alcuni casi, gli esempi sulla loro risoluzione.

|**ERRORE**|**Descrizione del tipo di errore**|**Correzione suggerita**|**Esempio**|
|:-----|:-----|:-----|:-----|
|**carattere** | Illegal characters. The value contains a character which is invalid. | La risoluzione suggerita per l'errore visualizzato nella colonna **UPDATE** mostra il valore con il carattere non valido rimosso.  <br/> | Uno spazio finale alla fine di un indirizzo di posta elettronica valido è un carattere illegale, ad esempio:  <br/> " `user@contoso.com` "  <br/> Uno spazio iniziale all'inizio di un indirizzo di posta elettronica valido è un carattere illegale, ad esempio:  <br/> " ` user@contoso.com `"  <br/>  Il `ú` carattere è un carattere non valido. |
|**duplicato** | Duplicate entry. The value has a duplicate within the scope of the query. All duplicate values will be displayed as errors. | Edit or remove values to eliminate duplication. The tool will not provide a suggested fix for duplicates. Instead, you must choose which of the two or more duplicates is the correct one and delete the duplicate entry or entries. ||
|**formato** | Formatting error. The value violates the format requirements for the attribute usage. | The suggested Update will show the value with any invalid characters removed. If there are no invalid characters the Update and Value will appear the same. You need to determine what you really want in the Update. The tool will not provide a suggested fix for all formatting errors. | Ad esempio, gli indirizzi SMTP devono soddisfare lo standard RFC 2822 e mailNickName non può iniziare o terminare con un punto. Per ulteriori informazioni sui requisiti di formato per gli attributi delle directory, vedere la sezione relativa alla preparazione degli oggetti directory e dell'attributo in [preparare il provisioning degli utenti tramite la sincronizzazione della directory con Microsoft 365](prepare-for-directory-synchronization.md). |
|TopLevelDomain  <br/> |Dominio di livello superiore. Questo si applica ai valori soggetti alla formattazione [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Se il dominio di livello superiore non è instradabile su Internet, l'evento viene identificato come errore. Ad esempio, un indirizzo SMTP che termina in .local non è instradabile su Internet e causa l'errore. |Modificare il valore in un dominio instradabile su Internet, ad esempio `.com` o `.net` . | Passare `myaddress@fourthcoffee.local` a `fourthcoffee.com` un altro dominio instradabile su Internet.  <br/> Per istruzioni, vedere [come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**partedominio** | Domain part error. This applies to values subject to RFC 2822 formatting. If the domain portion of the value is invalid and does not comply with RFC 2822 this will be generated. | Modificare il valore su uno che soddisfa la formattazione RFC 2822. Ad esempio, assicurarsi che non contenga spazi o caratteri non validi. | Passare `myaddress@fourth coffee.com` a `myaddress@fourthcoffee.com` . |
|**domainpart_localpart** | Local-part error. This applies to values subject to RFC 2822 formatting. If the local-part of the value is invalid and does not comply with RFC 2822 this will be generated. |Modificare il valore su uno che soddisfa la formattazione RFC 2822. Ad esempio, assicurarsi che non contenga spazi o caratteri non validi. |Passare `my"work"address@fourthcoffee.com` a `myworkaddress@fourthcoffee.com` . |
|**lunghezza** | Length error. The value violates the length limit for the attribute. This is most commonly encountered when the directory schema has been altered.  | L'aggiornamento consigliato da IdFix tronca il valore alla lunghezza accettabile.  <br/> Be aware that this may produce undesired results. You should review the suggested fix and change it if necessary before you click **Apply**. ||
|**vuoto**  | Blank or null error. The value violates the null restriction for attributes to be synchronized. Only a few attributes must contain a value. | Se possibile, l'aggiornamento suggerito utilizza altri valori per poter generare un probabile sostituto. ||
|**mailmatch** | Questo si applica a Microsoft 365 dedicato solo. Il valore non corrisponde all'attributo della posta. | L'aggiornamento consigliato sarà il valore dell'attributo mail preceduto da "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operazioni eseguibili utilizzando IdFix
Per correggere un errore, è possibile selezionare un'opzione dall'elenco a discesa **ACTION**. Nella seguente tabella vengono descritte le operazioni **ACTION** che è possibile eseguire sugli attributi utilizzando lo strumento IdFix. Se la colonna **ACTION** viene lasciata vuota, lo strumento IdFix non effettua nessuna azione sull'errore specifico nella directory. 

|**AZIONE**|**Descrizione azione**|**Esempio**|
|:-----|:-----|:-----|
|**COMPLETA** | Il valore originale è accettabile e non deve essere modificato nonostante sia stato identificato come errore. | Two users have a proxyAddress identified as duplicate. Only one can use the value for mail delivery. Mark the user with the correct value as **COMPLETE**. |
|**RIMUOVERE** | Il valore dell'attributo verrà eliminato dall'oggetto di origine. Nel caso di un attributo multivalore, ad esempio, viene `proxyAddresses` eliminato solo il singolo valore visualizzato. | Two users have a proxyAddress identified as duplicate. Only one can use the value for mail delivery. Mark the user with the duplicate value as **REMOVE**. |
|**MODIFICA** | Le informazioni contenute nella colonna **UPDATE** vengono utilizzate per modificare il valore dell'attributo. Se IdFix ha suggerito un valore **UPDATE** valido, dalla colonna **ACTION**, selezionare **EDIT** e procedere con l'errore successivo. Se non si è interessati al suggerimento, digitarne uno nuovo nella colonna **Update** e quindi, nella colonna **azione** , selezionare **modifica**. ||
|**ANNULLARE** | This option is only available if you have restored from a transaction log. If you select **UNDO**, the attribute value will be restored to the original value. ||
|**FAIL** | Tale valore viene restituito solo se un valore **UPDATE** presenta un conflitto sconosciuto con regole AD DS. In questo caso, se si conosce l'errore, è possibile modificare nuovamente il valore nella colonna **UPDATE**. Potrebbe essere necessario analizzare i valori nell'oggetto utilizzando ADSI Edit. Per ulteriori informazioni, vedere [ADSI Edit (ADSIEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

After choosing an **ACTION** for an error or a batch of errors, click **Apply**. When you click **Apply**, the tool makes the changes in the directory. You can provide fixes for multiple errors before you click **Apply** and IdFix will change them all at the same time.

Eseguire di nuovo IdFix per assicurarsi che le correzioni apportate non introducano nuovi errori. È possibile ripetere la procedura tutte le volte che è necessario. È consigliabile ripetere il processo più volte prima di eseguire la sincronizzazione.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Modifica del set di regole utilizzato da IdFix
Per impostazione predefinita, IdFix utilizza il set di regole multi-tenant per controllare le voci nella directory. Si tratta del set di regole appropriato per la maggior parte dei clienti di Microsoft 365. Tuttavia, se si è un cliente di Microsoft 365 dedicato o ITAR (International Traffic on Arms Regulations), è possibile configurare IdFix per utilizzare il set di regole dedicato. Se non si sa a quale tipologia di cliente si appartiene, è possibile saltare questo passaggio. Per impostare il set di regole su Dedicated, fare clic sull'icona a forma di ingranaggio nella barra dei menu e fare clic su **Dedicated**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Modifica dell'ambito della ricerca utilizzata da IdFix
By default, IdFix searches the entire directory. If you want, you can configure the tool to search a specific subtree instead. To do this, in the menu bar, click the Filter icon and enter a valid subtree.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Ripristino delle modifiche utilizzando l'interfaccia grafica di IdFix
Tutte le volte che si seleziona **Applica** per applicare le modifiche, lo strumento IdFix crea un file separato denominato registro di transazione che elenca le modifiche appena effettuate. In caso di errore, è possibile utilizzare il registro di transazione per ripristinare solo le modifiche presenti nel registro più recente. In caso di errore durante l'aggiornamento, è possibile annullare le modifiche recentemente applicate selezionando **Annulla**. Quando scegli **Annulla**, IdFix utilizza il registro di transazione per ripristinare solo le modifiche presenti nel registro più recente. Per ulteriori informazioni sull'utilizzo del log delle transazioni, vedere [Microsoft 365 IdFix Transaction Log](idfix-transaction-log.md).

## <a name="next-step"></a>Passaggio successivo

[Configurare la sincronizzazione della directory](set-up-directory-synchronization.md)
