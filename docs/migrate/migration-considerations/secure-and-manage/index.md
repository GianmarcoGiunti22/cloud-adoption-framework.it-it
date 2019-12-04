---
title: Protezione e gestione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti di monitoraggio e gestione sicuri
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: c03e6d25734a487c317fa9c6904a799dfd53f631
ms.sourcegitcommit: 72df8c1b669146285a8680e05aeceecd2c3b2e83
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74681796"
---
# <a name="secure-monitoring-and-management-tools"></a>Strumenti di monitoraggio e gestione sicuri

Dopo aver completato la migrazione, gli asset migrati devono essere gestiti da operazioni IT controllate. Questo articolo non rappresenta una deviazione dalle procedure operative consigliate. Al contrario, le indicazioni seguenti dovrebbero essere considerate come prodotto minimo funzionante per la protezione e la gestione degli asset migrati, dalle operazioni IT oppure in modo indipendente quando le operazioni IT sono online.

## <a name="monitoring"></a>Monitoraggio

Il *monitoraggio* è l'azione di raccolta e analisi dei dati per determinare le prestazioni, l'integrità e la disponibilità del carico di lavoro aziendale e delle risorse da cui dipende. Azure include più servizi che singolarmente eseguono un'attività o un ruolo specifico nell'area di monitoraggio. Nel loro insieme questi servizi offrono una soluzione completa per la raccolta, l'analisi e l'utilizzo dei dati di telemetria dalle applicazioni del carico di lavoro e dalle risorse di supporto di Azure sottostanti. È possibile ottenere visibilità a livello di integrità e prestazioni delle app, dell'infrastruttura e dei dati in Azure con gli strumenti di monitoraggio del cloud come Monitoraggio di Azure, Log Analytics e Application Insights. Usare questi strumenti di monitoraggio del cloud per intraprendere le azioni necessarie e integrali nelle soluzioni di gestione dei servizi:

- **Monitoraggio di base.** Il monitoraggio di base offre il monitoraggio essenziale delle diverse risorse di Azure. Questi servizi richiedono una configurazione minima e raccolgono i dati di telemetria principali usati dai servizi di monitoraggio Premium.
- **Monitoraggio approfondito delle applicazioni e dell'infrastruttura.** I servizi di Azure seguenti offrono funzionalità avanzate per la raccolta e l'analisi dei dati di monitoraggio a un livello più profondo. Questi servizi sono basati sul monitoraggio di base e sfruttano alcune funzionalità comuni di Azure. Offrono potente analisi con i dati raccolti per fornire informazioni esclusive sulle applicazioni e sull'infrastruttura.

Vedere ulteriori informazioni su [Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) per il monitoraggio degli asset migrati.

## <a name="security-monitoring"></a>Monitoraggio della protezione

Affidarsi al Centro sicurezza di Azure per una gestione unificata del monitoraggio della sicurezza e delle notifiche avanzate per le minacce per i carichi di lavoro cloud ibridi. Il Centro sicurezza offre la visibilità completa e il controllo della sicurezza delle applicazioni cloud in Azure. È possibile rilevare e reagire rapidamente alle minacce e ridurre l'esposizione abilitando la protezione adattiva dalle minacce. Il dashboard predefinito fornisce informazioni dettagliate immediate sugli avvisi di sicurezza e sulle vulnerabilità che richiedono attenzione. Centro sicurezza di Azure può essere utile con molte funzioni, tra cui:

- **Monitoraggio centralizzato dei criteri.** Garantire la conformità con i requisiti di sicurezza normativi o aziendali tramite la gestione centralizzata dei criteri di sicurezza in tutti i carichi di lavoro cloud ibridi.
- **Valutazione continua della sicurezza.** Monitorare la sicurezza dei computer, delle reti, dei servizi di archiviazione e dati e delle applicazioni per individuare potenziali problemi di sicurezza.
- **Consigli operativi.** Correggere le vulnerabilità di sicurezza prima che possano essere sfruttate da utenti malintenzionati. Sono incluse raccomandazioni per la sicurezza classificate in ordine di priorità e di utilità pratica.
- **Difese del cloud avanzate.** Ridurre le minacce con l'accesso JIT (Just-in-Time) alle porte di gestione ed elenchi degli elementi consentiti per controllare le applicazioni in esecuzione nelle macchine virtuali.
- **Avvisi ed eventi imprevisti classificati in ordine di priorità.** Concentrarsi per prima cosa sulle minacce principali con avvisi di sicurezza ed eventi imprevisti classificati in ordine di priorità.
- **Soluzioni di sicurezza integrate.** Raccogliere, eseguire ricerche e analizzare i dati di sicurezza da diverse origini, incluse soluzioni partner connesse.

Altre informazioni sul [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center) per la protezione degli asset migrati.

## <a name="service-health-monitoring"></a>Monitoraggio dell'integrità dei servizi

Integrità dei servizi di Azure fornisce indicazioni e avvisi personalizzati in caso di problemi dei servizi di Azure che influiscono sull'organizzazione. Può inviare notifiche, aiutare a comprendere l'impatto dei problemi e fornire informazioni aggiornate durante la risoluzione. Può anche semplificare la preparazione per la manutenzione pianificata e per le modifiche che potrebbero influire sulla disponibilità delle risorse.

- **Dashboard di integrità dei servizi.** Controllare l'integrità generale di servizi e aree di Azure, con aggiornamenti dettagliati su eventuali problemi correnti, interventi imminenti di manutenzione pianificata e transizioni dei servizi.
- **Avvisi sull'integrità dei servizi.** Configurare avvisi per ricevere notifiche in caso di problemi di un servizio come un'interruzione o un intervento imminente di manutenzione pianificata.
- **Cronologia dell'integrità dei servizi.** Rivedere i problemi passati dei servizi e scaricare i riepiloghi e i report ufficiali di Microsoft.

Leggere altre informazioni su [Integrità dei servizi di Azure](https://docs.microsoft.com/azure/service-health) per rimanere informati sull'integrità delle risorse trasferite.

## <a name="protect-assets-and-data"></a>Proteggere gli asset e i dati

Backup di Azure offre una soluzione per proteggere le macchine virtuali, i file e dati. Backup di Azure può essere utile con molte funzioni, tra cui:

- Backup di macchine virtuali.
- Backup di file.
- Backup dei database di SQL Server.
- Recupero degli asset protetti.

Vedere ulteriori informazioni su [Backup di Azure](https://docs.microsoft.com/azure/backup) per la protezione degli asset migrati.

## <a name="optimize-resources"></a>Ottimizzare le risorse

Azure Advisor è la guida personalizzata per le procedure consigliate di Azure. Analizza i dati di telemetria relativi a configurazioni e utilizzo e offre raccomandazioni per aiutare a ottimizzare le risorse di Azure in termini di disponibilità elevata, sicurezza, prestazioni e costi. Le azioni inline di Advisor consentono di correggere gli errori segnalati dalle raccomandazioni in modo semplice e immediato e di ottimizzare le distribuzioni.

- **Procedure consigliate per Azure.** Ottimizzare le risorse trasferite per la disponibilità elevata, la sicurezza, le prestazioni e i costi.
- **Guida dettagliata.** Correggere in modo efficiente gli errori segnalati dalle raccomandazioni con collegamenti rapidi guidati.
- **Avvisi per nuove raccomandazioni.** Rimanere informati sulle nuove raccomandazioni, ad esempio altre opportunità di dimensionare correttamente le VM per risparmiare sui costi.

Leggere altre informazioni su [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) per l'ottimizzazione delle risorse dopo la migrazione.

## <a name="suggested-skills"></a>Competenze suggerite

Microsoft Learn è un nuovo approccio all'apprendimento. Non è facile essere subito pronti ad assumersi le nuove responsabilità e competenze associate all'adozione del cloud. Microsoft Learn offre un approccio più gratificante all'apprendimento pratico che consente di raggiungere più velocemente i propri obiettivi. Conseguendo punti e livelli è possibile raggiungere traguardi sempre più impegnativi.

Ecco un esempio di percorso di apprendimento personalizzato di Microsoft Learn in linea con la sezione relativa a sicurezza e a gestione di Cloud Adoption Framework: 

[Proteggere i dati nel cloud](https://docs.microsoft.com/learn/paths/secure-your-cloud-data/): Azure è una piattaforma progettata per offrire sicurezza e conformità. Verrà illustrato come sfruttare i servizi predefiniti per archiviare in sicurezza i dati delle app in modo che solo i client e i servizi autorizzati possano accedervi.
