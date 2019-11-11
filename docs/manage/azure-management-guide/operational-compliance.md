---
title: Conformità operativa in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Garantire la stabilità aziendale aumentando la conformità operativa
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: b5a94ab41bff26371621acc5e62ae19d9fd02e5c
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565475"
---
# <a name="operational-compliance-in-azure"></a>Conformità operativa in Azure

La _conformità operativa_ è la seconda disciplina in qualsiasi baseline di gestione del cloud.

![Baseline di gestione del cloud](../../_images/manage/management-baseline.png)

Il miglioramento della conformità operativa riduce la probabilità che si verifichino interruzioni del servizio dovute a differenze di configurazione oppure vulnerabilità causate dall'applicazione impropria di patch ai sistemi.

Per qualsiasi ambiente di livello aziendale, la tabella seguente include il minimo consigliato per una baseline di gestione.

|Process  |Strumento  |Scopo  |
|---------|---------|---------|
|Gestione delle patch|Gestione degli aggiornamenti|Gestione e pianificazione degli aggiornamenti|
|Imposizione dei criteri|Criteri di Azure|Applicazione di criteri per garantire la conformità di ambiente e guest|
|Configurazione dell'ambiente|Azure Blueprint|Conformità automatizzata per i servizi essenziali|

::: zone target="docs"

## <a name="update-management"></a>Gestione degli aggiornamenti

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gestione degli aggiornamenti](#tab/UpdateManagement)

::: zone-end

I computer gestiti da Gestione aggiornamenti usano le configurazioni seguenti per le valutazioni e la distribuzione degli aggiornamenti:

- Microsoft Monitoring Agent (MMA) per Windows o Linux
- PowerShell DSC (Desired State Configuration) per Linux
- Ruolo di lavoro ibrido per runbook di Automazione di Azure
- Microsoft Update o Windows Server Update Services (WSUS) per computer Windows

Per altre informazioni, vedere [Soluzione Gestione aggiornamenti](https://docs.microsoft.com/azure/automation/automation-update-management).

> [!WARNING]
> Prima di usare Gestione aggiornamenti, è necessario eseguire l'onboarding delle macchine virtuali o di un'intera sottoscrizione in Log Analytics e Automazione di Azure.
>
> Sono disponibili due approcci all'onboarding:
>
> - [Singola macchina virtuale](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Intera sottoscrizione](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)
>
> È consigliabile adottare uno di questi approcci prima di procedere con Gestione aggiornamenti.

### <a name="manage-updates"></a>Gestire gli aggiornamenti

Per applicare criteri a un gruppo di risorse:

1. Passare ad [Automazione di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Selezionare **Account di automazione** e scegliere uno degli account nell'elenco.
1. Passare a **Gestione della configurazione**.
1. È possibile usare le opzioni **Inventario**, **Gestione del cambiamento** e **State Configuration** per controllare lo stato e la conformità operativa delle VM gestite.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

## <a name="azure-policy"></a>Criteri di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-policytabazurepolicy"></a>[Criteri di Azure](#tab/AzurePolicy)

::: zone-end

Il servizio Criteri di Azure viene usato in tutti i processi di governance. Risulta anche estremamente utile all'interno dei processi di gestione del cloud. Criteri di Azure consente di controllare e correggere le risorse di Azure, oltre che di controllare le impostazioni all'interno di un computer. La convalida viene eseguita dall'estensione della configurazione guest e dal client. L'estensione, tramite il client, convalida impostazioni come:

- Configurazione del sistema operativo.
- Configurazione o presenza di applicazioni.
- Impostazioni dell'ambiente.

Al momento, Configurazione guest di Criteri di Azure controlla solo le impostazioni all'interno del computer. Non applica le configurazioni.

::: zone target="chromeless"

### <a name="action"></a>Azione

Assegnare un criterio predefinito a un gruppo di gestione, una sottoscrizione o un gruppo di risorse.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

### <a name="apply-a-policy"></a>Applicare un criterio

Per applicare criteri a un gruppo di risorse:

1. Passare a [Criteri di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Selezionare **Assegna un criterio**.

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Criteri di Azure](https://docs.microsoft.com/azure/azure-policy)
- [Criteri di Azure - Configurazione guest](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration)
- [Cloud Adoption Framework: Guida relativa alle decisioni di applicazione dei criteri](../../decision-guides/policy-enforcement/index.md)

## <a name="azure-blueprints"></a>Azure Blueprint

::: zone-end
::: zone target="chromeless"

## <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprint](#tab/AzureBlueprints)

::: zone-end

Con Azure Blueprints, gli architetti cloud e i gruppi IT centrali possono definire un set ripetibile di risorse di Azure. Queste risorse implementano e rispettano gli standard, i modelli e i requisiti di un'organizzazione.

Con Azure Blueprints, i team di sviluppo possono creare e configurare rapidamente nuovi ambienti, con la certezza di rispettare la conformità dell'organizzazione. A tale scopo, usano un set di componenti predefiniti, come la rete, per velocizzare lo sviluppo e la distribuzione.

I progetti costituiscono un metodo dichiarativo per orchestrare la distribuzione di vari modelli di risorse e altri artefatti, ad esempio:

- Assegnazioni di ruoli.
- Assegnazioni di criteri.
- Modelli di Azure Resource Manager.
- Gruppi di risorse.

L'applicazione di un progetto consente di rafforzare la conformità operativa nell'ambiente, se non è già stato fatto dal team di governance del cloud.

### <a name="create-a-blueprint"></a>Creare un progetto

Per creare un progetto:

::: zone target="chromeless"

1. Passare a **Blueprints - Guida introduttiva**.
1. Nel riquadro **Crea un progetto** selezionare **Crea**.
1. Filtrare l'elenco di progetti per selezionare quello appropriato.
1. Nella casella **Nome progetto** immettere il nome del progetto.
1. Selezionare **Località della definizione**e scegliere la località appropriata.
1. Selezionare **Avanti: Artefatti >>** ed esaminare gli artefatti inclusi nel progetto.
1. Selezionare **Salva bozza**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Passare a [Blueprints - Guida introduttiva](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. Nel riquadro **Crea un progetto** selezionare **Crea**.
1. Filtrare l'elenco di progetti per selezionare quello appropriato.
1. Nella casella **Nome progetto** immettere il nome del progetto.
1. Selezionare **Località della definizione**e scegliere la località appropriata.
1. Selezionare **Avanti: Artefatti >>** ed esaminare gli artefatti inclusi nel progetto.
1. Selezionare **Salva bozza**.

::: zone-end

### <a name="publish-a-blueprint"></a>Pubblicare un progetto

Per pubblicare gli artefatti di un progetto nella sottoscrizione:

::: zone target="chromeless"

1. Passare a **Progetti - Definizioni di progetto**.
1. Selezionare il progetto creato nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Nella casella **Versione** immettere una versione, ad esempio "1.0".
1. Nella casella **Modifica le note** modifiche immettere le note.
1. Selezionare **Pubblica**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Passare a [Progetti - Definizioni di progetto](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selezionare il progetto creato nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Nella casella **Versione** immettere una versione, ad esempio "1.0".
1. Nella casella **Modifica le note** modifiche immettere le note.
1. Selezionare **Pubblica**.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guida relativa alle decisioni di coerenza delle risorse](../../decision-guides/resource-consistency/index.md)
- [Esempi di progetti basati su standard](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
