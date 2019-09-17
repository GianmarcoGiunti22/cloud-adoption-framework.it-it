---
title: Stabilire una verifica dell'idoneità operativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Linee guida per i concetti fondamentali dell'operatività
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/20/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 04afedc133d001405c5042b309a45c9b41f3268e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027782"
---
# <a name="establish-an-operational-fitness-review"></a>Stabilire una verifica dell'idoneità operativa

Quando l'azienda inizia a usare i carichi di lavoro in Azure, il passaggio successivo consiste nel definire un processo per la *Verifica dell'idoneità operativa*. Questo processo enumera, implementa e esamina in modo iterativo i *requisiti non funzionali* per questi carichi di lavoro. I requisiti non funzionali sono correlati al comportamento operativo previsto del servizio.

Esistono cinque categorie essenziali di requisiti non funzionali, detti [pilastri della qualità del software](https://docs.microsoft.com/azure/architecture/guide/pillars):

- Scalabilità
- Disponibilità
- Resilienza, tra cui la continuità aziendale e il ripristino di emergenza
- Gestione
- Security

Un processo per la verifica dell'idoneità operativa garantisce che i carichi di lavoro cruciali soddisfino le aspettative dell'azienda rispetto ai pilastri qualitativi.

È necessario che l'azienda crei un processo per la revisione dell'idoneità operativa per comprendere completamente i problemi derivanti dall'esecuzione di carichi di lavoro in un ambiente di produzione, determinare come correggere tali problemi e risolverli. Questo articolo descrive un processo di alto livello per la revisione di idoneità operativa che l'azienda può usare per raggiungere questo obiettivo.

## <a name="operational-fitness-at-microsoft"></a>Idoneità operativa a Microsoft

Fin dall'inizio, lo sviluppo della piattaforma Azure è stato un progetto continuo di molti team in Microsoft. È difficile garantire la qualità e la coerenza per un progetto di tali dimensioni e complessità. Un processo affidabile è necessario per enumerare e implementare i requisiti di base non funzionali a intervalli regolari.

I processi che Microsoft segue costituiscono la base per i processi descritti in questo articolo.

## <a name="understand-the-problem"></a>Informazioni sul problema

Come illustrato in [Introduzione](../getting-started/migrate.md), il primo passaggio della trasformazione digitale di un'azienda consiste nell'identificare i problemi aziendali da risolvere mediante l'adozione di Azure. Il passaggio successivo consiste nel determinare una soluzione di alto livello al problema, ad esempio la migrazione di un carico di lavoro nel cloud o l'adattamento di un servizio locale esistente per includere le funzionalità cloud. Infine, la soluzione viene progettata e implementata.

Durante questo processo, lo stato attivo è spesso relativo alle funzionalità del servizio: il set di requisiti _funzionali_ che si desidera venga eseguito dal servizio. Il servizio di recapito di un prodotto, ad esempio, richiede funzionalità per determinare le posizioni di origine e di destinazione del prodotto, il rilevamento del prodotto durante il recapito, le notifiche dei clienti e altro ancora.

I requisiti non _funzionali_ , al contrario, si riferiscono a proprietà quali la [disponibilità](https://docs.microsoft.com/azure/architecture/checklist/availability), la [resilienza](https://docs.microsoft.com/azure/architecture/resiliency)e la [scalabilità](https://docs.microsoft.com/azure/architecture/checklist/scalability)del servizio. Queste proprietà differiscono dai requisiti funzionali perché non influiscono direttamente sulla funzione finale di una particolare funzionalità nel servizio. Tuttavia, i requisiti non funzionali sono correlati alle prestazioni e alla continuità del servizio.

È possibile specificare alcuni requisiti non funzionali in termini di contratto di servizio (SLA). Per la continuità del servizio, ad esempio, un requisito di disponibilità per il servizio può essere espresso come percentuale: "Disponibile il 99,99% del tempo". Altri requisiti non funzionali potrebbero risultare più difficili da definire e possono cambiare in base alle esigenze di produzione. Un servizio orientato ai consumatori, ad esempio, potrebbe affrontare i requisiti di velocità effettiva inaspettati dopo un picco di popolarità.

> [!NOTE]
> I requisiti per la resilienza vengono esaminati in modo più approfondito nella [progettazione di applicazioni Azure affidabili](https://docs.microsoft.com/azure/architecture/reliability#define-requirements). In questo articolo sono incluse spiegazioni di concetti quali il punto di ripristino (RPO), l'obiettivo del tempo di ripristino (RTO), il contratto di servizio e altri.

## <a name="process-for-operational-fitness-review"></a>Processo per la verifica dell'idoneità operativa

La chiave per mantenere le prestazioni e la continuità dei servizi di un'azienda consiste nell'implementazione di un processo per la verifica dell'idoneità operativa.

![Panoramica del processo di analisi di idoneità operativa](../_images/manage/ofr-flow.png)

A livello generale, il processo prevede due fasi. Nella *fase dei prerequisiti*i requisiti vengono stabiliti e mappati ai servizi di supporto. Questa fase si verifica raramente: probabilmente ogni anno o quando vengono introdotte nuove operazioni. L'output della fase dei prerequisiti viene usato nella *fase del flusso*. La fase di flusso si verifica più spesso: è consigliabile usare ogni mese.

### <a name="prerequisites-phase"></a>Fase dei prerequisiti

I passaggi in questa fase acquisiscono i requisiti per l'esecuzione di una revisione regolare dei servizi importanti.

1. **Identificare le operazioni aziendali cruciali**. Identificare le operazioni aziendali cruciali dell'organizzazione. Le operazioni aziendali sono indipendenti da qualsiasi funzionalità dei servizi di supporto. In altre parole, le operazioni di business rappresentano le attività effettive che devono essere eseguite dall'azienda e supportate da un set di servizi IT.

    Il termine *mission-critical* (o *business critical*) riflette un grave effetto sull'azienda se l'operazione è ostacolata. Un rivenditore online, ad esempio, potrebbe avere un'operazione aziendale, ad esempio "consentire a un cliente di aggiungere un elemento a un carrello acquisti" o "elaborare un pagamento con carta di credito". Se una di queste operazioni ha esito negativo, un cliente non può completare la transazione e l'azienda non riesce a realizzare le vendite.

1. **Abbinare le operazioni ai servizi**. Eseguire il mapping delle operazioni aziendali critiche ai servizi che le supportano. Nell'esempio del carrello della spesa possono essere necessari diversi servizi: un servizio di gestione delle scorte di inventario, un servizio di carrello acquisti e altro. Per elaborare un pagamento con carta di credito, un servizio di pagamento locale può interagire con un servizio di elaborazione dei pagamenti di terze parti.

1. **Analizzare le dipendenze dei servizi**. Per la maggior parte delle operazioni aziendali è necessaria un'orchestrazione tra più servizi di supporto È importante comprendere le dipendenze tra i servizi e il flusso di transazioni cruciali attraverso questi servizi.

    Prendere in considerazione anche le dipendenze tra i servizi locali e i servizi di Azure. Nell'esempio relativo al carrello della spesa, il servizio di gestione delle scorte di inventario potrebbe essere ospitato in locale e inserire i dati immessi dai dipendenti da un magazzino fisico. Tuttavia, potrebbe archiviare i dati fuori sede in un servizio di Azure, ad esempio [archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction)o un database, ad esempio [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction).

Un output da queste attività è un set di *metriche di scorecard* per le operazioni del servizio. Le metriche sono suddivise in categorie in termini di criteri non funzionali, ad esempio disponibilità, scalabilità e ripristino di emergenza. Le metriche della scorecard esprimono i criteri operativi che il servizio dovrebbe soddisfare. Queste metriche possono essere espresse a qualsiasi livello di granularità appropriato per l'operazione del servizio.

La scorecard deve essere espressa in termini semplici per promuovere scambi di opinioni significativi tra i titolari dell'azienda e il personale tecnico. Una metrica della scorecard per la scalabilità, ad esempio, può essere espressa in verde per soddisfare i criteri definiti, il giallo in modo da non soddisfare i criteri definiti, ma implementare attivamente una correzione pianificata o rosso per non soddisfare i criteri definiti senza alcun piano oppure azione.

È importante sottolineare che queste metriche devono riflettere direttamente le esigenze aziendali.

### <a name="service-review-phase"></a>Servizio-fase di Revisione

La fase di revisione del servizio è il nucleo della verifica di idoneità operativa. Questa procedura include i passaggi seguenti:

1. **Misurare le metriche del servizio**. Usare le metriche scorecard per monitorare i servizi, in modo da garantire che i servizi soddisfino le esigenze aziendali. In altre parole, il monitoraggio del servizio è essenziale. Se non è possibile monitorare un set di servizi per quanto riguarda i requisiti non funzionali, prendere in considerazione le metriche della scorecard corrispondenti in rosso. In questo caso, il primo passaggio per la correzione consiste nell'implementare il monitoraggio del servizio appropriato. Se, ad esempio, l'azienda prevede che un servizio operi con una disponibilità del 99,99%, ma non sono disponibili dati di telemetria di produzione per misurare la disponibilità, si supponga di non soddisfare i requisiti.

2. **Pianificare gli interventi correttivi**. Per ogni operazione del servizio per la quale le metriche scendono al di sotto di una soglia accettabile, determinare il costo della correzione del servizio per portare l'operazione a un livello accettabile. Se il costo per il monitoraggio e l'aggiornamento del servizio è superiore alla generazione dei ricavi previsti per il servizio, è opportuno prendere in considerazione i costi intangibili, ad esempio l'esperienza del cliente. Se, ad esempio, i clienti hanno difficoltà a inserire un ordine corretto usando il servizio, potrebbero invece scegliere un concorrente.

3. **Implementare gli interventi correttivi**. Una volta che i proprietari dell'azienda e la progettazione concordano su un piano, implementarla. Segnala lo stato dell'implementazione ogni volta che le metriche della scorecard di revisione.

Questo processo è iterativo e idealmente l'azienda dispone di un team dedicato. Questo team deve essere aggiornato regolarmente per esaminare i progetti correttivi esistenti, avviare la revisione fondamentale dei nuovi carichi di lavoro e tenere traccia della scorecard complessiva dell'azienda. Il team deve inoltre disporre dell'autorità per tenere conto dei team di monitoraggio e aggiornamento in caso di mancata pianificazione o di mancato rispetto della metrica.

## <a name="structure-of-the-review-team"></a>Struttura del team di Revisione

Il team responsabile della revisione dell'idoneità operativa è costituito dai ruoli seguenti:

- **Proprietario dell'azienda**: Fornisce informazioni sull'azienda per identificare e classificare in ordine di priorità ogni operazione aziendale cruciale. Questo ruolo, inoltre, è in grado di soppesare il costo delle correzioni in relazione all'impatto aziendale e guida la decisione finale in merito agli interventi correttivi.

- **Business Advocate**: Suddivide le operazioni aziendali in parti discrete ed esegue il mapping di tali parti ai servizi e all'infrastruttura, sia in locale che nel cloud. Il ruolo richiede una profonda conoscenza della tecnologia associata a ogni operazione aziendale.

- **Proprietario della progettazione**: Implementa i servizi associati all'operazione di business. Questi utenti possono partecipare alla progettazione, all'implementazione e alla distribuzione di qualsiasi soluzione per problemi di requisiti non funzionali che vengono scoperti dal team di revisione.

- **Responsabile dei servizi**. Gestisce le applicazioni e i servizi aziendali. Queste persone raccolgono dati di registrazione e utilizzo per questi servizi e applicazioni. Questi dati vengono utilizzati sia per identificare i problemi che per verificare le correzioni dopo la loro distribuzione.

## <a name="review-meeting"></a>Revisione della riunione

È consigliabile che il team di revisione soddisfi a intervalli regolari. Il team, ad esempio, potrebbe essere in grado di soddisfare mensilmente e quindi segnalare lo stato e le metriche ai dirigenti su base trimestrale.

Adatta i dettagli del processo e della riunione per soddisfare le tue esigenze specifiche. Come punto di partenza, è consigliabile includere le attività seguenti:

1. Il titolare dell'azienda e il fautore aziendale enumerano e determinano i requisiti non funzionali per ogni operazione aziendale, con l'input dei proprietari del reparto e della progettazione. Per le operazioni aziendali che sono state identificate in precedenza, la priorità viene esaminata e verificata. Per le nuove operazioni aziendali, viene assegnata una priorità nell'elenco esistente.

2. I proprietari dei servizi e della progettazione mappano lo stato corrente delle operazioni aziendali ai servizi locali e cloud corrispondenti. Il mapping è un elenco dei componenti di ogni servizio, orientati come albero delle dipendenze. Dopo che l'elenco e l'albero delle dipendenze sono stati generati, vengono determinati i percorsi critici nell'albero.

3. I responsabili tecnici e dei servizi verificano lo stato corrente di registrazione e monitoraggio operativi per i servizi elencati nel passaggio precedente. La registrazione e il monitoraggio affidabili sono fondamentali: identificano i componenti del servizio che contribuiscono a un errore per soddisfare i requisiti non funzionali. Se non sono presenti registrazioni e monitoraggi sufficienti, è necessario creare e implementare un piano per inserirli.

4. Le metriche della scorecard vengono create per le nuove operazioni aziendali. La scorecard è costituita dall'elenco dei componenti costitutivi per ogni servizio identificato nel passaggio 2. È allineata con i requisiti non funzionali e include una misura del modo in cui ogni componente soddisfa i requisiti.

5. Per i componenti costitutivi che non soddisfano i requisiti non funzionali, viene progettata una soluzione di alto livello e viene assegnato un proprietario tecnico. A questo punto, il titolare dell'azienda e il fautore aziendale stabiliscono un budget per il lavoro di correzione, in base ai ricavi previsti per l'operazione aziendale.

6. Infine, viene effettuata una verifica degli interventi correttivi in corso. Ogni metrica della scorecard per il lavoro in corso viene controllata rispetto ai criteri previsti. Per i componenti costitutivi che soddisfano i criteri di metrica, il proprietario del servizio presenta i dati di registrazione e monitoraggio per verificare che i criteri siano soddisfatti. Per i componenti costitutivi che non soddisfano i criteri di metrica, ogni proprietario della progettazione illustra i problemi che impediscono il soddisfacimento dei criteri e presenta le nuove progettazioni per la correzione.

## <a name="recommended-resources"></a>Risorse consigliate

- [Concetti fondamentali della qualità del software](https://docs.microsoft.com/azure/architecture/guide/pillars).
    Questa sezione della Guida all'architettura applicazione Azure descrive i cinque pilastri della qualità del software: scalabilità, disponibilità, resilienza, gestione e sicurezza.
- [Dieci principi di progettazione per le applicazioni Azure](https://docs.microsoft.com/azure/architecture/guide/design-principles).
    In questa sezione della Guida all'architettura applicazione Azure viene illustrato un set di principi di progettazione per rendere l'applicazione più scalabile, resiliente e gestibile.
- [Progettazione di applicazioni resilienti per Azure](https://docs.microsoft.com/azure/architecture/resiliency).
    Questa guida inizia con una definizione del termine _resilienza_ e dei concetti correlati. Descrive quindi un processo per ottenere la resilienza usando un approccio strutturato per la durata di un'applicazione, dalla progettazione e implementazione alla distribuzione e alle operazioni.
- [Modelli di progettazione cloud](https://docs.microsoft.com/azure/architecture/patterns).
    Questi modello di progettazione sono utili per i team di progettazione durante lo sviluppo di applicazioni in base ai pilastri della qualità del software.
