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
ms.openlocfilehash: 5b775feb4b007629a6c93e762c8b02e5d5ef0a8a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565444"
---
# <a name="platform-specialization-for-cloud-management"></a>Specializzazione della piattaforma per la gestione del cloud

In modo simile alla baseline di gestione ottimizzata, la specializzazione della piattaforma è un'estensione della baseline di gestione standard. L'immagine e l'elenco che seguono mostrano come espandere la baseline di gestione. Questo articolo riguarda l'opzione di specializzazione della piattaforma.

![Oltre la baseline di gestione del cloud](../../_images/manage/beyond-the-baseline.png)

- **Operazioni per i carichi di lavoro:** il maggiore investimento in operazioni per carico di lavoro e il massimo livello di resilienza. Queste operazioni sono consigliate per circa il 20% dei carichi di lavoro che generano valore di business. La specializzazione è in genere riservata ai carichi di lavoro ad alta criticità o cruciali.
- **Operazioni della piattaforma:** investimenti in operazioni distribuiti su molti carichi di lavoro. I miglioramenti della resilienza hanno effetto su tutti i carichi di lavoro che usano la piattaforma definita. Queste operazioni sono consigliate per circa il 20% delle piattaforme con la massima criticità. La specializzazione è in genere riservata ai carichi di lavoro con criticità medio-alta.
- **Baseline di gestione ottimizzata:** l'investimento relativamente minimo in operazioni. La specializzazione migliora leggermente gli impegni aziendali tramite l'aggiunta di strumenti e processi operativi nativi del cloud.

Per le operazioni dei carichi di lavoro e per quelle della piattaforma è necessario apportare cambiamenti ai principi di progettazione e architettura. Questi cambiamenti possono richiedere del tempo e generare un aumento delle spese operative. Per ridurre il numero di carichi di lavoro che richiedono tali investimenti, una baseline di gestione ottimizzata potrebbe assicurare un miglioramento sufficiente per l'impegno aziendale.

La tabella seguente illustra alcuni processi, strumenti e potenziali effetti comuni nelle baseline di gestione ottimizzate dei clienti:

|Process  |Strumento  |Scopo  |Livello di gestione suggerito  |
|---------|---------|---------|---------|
|Miglioramento della progettazione dei sistemi|Azure Architecture Framework|Miglioramento della progettazione dell'architettura della piattaforma per migliorare le operazioni|N/D|
|Correzione automatizzata|Automazione di Azure|Automazione specifica della piattaforma in risposta a dati della piattaforma avanzati|Operazioni della piattaforma|
|Catalogo di servizi|Centro applicazioni gestite|Disponibilità di un catalogo self-service di soluzioni approvate che soddisfano gli standard aziendali|Operazioni della piattaforma|
|Prestazioni dei contenitori|Monitoraggio di Azure per contenitori|Monitoraggio e diagnostica dei contenitori|Operazioni della piattaforma|
|Prestazioni dei dati della piattaforma distribuita come servizio (PaaS)|Azure SQL Analytics|Monitoraggio e diagnostica per i database PaaS|Operazioni della piattaforma|
|Prestazioni dei dati dell'infrastruttura distribuita come servizio (IaaS)|Controllo integrità di SQL Server|Monitoraggio e diagnostica per i database IaaS|Operazioni della piattaforma|

## <a name="high-level-process"></a>Processo di alto livello

La specializzazione della piattaforma consiste nell'esecuzione disciplinata dei quattro processi seguenti in un approccio iterativo. Ogni processo viene descritto in maggior dettaglio nelle sezioni seguenti di questo articolo.

- **Miglioramento della progettazione dei sistemi:** migliorare la progettazione di sistemi o piattaforme comuni in modo da ridurre al minimo le interruzioni.
- **Automazione della correzione:** alcuni miglioramenti non sono economicamente convenienti. In questi casi, può essere opportuno automatizzare la correzione dei problemi e ridurre l'impatto delle interruzioni.
- **Scalabilità della soluzione:** con il miglioramento della progettazione dei sistemi e della correzione automatizzata, questi cambiamenti possono essere applicati gradualmente nell'intero ambiente tramite il catalogo di servizi.
- **Miglioramento continuo:** è possibile usare diversi strumenti di monitoraggio per individuare i miglioramenti incrementali, che possono essere affrontati nella fase successiva della progettazione dei sistemi, dell'automazione e della scalabilità.

::: zone target="docs"

## <a name="improve-system-design"></a>Miglioramento della progettazione dei sistemi

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Miglioramento della progettazione dei sistemi](#tab/SystemsDesign)

::: zone-end

Il miglioramento della progettazione dei sistemi è l'approccio più efficace per migliorare le operazioni di qualsiasi piattaforma comune. Tramite questi miglioramenti, è possibile aumentare la stabilità e ridurre le interruzioni per il business. La progettazione di singoli sistemi non rientra nell'ambito della visione dell'ambiente acquisita in Cloud Adoption Framework per Azure.

Come complemento a questo framework, Azure Architecture Framework fornisce le procedure consigliate per migliorare la resilienza e la progettazione di un sistema specifico. I miglioramenti possono essere applicati alla progettazione dei sistemi di una piattaforma o di un carico di lavoro specifico.

Azure Architecture Framework è incentrato sul miglioramento di cinque pilastri della progettazione dei sistemi:

- **Scalabilità:** scalabilità degli asset comuni della piattaforma per gestire l'aumento del carico
- **Disponibilità:** riduzione delle interruzioni per il business grazie alla possibilità di migliorare il tempo di attività
- **Resilienza**: miglioramento dei tempi di ripristino per ridurre la durata delle interruzioni
- **Sicurezza:** protezione di applicazioni e dati da minacce esterne
- **Gestione:** processi operativi specifici per gli asset comuni della piattaforma

Il debito tecnico e gli errori architetturali causano la maggior parte delle interruzioni per il business. Per le distribuzioni esistenti, i miglioramenti della progettazione dei sistemi possono essere visti come pagamenti a fronte del debito tecnico esistente. Per le nuove distribuzioni, è possibile considerare questi miglioramenti come mezzo per evitare il debito tecnico.

La scheda successiva, **Correzione automatizzata**, illustra come gestire il debito tecnico che non può o non dovrebbe essere risolto.

Vedere altre informazioni su [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) per migliorare la progettazione dei sistemi.

Dopo aver migliorato la progettazione dei sistemi, tornare in questo articolo per trovare nuove opportunità di miglioramento e scalabilità nell'intero ambiente.

::: zone target="docs"

## <a name="automated-remediation"></a>Correzione automatizzata

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correzione automatizzata](#tab/AutomatedRemediation)

::: zone-end

Alcuni debiti tecnici non possono essere risolti. La risoluzione potrebbe essere troppo costosa da implementare o potrebbe essere pianificata ma con una durata prolungata del progetto. L'interruzione potrebbe non avere un effetto significativo sul business. Oppure l'organizzazione potrebbe considerare prioritario un ripristino rapido rispetto a un investimento in resilienza.

Se la risoluzione del debito tecnico non è l'approccio desiderato, il passaggio successivo è in genere la correzione automatizzata. L'approccio più comune consiste nell'uso di Automazione di Azure o di Monitoraggio di Azure per rilevare tendenze e fornire la correzione automatizzata.

Per istruzioni sulla correzione automatica, vedere questo articolo su [Automazione di Azure e avvisi](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Ridimensionare la soluzione con un catalogo di servizi

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Ridimensionare la soluzione con un catalogo di servizi](#tab/ServiceCatalog)

::: zone-end

L'elemento fondamentale della specializzazione e delle operazioni della piattaforma è un catalogo di servizi ben gestito. Con l'uso di un catalogo, i miglioramenti apportati alla progettazione dei sistemi e alla correzione vengono applicati in tutto l'ambiente.

Il team della piattaforma cloud collabora con il team dell'automazione del cloud per creare soluzioni ripetibili per le piattaforme più comuni in qualsiasi ambiente. Ma se queste soluzioni non vengono usate in modo coerente, la gestione del cloud diventa poco più di un'offerta di base.

Per ottimizzare l'adozione e ridurre il sovraccarico di manutenzione di qualsiasi piattaforma ottimizzata, è necessario aggiungere la piattaforma a un catalogo di servizi in Azure. Ogni applicazione del catalogo può essere distribuita per l'utilizzo interno tramite il catalogo di servizi o come offerta del Marketplace per i clienti esterni.

Vedere la serie di articoli sulla [pubblicazione in un catalogo di servizi](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app) per informazioni sulla procedura.

### <a name="deploy-applications-from-the-service-catalog"></a>Distribuire applicazioni dal catalogo di servizi

1. Nel portale di Azure passare a **Centro applicazioni gestite (anteprima)** .
2. Nel riquadro **Sfoglia** selezionare **Applicazioni del catalogo di servizi**.
3. Fare clic su **+ Aggiungi** per scegliere una definizione di applicazione nel catalogo di servizi dell'azienda.

Vengono visualizzate tutte le applicazioni gestite in uso.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gestire le applicazioni del catalogo di servizi

1. Nel portale di Azure passare a **Centro applicazioni gestite (anteprima)** .
1. Nel riquadro **Servizio** selezionare **Applicazioni del catalogo di servizi**.

Vengono visualizzate tutte le applicazioni gestite in uso.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Miglioramento continuo

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Miglioramento continuo](#tab/ContinuousImprovement)

::: zone-end

La specializzazione e le operazioni della piattaforma dipendono da cicli di feedback efficaci tra i team di adozione, piattaforma, automazione e gestione. Basando questi cicli di feedback sui dati, ogni team è in grado di prendere decisioni oculate. Per rispettare gli impegni aziendali a lungo termine con le operazioni della piattaforma, è importante usare informazioni specifiche della piattaforma centralizzata.

I contenitori e SQL Server sono le due piattaforme a gestione centralizzata più comuni. Questi articoli possono essere utili per iniziare a usare la raccolta di dati sul miglioramento continuo in queste piattaforme:

- [Prestazioni dei contenitori](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Prestazioni dei database PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Prestazioni dei database IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
