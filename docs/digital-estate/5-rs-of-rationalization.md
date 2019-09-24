---
title: Razionalizzazione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esaminare le opzioni disponibili per la razionalizzazione di un digital estate.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/16/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: 35709a6208de54f43cdb51aadb1e32f34a0ba844
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223862"
---
# <a name="cloud-rationalization"></a>Razionalizzazione del cloud

La razionalizzazione del cloud è il processo di valutazione degli asset per determinare il modo migliore per eseguire la migrazione o modernizzare ogni asset nel cloud. Per ulteriori informazioni sul processo di razionalizzazione, vedere [che cos'è un Digital estate?](./index.md).

## <a name="rationalization-context"></a>Contesto di razionalizzazione

Le "cinque RS di razionalizzazione" elencate in questo articolo sono un ottimo modo per etichettare un potenziale stato futuro per qualsiasi carico di lavoro considerato come un candidato al cloud. Tuttavia, questo processo di assegnazione di etichette deve essere inserito nel contesto corretto prima di provare a razionalizzare un ambiente. Esaminare i seguenti miti per fornire il contesto:

- **Mito: È facile prendere decisioni di razionalizzazione nelle prime fasi del processo.** Una razionalizzazione accurata richiede una conoscenza approfondita del carico di lavoro e degli asset associati (app, VM e dati). Soprattutto, le decisioni di razionalizzazione accurate prendono tempo. Si consiglia di usare un [processo](./rationalize.md#incremental-rationalization)di razionalizzazione incrementale.

- **Mito: L'adozione del cloud deve attendere la razionalizzazione di tutti i carichi di lavoro.** La razionalizzazione di un intero portfolio IT o anche di un singolo Data Center può ritardare la realizzazione del valore aziendale per mesi o anche anni. Quando possibile, è consigliabile evitare una razionalizzazione completa. Usare invece la [potenza di 10 approccio per la pianificazione del rilascio](./rationalize.md#release-planning) , in modo da prendere decisioni sagge sui 10 carichi di lavoro più prossimi disponibili per l'adozione del cloud.

- **Mito: La giustificazione aziendale deve attendere la razionalizzazione di tutti i carichi di lavoro.** Per sviluppare una motivazione aziendale per un lavoro di adozione del cloud, è necessario prendere in considerazione alcuni presupposti di base a livello di portfolio. Quando le motivazioni sono allineate all'innovazione, si supponga di riarchitettura. Quando le motivazioni sono allineate alla migrazione, si supponga di riospitare. Questi presupposti possono accelerare il processo di giustificazione aziendale. I presupposti vengono quindi contestati e i budget vengono perfezionati durante la fase di valutazione dei cicli di adozione di ogni carico di lavoro.

Per acquisire familiarità con il processo a lungo termine, è ora possibile esaminare le seguenti cinque RS di razionalizzazione. Durante lo sviluppo del piano di adozione del cloud, scegliere l'opzione più adatta alle proprie motivazioni, risultati aziendali e ambiente di stato attuale. L'obiettivo della razionalizzazione delle proprietà digitali è quello di impostare una linea di base, non di razionalizzare tutti i carichi di lavoro.

## <a name="the-five-rs-of-rationalization"></a>Cinque RS di razionalizzazione

I cinque criteri di razionalizzazione elencati di seguito descrivono le opzioni più comuni per la razionalizzazione.

## <a name="rehost"></a>Rehosting

Nota anche come migrazione in modalità Lift-and-Shift, un impegno rehost sposta un asset di stato corrente nel provider di servizi cloud scelto, con una modifica minima dell'architettura complessiva.

I driver comuni possono includere:

- Riduzione delle spese di capitale
- Liberare spazio per il Data Center
- Ottenere un ritorno rapido sugli investimenti nel cloud

Fattori di analisi quantitativa:

- Dimensioni della macchina virtuale (CPU, memoria, archiviazione)
- Dipendenze (traffico di rete)
- Compatibilità degli asset

Fattori di analisi qualitativa:

- Tolleranza alle modifiche
- Priorità aziendali
- Eventi aziendali critici
- Dipendenze dei processi

## <a name="refactor"></a>Refactoring

Le opzioni di piattaforma distribuita come servizio (PaaS) possono ridurre i costi operativi associati a molte applicazioni. È consigliabile effettuare leggermente il refactoring di un'applicazione per adattarla a un modello basato su PaaS.

"Refactoring" si riferisce anche al processo di sviluppo di applicazioni di refactoring del codice per consentire a un'applicazione di offrire nuove opportunità di business.

I driver comuni possono includere:

- Aggiornamenti più veloci e più brevi
- Portabilità del codice
- Maggiore efficienza del cloud (risorse, velocità, costi, operazioni gestite)

Fattori di analisi quantitativa:

- Dimensioni degli asset dell'applicazione (CPU, memoria, archiviazione)
- Dipendenze (traffico di rete)
- Traffico utente (visualizzazioni pagina, tempo su una pagina, tempo di caricamento)
- Piattaforma di sviluppo (linguaggi, piattaforma dati, servizi di livello intermedio)
- Database (CPU, memoria, archiviazione, versione)

Fattori di analisi qualitativa:

- Investimenti aziendali continui
- Aumento delle opzioni/sequenze temporali
- Dipendenze dei processi aziendali

## <a name="rearchitect"></a>Riprogettazione

Alcune applicazioni obsolete non sono compatibili con i provider di servizi cloud a causa delle decisioni di architettura effettuate durante la compilazione dell'applicazione. In questi casi, potrebbe essere necessario riprogettare l'applicazione prima della trasformazione.

In altri casi, le applicazioni che sono compatibili con il cloud, ma non native del cloud, possono creare efficienza dei costi e efficienza operativa riprogettando la soluzione in un'applicazione nativa del cloud.

I driver comuni possono includere:

- Scalabilità e flessibilità dell'applicazione
- Adozione più semplice di nuove funzionalità del cloud
- Miscela di stack di tecnologie

Fattori di analisi quantitativa:

- Dimensioni degli asset dell'applicazione (CPU, memoria, archiviazione)
- Dipendenze (traffico di rete)
- Traffico utente (visualizzazioni pagina, tempo su una pagina, tempo di caricamento)
- Piattaforma di sviluppo (linguaggi, piattaforme di dati, servizi di livello intermedio)
- Database (CPU, memoria, archiviazione, versione)

Fattori di analisi qualitativa:

- Investimenti aziendali in crescita
- Costi operativi
- Potenziali cicli di feedback e investimenti DevOps.

## <a name="rebuild"></a>Ricompila

In alcuni scenari, il Delta che deve essere superato per portare avanti un'applicazione può essere troppo grande per giustificare ulteriori investimenti. Questo vale soprattutto per le applicazioni che in precedenza soddisfacevano le esigenze di un'azienda, ma che ora non sono supportate o non sono allineate ai processi aziendali correnti. In questo caso, viene creata una nuova codebase per allinearla a un approccio nativo per il [cloud](https://azure.microsoft.com/overview/cloudnative) .

I driver comuni possono includere:

- Accelerazione dell'innovazione
- Compilazione delle app più veloce
- Riduzione dei costi operativi

Fattori di analisi quantitativa:

- Dimensioni degli asset dell'applicazione (CPU, memoria, archiviazione)
- Dipendenze (traffico di rete)
- Traffico utente (visualizzazioni pagina, tempo su una pagina, tempo di caricamento)
- Piattaforma di sviluppo (linguaggi, piattaforme di dati, servizi di livello intermedio)
- Database (CPU, memoria, archiviazione, versione)

Fattori di analisi qualitativa:

- Rifiuto della soddisfazione degli utenti finali
- Processi aziendali limitati per funzionalità
- Potenziali guadagni in termini di costi, esperienza o ricavi

## <a name="replace"></a>Sostituisci

Le soluzioni vengono in genere implementate usando la tecnologia e l'approccio più adatti al momento. Talvolta le applicazioni SaaS (Software as a Service) possono fornire tutte le funzionalità necessarie per l'applicazione ospitata. In questi scenari, è possibile pianificare un carico di lavoro per la sostituzione futura, in modo da rimuoverlo dal lavoro di trasformazione.

I driver comuni possono includere:

- Standardizzazione delle procedure consigliate per il settore
- Accelerazione dell'adozione di approcci basati sui processi aziendali
- Riallocazione di investimenti di sviluppo in applicazioni che creano vantaggi o differenziazione competitiva

Fattori di analisi quantitativa:

- Riduzione dei costi operativi generali
- Dimensioni della macchina virtuale (CPU, memoria, archiviazione)
- Dipendenze (traffico di rete)
- Asset da ritirare
- Database (CPU, memoria, archiviazione, versione)

Fattori di analisi qualitativa:

- Analisi costi-benefici dell'architettura attuale rispetto alla soluzione SaaS
- Mapping dei processi aziendali
- Schemi di dati
- Processi personalizzati o automatizzati

## <a name="next-steps"></a>Passaggi successivi

Collettivamente, è possibile applicare queste cinque RS di razionalizzazione a una proprietà digitale per semplificare le decisioni di razionalizzazione relative allo stato futuro di ogni applicazione.

> [!div class="nextstepaction"]
> [Informazioni sul digital estate](./index.md)
