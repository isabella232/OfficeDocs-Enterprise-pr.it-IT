---
title: Guida del laboratorio di testing configurare un laboratorio di testing di Exchange, Lync e SharePoint integrato
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: 'Riepilogo: informazioni su come creare un laboratorio di testing integrato contenente un server che esegue Exchange Server 2013, un server che esegue Lync Server 2013 e un server che esegue SharePoint Server 2013.'
ms.openlocfilehash: bfb2e1be3b9bb401514e736d38a6f1a2944940f0
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996520"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="e7ebe-103">Guida del laboratorio di testing: configurare un laboratorio di testing di Exchange, Lync e SharePoint integrato</span><span class="sxs-lookup"><span data-stu-id="e7ebe-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="e7ebe-104">Informazioni su come creare un laboratorio di testing integrato contenente un server che esegue Exchange Server 2013, un server che esegue Lync Server 2013 e un server che esegue SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-104">Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="e7ebe-105">**Video introduttivo della guida del laboratorio di testing integrato di Exchange, Lync e SharePoint**</span><span class="sxs-lookup"><span data-stu-id="e7ebe-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="e7ebe-106">Il laboratorio di testing risultante da questa configurazione, che include l'autenticazione da server a server tra tutti e tre i tipi di server, può essere utilizzato per la creazione e la dimostrazione di scenari e soluzioni multi-prodotto che utilizzano un server che esegue Exchange Server 2013, un server che esegue Lync Server 2013 e un server che esegue SharePoint Server 2013.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="e7ebe-107">Questo documento contiene istruzioni per:</span><span class="sxs-lookup"><span data-stu-id="e7ebe-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="e7ebe-108">Configurazione del laboratorio di testing di configurazione di base di Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="e7ebe-109">Installazione e configurazione di un nuovo server denominato SQL1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="e7ebe-110">Installazione di SQL Server 2012 nel server SQL1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="e7ebe-111">Installazione e configurazione di un nuovo computer client denominato CLIENT2.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="e7ebe-112">Installazione e configurazione di Exchange Server 2013 su EX1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="e7ebe-113">Installazione e configurazione di un nuovo server denominato LYNC1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="e7ebe-114">Installazione di Lync Server 2013 Standard Edition in LYNC1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="e7ebe-115">Installazione di SharePoint Server 2013 su SP1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="e7ebe-116">Configurazione dell'integrazione tra EX1, LYNC1 e SP1.</span><span class="sxs-lookup"><span data-stu-id="e7ebe-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="e7ebe-117">Per informazioni su come configurare il laboratorio di testing in Hyper-V, vedere [hosting del laboratorio di testing integrato di Exchange, Lync e SharePoint con Windows Server 2012 Hyper-v](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span><span class="sxs-lookup"><span data-stu-id="e7ebe-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="e7ebe-118">Scaricare la guida del laboratorio di testing</span><span class="sxs-lookup"><span data-stu-id="e7ebe-118">Download the test lab guide</span></span>

<span data-ttu-id="e7ebe-119">[Guida del laboratorio di testing: configurare un laboratorio di testing di Exchange, Lync e SharePoint integrato](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="e7ebe-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e7ebe-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7ebe-120">See Also</span></span>

[<span data-ttu-id="e7ebe-121">Guide dei laboratori di testing</span><span class="sxs-lookup"><span data-stu-id="e7ebe-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




