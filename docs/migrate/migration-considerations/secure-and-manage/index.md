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
ms.openlocfilehash: 14bd697a3332466fb97043d3420d80b1dca50679
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818132"
---
# <a name="secure-monitoring-and-management-tools"></a>Strumenti di monitoraggio e gestione sicuri

Dopo aver completato la migrazione, gli asset migrati devono essere gestiti da operazioni IT controllate. Questo articolo non intende suggerire deviazioni dalle procedure operative consigliate. Al contrario, le indicazioni seguenti dovrebbero essere considerate come prodotto minimo funzionante per la protezione e la gestione degli asset migrati, dalle operazioni IT oppure in modo indipendente quando le operazioni IT sono online.

## <a name="monitoring"></a>Monitoraggio

Il *monitoraggio* è l'azione di raccolta e analisi dei dati per determinare le prestazioni, l'integrità e la disponibilità del carico di lavoro aziendale e delle risorse da cui dipende. Azure include più servizi che singolarmente eseguono un'attività o un ruolo specifico nell'area di monitoraggio. Nel loro insieme questi servizi offrono una soluzione completa per la raccolta, l'analisi e l'utilizzo dei dati di telemetria dalle applicazioni del carico di lavoro e dalle risorse di supporto di Azure sottostanti. È possibile ottenere visibilità a livello di integrità e prestazioni delle app, dell'infrastruttura e dei dati in Azure con gli strumenti di monitoraggio del cloud come Monitoraggio di Azure, Log Analytics e Application Insights. Usare questi strumenti di monitoraggio del cloud per intraprendere le azioni necessarie e integrali nelle soluzioni di gestione dei servizi:

- **Monitoraggio di base.** Il monitoraggio di base offre il monitoraggio essenziale delle diverse risorse di Azure. Questi servizi richiedono una configurazione minima e raccolgono i dati di telemetria principali usati dai servizi di monitoraggio Premium.
- **Monitoraggio approfondito delle applicazioni e dell'infrastruttura.** I servizi di Azure seguenti offrono funzionalità avanzate per la raccolta e l'analisi dei dati di monitoraggio a un livello più profondo. Questi servizi sono basati sul monitoraggio di base e sfruttano alcune funzionalità comuni di Azure. Offrono potente analisi con i dati raccolti per fornire informazioni esclusive sulle applicazioni e sull'infrastruttura.

Vedere ulteriori informazioni su [Monitoraggio di Azure](/azure/azure-monitor/overview) per il monitoraggio degli asset migrati.

## <a name="security-monitoring"></a>Monitoraggio della protezione

Affidarsi al Centro sicurezza di Azure per una gestione unificata del monitoraggio della sicurezza e delle notifiche avanzate per le minacce per i carichi di lavoro cloud ibridi. Il Centro sicurezza offre la visibilità completa e il controllo della sicurezza delle applicazioni cloud in Azure. È possibile rilevare e reagire rapidamente alle minacce e ridurre l'esposizione abilitando la protezione adattiva dalle minacce. Il dashboard predefinito fornisce informazioni dettagliate immediate sugli avvisi di sicurezza e sulle vulnerabilità che richiedono attenzione. Centro sicurezza di Azure può essere utile con molte funzioni, tra cui:

- **Monitoraggio centralizzato dei criteri.** Garantire la conformità con i requisiti di sicurezza normativi o aziendali tramite la gestione centralizzata dei criteri di sicurezza in tutti i carichi di lavoro cloud ibridi.
- **Valutazione continua della sicurezza.** Monitorare la sicurezza dei computer, delle reti, dei servizi di archiviazione e dati e delle applicazioni per individuare potenziali problemi di sicurezza.
- **Consigli operativi.** Correggere le vulnerabilità di sicurezza prima che possano essere sfruttate da utenti malintenzionati. Sono incluse raccomandazioni per la sicurezza classificate in ordine di priorità e di utilità pratica.
- **Difese del cloud avanzate.** Ridurre le minacce con l'accesso JIT (Just-in-Time) alle porte di gestione ed elenchi degli elementi consentiti per controllare le applicazioni in esecuzione nelle macchine virtuali.
- **Avvisi ed eventi imprevisti classificati in ordine di priorità.** Concentrarsi per prima cosa sulle minacce principali con avvisi di sicurezza ed eventi imprevisti classificati in ordine di priorità.
- **Soluzioni di sicurezza integrate.** Raccogliere, eseguire ricerche e analizzare i dati di sicurezza da diverse origini, incluse soluzioni partner connesse.

Altre informazioni sul [Centro sicurezza di Azure](/azure/security-center) per la protezione degli asset migrati.

## <a name="protect-assets-and-data"></a>Proteggere gli asset e i dati

Backup di Azure offre una soluzione per proteggere le macchine virtuali, i file e dati. Backup di Azure può essere utile con molte funzioni, tra cui:

- Backup di macchine virtuali.
- Backup di file.
- Backup dei database di SQL Server.
- Recupero degli asset protetti.

Vedere ulteriori informazioni su [Backup di Azure](/azure/backup) per la protezione degli asset migrati.
