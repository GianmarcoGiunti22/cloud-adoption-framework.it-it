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
ms.openlocfilehash: 9fdef4d5d3d9cd39d16566221262330ef110bb3a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548172"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guida al monitoraggio del cloud: strategia di monitoraggio per i modelli di distribuzione cloud

Questo articolo include la strategia di monitoraggio consigliata per ognuno dei modelli di distribuzione cloud, in base ai criteri seguenti:

- È necessario mantenere il proprio impegno per Operations Manager o un'altra piattaforma di monitoraggio aziendale a causa dell'integrazione con i processi, le conoscenze e le competenze delle operazioni IT o alcune funzionalità non ancora disponibili in monitoraggio di Azure.
- È necessario monitorare i carichi di lavoro sia in locale che nel cloud pubblico oppure solo nel cloud.
- La strategia di migrazione cloud include la modernizzazione delle operazioni IT e il passaggio alle soluzioni e ai servizi di monitoraggio cloud.
- Potrebbero essere presenti sistemi critici, gapped o fisicamente isolati, ospitati in un cloud privato o su hardware fisico e che devono essere monitorati.

Questa strategia include il supporto per il monitoraggio dell'infrastruttura (elaborazione, archiviazione e carichi di lavoro del server), l'applicazione (utente finale, le eccezioni e il client) e le risorse di rete per offrire una prospettiva di monitoraggio completa e orientata ai servizi.

## <a name="azure-cloud-monitoring"></a>Monitoraggio cloud di Azure

Monitoraggio di Azure è il servizio della piattaforma Azure native che fornisce un'unica origine per il monitoraggio delle risorse di Azure. È progettato per le soluzioni cloud basate su Azure e che supportano una funzionalità aziendale basata sui carichi di lavoro delle macchine virtuali o su architetture complesse che usano microservizi e altre risorse della piattaforma. Monitora tutti i livelli dello stack, a partire da servizi tenant come Azure Active Directory Domain Services ed eventi a livello di sottoscrizione e integrità dei servizi di Azure. Monitora anche le risorse dell'infrastruttura, ad esempio macchine virtuali, archiviazione e risorse di rete, e, al livello superiore, l'applicazione. Monitorando ognuna di queste dipendenze e raccogliendo i segnali corretti che ognuno può emettere, offre l'osservabilità delle applicazioni e l'infrastruttura chiave necessaria.

La tabella seguente riepiloga l'approccio consigliato per il monitoraggio di ogni livello dello stack.

<!-- markdownlint-disable MD033 -->

Livello | Gruppi | Scope | Metodo
---|---|---|----
Richiesta | Applicazione basata sul Web in esecuzione su .NET, .NET Core, Java, JavaScript e piattaforma node. js in una VM di Azure, app Azure Services, Azure Service Fabric, funzioni di Azure e servizi cloud di Azure | Monitorare un'applicazione Web attiva per rilevare automaticamente le anomalie delle prestazioni, identificare le eccezioni e i problemi del codice e raccogliere analisi del comportamento dell'utente. |  Monitoraggio di Azure (Application Insights)
Risorse di Azure-PaaS | 1. servizi di database di Azure (ad esempio, SQL o mySQL) | 1. metriche delle prestazioni del database di Azure per SQL. | 1. abilitare la registrazione diagnostica per trasmettere i dati SQL ai log di monitoraggio di Azure.
Risorse di Azure-IaaS | 1. archiviazione di Azure<br/> 2. applicazione Azure gateway<br/> 3. gruppi di sicurezza di rete<br/> 4. gestione traffico di Azure<br/> 5. macchina virtuale<br/> 6. servizio Azure Kubernetes/istanze di contenitore di Azure | 1. capacità, disponibilità e prestazioni.<br/> 2. log di diagnostica e di prestazioni (attività, accesso, prestazioni e firewall).<br/> 3. monitorare gli eventi quando vengono applicate le regole e il contatore delle regole per il numero di volte in cui una regola viene applicata a Deny o Allow.<br/> 4. monitorare la disponibilità dello stato dell'endpoint.<br/> 5. monitorare la capacità, la disponibilità e le prestazioni nel sistema operativo della macchina virtuale guest. Eseguire il mapping delle dipendenze delle app ospitate in ogni macchina virtuale, inclusa la visibilità delle connessioni di rete attive tra i server, la latenza delle connessioni in ingresso e in uscita e le porte di qualsiasi architettura connessa a TCP.<br/> 6. monitorare la capacità, la disponibilità e le prestazioni dei carichi di lavoro in esecuzione su contenitori e istanze di contenitore. | 1. metriche di archiviazione per l'archiviazione BLOB.<br/> 2. abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.<br/> 3. abilitare la registrazione diagnostica dei gruppi di sicurezza di rete e configurare lo streaming nei log di monitoraggio di Azure.<br/> 4. abilitare la registrazione diagnostica degli endpoint di gestione traffico e configurare lo streaming nei log di monitoraggio di Azure.<br/> 5. abilitare Monitoraggio di Azure per le macchine virtuali<br/> 6. abilitare monitoraggio di Azure per i contenitori
Rete| Comunicazione tra la macchina virtuale e uno o più endpoint (un'altra VM, un nome di dominio completo, un identificatore di risorsa uniforme o un indirizzo IPv4). | Monitorare la raggiungibilità, la latenza e le modifiche alla topologia di rete che si verificano tra la macchina virtuale e l'endpoint. | Azure Network Watcher
Sottoscrizione di Azure | Integrità del servizio di Azure e integrità delle risorse di base | <li> Azioni amministrative eseguite su un servizio o una risorsa.<br/><li> L'integrità del servizio con un servizio di Azure è in uno stato danneggiato o non disponibile.<br/><li> Problemi di integrità rilevati con una risorsa di Azure dal punto di vista del servizio di Azure.<br/><li> Operazioni eseguite con la scalabilità automatica di Azure che indicano un errore o un'eccezione. <br/><li> Operazioni eseguite con criteri di Azure che indicano che si è verificata un'azione consentita o negata.<br/><li> Record degli avvisi generati dal centro sicurezza di Azure. |Recapitato nel log attività per il monitoraggio e l'invio di avvisi tramite Azure Resource Manager.
Tenant di Azure|Azure Active Directory || Abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Monitoraggio del cloud ibrido

Per molte organizzazioni, il cloud deve essere approcciato gradualmente, in cui il modello di cloud ibrido è il primo passaggio più comune del viaggio. È possibile selezionare con attenzione il subset appropriato di applicazioni e l'infrastruttura per iniziare la migrazione, evitando così l'intralcio per l'azienda. Tuttavia, poiché sono disponibili due piattaforme di monitoraggio che supportano questo modello cloud, i responsabili decisionali IT sono confusi per la scelta migliore per supportare l'attività aziendale e gli obiettivi operativi IT. Verranno esaminati diversi fattori per risolvere l'incertezza e verrà fornita una conoscenza della piattaforma da considerare.

Di seguito sono riportate alcune delle principali caratteristiche tecniche da considerare:

- È necessario raccogliere i dati dalle risorse di Azure che supportano il carico di lavoro e trasmetterli agli strumenti locali o del provider di servizi gestiti esistenti.

- È necessario mantenere l'investimento attuale in System Center Operations Manager e configurarlo per monitorare le risorse IaaS e PaaS in esecuzione in Azure. Facoltativamente, poiché si monitorano due ambienti con caratteristiche diverse, a seconda dei requisiti, è possibile determinare l'integrazione con monitoraggio di Azure per supportare la strategia.

- Come parte della strategia di modernizzazione per la standardizzazione in un singolo strumento per ridurre i costi e la complessità, è possibile eseguire il commit in monitoraggio di Azure per monitorare le risorse in Azure e nella rete aziendale.

La tabella seguente riepiloga i requisiti che monitoraggio di Azure e System Center Operations Manager supportano per il monitoraggio del modello di cloud ibrido in base a un set comune di criteri.

<!-- markdownlint-disable MD033 -->

|Requisito | Monitoraggio di Azure | Operations Manager |
|:--|:---|:---|
|Requisiti dell'infrastruttura | **No** | **Sì**<br> Richiede almeno un server di gestione e un server SQL per ospitare il database operativo e il database di data warehouse per reporting. Diventa più complesso quando sono necessari la disponibilità elevata e il ripristino di emergenza, i computer in più siti, sistemi non attendibili e altre considerazioni di progettazione complesse.|
|Connettività limitata-Internet<br> o rete isolata | **No** | **Sì** |
|Accesso limitato a Internet controllato dalla connettività | **Sì** | **Sì** |
|Connettività limitata: spesso disconnessa | **Sì** | **Sì** |
|Monitoraggio dello stato configurabile | **No** | **Sì** |
| Test di disponibilità dell'app Web (rete isolata) | **Sì, limitato**<br> Monitoraggio di Azure ha un supporto limitato in quest'area e richiede eccezioni del firewall personalizzate. | **Sì** |
| Test di disponibilità dell'app Web (distribuito a livello globale) | **No** | **Sì** |
|Monitorare i carichi di lavoro delle macchine virtuali | **Sì, limitato**<br> Consente di raccogliere i log degli errori di IIS e SQL Server, gli eventi di Windows e i contatori delle prestazioni. Richiede la creazione di query, avvisi e visualizzazioni personalizzati. | **Sì**<br> Supporta il monitoraggio della maggior parte dei carichi di lavoro del server con i Management Pack disponibili. Richiede l'agente di Log Analytics Windows o l'agente Operations Manager nella macchina virtuale, segnalando di nuovo il gruppo di gestione nella rete aziendale.|
|Monitorare Azure IaaS | **Sì** | **Sì**<br> Supporta il monitoraggio della maggior parte dell'infrastruttura dalla rete aziendale. Rileva lo stato di disponibilità, le metriche e gli avvisi per le macchine virtuali di Azure, SQL e l'archiviazione tramite il Management Pack di Azure.|
|Monitorare Azure PaaS | **Sì** | **Sì, limitato**<br> In base a ciò che è supportato nel Management Pack di Azure. |
|Monitoraggio del servizio di Azure | **Sì**<br> | **Sì**<br> Sebbene non sia attualmente disponibile il monitoraggio nativo dell'integrità dei servizi di Azure tramite una Management Pack, è possibile creare flussi di lavoro personalizzati per eseguire query sugli avvisi di integrità dei servizi di Azure. Usare l'API REST di Azure per ricevere avvisi tramite le notifiche esistenti.|
|Monitoraggio delle applicazioni Web moderne | **Sì** | **No** |
|Monitoraggio delle applicazioni Web legacy | **Sì, Limited varia a seconda dell'SDK**<br> Supporta il monitoraggio delle versioni precedenti delle applicazioni Web .NET e Java. | **Sì, limitato** |
|Monitorare i contenitori dei servizi Kubernetes di Azure | **Sì** | **No** |
|Monitorare i contenitori Docker/Windows | **Sì** | **No** |
|Monitoraggio delle prestazioni di rete | **Sì** | **Sì, limitato**<br> Supporta i controlli di disponibilità e raccoglie le statistiche di base dai dispositivi di rete utilizzando il protocollo SNMP dalla rete aziendale.|
|Analisi interattiva dei dati | **Sì** | **No**<br> Si basa su SQL Server Reporting Services report predefiniti o personalizzati, soluzioni di visualizzazione di terze parti o un'implementazione di Power BI personalizzata. Il Operations Manager data warehouse presenta limitazioni relative a scalabilità e prestazioni. Eseguire l'integrazione con i log di monitoraggio di Azure come alternativa per i requisiti di aggregazione dei dati. L'integrazione viene eseguita configurando il connettore Log Analytics.|
|Diagnostica end-to-end, analisi della causa radice e risoluzione dei problemi tempestiva | **Sì** | **Sì, limitato**<br> Supporta la diagnostica end-to-end e la risoluzione dei problemi solo per le applicazioni e l'infrastruttura locali. USA altri componenti di System Center o soluzioni partner.|
|Visualizzazioni interattive (Dashboard) | **Sì** | **Sì, limitato**<br> Offre dashboard essenziali con la console Web HTLM5 o un'esperienza avanzata dalle soluzioni dei partner come Squared Up e Savision. |
|Integrazione con gli strumenti IT/DevOps | **Sì** | **Sì, limitato** |

<!-- markdownlint-enable MD033 -->

### <a name="collect-and-stream-monitoring-data-to-third-party-or-on-premises-tools"></a>Raccogliere e trasmettere i dati di monitoraggio a strumenti di terze parti o locali

Per raccogliere metriche e log dall'infrastruttura di Azure e dalle risorse della piattaforma, è necessario abilitare i log di diagnostica di Azure per tali risorse. Inoltre, con le macchine virtuali di Azure, è possibile raccogliere metriche e log dal sistema operativo guest abilitando l'estensione Diagnostica di Azure. Per inviare i dati di diagnostica emessi dalle risorse di Azure agli strumenti locali o al provider di servizi gestiti, configurare [Hub eventi](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs) per trasmettere i dati.

### <a name="monitor-with-system-center-operations-manager"></a>Monitorare con System Center Operations Manager

Sebbene System Center Operations Manager sia stato originariamente progettato come soluzione locale per il monitoraggio di applicazioni, carichi di lavoro e infrastruttura in esecuzione nell'ambiente IT, si è evoluto in modo da includere funzionalità di monitoraggio del cloud e integrarsi con Azure, Office 365 e Amazon Web Services (AWS). È in grado di eseguire il monitoraggio in questi diversi ambienti con i Management Pack progettati e aggiornati per supportarli.  

Per i clienti che hanno effettuato investimenti significativi in Operations Manager per ottenere un monitoraggio completo strettamente integrato con i loro processi e strumenti di Gestione dei servizi IT, o con i clienti nuovi in Azure, è comprensibile porsi una domanda:

- Può Operations Manager continuare a fornire un valore e a un senso aziendale?

- Se le funzionalità di Operations Manager lo rendono idonea per la nostra organizzazione IT?

- L'integrazione di Operations Manager con monitoraggio di Azure offre una soluzione di monitoraggio economica e completa necessaria?

Se si è già investito in Operations Manager, non è necessario concentrarsi sulla pianificazione di una migrazione per la sostituzione immediata. Con Azure o altri provider di servizi cloud esistenti come estensione della rete locale, Operations Manager possibile monitorare le macchine virtuali guest e le risorse di Azure come se si trovassero nella rete aziendale. A tale scopo, è necessario disporre di una connessione di rete affidabile tra la rete e la rete virtuale di Azure con una larghezza di banda sufficiente.

Per monitorare i carichi di lavoro in esecuzione in Azure, è necessario:

- Il [Management Pack di Azure](https://www.microsoft.com/download/details.aspx?id=50013) per raccogliere le metriche delle prestazioni emesse dai servizi di Azure, ad esempio i ruoli Web e di lavoro, i test di disponibilità Application Insights (test Web), il bus di servizio e così via. Il Management Pack Usa l'API REST di Azure per monitorare la disponibilità e le prestazioni di queste risorse. Alcuni tipi di servizi di Azure non hanno alcuna metrica né monitoraggi predefiniti nel Management Pack, ma possono comunque essere monitorati tramite le relazioni definite nel Management Pack di Azure per i servizi individuati.

- Il [database SQL di azure Management Pack](https://www.microsoft.com/download/details.aspx?id=38829) per monitorare la disponibilità e le prestazioni dei database SQL di Azure e dei server di database SQL di Azure usando l'API REST di Azure e le query T-SQL per SQL Server le visualizzazioni di sistema.

- Per monitorare il sistema operativo guest e i carichi di lavoro in esecuzione nella macchina virtuale, ad esempio SQL Server, IIS o Apache Tomcat, è necessario scaricare e importare i Management Pack che supportano l'applicazione, il servizio e il sistema operativo.

Le informazioni sono definite nella Management Pack, che descrive come monitorare le singole dipendenze e i singoli componenti. Entrambi i Management Pack di Azure richiedono l'esecuzione di una serie di passaggi di configurazione in Azure e Operations Manager per iniziare a monitorare queste risorse.

A livello di applicazione, Operations Manager offre funzionalità di base per il monitoraggio delle prestazioni delle applicazioni per alcune versioni legacy di .NET e Java. Se alcune applicazioni all'interno dell'ambiente cloud ibrido operano in modalità offline o con isolamento rete, in modo che non possano comunicare con un servizio cloud pubblico, Operations Manager APM (Application Performance Monitoring) può essere un'opzione valida per alcuni scenari limitati. Per le applicazioni non in esecuzione su piattaforme legacy, ospitate sia in locale che in qualsiasi cloud pubblico che consente la comunicazione attraverso un firewall (diretto o tramite proxy) ad Azure, usare Application Insights di monitoraggio di Azure. Questo offre un monitoraggio approfondito a livello di codice, con supporto di prima classe per ASP.NET, ASP.NET Core, Java, JavaScript e node. js.

Per qualsiasi applicazione Web che può essere raggiunta esternamente, è necessario abilitare un tipo di transazioni sintetiche noto come [monitoraggio della disponibilità]( https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability). È importante stabilire se l'applicazione o un endpoint HTTP/HTTPS critico su cui si basa l'app è disponibile e reattivo. Application Insights monitoraggio della disponibilità consente di eseguire test da più data center di Azure e di fornire informazioni dettagliate sull'integrità dell'applicazione da una prospettiva globale.

Sebbene Operations Manager sia in grado di monitorare le risorse ospitate in Azure, sono disponibili diversi vantaggi per l'inclusione di monitoraggio di Azure, in quanto i punti di forza superano le limitazioni di Operations Manager e stabiliscono una base solida per supportare la migrazione finale da questa pagina. In questo articolo vengono esaminate tutte le raccomandazioni per includere monitoraggio di Azure nella strategia di monitoraggio ibrido.  

#### <a name="disadvantage-of-using-operations-manager-by-itself"></a>Svantaggi dell'utilizzo di Operations Manager da solo

1. L'analisi dei dati di monitoraggio in Operations Manager viene in genere eseguita utilizzando viste predefinite definite nei Management Pack a cui si accede dalla console di, dai report di SQL Server Reporting Services (SSRS) o da visualizzazioni personalizzate create dall'utente finale. L'esecuzione di un'analisi ad hoc dei dati non è possibile. La creazione di report Operations Manager non è flessibile, il data warehouse che fornisce la conservazione a lungo termine dei dati di monitoraggio non è scalabile o non funziona correttamente e le competenze per scrivere istruzioni T-SQL, sviluppare una soluzione Power BI o usare soluzioni di terze parti sono necessaria per supportare i requisiti per i diversi utenti di un'organizzazione IT.

2. Gli avvisi nel Operations Manager non forniscono supporto per espressioni complesse e includono la logica di correlazione per ridurre il rumore degli avvisi e raggruppare gli avvisi in modo da visualizzare la relazione tra di essi per identificare la causa radice del problema.

#### <a name="advantage-of-operations-manager--azure-monitor"></a>Vantaggi di Operations Manager + monitoraggio di Azure

1. I log di monitoraggio di Azure sono la soluzione ideale per aggirare le limitazioni di Operations Manager e i Operations Manager database data warehouse per raccogliere importanti dati di prestazioni e log. Monitoraggio di Azure offre analisi migliori, prestazioni durante l'esecuzione di query su volumi di dati di grandi dimensioni e conservazione rispetto al data warehouse Operations Manager. Il linguaggio di query consente di creare query molto più complesse e sofisticate, con la possibilità di eseguire query su terabyte di dati in pochi secondi. È possibile trasformare rapidamente i dati in grafici a torta, grafici temporali e molte altre visualizzazioni. Non è più necessario usare i report in Operations Manager basati su SQL Server Reporting Services, query SQL personalizzate o altre soluzioni alternative per analizzare questi dati.

2. Offrire un'esperienza di avviso migliorata implementando la soluzione di gestione degli avvisi di monitoraggio di Azure. Gli avvisi generati nel gruppo di gestione di Operations Manager possono essere trasmessi all'area di lavoro di analisi dei log di monitoraggio di Azure. È possibile configurare la sottoscrizione responsabile dell'invio degli avvisi da Operations Manager ai log di monitoraggio di Azure per l'invio solo di determinati avvisi. È ad esempio possibile trasmettere solo gli avvisi che soddisfano i criteri per l'esecuzione di query a supporto della gestione dei problemi per le tendenze e l'analisi della causa radice di errori o problemi, tramite un unico riquadro di vetro. Inoltre, è possibile correlare altri dati di log da Application Insights o da altre origini, per ottenere informazioni utili per migliorare l'esperienza utente, aumentare il tempo di attività e ridurre il tempo necessario per risolvere gli eventi imprevisti.

3. Monitora l'infrastruttura e le applicazioni native del cloud, da un'architettura semplice o a più livelli in Azure e usa Operations Manager per monitorare l'infrastruttura locale. Sono incluse una o più macchine virtuali, più macchine virtuali inserite in un set di disponibilità o un set di scalabilità di macchine virtuali o un'applicazione in contenitori distribuita in Azure Kubernetes Service (AKS) in esecuzione su contenitori di Windows Server o Linux.

4. Usare la soluzione Controllo integrità di System Center Operations Manager per valutare in modo proattivo il rischio e l'integrità del gruppo di gestione System Center Operations Manager a intervalli regolari. Questo può sostituire o complimentarsi con le funzionalità personalizzate aggiunte al gruppo di gestione.

5. Con la funzionalità di mapping di Monitoraggio di Azure per le macchine virtuali, è possibile monitorare le metriche di connettività standard dalle connessioni di rete tra le macchine virtuali di Azure e le macchine virtuali locali. Queste metriche includono il tempo di risposta, le richieste al minuto, la velocità effettiva del traffico e i collegamenti. È possibile identificare le connessioni non riuscite, risolvere i problemi, eseguire la convalida della migrazione, eseguire analisi di sicurezza e verificare l'architettura complessiva del servizio. Map può individuare automaticamente i componenti delle applicazioni nei sistemi Windows e Linux ed eseguire il mapping delle comunicazioni tra i servizi. Questo consente di identificare le connessioni e le dipendenze di cui si è consapevoli, pianificare e convalidare la migrazione ad Azure e ridurre al minimo la speculazione durante la risoluzione degli eventi imprevisti.

6. Utilizzando Monitoraggio prestazioni rete, monitorare la connettività di rete tra:

   - La rete aziendale e Azure.

   - Applicazioni e micro-servizi multilivello mission-critical.

   - Percorsi utente e applicazioni basate sul Web (HTTP/HTTPs).

   Questa strategia offre visibilità del livello di rete, senza la necessità di SNMP. Può anche essere presente in una mappa topologica interattiva, la topologia hop-by-hop delle route tra l'endpoint di origine e quello di destinazione. Si tratta di una scelta migliore rispetto al tentativo di ottenere lo stesso risultato con il monitoraggio di rete in Operations Manager o altri strumenti di monitoraggio di rete attualmente utilizzati nell'ambiente in uso.

### <a name="monitor-with-azure-monitor"></a>Monitorare con Monitoraggio di Azure

Mentre una migrazione al cloud presenta numerose esigenze, include anche una serie di opportunità. Consente all'organizzazione di eseguire la migrazione da uno o più strumenti di monitoraggio aziendale locali in modo da non solo ridurre potenzialmente le spese di capitale e i costi operativi, ma anche i vantaggi offerti da una piattaforma di monitoraggio cloud come Azure monitor a livello di cloud. Esaminare i requisiti di monitoraggio e avviso, la configurazione degli strumenti di monitoraggio esistenti, i carichi di lavoro che passano al cloud e la configurazione di monitoraggio di Azure dopo la finalizzazione del piano.

- Consente di monitorare l'infrastruttura e le applicazioni ibride, da un'architettura semplice o a più livelli in cui i componenti sono ospitati tra Azure, altri provider di servizi cloud e la rete aziendale. Sono incluse una o più macchine virtuali, più macchine virtuali inserite in un set di disponibilità o un set di scalabilità di macchine virtuali o un'applicazione in contenitori distribuita in Azure Kubernetes Service (AKS) in esecuzione su contenitori di Windows Server o Linux.

- Abilita Monitoraggio di Azure per le macchine virtuali, monitoraggio di Azure per i contenitori e Application Insights per rilevare e diagnosticare i problemi tra l'infrastruttura e le applicazioni. Per un'analisi più approfondita e la correlazione dei dati raccolti da più componenti o dipendenze che supportano l'applicazione, è necessario usare i log di monitoraggio di Azure.

- Creare avvisi intelligenti che possono essere applicati a un set di base di applicazioni e componenti del servizio, ridurre il rumore degli avvisi con soglie dinamiche per i segnali complessi e usare l'aggregazione degli avvisi in base agli algoritmi di machine learning per identificare rapidamente il problema.

- Definire una libreria di query e dashboard per supportare i requisiti per i diversi utenti di un'organizzazione IT.

- Definire standard e metodi per abilitare il monitoraggio tra le risorse ibride e cloud, una linea di base di monitoraggio per ogni risorsa, soglie di avviso e così via.  

- Configurare il controllo degli accessi in base al ruolo (RBAC) in modo da concedere agli utenti e ai gruppi solo la quantità di accesso necessaria per lavorare con i dati di monitoraggio dalle risorse che sono responsabili della gestione.

- Includere automazione e self-service per consentire a ogni team di creare, abilitare e ottimizzare le configurazioni di monitoraggio e avviso in base alle esigenze.

## <a name="private-cloud-monitoring"></a>Monitoraggio del cloud privato

È possibile ottenere il monitoraggio olistico di Azure Stack con System Center Operations Manager. In particolare, è possibile monitorare i carichi di lavoro in esecuzione nel tenant, il livello di risorse, le macchine virtuali e l'infrastruttura che ospita Azure Stack (server fisici e commutatori di rete). È anche possibile ottenere il monitoraggio olistico con una combinazione di [funzionalità di monitoraggio dell'infrastruttura](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluse in Azure stack. Queste funzionalità consentono di visualizzare lo stato e gli avvisi per un'area Azure Stack e il [servizio monitoraggio di Azure](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) in Azure stack, che fornisce metriche e log dell'infrastruttura di livello base per la maggior parte dei servizi.

Se si è già investito in Operations Manager, usare il Management Pack Azure Stack per monitorare lo stato di disponibilità e integrità delle distribuzioni Azure Stack. Sono incluse le aree, i provider di risorse, gli aggiornamenti, le esecuzioni di aggiornamenti, le unità di scala, i nodi unità, i ruoli infrastruttura e le relative istanze (entità logiche costituite dalle risorse hardware). Usa le API REST del provider di risorse di integrità e aggiornamento per comunicare con Azure Stack. Per monitorare i server fisici e i dispositivi di archiviazione, usare l'Management Pack dei fornitori OEM (ad esempio, fornito da Lenovo, Hewlett Packard o dell). Operations Manager possibile monitorare in modo nativo i commutatori di rete per raccogliere statistiche di base tramite il protocollo SNMP. Il monitoraggio dei carichi di lavoro del tenant è possibile con il Management Pack di Azure seguendo due passaggi di base. Configurare la sottoscrizione che si desidera monitorare e quindi aggiungere i monitoraggi per tale sottoscrizione.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Raccolta dei dati appropriati](./data-collection.md)
