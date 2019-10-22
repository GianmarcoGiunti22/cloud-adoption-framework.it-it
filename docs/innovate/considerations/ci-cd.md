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
ms.openlocfilehash: 0c6f55ec7f82756658fc67fb9412d7d83d503b97
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683235"
---
# <a name="empower-adoption"></a>Adozione potenziata

Il test finale dell'innovazione è la reazione dei clienti alla tua invenzione. L'ipotesi è stata rivelata vera? I clienti usano la soluzione? Scalabilità per soddisfare le esigenze della percentuale di utenti desiderata? In particolare, continuano a tornare indietro? Nessuna di queste domande può essere richiesta fino alla distribuzione della soluzione MVP. In questo articolo si escentrerà sulla disciplina dell'adozione.

## <a name="reducing-friction-to-adoption"></a>Riduzione dell'attrito all'adozione

Ci sono alcuni punti chiave di attrito da adottare che possono essere ridotti al minimo tramite una combinazione di tecnologia e processi. Per i lettori che hanno familiarità con i processi di integrazione continua/distribuzione continua o DevOps, il codice seguente risulterà molto simile. L'obiettivo di questo articolo è stabilire un punto di partenza per i team di adozione del cloud, che fornirà i cicli di innovazione e feedback. A lungo termine, questo punto di partenza potrebbe crescere in approcci CI/CD o DevOps più affidabili Man mano che i prodotti e i team maturano.

Un descritto in [misurazione dell'impatto sul cliente](./measure.md), la convalida positiva di qualsiasi ipotesi richiede iterazione e determinazione. Si avranno più errori rispetto a WINS durante qualsiasi ciclo di innovazione. Si tratta di un comportamento previsto. Tuttavia, in caso di necessità del cliente, ipotesi e allineamento della soluzione su larga scala, il mondo cambia rapidamente. Questo articolo ha lo scopo di ridurre al minimo i [picchi tecnici](./build.md#reduce-complexity-and-delay-technical-spikes) che potrebbero rallentare l'innovazione, ma assicurarsi che siano presenti alcune procedure consigliate solide. Questa operazione consentirà al team di progettare un successo futuro, ma di garantire le attuali esigenze dei clienti.

## <a name="empowering-adoption---maturity-model"></a>Potenziamento del modello di adozione-maturità

L'obiettivo principale della [metodologia di innovazione](./index.md) è quello di creare relazioni con i clienti e accelerare i cicli di feedback, che comporteranno innovazioni di mercato.
Nell'immagine e nelle sezioni di contenuto seguenti vengono descritte le implementazioni iniziali che supporteranno la metodologia.

![Adozione potenziamento-modello maturità](../../_images/innovate/empower-adoption-maturity.png)

- [Soluzione condivisa](#shared-solution): definire un repository centralizzato per tutti gli aspetti della soluzione.
- [Cicli di feedback](#feedback-loops): assicurarsi che i cicli di feedback possano essere gestiti in modo coerente tramite le iterazioni.
- [Integrazione continua](#continuous-integration): compilare e consolidare regolarmente la soluzione.
- [Test affidabili](#reliable-testing): convalida la qualità della soluzione e le modifiche previste per garantire le misure.
- [Distribuzione della soluzione](#solution-deployment): distribuzione di una soluzione per consentire al team di condividere rapidamente le modifiche con i clienti.
- [Misurazione integrata](#integrated-measurements): aggiungere metriche di apprendimento al ciclo di feedback per un'analisi chiara da parte del team completo.

Riducendo al minimo i picchi tecnici, si supponga che la maturità sia inizialmente limitata a tutti questi principi. Tuttavia, pianificare in anticipo allineando gli strumenti e i processi che possono essere ridimensionati in base alle ipotesi con granularità più fine. In Azure, la combinazione di [GitHub](https://guides.github.com) e [Azure DevOps](https://docs.microsoft.com/azure/devops) consente ai piccoli team di iniziare a usare un po' di attrito. Cresce quindi fino a migliaia di sviluppatori che collaborano a soluzioni di scalabilità che testano centinaia di clienti. Nella parte restante di questo articolo verrà illustrato il piano di grandi dimensioni, avviando un piccolo approccio per consentire l'adozione di tutti questi principi.

## <a name="shared-solution"></a>Soluzione condivisa

Un descritto in [misurazione dell'impatto sul cliente](./measure.md), la convalida positiva di qualsiasi ipotesi richiede iterazione e determinazione. Si avranno più errori rispetto a WINS durante qualsiasi ciclo di innovazione. Si tratta di un comportamento previsto. Tuttavia, in caso di necessità del cliente, ipotesi e allineamento della soluzione su larga scala, il mondo cambia rapidamente.

Quando si ridimensiona l'innovazione, non esiste un strumento più prezioso rispetto a una codebase condivisa per la soluzione. Sfortunatamente, non esiste alcun modo per prevedere quale iterazione o quale MVP produrrà la combinazione vincente. Questo è il motivo per cui non è mai troppo presto creare una codebase o un repository condiviso. Si tratta di un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes) che non dovrebbe mai essere ritardato. Quando il team esegue l'iterazione in varie soluzioni MVP, un repository condiviso consentirà di semplificare la collaborazione e lo sviluppo accelerato. Quando le modifiche apportate alla soluzione generano un impatto negativo sulle metriche di apprendimento, il controllo della versione può consentire un rollback alla versione precedente e più efficace della soluzione.

Lo strumento più comune per la gestione dei repository di codice è [GitHub](https://guides.github.com) , che consente la creazione di un repository di codice condiviso con pochi clic. Inoltre, è possibile usare la funzionalità [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) di Azure DevOps per creare un repository [git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) o [Team Foundation](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="feedback-loops"></a>Cicli di feedback

La chiave per la creazione di relazioni con i clienti durante i cicli di innovazione consiste nel rendere il cliente una parte della soluzione. Questa operazione viene eseguita con una lunghezza delle armi attraverso la [misurazione dell'effetto del cliente](./measure.md). Più attentamente, richiede conversazioni e test diretti con il cliente. Entrambi comportano il feedback che deve essere gestito.

Ogni punto di feedback è una potenziale soluzione per le esigenze dei clienti. Ancora più importante, ogni bit di feedback direttamente da un cliente è un'opportunità per migliorare la collaborazione. Se il feedback lo trasforma in una soluzione MVP, celebrarlo con il cliente. Anche se il feedback non è praticabile, è semplicemente trasparente con la decisione di declassificare i commenti e suggerimenti, illustra un [mindset di crescita](./learn.md#growth-mindset) e un focus sull' [apprendimento continuo](./learn.md#continuous-learning).

[Azure DevOps](https://docs.microsoft.com/azure/devops) include modi per [richiedere, fornire e gestire il feedback](https://docs.microsoft.com/azure/devops/project/feedback). Ognuno di questi strumenti centralizza il feedback, in modo che il team possa intervenire e creare report sui commenti e suggerimenti, fornendo un ciclo di feedback trasparente.

## <a name="continuous-integration"></a>Integrazione continua

Poiché la scalabilità delle adozioni e un'ipotesi si avvicinano alla vera innovazione su larga scala, il numero di ipotesi più piccole da testare aumenterà rapidamente. Per i cicli di feedback accurati e i processi di adozione senza problemi, è importante che ognuno di tali ipotesi sia integrato e supporti l'ipotesi primaria alla base dell'innovazione. Sfortunatamente, è anche necessario passare rapidamente a innovare e crescere, in modo da richiedere a più sviluppatori di testare varianti dell'ipotesi di base. Per le attività di sviluppo in fase successiva, potrebbe essere necessario che più team di sviluppatori creino ogni compilazione verso una soluzione condivisa. L'integrazione continua è il primo passo avanti verso la gestione delle varie parti mobili.

Nell'integrazione continua, le modifiche al codice vengono spesso unite nel ramo principale. I processi di compilazione e test automatici assicurano che il codice nel ramo principale sia sempre di qualità di produzione. Ciò assicura che gli sviluppatori collaborino per sviluppare soluzioni condivise che forniscono cicli di feedback accurati e affidabili.

Azure DevOps e [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) fornisce funzionalità di integrazione continua con pochi clic, per GitHub o diversi altri repository.
Per altre informazioni, vedere l'articolo relativo all' [integrazione continua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-integration) o all'esecuzione nel [Lab pratico](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration) . Sono disponibili anche architetture di soluzioni per accelerare la creazione di [pipeline ci/CD usando Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="reliable-testing"></a>Test affidabili

I difetti in qualsiasi soluzione possono creare falsi positivi o falsi negativi. Gli errori imprevisti possono facilmente compromettere l'interpretazione delle metriche di adozione da parte degli utenti. Può anche causare commenti negativi da parte dei clienti che non rappresentano correttamente il test dell'ipotesi.

Durante le prime iterazioni di una soluzione MVP, i difetti sono previsti, i primi utenti possono anche trovarli. Nelle prime versioni, il test di accettazione probabilmente sarà inesistente. Tuttavia, un aspetto della compilazione con empatia è la convalida della necessità e dell'ipotesi. Entrambi possono essere completati tramite unit test a livello di codice e test di accettazione manuali prima della distribuzione. Insieme, questi forniranno un certo mezzo di affidabilità nei test. A lungo termine, una serie ben definita di test di compilazione, unità e accettazione dovrebbe essere automatizzata per garantire metriche affidabili correlate a ottimizzazioni di granularità più fine per l'ipotesi e la soluzione risultante.

[Azure test plans](https://docs.microsoft.com/azure/devops/test/track-test-status?view=azure-devops) offre strumenti per sviluppare e utilizzare piani di test durante l'esecuzione di test manuali o automatizzati.

## <a name="solution-deployment"></a>Distribuzione della soluzione

Forse l'aspetto più significativo dell'adozione è la possibilità di controllare il rilascio di una soluzione ai clienti. Fornire una pipeline self-service o automatizzata per rilasciare una soluzione ai clienti accelera il ciclo di feedback. Consentendo ai clienti di interagire rapidamente con le modifiche apportate alla soluzione, invita il cliente nel processo. Consente inoltre di testare più rapidamente le ipotesi, riducendo i presupposti e la potenziale rielaborazione.

Sono disponibili diversi approcci alla distribuzione della soluzione. di seguito sono illustrati i tre approcci più comuni:

- L'approccio più avanzato, **distribuzione continua**, distribuisce automaticamente le modifiche al codice in produzione. Per i team maturi che testano le ipotesi mature, la distribuzione continua può essere estremamente preziosa.
- Durante le fasi iniziali dello sviluppo, il **recapito continuo** potrebbe essere più appropriato. Nel recapito continuo tutte le modifiche al codice vengono distribuite automaticamente in un ambiente di tipo produzione. Gli sviluppatori, i decisori aziendali e altri utenti del team possono utilizzare questo ambiente per verificare che il lavoro sia pronto per la produzione. Può anche essere usato per testare un'ipotesi con i clienti, senza influire sulle attività di business in corso.
- La **distribuzione manuale** è l'approccio meno avanzato alla gestione delle versioni. Come suggerisce il nome, un utente del team distribuirà manualmente le modifiche al codice più recenti. Questo approccio è soggetto a errori, non affidabile e considerato un antipattern da parte dei tecnici più esperti.

Durante la prima iterazione di una soluzione MVP, la distribuzione manuale è un approccio comune, nonostante la descrizione descritta in precedenza. Quando la soluzione è estremamente fluida e i suggerimenti dei clienti sono sconosciuti, esiste un rischio significativo per reimpostare l'intera soluzione (o anche l'ipotesi principale). Regola generale per la distribuzione manuale: nessuna prova del cliente, nessuna automazione della distribuzione. L'investimento anticipato può causare perdita di tempo. Ancora più importante, può creare dipendenze dalla pipeline di rilascio che renderebbe il team più resistente a un primo pivot. Dopo le prime iterazioni o quando il feedback dei clienti suggerisce un potenziale successo, è consigliabile adottare rapidamente un modello più avanzato di distribuzione.

In qualsiasi fase della convalida dell'ipotesi, Azure DevOps e [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) offre funzionalità di distribuzione continua e distribuzione continua con pochi clic. Per altre informazioni, vedere la pagina relativa al [recapito continuo](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-delivery) o eseguire l' [esercitazione pratica](https://www.azuredevopslabs.com/labs/azuredevops/continuousdeployment) . Le architetture della soluzione possono anche accelerare la creazione di [pipeline ci/CD usando Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="integrated-measurements"></a>Misurazioni integrate

Quando si [misurano gli effetti dei clienti](./measure.md), è importante comprendere in che modo i clienti reagiscono alle modifiche apportate alla soluzione. Questi dati, chiamati telemetria, forniscono informazioni dettagliate sulle azioni eseguite da un uso (o coorte di utenti) quando si usa la soluzione. Da questi dati è facile ottenere una convalida quantitativa dell'ipotesi. Queste metriche possono quindi essere usate per modificare la soluzione e generare ipotesi con granularità più fine. Queste modifiche più sottili consentono di maturare la soluzione iniziale nelle iterazioni successive, ottenendo in definitiva la ripetizione dell'adozione su larga scala.

In Azure [monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) fornisce gli strumenti e l'interfaccia per raccogliere ed esaminare i dati dalle esperienze dei clienti. Tali osservazioni e informazioni possono essere usate per affinare il backlog usando [Azure Boards](https://docs.microsoft.com/azure/devops/boards).

## <a name="next-steps"></a>Passaggi successivi

Con la comprensione degli strumenti e dei processi necessari per consentire l'adozione, è possibile esaminare una disciplina di innovazione più avanzata e [interagire con i dispositivi](./devices.md). Che consente di ridurre le barriere tra esperienze fisiche e digitali, rendendo la soluzione ancora più semplice da adottare.

> [!div class="nextstepaction"]
> [Interagire con i dispositivi](./devices.md)
