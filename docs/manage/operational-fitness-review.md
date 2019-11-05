---
title: Stabilire una verifica dell'idoneità operativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Linee guida per i concetti fondamentali dell'operatività
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 122f1e451c8b83de3d020c58426d8b897013aa8d
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564901"
---
# <a name="establish-an-operational-fitness-review"></a>Stabilire una verifica dell'idoneità operativa

Quando l'azienda inizia a usare i carichi di lavoro in Azure, il passaggio successivo consiste nel definire un processo per la *Verifica dell'idoneità operativa*. Questo processo enumera, implementa e esamina in modo iterativo i *requisiti non funzionali* per questi carichi di lavoro. I requisiti non funzionali sono correlati al comportamento operativo previsto del servizio.

Esistono cinque categorie essenziali di requisiti non funzionali, detti [pilastri della qualità del software](https://docs.microsoft.com/azure/architecture/guide/pillars):

- Scalabilità
- Disponibilità
- Resilienza, tra cui la continuità aziendale e il ripristino di emergenza
- gestione
- Sicurezza

Un processo per la verifica dell'idoneità operativa garantisce che i carichi di lavoro cruciali soddisfino le aspettative dell'azienda rispetto ai pilastri qualitativi.

Creare un processo per la verifica dell'idoneità operativa per comprendere completamente i problemi derivanti dall'esecuzione di carichi di lavoro in un ambiente di produzione e come correggere e risolvere tali problemi. Questo articolo descrive un processo di alto livello per la revisione di idoneità operativa che l'azienda può usare per raggiungere questo obiettivo.

## <a name="operational-fitness-at-microsoft"></a>Idoneità operativa a Microsoft

Fin dall'inizio, molti team di Microsoft hanno partecipato allo sviluppo della piattaforma Azure. È difficile garantire la qualità e la coerenza per un progetto di tali dimensioni e complessità. È necessario un processo affidabile per enumerare e implementare i requisiti di base non funzionali a intervalli regolari.

I processi che Microsoft segue costituiscono la base per i processi descritti in questo articolo.

## <a name="understand-the-problem"></a>Informazioni sul problema

Come illustrato in [Introduzione](../getting-started/migrate.md), il primo passaggio della trasformazione digitale di un'azienda consiste nell'identificare i problemi aziendali da risolvere mediante l'adozione di Azure. Il passaggio successivo consiste nel determinare una soluzione di alto livello al problema, ad esempio la migrazione di un carico di lavoro nel cloud o l'adattamento di un servizio locale esistente per includere le funzionalità cloud. Infine, è necessario progettare e implementare la soluzione.

Durante questo processo, lo stato attivo è spesso relativo alle funzionalità del servizio: il set di requisiti _funzionali_ che si desidera venga eseguito dal servizio. Il servizio di recapito di un prodotto, ad esempio, richiede funzionalità per determinare le posizioni di origine e di destinazione del prodotto, tenere traccia del prodotto durante il recapito e inviare notifiche al cliente.

I requisiti non _funzionali_ , al contrario, si riferiscono a proprietà quali la [disponibilità](https://docs.microsoft.com/azure/architecture/checklist/availability), la [resilienza](https://docs.microsoft.com/azure/architecture/resiliency)e la [scalabilità](https://docs.microsoft.com/azure/architecture/checklist/scalability)del servizio. Queste proprietà differiscono dai requisiti funzionali perché non influiscono direttamente sulla funzione finale di una particolare funzionalità nel servizio. Tuttavia, i requisiti non funzionali sono correlati alle prestazioni e alla continuità del servizio.

È possibile specificare alcuni requisiti non funzionali in termini di contratto di servizio (SLA). Ad esempio, è possibile esprimere la continuità del servizio come percentuale della disponibilità: "disponibile 99,99% del tempo". Altri requisiti non funzionali potrebbero risultare più difficili da definire e possono cambiare in base alle esigenze di produzione. Un servizio orientato ai consumatori, ad esempio, potrebbe affrontare i requisiti di velocità effettiva inaspettati dopo un picco di popolarità.

> [!NOTE]
> Per altre informazioni sui requisiti di resilienza, vedere [progettazione di applicazioni Azure affidabili](https://docs.microsoft.com/azure/architecture/reliability#define-requirements). Questo articolo include spiegazioni di concetti quali il punto di ripristino (RPO), l'obiettivo del tempo di ripristino (RTO) e il contratto di servizio.

## <a name="process-for-operational-fitness-review"></a>Processo per la verifica dell'idoneità operativa

La chiave per mantenere le prestazioni e la continuità dei servizi di un'azienda consiste nell'implementazione di un processo per la verifica dell'idoneità operativa.

![Panoramica del processo di analisi di idoneità operativa](../_images/manage/ofr-flow.png)

A livello generale, il processo prevede due fasi. Nella *fase dei prerequisiti*i requisiti vengono stabiliti e mappati ai servizi di supporto. Questa fase si verifica raramente: probabilmente ogni anno o quando vengono introdotte nuove operazioni. L'output della fase dei prerequisiti viene usato nella *fase del flusso*. La fase di flusso viene eseguita più di frequente, ad esempio ogni mese.

### <a name="prerequisites-phase"></a>Fase dei prerequisiti

I passaggi in questa fase acquisiscono i requisiti per l'esecuzione di una revisione regolare dei servizi importanti.

1. **Identificare le operazioni aziendali cruciali**. Identificare le operazioni aziendali cruciali dell'organizzazione. Le operazioni aziendali sono indipendenti da qualsiasi funzionalità dei servizi di supporto. In altre parole, le operazioni di business rappresentano le attività effettive che devono essere eseguite dall'azienda e supportate da un set di servizi IT.

    Il termine *mission-critical* (o *business critical*) riflette un grave effetto sull'azienda se l'operazione è ostacolata. Un rivenditore online, ad esempio, potrebbe avere un'operazione aziendale, ad esempio "consentire a un cliente di aggiungere un elemento a un carrello acquisti" o "elaborare un pagamento con carta di credito". Se una di queste operazioni ha esito negativo, un cliente non può completare la transazione e l'azienda non riesce a realizzare le vendite.

1. **Abbinare le operazioni ai servizi**. Eseguire il mapping delle operazioni aziendali critiche ai servizi che le supportano. Nell'esempio relativo al carrello della spesa potrebbero essere necessari diversi servizi, tra cui un servizio di gestione delle scorte di inventario e un servizio di carrello acquisti. Per elaborare un pagamento con carta di credito, un servizio di pagamento locale può interagire con un servizio di elaborazione dei pagamenti di terze parti.

1. **Analizzare le dipendenze dei servizi**. Per la maggior parte delle operazioni aziendali è necessaria un'orchestrazione tra più servizi di supporto È importante comprendere le dipendenze tra i servizi e il flusso di transazioni cruciali attraverso questi servizi.

    Prendere in considerazione anche le dipendenze tra i servizi locali e i servizi di Azure. Nell'esempio relativo al carrello della spesa, il servizio di gestione delle scorte di inventario potrebbe essere ospitato in locale e inserire i dati immessi dai dipendenti da un magazzino fisico. Tuttavia, potrebbe archiviare i dati fuori sede in un servizio di Azure, ad esempio [archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction)o un database, ad esempio [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction).

Un output da queste attività è un set di *metriche di scorecard* per le operazioni del servizio. La scorecard misura i criteri come la disponibilità, la scalabilità e il ripristino di emergenza. Le metriche della scorecard esprimono i criteri operativi previsti per il servizio. Queste metriche possono essere espresse a qualsiasi livello di granularità appropriato per l'operazione del servizio.

La scorecard deve essere espressa in termini semplici per promuovere scambi di opinioni significativi tra i titolari dell'azienda e il personale tecnico. Una metrica scorecard per la scalabilità, ad esempio, potrebbe essere codificata in modo semplice. Verde significa che soddisfano i criteri definiti, il giallo significa che non soddisfa i criteri definiti, ma implementa attivamente una correzione pianificata e il rosso significa che non soddisfa i criteri definiti senza alcun piano o azione.

È importante sottolineare che queste metriche devono riflettere direttamente le esigenze aziendali.

### <a name="service-review-phase"></a>Servizio-fase di Revisione

La fase di revisione del servizio è il nucleo della verifica di idoneità operativa. Questa procedura include i passaggi seguenti:

1. **Misurare le metriche del servizio**. Usare le metriche scorecard per monitorare i servizi, in modo da garantire che i servizi soddisfino le esigenze aziendali. Il monitoraggio del servizio è essenziale. Se non è possibile monitorare un set di servizi per quanto riguarda i requisiti non funzionali, prendere in considerazione le metriche della scorecard corrispondenti in rosso. In questo caso, il primo passaggio per la correzione consiste nell'implementare il monitoraggio del servizio appropriato. Se, ad esempio, l'azienda prevede che un servizio operi con una disponibilità del 99,99%, ma non sono disponibili dati di telemetria di produzione per misurare la disponibilità, si supponga di non soddisfare i requisiti.

2. **Pianificare gli interventi correttivi**. Per ogni operazione del servizio per la quale le metriche scendono al di sotto di una soglia accettabile, determinare il costo della correzione del servizio per portare l'operazione a un livello accettabile. Se il costo per il monitoraggio e l'aggiornamento del servizio è superiore alla generazione dei ricavi previsti per il servizio, è opportuno prendere in considerazione i costi intangibili, ad esempio l'esperienza del cliente. Se, ad esempio, i clienti hanno difficoltà a inserire un ordine corretto usando il servizio, potrebbero invece scegliere un concorrente.

3. **Implementare gli interventi correttivi**. Una volta che i proprietari dell'azienda e il team di progettazione hanno accettato un piano, implementarlo. Segnalare lo stato dell'implementazione quando si esaminano le metriche della scorecard.

Questo processo è iterativo e idealmente l'azienda dispone di un team dedicato. Questo team deve essere aggiornato regolarmente per esaminare i progetti correttivi esistenti, avviare la revisione fondamentale dei nuovi carichi di lavoro e tenere traccia della scorecard complessiva dell'azienda. Il team deve inoltre disporre dell'autorità per tenere conto dei team di monitoraggio e aggiornamento in caso di mancata pianificazione o di mancato rispetto della metrica.

## <a name="structure-of-the-review-team"></a>Struttura del team di Revisione

Il team responsabile della revisione dell'idoneità operativa è costituito dai ruoli seguenti:

- **Proprietario dell'azienda:** Fornisce informazioni sull'azienda per identificare e classificare in ordine di priorità ogni operazione aziendale cruciale. Questo ruolo confronta inoltre il costo della mitigazione con l'impatto aziendale e determina la decisione finale sul monitoraggio e l'aggiornamento.

- **Business Advocate:** Suddivide le operazioni aziendali in parti discrete ed esegue il mapping di tali parti ai servizi e all'infrastruttura, sia in locale che nel cloud. Il ruolo richiede una profonda conoscenza della tecnologia associata a ogni operazione aziendale.

- **Proprietario della progettazione:** Implementa i servizi associati all'operazione di business. Questi utenti possono partecipare alla progettazione, all'implementazione e alla distribuzione di qualsiasi soluzione per problemi di requisiti non funzionali che vengono scoperti dal team di revisione.

- **Proprietario del servizio:** Gestisce le applicazioni e i servizi aziendali. Queste persone raccolgono dati di registrazione e utilizzo per questi servizi e applicazioni. Questi dati vengono utilizzati sia per identificare i problemi che per verificare le correzioni dopo la loro distribuzione.

## <a name="review-meeting"></a>Revisione della riunione

È consigliabile che il team di revisione soddisfi a intervalli regolari. È ad esempio possibile che il team soddisfi ogni mese e quindi segnali lo stato e le metriche ai dirigenti su base trimestrale.

Adatta i dettagli del processo e della riunione per soddisfare le tue esigenze specifiche. Come punto di partenza, è consigliabile includere le attività seguenti:

1. Il titolare dell'azienda e il fautore aziendale enumerano e determinano i requisiti non funzionali per ogni operazione aziendale, con l'input dei proprietari del reparto e della progettazione. Per le operazioni aziendali che sono state identificate in precedenza, rivedere e verificare la priorità. Per le nuove operazioni aziendali, assegnare una priorità nell'elenco esistente.

2. I proprietari dei servizi e della progettazione mappano lo stato corrente delle operazioni aziendali ai servizi locali e cloud corrispondenti. Il mapping è un elenco dei componenti di ogni servizio, orientati come albero delle dipendenze. I proprietari del servizio e della progettazione determinano quindi i percorsi critici nell'albero.

3. I responsabili tecnici e dei servizi verificano lo stato corrente di registrazione e monitoraggio operativi per i servizi elencati nel passaggio precedente. La registrazione e il monitoraggio affidabili sono fondamentali: identificano i componenti del servizio che contribuiscono a un errore per soddisfare i requisiti non funzionali. Se non sono presenti registrazioni e monitoraggi sufficienti, il team deve inserirle creando e implementando un piano.

4. Il team crea le metriche della scorecard per le nuove operazioni aziendali. La scorecard è costituita dall'elenco dei componenti costitutivi per ogni servizio identificato nel passaggio 2. È allineata con i requisiti non funzionali e include una misura del modo in cui ogni componente soddisfa i requisiti.

5. Per i componenti costitutivi che non soddisfano i requisiti non funzionali, il team progetta una soluzione di alto livello e assegna un proprietario di progettazione. A questo punto, il titolare dell'azienda e il fautore aziendale stabiliscono un budget per il lavoro di correzione, in base ai ricavi previsti per l'operazione aziendale.

6. Infine, il team esegue una revisione del lavoro di monitoraggio e aggiornamento in corso. Ogni metrica della scorecard per il lavoro in corso viene controllata rispetto ai criteri previsti. Per i componenti costitutivi che soddisfano i criteri di metrica, il proprietario del servizio presenta i dati di registrazione e monitoraggio per verificare che i criteri siano soddisfatti. Per i componenti costitutivi che non soddisfano i criteri di metrica, ogni proprietario della progettazione illustra i problemi che impediscono il soddisfacimento dei criteri e presenta le nuove progettazioni per la correzione.

## <a name="recommended-resources"></a>Risorse consigliate

- [Concetti fondamentali della qualità del software](https://docs.microsoft.com/azure/architecture/guide/pillars).
    Questa sezione della Guida all'architettura applicazione Azure descrive i cinque pilastri della qualità del software: scalabilità, disponibilità, resilienza, gestione e sicurezza.
- [Dieci principi di progettazione per le applicazioni Azure](https://docs.microsoft.com/azure/architecture/guide/design-principles).
    In questa sezione della Guida all'architettura applicazione Azure viene illustrato un set di principi di progettazione per rendere l'applicazione più scalabile, resiliente e gestibile.
- [Progettazione di applicazioni resilienti per Azure](https://docs.microsoft.com/azure/architecture/resiliency).
    Questa guida inizia con una definizione del termine _resilienza_ e dei concetti correlati. Descrive quindi un processo per ottenere la resilienza usando un approccio strutturato per la durata di un'applicazione, dalla progettazione e implementazione alla distribuzione e alle operazioni.
- [Modelli di progettazione cloud](https://docs.microsoft.com/azure/architecture/patterns).
    Questi modello di progettazione sono utili per i team di progettazione durante lo sviluppo di applicazioni in base ai pilastri della qualità del software.
