---
title: Baseline di gestione ottimizzata in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Miglioramenti comuni per la baseline di gestione
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: cfe7fdfa47b04cbcff7e09b18c5ba6a0b4fec795
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565519"
---
# <a name="enhanced-management-baseline-in-azure"></a>Baseline di gestione ottimizzata in Azure

Le prime tre discipline di gestione del cloud descrivono una baseline di gestione. Negli articoli precedenti di questa guida è stata descritta una soluzione MVP (Minimum Viable Product) per i servizi di gestione del cloud, indicata come baseline di gestione. Questo articolo illustra alcuni miglioramenti comuni della baseline.

Lo scopo della baseline di gestione è creare un'offerta coerente che fornisca un livello minimo di impegno aziendale per *tutti* i carichi di lavoro supportati. Con questa baseline di offerte di gestione ripetibili e comuni, il team può offrire una gestione operativa altamente ottimizzata con una deviazione minima.

Tuttavia, potrebbe essere necessario un impegno maggiore per l'organizzazione, oltre all'offerta standard. L'immagine e l'elenco che seguono mostrano tre modi per espandere la baseline di gestione.

![Oltre la baseline di gestione del cloud](../../_images/manage/beyond-the-baseline.png)

- **Operazioni per i carichi di lavoro:**
  - investimento maggiore in operazioni per carico di lavoro.
  - Massimo grado di resilienza.
  - Suggerite per circa il 20% dei carichi di lavoro che determinano un valore di business.
  - Generalmente riservate ai carichi di lavoro ad alta criticità o cruciali.
- **Operazioni della piattaforma:**
  - investimenti in operazioni distribuiti su molti carichi di lavoro.
  - I miglioramenti della resilienza hanno effetto su tutti i carichi di lavoro che usano la piattaforma definita.
  - Sono consigliati per circa il 20% delle piattaforme con la massima criticità.
  - Generalmente riservate ai carichi di lavoro con criticità medio-alta.
- **Baseline di gestione ottimizzata:**
  - investimento minimo relativo in operazioni.
  - Impegni aziendali leggermente migliorati tramite l'aggiunta di strumenti e processi operativi nativi del cloud.

Per le operazioni dei carichi di lavoro e per quelle della piattaforma è necessario apportare cambiamenti ai principi di progettazione e architettura. Questi cambiamenti possono richiedere del tempo e generare un aumento delle spese operative. Per ridurre il numero di carichi di lavoro che richiedono tali investimenti, una baseline di gestione ottimizzata può assicurare un miglioramento sufficiente per l'impegno aziendale.

La tabella seguente illustra alcuni processi, strumenti e potenziali effetti comuni nelle baseline di gestione ottimizzate dei clienti:

| Disciplina  | Process  | Strumento | Impatto potenziale | Altre informazioni |
|---|---|---|---|---|
|Inventario e visibilità|Rilevamento modifiche del servizio|Diagramma delle risorse di Azure|Una maggiore visibilità delle modifiche apportate ai servizi di Azure può aiutare a rilevare tempestivamente gli effetti negativi o a correggerli più rapidamente.|[Panoramica di Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview)|
|Inventario e visibilità|Integrazione di Gestione dei servizi IT|IT Service Management Connector|La connessione automatizzata di Gestione dei servizi IT crea consapevolezza in anticipo.|[Connettore di Gestione dei servizi IT](https://docs.microsoft.com/azure/azure-monitor/platform/itsmc-overview)|
|Conformità operativa|Automazione delle operazioni|Automazione di Azure|Automatizzare la conformità operativa per una risposta più rapida e accurata al cambiamento.|Vedere le sezioni seguenti|
|Conformità operativa|Operazioni multicloud|Ruolo di lavoro ibrido per runbook di Automazione di Azure|Automatizzare le operazioni tra più cloud.|[Panoramica del ruolo di lavoro ibrido per runbook](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)|
|Conformità operativa|Automazione guest| Configurazione dello stato desiderato (DSC)|Configurazione basata su codice dei sistemi operativi guest per ridurre gli errori e le differenze di configurazione.|[Panoramica di DSC](https://docs.microsoft.com/powershell/scripting/dsc/overview/overview)|
|Protezione e ripristino|Notifica delle violazioni|Centro sicurezza di Azure|Estendere la protezione per includere i trigger di ripristino da violazioni della sicurezza.|Vedere le sezioni seguenti|

::: zone target="docs"

## <a name="azure-automation"></a>Automazione di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-automationtabazureautomation"></a>[Automazione di Azure](#tab/AzureAutomation)

::: zone-end

Automazione di Azure fornisce un sistema centralizzato per la gestione dei controlli automatizzati. In Automazione di Azure è possibile eseguire semplici processi di correzione, ridimensionamento e ottimizzazione in risposta a metriche ambientali. Questi processi riducono il sovraccarico associato all'elaborazione manuale degli eventi imprevisti.

Soprattutto, la correzione automatizzata può essere implementata quasi in tempo reale, con una riduzione significative delle interruzioni per i processi aziendali. Uno studio delle interruzioni più comuni consente di identificare le attività all'interno dell'ambiente che potrebbero essere automatizzate.

### <a name="runbooks"></a>Runbook

Il runbook è l'unità di base di codice per offrire correzione automatizzata. I runbook contengono le istruzioni per la correzione o il ripristino in seguito a un evento imprevisto.

Per creare o gestire runbook:

1. Passare ad [Automazione di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Selezionare **Account di automazione** e scegliere uno degli account nell'elenco.
1. Passare ad **Automazione processi**.
1. Con le opzioni presentate, è possibile creare o gestire runbook, pianificazioni e altre funzionalità di correzione automatizzata.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
::: zone target="docs"

## <a name="azure-security-center"></a>Centro sicurezza di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-security-centertabazuresecuritycenter"></a>[Centro sicurezza di Azure](#tab/AzureSecurityCenter)

::: zone-end

Anche Centro sicurezza di Azure svolge un ruolo importante nella strategia di protezione e ripristino. Consente di monitorare la sicurezza di computer, reti, archiviazione, servizi dati e applicazioni.

Centro sicurezza di Azure offre il rilevamento avanzato delle minacce tramite Machine Learning e analisi comportamentale per semplificare l'identificazione delle minacce attive destinate alle risorse di Azure. Fornisce inoltre protezione dalle minacce in grado di bloccare malware e altro codice indesiderato e riduce la superficie esposta ad attacchi di forza bruta e ad altre minacce per la rete.

Quando identifica una minaccia, Centro sicurezza attiva un avviso di sicurezza con i passaggi necessari per rispondere a un attacco. Fornisce inoltre un report con informazioni sulla minaccia rilevata.

Il Centro sicurezza di Azure è disponibile in due livelli: gratuito e Standard. Funzionalità come le raccomandazioni di sicurezza sono disponibili nel livello gratuito. Il livello Standard offre protezione aggiuntiva, tra cui il rilevamento delle minacce avanzato e la protezione per i carichi di lavoro cloud ibridi.

::: zone target="chromeless"

### <a name="action"></a>Azione

#### <a name="try-standard-tier-for-free-for-your-first-30-days"></a>È possibile provare gratuitamente il livello standard per i primi 30 giorni.

Dopo aver abilitato e configurato i criteri di sicurezza per le risorse della sottoscrizione, è possibile visualizzare lo stato di sicurezza delle risorse ed eventuali problemi nel riquadro **Prevenzione**. Anche nel riquadro **Raccomandazioni** è disponibile l'elenco dei problemi riscontrati.

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Per esplorare il Centro sicurezza di Azure, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione del Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center).

::: zone-end
