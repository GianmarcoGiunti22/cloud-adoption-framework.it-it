---
title: "Guida all'innovazione di Azure: Coinvolgere i clienti tramite app"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come usare Azure per promuovere l'innovazione coinvolgendo i clienti tramite app
author: billyclaymyersmsft
ms.author: wimyers
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: bafeecd715ac2c18c9ae744165be249c2b3639e5
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751565"
---
::: zone target="docs"

# <a name="azure-innovation-guide-engage-customers-through-apps"></a>Guida all'innovazione di Azure: Coinvolgere i clienti tramite app

::: zone-end

::: zone target="chromeless"

# <a name="engage-customers-through-apps"></a>Coinvolgere i clienti tramite app

::: zone-end

L'innovazione con le app include la modernizzazione delle app esistenti ospitate in locale e la creazione di app native del cloud tramite contenitori o tecnologie serverless. Per quanto riguarda la modernizzazione delle app, Azure offre servizi PaaS come il servizio app di Azure per modernizzare facilmente le app Web e API esistenti scritte in .NET, .NET Core, Java, Node.js, Ruby, Python o PHP per la distribuzione in Azure.

Con un modello a contenitori basato su standard aperti, la creazione di microservizi o la containerizzazione delle app esistenti e la relativa distribuzione in Azure risultano semplificate grazie a servizi gestiti come Azure Kubernetes, Istanze di Azure Container e app Web per contenitori. Le tecnologie serverless come Funzioni di Azure e App per la logica di Azure sono basate su un modello a consumo (si paga per le risorse usate) e consentono quindi di concentrarsi sulla creazione di applicazioni invece di preoccuparsi a distribuire e gestire l'infrastruttura.

<!-- markdownlint-disable MD025 -->

# <a name="deliver-value-fastertabdelivervaluefaster"></a>[Offrire valore più rapidamente](#tab/DeliverValueFaster)

Uno dei vantaggi delle soluzioni basate sul cloud consiste nella possibilità di raccogliere feedback più rapidamente e iniziare a offrire valore all'utente. Indipendentemente dal fatto che si tratti di un cliente esterno o di un utente interno dell'azienda, è sempre preferibile riuscire a ottenere feedback sulle applicazioni il più rapidamente possibile.

## <a name="azure-app-service"></a>Servizio app di Azure

Il Servizio app di Azure fornisce un ambiente di hosting per le applicazioni che rimuove il carico associato alla gestione dell'infrastruttura e alla distribuzione di patch del sistema operativo. Il servizio offre funzionalità di automazione su larga scala per soddisfare le esigenze degli utenti, rispettando comunque i limiti definiti per tenere sotto controllo i costi.

Il servizio app di Azure offre un supporto eccellente per i linguaggi come ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP e Python. Se è necessario ospitare un altro stack di runtime, il servizio app Web per contenitori consente di ospitare in modo semplice e immediato un contenitore Docker all'interno del servizio app, ospitando in questo modo lo stack di codice personalizzato in un ambiente che evita all'organizzazione di occuparsi dei server.

### <a name="action"></a>Azione

Per configurare o monitorare le distribuzioni del Servizio app di Azure:

1. Passare a **Servizi app**.
2. Configurare un nuovo servizio: selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i servizi esistenti, selezionare l'app desiderata nell'elenco di applicazioni ospitate.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-cognitive-services"></a>Servizi cognitivi di Azure

Con Servizi cognitivi di Azure è possibile infondere intelligenza avanzata direttamente nell'app tramite un set di API, che consentono di sfruttare i vantaggi offerti dagli algoritmi di intelligenza artificiale e di Machine Learning supportati da Microsoft.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per configurare o monitorare le distribuzioni di Servizi cognitivi di Azure:

1. Passare a **Servizi cognitivi**.
2. Per configurare un nuovo servizio, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i servizi esistenti, selezionare il servizio desiderato nell'elenco di servizi ospitati.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-bot-service"></a>Servizio Azure Bot

Il servizio Azure Bot estende l'applicazione standard aggiungendo un'interfaccia bot naturale che usa funzionalità di intelligenza artificiale e Machine Learning per creare una nuova modalità di interazione con i clienti.

### <a name="action"></a>Azione

Per configurare o monitorare le distribuzioni dei servizi Azure Bot:

1. Passare a **Servizi Bot**.
2. Per configurare un nuovo servizio, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i servizi esistenti, selezionare il bot desiderato nell'elenco di servizi ospitati.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.BotService%2FbotServices]" submitText="Go to Bot Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-devops"></a>Azure DevOps

Nel percorso verso l'innovazione si incontreranno inevitabilmente le procedure DevOps. Microsoft offre da molto tempo un prodotto locale noto come Team Foundation Server (TFS). Durante il proprio percorso verso l'innovazione, Microsoft ha sviluppato Azure DevOps, un servizio basato sul cloud che offre strumenti per la compilazione e il rilascio con il supporto di molti linguaggi e destinazioni. Per altre informazioni, vedere [Azure DevOps](https://docs.microsoft.com/azure/devops).

## <a name="visual-studio-app-center"></a>Visual Studio App Center

Con le app per dispositivi mobili che continuano a crescere in popolarità, si avverte sempre di più l'esigenza di una piattaforma in grado di offrire test automatizzati su dispositivi reali con varie configurazioni. Oltre a offrire un ambiente in cui testare le applicazioni in iOS, Android, Windows e macOS, Visual Studio App Center fornisce una piattaforma di monitoraggio con la possibilità di sfruttare Azure Application Insights per analizzare in modo semplice e immediato i dati di telemetria. Per altre informazioni, vedere [Panoramica di Visual Studio App Center](https://docs.microsoft.com/appcenter).

Visual Studio App Center include inoltre un servizio di notifica che consente di inviare notifiche all'app su più piattaforme con una singola chiamata, senza la necessità di contattare singolarmente ogni servizio. Per altre informazioni, vedere [Visual Studio App Center Push (ACP)](https://docs.microsoft.com/appcenter/push).

### <a name="learn-more"></a>Altre informazioni

- [Panoramica del Servizio app](https://docs.microsoft.com/azure/app-service/overview)
- [App Web per contenitori: eseguire un contenitore personalizzato](https://docs.microsoft.com/azure/app-service/containers/quickstart-docker)
- [Introduzione a Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview)
- [Azure per sviluppatori .NET e .NET Core](https://docs.microsoft.com/dotnet/azure/?view=azure-dotnet)
- [Documentazione di Azure SDK per Python](https://docs.microsoft.com/azure/python)
- [Azure per sviluppatori cloud Java](https://docs.microsoft.com/azure/java/?view=azure-java-stable)
- [Creare un'app Web PHP in Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-php)
- [Documentazione di Azure SDK per JavaScript](https://docs.microsoft.com/azure/javascript)
- [Documentazione di Azure SDK per Go](https://docs.microsoft.com/azure/go)
- [Soluzioni DevOps](https://azure.microsoft.com/solutions/devops)

# <a name="create-cloud-native-appstabcloudnative"></a>[Creare app native del cloud](#tab/CloudNative)

<!-- markdownlint-disable MD026 -->

## <a name="what-are-cloud-native-applications"></a>Che cosa sono le applicazioni native del cloud?

Le applicazioni native del cloud sono create da zero e ottimizzate per le prestazioni e la scalabilità del cloud. Sono basate su architetture di microservizi ad accoppiamento debole, usano servizi gestiti, possono essere osservabili e sfruttano la distribuzione continua per garantire affidabilità e accelerare il time-to-market. Sono in genere portabili e possono essere eseguite in ambienti dinamici come cloud pubblici, privati e ibridi. Le applicazioni native del cloud vengono in genere create adottando uno o più approcci seguenti:

- Microservizi
- Senza server
- Contenitori

## <a name="microservices"></a>Microservizi

I microservizi offrono uno stile di architettura software in cui le app sono composte da piccoli moduli indipendenti che comunicano tra loro tramite contratti API ben definiti. Questi moduli di servizi sono costituiti da blocchi predefiniti con un alto livello di disaccoppiamento, abbastanza piccoli da implementare una singola funzionalità. I microservizi consentono di:

- Creare servizi in modo indipendente.
- Ridimensionare i servizi in modo autonomo.
- Usare gli approcci più appropriati per la distribuzione e i linguaggi di programmazione.
- Isolare i punti di errore.
- Generare più rapidamente valore.

### <a name="azure-kubernetes-service-aks"></a>Servizio Azure Kubernetes

Usare un servizio Kubernetes completamente gestito per il provisioning, l'aggiornamento e il ridimensionamento delle risorse cluster su richiesta. Il servizio Azure Kubernetes semplifica la distribuzione e la gestione di applicazioni in contenitori. Offre Kubernetes serverless, un'esperienza CI/CD integrata, oltre a sicurezza e governance di livello aziendale. È possibile unificare i team di sviluppo e delle operazioni in una singola piattaforma per velocizzare le attività di compilazione, distribuzione e ridimensionamento delle applicazioni, in tutta sicurezza.

#### <a name="action"></a>Azione

Per configurare o monitorare un servizio Azure Kubernetes:

1. Passare a **Servizi Kubernetes**.
2. Per configurare un nuovo servizio, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i servizi esistenti, selezionare il servizio Kubernetes desiderato nell'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.ContainerService%2FmanagedClusters]" submitText="Go to Azure Kubernetes services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="event-based-solutions"></a>Soluzioni basate su eventi

### <a name="azure-functions"></a>Funzioni di Azure

Funzioni di Azure offre una piattaforma per l'esecuzione di piccole unità di codice, o funzioni, all'interno del cloud. Le funzioni possono essere un modo per avviare il refactoring del codice in un'architettura di microservizi.

Il runtime di Funzioni di Azure supporta molti linguaggi, tra cui C#, Java, JavaScript e Python. Per l'elenco completo, vedere [Linguaggi supportati in Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/supported-languages).

Un altro vantaggio delle funzioni consiste nella possibilità di attivarle tramite azioni ed eventi diversi, ad esempio HTTPTriggers, TimerTriggers e trigger di altri servizi di Azure, come Archiviazione BLOB, Griglia di eventi e il bus di servizio. Per altre informazioni su trigger e binding, vedere [Concetti relativi a trigger e binding in Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

#### <a name="action"></a>Azione

Per configurare o monitorare le distribuzioni di Funzioni di Azure:

1. Passare ad **App per le funzioni**.
2. Per configurare una nuova app, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire le app esistenti, selezionare l'app desiderata dall'elenco di app per le funzioni.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites/kind/functionapp]" submitText="Go to Azure Functions" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="serverless-solutions"></a>Soluzioni serverless

È possibile creare app native del cloud senza occuparsi del provisioning e della gestione dell'infrastruttura, usando una piattaforma completamente gestita in cui scalabilità, disponibilità e prestazioni vengono gestite automaticamente. I vantaggi delle soluzioni serverless di Azure includono:

- Maggiore velocità di sviluppo.
- Aumento delle prestazioni del team.
- Miglioramento dell'impatto organizzativo.

### <a name="azure-logic-apps"></a>App per la logica di Azure

È possibile integrare i dati e le app invece di scrivere codice di integrazione complesso tra sistemi diversi. App per la logica di Azure consente di creare visivamente flussi di lavoro serverless e di usare le proprie API, funzioni serverless o connettori SaaS (Software as a Service) predefiniti, inclusi Salesforce, Microsoft Office 365 e Dropbox.

#### <a name="action"></a>Azione

Per configurare o monitorare App per la logica di Azure:

1. Passare ad **App per la logica**.
2. Per configurare una nuova app, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire le app esistenti, selezionare l'app per la logica desiderata dall'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Logic%2Fworkflows]" submitText="Go to Azure Logic Apps" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="serverless-api-management"></a>Gestione di API serverless

Con Gestione API di Azure, un servizio completamente gestito che offre un modello di utilizzo progettato e implementato per adattarsi in modo organico alle applicazioni serverless, è possibile pubblicare, proteggere, trasformare, gestire e monitorare le API.

#### <a name="action"></a>Azione

Per configurare o monitorare i servizi Gestione API:

1. Passare a **Servizi Gestione API**.
2. Per configurare un nuovo servizio, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i servizi esistenti, selezionare il servizio desiderato nell'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="containers"></a>Contenitori

Per la modernizzazione del portfolio di applicazioni, Azure offre diversi servizi contenitore per eseguire la migrazione delle app esistenti in contenitori, oltre che per creare app di microservizi native del cloud in modo da offrire più rapidamente valore agli utenti. Per sviluppare, aggiornare e distribuire le applicazioni in contenitori, è possibile usare strumenti di CI/CD e di sviluppo end-to-end. Per gestire i contenitori su larga scala, è disponibile un servizio di orchestrazione dei contenitori Kubernetes completamente gestito che si integra con Azure Active Directory. Ovunque ci si trovi nel percorso di modernizzazione delle app, è possibile accelerare lo sviluppo di applicazioni in contenitori rispettando al tempo stesso i requisiti di sicurezza.

### <a name="azure-container-instances"></a>Istanze di Azure Container

È possibile eseguire contenitori Docker su richiesta in un ambiente di Azure gestito e serverless. Istanze di Azure Container è una soluzione adatta a qualsiasi scenario e funziona anche in contenitori isolati senza orchestrazione. Eseguendo i carichi di lavoro in Istanze di Azure Container, è possibile concentrarsi sulla progettazione e sulla creazione di applicazioni invece di gestire l'infrastruttura che le esegue.

### <a name="action"></a>Azione

Per configurare o monitorare le istanze di contenitore:

1. Passare a **Istanze di Container**.
2. Configurare una nuova istanza di contenitore: selezionare **Aggiungi** e seguire le istruzioni.
3. Gestire le istanze di contenitore esistenti: selezionare l'istanza di contenitore desiderata nell'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ContainerInstance%2FcontainerGroups]" submitText="Go to Container instances" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

Azure Red Hat OpenShift offre funzionalità di distribuzione flessibili e self-service per cluster OpenShift completamente gestiti. È possibile garantire la conformità alle normative e concentrarsi sullo sviluppo di applicazioni, mentre i nodi di applicazioni, master e infrastruttura vengono corretti tramite patch, aggiornati e monitorati da Microsoft e Red Hat. È possibile scegliere il proprio registro e le proprie soluzioni di rete, archiviazione e CI/CD o, in alternativa, usare subito soluzioni predefinite con gestione automatizzata del codice sorgente, creazione di contenitori e applicazioni, distribuzioni, scalabilità, gestione dell'integrità e altro ancora.

**Passare ad [Azure Red Hat OpenShift](https://docs.microsoft.com/azure/openshift/intro-openshift)**

# <a name="isolate-points-of-failuretabisolatepointsoffailure"></a>[Isolare i punti di errore](#tab/IsolatePointsOfFailure)

Quando si avvia la transizione dalla fase di test iniziale, valutare come isolare e rimuovere i punti di errore. Considerata la natura distribuita della piattaforma cloud Azure, è possibile progettare l'applicazione per ridurre al minimo gli errori migliorando al tempo stesso le prestazioni.

## <a name="azure-front-door-service"></a>Servizio Frontdoor di Azure

Il servizio Frontdoor di Azure offre un punto di ingresso sicuro e scalabile per distribuire l'applicazione in tutto il mondo. Questo servizio combina l'ottimizzazione del traffico per migliorare le prestazioni con il failover globale immediato. È preferibile scegliere il servizio Frontdoor di Azure rispetto a Gestione traffico di Azure se è necessaria la terminazione del protocollo TLS (Transport Layer Security) (offload SSL) o l'elaborazione del livello di applicazioni per ogni richiesta HTTP/HTTPS.

### <a name="action"></a>Azione

Per configurare o monitorare Frontdoor:

1. Passare a **Frontdoor**.
2. Per configurare una nuova istanza di Frontdoor, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire le istanze di Frontdoor esistenti, selezionare l'istanza di Frontdoor desiderata dall'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ffrontdoors]" submitText="Go to Front Doors" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="traffic-manager"></a>Gestione traffico

Gestione traffico fornisce il bilanciamento del carico basato su DNS che può essere instradato in base a diverse regole. Questa funzionalità consente di garantire la resilienza in caso di errore dei servizi distribuiti. È anche possibile configurare Gestione traffico per usare sia il routing basato su errori sia il routing basato su prestazioni, in modo da offrire la migliore esperienza possibile in base all'area geografica.

### <a name="action"></a>Azione

Per configurare o monitorare i profili di Gestione traffico:

1. Passare a **Profili di Gestione traffico**.
2. Per configurare un nuovo profilo, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i profili esistenti, selezionare il profilo desiderato nell'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ftrafficmanagerprofiles]" submitText="Go to Traffic Manager profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-content-delivery-network"></a>Rete per la distribuzione di contenuti di Azure

Azure offre una rete per la distribuzione di contenuti (CDN) distribuita che garantisce la distribuzione tempestiva degli asset tramite memorizzazione nella cache in prossimità degli utenti. Questa modalità di memorizzazione consente di migliorare le esperienze dei clienti e di evitare problemi durante il download dei contenuti a causa di errori di rete tra l'endpoint della rete CDN e il data center che ospita l'applicazione. La rete CDN può essere usata anche da applicazioni non ospitate in Azure.

### <a name="action"></a>Azione

Per configurare o monitorare i profili di rete CDN:

1. Passare a **Profili CDN**.
2. Per configurare un nuovo profilo, selezionare **Aggiungi** e seguire le istruzioni.
3. Per gestire i profili esistenti, selezionare il profilo desiderato nell'elenco.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.cdn%2Fprofiles]" submitText="Go to CDN profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>Altre informazioni

- [Frontdoor di Azure](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
- [Gestione traffico](https://docs.microsoft.com/azure/traffic-manager)
- [Rete per la distribuzione di contenuti](https://docs.microsoft.com/azure/cdn)
