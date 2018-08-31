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
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: Vengono fornite istruzioni sull'utilizzo di IdFix per preparare e pulire la directory locale prima della sincronizzazione a Office 365.
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541372"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>Preparare gli attributi della directory per la sincronizzazione a Office 365 utilizzando lo strumento IdFix
In questo argomento è incluse istruzioni dettagliate su come eseguire lo strumento IdFix, alcuni errori comuni che possono verificarsi, suggerito correzioni, esempi e procedure consigliate per gli elementi da eseguire se si dispone di un numero elevato di errori.
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>Correzione degli errori nella directory utilizzando l'interfaccia grafica di IdFix
[Eseguire lo strumento IdFix di Office 365](install-and-run-idfix.md) per la ricerca dei problemi nella directory e quindi correggere gli errori nell'interfaccia utente come descritto in questo argomento. Se la restituzione di una tabella vuota tramite lo strumento, sono stati rilevati senza errori. Se non esistono numerosi problemi nella directory, può risultare complessa quando lo strumento restituisce gli errori. Un modo per affrontare questo è per correggere tutti gli errori di un tipo di e quindi spostare il tipo di successivo. 
  
1. Prima di iniziare ad apportare modifiche, esaminare i consigli presentati da IdFix.
    
2. Scorrere l'elenco degli errori restituiti da IdFix. È possibile ordinare gli errori per tipo facendo clic su **ERROR** all'inizio della colonna che elenca i tipi di errore. Se a un singolo attributo viene associato più di un errore, gli errori vengono uniti in una sola riga. Se possibile, IdFix presenta una raccomandazione per una correzione nella colonna **UPDATE**. La correzione è basata su un controllo di altri attributi associati a un oggetto. Mentre questi, in genere, sono meglio di quelli già presenti nella directory, solo l'utente può decidere cosa è realmente accurato. 
    
3. Se lo strumento IdFix ha un suggerimento di correggere un errore di duplicazione, la correzione è identificata da uno dei tre contrassegni all'inizio del valore nella colonna **UPDATE** , ad esempio `[E]john.doe@contoso.com`. Se si accetta il suggerimento quando si applica la modifica che il flag non verrà inserito nella directory. Solo il valore seguente suggerimento Contrassegno applicato, ad esempio `john.doe@contoso.com`. Se si desidera accettare il suggerimento, selezionare l'azione corrispondente nella colonna **azione** . I flag indicano azioni nel modo seguente: 
    
 - **[C]** Azione suggerita **COMPLETE**. Il valore non deve essere modificato.
    
 - **[E]** Azione suggerita **EDIT**. Il valore deve essere modificato per evitare conflitti con un altro valore nella directory.
    
 - **[R]** Azione suggerita **REMOVE**. Il valore è un proxy SMTP su un oggetto non abilitato alla posta e probabilmente può essere rimosso in sicurezza.
    
4. Una volta è stato letto e compreso gli errori, aggiornare la voce nella colonna **aggiornamento** con le modifiche apportate e quindi in **azione** colonna selezionare gli elementi da IdFix da eseguire per implementare la modifica. Ad esempio, due utenti possono avere un `proxyAddress` identificato come duplicato. Solo un utente può utilizzare il `proxyAddress` per il recapito della posta. Per risolvere questo problema, contrassegnare la colonna **azione** **completa** per l'utente con il valore corretto e contrassegnare la colonna **azione** **rimuovere** per l'altro utente. Consente di rimuovere il `proxyAddress` attributo da parte dell'utente a cui questo `proxyAddress` non appartiene e non apporta alcuna modifica all'utente per il quale si `proxyAddress` sia corretto.
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>Errori comuni e correzioni rilevati da IdFix
Nella seguente tabella vengono descritti gli errori rilevati da IdFix, vengono fornite le risoluzioni più comuni dalla strumento e, in alcuni casi, gli esempi sulla loro risoluzione.

|**ERRORE**|**Descrizione del tipo di errore**|**Correzione suggerita**|**Esempio**|
|:-----|:-----|:-----|:-----|
|**carattere** | Caratteri non validi. Il valore contiene un carattere non valido. | La risoluzione suggerita per l'errore visualizzato nella colonna **UPDATE** mostra il valore con il carattere non valido rimosso.  <br/> | Uno spazio finale alla fine di un indirizzo di posta elettronica valido è un carattere non valido, ad esempio:  <br/> " `user@contoso.com` "  <br/> Spazio iniziale all'inizio di un indirizzo di posta elettronica valido è un carattere non valido, ad esempio:  <br/> " ` user@contoso.com `"  <br/>  Il `ú` carattere è un carattere non valido. |
|**duplicazione** | Voce duplicata. Il valore ha un duplicato all'interno dell'ambito della query. Tutti i valori duplicati verranno visualizzati come errori. | Modificare o rimuovere i valori per eliminare i duplicati. Lo strumento non fornirà una correzione suggerita di duplicati. Al contrario, è necessario scegliere quale dei due o più duplicati è corretto ed eliminare la voce o le voci duplicate. ||
|**formato** | Errore di formattazione. Il valore viola i requisiti di formato per l'utilizzo dell'attributo. | L'aggiornamento suggerito mostrerà il valore con caratteri non validi rimossi. Se non sono presenti caratteri non validi, Update e Value saranno uguali. Devi decidere quello che ti interessa veramente dell'aggiornamento. Lo strumento non fornirà una correzione suggerita per tutti gli errori di formattazione. | Ad esempio gli indirizzi SMTP devono soddisfare lo standard RFC 2822 e mailNickName non può iniziare o terminare con un punto. Per ulteriori informazioni sui requisiti di formato per gli attributi della directory, vedere "Preparazione Directory oggetti e attributi" in [Prepare to provision utenti mediante la sincronizzazione delle directory per Office 365](prepare-for-directory-synchronization.md). |
|topleveldomain  <br/> |Dominio di livello superiore. Ciò vale per i valori soggetti a [RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464) formattazione. Se il dominio di livello principale non è internet instradabile ciò viene identificato come errore. Ad esempio un indirizzo SMTP che termina con. Local non instradabile internet e causerebbe questo errore. |Modificare il valore in un dominio instradabile su internet, ad esempio `.com` o `.net`. | Modifica `myaddress@fourthcoffee.local` a `fourthcoffee.com` o un altro dominio instradabile su internet.  <br/> Per ulteriori informazioni, vedere [come preparare un dominio non instradabili (ad esempio domain Local) per la sincronizzazione delle directory](prepare-a-non-routable-domain-for-directory-synchronization.md). |
|**domainpart** | Errore di parte del dominio. Questo vale per valori soggetti a formattazione RFC 2822. Se la parte di dominio del valore non è valida e non soddisfa la formattazione RFC 2822, viene generata. | Sostituire il valore conforme agli standard RFC 2822. Ad esempio, assicurarsi che non contengono spazi o caratteri non validi. | Modifica `myaddress@fourth coffee.com` a `myaddress@fourthcoffee.com`. |
|**domainpart_localpart** | Errore della parte locale. Questo vale per valori soggetti a formattazione RFC 2822. Se la parte locale del valore non è valida e non soddisfa la formattazione RFC 2822, viene generata. |Sostituire il valore conforme agli standard RFC 2822. Ad esempio, assicurarsi che non contengono spazi o caratteri non validi. |Modifica `my"work"address@fourthcoffee.com` a `myworkaddress@fourthcoffee.com`. |
|**lunghezza** | Errore di lunghezza. Il valore viola il limite di lunghezza per l'attributo. In genere, si verifica quando viene modificato lo schema di directory.  | L'aggiornamento consigliato da IdFix tronca il valore alla lunghezza accettabile.  <br/> Tenere presente che questo può produrre risultati indesiderati. È necessario rivedere la soluzione suggerita e, se necessario, modificarla prima di fare clic su **Applica**. ||
|**vuoto**  | Errore null o vuoto. Il valore viola la restrizione null per gli attributi da sincronizzare. Solo alcuni attributi devono contenere un valore. | Se possibile, l'aggiornamento suggerito utilizza altri valori per poter generare un probabile sostituto. ||
|**mailmatch** | Si applica solo alle soluzioni qualificate con Office 365. Il valore non corrisponde all'attributo mail. | L'aggiornamento suggerito è il valore dell'attributo mail preceduti dal prefisso "SMTP:". ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>Operazioni eseguibili utilizzando IdFix
Per correggere un errore, si seleziona un'opzione dall'elenco a discesa **ACTION** . Nella tabella seguente vengono descritte le operazioni di **azione** che è possibile effettuare per gli attributi utilizzando lo strumento IdFix. Se si lascia vuoto nella colonna **azione** , lo strumento IdFix non eseguirà alcuna azione in tale errore specifico nella directory. 

|**AZIONE**|**Descrizione azione**|**Esempio**|
|:-----|:-----|:-----|
|**COMPLETE** | Il valore originale è accettabile e non deve essere modificato nonostante sia stato identificato come errore. | Due utenti hanno un proxyAddress identificato come duplicato. Solo uno può essere utilizzato per il recapito della posta. Contrassegnare l'utente con il valore corretto come **COMPLETE**. |
|**RIMUOVERE** | Il valore dell'attributo verrà eliminato dall'oggetto di origine. Nel caso di un attributo a valore singolo, ad esempio `proxyAddresses`, verrà eliminato i singolo valore visualizzato. | Due utenti hanno un proxyAddress identificato come duplicato. Solo uno può essere utilizzato per il recapito della posta. Contrassegnare l'utente con il valore duplicato come **REMOVE**. |
|**MODIFICA** | Le informazioni nella colonna **UPDATE** verranno utilizzate per modificare il valore dell'attributo. Se un valore valido di **aggiornamento** è stato consigliato da IdFix, quindi, nella colonna **azione** selezionare **Modifica** e passare all'errore successivo. Se non ti piace il suggerimento, digitare un nuovo nella colonna **UPDATE** e quindi selezionare **Modifica**nella colonna **azione** . ||
|**ANNULLAMENTO** | Questa opzione è disponibile solo se sei stato ripristinato da un registro di transazioni. Se selezioni **ANNULLA**, il valore dell'attributo verrà ripristinato al valore originale. ||
|**FAIL** | Questo valore viene restituito solo se un valore di **aggiornamento** presenta un conflitto sconosciuto con le regole di dominio Active Directory. In questo caso, è possibile modificare il valore nella colonna **UPDATE** nuovamente se si conosce l'errore. Potrebbe essere necessario analizzare i valori nell'oggetto utilizzando ADSI Edit. Per ulteriori informazioni, vedere [ADSI Edit (Adsiedit. msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170). ||

Dopo aver scelto il valore **ACTION** per un errore o un batch di errori, fare clic su **Applica**. Quando fa clic su **Applica**, lo strumento apporta le modifiche nella directory. È possibile fornire delle correzioni per più errori prima di fare clic su **Applica** e IdFix le modificherà tutte contemporaneamente.

Eseguire lo strumento IdFix per verificare che le correzioni apportate non introducano nuovi errori. È possibile ripetere questi passaggi più volte è necessario. È buona norma passare attraverso il processo più volte prima della sincronizzazione.
    
## <a name="changing-the-rule-set-used-by-idfix"></a>Modifica del set di regole utilizzato da IdFix
Per impostazione predefinita, lo strumento IdFix utilizza multi-Tenant set di regole per testare le voci nella directory. Si tratta della regola destra impostato per la maggior parte dei Office 365 = clienti. Tuttavia, se si è un cliente ITAR che offre (traffico internazionale in rami normative) o dedicati di Office 365, è possibile configurare IdFix per l'utilizzo in realtà set di regole dedicato. Se non si è certi di che tipo di cliente è, in modo sicuro è possibile ignorare questo passaggio. Per impostare il set di regole per dedicate, fare clic sull'icona dell'ingranaggio nella barra dei menu e quindi fare clic su **dedicate**.
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>Modifica dell'ambito della ricerca utilizzata da IdFix
Per impostazione predefinita, IdFix ricerca l'intera directory. Se si desidera, è possibile configurare lo strumento per la ricerca di una sottostruttura specifica. A tale scopo, nella barra dei menu, fare clic sull'icona Filter e immettere una sottostruttura valida.
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>Ripristino delle modifiche utilizzando l'interfaccia grafica di IdFix
Ogni volta che si fa clic su **Apply** per applicare le modifiche, lo strumento IdFix consente di creare un file separato denominato un log delle transazioni che sono elencate le modifiche appena apportate. È possibile utilizzare il registro delle transazioni per eseguire il rollback solo le modifiche presenti nel registro più recente nel caso in cui si effettua un errore. Se si effettua un errore durante l'aggiornamento, facendo clic su **Annulla**per annullare le modifiche applicate più di recente. Quando si fa clic su **Annulla**, il log delle transazioni IdFix utilizza per eseguire il rollback solo le modifiche presenti nel registro delle transazioni più recente. Per ulteriori informazioni sull'utilizzo del log delle transazioni, vedere [Guida di riferimento: registro delle transazioni IdFix di Office 365](idfix-transaction-log.md).