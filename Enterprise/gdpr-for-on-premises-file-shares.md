---
title: RGDP per condivisioni file locali
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informazioni su come gestire i requisiti RGPD nelle condivisioni file di Windows Server locale.
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a><span data-ttu-id="49d30-103">Condivide l'RGDP per le condivisioni file di Windows Server locale</span><span class="sxs-lookup"><span data-stu-id="49d30-103">GDPR for on-premises Windows Server file shares</span></span>

<span data-ttu-id="49d30-104">L'approccio di base consigliato per le condivisioni file è il seguente:</span><span class="sxs-lookup"><span data-stu-id="49d30-104">The basic recommended approach for file shares is:</span></span>

-   <span data-ttu-id="49d30-105">Utilizzare Azure Information Protection per etichettare dati sensibili.</span><span class="sxs-lookup"><span data-stu-id="49d30-105">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="49d30-106">Utilizzare lo scanner di Azure Information Protection per individuare dati.</span><span class="sxs-lookup"><span data-stu-id="49d30-106">Use Azure Information Protection scanner to find data.</span></span>

<span data-ttu-id="49d30-107">L'approccio consigliato per le condivisioni file include i seguenti passaggi:</span><span class="sxs-lookup"><span data-stu-id="49d30-107">The recommended approach for files shares includes these steps:</span></span>

1.  <span data-ttu-id="49d30-108">**Installare e configurare lo scanner di Azure Information Protection.**</span><span class="sxs-lookup"><span data-stu-id="49d30-108">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="49d30-109">Scegliere i tipi di dati sensibili da usare.</span><span class="sxs-lookup"><span data-stu-id="49d30-109">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="49d30-110">Specificare le cartelle locali e le condivisioni di rete da utilizzare.</span><span class="sxs-lookup"><span data-stu-id="49d30-110">Specify local folders and network shares to use.</span></span>

2.  <span data-ttu-id="49d30-111">**Completare un ciclo di individuazione.**</span><span class="sxs-lookup"><span data-stu-id="49d30-111">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="49d30-112">Eseguire lo scanner in modalità di individuazione e convalidare i risultati.</span><span class="sxs-lookup"><span data-stu-id="49d30-112">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="49d30-113">Se necessario, ottimizzare le condizioni e i tipi di informazioni riservate.</span><span class="sxs-lookup"><span data-stu-id="49d30-113">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="49d30-114">Valutare l'impatto previsto dell'applicazione automatica delle etichette.</span><span class="sxs-lookup"><span data-stu-id="49d30-114">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="49d30-115">**Eseguire lo scanner di Azure Information Protection per applicare etichette a documenti idonei**.</span><span class="sxs-lookup"><span data-stu-id="49d30-115">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="49d30-116">**Per la protezione:**</span><span class="sxs-lookup"><span data-stu-id="49d30-116">**For protection:**</span></span>

    -   <span data-ttu-id="49d30-117">Configurare le regole di prevenzione della perdita dei dati di Exchange per proteggere i documenti con l'etichetta desiderata.</span><span class="sxs-lookup"><span data-stu-id="49d30-117">Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    -   <span data-ttu-id="49d30-118">Assicurarsi di utilizzare le autorizzazioni per definire chi può accedere ai file.</span><span class="sxs-lookup"><span data-stu-id="49d30-118">Be sure to use permissions to limit who can access files.</span></span>

5.  <span data-ttu-id="49d30-119">**Per il monitoraggio, integrare i log di Windows Server con uno strumento informazioni di sicurezza e gestione degli eventi.**</span><span class="sxs-lookup"><span data-stu-id="49d30-119">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    -   <span data-ttu-id="49d30-p101">Per trovare i dati personali per le richieste del soggetto dei dati, usare uno scanner di Azure Information Protection. È anche possibile configurare una ricerca per indicizzazione nelle condivisioni file di SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="49d30-p101">To find personal data for data subject requests, use Azure Information Protection scanner. You can also configure SharePoint Server search to crawl file shares.</span></span>

<span data-ttu-id="49d30-122">Per ulteriori informazioni sull'uso dello scanner di Azure Information Protection per individuare ed etichettare dati personali, vedere Microsoft GDPR Data Discovery Toolkit in [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>).</span><span class="sxs-lookup"><span data-stu-id="49d30-122">For more information on using Azure Information Protection scanner to find and label personal data, see the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>).</span></span>

<span data-ttu-id="49d30-p102">Per informazioni sulla configurazione dello scanner per le condizioni e l'utilizzo con tipi di informazioni riservate di prevenzione della perdita dei dati di Office 365, vedere [Come configurare le condizioni per la classificazione automatica e consigliata per Azure Information Protection](https://docs.microsoft.com/it-IT/information-protection/deploy-use/configure-policy-classification). Si noti che i nuovi tipi di informazioni riservate di Office 365 non saranno immediatamente disponibili per l'uso con lo scanner e che i tipi di informazioni riservate personalizzate non possono essere usati con lo scanner.</span><span class="sxs-lookup"><span data-stu-id="49d30-p102">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/it-IT/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>