---
title: Controlli di accesso di Office 365 Yammer Enterprise
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: "Riepilogo: breve riepilogo sui controlli di accesso di Yammer Enterprise nell'ambiente di produzione."
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841793"
---
# <a name="yammer-enterprise-access-controls"></a><span data-ttu-id="f2418-103">Controlli di accesso di Yammer Enterprise</span><span class="sxs-lookup"><span data-stu-id="f2418-103">Yammer Enterprise Access Controls</span></span> 

<span data-ttu-id="f2418-104">L'accesso fisico e logico all'ambiente di produzione di Yammer è limitato a un piccolo gruppo di utenti (Infrastructure and Operations).</span><span class="sxs-lookup"><span data-stu-id="f2418-104">Physical and logical access to the Yammer production environment is restricted to a small set of people (infrastructure and operations).</span></span> <span data-ttu-id="f2418-105">Come per gli altri ingegneri di Office 365, gli ingegneri di Yammer hanno accesso a zero diritti ai dati dei clienti.</span><span class="sxs-lookup"><span data-stu-id="f2418-105">As with other Office 365 engineers, Yammer engineers have zero standing access to Customer Data.</span></span> <span data-ttu-id="f2418-106">L'accesso deve essere richiesto utilizzando un sistema di controllo dell'accesso basato su approvazione analogo all'archivio protetto con un numero limitato di responsabili approvazione.</span><span class="sxs-lookup"><span data-stu-id="f2418-106">Access must be requested using an approval-based just-in-time access control system similar to Lockbox with a limited number of approvers.</span></span> <span data-ttu-id="f2418-107">I responsabili approvazione verificano la richiesta (ad esempio, verificano se la richiesta è legittima in base alle esigenze, al caso aziendale, al tempo e così via) e quindi approva o rifiuta la richiesta.</span><span class="sxs-lookup"><span data-stu-id="f2418-107">Approvers verify the request (for example, they verify whether the request is legitimate based on need, business case, time, etc.), and then approve or deny the request.</span></span> <span data-ttu-id="f2418-108">Se la richiesta viene approvata, l'accesso JIT viene concesso per un periodo di tempo definito e limitato.</span><span class="sxs-lookup"><span data-stu-id="f2418-108">If the request is approved, JIT access is granted for a defined and limited time.</span></span> <span data-ttu-id="f2418-109">Dopo aver superato il tempo di accesso, l'accesso scade automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f2418-109">After access time is exceeded, the access automatically expires.</span></span>

<span data-ttu-id="f2418-110">Come per gli altri servizi di Office 365, tutti gli accessi all'ambiente di produzione di Yammer utilizzano l'autenticazione a più fattori.</span><span class="sxs-lookup"><span data-stu-id="f2418-110">As with other Office 365 services, all access to the Yammer production environment uses multi-factor authentication.</span></span> <span data-ttu-id="f2418-111">Tutti gli accessi e la cronologia dei comandi vengono assegnati a un utente e registrati e recensiti regolarmente dal team di sicurezza di Yammer.</span><span class="sxs-lookup"><span data-stu-id="f2418-111">All access and command history is attributed to a user, and logged and reviewed regularly by the Yammer security team.</span></span>

<span data-ttu-id="f2418-112">Per ulteriori informazioni sull'amministrazione e la gestione di Yammer, vedere la Guida di amministrazione di [Yammer](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span><span class="sxs-lookup"><span data-stu-id="f2418-112">For more information about Yammer administration and management, see [Yammer Admin Help](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).</span></span>