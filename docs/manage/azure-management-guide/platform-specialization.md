---
title: Specializzazione della piattaforma per la gestione del cloud in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migliorare le operazioni di gestione del cloud specifiche della piattaforma
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 0386a8c30758cce6c1c3d23bfa73d1f90e919692
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556973"
---
# <a name="platform-specialization-for-cloud-management"></a>Specializzazione della piattaforma per la gestione del cloud

In modo simile alla baseline di gestione ottimizzata, la specializzazione della piattaforma è un'estensione della baseline di gestione standard. Per un elenco puntato visivo delle opportunità modi disponibili per espandere la baseline di gestione, vedere di seguito. Questo articolo riguarda l'opzione di specializzazione della piattaforma.

![Oltre la baseline di gestione del cloud](../../_images/manage/beyond-the-baseline.png)

- **Operazioni per i carichi di lavoro:** investimento maggiore in operazioni per i carichi di lavoro. Massimo grado di resilienza. Suggerite per circa il 20% dei carichi di lavoro che determinano un valore di business. Generalmente riservate ai carichi di lavoro ad alta criticità o cruciali.
- **Operazioni della piattaforma:** investimenti in operazioni distribuiti su molti carichi di lavoro. I miglioramenti della resilienza hanno effetto su tutti i carichi di lavoro che sfruttano la piattaforma definita. Suggerite per circa il 20% delle piattaforme con la massima criticità. Generalmente riservate ai carichi di lavoro con criticità medio-alta.
- **Baseline di gestione ottimizzata:** investimento minimo relativo in operazioni. Impegni aziendali leggermente migliorati tramite l'aggiunta di strumenti e processi operativi nativi del cloud.

Per le operazioni dei carichi di lavoro e per quelle della piattaforma sarà necessario apportare cambiamenti in principi di progettazione e architettura. Questi cambiamenti possono richiedere del tempo e generare un aumento delle spese operative. Per ridurre il numero di carichi di lavoro che richiedono tali investimenti, una baseline di gestione ottimizzata potrebbe assicurare un miglioramento sufficiente per l'impegno aziendale.

La tabella seguente illustra alcuni processi, strumenti e potenziali effetti comuni nelle baseline di gestione ottimizzate dei clienti.

|Process  |Strumento  |Scopo  |Livello di gestione suggerito  |
|---------|---------|---------|---------|
|Miglioramento della progettazione dei sistemi|Azure Architecture Framework|Miglioramento della progettazione dell'architettura della piattaforma per migliorare le operazioni|
|Correzione automatizzata|Automazione di Azure|Automazione specifica della piattaforma in risposta a dati della piattaforma avanzati|Operazioni della piattaforma|
|Catalogo di servizi|Centro applicazioni gestite|Disponibilità di un catalogo self-service di soluzioni approvate che soddisfano gli standard aziendali|Operazioni della piattaforma|
|Prestazioni dei contenitori|Monitoraggio di Azure per contenitori|Monitoraggio e diagnostica dei contenitori|Operazioni della piattaforma|
|Prestazioni dei dati PaaS|Azure SQL Analytics|Monitoraggio e diagnostica dei database PaaS|Operazioni della piattaforma|
|Prestazioni dei dati IaaS|Controllo integrità di SQL Server|Monitoraggio e diagnostica dei database IaaS|Operazioni della piattaforma|

## <a name="high-level-process"></a>Processo di alto livello

La specializzazione della piattaforma consiste nell'esecuzione disciplinata dei quattro processi seguenti in un approccio iterativo. Ogni processo viene descritto in maggior dettaglio nelle sezioni seguenti di questo articolo.

- **Miglioramento della progettazione dei sistemi:** migliorare la progettazione di sistemi comuni (o piattaforme) in modo da ridurre al minimo le interruzioni.
- **Automazione della correzione:** alcuni miglioramenti non sono economicamente convenienti. In questi casi, può essere opportuno automatizzare la correzione e ridurre l'impatto delle interruzioni.
- **Scalabilità della soluzione:** con il miglioramento della progettazione dei sistemi e della correzione automatizzata, questi cambiamenti possono essere applicati gradualmente nell'intero ambiente tramite il catalogo di servizi.
- **Miglioramento continuo:** è possibile usare vari strumenti di monitoraggio per individuare i miglioramenti incrementali che possono essere affrontati come fase successiva della progettazione dei sistemi, dell'automazione e della scalabilità.

::: zone target="docs"

## <a name="improve-system-design"></a>Miglioramento della progettazione dei sistemi

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Miglioramento della progettazione dei sistemi](#tab/SystemsDesign)

::: zone-end

Il miglioramento della progettazione dei sistemi è l'approccio più efficace per migliorare le operazioni di qualsiasi piattaforma comune. Tramite questi miglioramenti, è possibile aumentare la stabilità e ridurre le interruzioni per il business. La progettazione di singoli sistemi non rientra nell'ambito della visione dell'ambiente acquisita in Cloud Adoption Framework. Come complemento a questo framework, Azure Architecture Framework fornisce le procedure consigliate per migliorare la resilienza e la progettazione di un sistema specifico. I miglioramenti possono essere applicati alla progettazione dei sistemi di una piattaforma o di un carico di lavoro specifico.

Azure Architecture Framework è incentrato sul miglioramento di cinque pilastri della progettazione dei sistemi:

- **Scalabilità:** scalabilità degli asset comuni della piattaforma per gestire l'aumento del carico.
- **Disponibilità:** riduzione delle interruzioni per il business grazie alla possibilità di migliorare il tempo di attività.
- **Resilienza**: miglioramento dei tempi di ripristino per ridurre la durata delle interruzioni.
- **Sicurezza:** protezione di applicazioni e dati da minacce esterne.
- **Gestione:** processi operativi specifici per gli asset comuni della piattaforma.

La maggior parte delle interruzioni per il business equivale a una forma di debito tecnico o a una carenza dell'architettura. Per le distribuzioni esistenti, i miglioramenti della progettazione dei sistemi possono essere visti come pagamenti a fronte del debito tecnico esistente. Per le nuove distribuzioni, possono essere visti come misure di prevenzione del debito tecnico. La scheda successiva, "Correzione automatizzata", illustra come gestire il debito tecnico che non può o non dovrebbe essere risolto.

Vedere altre informazioni su [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) per migliorare la progettazione dei sistemi.

Dopo aver migliorato la progettazione dei sistemi, tornare in questo articolo per trovare nuove opportunità di miglioramento e scalabilità nell'intero ambiente.

::: zone target="docs"

## <a name="automated-remediation"></a>Correzione automatizzata

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correzione automatizzata](#tab/AutomatedRemediation)

::: zone-end

Alcuni debiti tecnici non possono essere risolti. La risoluzione potrebbe essere troppo costosa da applicare oppure, anche se pianificata, potrebbe richiedere tempi lunghi. Può essere che l'interruzione per il business non abbia un impatto significativo o che la priorità aziendale sia di provvedere rapidamente al ripristino invece di investire in resilienza.

Quando la risoluzione del debito tecnico non è il percorso desiderato, il passaggio successivo è in genere la correzione automatizzata. L'approccio più comune consiste nell'uso di Automazione di Azure o di Monitoraggio di Azure per rilevare tendenze e fornire la correzione automatizzata.

Per istruzioni sulla correzione automatica, vedere questo articolo su [Automazione di Azure e avvisi](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Ridimensionare la soluzione con un catalogo di servizi

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Ridimensionare la soluzione con un catalogo di servizi](#tab/ServiceCatalog)

::: zone-end

L'elemento fondamentale della specializzazione e delle operazioni della piattaforma è un catalogo di servizi ben gestito. È così che i miglioramenti apportati alla progettazione dei sistemi e alla correzione vengono applicati in tutto l'ambiente. Il team della piattaforma cloud collabora con il team dell'automazione del cloud per creare soluzioni ripetibili per le piattaforme più comuni in qualsiasi ambiente. Ma se queste soluzioni non vengono sfruttate in modo coerente, la gestione del cloud diventa poco più di un'offerta di base.

Per ottimizzare l'adozione e ridurre il sovraccarico di manutenzione di qualsiasi piattaforma ottimizzata, è necessario aggiungere la piattaforma a un catalogo di servizi in Azure. Ogni applicazione del catalogo può essere distribuita per l'utilizzo interno tramite il catalogo di servizi o come offerta del Marketplace per i clienti esterni.

Vedere la serie di articoli sulla [pubblicazione in un catalogo di servizi](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app) per informazioni sulla procedura.

### <a name="deploy-applications-from-the-service-catalog"></a>Distribuire applicazioni dal catalogo di servizi

1. Nella portale di Azure cercare **Centro applicazioni gestite (anteprima)** .
2. Fare clic su **Applicazioni del catalogo di servizi** nella sezione **Sfoglia** del riquadro di spostamento del portale.
3. Fare clic su **+ Aggiungi** per scegliere una definizione di applicazione dal catalogo di servizi dell'azienda.

Tutte le applicazioni gestite in uso vengono visualizzate qui.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gestire le applicazioni del catalogo di servizi

1. Nella portale di Azure cercare **Centro applicazioni gestite (anteprima)** .
2. Fare clic su **Applicazioni del catalogo di servizi** nella sezione **Servizio** del riquadro di spostamento del portale.

Tutte le applicazioni gestite in uso vengono visualizzate qui.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Miglioramento continuo

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Miglioramento continuo](#tab/ContinuousImprovement)

::: zone-end

La specializzazione e le operazioni della piattaforma dipendono da cicli di feedback efficaci tra i team di adozione, piattaforma, automazione e gestione. Basando questi cicli di feedback sui dati, ogni team è in grado di prendere decisioni oculate. Per rispettare gli impegni aziendali a lungo termine con le operazioni della piattaforma, è importante sfruttare le informazioni specifiche della piattaforma centralizzata. Poiché i contenitori e SQL Server sono le due piattaforme gestite centralmente più comuni, di seguito sono riportati alcuni articoli che consentono di iniziare a usare la raccolta di dati per il miglioramento continuo.

[Prestazioni dei contenitori](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
[Prestazioni dei database PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
[Prestazioni dei database IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
