---
title: 'Innovazione nel cloud: adozione di potenziamenti'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione nel cloud-potenziamento dell'adozione
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: e4c09cb67872cec6fca8ab395f7ab88e2e0f2064
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752096"
---
# <a name="empower-adoption"></a>Supportare l'adozione

Il test finale dell'innovazione è la reazione dei clienti alla tua invenzione. L'ipotesi è stata rivelata vera? I clienti usano la soluzione? Scalabilità per soddisfare le esigenze della percentuale di utenti desiderata? In particolare, continuano a tornare indietro? Nessuna di queste domande può essere richiesta fino a quando non è stata distribuita la soluzione di prodotto (MVP) minima. In questo articolo si concentrerà sulla disciplina di potenziamento dell'adozione.

## <a name="reduce-friction-that-affects-adoption"></a>Riduzione dell'attrito che influiscono sull'adozione

Ci sono alcuni punti chiave di attrito da adottare che possono essere ridotti al minimo tramite una combinazione di tecnologia e processi. Per i lettori che conoscono i processi di integrazione continua (CI) e di distribuzione continua (CD) o DevOps, saranno noti gli elementi seguenti. Questo articolo costituisce un punto di partenza per i team di adozione del cloud che alimentano i cicli di innovazione e di feedback. In futuro, questo punto di partenza potrebbe favorire approcci più affidabili di integrazione continua/recapito continuo o DevOps, in base alla maturità dei prodotti e dei team.

Come descritto in [misurare l'impatto del cliente](./measure.md), la convalida positiva di qualsiasi ipotesi richiede iterazione e determinazione. Si verificheranno molti più errori rispetto a WINS durante qualsiasi ciclo di innovazione. Si tratta di un comportamento previsto. Tuttavia, in caso di necessità, ipotesi e allineamento della soluzione a livello di cliente, il mondo cambia rapidamente. Questo articolo ha lo scopo di ridurre al minimo i [picchi tecnici](./build.md#reduce-complexity-and-delay-technical-spikes) che rallentano l'innovazione, assicurando comunque di mantenere alcune solide procedure consigliate. Questa operazione consentirà al team di progettare per un futuro successo, garantendo al tempo stesso le esigenze attuali dei clienti.

## <a name="empowering-adoption-the-maturity-model"></a>Potenziamento dell'adozione: modello di maturità

L'obiettivo principale della [metodologia di innovazione](./index.md) è quello di creare relazioni con i clienti e accelerare i cicli di feedback, che comporteranno innovazioni di mercato. Nell'immagine e nelle sezioni seguenti vengono descritte le implementazioni iniziali che supportano questa metodologia.

![Adozione di Empower: modello di maturità](../../_images/innovate/empower-adoption-maturity.png)

- [Soluzione condivisa](#shared-solution): definire un repository centralizzato per tutti gli aspetti della soluzione.
- [Cicli di feedback](#feedback-loops): assicurarsi che i cicli di feedback possano essere gestiti in modo coerente tramite le iterazioni.
- [Integrazione continua](#continuous-integration): compilare e consolidare regolarmente la soluzione.
- [Test affidabili](#reliable-testing): consente di convalidare la qualità della soluzione e le modifiche previste per garantire l'affidabilità delle metriche di test.
- [Distribuzione della soluzione](#solution-deployment): distribuire le soluzioni in modo che il team possa condividere rapidamente le modifiche con i clienti.
- [Misurazione integrata](#integrated-measurements): aggiungere metriche di apprendimento al ciclo di feedback per un'analisi chiara da parte del team completo.

Per ridurre al minimo i picchi tecnici, si supponga che la maturità sia inizialmente limitata a tutti questi principi. Ma certamente pianificare in anticipo allineando gli strumenti e i processi che possono essere ridimensionati in base alle ipotesi con granularità più fine. In Azure, [GitHub](https://guides.github.com) e [Azure DevOps](https://docs.microsoft.com/azure/devops) consentono ai piccoli team di iniziare a usare un po' di attrito. Questi team possono crescere fino a includere migliaia di sviluppatori che collaborano su soluzioni di scalabilità e testano centinaia di ipotesi dei clienti. Nella parte restante di questo articolo viene illustrato il piano di grandi dimensioni/avvio per consentire l'adozione di tutti questi principi.

## <a name="shared-solution"></a>Soluzione condivisa

Come descritto in [misurare l'impatto del cliente](./measure.md), la convalida positiva di qualsiasi ipotesi richiede iterazione e determinazione. Si verificheranno molti più errori rispetto a WINS durante qualsiasi ciclo di innovazione. Si tratta di un comportamento previsto. Tuttavia, in caso di necessità, ipotesi e allineamento della soluzione a livello di cliente, il mondo cambia rapidamente.

Quando si esegue il ridimensionamento dell'innovazione, non è disponibile uno strumento più prezioso rispetto a una codebase condivisa per la soluzione. Sfortunatamente, non esiste un modo affidabile per prevedere quale iterazione o quale MVP produrrà la combinazione vincente. Questo è il motivo per cui non è mai troppo presto creare una codebase o un repository condiviso. Si tratta di un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes) che non dovrebbe mai essere ritardato. Quando il team esegue l'iterazione attraverso diverse soluzioni MVP, un repository condiviso consente una collaborazione semplice e uno sviluppo accelerato. Quando le modifiche apportate alla soluzione trascinano le metriche di apprendimento, il controllo della versione consente di eseguire il rollback a una versione precedente e più efficace della soluzione.

Lo strumento più usato per la gestione dei repository di codice è [GitHub](https://guides.github.com), che consente di creare un repository di codice condiviso con pochi clic. Inoltre, è possibile usare la funzionalità [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) di Azure DevOps per creare un repository [git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) o [Team Foundation](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="feedback-loops"></a>Cicli di feedback

Fare in modo che il cliente faccia parte della soluzione sia la chiave per la creazione di relazioni con i clienti durante i cicli di innovazione. Questa operazione viene eseguita, in parte, [misurando l'effetto del cliente](./measure.md). Richiede conversazioni e test diretti con il cliente. Entrambi generano commenti e suggerimenti che devono essere gestiti in modo efficace.

Ogni punto di feedback è una potenziale soluzione per le esigenze dei clienti. Ancora più importante, ogni bit di feedback diretto dei clienti rappresenta un'opportunità per migliorare la collaborazione. Se il feedback lo trasforma in una soluzione MVP, festeggiare con il cliente. Anche se alcuni commenti e suggerimenti non sono interoperabili, la semplice trasparenza con la decisione di declassificare i commenti e suggerimenti illustra una [tendenza alla crescita](./learn.md#growth-mindset) e l'attenzione all' [apprendimento continuo](./learn.md#continuous-learning).

[Azure DevOps](https://docs.microsoft.com/azure/devops) include modi per [richiedere, fornire e gestire il feedback](https://docs.microsoft.com/azure/devops/project/feedback). Ognuno di questi strumenti centralizza il feedback, in modo che il team possa intervenire e fornire un completamento in servizio di un ciclo di feedback trasparente.

## <a name="continuous-integration"></a>Integrazione continua

Con la scalabilità delle adozioni e un'ipotesi più vicina alla vera innovazione su larga scala, il numero di ipotesi più piccole da testare tende a crescere rapidamente. Per i cicli di feedback accurati e i processi di adozione senza problemi, è importante che ognuno di tali ipotesi sia integrato e supporti l'ipotesi primaria alla base dell'innovazione. Ciò significa che è anche necessario passare rapidamente a innovare e crescere, che richiede più sviluppatori per testare le varianti dell'ipotesi di base. Per le attività di sviluppo in fase successiva, potrebbe essere necessario più team di sviluppatori, ciascuno dei quali si basa su una soluzione condivisa. L'integrazione continua è il primo passo avanti verso la gestione di tutte le parti mobili.

Nell'integrazione continua, le modifiche al codice vengono spesso unite nel ramo principale. I processi di compilazione e test automatici assicurano che il codice nel ramo principale sia sempre di qualità di produzione. Ciò assicura che gli sviluppatori collaborino per sviluppare soluzioni condivise che forniscono cicli di feedback accurati e affidabili.

Azure DevOps e [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) offrono funzionalità di integrazione continua con pochi clic in GitHub o in diversi altri repository.
Altre informazioni sull' [integrazione continua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-integration)o per altre informazioni, vedere l' [esercitazione pratica](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration). Sono inoltre disponibili architetture di soluzioni per accelerare la creazione di [pipeline ci/CD tramite Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="reliable-testing"></a>Test affidabili

I difetti in qualsiasi soluzione possono creare falsi positivi o falsi negativi. Gli errori imprevisti possono facilmente compromettere l'interpretazione delle metriche di adozione da parte degli utenti. Possono anche generare feedback negativi da clienti che non rappresentano in modo accurato il test dell'ipotesi.

Durante le prime iterazioni di una soluzione MVP, sono previsti dei difetti; i primi ad adottare potrebbero anche trovarli. Nelle prime versioni, il test di accettazione è in genere inesistente. Tuttavia, un aspetto della compilazione con empatia riguarda la convalida della necessità e dell'ipotesi. Entrambi possono essere completati tramite unit test a livello di codice e test di accettazione manuali prima della distribuzione. Insieme, questi forniscono un mezzo di affidabilità nei test. È necessario cercare di automatizzare una serie ben definita di test di compilazione, unità e accettazione. In questo modo, le metriche affidabili sono correlate a modifiche più granulari all'ipotesi e alla soluzione risultante.

La funzionalità [Azure test plans](https://docs.microsoft.com/azure/devops/test/track-test-status?view=azure-devops) offre strumenti per sviluppare e gestire i piani di test durante l'esecuzione di test manuali o automatizzati.

## <a name="solution-deployment"></a>Distribuzione della soluzione

Forse l'aspetto più significativo dell'adozione dell'adozione riguarda la possibilità di controllare il rilascio di una soluzione ai clienti. Fornendo una pipeline self-service o automatizzata per rilasciare una soluzione ai clienti, si accelererà il ciclo di feedback. Consentendo ai clienti di interagire rapidamente con le modifiche apportate alla soluzione, è possibile invitarle nel processo. Questo approccio attiva anche il test più rapido delle ipotesi, riducendo così i presupposti e la potenziale rielaborazione.

Sono disponibili diversi metodi per la distribuzione della soluzione. Di seguito sono rappresentate le tre più comuni:

- La **distribuzione continua** è il metodo più avanzato, perché distribuisce automaticamente le modifiche al codice nell'ambiente di produzione. Per i team maturi che testano le ipotesi mature, la distribuzione continua può essere estremamente preziosa.
- Durante le fasi iniziali dello sviluppo, il **recapito continuo** potrebbe essere più appropriato. Nel recapito continuo tutte le modifiche al codice vengono distribuite automaticamente in un ambiente di tipo produzione. Gli sviluppatori, i decision maker aziendali e altri utenti del team possono utilizzare questo ambiente per verificare che il lavoro sia pronto per la produzione. È anche possibile usare questo metodo per testare un'ipotesi con i clienti senza influire sulle attività di business in corso.
- La **distribuzione manuale** è l'approccio meno sofisticato per la gestione delle versioni. Come suggerisce il nome, un utente del team distribuisce manualmente le modifiche apportate al codice più recenti. Questo approccio è soggetto a errori, non affidabile e considerato un antipattern da parte dei tecnici più esperti.

Durante la prima iterazione di una soluzione MVP, la distribuzione manuale è comune, nonostante la valutazione precedente. Quando la soluzione è estremamente fluida e i suggerimenti dei clienti sono sconosciuti, c'è un rischio significativo nella reimpostazione dell'intera soluzione (o anche dell'ipotesi principale). Ecco la regola generale per la distribuzione manuale: nessuna prova del cliente, nessuna automazione della distribuzione.

L'investimento anticipato può causare perdita di tempo. Ancora più importante, è possibile creare dipendenze dalla pipeline di rilascio che rendono il team più resistente a un primo pivot. Dopo le prime iterazioni o quando il feedback dei clienti suggerisce un potenziale successo, è consigliabile adottare rapidamente un modello più avanzato di distribuzione.

In qualsiasi fase della convalida dell'ipotesi, Azure DevOps e [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) offrono funzionalità di distribuzione continua e distribuzione continua. Scopri di più sul [recapito continuo](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-delivery)o guarda l' [esercitazione pratica](https://www.azuredevopslabs.com/labs/azuredevops/continuousdeployment). L'architettura della soluzione può anche accelerare la creazione di [pipeline ci/CD tramite Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="integrated-measurements"></a>Misurazioni integrate

Quando si [misurano gli effetti del cliente](./measure.md), è importante comprendere in che modo i clienti reagiscono alle modifiche apportate alla soluzione. Questi dati, noti come dati di *telemetria*, forniscono informazioni approfondite sulle azioni eseguite da un utente (o coorte di utenti) quando si lavora con la soluzione. Da questi dati è facile ottenere una convalida quantitativa dell'ipotesi. Queste metriche possono quindi essere usate per modificare la soluzione e generare ipotesi con granularità più fine. Queste modifiche più sottili consentono di maturare la soluzione iniziale nelle iterazioni successive, ottenendo in definitiva la ripetizione dell'adozione su larga scala.

In Azure [monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) fornisce gli strumenti e l'interfaccia per raccogliere ed esaminare i dati dalle esperienze dei clienti. È possibile applicare tali osservazioni e informazioni dettagliate per perfezionare il backlog usando [Azure Boards](https://docs.microsoft.com/azure/devops/boards).

## <a name="next-steps"></a>Passaggi successivi

Una volta acquisite informazioni sugli strumenti e sui processi necessari per consentire l'adozione, è possibile esaminare una disciplina di innovazione più avanzata: [interagire con i dispositivi](./devices.md). Questa disciplina può aiutare a ridurre le barriere tra esperienze fisiche e digitali, rendendo la soluzione ancora più semplice da adottare.

> [!div class="nextstepaction"]
> [Interagire con i dispositivi](./devices.md)
