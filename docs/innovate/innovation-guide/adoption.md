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
ms.openlocfilehash: a6eb791e22d834f51face8819133c0ada6774952
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752952"
---
::: zone target="docs"

# <a name="azure-innovation-guide-prepare-for-customer-feedback"></a>Guida all'innovazione di Azure: Prepararsi per il feedback dei clienti

::: zone-end

::: zone target="chromeless"

# <a name="prepare-for-customer-feedback"></a>Prepararsi per il feedback dei clienti

::: zone-end

L'adozione, l'engagement e la fidelizzazione degli utenti sono fondamentali per il successo dell'innovazione. Perché?

Sviluppare una nuova soluzione innovativa non significa dare agli utenti quello che vogliono o che pensano di volere. Significa piuttosto formulare un'ipotesi che è possibile testare e continuare a migliorare. I test sono di due tipi diversi:

- **Quantitativi (feedback dei test):** questo feedback consente di verificare se i risultati sono quelli auspicati.
- **Qualitativi (feedback dei clienti):** questo feedback indica quali metriche sono significative nelle opinioni dei clienti.

Prima di integrare i cicli di feedback, è necessario disporre di un repository condiviso per la propria soluzione. Un repository centralizzato consentirà di registrare tutto il feedback in arrivo sul progetto e agire di conseguenza. [GitHub](https://github.com) è il sito del software open source. È anche una delle piattaforme più diffuse per ospitare i repository di codice sorgente per le app commerciali sviluppate. L'articolo sulla [creazione dei repository GitHub](https://docs.microsoft.com/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml) può essere utile per iniziare a usare un proprio repository.

Ognuno degli strumenti seguenti di Azure si integra o è compatibile con i progetti ospitati in GitHub:

## <a name="quantitative-feedback-for-web-appstabquantitative-apps"></a>[Feedback quantitativo per le app Web](#tab/Quantitative-Apps)

Application Insights è uno strumento di monitoraggio che consente di ottenere feedback quantitativo quasi in tempo reale sull'uso di un'applicazione. Questo feedback può aiutare a testare e convalidare l'ipotesi corrente per definire la funzionalità o storia utente successiva nel proprio backlog.

### <a name="action"></a>Azione

Per visualizzare i dati quantitativi sulle applicazioni:

1. Passare ad **Application Insights**.
   - Se l'applicazione non viene visualizzata nell'elenco, selezionare **Aggiungi** e seguire le istruzioni per avviare la configurazione di Application Insights.
   - Se l'app desiderata è inclusa nell'elenco, selezionarla.
1. Il riquadro **Panoramica** include alcune statistiche sull'applicazione. Selezionare **Dashboard dell'applicazione** per creare un dashboard personalizzato in cui visualizzare i dati più pertinenti per l'ipotesi formulata.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Go to Application Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per visualizzare i dati sulle app, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

- [Configurare Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/learn/quick-monitor-portal)
- [Introduzione ad Application Insights di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-users)
- [Creare un dashboard di telemetria](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

## <a name="quantitative-feedback-for-apistabquantitative-apis"></a>[Feedback quantitativo per le API](#tab/Quantitative-APIs)

L'economia connessa sta cambiando il modo in cui le organizzazioni scelgono di innovare. Come mai prima d'ora, mercati e settori sono sottoposti a effetti dirompenti che assumono forme diverse, mentre le organizzazioni si trovano alle prese con il _dilemma dell'innovatore_, ovvero come stabilire il ritmo del cambiamento senza ostacolare l'attività aziendale in corso.

Le API vengono usate all'esterno delle aziende per cambiare il modo in cui interagiscono con clienti e partner e all'interno per connettere tra loro le diverse componenti del business. L'economia delle API si basa su quattro elementi costitutivi: social networking, mobilità, analisi e cloud. Le app e i servizi possono essere collegati in modo rapido e a costi contenuti per creare una proposta di valore estesa.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per registrare i dati quantitativi sulle API:

1. Passare a **Servizi Gestione API**.
2. Selezionare l'API desiderata nell'elenco.
3. Selezionare **Impostazioni di diagnostica** nella sezione **Monitoraggio**.

Per visualizzare i dati quantitativi sulle API:

1. Passare a **Servizi Gestione API**.
2. Selezionare l'API desiderata nell'elenco.
3. Selezionare **Applicazione** nella sezione **Monitoraggio**.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per aprire i servizi di Gestione API, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

- [Usare Monitoraggio di Azure per ottenere feedback sulle API](https://docs.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor)

## <a name="qualitative-feedbacktabqualitative"></a>[Feedback qualitativo](#tab/Qualitative)

Il backlog (o lavagna) si usa per registrare il feedback sotto forma di storie utente. Consente inoltre di tenere traccia del lavoro correlato come attività eseguibili. Il servizio Azure Boards può essere integrato direttamente in GitHub per offrire un'esperienza di continuità tra la gestione del feedback e qualsiasi codice sorgente.

::: zone target="docs"

### <a name="action"></a>Azione

Azure Board e Azure Pipelines richiedono un portale separato da GitHub e Azure.
Per iniziare a usare uno di questi strumenti, passare ad [Azure DevOps](https://dev.azure.com).

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Azione

Per creare un progetto DevOps:

1. Passare a **Azure DevOps Projects**.
2. Selezionare **Crea progetto DevOps**.
3. Selezionare **un runtime, un framework e un servizio**.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/microsoft.visualstudio%2Faccount%2Fproject]" submitText="Go to Azure DevOps Projects" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>Altre informazioni

Questi articoli consentono di centralizzare e gestire il feedback usando Azure Boards insieme a GitHub:

- [Introduzione ad Azure Boards](https://docs.microsoft.com/azure/devops/boards/get-started/?view=azure-devops)
- [Azure Boards e GitHub](https://docs.microsoft.com/azure/devops/boards/github?view=azure-devops)

## <a name="close-the-loop-with-pipelinestabpipelines"></a>[Chiudere il ciclo con le pipeline](#tab/pipelines)

Agire in base al feedback non sempre significa aggiungere la funzionalità richiesta dal cliente. Tuttavia, ogni dato dovrebbe generare qualche forma di cambiamento, ad esempio un nuovo punto di vista oppure una modifica tecnica completamente diversa da quella richiesta. In ogni caso, le pipeline di distribuzione e gli strumenti come Azure Pipelines consentono di pubblicare rapidamente queste modifiche in modo da condividerle frequentemente con il cliente.

### <a name="action"></a>Azione

Per visualizzare le distribuzioni correnti nella pipeline:

1. Passare a **Servizi app**.
2. Selezionare l'applicazione desiderata nell'elenco.
3. Selezionare **Centro distribuzione** nella sezione **Distribuzione** del riquadro Servizi app.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per visualizzare le applicazioni in Servizio app, passare al [portale di Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites).

::: zone-end

### <a name="learn-more"></a>Altre informazioni

Iniziare a creare le pipeline di distribuzione:

- [Creare la prima pipeline](https://docs.microsoft.com/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)
- [Attività con le versioni di GitHub](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/github-release?view=azure-devops)
