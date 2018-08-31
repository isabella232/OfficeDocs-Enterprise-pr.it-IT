---
title: Creare da zero
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: 'Riepilogo: Visualizzare i dettagli sul set di blocchi predefiniti di archiviazione cloud che è possibile utilizzare per creare il proprio servizio o la propria soluzione di archiviazione.'
ms.openlocfilehash: 8ef5d7a99c4e82d9a4fc3eb281a4af505887b792
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915681"
---
# <a name="build-from-the-ground-up"></a>Creare da zero

 **Riepilogo:** Visualizzare i dettagli sul set di blocchi predefiniti di archiviazione cloud che è possibile utilizzare per creare il proprio servizio o la propria soluzione di archiviazione.
  
Soluzioni di archiviazione "Creare da zero":
  
- Consente di creare la propria soluzione di archiviazione da zero. 
    
- Richiede una programmazione tramite l'API REST.
    
- Fornire il massimo di personalizzazione e flessibilità.
    
Le sezioni seguenti descrivono i dettagli di ciascuna opzione di archiviazione "Creare da zero".
  
## <a name="azure-storage-files"></a>Spazio di archiviazione di Azure (file)

### <a name="features"></a>Caratteristiche

- Semplifica lo spostamento delle applicazioni legacy nel cloud
    
- Archiviazione BLOB preferita per le nuove applicazioni
    
- Può essere installato da una macchina virtuale Azure
    
- Può essere installato in locale con SMB 3.0
    
- Funziona con Linux e Windows
    
- Non supporta l'autenticazione basata su Active Directory Azure o gli elenchi ACL (archiviazione Azure account chiavi consentono l'autenticazione e accesso autorizzato alla condivisione file)
    
### <a name="common-uses"></a>Utilizzi comuni

- Migrazione di applicazioni legacy nel cloud che si basano su condivisioni di file
    
- Strumenti di sviluppo della condivisione e test
    
- Le app distribuite possono archiviare registri, dati di diagnostica e dump di arresto anomalo del sistema
    
### <a name="key-storage-scenarios"></a>Scenari di archiviazione chiave

- File di backup
    
### <a name="resources"></a>Risorse

Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Spazio di archiviazione di Azure (blob)

### <a name="features"></a>Funzionalità

- Ogni account di archiviazione può contenere fino a 500 TB (una sottoscrizione può avere più account di archiviazione)





    
- Gli account di archiviazione sono organizzati in contenitori, a cui è applicata la sicurezza e che possono contenere BLOB
    
- I BLOB in blocchi sono ottimizzati per lo streaming e l’archiviazione di oggetti cloud, di dimensioni fino a 200 GB
    
- I BLOB di pagine sono ottimizzati per rappresentare dischi PaaS e supportare scritture casuali, di dimensioni fino a 1 TB
    
- I BLOB di accodamento sono ottimizzati per accodare le operazioni, fino a 195 GB
    
- L’archiviazione Premium offre IOPS più rapidi tramite lo spazio di archiviazione SSD
    
### <a name="common-uses"></a>Utilizzi comuni

- Backup dei file, computer, i database e i dispositivi immagini e testo per le applicazioni web
    
- Dati di configurazione per applicazioni cloud
    
- Big data, ad esempio registri e altri set di dati di grandi dimensioni
    
- Azure utilizza l’archivio BLOB per i propri servizi, ad esempio dischi HDInsight e di macchine virtuali
    
### <a name="key-storage-scenarios"></a>Scenari di archiviazione chiave

- Gestire i dati
    
### <a name="resources"></a>Risorse

Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Spazio di archiviazione di Azure (code)

### <a name="features"></a>Caratteristiche

- L’account di archiviazione può contenere qualsiasi numero di code
    
- La coda può contenere qualsiasi numero di messaggi (fino a riempire l'account di archiviazione)
    
- I messaggi in coda vengono automaticamente eliminati dopo sette giorni se non recuperati ed eliminati da un'applicazione
    
- I messaggi possono essere di dimensioni fino a 64 KB
    
- Protetto a livello di account di archiviazione
    
- Le code sono progettate per trasmettere i messaggi di controllo, non i dati non elaborati
    
### <a name="common-uses"></a>Utilizzi comuni

- Creare un backlog di lavoro da elaborare in modo asincrono
    
- Elaborazione dei messaggi del registro
    
- Decuplicare le applicazioni
    
### <a name="key-storage-scenarios"></a>Scenari di archiviazione chiave

- Distribuire gli eventi
    
### <a name="resources"></a>Risorse

Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Spazio di archiviazione di Azure (tabelle)

### <a name="features"></a>Caratteristiche

- Indicato per i set di dati semi-strutturati
    
- Costo in genere inferiore rispetto a SQL tradizionale
    
- Molto rapido nella ricerca di chiavi, lento nella ricerca di valori

    
- Ampiamente scalabile; qualsiasi quantità di tabelle entro i limiti dell'account di archiviazione
    
- Accessibile tramite l'API REST, il protocollo oData limitato, .NET
    
- I valori devono essere serializzati
    
### <a name="common-uses"></a>Utilizzi comuni

- Dati utente per applicazioni web
    
- Rubriche
    
- Informazioni sul dispositivo
    
### <a name="key-storage-scenarios"></a>Scenari di archiviazione chiave

- Gestire i dati
    
### <a name="resources"></a>Risorse

Per ulteriori informazioni, fare clic [qui](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Per informazioni sui costi, fare clic [qui](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Elementi consigliati di Archiviazione di Microsoft Azure

Quando si progetta la soluzione di archiviazione personalizzata con l'archiviazione di Azure, tenere presente quanto segue:
  
- Utilizzare più account di archiviazione per una maggiore scalabilità, per dimensioni maggiori (> 100 TB) o per una maggiore velocità effettiva (> 5.000 operazioni al secondo).
    
- Progettare la possibilità di aggiungere account di archiviazione supplementari come una modifica della configurazione, non come una modifica del codice.
    
- Selezionare attentamente le funzioni di partizionamento per l'archiviazione di tabelle per abilitare la scala desiderata in termini di prestazioni di inserimento e query.
    
- Scegliere nomi di colonna brevi per le proprietà di tabella, in quanto i metadati (nomi di proprietà) vengono archiviati in banda (i nomi di colonna vengono considerati anche ai fini delle dimensioni massime di riga pari a 1 MB).
    
- Se possibile, raggruppare le operazioni nello spazio di archiviazione.
    
- Memorizzare in modo aggressivo le informazioni presenti nel database di configurazione in una cache distribuita.
    
- Se le prestazioni o l’affidabilità dell'applicazione dipendono dalla disponibilità di un determinato segmento di dati presente nella cache, l'applicazione deve rifiutare le richieste in arrivo fino a quando la cache non viene prepopolata.
    
- Suddividere i dati in verticale (per tabella) o in orizzontale (segmentare la tabella in più partizioni) per distribuire il carico tra più database.
    
## <a name="see-also"></a>Vedere anche

[Archiviazione cloud Microsoft per Enterprise Architects](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Risorse sull'architettura IT del cloud Microsoft](microsoft-cloud-it-architecture-resources.md)

[Guida di orientamento del cloud aziendale Microsoft: risorse per i decision maker del settore IT](https://sway.com/FJ2xsyWtkJc2taRD)



