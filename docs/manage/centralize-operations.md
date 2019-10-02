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
ms.openlocfilehash: b8e4e37ba9a771937b11f08f1abae45de2f818ab
ms.sourcegitcommit: 1dccf1aed8e98aa0f58c4f86d90c65f5fa5ac84d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71804730"
---
# <a name="centralize-management-operations"></a>Centralizzare le operazioni di gestione

Per la maggior parte delle organizzazioni, l'uso di un singolo tenant di Azure Active Directory (Azure AD) per tutti gli utenti semplifica le operazioni di gestione e riduce i costi di manutenzione, perché tutte le attività di gestione possono essere da utenti designati, gruppi di utenti o entità servizio all'interno di tale inquilino. Se possibile, è consigliabile usare solo un tenant di Azure AD per l'organizzazione.

In alcuni casi, tuttavia, potrebbe essere necessario che un'organizzazione gestisca più tenant Azure AD. È ad esempio possibile che siano necessari più tenant a causa di:

- Sussidiarie completamente indipendenti.
- Funzionamento indipendente in più aree geografiche.
- Requisiti legali o di conformità.
- Acquisizioni di altre organizzazioni (talvolta temporanee fino a quando non viene definita una strategia di consolidamento dei tenant a lungo termine).

Nei casi in cui è necessaria un'architettura multi-tenant, [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) fornisce un modo per centralizzare e semplificare le operazioni di gestione. Le sottoscrizioni di più tenant possono essere caricate per la [gestione delle risorse delegate di Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management), consentendo agli utenti specifici del tenant di gestione di eseguire [funzioni di gestione tra tenant](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) in modo centralizzato e scalabile.

Si immagini, ad esempio, che l'organizzazione disponga di un singolo tenant, ovvero *tenant a*. L'organizzazione acquisisce quindi due tenant aggiuntivi, *Tenant B* e *Tenant C*, che per motivi aziendali devono essere mantenuti distinti.

L'organizzazione vuole usare le stesse definizioni di criteri e procedure di backup e gli stessi processi di sicurezza in tutti i tenant. Dato che sono già presenti utenti (inclusi gruppi di utenti ed entità servizio) incaricati di queste attività in Tenant A, è possibile eseguire l'onboarding di tutte le sottoscrizioni di Tenant B e Tenant C in modo che gli stessi utenti di Tenant A possano eseguire tali attività. Il tenant A diventa quindi il tenant di gestione per il tenant B e il tenant C.

![Utenti di Tenant A che gestiscono le risorse in Tenant B e Tenant C](../_images/manage/enterprise-azure-lighthouse.jpg)

Per altre informazioni, vedere [Azure Lighthouse in Enterprise Scenarios](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
