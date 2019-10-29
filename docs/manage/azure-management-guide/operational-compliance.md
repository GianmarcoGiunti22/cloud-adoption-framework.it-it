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
ms.openlocfilehash: 7073df6b697da49429d4086d9f8f3f113583e52d
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557092"
---
# <a name="operational-compliance-in-azure"></a>Conformità operativa in Azure

La conformità operativa è la seconda disciplina in qualsiasi baseline di gestione del cloud.

![Baseline di gestione del cloud](../../_images/manage/management-baseline.png)

Il miglioramento della conformità operativa riduce la probabilità che si verifichino interruzioni del servizio dovute a errori di configurazione oppure vulnerabilità causate dalla mancata applicazione di patch ai sistemi.

Per qualsiasi ambiente di livello aziendale, la tabella seguente include il minimo consigliato per qualsiasi baseline di gestione.

|Process  |Strumento  |Scopo  |
|---------|---------|---------|
|Gestione delle patch|Gestione degli aggiornamenti|Gestione e pianificazione degli aggiornamenti|
|Imposizione dei criteri|Criteri di Azure|Applicazione di criteri per garantire la conformità di ambiente e guest|
|Ambiente Configurazione|Azure Blueprint|Conformità automatizzata per i servizi essenziali|

::: zone target="docs"

## <a name="update-management"></a>Gestione degli aggiornamenti

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gestione degli aggiornamenti](#tab/UpdateManagement)

::: zone-end

I computer gestiti da Gestione aggiornamenti usano le configurazioni seguenti per le valutazioni e le distribuzioni degli aggiornamenti:

- Microsoft Monitoring Agent (MMA) per Windows o Linux
- PowerShell DSC (Desired State Configuration) per Linux
- Ruolo di lavoro ibrido per runbook di Automazione
- Microsoft Update o Windows Server Update Services (WSUS) per computer Windows

Per altre informazioni, vedere [Soluzione Gestione aggiornamenti](https://docs.microsoft.com/azure/automation/automation-update-management).

> [!WARNING]
> Prima di applicare la gestione degli aggiornamenti, è necessario eseguire l'onboarding delle VM o di un'intera sottoscrizione in Log Analytics e Automazione di Azure.
> Esistono due approcci all'onboarding ed è necessario adottarne uno prima di procedere alla gestione degli aggiornamenti.
>
> - [Singola macchina virtuale](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Intera sottoscrizione](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

### <a name="manage-updates"></a>Gestire gli aggiornamenti

Per applicare criteri a un gruppo di risorse:

1. Passare ad [Automazione di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
2. Scegliere uno degli **account di automazione** elencati.
3. Trovare la sezione **Gestione della configurazione** nel riquadro di spostamento del portale.
4. È possibile usare le opzioni Inventario, Gestione del cambiamento e State Configuration per controllare lo stato e la conformità operativa delle VM gestite.

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

Il servizio Criteri di Azure viene usato in tutti i processi di governance. Ma risulta anche estremamente utile all'interno dei processi di gestione del cloud. Oltre al controllo e alla correzione delle risorse di Azure, Criteri di Azure consente di controllare le impostazioni all'interno di un computer. La convalida viene eseguita dall'estensione della configurazione guest e dal client. L'estensione, tramite il client, convalida impostazioni come:

- Configurazione del sistema operativo
- Configurazione o presenza di applicazioni
- Impostazioni dell'ambiente

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

Azure Blueprints consente agli architetti del cloud e ai gruppi centrali del settore IT di definire un set ripetibile di risorse di Azure per implementare e rispettare gli standard, i modelli e i requisiti di un'organizzazione. Azure Blueprints consente ai team di sviluppo di creare e realizzare rapidamente nuovi ambienti sapendo che vengono creati in conformità con i requisiti dell'organizzazione con un set di componenti integrati, ad esempio le reti, per velocizzare lo sviluppo e il recapito.

I progetti costituiscono un metodo dichiarativo per orchestrare la distribuzione di vari modelli di risorse e altri artefatti, ad esempio:

- Assegnazioni di ruoli.
- Assegnazioni di criteri.
- Modelli di Azure Resource Manager.
- Gruppi di risorse.

L'applicazione di un progetto consente di rafforzare la conformità operativa nell'ambiente, se non è già stato fatto dal team di governance del cloud.

### <a name="create-a-blueprint"></a>Creare un progetto

Per creare un progetto:

::: zone target="chromeless"

1. Passare a **Progetti - Introduzione**.
1. Nella sezione **Crea un progetto** selezionare **Crea**.
1. Filtrare l'elenco di progetti per selezionare quello appropriato.
1. Immettere un valore in **Nome progetto** e selezionare la posizione appropriata in  **Località della definizione**.
1. Fare clic su **Avanti: Artefatti >>** ed esaminare gli artefatti inclusi nel progetto.
1. Fare clic su **Salva bozza**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Passare a [Blueprints - Guida introduttiva](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. Nella sezione **Crea un progetto** selezionare **Crea**.
1. Filtrare l'elenco di progetti per selezionare quello appropriato.
1. Immettere un valore in **Nome progetto** e selezionare la posizione appropriata in  **Località della definizione**.
1. Fare clic su **Avanti: Artefatti >>** ed esaminare gli artefatti inclusi nel progetto.
1. Fare clic su **Salva bozza**.

::: zone-end

### <a name="publish-a-blueprint"></a>Pubblicare un progetto

Per pubblicare gli artefatti di un progetto nella sottoscrizione:

::: zone target="chromeless"

1. Passare a **Progetti - Definizioni di progetto**.
1. Selezionare il progetto creato nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Specificare un valore in **Versione** (ad esempio "1.0") e in **Modifica le note**, quindi selezionare **Pubblica**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Passare a [Progetti - Definizioni di progetto](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selezionare il progetto creato nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Specificare un valore in **Versione** (ad esempio "1.0") e in **Modifica le note**, quindi selezionare **Pubblica**.

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guida relativa alle decisioni di coerenza delle risorse](../../decision-guides/resource-consistency/index.md)
- [Esempi di progetti basati su standard](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
