---
title: Gestire l'accesso all'ambiente di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come configurare il controllo di accesso per l'ambiente di Azure con il controllo degli accessi in base al ruolo.
author: LijuKodicheraJayadevan
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: 7ce8b1f8509ab0e51c94913ef010eb35b22b8978
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72379034"
---
# <a name="manage-access-to-your-azure-environment-with-role-based-access-controls"></a>Gestire l'accesso all'ambiente di Azure con controlli degli accessi in base al ruolo

La gestione di chi può accedere alle risorse e alle sottoscrizioni di Azure costituisce una parte importante della strategia di governance di Azure ed è buona norma assegnare privilegi e diritti di accesso basati sui gruppi. La gestione di gruppi, anziché di singoli utenti, consente di gestire più facilmente i criteri di accesso, mantenere la coerenza degli accessi tra i team e ridurre gli errori di configurazione. Il controllo degli accessi in base al ruolo di Azure è il metodo principale di gestione dell'accesso in Azure.

Il controllo degli accessi in base al ruolo consente di gestire in modo dettagliato l'accesso alle risorse in Azure. Questa funzionalità permette di gestire chi ha accesso alle diverse risorse di Azure, le operazioni consentite a ciascuno con tali risorse e a quali ambiti è possibile accedere.

Quando si pianifica la strategia di controllo degli accessi, concedere agli utenti il minimo privilegio necessario per completare la loro sessione di lavoro. La figura seguente mostra un modello consigliato per l'assegnazione del controllo degli accessi in base al ruolo.

![Diagramma che mostra i ruoli Controllo degli accessi in base al ruolo](./media/manage-access/role-examples.png)

Nel pianificare la metodologia di controllo di accesso, è consigliabile collaborare con persone che nell'organizzazione si occupano di sicurezza e conformità, amministrazione IT e architettura aziendale.

Cloud Adoption Framework offre indicazioni aggiuntive su come [usare il controllo degli accessi in base al ruolo](../azure-best-practices/roles.md) come parte delle attività di adozione del cloud.

::: zone target="chromeless"

## <a name="actions"></a>Azioni

**Concedere l'accesso a un gruppo di risorse:**

Per concedere a un utente l'accesso a un gruppo di risorse:

1. Passare a **Gruppi di risorse**.
1. Selezionare un gruppo di risorse.
1. Selezionare **Controllo di accesso (IAM)** .
1. Selezionare **Aggiungi** > **Aggiungi assegnazione di ruolo**.
1. Selezionare un ruolo e quindi assegnare l'accesso a un utente, un gruppo o un'entità servizio.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups]" submitText="Go to resource groups" ::: form-end

**Concedere l'accesso a una sottoscrizione:**

Per concedere l'accesso utente a una sottoscrizione:

1. Passare a **Sottoscrizioni**.
1. Selezionare una sottoscrizione.
1. Selezionare **Controllo di accesso (IAM)** .
1. Selezionare **Aggiungi** > **Aggiungi assegnazione di ruolo**.
1. Selezionare un ruolo e quindi assegnare l'accesso a un utente, un gruppo o un'entità servizio.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to subscriptions" ::: form-end

::: zone-end

::: zone target="docs"

## <a name="grant-resource-group-access"></a>Concedere l'accesso a un gruppo di risorse

Per concedere a un utente l'accesso a un gruppo di risorse:

1. Passare a [Gruppi di risorse](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Selezionare un gruppo di risorse.
1. Selezionare **Controllo di accesso (IAM)** .
1. Selezionare **Aggiungi** > **Aggiungi assegnazione di ruolo**.
1. Selezionare un ruolo e quindi assegnare l'accesso a un utente, un gruppo o un'entità servizio.

## <a name="grant-subscription-access"></a>Concedere l'accesso a una sottoscrizione

Per concedere l'accesso utente a una sottoscrizione:

1. Passare a [Sottoscrizioni](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Selezionare una sottoscrizione.
1. Selezionare **Controllo di accesso (IAM)** .
1. Selezionare **Aggiungi** > **Aggiungi assegnazione di ruolo**.
1. Selezionare un ruolo e quindi assegnare l'accesso a un utente, un gruppo o un'entità servizio.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Che cos'è il controllo degli accessi in base al ruolo?](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [Cloud Adoption Framework: Usare il controllo degli accessi in base al ruolo](../azure-best-practices/roles.md)

::: zone-end
