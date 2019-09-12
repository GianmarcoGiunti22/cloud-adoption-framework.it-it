---
title: Guida al monitoraggio del cloud-panoramica sulle piattaforme di monitoraggio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: mgoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 33d9647a0804859a611d45e130c753cab89a6ef6
ms.sourcegitcommit: b94e9be9e43214d954ff8a7b6fdf96b84cbac55a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70863651"
---
# <a name="cloud-monitoring-guide-overview-of-our-monitoring-platforms"></a>Guida al monitoraggio del cloud: Panoramica delle piattaforme di monitoraggio

Microsoft offre una gamma di funzionalità di monitoraggio di due prodotti: System Center Operations Manager progettato per l'ambiente locale e quindi esteso al cloud e monitoraggio di Azure, progettato per il cloud, ma anche per il monitoraggio dei sistemi locali. Queste due offerte offrono servizi di monitoraggio di base, ad esempio avvisi, monitoraggio del tempo di esecuzione del servizio, monitoraggio dell'integrità delle applicazioni e dell'infrastruttura, diagnostica e analisi.

Molte organizzazioni adottano le procedure più recenti per l'agilità DevOps e le innovazioni cloud per gestire gli ambienti eterogeneo. Tuttavia, sono anche preoccupati della loro capacità di prendere decisioni appropriate e responsabili in merito al monitoraggio di tali carichi di lavoro.

Questo articolo fornisce una panoramica generale delle piattaforme di monitoraggio che consentono di comprendere in che modo entrambe le funzionalità forniscono funzionalità di monitoraggio di base.

## <a name="story-of-system-center-operations-manager"></a>Storia di System Center Operations Manager

In 2000 è stato immesso il campo Operations Management con Microsoft Operations Manager (MOM) 2000. In 2007 è stata introdotta una versione riprogettata del prodotto denominata System Center Operations Manager. Il servizio è stato spostato oltre il semplice monitoraggio di un server Windows e si concentrava sul monitoraggio affidabile di servizi e applicazioni end-to-end, incluse le piattaforme eterogeneo, i dispositivi di rete e altre dipendenze dell'applicazione o del servizio. Si tratta di una piattaforma di monitoraggio di livello aziendale e consolidata per gli ambienti locali, nella stessa classe di IBM Tivoli o HP Operations Manager nel settore. È cresciuta per supportare il monitoraggio delle risorse di calcolo e piattaforma in esecuzione in Azure, Amazon Web Services (AWS) e altri provider di servizi cloud.

## <a name="story-of-azure-monitor"></a>Storia di monitoraggio di Azure

Quando Azure è stato rilasciato in 2010, il monitoraggio dei servizi cloud è stato fornito con l'agente di Diagnostica di Azure, che fornisce un modo per raccogliere i dati di diagnostica dalle risorse di Azure. Questa funzionalità era considerata uno strumento di monitoraggio generale anziché una piattaforma di monitoraggio di livello aziendale.  

Application Insights è stato introdotto per passare con le modifiche apportate al settore in cui la proliferazione dei dispositivi cloud, mobile e Internet è cresciuta e l'introduzione delle procedure DevOps. È cresciuta da Application Performance Monitoring in Operations Manager a un servizio in Azure, dove offre un monitoraggio completo delle applicazioni Web scritte in un'ampia gamma di linguaggi. In 2015, l'anteprima di Application Insights per Visual Studio è stata annunciata e in seguito è diventata nota come Application Insights. Raccoglie informazioni dettagliate sulle prestazioni dell'applicazione, sulle richieste, sulle eccezioni e sulle tracce.

In 2015 Azure Operational Insights è stato reso disponibile a livello generale. Ha fornito il servizio di analisi Log Analytics che ha raccolto e cercato i dati da computer in Azure, locali o altri ambienti cloud e connessi a System Center Operations Manager. Sono stati offerti Intelligence Pack che hanno fornito diverse configurazioni di gestione e monitoraggio predefinite che contenevano una raccolta di regole di query e logica analitica, visualizzazioni e regole di raccolta dati per scenari come il controllo della sicurezza, l'integrità valutazioni e gestione degli avvisi.  In seguito Operational Insights di Azure è stato noto come Log Analytics.  

In 2016, l'anteprima di monitoraggio di Azure è stata annunciata Ignite. Ha fornito un Framework comune per raccogliere le metriche della piattaforma, i log di diagnostica delle risorse e gli eventi del log attività a livello di sottoscrizione da qualsiasi servizio di Azure che ha iniziato a usare il Framework. In precedenza, ogni servizio di Azure aveva un proprio metodo di monitoraggio.

Alla conferenza Microsoft Ignite del 2018, abbiamo annunciato che il marchio di monitoraggio di Azure è stato ampliato in modo da includere diversi servizi diversi originariamente sviluppati con funzionalità indipendenti:

- Funzionalità di **monitoraggio di Azure** originale per la raccolta di metriche della piattaforma, log di diagnostica delle risorse e log attività solo per le risorse della piattaforma Azure.
- **Application Insights** per il monitoraggio delle applicazioni.
- **Log Analytics** come posizione primaria per la raccolta e l'analisi dei dati di log.
- Un nuovo **servizio di avvisi unificato** che ha riunito meccanismi di avviso da ognuno degli altri servizi indicati in precedenza.  
- **Azure Network Watcher** per monitorare, diagnosticare e visualizzare le metriche per le risorse in una rete virtuale di Azure.

## <a name="the-story-of-operations-management-suite-oms"></a>Storia di Operations Management Suite (OMS)

Da 2015 fino al 2018 aprile, Operations Management Suite (OMS) era un bundle dei seguenti servizi di gestione di Azure per scopi di licenza:

- Application Insights
- Automazione di Azure
- Backup di Azure
- Operational Insights (in seguito il Log Analytics rimarchiato)
- Site Recovery

La funzionalità dei servizi che facevano parte di OMS non è stata modificata quando OMS è stata sospesa, sono stati riallineati in monitoraggio di Azure.

## <a name="infrastructure-requirements"></a>Requisiti dell'infrastruttura

### <a name="operations-manager"></a>Operations Manager

Operations Manager richiede un'infrastruttura e una manutenzione significative per supportare un gruppo di gestione, che è un'unità di base di funzionalità. Come minimo, un gruppo di gestione è costituito da uno o più server di gestione, un SQL Server, che ospita il database operativo e data warehouse per reporting e gli agenti. La complessità della progettazione di un gruppo di gestione dipende da diversi fattori, ad esempio l'ambito dei carichi di lavoro da monitorare e il numero di dispositivi o computer che supportano i carichi di lavoro. Se è necessaria la disponibilità elevata e la resilienza del sito, come in genere accade con le piattaforme di monitoraggio aziendali, i requisiti dell'infrastruttura e la manutenzione associata possono aumentare notevolmente.

![Diagramma del gruppo di gestione di Operations Manager](./media/monitoring-management-guidance-cloud-and-on-premises/operations-manager-management-group-optimized.svg)

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure è un servizio SaaS, in cui tutte le infrastrutture che lo supportano sono in esecuzione in Azure e sono gestite da Microsoft. È progettato per eseguire il monitoraggio, l'analisi e la diagnostica su larga scala ed è disponibile in tutti i cloud nazionali. Le parti principali dell'infrastruttura (agenti di raccolta, metriche e archivio di log e analisi) necessarie per supportare monitoraggio di Azure sono gestite da Microsoft.  

![Diagramma di monitoraggio di Azure](./media/monitoring-management-guidance-cloud-and-on-premises/azure-monitor-greyed-optimized.svg)

## <a name="data-collection"></a>Raccolta dei dati

### <a name="operations-manager"></a>Operations Manager

#### <a name="agents"></a>Agenti

Operations Manager raccoglie solo i dati direttamente dagli agenti installati nei [computer Windows](https://docs.microsoft.com//system-center/scom/plan-planning-agent-deployment?view=sc-om-1807#windows-agent). Può accettare i dati da Operations Manager SDK, ma in genere viene usato per i partner che estendono il prodotto con applicazioni personalizzate, non per la raccolta dei dati di monitoraggio. Può raccogliere dati da altre origini, ad esempio i [computer Linux](https://docs.microsoft.com/system-center/scom/plan-planning-agent-deployment?view=sc-om-1807#linuxunix-agent) e i dispositivi di rete, usando moduli speciali eseguiti nell'agente di Windows per accedere in remoto a questi altri dispositivi.

![Diagramma dell'agente Operations Manager](./media/monitoring-management-guidance-cloud-and-on-premises/data-collection-opsman-agents-optimized.svg)

L'agente di Operations Manager può raccogliere da più origini dati nel computer locale, ad esempio il registro eventi, i log personalizzati e i contatori delle prestazioni. Consente inoltre di eseguire script, che possono raccogliere dati dal computer locale o da origini esterne. È possibile scrivere script personalizzati per raccogliere dati che non possono essere raccolti in altro modo o da un'ampia gamma di dispositivi remoti che altrimenti non possono essere monitorati.

#### <a name="management-packs"></a>Management Pack

Operations Manager esegue tutti i monitoraggi con i flussi di lavoro (regole, monitoraggi e individuazioni oggetti). Questi pacchetti vengono inclusi in un [Management Pack](https://docs.microsoft.com/system-center/scom/manage-overview-management-pack?view=sc-om-2019)e distribuiti agli agenti. I Management Pack sono disponibili per un'ampia gamma di prodotti e servizi che includono regole e monitoraggi predefiniti. È anche possibile creare Management Pack personalizzati per le applicazioni e gli scenari personalizzati.

#### <a name="monitoring-configuration"></a>Configurazione del monitoraggio

I Management Pack possono contenere centinaia di regole, monitoraggi e regole di individuazione oggetti. Un agente esegue tutte queste impostazioni di monitoraggio da tutti i Management Pack che si applicano, determinati dalle regole di individuazione. Ogni istanza di ogni impostazione di monitoraggio viene eseguita in modo indipendente e agisce immediatamente sui dati raccolti. Questo è il modo in cui Operations Manager possibile ottenere avvisi quasi in tempo reale e lo stato di integrità corrente delle risorse monitorate.

Ad esempio, un monitoraggio può campionare un contatore delle prestazioni ogni pochi minuti. Se il contatore supera una soglia, imposta immediatamente lo stato di integrità del relativo oggetto di destinazione, che attiva immediatamente un avviso nel gruppo di gestione. Una regola pianificata potrebbe controllare la creazione di un evento specifico e generare immediatamente un avviso quando l'evento viene creato nel registro eventi locale.

Poiché queste impostazioni di monitoraggio sono isolate l'una dall'altra e funzionano dalle singole origini dati, Operations Manager presenta problemi di correlazione dei dati tra più origini. È anche difficile reagire ai dati dopo che sono stati raccolti. È possibile eseguire flussi di lavoro che accedono al database Operations Manager, ma questo scenario non è comune e viene in genere usato per un numero limitato di flussi di lavoro per scopi specifici.

![Diagramma del gruppo di gestione di Operations Manager](./media/monitoring-management-guidance-cloud-and-on-premises/operations-manager-management-group-optimized.svg)

### <a name="azure-monitor"></a>Monitoraggio di Azure

#### <a name="data-sources"></a>Origini dati

Monitoraggio di Azure raccoglie i dati da un'ampia gamma di origini, tra cui l'infrastruttura di Azure e le risorse della piattaforma, gli agenti nei computer Windows e Linux e il monitoraggio dei dati raccolti in archiviazione di Azure. Qualsiasi client REST può scrivere i dati di log in monitoraggio di Azure usando un'API ed è possibile definire metriche personalizzate per le applicazioni Web. Alcuni dati della metrica possono essere indirizzati a posizioni diverse, a seconda dell'utilizzo. Ad esempio, è possibile usare i dati per gli avvisi "rapidi" o per l'analisi delle tendenze a lungo termine ricercata in combinazione con altri dati di log.

#### <a name="monitoring-solutions-and-insights"></a>Soluzioni di monitoraggio e informazioni dettagliate

Le soluzioni di monitoraggio usano la piattaforma logs in monitoraggio di Azure per fornire il monitoraggio di un'applicazione o un servizio specifico. In genere definiscono la raccolta di dati dagli agenti o dai servizi di Azure e forniscono query e visualizzazioni di log per analizzare i dati. In genere non forniscono regole di avviso, ovvero è necessario definire i propri criteri di avviso in base ai dati raccolti.

Informazioni dettagliate, ad esempio monitoraggio di Azure per contenitori e Monitoraggio di Azure per le macchine virtuali, usano la piattaforma log e metriche di monitoraggio di Azure per offrire un'esperienza di monitoraggio personalizzata per un'applicazione o un servizio nel portale di Azure. Potrebbero fornire condizioni di monitoraggio dello stato e di avviso, oltre all'analisi personalizzata dei dati raccolti.

#### <a name="monitoring-configuration"></a>Configurazione del monitoraggio

Monitoraggio di Azure separa la raccolta di dati da azioni eseguite su tali dati, che supporta microservizi distribuiti in un ambiente cloud. Consente di consolidare i dati di più origini in una piattaforma dati comune e fornisce funzionalità di analisi, visualizzazione e avviso in base ai dati raccolti.

Tutti i dati raccolti da monitoraggio di Azure vengono archiviati come log o metriche e le diverse funzionalità di monitoraggio si basano su entrambe. Le metriche contengono valori numerici in serie temporali che sono particolarmente adatti per gli avvisi quasi in tempo reale e per il rilevamento rapido dei problemi. I log contengono dati di testo o numerici e sono supportati da un linguaggio di query avanzato che li rende particolarmente utili per l'esecuzione di analisi complesse.

Poiché il monitoraggio separa la raccolta di dati da azioni rispetto a tali dati, potrebbe non essere in grado di fornire avvisi quasi in tempo reale in molti casi. Per generare un avviso sui dati del log, le query vengono eseguite in base a una pianificazione ricorrente definita nell'avviso. Questo comportamento consente a monitoraggio di Azure di correlare facilmente i dati di tutte le origini monitorate ed è possibile analizzare i dati in modo interattivo in diversi modi. Questa operazione è particolarmente utile per eseguire l'analisi della causa radice e identificare la posizione in cui può verificarsi un problema.

## <a name="health-monitoring"></a>Monitoraggio dell’integrità

### <a name="operations-manager"></a>Operations Manager

I Management Pack in Operations Manager includono un modello di servizio che descrive i componenti dell'applicazione monitorata e le relative relazioni. I monitoraggi identificano lo stato di integrità corrente di ogni componente in base ai dati e agli script nell'agente. Gli Stati di integrità vengono sottoposti a rollup in modo da visualizzare rapidamente lo stato di integrità riepilogato dei computer e delle applicazioni monitorati.

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure non fornisce un metodo definibile dall'utente per l'implementazione di un modello di servizio o di monitoraggi che indicano lo stato di integrità corrente di tutti i componenti del servizio. Poiché le soluzioni di monitoraggio sono basate sulle funzionalità standard di monitoraggio di Azure, non forniscono il monitoraggio a livello di stato. Le funzionalità seguenti di monitoraggio di Azure possono essere utili:

- **Application Insights** compila una mappa composita dell'applicazione Web e fornisce uno stato di integrità per ogni componente dell'applicazione o dipendenza. Sono inclusi lo stato degli avvisi e il drill-down per la diagnostica più dettagliata dell'applicazione.

- **Monitoraggio di Azure per le macchine virtuali** offre un'esperienza di monitoraggio dell'integrità per le VM di Azure Guest, in modo analogo a Operations Manager, durante il monitoraggio di macchine virtuali Windows e Linux. Valuta l'integrità dei componenti principali del sistema operativo dal punto di vista della disponibilità e delle prestazioni per determinare lo stato di integrità corrente. Quando determina che la macchina virtuale guest sta riscontrando un utilizzo prolungato delle risorse, la capacità dello spazio su disco o un problema correlato alla funzionalità di base del sistema operativo, viene generato un avviso per portare questo stato all'attenzione dell'utente.

- **Monitoraggio di Azure per i contenitori** monitora le prestazioni e l'integrità dei servizi Kubernetes di Azure o delle istanze di contenitore di Azure. che raccoglie metriche sulla memoria e sul processore da controller, nodi e contenitori disponibili in Kubernetes tramite l'API Metriche. Raccoglie anche i log del contenitore e i dati di inventario relativi ai contenitori e alle relative immagini. I criteri di integrità predefiniti basati sui dati sulle prestazioni raccolti consentono di identificare se si verifica un collo di bottiglia delle risorse o un problema di capacità. È anche possibile comprendere le prestazioni complessive o le prestazioni di un tipo di oggetto Kubernetes specifico (Pod, nodo, controller o contenitore).

## <a name="analyzing-data"></a>Analisi dei dati

### <a name="operations-manager"></a>Operations Manager

Operations Manager offre quattro modi di base per analizzare i dati dopo che sono stati raccolti.

- Con **Esplora stati**è possibile individuare i monitoraggi che identificano un problema di stato di integrità ed esaminare le informazioni sul monitoraggio e le possibili cause per le azioni correlate.

- Le **visualizzazioni** sono visualizzazioni predefinite dei dati raccolti, ad esempio un grafico dei dati sulle prestazioni o un elenco di componenti monitorati e il relativo stato di integrità corrente. Le visualizzazioni diagramma presentano visivamente il modello di servizio di un'applicazione.

- I **report** consentono di riepilogare i dati cronologici archiviati nel data warehouse di Operations Manager. È possibile personalizzare i dati su cui si basano le visualizzazioni e i report. Tuttavia, non esiste alcuna funzionalità per consentire l'analisi complessa o interattiva dei dati raccolti.

- **Operations Manager Shell dei comandi**, che estende Windows PowerShell con un set aggiuntivo di cmdlet, può eseguire query e visualizzare i dati raccolti. Sono inclusi i grafici e altre visualizzazioni, in modo nativo con PowerShell o con la Operations Manager Console Web basata su HTML.

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure dispone di un potente motore di analisi che consente di lavorare in modo interattivo con i dati di log e combinarli con altri dati di monitoraggio per le tendenze e altre analisi dei dati. Viste e dashboard consentono di visualizzare i dati delle query in modi diversi dal portale di Azure e di importare in Power BI. Le soluzioni di monitoraggio includono query e visualizzazioni per presentare i dati raccolti. Informazioni dettagliate, ad esempio Application Insights, Monitoraggio di Azure per le macchine virtuali e monitoraggio di Azure per i contenitori, includono visualizzazioni personalizzate per supportare scenari di monitoraggio interattivo.

## <a name="alerting"></a>Creazione di avvisi

### <a name="operations-manager"></a>Operations Manager

Operations Manager crea avvisi in risposta a eventi predefiniti, quando viene soddisfatta una soglia di prestazioni e quando viene modificato lo stato di integrità di un componente monitorato. Include la gestione completa degli avvisi, che consente di impostare la risoluzione e di assegnarli a operatori o tecnici di sistema diversi. È possibile impostare regole di notifica che specificano gli avvisi che invieranno notifiche proattive.

I Management Pack includono diverse regole di avviso predefinite per diverse condizioni critiche nell'applicazione monitorata. È possibile ottimizzare queste regole o creare regole personalizzate per i requisiti specifici dell'ambiente in uso.

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure consente di creare avvisi in base a una metrica che supera una soglia o in base a un risultato di query pianificato. Gli avvisi basati sulle metriche possono ottenere risultati quasi in tempo reale, mentre le query pianificate hanno tempi di risposta più lunghi, a seconda della velocità di inserimento e indicizzazione dei dati. Anziché essere limitati a un agente specifico, gli avvisi di query di log in monitoraggio di Azure consentono di analizzare i dati in tutti i dati archiviati in più aree di lavoro. Questi avvisi includono anche i dati di un'app di Application Insights specifica usando una query tra aree di lavoro.

Mentre le soluzioni di monitoraggio possono includere regole di avviso, in genere vengono create in base ai propri requisiti.

## <a name="workflows"></a>Workflows

### <a name="operations-manager"></a>Operations Manager

I Management Pack in Operations Manager contengono centinaia di singoli flussi di lavoro e determinano i dati da raccogliere e l'azione da eseguire con tali dati. Una regola, ad esempio, può campionare un contatore delle prestazioni ogni pochi minuti, archiviando i risultati per l'analisi. Un monitoraggio può campionare lo stesso contatore delle prestazioni e confrontare il relativo valore con una soglia per determinare lo stato di integrità di un oggetto monitorato. Un'altra regola potrebbe eseguire uno script per raccogliere e analizzare alcuni dati in un computer agente e generare un avviso se restituisce un valore specifico.

I flussi di lavoro in Operations Manager sono indipendenti tra loro, quindi l'analisi tra più oggetti monitorati è difficile. Questi scenari di monitoraggio devono essere basati sui dati dopo che sono stati raccolti, il che è possibile, ma può essere difficile e non è comune.

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure separa la raccolta di dati da azioni e analisi eseguite da tali dati. Gli agenti e altre origini dati scrivono i dati di log in un'area di lavoro Log Analytics e i dati delle metriche nel database delle metriche, senza alcuna analisi dei dati o della relativa modalità di utilizzo. Il monitoraggio esegue avvisi e altre azioni dai dati archiviati, consentendo di eseguire analisi tra i dati di tutte le origini.

## <a name="extending-base-platform"></a>Estensione della piattaforma di base

### <a name="operations-manager"></a>Operations Manager

Operations Manager implementa tutta la logica di monitoraggio in un Management Pack, che è possibile creare o ottenere da Microsoft o da un partner. Quando si installa una Management Pack, individua automaticamente i componenti dell'applicazione o del servizio su agenti diversi e distribuisce le regole e i monitoraggi appropriati. Il Management Pack contiene le definizioni di integrità, le regole di avviso, le regole di raccolta di eventi e prestazioni, nonché le visualizzazioni, per fornire il monitoraggio completo che supporta il servizio o l'applicazione dell'infrastruttura.

Il Operations Manager SDK consente di integrare Operations Manager con piattaforme di monitoraggio di terze parti o con software ITSM. L'SDK è usato anche da alcuni Management Pack dei partner per supportare il monitoraggio dei dispositivi di rete e offrire esperienze di presentazione personalizzate come il dashboard HTML5 quadrato o l'integrazione con Microsoft Office Visio.

### <a name="azure-monitor"></a>Monitoraggio di Azure

Monitoraggio di Azure raccoglie metriche e log dalle risorse di Azure, senza alcuna configurazione. Le soluzioni di monitoraggio aggiungono la logica per il monitoraggio di un'applicazione o di un servizio, ma continuano a funzionare nelle query e nelle viste di log standard in monitor. Informazioni dettagliate, ad esempio Application Insights e Monitoraggio di Azure per le macchine virtuali, usano la piattaforma di monitoraggio per la raccolta e l'elaborazione dei dati e forniscono anche strumenti aggiuntivi per visualizzare e analizzare i dati. È possibile combinare i dati raccolti da informazioni dettagliate con altri dati, usando le funzionalità di monitoraggio di base, ad esempio query e avvisi del log.

Il monitoraggio supporta diversi metodi per raccogliere dati di monitoraggio o di gestione da Azure o da risorse esterne. È quindi possibile estrarre e trasmettere i dati dalla metrica o dagli archivi di log alle ITSM o agli strumenti di monitoraggio oppure eseguire attività amministrative usando l'API REST di monitoraggio di Azure.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Monitoraggio dei modelli di distribuzione cloud](./cloud-models-monitor-overview.md)
