---
title: Applicare principi di progettazione e operazioni avanzate
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Applicare principi di progettazione e operazioni avanzate
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 8daab86846ef0c3dbc93a5382f76080f678c1a08
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564999"
---
# <a name="apply-design-principles-and-advanced-operations"></a>Applicare principi di progettazione e operazioni avanzate

Le prime tre discipline di gestione del cloud descrivono una baseline di gestione. Come minimo, una linea di base di gestione deve includere un impegno aziendale standard per ridurre al minimo le interruzioni aziendali e accelerare il ripristino in caso di interruzione del servizio. La maggior parte delle linee di base di gestione comprende un'attenzione disciplinata alla gestione dell'inventario e della visibilità, della "conformità operativa" e della "protezione e ripristino".

Lo scopo di una linea di base di gestione è creare un'offerta coerente che fornisce un livello minimo di impegno aziendale per tutti i carichi di lavoro supportati. Questa linea di base delle offerte di gestione comuni e ripetibili consente al team di offrire un livello di gestione operativa altamente ottimizzato, con una deviazione minima. Tuttavia, l'offerta standard potrebbe non offrire un impegno sufficiente per l'azienda.

Il diagramma nella sezione successiva illustra tre modi per superare la linea di base di gestione.

La linea di base di gestione deve soddisfare l'impegno minimo richiesto dal 80% dei carichi di lavoro di criticità più bassi nel portfolio. La linea di base non deve essere applicata ai carichi di lavoro cruciali. Né devono essere applicati a piattaforme comuni condivise tra i carichi di lavoro. Questi carichi di lavoro richiedono un focus sui principi di progettazione e sulle operazioni avanzate.

## <a name="advanced-operations-options"></a>Opzioni avanzate per le operazioni

Sono disponibili tre percorsi consigliati per migliorare gli impegni aziendali oltre la linea di base di gestione, come illustrato nel diagramma seguente:

![Operazioni avanzate](../_images/manage/beyond-the-baseline.png)

## <a name="enhanced-management-baseline"></a>Linea di base di gestione migliorata

Come descritto nella Guida alla gestione di Azure, una linea di base di gestione avanzata usa strumenti nativi del cloud per migliorare il tempo di indisponibilità e ridurre i tempi di ripristino. I miglioramenti sono significativi, ma inferiori rispetto alla specializzazione della piattaforma o del carico di lavoro. Il vantaggio di una linea di base di gestione migliorata è la riduzione altrettanto significativa del tempo di implementazione e dei costi.

## <a name="management-specialization"></a>Specializzazione Gestione

Gli aspetti delle operazioni di carico di lavoro e piattaforma potrebbero richiedere modifiche ai principi di progettazione e architettura. Tali modifiche potrebbero richiedere tempo e potrebbero comportare un aumento delle spese operative. Per ridurre il numero di carichi di lavoro che richiedono tali investimenti, una linea di base di gestione avanzata potrebbe offrire un miglioramento sufficiente per l'impegno aziendale.

Per i carichi di lavoro che garantiscono un investimento superiore per soddisfare un impegno aziendale, la specializzazione delle operazioni è fondamentale.

## <a name="areas-of-management-specialization"></a>Aree della specializzazione di gestione

Esistono due aree di specializzazione:

- **Specializzazione piattaforma:** Investire nelle operazioni in corso di una piattaforma condivisa, distribuendo l'investimento tra più carichi di lavoro.
- **Specializzazione del carico di lavoro:** Investire nelle operazioni in corso di un carico di lavoro specifico, generalmente riservato ai carichi di lavoro di importanza critica.

### <a name="central-it-or-cloud-center-of-excellence-ccoe"></a>IT centrale o cloud Center of Excellence (CCoE)

Le decisioni tra specializzazione della piattaforma e specializzazione dei carichi di lavoro si basano sulla criticità e sull'effetto di ogni carico di lavoro Tuttavia, queste decisioni sono anche indicative di decisioni culturali più grandi tra i modelli dell'organizzazione IT centrale e CCoE.

La specializzazione del carico di lavoro spesso attiva una modifica culturale. IT tradizionale e centrale IT entrambi i processi di compilazione che possono fornire supporto su larga scala. Il supporto per la scalabilità è più raggiungibile per i servizi ripetibili trovati in una linea di base di gestione, una linea di base avanzata o anche operazioni di piattaforma. La specializzazione del carico di lavoro non si ridimensiona spesso. Questa mancanza di scalabilità rende difficile per un'organizzazione IT centralizzata fornire il supporto necessario senza raggiungere limitazioni di scalabilità organizzative.

In alternativa, l'approccio basato su cloud Center of Excellence si ridimensiona attraverso la delega intenzionale di responsabilità e la centralizzazione selettiva. La specializzazione del carico di lavoro tende a migliorare l'allineamento con l'approccio di responsabilità delegato di un CCoE.

L'allineamento naturale dei ruoli in un CCoE è descritto di seguito:

- Il team della piattaforma cloud aiuta a creare piattaforme comuni che supportano più team di adozione del cloud.
- Il team di automazione del cloud estende le piattaforme in risorse distribuibili in un catalogo di servizi.
- Gestione cloud offre la linea di base di gestione in modo centralizzato e consente di supportare l'utilizzo del catalogo di servizi.
- Tuttavia, la business unit, sotto forma di Team DevOps aziendale o team di adozione del cloud, è responsabile delle operazioni quotidiane del carico di lavoro, della pipeline o delle prestazioni.

Per quanto riguarda l'allineamento delle aree di gestione, i modelli di IT centrale e CCoE possono in genere fornire una specializzazione della piattaforma, con modifiche culturali minime. La distribuzione della specializzazione del carico di lavoro potrebbe essere un po' più complessa per i team IT centrali.

## <a name="management-specialization-processes"></a>Processi di specializzazione Gestione

All'interno di ogni specializzazione, il processo in quattro passaggi seguente viene fornito in un approccio iterativo e disciplinato. Questo approccio richiede la collaborazione tra l'adozione del cloud, la piattaforma cloud, l'automazione cloud e gli esperti di gestione cloud per creare un ciclo di feedback valido e informato.

- **Miglioramento della progettazione del sistema:** Migliorare la progettazione di sistemi comuni (piattaforme) o carichi di lavoro specifici per ridurre al minimo le interruzioni.
- **Automatizzare la correzione:** Alcuni miglioramenti non sono convenienti. In questi casi, potrebbe essere più opportuno automatizzare la correzione e ridurre l'effetto delle interruzioni.
- **Ridimensionare la soluzione:** Con il miglioramento della progettazione dei sistemi e della correzione automatica, è possibile ridimensionare le modifiche nell'ambiente tramite il catalogo di servizi.
- **Miglioramento continuo:** È possibile usare vari strumenti di monitoraggio per individuare i miglioramenti incrementali da affrontare nel passaggio successivo della progettazione del sistema, dell'automazione e della scalabilità.

### <a name="improve-system-design"></a>Migliorare la progettazione del sistema

Il miglioramento della progettazione del sistema è l'approccio più efficace per migliorare le operazioni di qualsiasi piattaforma comune. I miglioramenti della progettazione del sistema possono contribuire a migliorare la stabilità e a ridurre le interruzioni aziendali. La progettazione di singoli sistemi non rientra nell'ambito della visualizzazione dell'ambiente eseguita nel Framework di adozione del cloud. Come complemento a questo Framework, il Framework di architettura di Azure fornisce le procedure consigliate per migliorare la resilienza e la progettazione di un sistema specifico. È possibile applicare tali miglioramenti alla progettazione dei sistemi di una piattaforma o di un carico di lavoro specifico.

Il Framework di architettura di Azure è incentrato sul miglioramento tra cinque pilastri della progettazione del sistema:

- **Scalabilità:** Ridimensionamento delle risorse comuni della piattaforma per gestire un aumento del carico.
- **Disponibilità:** Riduzione delle interruzioni aziendali grazie alla possibilità di migliorare il tempo di attività.
- **Resilienza:** Miglioramento dei tempi di ripristino per ridurre la durata delle interruzioni.
- **Sicurezza:** Protezione delle applicazioni e dei dati da minacce esterne.
- **Gestione:** Processi operativi specifici per le risorse comuni della piattaforma.

La maggior parte delle interruzioni aziendali equivale a una forma di debito tecnico o a un deficit nell'architettura. Per le distribuzioni esistenti, i miglioramenti alla progettazione dei sistemi possono essere visualizzati come pagamenti rispetto al debito tecnico esistente. Per le nuove distribuzioni, i miglioramenti alla progettazione dei sistemi possono essere considerati come evitare il debito tecnico. La sezione successiva, "monitoraggio e aggiornamento automatizzato", esamina i modi per risolvere i debiti tecnici che non possono o non devono essere risolti.

Per contribuire a migliorare la progettazione del sistema, vedere altre informazioni sul [Framework di architettura di Azure](https://docs.microsoft.com/azure/architecture/guide/pillars). Con il miglioramento della progettazione del sistema, tornare a questo articolo per trovare nuove opportunità per migliorare e ridimensionare i miglioramenti nell'ambiente in uso.

### <a name="automated-remediation"></a>Correzione automatica

Alcuni crediti tecnici non possono o non devono essere risolti. La risoluzione potrebbe essere troppo costosa per essere corretta. Potrebbe essere pianificata, ma può avere una durata prolungata del progetto. L'interruzione aziendale potrebbe non avere un impatto significativo sull'azienda o la priorità di business consiste nel recuperare rapidamente anziché investire nella resilienza.

Quando la risoluzione del debito tecnico non è il percorso desiderato, il monitoraggio e aggiornamento automatico è in genere il passaggio successivo desiderato. Usare automazione di Azure e monitoraggio di Azure per rilevare le tendenze e fornire la correzione automatica è l'approccio più comune per la correzione automatica.

Per istruzioni sulla correzione automatica, vedere [automazione e avvisi di Azure](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

### <a name="scale-the-solution-with-a-service-catalog"></a>Ridimensionare la soluzione con un catalogo di servizi

L'elemento fondamentale della specializzazione della piattaforma e delle operazioni della piattaforma è un catalogo di servizi ben gestito. Questo è il modo in cui i miglioramenti apportati alla progettazione e alla correzione dei sistemi vengono ridimensionati in un ambiente. Il team di Cloud Platform e il team di automazione cloud si allineano per creare soluzioni ripetibili alle piattaforme più comuni in qualsiasi ambiente. Tuttavia, se tali soluzioni non vengono applicate in modo coerente, la gestione cloud può offrire un minor numero di offerte di base.

Per ottimizzare l'adozione e ridurre il sovraccarico di manutenzione di qualsiasi piattaforma ottimizzata, è necessario aggiungere la piattaforma a un catalogo di servizi. Ogni applicazione nel catalogo può essere distribuita per l'utilizzo interno tramite il catalogo di servizi o come offerta del Marketplace per i consumer esterni.

Per informazioni sulla pubblicazione in un catalogo di servizi, vedere la serie relativa alla [pubblicazione in un catalogo di servizi](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="continuous-improvement"></a>Miglioramento continuo

La specializzazione della piattaforma e le operazioni della piattaforma dipendono dai cicli di feedback forte tra i team di adozione, piattaforma, automazione e gestione. L'utilizzo di questi cicli di feedback nei dati consente a ogni team di prendere decisioni sagge. Per le operazioni della piattaforma per ottenere impegni aziendali a lungo termine, è importante sfruttare le informazioni specifiche della piattaforma centralizzata. Poiché i contenitori e SQL Server sono le due piattaforme gestite centralmente più comuni, è consigliabile iniziare a usare la raccolta di dati di miglioramento continuo esaminando gli articoli seguenti:

- [Prestazioni del contenitore](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Prestazioni del database PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Prestazioni del database IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
