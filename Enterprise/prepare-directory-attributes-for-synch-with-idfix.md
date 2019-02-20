---
title: Preparare gli attributi della directory per la sincronizzazione a Office 365 utilizzando lo strumento IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Vengono fornite istruzioni sull'utilizzo di IdFix per preparare e pulire la directory locale prima di eseguire la sincronizzazione con Office 365.
ms.openlocfilehash: cdfee8178f731d20c799f550d1dacb0a04a72cae
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085095"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparare gli attributi della directory per la sincronizzazione a Office 365 utilizzando lo strumento IdFix
Questo argomento contiene istruzioni dettagliate sull'esecuzione dello strumento IdFix, alcuni errori comuni che è possibile riscontrare, correzioni consigliate, esempi e procedure consigliate per le operazioni da eseguire se si dispone di un numero elevato di errori.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correzione degli errori nella directory utilizzando l'interfaccia grafica di IdFix
[Eseguire lo strumento IdFix di Office 365](install-and-run-idfix.md) per cercare i problemi nella directory e quindi correggere gli errori nella GUI come descritto in questo argomento. Se lo strumento restituisce una tabella vuota, non sono stati individuati errori. Se nella directory sono presenti molti problemi, è possibile che si verifichi un problema quando lo strumento restituisce gli errori. Un modo per risolvere questo errore consiste nel correggere tutti gli errori di un tipo e quindi passare al tipo successivo. 
  
1. Prima di iniziare ad apportare modifiche, esaminare i consigli presentati da IdFix.
    
2. Scorrere l'elenco degli errori restituiti da IdFix. È possibile ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore. Se a un singolo attributo viene associato più di un errore, gli errori vengono uniti in una sola riga. Se possibile, IdFix presenta una raccomandazione per una correzione nella colonna **UPDATE**. La correzione è basata su un controllo di altri attributi associati a un oggetto. Mentre questi, in genere, sono meglio di quelli già presenti nella directory, solo l'utente può decidere cosa è realmente accurato. 
    
3. Se IdFix ha un suggerimento per una correzione per un errore di duplicazione, la correzione è identificata da uno dei tre flag all'inizio del valore nella colonna **Update** , ad esempio `[E]john.doe@contoso.com`. Se si accetta il suggerimento, quando si applica la modifica, il contrassegno non verrà inserito nella directory. Solo il valore che segue il flag del suggerimento verrà applicato, ad esempio `john.doe@contoso.com`,. Se si desidera accettare il suggerimento, selezionare l'azione corrispondente dalla colonna **azione** . I flag indicano azioni come indicato di seguito: 
    
 - **[C]** Azione suggerita **COMPLETE**. Il valore non deve essere modificato.
    
 - **[E]** Azione suggerita **EDIT**. Il valore deve essere modificato per evitare conflitti con un altro valore nella directory.
    
 - **[R]** Azione suggerita **REMOVE**. Il valore è un proxy SMTP su un oggetto non abilitato alla posta e probabilmente può essere rimosso in sicurezza.
    
4. Dopo aver letto e compreso gli errori, aggiornare la voce nella colonna **Aggiorna** con le modifiche e quindi nella colonna **azione** Selezionare gli elementi che si desidera IdFix per implementare la modifica. Ad esempio, due utenti possono essere `proxyAddress` identificati come duplicati. Solo un utente può utilizzare il `proxyAddress` per il recapito della posta. Per risolvere questo errore, contrassegnare la colonna **azione** **completa** per l'utente con il valore corretto e contrassegnare la colonna **azione** **Rimuovi** per l'altro utente. Questo consente di `proxyAddress` rimuovere l'attributo dall'utente a cui `proxyAddress` non appartiene e non apporta alcuna modifica all'utente per il quale `proxyAddress` è corretta.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Errori comuni e correzioni rilevati da IdFix
Nella seguente tabella vengono descritti gli errori rilevati da IdFix, vengono fornite le risoluzioni più comuni dalla strumento e, in alcuni casi, gli esempi sulla loro risoluzione.

|**ERRORE**|**Descrizione del tipo di errore**|**Correzione suggerita**|**Esempio**|
|:-----|:-----|:-----|:-----|
|**carattere** | Caratteri non validi. Il valore contiene un carattere non valido. | La risoluzione suggerita per l'errore visualizzato nella colonna **UPDATE** mostra il valore con il carattere non valido rimosso.  <br/> | Uno spazio finale alla fine di un indirizzo di posta elettronica valido è un carattere illegale, ad esempio:  <br/> " `user@contoso.com` "  <br/> Uno spazio iniziale all'inizio di un indirizzo di posta elettronica valido è un carattere illegale, ad esempio:  <br/> " ` user@contoso.com `"  <br/>  Il `ú` carattere è un carattere non valido. |
|**duplicazione** | Voce duplicata. Il valore ha un duplicato all'interno dell'ambito della query. Tutti i valori duplicati verranno visualizzati come errori. | Modificare o rimuovere i valori per eliminare i duplicati. Lo strumento non fornirà una correzione suggerita di duplicati. Al contrario, è necessario scegliere quale dei due o più duplicati è corretto ed eliminare la voce o le voci duplicate. ||
|**formato** | Errore di formattazione. Il valore viola i requisiti di formato per l'utilizzo dell'attributo. | L'aggiornamento suggerito mostrerà il valore con caratteri non validi rimossi. Se non sono presenti caratteri non validi, Update e Value saranno uguali. Devi decidere quello che ti interessa veramente dell'aggiornamento. Lo strumento non fornirà una correzione suggerita per tutti gli errori di formattazione. | Ad esempio, gli indirizzi SMTP devono essere conformi alle specifiche RFC 2822 e mailNickName non possono iniziare o terminare con un punto. Per ulteriori informazioni sui requisiti di formato per gli attributi delle directory, vedere la sezione relativa alla preparazione degli oggetti directory e dell'attributo in preparare il provisioning [degli utenti tramite la sincronizzazione della directory con Office 365](prepare-for-directory-synchronization.md) |
|topleveldomain  <br/> |Dominio di primo livello. Questo si applica ai valori soggetti alla formattazione [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) . Se il dominio di primo livello non è instradabile su Internet, verrà identificato come un errore. Ad esempio, un indirizzo SMTP che termina con. local non è instradabile su Internet e potrebbe causare questo errore. |Modificare il valore in un dominio instradabile su Internet `.com` , `.net`ad esempio o. | Passare `myaddress@fourthcoffee.local` a `fourthcoffee.com` un altro dominio instradabile su Internet.  <br/> Per istruzioni, vedere [come preparare un dominio non instradabile (ad esempio, dominio locale) per la sincronizzazione della directory](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Errore di parte del dominio. Questo vale per valori soggetti a formattazione RFC 2822. Se la parte di dominio del valore non è valida e non soddisfa la formattazione RFC 2822, viene generata. | Modificare il valore in una conforme a RFC 2822. Ad esempio, assicurarsi che non contenga spazi o caratteri non validi. | Passare `myaddress@fourth coffee.com` a `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Errore della parte locale. Questo vale per valori soggetti a formattazione RFC 2822. Se la parte locale del valore non è valida e non soddisfa la formattazione RFC 2822, viene generata. |Modificare il valore in una conforme a RFC 2822. Ad esempio, assicurarsi che non contenga spazi o caratteri non validi. |Passare `my"work"address@fourthcoffee.com` a `myworkaddress@fourthcoffee.com`. |
|**lunghezza** | Errore di lunghezza. Il valore viola il limite di lunghezza per l'attributo. In genere, si verifica quando viene modificato lo schema di directory.  | L'aggiornamento consigliato da IdFix tronca il valore alla lunghezza accettabile.  <br/> Tenere presente che questo può produrre risultati indesiderati. È necessario rivedere la soluzione suggerita e, se necessario, modificarla prima di fare clic su **Applica**. ||
|**vuoto**  | Errore null o vuoto. Il valore viola la restrizione null per gli attributi da sincronizzare. Solo alcuni attributi devono contenere un valore. | Se possibile, l'aggiornamento suggerito utilizza altri valori per poter generare un probabile sostituto. ||
|**mailmatch** | Questo si applica a Office 365 dedicato solo. Il valore non corrisponde all'attributo mail. | L'aggiornamento consigliato sarà il valore dell'attributo mail preceduto da "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operazioni eseguibili utilizzando IdFix
Per correggere un errore, è possibile selezionare un'opzione nell'elenco a discesa **azione** . Nella tabella seguente vengono descritte le operazioni di **azione** che è possibile eseguire sugli attributi utilizzando lo strumento IdFix. Se si lascia vuota la colonna **azione** , lo strumento IdFix non eseguirà alcuna azione su quell'errore specifico nella directory. 

|**AZIONE**|**Descrizione azione**|**Esempio**|
|:-----|:-----|:-----|
|**COMPLETE** | Il valore originale è accettabile e non deve essere modificato nonostante sia stato identificato come errore. | Due utenti hanno un proxyAddress identificato come duplicato. Solo uno può essere utilizzato per il recapito della posta. Contrassegnare l'utente con il valore corretto come **COMPLETE**. |
|**RIMUOVERE** | Il valore dell'attributo verrà eliminato dall'oggetto di origine. Nel caso di un attributo multivalore, ad esempio `proxyAddresses`, viene eliminato solo il singolo valore visualizzato. | Due utenti hanno un proxyAddress identificato come duplicato. Solo uno può essere utilizzato per il recapito della posta. Contrassegnare l'utente con il valore duplicato come **REMOVE**. |
|**MODIFICA** | Le informazioni contenute nella colonna **Update** verranno utilizzate per modificare il valore dell'attributo. Se un valore di **aggiornamento** valido è stato suggerito da IdFix, fare clic su **modifica** nella colonna **azione** e passare all'errore successivo. Se non si è interessati al suggerimento, digitarne uno nuovo nella colonna **Update** e quindi, nella colonna **azione** , selezionare **modifica**. ||
|**ANNULLARE** | Questa opzione è disponibile solo se sei stato ripristinato da un registro di transazioni. Se selezioni **ANNULLA**, il valore dell'attributo verrà ripristinato al valore originale. ||
|**FAIL** | Questo valore viene restituito solo se un valore di **aggiornamento** ha un conflitto sconosciuto con le regole di servizi di dominio Active Directory. In questo caso, è possibile modificare di nuovo il valore nella colonna **Update** , se si conosce il problema. Potrebbe essere necessario analizzare i valori nell'oggetto utilizzando ADSI Edit. Per ulteriori informazioni, vedere [ADSI Edit (ADSIEdit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Dopo aver scelto il valore **ACTION** per un errore o un batch di errori, fare clic su **Applica**. Quando fa clic su **Applica**, lo strumento apporta le modifiche nella directory. È possibile fornire delle correzioni per più errori prima di fare clic su **Applica** e IdFix le modificherà tutte contemporaneamente.

Eseguire di nuovo IdFix per assicurarsi che le correzioni apportate non introducano nuovi errori. È possibile ripetere questi passaggi tutte le volte che è necessario. È consigliabile passare un paio di volte al processo prima di eseguire la sincronizzazione.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Modifica del set di regole utilizzato da IdFix
Per impostazione predefinita, in IdFix viene utilizzato il set di regole multi-tenant per testare le voci nella directory. Si tratta del set di regole appropriato per la maggior parte dei clienti di Office 365 =. Tuttavia, se si è un cliente di Office 365 dedicato o ITAR (International Traffic on Arms Regulations), è possibile configurare IdFix per utilizzare il set di regole dedicato. Se non si è certi del tipo di cliente, è possibile ignorare questo passaggio. Per impostare il set di regole su dedicato, fare clic sull'icona dell'ingranaggio sulla barra dei menu e quindi fare clic su **dedicato**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Modifica dell'ambito della ricerca utilizzata da IdFix
Per impostazione predefinita, IdFix ricerca l'intera directory. Se si desidera, è possibile configurare lo strumento per la ricerca di una sottostruttura specifica. A tale scopo, nella barra dei menu, fare clic sull'icona Filter e immettere una sottostruttura valida.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Ripristino delle modifiche utilizzando l'interfaccia grafica di IdFix
Ogni volta che si fa clic su **applica** per applicare le modifiche, lo strumento IdFix crea un file separato denominato log delle transazioni che elenca le modifiche appena apportate. È possibile utilizzare il registro delle transazioni per eseguire il rollback solo di quelle modifiche presenti nel log più recente in caso di errore. Se si commette un errore durante l'aggiornamento, è possibile annullare le modifiche applicate più di recente facendo clic su **Annulla**. Quando si fa clic su **Annulla**, IdFix utilizza il registro delle transazioni per eseguire il rollback solo delle modifiche presenti nel log delle transazioni più recente. Per ulteriori informazioni sull'utilizzo del log delle transazioni, vedere [Reference: Office 365 IdFix Transaction Log](idfix-transaction-log.md).