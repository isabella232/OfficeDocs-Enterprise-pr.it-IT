---
title: RGPD per Project Server
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Informazioni su come gestire i requisiti RGPD nell'ambiente Project Server locale.
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="33ba1-103">RGPD per Project Server</span><span class="sxs-lookup"><span data-stu-id="33ba1-103">Plan for Project Server</span></span>

<span data-ttu-id="33ba1-p101">Project Server utilizza gli script personalizzati per esportare e redigere dati utente in Project Web App. Il processo di base è il seguente:</span><span class="sxs-lookup"><span data-stu-id="33ba1-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="33ba1-106">Trovare i siti di Project Web App della farm.</span><span class="sxs-lookup"><span data-stu-id="33ba1-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="33ba1-107">Trovare i progetti in ogni sito che contiene l'utente.</span><span class="sxs-lookup"><span data-stu-id="33ba1-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="33ba1-108">Esportare ed esaminare i tipi di dati da esaminare.</span><span class="sxs-lookup"><span data-stu-id="33ba1-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="33ba1-109">Redigere i dati in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="33ba1-109">Redact data as needed.</span></span>

<span data-ttu-id="33ba1-110">Questi passaggi sono descritti dettagliatamente negli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="33ba1-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="33ba1-111">Esportare i dati degli utenti da Project Server</span><span class="sxs-lookup"><span data-stu-id="33ba1-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="33ba1-112">Eliminare i dati degli utenti da Project Server</span><span class="sxs-lookup"><span data-stu-id="33ba1-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="33ba1-113">Tenere presente che Project Server è basato su SharePoint Server e registra gli eventi nei registri del Servizio di registrazione unificato e su database servizio di utilizzo.</span><span class="sxs-lookup"><span data-stu-id="33ba1-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
