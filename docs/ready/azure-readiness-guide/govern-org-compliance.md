---
title: Governance, sicurezza e conformità in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come configurare la governance, la sicurezza e la conformità per l'ambiente di Azure.
author: tvuylsteke
ms.author: kfollis
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: e4ba8670954371e58b688c36e6623f27708be3ef
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548949"
---
# <a name="governance-security-and-compliance-in-azure"></a>Governance, sicurezza e conformità in Azure

Quando si definiscono i criteri aziendali e si pianificano le strategie di governance, è possibile usare strumenti e servizi come Criteri di Azure, Azure Blueprints e Centro sicurezza di Azure per applicare e automatizzare le decisioni di governance dell'organizzazione. Prima di iniziare la pianificazione della governance, usare lo [strumento di benchmark della governance](https://cafbaseline.com) per identificare le potenziali lacune nell'approccio di governance del cloud dell'organizzazione. Per altre informazioni su come sviluppare i processi di governance, vedere le [indicazioni sulla governance di Cloud Adoption Framework for Azure](../../govern/index.md).

# <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprint](#tab/AzureBlueprints)

Azure Blueprints consente agli architetti del cloud e ai gruppi centrali del settore IT di definire un set ripetibile di risorse di Azure per implementare e rispettare gli standard, i modelli e i requisiti di un'organizzazione. Azure Blueprints consente ai team di sviluppo di creare e realizzare rapidamente nuovi ambienti sapendo che vengono creati in conformità con i requisiti dell'organizzazione con un set di componenti integrati, ad esempio le reti, per velocizzare lo sviluppo e il recapito.

I progetti costituiscono un metodo dichiarativo per orchestrare la distribuzione di vari modelli di risorse e altri artefatti, ad esempio:

- Assegnazioni di ruoli.
- Assegnazioni di criteri.
- Modelli di Azure Resource Manager.
- Gruppi di risorse.

## <a name="create-a-blueprint"></a>Creare un progetto

Per creare un progetto:

::: zone target="chromeless"

1. Passare a **Blueprints - Guida introduttiva**.
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

## <a name="publish-a-blueprint"></a>Pubblicare un progetto

Per pubblicare gli artefatti di un progetto in una sottoscrizione:

::: zone target="chromeless"

1. Passare a **Progetti - Definizioni di progetto**.
1. Selezionare il progetto creato nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Specificare un valore in **Versione** (ad esempio _1.0_) e in **Modifica le note**, quindi selezionare **Pubblica**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Passare a [Progetti - Definizioni di progetto](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selezionare la definizione di progetto creata nei passaggi precedenti.
1. Esaminare la definizione del progetto e selezionare **Pubblica progetto**.
1. Specificare un valore in **Versione** (ad esempio _1.0_) e in **Modifica le note**, quindi selezionare **Pubblica**.

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guida relativa alle decisioni di coerenza delle risorse](../../decision-guides/resource-consistency/index.md)
- [Esempi di progetti basati su standard](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end

# <a name="azure-policytabazurepolicy"></a>[Criteri di Azure](#tab/AzurePolicy)

Criteri di Azure è un servizio che consente di creare, assegnare e gestire criteri. Questi criteri applicano regole alle risorse, per garantire la conformità di tali risorse agli standard aziendali e ai contratti di servizio. Criteri di Azure analizza le risorse per identificare quelle che non sono conformi ai criteri implementati. Ad esempio, è possibile definire un criterio per consentire solo una dimensione di macchina virtuale specifica da eseguire nell'ambiente. Quando viene implementato, questo criterio valuta le macchine virtuali esistenti nell'ambiente e tutte quelle nuove distribuite. La valutazione dei criteri genera eventi di conformità da usare per il monitoraggio e la creazione di report.

Prendere in considerazione i criteri comuni per:

- Applicare i tag per risorse e gruppi di risorse.
- Limitare le aree per le risorse distribuite.
- Limitare le SKU per risorse specifiche.
- Controllare l'uso di funzionalità facoltative importanti, come Azure Managed Disks.

::: zone target="chromeless"

## <a name="action"></a>Azione

Assegnare un criterio predefinito a un gruppo di gestione, una sottoscrizione o un gruppo di risorse.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

## <a name="apply-a-policy"></a>Applicare un criterio

Per applicare criteri a un gruppo di risorse:

1. Passare a [Criteri di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Selezionare **Assegna un criterio**.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Criteri di Azure](https://docs.microsoft.com/azure/azure-policy)
- [Cloud Adoption Framework: Guida relativa alle decisioni di applicazione dei criteri](../../decision-guides/policy-enforcement/index.md)

::: zone-end

# <a name="azure-security-centertabazuresecuritycenter"></a>[Centro sicurezza di Azure](#tab/AzureSecurityCenter)

Centro sicurezza di Azure ha un ruolo importante nella strategia di governance. Consente di controllare la sicurezza grazie alle caratteristiche seguenti:

- Offre una visualizzazione unificata della sicurezza tra tutti i carichi di lavoro.
- Raccoglie, cerca e analizza i dati sulla sicurezza da un'ampia gamma di origini, tra cui firewall e altre soluzioni partner.
- Offre raccomandazioni di utilità pratica sulla sicurezza per risolvere i problemi prima che possano essere sfruttati da utenti malintenzionati.
- Consente di applicare criteri di sicurezza ai carichi di lavoro cloud ibridi per garantire la conformità agli standard di sicurezza.

Molte delle funzionalità di sicurezza, come i criteri di sicurezza e le raccomandazioni, sono disponibili gratuitamente. Alcune delle funzionalità più avanzate, come l'accesso JIT alle macchine virtuali e il supporto per carichi di lavoro ibridi, sono disponibili con il livello Standard di Centro sicurezza di Azure. L'accesso JIT alle macchine virtuali contribuisce a ridurre la superficie di attacco della rete controllando l'accesso alle porte di gestione nelle macchine virtuali di Azure.

> [!TIP]
> Il Centro sicurezza di Azure è abilitato per impostazione predefinita in ogni sottoscrizione. È consigliabile abilitare la raccolta dati dalle macchine virtuali per consentire a Centro sicurezza di Azure di installare il proprio agente e iniziare a raccogliere dati.

::: zone target="docs"

Per esplorare il Centro sicurezza di Azure, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere:

- [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center)
- [Accesso JIT alle macchine virtuali](https://docs.microsoft.com/azure/security-center/security-center-just-in-time#how-does-just-in-time-access-work)
- [Piani tariffari Standard e Gratuito a confronto](https://azure.microsoft.com/pricing/details/security-center)
- [Cloud Adoption Framework: Disciplina di governance Baseline di sicurezza](../../govern/security-baseline/index.md)

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Azione

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end
