---
title: Centralizzare le operazioni di gestione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Linee guida per centralizzare le operazioni di gestione
author: JnHs
ms.author: jenhayes
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: b88a1541a2f96dbd4b8d63572e44d493bce8cc45
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72979949"
---
# <a name="centralize-management-operations"></a>Centralizzare le operazioni di gestione

Per la maggior parte delle organizzazioni, l'uso di un singolo tenant di Azure Active Directory (Azure AD) per tutti gli utenti semplifica le operazioni di gestione e riduce i costi di manutenzione. Questo perché tutte le attività di gestione possono essere da utenti designati, gruppi di utenti o entità servizio all'interno di tale tenant. 

Se possibile, è consigliabile usare solo un tenant Azure AD per l'organizzazione. Alcune situazioni possono tuttavia richiedere a un'organizzazione di gestire più tenant Azure AD per i motivi seguenti:

- Sono sussidiarie completamente indipendenti.
- Operano in modo indipendente in più aree geografiche.
- Si applicano alcuni requisiti legali o di conformità.
- Sono disponibili acquisizioni di altre organizzazioni (talvolta temporanee fino a quando non viene definita una strategia di consolidamento dei tenant a lungo termine).

Quando è necessaria un'architettura multi-tenant, [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) fornisce un modo per centralizzare e semplificare le operazioni di gestione. Le sottoscrizioni di più tenant possono essere caricate per la [gestione delle risorse delegate di Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management). Questa opzione consente agli utenti specificati nel tenant di gestione di eseguire [funzioni di gestione tra tenant](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) in modo centralizzato e scalabile.

Si immagini, ad esempio, che l'organizzazione disponga di un singolo tenant, ovvero *tenant a*. L'organizzazione acquisisce quindi due tenant aggiuntivi, il *tenant B* e il *tenant C*e i motivi aziendali necessari per mantenerli come tenant distinti.

L'organizzazione vuole usare le stesse definizioni di criteri e procedure di backup e gli stessi processi di sicurezza in tutti i tenant. Poiché sono già presenti utenti (inclusi i gruppi di utenti e le entità servizio) che sono responsabili dell'esecuzione di queste attività nel tenant A, è possibile caricare tutte le sottoscrizioni nel tenant B e nel tenant C in modo che gli stessi utenti nel tenant A possano eseguirli attività. Il tenant A diventa quindi il tenant di gestione per il tenant B e il tenant C.

![Utenti di Tenant A che gestiscono le risorse in Tenant B e Tenant C](../_images/manage/enterprise-azure-lighthouse.jpg)

Per altre informazioni, vedere [Azure Lighthouse in Enterprise Scenarios](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
