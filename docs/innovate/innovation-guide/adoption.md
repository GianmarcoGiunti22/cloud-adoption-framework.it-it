---
title: "Guida all'innovazione di Azure: Prepararsi per il feedback dei clienti"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Prepararsi per il feedback dei clienti
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: ec17c66fa92abc292a19a8e74c215111d8638a05
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769376"
---
::: zone target="docs"

# <a name="azure-innovation-guide-prepare-for-customer-feedback"></a>Guida all'innovazione di Azure: Prepararsi per il feedback dei clienti

::: zone-end

::: zone target="chromeless"

# <a name="prepare-for-customer-feedback"></a>Prepararsi per il feedback dei clienti

::: zone-end

L'adozione, l'engagement e la fidelizzazione degli utenti sono fondamentali per il successo dell'innovazione. Perché?

Sviluppare una nuova soluzione innovativa non significa dare all'utente quello che vuole o che pensa di volere. È invece necessario formulare un'ipotesi che è possibile testare e continuare a migliorare. I test sono di due tipi diversi: quantitativi (feedback dei test), per verificare se i risultati sono quelli auspicati, e qualitativi (feedback dei clienti), che indicano quali metriche sono significative nelle opinioni dei clienti. Nell'insieme, questi test forniscono le informazioni per formulare nuove ipotesi e apportare i successivi miglioramenti alla soluzione. Questi cicli di feedback costituiscono il fondamento del processo di [creazione-misurazione-apprendimento](../considerations/adoption.md) su cui si basa di questa metodologia.

Prima di integrare i cicli di feedback, è assolutamente necessario istituire un repository condiviso per la soluzione. Un repository centralizzato offrirà un modo per registrare tutto il feedback in arrivo sul progetto e agire di conseguenza.  [GitHub](https://github.com/) è il sito del software open source. È anche una delle piattaforme più diffuse per ospitare il repository di codice sorgente per le applicazioni commerciali sviluppate. L'articolo sulla [creazione dei repository GitHub](https://docs.microsoft.com/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml) può essere utile per iniziare con un proprio repository.

Ognuno degli strumenti seguenti di Azure si integra o è compatibile con i progetti ospitati in GitHub:

## <a name="quantitative-feedback-for-web-appstabquantitative-apps"></a>[Feedback quantitativo per le app Web](#tab/Quantitative-Apps)

Application Insights è uno strumento di monitoraggio che consente di ottenere un feedback quantitativo quasi in tempo reale sull'utilizzo dell'applicazione. Questo feedback può aiutare a testare e convalidare l'ipotesi corrente per definire la funzionalità successiva o la storia utente nel backlog.

### <a name="action"></a>Azione

Per visualizzare i dati quantitativi sulle applicazioni:

1. Passare ad **Application Insights**.
2. Se l'applicazione non viene visualizzata nell'elenco, fare clic sul collegamento **Aggiungi +** e seguire le istruzioni per avviare la configurazione di Application Insights.
3. Se l'app desiderata è inclusa nell'elenco, selezionarla.
4. Il riquadro **Panoramica** include alcune statistiche sull'applicazione. Il collegamento **Dashboard dell'applicazione** consentirà di creare un dashboard personalizzato per visualizzare i dati più pertinenti per l'ipotesi formulata.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Go to App Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per visualizzare i dati relativi alle app, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

- [Configurare Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/learn/quick-monitor-portal)
- [Introduzione ad Application Insights di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-users)
- [Creare un dashboard di telemetria](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

## <a name="quantitative-feedback-for-apistabquantitative-apis"></a>[Feedback quantitativo per le API](#tab/Quantitative-APIs)

L'economia connessa sta cambiando il modo in cui le organizzazioni scelgono di innovare.  Come mai prima d'ora, mercati e settori sono sottoposti a effetti dirompenti che assumono forme diverse, mentre le organizzazioni si trovano alle prese con il **'dilemma dell'innovatore'** : come stabilire il ritmo del cambiamento senza ostacolare l'attività aziendale in corso.

All'esterno, le aziende usano le API per cambiare il modo in cui interagiscono con clienti e partner. All'interno, le usano per connettere tra loro le varie componenti del business. L'economia delle API si basa su quattro elementi costitutivi: social networking, mobilità, analisi e cloud. Le app e i servizi possono essere collegati in modo rapido e a costi contenuti per creare una proposta di valore estesa.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per registrare i dati quantitativi sulle API:

1. Passare a **Servizio Gestione API**.
2. Selezionare l'API desiderata nell'elenco.
3. Scegliere **Impostazioni di diagnostica** nella sezione **Monitoraggio**.

Per visualizzare i dati quantitativi sulle API:

1. Passare a **Servizio Gestione API**.
2. Selezionare l'API desiderata nell'elenco.
3. Scegliere **Applicazione** nella sezione **Monitoraggio**.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per aprire il servizio Gestione API, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

Questo articolo può essere utile per usare [Monitoraggio di Azure per ottenere feedback sulle API](https://docs.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor)

## <a name="qualitative-feedbacktabqualitative"></a>[Feedback qualitativo](#tab/Qualitative)

Il backlog (o lavagna) si usa per registrare il feedback sotto forma di storie utente. Consente inoltre di tenere traccia del lavoro correlato come attività eseguibili. Il servizio Azure Boards può essere integrato direttamente in GitHub per offrire un'esperienza semplice tra la gestione del feedback e qualsiasi codice sorgente.

::: zone target="docs"

### <a name="action"></a>Azione

Azure Board e Azure Pipelines richiedono un portale separato da GitHub e Azure.
Per iniziare a usare questi strumenti, vedere [Azure DevOps](https://dev.azure.com/)

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Azione

Per creare un progetto DevOps:

1. Passare a **Progetto Azure DevOps**.
2. Fare clic su **Crea progetto DevOps**.
3. Scegliere **un runtime, un framework e un servizio**.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/microsoft.visualstudio%2Faccount%2Fproject]" submitText="Go to Azure DevOps Project" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>Altre informazioni

I collegamenti seguenti consentono di centralizzare e gestire il feedback usando Azure Boards insieme a GitHub:

- [Introduzione ad Azure Boards](https://docs.microsoft.com/azure/devops/boards/boards/kanban-quickstart?view=azure-devops)
- [Azure Boards e GitHub](https://docs.microsoft.com/azure/devops/boards/boards/kanban-quickstart?view=azure-devops)

## <a name="close-the-loop-with-pipelinestabpipelines"></a>[Chiudere il ciclo con le pipeline](#tab/pipelines)

Il feedback non sempre porta a iniziative per produrre le funzionalità richieste dai clienti. Ma ogni dato dovrebbe generare qualche forma di cambiamento, ad esempio un nuovo punto di vista oppure una modifica tecnica completamente diversa da quella richiesta. In ogni caso, le pipeline di distribuzione e strumenti come Azure Pipelines consentono di pubblicare rapidamente questi cambiamenti in modo da condividerli spesso con il cliente.

Per vedere le distribuzioni attive correlate alle applicazioni ospitate in Azure:

### <a name="action"></a>Azione

Per visualizzare le distribuzioni correnti nella pipeline:

1. Passare a **Servizio app**.
2. Selezionare l'applicazione desiderata nell'elenco.
3. Scegliere **Centro distribuzione** nella sezione **Distribuzione** del riquadro dei servizi app.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per visualizzare le applicazioni in Servizio app, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

I collegamenti aggiuntivi seguenti sono utili per iniziare a creare le pipeline di distribuzione:

- [Creare la prima pipeline](https://docs.microsoft.com/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)
- [Attività con le versioni di GitHub](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/github-release?view=azure-devops)
