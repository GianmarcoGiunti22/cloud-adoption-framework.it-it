---
title: Organizzare le risorse di Azure in modo efficace
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Procedure consigliate per organizzare in modo efficace le risorse di Azure allo scopo di semplificarne la gestione.
author: laraaleite
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 19299c5855600524f3335b00272974790d83c8fa
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022764"
---
# <a name="organize-your-azure-resources"></a>Organizzare le risorse di Azure

Usare le funzionalità e le procedure consigliate seguenti per proteggere le risorse cruciali per il sistema. Aggiungere tag alle risorse in modo da tenerne traccia tramite valori significativi per l'organizzazione.

<!-- markdownlint-disable MD024 MD025 -->

# <a name="azure-management-groups-and-hierarchytabazuremanagmentgroupsandhierarchy"></a>[Gruppi di gestione di Azure e gerarchia](#tab/AzureManagmentGroupsAndHierarchy)

La struttura organizzativa per le risorse in Azure include quattro livelli: gruppi di gestione, sottoscrizioni, gruppi di risorse e risorse. L'immagine seguente mostra la relazione tra questi livelli.

![Diagramma che mostra le relazioni nella gerarchia di gestione](./media/organize-resources/scope-levels.png)

- **Gruppi di gestione:** contenitori che semplificano la gestione di accesso, criteri e conformità per più sottoscrizioni. Tutte le sottoscrizioni in un gruppo di gestione ereditano automaticamente le condizioni applicate al gruppo di gestione.
- **Sottoscrizioni:** una sottoscrizione raggruppa insieme gli account utente e le risorse create da ognuno di essi. A ogni sottoscrizione si applicano limiti o quote relativamente alla quantità di risorse che è possibile creare e usare. Le organizzazioni possono usare sottoscrizioni per gestire i costi e le risorse create da utenti, team o progetti.
- **Gruppi di risorse:** Un gruppo di risorse è un contenitore logico in cui vengono distribuite e gestite risorse di Azure come app Web, database e account di archiviazione.
- **Risorse:** le risorse sono istanze di servizi create, ad esempio macchine virtuali, archiviazione o database SQL.

## <a name="scope-of-management-settings"></a>Ambito delle impostazioni di gestione

È possibile applicare impostazioni di gestione, come criteri e controlli degli accessi in base al ruolo, con qualsiasi livello di gestione. Il livello selezionato determina l'estensione con cui viene applicata l'impostazione. I livelli inferiori ereditano le impostazioni dai livelli superiori. Ad esempio, quando si applicano criteri a una sottoscrizione, i criteri vengono applicati anche a tutti i gruppi di risorse e alle risorse nella sottoscrizione.

In genere, è consigliabile applicare le impostazioni critiche ai livelli superiori e i requisiti specifici dei progetti ai livelli inferiori. Ad esempio, potrebbe essere necessario fare in modo che tutte le risorse per l'organizzazione vengano distribuite in determinate aree. A questo scopo, è possibile applicare un criterio alla sottoscrizione per specificare le località consentite. Quando altri utenti nell'organizzazione aggiungono nuovi gruppi di risorse e nuove risorse, vengono applicate automaticamente le posizioni consentite. Altre informazioni sui criteri sono disponibili nella sezione su governance, sicurezza e conformità di questa guida.

Nel pianificare una strategia di conformità, è consigliabile collaborare con le persone che nell'organizzazione si occupano di sicurezza e conformità, amministrazione IT, architettura aziendale, reti, finanza e approvvigionamento.

::: zone target="docs"

## <a name="create-a-management-level"></a>Creare un livello di gestione

È possibile creare un gruppo di gestione, sottoscrizioni aggiuntive o gruppi di risorse.

### <a name="create-management-group"></a>Creare un gruppo di gestione

Creare un gruppo di gestione per semplificare la gestione di accesso, criteri e conformità per più sottoscrizioni.

1. Passare a [Gruppi di gestione](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade).
2. Selezionare **Aggiungi gruppo di gestione**.

### <a name="create-subscription"></a>Creare la sottoscrizione

Usare le sottoscrizioni per gestire i costi e le risorse create da utenti, team o progetti.

1. Passare a [Sottoscrizioni](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Selezionare **Aggiungi**.

### <a name="create-resource-group"></a>Creare un gruppo di risorse

Creare un gruppo di risorse per contenere le risorse come app Web, database e account di archiviazione, che condividono ciclo di vita, autorizzazioni e criteri.

1. Passare a [Gruppi di risorse](https://portal.azure.com/#create/Microsoft.ResourceGroup).
1. Selezionare **Aggiungi**.
1. In **Sottoscrizione** selezionare la sottoscrizione che deve includere il gruppo di risorse creato.
1. Immettere un nome per il **gruppo di risorse**.
1. Selezionare un'**area** per la posizione del gruppo di risorse.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Informazioni sulla gestione dell'accesso alle risorse in Azure](../../govern/resource-consistency/resource-access-management.md)
- [Organizzare le risorse con i gruppi di gestione di Azure ](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview)
- [Limiti del servizio di sottoscrizione](https://docs.microsoft.com/azure/azure-subscription-service-limits)

::: zone-end

::: zone target="chromeless"

## <a name="actions"></a>Azioni

**Creare un gruppo di gestione:**

Creare un gruppo di gestione per semplificare la gestione di accesso, criteri e conformità per più sottoscrizioni.

1. Passare a **Gruppi di gestione**.
1. Selezionare **Aggiungi gruppo di gestione**.

::: form action="OpenBlade[#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade]" submitText="Go to Management groups" :::

**Creare una sottoscrizione aggiuntiva:**

Usare le sottoscrizioni per gestire i costi e le risorse create da utenti, team o progetti.

1. Passare a **Sottoscrizioni**.
1. Selezionare **Aggiungi**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

**Creare un gruppo di risorse:**

Creare un gruppo di risorse per contenere le risorse come app Web, database e account di archiviazione, che condividono ciclo di vita, autorizzazioni e criteri.

1. Passare a **Gruppi di risorse**.
1. Selezionare **Aggiungi**.
1. In **Sottoscrizione** selezionare la sottoscrizione che deve includere il gruppo di risorse creato.
1. Immettere un nome per il **gruppo di risorse**.
1. Selezionare un'**area** per la posizione del gruppo di risorse.

::: form action="Create[#create/Microsoft.ResourceGroup]" submitText="Create a resource group" :::

::: zone-end

# <a name="naming-standardstabnamingstandards"></a>[Standard di denominazione](#tab/NamingStandards)

Uno standard di denominazione ben progettato consente di identificare le risorse nel portale, in una fattura e negli script. È possibile che siano già stati definiti gli standard di denominazione per l'infrastruttura locale. Quando si aggiunge Azure all'ambiente, è opportuno estendere tali standard di denominazione alle risorse di Azure. Gli standard di denominazione sono utili per gestire l'ambiente in modo più efficiente a tutti i livelli. È possibile usare Criteri di Azure come strumento per applicare standard di denominazione nell'intero ambiente di Azure.

::: zone target="docs"

È consigliabile esaminare le [linee guida su modelli e procedure](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions) e adottarle dove possibile.

>[!TIP]
>Evitare i caratteri speciali, `-` o `_`, come primo o ultimo carattere in qualsiasi nome. Questi caratteri impediscono la riuscita della maggior parte delle regole di convalida.

::: zone-end

| Entità | Scope | Length | Maiuscole/minuscole | Caratteri validi | Schema consigliato | Esempio |
| --- | --- | --- | --- | --- | --- | --- |
|Resource group |Subscription |1-90 |Non fa distinzione tra maiuscole e minuscole |Caratteri alfanumerici, di sottolineatura e Unicode, parentesi, trattino e punto (tranne alla fine) |`<service short name>-<environment>-rg` |`profx-prod-rg` |
|Set di disponibilità |Resource group |1-80 |Non fa distinzione tra maiuscole e minuscole |Alfanumerico, carattere di sottolineatura e trattino |`<service-short-name>-<context>-as` |`profx-sql-as` |
|Tag |Entità associata |512 (nome), 256 (valore) |Non fa distinzione tra maiuscole e minuscole |Alfanumerico |`"key" : "value"` |`"department" : "Central IT"` |

# <a name="resource-tagstabresourcetags"></a>[Tag delle risorse](#tab/ResourceTags)

I tag sono utili per identificare rapidamente le risorse e i gruppi di risorse. I tag vengono applicati alle risorse di Azure per organizzarle in modo logico in categorie. Ogni tag è costituito da un nome e un valore. Ad esempio, è possibile applicare il nome "Environment" e il valore "Production" a tutte le risorse nell'ambiente di produzione.

Dopo aver applicato i tag, è possibile recuperare tutte le risorse nella sottoscrizione che hanno un nome e un valore di tag corrispondenti. I tag consentono di recuperare le risorse correlate da gruppi di risorse diversi e questo è utile per organizzare le risorse per la fatturazione o la gestione.

È possibile usare tag anche per molti altri scopi. I casi d'uso comuni includono i seguenti:

- **Metadata e documentazione:** gli amministratori possono visualizzare facilmente informazioni dettagliate sulle risorse che stanno usando applicando un tag come "ProjectOwner".
- **Automazione:** è possibile eseguire regolarmente script in grado di effettuare un'azione in base al valore di un tag, ad esempio "ShutdownTime" o "DeprovisionDate".
- **Fatturazione:** i tag possono essere inclusi nella fattura. È possibile usarli per semplificare la segmentazione della fattura usando tag come "CostCenter" o "BillTo".

Ogni risorsa o gruppo di risorse può avere un massimo di 15 coppie nome-valore di tag. Questo limite vale tuttavia solo per i tag applicati direttamente al gruppo di risorse o alla risorsa.

Per altre informazioni sull'assegnazione di tag, vedere le [convenzioni di denominazione per le risorse di Azure del Centro architetture di Azure](../../ready/considerations/naming-and-tagging.md#metadata-tags)

::: zone target="docs"

## <a name="apply-a-resource-tag"></a>Applicare un tag per le risorse

Per applicare un tag a un gruppo di risorse:

1. Passare a [Gruppi di risorse](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Selezionare un gruppo di risorse.
1. Selezionare **Tag**.
1. Immettere un nuovo nome e un valore o usare l'elenco a discesa per selezionare un nome e un valore esistenti.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere [Usare tag per organizzare le risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Azione

**Applicare un tag delle risorse:**

Per applicare un tag a un gruppo di risorse:

1. Passare a **Gruppi di risorse**.
1. Selezionare un gruppo di risorse.
1. Selezionare **Tag**.
1. Immettere un nuovo nome e un valore o selezionare un nome e un valore esistenti.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups]" submitText="Go to resource groups" :::

::: zone-end
