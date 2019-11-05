---
title: Operazioni della piattaforma-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Operazioni della piattaforma-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 6a2cf644a7c046dfb62f6049c2eae6b283e6552b
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565069"
---
# <a name="platform-operations-in-cloud-management"></a>Operazioni della piattaforma in gestione cloud

Una linea di base di gestione cloud che si estende su [inventario e visibilità](./inventory.md), [conformità operativa](./operational-compliance.md)e [protezione e ripristino](./protect.md) potrebbe offrire un livello sufficiente di gestione del cloud per la maggior parte dei carichi di lavoro nel portfolio it. Tuttavia, la linea di base è raramente sufficiente per supportare il portfolio completo. Questo articolo si basa sul passaggio successivo più comune di gestione del cloud e delle operazioni di portfolio.

Uno studio rapido degli asset nel portfolio IT evidenzia i modelli nei carichi di lavoro supportati. All'interno di questi carichi di lavoro, saranno disponibili diverse piattaforme comuni. A seconda delle decisioni tecniche passate all'interno dell'azienda, queste piattaforme possono variare notevolmente.

Per alcune organizzazioni, ci sarà una dipendenza forte da SQL Server, Oracle o altre piattaforme di dati Open Source. In altre organizzazioni, le comunanze potrebbero essere radicate nelle piattaforme di hosting per le macchine virtuali (VM) o i contenitori. Altri ancora possono avere una dipendenza comune dalle applicazioni o dai sistemi ERP (Enterprise Resource Planning), ad esempio SAP, Oracle o altri.

Grazie alla comprensione di queste comunanze, il team di gestione cloud può specializzarsi in livelli più elevati di supporto per le piattaforme con priorità.

## <a name="establish-a-service-catalog"></a>Definire un catalogo di servizi

L'obiettivo delle operazioni della piattaforma è creare soluzioni affidabili e ripetibili, che possono essere usate dal team di adozione del cloud per offrire una piattaforma che offra un livello di impegno aziendale più elevato. Questo impegno potrebbe ridurre la probabilità o la frequenza di tempi di inattività, migliorando l'affidabilità. In caso di errore di sistema, l'impegno potrebbe contribuire a ridurre la quantità di perdita di dati o il tempo di recupero. Un impegno di questo tipo include spesso operazioni centralizzate in corso per supportare la piattaforma.

Poiché il team di gestione cloud stabilisce livelli più elevati di gestione operativa e specializzazione correlati a piattaforme specifiche, queste piattaforme vengono aggiunte a un catalogo di servizi in continua crescita. Il catalogo di servizi offre la distribuzione self-service di piattaforme in una configurazione specifica, che aderisce alle operazioni della piattaforma in corso. Durante la conversazione di allineamento aziendale, i team di gestione cloud e di strategia cloud possono proporre soluzioni di catalogo di servizi per consentire all'azienda di migliorare l'affidabilità, il tempo di attività e gli impegni di recupero in un processo ripetibile e controllato.

Per riferimento, alcune organizzazioni fanno riferimento a un catalogo di servizi in anticipo come un _elenco approvato_. La differenza principale è rappresentata dal fatto che un catalogo di servizi è associato a impegni operativi continui dal cloud Center of Excellence (CCoE). Un elenco approvato è simile, in quanto fornisce un elenco di soluzioni preapprovate che un team può usare nel cloud. In genere, tuttavia, non esiste un vantaggio operativo associato alle applicazioni in un elenco approvato.

Analogamente al dibattito tra IT centrale e CCoE, la differenza è una delle priorità. Un catalogo di servizi presuppone un buon scopo, ma fornisce Guardrails operative, di governance e sicurezza che accelerano l'innovazione. Un elenco approvato ostacola l'innovazione fino a quando non è possibile passare operazioni, conformità e controlli di sicurezza per una soluzione. Entrambe le soluzioni sono valide, ma richiedono che l'azienda renda le decisioni di assegnazione di priorità minime per investire maggiormente nell'innovazione o nella conformità.

### <a name="build-the-service-catalog"></a>Compilare il catalogo di servizi

La gestione del cloud non riesce raramente a consegnare un catalogo di servizi in un silo. Lo sviluppo appropriato del catalogo richiede una relazione tra l'IT centrale e la CCoE. Questo approccio tende a essere più efficace quando un'organizzazione IT raggiunge un livello di maturità CCoE, ma potrebbe essere implementata prima.

Quando si compila il catalogo di servizi all'interno di un modello CCoE, il team della piattaforma cloud crea la piattaforma di stato desiderata. I team di governance e sicurezza del cloud convalidano la governance e la conformità all'interno della distribuzione. Il team di gestione cloud stabilisce le operazioni in corso per tale piattaforma. E il team di automazione del cloud impacchetta la piattaforma per la distribuzione scalabile e ripetibile.

Dopo che la piattaforma è stata assemblata, il team di gestione cloud può aggiungerlo al catalogo di servizi in continua crescita. A questo punto, il team di adozione del cloud può usare il pacchetto o altri utenti nel catalogo durante la distribuzione. Una volta che la soluzione passa alla produzione, l'azienda si rende conto dei vantaggi aggiuntivi della gestione operativa migliorata e delle eventuali rotture aziendali potenzialmente ridotte.

> [!NOTE]
> Per la creazione di un catalogo di servizi è necessario molto tempo e impegno da parte di più team. L'uso di un catalogo di servizi o di un elenco approvato come meccanismo di controllo rallenterà l'innovazione. Quando l'innovazione è una priorità, i cataloghi di servizi devono essere sviluppati in parallelo ad altre attività di adozione.

## <a name="define-your-own-platform-operations"></a>Definire le operazioni della piattaforma

Anche se gli strumenti e i processi di gestione possono contribuire a migliorare le operazioni della piattaforma, spesso non sufficiente per ottenere gli stati desiderati di stabilità e affidabilità. La vera e propria piattaforma richiede una particolare attenzione ai pilastri di qualità dell'architettura. Quando una piattaforma giustifica un investimento più approfondito sulle operazioni, i cinque pilastri seguenti devono essere presi in considerazione prima che la piattaforma diventi parte di un catalogo di servizi:

- **Scalabilità:** Capacità di un sistema di gestire un aumento del carico.
- **Disponibilità:** Percentuale di tempo in cui un sistema è funzionante e funzionante.
- **Resilienza:** Possibilità che un sistema recuperi gli errori e continui a funzionare.
- **Gestione:** Processi operativi che mantengono un sistema in esecuzione nell'ambiente di produzione.
- **Sicurezza:** Protezione delle applicazioni e dei dati dalle minacce.

Il [Framework di architettura di Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) offre un approccio per la valutazione di carichi di lavoro specifici per l'adesione a questi pilastri, allo scopo di migliorare le operazioni complessive. Questi pilastri possono essere applicati sia alle operazioni della piattaforma che alle operazioni del carico di lavoro.

## <a name="get-started-with-specific-platforms"></a>Introduzione a piattaforme specifiche

Le piattaforme illustrate nelle sezioni successive sono comuni ai clienti di Azure tipici e possono facilmente giustificare un investimento in operazioni della piattaforma. I team di gestione cloud tendono a iniziare con questi elementi quando compilano i requisiti delle operazioni della piattaforma o un catalogo di servizi completo.

### <a name="paas-data-operations"></a>Operazioni sui dati di PaaS

I dati sono spesso la prima piattaforma a garantire gli investimenti per le operazioni di piattaforma. Quando i dati sono ospitati in un ambiente di piattaforma distribuita come servizio (PaaS), gli stakeholder aziendali tendono a richiedere un obiettivo del punto di ripristino (RPO) ridotto per ridurre al minimo la perdita di dati. A seconda della natura dell'applicazione, potrebbe anche richiedere una riduzione dell'obiettivo del tempo di ripristino (RTO). In entrambi i casi, l'architettura che supporta le soluzioni per i dati basate su PaaS può facilmente supportare un livello maggiore di supporto per la gestione.

Nella maggior parte degli scenari, il costo del miglioramento degli impegni di gestione è facile da giustificare, anche per le applicazioni che non sono cruciali. Questo miglioramento delle operazioni della piattaforma è così comune che molti team di gestione cloud lo vedono più come una base avanzata, anziché come un vero miglioramento delle operazioni della piattaforma.

### <a name="iaas-data-operations"></a>Operazioni sui dati di IaaS

Quando i dati sono ospitati in una soluzione di infrastruttura distribuita come servizio (IaaS) tradizionale, il lavoro necessario per migliorare RPO e RTO può essere notevolmente superiore. Tuttavia, il desiderio di ottenere migliori impegni di gestione è influisce raramente sulla decisione di PaaS e IaaS. Se qualcosa, una conoscenza delle differenze fondamentali nell'architettura potrebbe richiedere all'azienda di richiedere soluzioni PaaS o impegni che corrispondano a quelli disponibili nelle soluzioni PaaS. La modernizzazione di qualsiasi piattaforma di dati di IaaS deve essere considerata come il primo passaggio per le operazioni della piattaforma.

Quando la modernizzazione non è un'opzione, i team di gestione cloud in genere classificano in ordine di priorità le piattaforme dati basate su IaaS come primo servizio necessario nel catalogo di servizi. Offrire all'azienda una scelta tra i server di dati autonomi e le soluzioni per i dati in cluster e a disponibilità elevata rende molto più semplice la conversazione degli impegni aziendali. Una conoscenza di base dei miglioramenti operativi e dei costi maggiori offrirà il supporto per l'azienda per prendere la decisione migliore per i processi aziendali e i carichi di lavoro di supporto.

### <a name="other-common-platform-operations"></a>Altre operazioni comuni della piattaforma

Oltre alle piattaforme dati, gli host di macchine virtuali tendono a essere una piattaforma comune per i miglioramenti delle operazioni. In genere, la piattaforma cloud e i team di gestione cloud investono in miglioramenti per gli host VMware o le soluzioni contenitore. Tali investimenti possono migliorare la stabilità e l'affidabilità degli host, che supportano le VM, che a loro volta potenziano i carichi di lavoro. Le operazioni appropriate in un host o in un contenitore possono migliorare RPO o RTO di diversi carichi di lavoro. Questo approccio crea un miglioramento degli impegni aziendali, ma distribuisce l'investimento. Gli impegni migliorati e i costi ridotti si uniscono per semplificare la giustificazione dei miglioramenti apportati alla gestione del cloud e alle operazioni della piattaforma.

## <a name="next-steps"></a>Passaggi successivi

In parallelo con i miglioramenti apportati alle operazioni della piattaforma, i team di gestione cloud si concentrano anche sul miglioramento delle [operazioni del carico](./workload.md) di lavoro per il 20% o meno dei carichi di lavoro in

> [!div class="nextstepaction"]
> [Migliorare le operazioni del carico di lavoro](./workload.md)
