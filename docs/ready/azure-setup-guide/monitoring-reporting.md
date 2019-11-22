---
title: Monitoraggio e creazione di report in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come configurare il monitoraggio, la creazione di report e gli avvisi per l'ambiente di gestione di Azure.
author: timleyden
ms.author: tileyden
ms.date: 04/09/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: 0ed9f9c1739fc73f4d28bf532bd52bd0a182b2fc
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251356"
---
# <a name="monitoring-and-reporting-in-azure"></a>Monitoraggio e creazione di report in Azure

Azure offre molti servizi che insieme costituiscono una soluzione completa per la raccolta, l'analisi e l'utilizzo di dati di telemetria dall'applicazione, insieme alle risorse di Azure per supportare queste operazioni. Questi servizi possono anche essere estesi per monitorare le risorse locali critiche per ottenere un ambiente di monitoraggio ibrido.

# <a name="azure-monitortabazuremonitor"></a>[Monitoraggio di Azure](#tab/AzureMonitor)

Monitoraggio di Azure offre un solo hub unificato per tutti i dati di monitoraggio e diagnostica in Azure. È possibile usarlo per ottenere visibilità nelle risorse. Monitoraggio di Azure consente di individuare e correggere i problemi e di ottimizzare le prestazioni. Consente inoltre di comprendere il comportamento dei clienti.

- **Monitorare e visualizzare metriche:** le metriche sono valori numerici disponibili dalle risorse di Azure che consentono di determinare l'integrità dei sistemi. È possibile personalizzare i grafici per i dashboard e usare cartelle di lavoro per la creazione di report.

- **Eseguire query e analisi dei log:** i log includono log di attività e log di diagnostica di Azure. È possibile raccogliere log aggiuntivi da altre soluzioni di monitoraggio e gestione per le risorse cloud o locali. Log Analytics fornisce un repository centrale per aggregare tutti questi dati. Da qui è possibile eseguire query per semplificare la risoluzione dei problemi o per visualizzare i dati.

- **Configurare avvisi e azioni:** gli avvisi avvertono in modo proattivo riguardo a eventuali condizioni critiche. È possibile adottare azioni correttive in base a trigger generati da metriche, log o problemi di integrità dei servizi. È possibile configurare diverse notifiche e azioni e inviare i dati agli strumenti di gestione dei servizi IT.

::: zone target="docs"

 Iniziare monitorando gli elementi seguenti:

- [Applicazioni](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Contenitori](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Macchine virtuali](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Reti](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Per monitorare altre risorse, è possibile trovare soluzioni aggiuntive in Azure Marketplace.

Per esplorare Monitoraggio di Azure, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione di Monitoraggio di Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Azione

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

::: zone-end

# <a name="azure-service-healthtabazureservicehealth"></a>[Integrità dei servizi di Azure](#tab/AzureServiceHealth)

Integrità dei servizi di Azure fornisce una visualizzazione personalizzata dell'integrità dei servizi e delle aree di Azure che vengono usati. Le informazioni sui problemi attivi vengono pubblicate in Integrità dei servizi per comprendere meglio l'impatto per le risorse. Sono previsti aggiornamenti regolari per essere informati quando viene risolto il problema.

In Integrità dei servizi vengono anche pubblicati gli eventi di manutenzione pianificata, in modo che gli utenti siano a conoscenza delle modifiche che potrebbero influire sulla disponibilità delle risorse. Configurare gli avvisi di Integrità dei servizi per ricevere notifiche in caso di problemi dei servizi, eventi di manutenzione pianificata o altre modifiche che potrebbero influire sui servizi e sulle aree di Azure che vengono usati.

Integrità dei servizi di Azure include le informazioni seguenti:

- **Stato di Azure:** visualizzazione completa dell'integrità dei servizi di Azure.
- **Integrità dei servizi:** visualizzazione personalizzata dell'integrità dei servizi di Azure.
- **Integrità risorsa:** visualizzazione più dettagliata dell'integrità di ogni singola risorsa.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

## <a name="action"></a>Azione

Per configurare un avviso di Integrità dei servizi:

1. Passare a **Integrità dei servizi**.
2. Selezionare **Avvisi di integrità**.
3. Creare un avviso di integrità dei servizi.

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

Per configurare un avviso di Integrità dei servizi, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere [Documentazione di Integrità dei servizi di Azure](https://docs.microsoft.com/azure/service-health).

::: zone-end

# <a name="azure-advisortabazureadvisor"></a>[Azure Advisor](#tab/AzureAdvisor)

Azure Advisor è un consulente cloud personalizzato che semplifica l'applicazione e l'implementazione delle procedure consigliate per le distribuzioni di Azure. Analizza la configurazione delle risorse e i dati di telemetria sull'utilizzo e consiglia soluzioni utili per ottimizzare l'ambiente. Le raccomandazioni sono suddivise nelle categorie seguenti:

- **Disponibilità elevata:** per migliorare la continuità delle applicazioni cruciali per l'azienda. Le raccomandazioni possono includere l'aggiunta di macchine virtuali a un set di disponibilità o l'aggiunta di endpoint con ridondanza geografica.
- **Sicurezza:** per rilevare le minacce e le vulnerabilità che potrebbero portare a potenziali violazioni della sicurezza. Le raccomandazioni possono includere l'applicazione della crittografia dei dischi o l'abilitazione di gruppi di sicurezza di rete.
- **Prestazioni:** per aumentare la velocità delle applicazioni. Le raccomandazioni possono includere il potenziamento delle prestazioni delle query SQL attraverso la creazione di indici o la riconfigurazione delle impostazioni di gestione del traffico.
- **Costo:** per ottimizzare e ridurre la spesa complessiva di Azure. Le raccomandazioni possono includere il ridimensionamento o l'arresto delle macchine virtuali sottoutilizzate oppure il passaggio a prenotazioni di Azure per ridurre il costo totale di proprietà.
- **Eccellenza operativa:** per migliorare l'efficienza e la gestibilità di processi e flussi di lavoro. Le raccomandazioni possono includere la configurazione e l'applicazione di regole di Criteri di Azure, la correzione di regole di avviso dei log non valide e la configurazione degli avvisi di integrità dei servizi di Azure.

Le raccomandazioni in Advisor sono basate sulle risorse distribuite e sulle azioni intraprese in Azure. È possibile controllare regolarmente Advisor per ottenere le raccomandazioni più recenti.

::: zone target="chromeless"

## <a name="action"></a>Azione

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Explore Azure Advisor" :::

::: zone-end

::: zone target="docs"

Per esplorare Azure Advisor, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Expert/AdvisorBlade).

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione di Azure Advisor](https://docs.microsoft.com/azure/advisor).

::: zone-end

# <a name="azure-security-centertabazuresecuritycenter"></a>[Centro sicurezza di Azure](#tab/AzureSecurityCenter)

Anche Centro sicurezza di Azure ha un ruolo importante nella strategia di monitoraggio. Consente di monitorare la sicurezza di computer, reti, archiviazione, servizi dati e applicazioni. Centro sicurezza offre il rilevamento delle minacce avanzato tramite Machine Learning e analisi comportamentale per semplificare l'identificazione delle minacce attive per le risorse di Azure. Fornisce inoltre protezione dalle minacce in grado di bloccare malware o altro codice indesiderato e riduce la superficie esposta ad attacchi di forza bruta e ad altre minacce per la rete.

Quando identifica una minaccia, Centro sicurezza attiva un avviso di sicurezza con indicazioni sulle misure da adottare per rispondere a un attacco. Fornisce inoltre un report con informazioni sulla minaccia rilevata.

Centro sicurezza di Azure è disponibile in due livelli: gratuito e standard. Funzionalità come le raccomandazioni di sicurezza sono disponibili gratuitamente. Il livello standard offre protezione aggiuntiva, tra cui il rilevamento delle minacce avanzato e la protezione per i carichi di lavoro cloud ibridi.

::: zone target="chromeless"

## <a name="action"></a>Azione

**È possibile provare gratuitamente il livello standard per i primi 30 giorni.**

Dopo aver attivato e configurato i criteri di sicurezza per le risorse della sottoscrizione, è possibile visualizzarne lo stato di sicurezza ed eventuali problemi nella sezione **Prevenzione**. Anche nel riquadro **Raccomandazioni** è disponibile l'elenco dei problemi riscontrati.

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Per esplorare il Centro sicurezza di Azure, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione del Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center).

::: zone-end
