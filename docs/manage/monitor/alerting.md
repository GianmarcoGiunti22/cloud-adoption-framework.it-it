---
title: Guida al monitoraggio del cloud-avvisi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 76fb8084aad799d3bbfdaf3bd2ef4330fd080ac0
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028600"
---
# <a name="cloud-monitoring-guide-alerting"></a>Guida al monitoraggio del cloud: Avvisi

Per anni, le organizzazioni IT hanno faticato a combattere la fatica degli avvisi creata dagli strumenti di monitoraggio distribuiti nell'organizzazione. Molti sistemi generano un volume elevato di avvisi spesso considerati irrilevanti, mentre altri sono rilevanti, ma sono trascurati o ignorati. Di conseguenza, le operazioni di IT e sviluppatori hanno avuto difficoltà a soddisfare la qualità del livello di servizio promessa ai clienti interni o esterni. È essenziale comprendere lo stato dell'infrastruttura e delle applicazioni per garantire l'affidabilità. È necessario identificare rapidamente le cause, ridurre al minimo la riduzione del servizio e l'interferenza oppure ridurre l'effetto o ridurre il numero di eventi imprevisti.

## <a name="successful-alerting-strategy"></a>Strategia di avviso riuscita

*Non è possibile correggere ciò che non si conosce è danneggiato.*

L'invio di avvisi sulla questione è fondamentale. È sottoposto a una raccolta e alla misurazione delle metriche e dei log corretti. È anche necessario uno strumento di monitoraggio in grado di archiviare, aggregare, visualizzare, analizzare e avviare una risposta automatica quando vengono soddisfatte le condizioni. Il miglioramento dell'osservabilità dei servizi e delle applicazioni può essere eseguito solo se la sua composizione è completamente comprensibile. È possibile eseguire il mapping di tale composizione in una configurazione di monitoraggio dettagliata che verrà applicata dalla piattaforma di monitoraggio. Sono inclusi gli Stati di errore prevedibili (i sintomi non la cui origine è l'errore) che hanno senso per l'avviso.

Prendere in considerazione i principi seguenti per determinare se un sintomo è un candidato appropriato per gli avvisi:

- **È importante?** Il problema è sintomatico di un problema reale o di un problema che influisce sull'integrità complessiva dell'applicazione? Ad esempio, se l'utilizzo della CPU è elevato nella risorsa? O che una particolare query SQL in esecuzione in un'istanza del database SQL su tale risorsa stia utilizzando un utilizzo elevato della CPU in un periodo di tempo prolungato? Poiché la condizione di utilizzo della CPU è un problema reale, è necessario avvisarlo. Tuttavia, non è necessario inviare una notifica al team, perché non consente di puntare a ciò che causa la condizione in primo luogo. Gli avvisi e le notifiche relative al problema di utilizzo del processo di query SQL sono rilevanti e interoperabili.
- **È urgente?** Il problema è reale e richiede attenzione urgente? In tal caso, il team responsabile deve ricevere immediatamente una notifica.
- **I clienti sono interessati?** Gli utenti del servizio o dell'applicazione sono interessati a causa del problema?
- **Sono interessati altri sistemi dipendenti?** Sono presenti avvisi provenienti da dipendenze intercorrelate e che potrebbero essere correlati per evitare la notifica a diversi team di lavorare sullo stesso problema?

Porre queste domande quando si sviluppa inizialmente una configurazione di monitoraggio. Verificare e convalidare i presupposti in un ambiente non di produzione e quindi distribuirli nell'ambiente di produzione. Le configurazioni di monitoraggio derivano da modalità di errore note, risultati dei test di errori simulati ed esperienza da membri diversi del team.

Dopo il rilascio della configurazione di monitoraggio, è possibile apprendere molto di ciò che funziona e cosa non lo è. Si prenda in considerazione un volume di avvisi elevato, problemi non osservati dal monitoraggio, ma notato dagli utenti finali, e quali sono state le azioni migliori da eseguire come parte della valutazione. Identificare le modifiche da implementare per migliorare la distribuzione dei servizi, come parte di un processo continuo di miglioramento continuo del monitoraggio. Non si tratta solo della valutazione del rumore degli avvisi o degli avvisi mancanti, ma anche dell'efficacia del monitoraggio del carico di lavoro. Si tratta dell'efficacia dei criteri di avviso, dei processi e delle impostazioni cultura generali per determinare se si sta migliorando.

Sia System Center Operations Manager che monitoraggio di Azure supportano gli avvisi in base alle soglie statiche o anche dinamiche e alle azioni impostate su di essi. Gli esempi includono avvisi per la posta elettronica, gli SMS e le chiamate vocali per le notifiche semplici. Entrambi i servizi supportano anche l'integrazione con ITSM, per automatizzare la creazione di record di eventi imprevisti ed eseguire l'escalation al team di supporto corretto o a qualsiasi altro sistema di gestione degli avvisi tramite un webhook.

Quando possibile, è possibile usare uno dei diversi servizi per automatizzare le azioni di ripristino. Sono inclusi gli agenti di orchestrazione di System Center, automazione di Azure, app per la logica di Azure o il ridimensionamento automatico in caso di carichi di lavoro elastici. Anche se la notifica ai team responsabili è l'azione più comune per gli avvisi, potrebbe essere opportuno automatizzare le azioni correttive. Ciò consente di semplificare l'intero processo di gestione degli eventi imprevisti. L'automazione di queste attività di ripristino può anche ridurre il rischio di errore umano.

## <a name="azure-monitor-alerting"></a>Avvisi di monitoraggio di Azure

Se si usa esclusivamente monitoraggio di Azure, vengono applicate le indicazioni seguenti. Seguire queste linee guida quando si considerano velocità, costi e volumi di archiviazione in monitoraggio di Azure.

Sono disponibili sei repository che archiviano i dati di monitoraggio, a seconda della funzionalità e della configurazione in uso.

- **Database di metriche di monitoraggio di Azure.** Un database di serie temporali usato principalmente per le metriche della piattaforma di monitoraggio di Azure, ma include anche Application Insights dati delle metriche con mirroring. Le informazioni immesse nel database hanno tempi di avviso più rapidi.

- **Archivio dei log Application Insights.** Un database che archivia la maggior parte Application Insights la telemetria nel form di log.

- **Archivio dei log di monitoraggio di Azure.** Archivio primario per i dati dei log di Azure. Altri strumenti possono instradare i dati e possono essere analizzati nei log di monitoraggio di Azure. Le query di avviso del log hanno una latenza superiore a causa dell'inserimento e dell'indicizzazione. Questa latenza è in genere di 5-10 minuti, ma può essere superiore in determinate circostanze.

- **Archivio dei log attività.** Usato per tutti gli eventi di integrità del servizio e del log attività. È possibile ricevere avvisi dedicati. Include gli eventi a livello di sottoscrizione che si verificano sugli oggetti della sottoscrizione, come illustrato dall'esterno degli oggetti. Ad esempio, quando si imposta un criterio o si accede o si elimina una risorsa.

- **Archiviazione di Azure.** Archiviazione per utilizzo generico supportata da Diagnostica di Azure e altri strumenti di monitoraggio. Si tratta di un'opzione a basso costo per la conservazione a lungo termine dei dati di telemetria del monitoraggio. Gli avvisi non sono supportati dai dati archiviati in questo servizio.

- **Hub eventi.** Usato in genere per eseguire lo streaming dei dati in strumenti di monitoraggio/ITSM in locale o in altri partner.

Sono disponibili quattro tipi di avvisi in monitoraggio di Azure, che sono in qualche modo collegati al repository in cui sono archiviati i dati.

- [Avviso della metrica](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric). Avvisi sui dati nel database di metriche di monitoraggio di Azure. Gli avvisi si verificano quando un valore monitorato supera una soglia definita dall'utente e quindi nuovamente quando torna allo stato "normale".

- [Avviso di query di log](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-log-query). Disponibile per gli avvisi sul contenuto nell'Application Insights o negli archivi di log di Azure. Può anche inviare un avviso in base alle query tra aree di lavoro.

- [Avviso del log attività](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log). Avvisi sugli elementi nell'archivio dei log attività, ad eccezione dei dati di integrità del servizio.

- [Avviso di integrità del servizio](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log-service-notifications?toc=%2fazure%2fservice-health%2ftoc.json). Un tipo speciale di avviso, solo per i problemi di integrità del servizio provenienti dall'archivio dei log attività.

### <a name="alerting-through-partner-tools"></a>Avvisi tramite gli strumenti dei partner

Se si usa una soluzione di avviso esterna, indirizzare quanto più possibile tramite hub eventi di Azure, perché questo è il percorso più veloce fuori da monitoraggio di Azure. Dovrai pagare per l'inserimento nell'hub eventi. Se il costo è un problema e la velocità non è, è possibile usare archiviazione di Azure come alternativa più economica. È sufficiente assicurarsi che gli strumenti di monitoraggio o ITSM possano leggere archiviazione di Azure per estrarre i dati.

Monitoraggio di Azure include il supporto per l'integrazione con altre piattaforme di monitoraggio e il software ITSM, ad esempio ServiceNow. È possibile usare gli avvisi di Azure e attivare ancora azioni esterne ad Azure, come richiesto dal processo di gestione degli eventi imprevisti o DevOps. Se si vuole ricevere un avviso in monitoraggio di Azure e automatizzare la risposta, è possibile avviare azioni automatiche usando funzioni di Azure, app per la logica di Azure o automazione di Azure, in base allo scenario e ai requisiti.

### <a name="specialized-azure-monitoring-offerings"></a>Offerte di monitoraggio di Azure specializzate

Le [soluzioni di gestione](https://docs.microsoft.com/azure/azure-monitor/insights/solutions-inventory) in genere archiviano i dati nell'archivio dei log di Azure. Le due eccezioni sono Monitoraggio di Azure per le macchine virtuali e monitoraggio di Azure per i contenitori. Nella tabella seguente viene descritta l'esperienza di avviso in base al tipo di dati specifico e alla posizione in cui sono archiviati.

Soluzione| Tipo di dati | Comportamento degli avvisi
:---|:---|:---
Monitoraggio di Azure per i contenitori | I dati relativi alle prestazioni medie calcolati da nodi e Pod vengono scritti nell'archivio di metriche. | Creare avvisi delle metriche se si desidera ricevere avvisi in base alla variazione delle prestazioni di utilizzo misurato, aggregato in un periodo di tempo.
|| I dati sulle prestazioni calcolati che usano percentile da nodi, controller, contenitori e Pod vengono scritti nell'archivio dei log. Anche i log del contenitore e le informazioni di inventario vengono scritti nell'archivio dei log. | Creare avvisi di query di log se si desidera ricevere avvisi in base a variazioni di utilizzo misurato da cluster e contenitori. Gli avvisi di query di log possono anche essere configurati in base ai conteggi delle fasi pod e ai conteggi dei nodi di stato.
Monitoraggio di Azure per le macchine virtuali | I criteri di integrità sono metriche scritte nell'archivio di metriche. | Gli avvisi vengono generati quando lo stato di integrità passa da integro a condizione non integro. Supporta solo gruppi di azioni configurati per l'invio di notifiche SMS o di posta elettronica.
|| I dati del log delle prestazioni del sistema operativo guest e mappa vengono scritti nell'archivio dei log. | Creare avvisi per le query di log.

### <a name="fastest-speed-driven-by-cost"></a>Velocità più veloce basata sui costi

La latenza è una delle decisioni più importanti che guidano gli avvisi e la risoluzione rapida dei problemi che interessano il servizio. Se sono necessari avvisi quasi in tempo reale in cinque minuti, valutare prima se si ha o è possibile ricevere avvisi sui dati di telemetria dove vengono archiviati per impostazione predefinita. In generale, questa strategia è anche l'opzione più economica, perché lo strumento che si sta utilizzando sta già inviando i dati a tale percorso.

Detto questo, vi sono alcune note importanti a questa regola.

I dati di telemetria del sistema **operativo guest** hanno diversi percorsi per accedere al sistema.

- Il modo più rapido per inviare avvisi su questi dati consiste nell'importarlo come metrica personalizzata. A tale scopo, utilizzare l'estensione Diagnostica di Azure e quindi utilizzare un avviso per la metrica. Tuttavia, le metriche personalizzate sono attualmente in anteprima e sono [più costose di altre opzioni](https://azure.microsoft.com/pricing/details/monitor/).

- Il metodo più economico ma più lento consiste nell'inviarlo all'archivio kusto dei log di Azure. L'esecuzione dell'agente di Log Analytics nella macchina virtuale rappresenta il modo migliore per ottenere tutte le metriche del sistema operativo guest e i dati di log in questo archivio.

- È possibile inviare a entrambi gli archivi eseguendo sia l'estensione che l'agente nella stessa VM. È quindi possibile inviare un avviso rapidamente, ma anche usare i dati del sistema operativo guest come parte di ricerche più complesse in combinazione con altri dati di telemetria.

**Importazione di dati da locale.** Se si sta tentando di eseguire query e monitorare tra computer in esecuzione in Azure e in locale, è possibile usare l'agente di Log Analytics per raccogliere i dati del sistema operativo guest. Quindi, è possibile usare una funzionalità denominata [registri per la metrica](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric-logs) per semplificare le metriche nell'archivio di metriche. Questo metodo ignora parte del processo di inserimento nell'archivio dei log di Azure ed è quindi disponibile prima nel database di metriche.

### <a name="minimize-alerts"></a>Riduci gli avvisi

Se si usa una soluzione come Monitoraggio di Azure per le macchine virtuali e si individuano i criteri di integrità predefiniti che controllano l'utilizzo delle prestazioni accettabile, non creare avvisi di metrica o di query di log sovrapposti in base agli stessi contatori delle prestazioni.

Se non si usa Monitoraggio di Azure per le macchine virtuali, esplorare le funzionalità seguenti per semplificare la creazione di avvisi e la gestione delle notifiche:  

> [!NOTE]
> Queste funzionalità si applicano solo agli avvisi delle metriche; ovvero gli avvisi basati sui dati inviati al database delle metriche di monitoraggio di Azure. Non si applicano agli altri tipi di avvisi. Come indicato in precedenza, l'obiettivo principale degli avvisi delle metriche è la velocità. Se ricevere un avviso in meno di 5 minuti non è un problema principale, è invece possibile usare un avviso di query di log.

- [Soglie dinamiche](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-dynamic-thresholds). Le soglie dinamiche esaminano l'attività della risorsa in un periodo di tempo e creano soglie di "comportamento normale" superiori e inferiori. Quando la metrica monitorata non rientra in queste soglie, viene generato un avviso.

- [Avvisi multifirmati](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts/). È possibile creare un avviso di metrica che usa la combinazione di due input diversi di due diversi tipi di risorse. Ad esempio, se si vuole generare un avviso quando la CPU di una macchina virtuale è superiore al 90% e il numero di messaggi in una determinata coda del bus di servizio di Azure che invia tale macchina virtuale supera una certa quantità, è possibile farlo senza creare una query di log. Questa operazione funziona solo per due segnali. Se si dispone di una query più complessa, inserire i dati delle metriche nell'archivio dei log di monitoraggio di Azure e usare una query di log.

- [Avvisi multirisorsa](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts/). Monitoraggio di Azure consente una singola regola di avviso metrica che si applica a tutte le risorse della macchina virtuale. Questa funzionalità consente di risparmiare tempo perché non è necessario creare singoli avvisi per ogni macchina virtuale. I prezzi per questo tipo di avviso sono gli stessi. Se sono stati creati 50 avvisi per il monitoraggio dell'utilizzo della CPU per le VM 50 o 1 avviso che monitora l'utilizzo della CPU per tutte le VM 50, il costo è lo stesso. È possibile utilizzare questi tipi di avvisi anche in combinazione con le soglie dinamiche.

Utilizzate insieme, queste funzionalità possono risparmiare tempo riducendo al minimo le notifiche di avviso e la gestione degli avvisi sottostanti.

### <a name="alerts-limitations"></a>Limitazioni degli avvisi

Assicurarsi di prendere nota delle [limitazioni](https://docs.microsoft.com/azure/azure-subscription-service-limits#azure-monitor-limits) del numero di avvisi che è possibile creare. Alcuni limiti (ma non tutti) possono essere aumentati chiamando il supporto.

### <a name="best-query-experience"></a>Migliore esperienza di query

Se si stanno cercando le tendenze in tutti i dati, è opportuno importare tutti i dati nei log di Azure, a meno che non siano già presenti in Application Insights. È possibile creare query in entrambe le aree di lavoro, quindi non è necessario spostare i dati tra di essi. È anche possibile importare i dati di integrità del servizio e del log attività nell'area di lavoro Log Analytics. Si paga per questa operazione di inserimento e archiviazione, ma si ottengono tutti i dati in un'unica posizione per l'analisi e l'esecuzione di query. Questo consente inoltre di creare condizioni di query complesse e di avvisare su di essi.