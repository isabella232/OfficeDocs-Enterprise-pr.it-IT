---
title: Gestire Office 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 'Riepilogo: i Partner di Syndication e Cloud Solution Provider (CSP) possono utilizzare Windows PowerShell per gestire i tenant dei clienti di Office 365.'
ms.openlocfilehash: 35aca54af9dcfb6c9aa31c893f7213b053e111d2
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004169"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="fcef8-103">Gestire Office 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="fcef8-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="fcef8-104">**Sintesi:** I Partner di Syndication e Cloud Solution Provider (CSP) possono utilizzare Windows PowerShell per gestire i tenant dei clienti di Office 365.</span><span class="sxs-lookup"><span data-stu-id="fcef8-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="fcef8-105">I partner di autorizzazione accesso delegato (DAP, Delegated Access Permission) sono partner di Syndication e Cloud Solution Provider (CSP).</span><span class="sxs-lookup"><span data-stu-id="fcef8-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="fcef8-106">Di solito, rappresentano fornitori di rete o telecomunicazioni di altre aziende.</span><span class="sxs-lookup"><span data-stu-id="fcef8-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="fcef8-107">Consentono di raggruppare le sottoscrizioni Office 365 nelle offerte di servizio per i clienti.</span><span class="sxs-lookup"><span data-stu-id="fcef8-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="fcef8-108">Quando vendono un abbonamento a Office 365, vengono loro concesse automaticamente le autorizzazioni Amministra per conto terzi ai tenancy dei clienti in modo che possano amministrare ed effettuare report sui tenancy dei clienti.</span><span class="sxs-lookup"><span data-stu-id="fcef8-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="fcef8-109">Nella maggior parte dei casi, è difficile e richiede molto tempo nell'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fcef8-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="fcef8-110">È molto più facile effettuare attività amministrative, come elencare tutti i **TenantId** e i domini dei clienti o identificare tutti gli utenti in un tenancy e le licenze loro assegnate, utilizzando Windows PowerShell per Office 365.</span><span class="sxs-lookup"><span data-stu-id="fcef8-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="fcef8-111">In alcuni casi, è possibile eseguire tali attività amministrative solo in Windows PowerShell per Office 365.</span><span class="sxs-lookup"><span data-stu-id="fcef8-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="fcef8-112">Di seguito sono riportati alcuni esempi di scenari più frequenti in cui i partner di Syndication e Cloud Solution Providers (CSP) amministrano i tenancy dei clienti:</span><span class="sxs-lookup"><span data-stu-id="fcef8-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="fcef8-113">Gestire tenant Office 365 con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="fcef8-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="fcef8-114">Aggiungere un dominio a un tenancy client con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="fcef8-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="fcef8-115">Connettersi ai tenant Exchange Online con Windows PowerShell remoto per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="fcef8-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="fcef8-116">Recuperare i dati di report dei tenant dei clienti con Windows PowerShell per i partner di autorizzazione accesso delegato (DAP, Delegated Access Permission)</span><span class="sxs-lookup"><span data-stu-id="fcef8-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

