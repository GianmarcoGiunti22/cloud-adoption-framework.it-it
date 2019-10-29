---
title: Guida al monitoraggio del cloud-strategia di monitoraggio per i modelli di distribuzione cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 10/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 6e02cffdbd76932e3066ed68501856aef2669b02
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72979904"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guida al monitoraggio del cloud: strategia di monitoraggio per i modelli di distribuzione cloud

Questo articolo include la strategia di monitoraggio consigliata per ognuno dei modelli di distribuzione cloud, in base ai criteri seguenti:

- È necessario mantenere il proprio impegno per Operations Manager o un'altra piattaforma di monitoraggio aziendale, perché è integrata con i processi, le conoscenze e le competenze delle operazioni IT, oppure alcune funzionalità non sono ancora disponibili in monitoraggio di Azure.
- È necessario monitorare i carichi di lavoro sia in locale che nel cloud pubblico oppure solo nel cloud.
- La strategia di migrazione cloud include la modernizzazione delle operazioni IT e il passaggio alle soluzioni e ai servizi di monitoraggio cloud.
- Potrebbero essere presenti sistemi critici, gapped o fisicamente isolati, ospitati in un cloud privato o su hardware fisico. E i sistemi devono essere monitorati.

Questa strategia include il supporto per il monitoraggio dell'infrastruttura (elaborazione, archiviazione e carichi di lavoro del server), applicazione (utente finale, eccezioni e client) e risorse di rete. Offre una prospettiva di monitoraggio completa e orientata ai servizi.

## <a name="azure-cloud-monitoring"></a>Monitoraggio cloud di Azure

Monitoraggio di Azure è il servizio della piattaforma Azure native che fornisce un'unica origine per il monitoraggio delle risorse di Azure. È progettato per le soluzioni cloud che:
* Sono basati su Azure.
* Supportare una funzionalità aziendale basata sui carichi di lavoro delle macchine virtuali (VM) o su architetture complesse che usano microservizi e altre risorse della piattaforma.

Esegue il monitoraggio di tutti i livelli dello stack, a partire dai servizi tenant, ad esempio Azure Active Directory Domain Services e gli eventi a livello di sottoscrizione e di integrità dei servizi di Azure. 

Monitora inoltre le risorse dell'infrastruttura, ad esempio macchine virtuali, archiviazione e risorse di rete. Al livello superiore viene monitorata l'applicazione. 

Monitorando ognuna di queste dipendenze e raccogliendo i segnali corretti che ognuno può emettere, si ottiene l'osservabilità delle applicazioni e l'infrastruttura chiave necessaria.

Il metodo consigliato per il monitoraggio di ogni livello dello stack è riepilogato nella tabella seguente:

<!-- markdownlint-disable MD033 -->

Livello | Gruppi | Scope | Metodo
---|---|---|----
Richiesta | Un'applicazione basata sul Web che viene eseguita in .NET, .NET Core, Java, JavaScript e nella piattaforma node. js in una VM di Azure, app Azure Services, Azure Service Fabric, funzioni di Azure e servizi cloud di Azure. | Monitorare un'applicazione Web attiva per rilevare automaticamente le anomalie delle prestazioni, identificare le eccezioni e i problemi del codice e raccogliere analisi del comportamento dell'utente. |  Monitoraggio di Azure (Application Insights).
Risorse di Azure-piattaforma distribuita come servizio (PaaS) | Servizi di database di Azure (ad esempio, SQL o MySQL). | Metriche delle prestazioni del database di Azure per SQL. | Abilitare la registrazione diagnostica per trasmettere i dati SQL ai log di monitoraggio di Azure.
Risorse di Azure-infrastruttura distribuita come servizio (IaaS) | 1. archiviazione di Azure<br/> 2. applicazione Azure gateway<br/> 3. gruppi di sicurezza di rete<br/> 4. gestione traffico di Azure<br/> 5. macchine virtuali di Azure<br/> 6. servizio Azure Kubernetes/istanze di contenitore di Azure | 1. capacità, disponibilità e prestazioni.<br/> 2. log di prestazioni e diagnostica (attività, accesso, prestazioni e firewall).<br/> 3. monitorare gli eventi quando vengono applicate le regole e il contatore delle regole per il numero di volte in cui una regola viene applicata a Deny o Allow.<br/> 4. monitorare la disponibilità dello stato dell'endpoint.<br/> 5. monitorare la capacità, la disponibilità e le prestazioni in un sistema operativo della macchina virtuale guest. Eseguire il mapping delle dipendenze delle app ospitate in ogni macchina virtuale, inclusa la visibilità delle connessioni di rete attive tra i server, la latenza delle connessioni in ingresso e in uscita e le porte di qualsiasi architettura connessa a TCP.<br/> 6. monitorare la capacità, la disponibilità e le prestazioni dei carichi di lavoro in esecuzione su contenitori e istanze di contenitore. | 1. metriche di archiviazione per l'archiviazione BLOB.<br/> 2. abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.<br/> 3. abilitare la registrazione diagnostica dei gruppi di sicurezza di rete e configurare lo streaming nei log di monitoraggio di Azure.<br/> 4. abilitare la registrazione diagnostica degli endpoint di gestione traffico e configurare lo streaming nei log di monitoraggio di Azure.<br/> 5. abilitare Monitoraggio di Azure per le macchine virtuali.<br/> 6. abilitare monitoraggio di Azure per i contenitori.
Rete | Comunicazione tra la macchina virtuale e uno o più endpoint (un'altra VM, un nome di dominio completo, un identificatore di risorsa uniforme o un indirizzo IPv4). | Monitorare la raggiungibilità, la latenza e le modifiche alla topologia di rete che si verificano tra la macchina virtuale e l'endpoint. | Network Watcher di Azure.
Sottoscrizione di Azure | Integrità del servizio di Azure e integrità delle risorse di base. | <li> Azioni amministrative eseguite su un servizio o una risorsa.<br/><li> L'integrità del servizio con un servizio di Azure è in uno stato danneggiato o non disponibile.<br/><li> Problemi di integrità rilevati con una risorsa di Azure dal punto di vista del servizio di Azure.<br/><li> Operazioni eseguite con la scalabilità automatica di Azure che indicano un errore o un'eccezione. <br/><li> Operazioni eseguite con criteri di Azure che indicano che si è verificata un'azione consentita o negata.<br/><li> Record degli avvisi generati dal centro sicurezza di Azure. | Recapitato nel log attività per il monitoraggio e l'invio di avvisi tramite Azure Resource Manager.
Tenant di Azure | Azure Active Directory || Abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Monitoraggio del cloud ibrido

Per molte organizzazioni, la transizione al cloud deve essere gradualmente affrontata, in cui il modello di cloud ibrido è il primo passaggio più comune del viaggio. Per iniziare la migrazione, è possibile selezionare con attenzione il subset di applicazioni e l'infrastruttura appropriato, evitando così l'interferenza dell'attività. Tuttavia, poiché sono disponibili due piattaforme di monitoraggio che supportano questo modello cloud, i responsabili decisionali IT potrebbero non essere certi di quale sia la scelta migliore per supportare l'attività aziendale e gli obiettivi operativi IT. 

In questa sezione si affronterà l'incertezza esaminando diversi fattori e offrendo una conoscenza della piattaforma da considerare.

Tenere presenti gli aspetti tecnici principali seguenti:

- È necessario raccogliere i dati dalle risorse di Azure che supportano il carico di lavoro e trasmetterli agli strumenti esistenti in locale o nel provider di servizi gestiti.

- È necessario mantenere l'investimento attuale in System Center Operations Manager e configurarlo per monitorare le risorse IaaS e PaaS in esecuzione in Azure. Facoltativamente, poiché si stanno monitorando due ambienti con caratteristiche diverse, in base ai requisiti, è necessario determinare come l'integrazione con monitoraggio di Azure supporti la strategia.

- Come parte della strategia di modernizzazione per la standardizzazione in un singolo strumento per ridurre i costi e la complessità, è necessario eseguire il commit in monitoraggio di Azure per monitorare le risorse in Azure e nella rete aziendale.

La tabella seguente riepiloga i requisiti che monitoraggio di Azure e System Center Operations Manager supportano per il monitoraggio del modello di cloud ibrido in base a un set comune di criteri.

<!-- markdownlint-disable MD033 -->

|Requisito | Monitoraggio di Azure | Operations Manager |
|:--|:---|:---|
|Requisiti dell'infrastruttura | No | SÌ<br> Richiede almeno un server di gestione e un server SQL per ospitare il database operativo e il database di data warehouse per reporting. La complessità aumenta quando sono necessari la disponibilità elevata e il ripristino di emergenza e sono presenti computer in più siti, sistemi non attendibili e altre considerazioni di progettazione complesse.|
|Connettività limitata-Internet<br> o rete isolata | No | SÌ |
|Accesso limitato a Internet controllato dalla connettività | SÌ | SÌ |
|Connettività limitata: spesso disconnessa | SÌ | SÌ |
|Monitoraggio dello stato configurabile | No | SÌ |
| Test di disponibilità dell'app Web (rete isolata) | Sì, limitato<br> Monitoraggio di Azure ha un supporto limitato in quest'area e richiede eccezioni del firewall personalizzate. | SÌ |
| Test di disponibilità dell'app Web (distribuito a livello globale) | No | SÌ |
|Monitorare i carichi di lavoro delle macchine virtuali | Sì, limitato<br> Consente di raccogliere i log degli errori di IIS e SQL Server, gli eventi di Windows e i contatori delle prestazioni. Richiede la creazione di query, avvisi e visualizzazioni personalizzati. | SÌ<br> Supporta il monitoraggio della maggior parte dei carichi di lavoro del server con i Management Pack disponibili. Richiede l'agente di Log Analytics Windows o l'agente Operations Manager nella macchina virtuale, segnalando di nuovo il gruppo di gestione nella rete aziendale.|
|Monitorare Azure IaaS | SÌ | SÌ<br> Supporta il monitoraggio della maggior parte dell'infrastruttura dalla rete aziendale. Rileva lo stato di disponibilità, le metriche e gli avvisi per le macchine virtuali di Azure, SQL e l'archiviazione tramite il Management Pack di Azure.|
|Monitorare Azure PaaS | SÌ | Sì, limitato<br> In base a ciò che è supportato nel Management Pack di Azure. |
|Monitoraggio del servizio di Azure | SÌ<br> | SÌ<br> Sebbene non sia attualmente disponibile il monitoraggio nativo dell'integrità dei servizi di Azure tramite una Management Pack, è possibile creare flussi di lavoro personalizzati per eseguire query sugli avvisi di integrità dei servizi di Azure. Usare l'API REST di Azure per ricevere avvisi tramite le notifiche esistenti.|
|Monitoraggio delle applicazioni Web moderne | SÌ | No |
|Monitoraggio delle applicazioni Web legacy | Sì, Limited, varia a seconda dell'SDK<br> Supporta il monitoraggio delle versioni precedenti delle applicazioni Web .NET e Java. | Sì, limitato |
|Monitorare i contenitori dei servizi Kubernetes di Azure | SÌ | No |
|Monitorare i contenitori Docker/Windows | SÌ | No |
|Monitoraggio delle prestazioni di rete | SÌ | Sì, limitato<br> Supporta i controlli di disponibilità e raccoglie le statistiche di base dai dispositivi di rete usando il Simple Network Management Protocol (SNMP) dalla rete aziendale.|
|Analisi interattiva dei dati | SÌ | No<br> Si basa su SQL Server Reporting Services report predefiniti o personalizzati, soluzioni di visualizzazione di terze parti o un'implementazione di Power BI personalizzata. Il Operations Manager data warehouse presenta limitazioni relative a scalabilità e prestazioni. Eseguire l'integrazione con i log di monitoraggio di Azure come alternativa per i requisiti di aggregazione dei dati. Per ottenere l'integrazione, è necessario configurare il connettore Log Analytics.|
|Diagnostica end-to-end, analisi della causa radice e risoluzione dei problemi tempestiva | SÌ | Sì, limitato<br> Supporta la diagnostica end-to-end e la risoluzione dei problemi solo per le applicazioni e l'infrastruttura locali. USA altri componenti di System Center o soluzioni partner.|
|Visualizzazioni interattive (Dashboard) | SÌ | Sì, limitato<br> Offre dashboard essenziali con la console Web HTML5 o un'esperienza avanzata dalle soluzioni dei partner, ad esempio Squared Up e Savision. |
|Integrazione con gli strumenti IT o DevOps | SÌ | Sì, limitato |

<!-- markdownlint-enable MD033 -->

### <a name="collect-and-stream-monitoring-data-to-third-party-or-on-premises-tools"></a>Raccogliere e trasmettere i dati di monitoraggio a strumenti di terze parti o locali

Per raccogliere metriche e log dall'infrastruttura di Azure e dalle risorse della piattaforma, è necessario abilitare i registri Diagnostica di Azure per tali risorse. Inoltre, con le macchine virtuali di Azure, è possibile raccogliere metriche e log dal sistema operativo guest abilitando l'estensione Diagnostica di Azure. Per inviare i dati di diagnostica emessi dalle risorse di Azure agli strumenti locali o al provider di servizi gestiti, configurare [Hub eventi](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs) per lo streaming dei dati.

### <a name="monitor-with-system-center-operations-manager"></a>Monitorare con System Center Operations Manager

Sebbene System Center Operations Manager sia stato originariamente progettato come soluzione locale per il monitoraggio di applicazioni, carichi di lavoro e infrastruttura eseguiti nell'ambiente IT, si è evoluto per includere funzionalità di monitoraggio del cloud. Si integra con Azure, Office 365 e Amazon Web Services (AWS). Che può monitorare in questi ambienti diversi con i Management Pack progettati e aggiornati per supportarli.  

Per i clienti che hanno effettuato investimenti significativi in Operations Manager per ottenere un monitoraggio completo strettamente integrato con i loro Gestione dei servizi IT processi e strumenti oppure per i clienti che non hanno familiarità con Azure, è comprensibile chiedere quanto segue domande

- Può Operations Manager continuare a fornire valore e ha un significato aziendale?
- Le funzionalità di Operations Manager lo rendono la soluzione ideale per l'organizzazione IT?
- L'integrazione di Operations Manager con monitoraggio di Azure offre una soluzione di monitoraggio economica e completa necessaria?

Se si è già investito in Operations Manager, non è necessario concentrarsi sulla pianificazione di una migrazione per sostituirla immediatamente. Con Azure o altri provider di servizi cloud che esistono come un'estensione della propria rete locale, Operations Manager possibile monitorare le macchine virtuali guest e le risorse di Azure come se si trovassero nella rete aziendale. Questo approccio richiede una connessione di rete affidabile tra la rete e la rete virtuale di Azure con una larghezza di banda sufficiente.

Per monitorare i carichi di lavoro in esecuzione in Azure, è necessario:

- [Management Pack per Azure](https://www.microsoft.com/download/details.aspx?id=50013). Raccoglie le metriche delle prestazioni emesse dai servizi di Azure, ad esempio ruoli Web e di lavoro, Application Insights test di disponibilità (test Web), bus di servizio di Azure e così via. Il Management Pack Usa l'API REST di Azure per monitorare la disponibilità e le prestazioni di queste risorse. Alcuni tipi di servizi di Azure non dispongono di metriche o monitoraggi predefiniti nel Management Pack, ma è comunque possibile monitorarli tramite le relazioni definite nel Management Pack di Azure per i servizi individuati.

- Il [Management Pack per il database SQL di Azure](https://www.microsoft.com/download/details.aspx?id=38829) consente di monitorare la disponibilità e le prestazioni dei database SQL di Azure e dei server di database SQL di Azure usando l'API REST di Azure e le query T-SQL per SQL Server le visualizzazioni di sistema.

- Per monitorare il sistema operativo guest e i carichi di lavoro in esecuzione nella macchina virtuale, ad esempio SQL Server, IIS o Apache Tomcat, è necessario scaricare e importare i Management Pack che supportano l'applicazione, il servizio e il sistema operativo.

Le informazioni sono definite nella Management Pack, che descrive come monitorare le singole dipendenze e i singoli componenti. Entrambi i Management Pack di Azure richiedono l'esecuzione di una serie di passaggi di configurazione in Azure e Operations Manager prima di poter iniziare il monitoraggio di queste risorse.

A livello di applicazione, Operations Manager offre funzionalità di base per il monitoraggio delle prestazioni delle applicazioni per alcune versioni legacy di .NET e Java. Se alcune applicazioni all'interno dell'ambiente cloud ibrido funzionano in modalità offline o con isolamento rete, in modo che non possano comunicare con un servizio cloud pubblico, Operations Manager APM (Application Performance Monitoring) potrebbe essere un'opzione valida per alcuni scenari limitati. Per le applicazioni che non sono in esecuzione su piattaforme legacy ma sono ospitate in locale e in qualsiasi cloud pubblico che consente la comunicazione attraverso un firewall (diretto o tramite proxy) ad Azure, usare Application Insights di monitoraggio di Azure. Questo servizio offre un monitoraggio approfondito a livello di codice, con supporto di prima classe per ASP.NET, ASP.NET Core, Java, JavaScript e node. js.

Per qualsiasi applicazione Web che può essere raggiunta esternamente, è necessario abilitare un tipo di transazione sintetica nota come [monitoraggio della disponibilità]( https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability). È importante sapere se l'applicazione o un endpoint HTTP/HTTPS critico su cui si basa l'app è disponibile e reattivo. Con Application Insights monitoraggio della disponibilità è possibile eseguire test da più data center di Azure e fornire informazioni dettagliate sull'integrità dell'applicazione da una prospettiva globale.

Sebbene Operations Manager sia in grado di monitorare le risorse ospitate in Azure, esistono diversi vantaggi per l'inclusione di monitoraggio di Azure, perché i punti di forza superano le limitazioni di Operations Manager e possono definire una solida base per supportare la migrazione finale. In questo articolo vengono esaminati i punti di forza e le debolezze, con la raccomandazione di includere monitoraggio di Azure nella strategia di monitoraggio ibrido.  

#### <a name="disadvantages-of-using-operations-manager-by-itself"></a>Svantaggi dell'utilizzo di Operations Manager da solo

- L'analisi dei dati di monitoraggio in Operations Manager viene in genere eseguita utilizzando viste predefinite definite nei Management Pack a cui si accede dalla console di, dai report di SQL Server Reporting Services (SSRS) o da visualizzazioni personalizzate create dagli utenti finali. L'esecuzione di analisi ad hoc dei dati non è possibile. La creazione di report Operations Manager non è flessibile. Il data warehouse che fornisce la conservazione a lungo termine dei dati di monitoraggio non è scalabile o non funziona correttamente. Sono necessarie competenze per la scrittura di istruzioni T-SQL, lo sviluppo di una soluzione Power BI o l'uso di soluzioni di terze parti per supportare i requisiti per i vari utenti di un'organizzazione IT.

- Gli avvisi nel Operations Manager non supportano espressioni complesse o includono la logica di correlazione. Per ridurre il rumore, gli avvisi vengono raggruppati per mostrare le relazioni tra di essi e per identificarne le cause.

#### <a name="advantages-of-using-operations-manager-with-azure-monitor"></a>Vantaggi dell'uso di Operations Manager con monitoraggio di Azure

- Monitoraggio di Azure è il modo per aggirare le limitazioni di Operations Manager. Integra l'Operations Manager database data warehouse raccogliendo importanti dati di prestazioni e log. Monitoraggio di Azure offre analisi migliori, prestazioni (durante l'esecuzione di query su un volume di dati di grandi dimensioni) e conservazione rispetto al data warehouse Operations Manager. 

  Con il linguaggio di query di monitoraggio di Azure, è possibile creare query molto più complesse e sofisticate. È possibile eseguire query su terabyte di dati in pochi secondi. È possibile trasformare rapidamente i dati in grafici a torta, grafici temporali e molte altre visualizzazioni. Per analizzare questi dati, non è più necessario lavorare con Operations Manager report basati su SQL Server Reporting Services, query SQL personalizzate o altre soluzioni alternative.

- È possibile offrire un'esperienza di avviso migliorata implementando la soluzione di gestione degli avvisi di monitoraggio di Azure. Gli avvisi generati nel gruppo di gestione di Operations Manager possono essere trasmessi all'area di lavoro di analisi dei log di monitoraggio di Azure. È possibile configurare la sottoscrizione responsabile dell'invio degli avvisi da Operations Manager ai log di monitoraggio di Azure per l'invio di solo determinati avvisi. È ad esempio possibile trasmettere solo gli avvisi che soddisfano i criteri per l'esecuzione di query a supporto della gestione dei problemi per le tendenze e l'analisi della causa radice di errori o problemi, tramite un unico riquadro di vetro. Inoltre, è possibile correlare altri dati di log da Application Insights o da altre origini, per ottenere informazioni utili per migliorare l'esperienza utente, aumentare il tempo di attività e ridurre il tempo necessario per risolvere gli eventi imprevisti.

- È possibile monitorare l'infrastruttura e le applicazioni native del cloud, da un'architettura semplice o a più livelli in Azure ed è possibile usare Operations Manager per monitorare l'infrastruttura locale. Questo monitoraggio include una o più macchine virtuali, più macchine virtuali inserite in un set di disponibilità o un set di scalabilità di macchine virtuali o un'applicazione in contenitori distribuita in Azure Kubernetes Service (AKS) in esecuzione nei contenitori di Windows Server o Linux.

- È possibile usare la soluzione Controllo integrità di System Center Operations Manager per valutare in modo proattivo il livello di rischio e l'integrità del gruppo di gestione System Center Operations Manager a intervalli regolari. Questa soluzione può sostituire o integrare eventuali funzionalità personalizzate aggiunte al gruppo di gestione.

- Usando la funzionalità di mapping di Monitoraggio di Azure per le macchine virtuali, è possibile monitorare le metriche di connettività standard dalle connessioni di rete tra le macchine virtuali di Azure e le macchine virtuali locali. Queste metriche includono il tempo di risposta, le richieste al minuto, la velocità effettiva del traffico e i collegamenti. È possibile identificare le connessioni non riuscite, risolvere i problemi, eseguire la convalida della migrazione, eseguire analisi di sicurezza e verificare l'architettura complessiva del servizio. Map può individuare automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed eseguire il mapping delle comunicazioni tra i servizi. Questa automazione consente di identificare le connessioni e le dipendenze di cui si è consapevoli, pianificare e convalidare la migrazione ad Azure e ridurre al minimo la speculazione durante la risoluzione degli eventi imprevisti.

- Utilizzando Monitoraggio prestazioni rete, è possibile monitorare la connettività di rete tra:

   - La rete aziendale e Azure.
   - Applicazioni e microservizi multilivello mission-critical.
   - Percorsi utente e applicazioni basate sul Web (HTTP/HTTPS).

   Questa strategia offre visibilità del livello di rete, senza la necessità di SNMP. Può inoltre presentare, in una mappa topologica interattiva, la topologia hop-by-hop delle route tra l'endpoint di origine e quello di destinazione. Si tratta di una scelta migliore rispetto al tentativo di ottenere lo stesso risultato con il monitoraggio di rete in Operations Manager o con altri strumenti di monitoraggio della rete attualmente utilizzati nell'ambiente in uso.

### <a name="monitor-with-azure-monitor"></a>Monitorare con Monitoraggio di Azure

Anche se una migrazione al cloud presenta numerose esigenze, include anche una serie di opportunità. Consente all'organizzazione di eseguire la migrazione da uno o più strumenti di monitoraggio aziendale locali in modo da non solo ridurre potenzialmente le spese di capitale e i costi operativi, ma anche di sfruttare i vantaggi offerti da una piattaforma di monitoraggio cloud come monitoraggio di Azure può essere recapitato a livello di cloud. Esaminare i requisiti di monitoraggio e avviso, la configurazione degli strumenti di monitoraggio esistenti e i carichi di lavoro che passano al cloud. Una volta finalizzato il piano, configurare monitoraggio di Azure.

- Consente di monitorare l'infrastruttura e le applicazioni ibride, da un'architettura semplice o multilivello in cui i componenti sono ospitati tra Azure, altri provider di servizi cloud e la rete aziendale. I componenti possono includere una o più macchine virtuali, più macchine virtuali inserite in un set di disponibilità o un set di scalabilità di macchine virtuali o un'applicazione in contenitori distribuita in Azure Kubernetes Service (AKS) in esecuzione su contenitori di Windows Server o Linux.

- Abilita Monitoraggio di Azure per le macchine virtuali, monitoraggio di Azure per i contenitori e Application Insights per rilevare e diagnosticare i problemi tra l'infrastruttura e le applicazioni. Per un'analisi più approfondita e la correlazione dei dati raccolti da più componenti o dipendenze che supportano l'applicazione, è necessario usare i log di monitoraggio di Azure.

- Creare avvisi intelligenti che possono essere applicati a un set di base di applicazioni e componenti del servizio, ridurre il rumore degli avvisi con soglie dinamiche per i segnali complessi e usare l'aggregazione degli avvisi in base agli algoritmi di machine learning per identificare rapidamente il problema.

- Definire una libreria di query e dashboard per supportare i requisiti dei diversi utenti nell'organizzazione IT.

- Definire standard e metodi per abilitare il monitoraggio tra le risorse ibride e cloud, una linea di base di monitoraggio per ogni risorsa, soglie di avviso e così via.  

- Configurare il controllo degli accessi in base al ruolo (RBAC) in modo da concedere agli utenti e ai gruppi solo la quantità di accesso necessaria per monitorare i dati dalle risorse che sono responsabili della gestione.

- Includere automazione e self-service per consentire a ogni team di creare, abilitare e ottimizzare le configurazioni di monitoraggio e avviso in base alle esigenze.

## <a name="private-cloud-monitoring"></a>Monitoraggio del cloud privato

È possibile ottenere il monitoraggio olistico di Azure Stack con System Center Operations Manager. In particolare, è possibile monitorare i carichi di lavoro in esecuzione nel tenant, il livello di risorse, le macchine virtuali e l'infrastruttura che ospita Azure Stack (server fisici e commutatori di rete). 

È anche possibile ottenere il monitoraggio olistico con una combinazione di [funzionalità di monitoraggio dell'infrastruttura](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluse in Azure stack. Queste funzionalità consentono di visualizzare lo stato e gli avvisi per un'area Azure Stack e il [servizio monitoraggio di Azure](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) in Azure stack, che fornisce metriche e log dell'infrastruttura di livello base per la maggior parte dei servizi.

Se si è già investito in Operations Manager, usare il Management Pack Azure Stack per monitorare lo stato di disponibilità e integrità delle distribuzioni Azure Stack. Sono incluse le aree, i provider di risorse, gli aggiornamenti, le esecuzioni di aggiornamenti, le unità di scala, i nodi unità, i ruoli infrastruttura e le relative istanze (entità logiche costituite dalle risorse hardware). Usa le API REST del provider di risorse di integrità e aggiornamento per comunicare con Azure Stack. Per monitorare i server fisici e i dispositivi di archiviazione, usare l'Management Pack dei fornitori OEM (ad esempio, fornito da Lenovo, Hewlett Packard o dell). Operations Manager possibile monitorare in modo nativo i commutatori di rete per raccogliere statistiche di base tramite SNMP. Il monitoraggio dei carichi di lavoro del tenant è possibile con il Management Pack di Azure seguendo due passaggi di base. Configurare la sottoscrizione che si desidera monitorare e quindi aggiungere i monitoraggi per tale sottoscrizione.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Raccogli i dati corretti](./data-collection.md)
