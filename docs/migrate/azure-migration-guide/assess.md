---
title: Valutare il digital estate
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Valutare il digital estate
author: matticusau
ms.author: mlavery
ms.date: 08/08/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: a2acba3f9aa06298922d2cc95d298d3792a9ada9
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240001"
---
# <a name="assess-the-digital-estate"></a>Valutare il digital estate

In una migrazione ideale ogni asset (infrastruttura, app o dati) sarà compatibile con una piattaforma cloud e sarà pronto per la migrazione. In realtà, non è necessario eseguire la migrazione nel cloud. Inoltre, non tutti gli asset sono compatibili con le piattaforme cloud. Prima di eseguire la migrazione di un carico di lavoro nel cloud, è importante valutare il carico di lavoro e ogni asset correlato (infrastruttura, app e dati).

Le risorse di questa sezione consentono di valutare l'ambiente per determinare l'idoneità per la migrazione e i metodi da considerare.

<!-- markdownlint-disable MD025 -->

# <a name="toolstabtools"></a>[Strumenti](#tab/Tools)

Gli strumenti seguenti consentono di valutare l'ambiente per determinare l'idoneità della migrazione e l'approccio migliore da usare. Per informazioni utili sulla scelta degli strumenti appropriati per supportare le attività di migrazione, vedere la [Guida alle decisioni relative agli strumenti di migrazione del framework di adozione del cloud](../../decision-guides/migrate-decision-guide/index.md).

## <a name="azure-migrate"></a>Azure Migrate

Il servizio Azure Migrate valuta l'infrastruttura, le applicazioni e i dati locali per la migrazione ad Azure. Il servizio valuta l'idoneità per la migrazione degli asset locali, esegue il dimensionamento in base alle prestazioni e offre stime dei costi per l'esecuzione degli asset locali in Azure. È il servizio ideale se si stanno prendendo in considerazione migrazioni in modalità lift-and-shift o si affrontano le prime fasi di valutazione della migrazione. Al termine della valutazione, è possibile usare Azure Migrate per eseguire la migrazione.

![Panoramica di Azure Migrate](./media/assess/azuremigrate-overview-1.png)

### <a name="create-a-new-server-migration-project"></a>Creare un nuovo progetto di migrazione dei server

Per iniziare a usare una valutazione della migrazione dei server con Azure Migrate, seguire questa procedura:

1. Selezionare **Azure Migrate**.
1. In **Panoramica** fare clic su **Valutare ed eseguire la migrazione dei server** .
1. Selezionare **Aggiungi strumenti**.
1. In **Individuare, valutare ed eseguire la migrazione dei server** fare clic su **Aggiungi strumenti**.
1. In **Progetto di migrazione** selezionare la sottoscrizione di Azure e creare un gruppo di risorse, se non se ne ha già uno.
1. In **Dettagli del progetto** specificare il nome del progetto e l'area geografica in cui lo si vuole creare e quindi fare clic su **Avanti**.
1. In **Selezionare lo strumento di valutazione** selezionare **Ignora l'aggiunta di uno strumento di valutazione per adesso > Avanti**.
1. In **Selezionare lo strumento di migrazione** selezionare **Azure Migrate: Migrazione del server > Avanti**.
1. In **Rivedi e aggiungi strumenti** rivedere le impostazioni e fare clic su **Aggiungi strumenti**
1. Dopo l'aggiunta, lo strumento viene visualizzato nel **progetto di Azure Migrate > Server > Strumenti di migrazione**.

::: zone target="chromeless"

::: form action="Blade[#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview]" submitText="Assess and migrate servers" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Altre informazioni

- [Panoramica di Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview)
- [Eseguire la migrazione di server fisici o virtuali ad Azure](https://docs.microsoft.com/azure/migrate/tutorial-migrate-physical-virtual-machines)
- [Azure Migrate nel portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)

::: zone-end

## <a name="service-map"></a>Elenco dei servizi

Mapping dei servizi individua automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed esegue la mappatura della comunicazione fra i servizi. Il Mapping dei servizi consente di visualizzare i server nel modo in cui si pensa a essi, ovvero come sistemi interconnessi che forniscono servizi critici. Il Mapping dei servizi visualizza le connessioni fra i server, i processi, la latenza di connessione in ingresso e in uscita e le porte di tutte le architetture connesse via TCP senza il bisogno di alcuna configurazione a parte l'installazione di un agente.

Azure Migrate usa Mapping dei servizi per migliorare le funzionalità di creazione di report e le dipendenze all'interno dell'ambiente. I dettagli completi di questa integrazione sono descritti nella [Visualizzazione dipendenze](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization). Se si usa il servizio migrazione di Azure, non sono necessari passaggi aggiuntivi per configurare e ottenere i vantaggi di Mapping dei servizi. Le istruzioni seguenti sono fornite per il riferimento se si vuole utilizzare Mapping dei servizi per altri scopi o progetti.

### <a name="enable-dependency-visualization-using-service-map"></a>Abilitare la visualizzazione delle dipendenze usando Mapping dei servizi

Per usare la visualizzazione delle dipendenze, è necessario scaricare e installare gli agenti in ogni computer locale che si vuole analizzare.

- [Microsoft Monitoring Agent (MMA)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) deve essere installato in ogni computer.
- [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) deve essere installato in ogni computer.
- Se vi sono computer senza accesso a Internet, è necessario scaricare e installare il gateway di Log Analytics.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>Altre informazioni

- [Uso della soluzione Mapping dei servizi in Azure](https://docs.microsoft.com/azure/azure-monitor/insights/service-map)
- [Azure Migrate e Mapping dei servizi: Visualizzazione delle dipendenze](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization)

# <a name="scenarios-and-stakeholderstabscenarios"></a>[Scenari e stakeholder](#tab/Scenarios)

## <a name="scenarios"></a>Scenari

Questa guida si concentra sugli scenari seguenti:

- **Hardware legacy:** si sta eseguendo la migrazione per rimuovere una dipendenza da hardware legacy prossimo alla fine del supporto o alla fine del ciclo di vita.
- **Aumento della capacità:** è necessario aumentare la capacità per gli asset (infrastruttura, app e dati), che non possono essere forniti dall'infrastruttura corrente.
- **Modernizzazione del data center:** è necessario estendere il data center o modernizzarlo con la tecnologia cloud per garantire che l'azienda rimanga aggiornata e competitiva.
- **Modernizzazione dell'applicazione o del servizio:** si vogliono aggiornare le applicazioni per sfruttare i vantaggi della funzionalità nativa del cloud. Anche se è l'obiettivo iniziale di una strategia di migrazione rehost, la possibilità di creare piani per la revisione di applicazioni o servizi e la modernizzazione potenziale è un processo comune in qualsiasi migrazione.

### <a name="organizational-alignment-and-stakeholders"></a>Allineamento aziendale e stakeholder

L'elenco completo delle parti interessate varia tra i progetti di migrazione. È preferibile presupporre che non si conoscano tutte le parti interessate all'inizio della pianificazione di una migrazione, perché le parti interessate vengono spesso identificate solo durante determinate fasi del progetto. Tuttavia, prima di avviare qualsiasi progetto di migrazione, è possibile identificare i principali leader aziendali da finanza, infrastruttura IT e gruppi di applicazioni che avranno un interesse per le attività generali di migrazione del cloud dell'organizzazione.

La creazione di un team di strategia cloud di base, basata su questi principali stakeholder di alto livello, può aiutare a preparare l'organizzazione per l'adozione del cloud e a guidare le attività complessive di migrazione nel cloud. Questo team è responsabile della comprensione delle tecnologie cloud e dei processi di migrazione, dell'identificazione della motivazione aziendale per le migrazioni e della determinazione delle migliori soluzioni di alto livello per le attività di migrazione. Il team consente inoltre di identificare e collaborare con specifici stakeholder aziendali e dell'applicazione per garantire una corretta migrazione.

Per altre informazioni su come preparare l'organizzazione per le attività di migrazione nel cloud, vedere l'articolo relativo all'[allineamento iniziale dell'organizzazione ](../../plan/initial-org-alignment.md) nel framework di adozione del cloud.

# <a name="timelinestabtimelines"></a>[Tempistica](#tab/Timelines)

A titolo generale, i clienti scoprono che lo scenario di migrazione trattato in questa guida può essere completato da uno a sei mesi.

Alcuni dei fattori da considerare durante la valutazione della sequenza temporale della migrazione sono:

- **Asset (infrastruttura, app e dati) di cui eseguire la migrazione:** il numero e la diversità degli asset.
- **Idoneità del personale:** il personale è pronto per gestire il nuovo ambiente o necessita di formazione?
- **Raccolta fondi:** per completare la migrazione, è necessario disporre dell'approvazione e del budget appropriati?
- **Gestione delle modifiche:** l'azienda ha requisiti specifici relativi all'implementazione e all'approvazione delle modifiche?
- **Normative del settore:** è necessario conformarsi alle normative relative a segmenti o settore?

# <a name="cost-managementtabmanagecost"></a>[Gestione dei costi](#tab/ManageCost)

Quando si valuta l'ambiente, viene presentata un'opportunità ideale per includere un passaggio di analisi dei costi. Usando i dati raccolti dalle attività di valutazione, si è essere in grado di analizzare e prevedere i costi. Questa stima dei costi dovrebbe comportare i costi del servizio di consumo oltre ai costi monouso, ad esempio un aumento dei dati in ingresso.

Durante la migrazione, alcuni fattori che influiscono sulle decisioni e sulle attività di esecuzione:

- **Portata del digital estate:** comprendere la portata del digital estate influirà direttamente sulle decisioni e sulle risorse necessarie per eseguire la migrazione.
- **Modelli di contabilità:** lo spostamento da un modello di spesa in conto capitale strutturato a un modello di spesa operativa fluida.

::: zone target="docs"

Per informazioni approfondite su WIF, vedere le risorse seguenti:

- [Stimare i costi del cloud](../migration-considerations/assess/estimate.md)

::: zone-end
