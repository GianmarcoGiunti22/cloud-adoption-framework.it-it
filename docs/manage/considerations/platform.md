---
title: Operazioni della piattaforma-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Operazioni della piattaforma-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: aab6dbe2ff8b1037a86317d00d717b4b22052c59
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558051"
---
# <a name="platform-operations-in-cloud-management"></a>Operazioni della piattaforma in gestione cloud

Una linea di base di gestione cloud che comprende [inventario e visibilità](./inventory.md), [conformità operativa](./operational-compliance.md)e [protezione e ripristino](./protect.md) può offrire un livello sufficiente di gestione del cloud per la maggior parte dei carichi di lavoro nel portfolio it. Tuttavia, raramente è sufficiente per supportare il portfolio completo. Questo articolo si basa sul passaggio successivo più comune di gestione del cloud e delle operazioni di portfolio.

Uno studio rapido degli asset nel portfolio IT evidenzierà i modelli nei carichi di lavoro supportati. All'interno di questi carichi di lavoro, saranno disponibili diverse piattaforme comuni. A seconda delle decisioni tecniche passate all'interno dell'azienda, queste piattaforme potrebbero essere molto diverse. Per alcune organizzazioni, ci sarà una dipendenza pesante da SQL Server, Oracle o altre piattaforme di dati Open Source. In altre organizzazioni, le comunanze potrebbero essere radicate nelle piattaforme di hosting per le macchine virtuali o i contenitori. Altri ancora possono avere una dipendenza comune da applicazioni o sistemi ERP (Enterprise Resource Planning) come SAP, Oracle o altri.

La comprensione di queste comunanze consente al team di gestione del cloud di specializzarsi in livelli più elevati di supporto per le piattaforme con priorità.

## <a name="establish-a-service-catalog"></a>Definire un catalogo di servizi

L'obiettivo delle operazioni della piattaforma è creare soluzioni affidabili e ripetibili che possono essere sfruttate da un team di adozione del cloud per offrire una piattaforma, che fornisce un livello di impegno aziendale più elevato. Questo impegno potrebbe ridurre la probabilità o la frequenza dei tempi di inattività, migliorando l'affidabilità. L'impegno può inoltre ridurre la quantità di perdita di dati o il tempo di recupero, in caso di errore di sistema. Questo impegno include spesso operazioni centralizzate in corso per supportare la piattaforma.

Poiché il team di gestione cloud stabilisce livelli più elevati di gestione operativa e specializzazione correlati a piattaforme specifiche, queste piattaforme vengono aggiunte a un catalogo di servizi in continua crescita. Il catalogo di servizi offre la distribuzione self-service di piattaforme in una configurazione specifica, che aderisce alle operazioni della piattaforma in corso. Durante la conversazione di allineamento aziendale, i team di gestione cloud e di strategia cloud possono proporre soluzioni di catalogo di servizi per migliorare l'affidabilità, il tempo di attività e il recupero degli impegni in un processo controllato e ripetibile.

Per riferimento, alcune organizzazioni faranno riferimento a un catalogo di servizi per fasi iniziali come "elenco approvato". La differenza principale è rappresentata dal fatto che un catalogo di servizi è associato a impegni operativi continui dal cloud Center of Excellence. Un "elenco approvato" è simile, in quanto fornisce un elenco di soluzioni già approvate che un team può usare nel cloud, ma in genere non è disponibile un vantaggio operativo associato alle applicazioni "approvate". Analogamente al dibattito tra IT centrale e CCoE, la differenza è una delle priorità. Un catalogo di servizi presuppone un buon scopo, ma fornisce Guardrails operative, di governance e sicurezza che accelerano l'innovazione. Un "elenco approvato" ostacola l'innovazione fino a quando non è possibile passare operazioni, conformità e controlli di sicurezza per una soluzione. Entrambe le soluzioni sono valide, ma richiedono una società per adottare decisioni di assegnazione di priorità minime per investire maggiormente nell'innovazione o nella conformità.

### <a name="building-the-service-catalog"></a>Compilazione del catalogo di servizi

La gestione del cloud non riesce raramente a consegnare un catalogo di servizi in un silo. Lo sviluppo appropriato del catalogo richiede una relazione tra l'IT centrale e il cloud Center of Excellence (CCoE). Questo approccio tende a essere più efficace quando un'organizzazione IT raggiunge un livello di maturità CCoE, ma potrebbe essere implementata prima.

Quando si compila il catalogo di servizi in un modello CCoE, il team della piattaforma cloud crea la piattaforma di stato desiderata. I team di governance e sicurezza del cloud convalidano la governance e la conformità all'interno della distribuzione. Il team di gestione cloud stabilisce le operazioni in corso per tale piattaforma. Il team di automazione del cloud impacchetta la piattaforma per la distribuzione scalabile e ripetibile.

Una volta creato il pacchetto, il team di gestione cloud può aggiungere il pacchetto al catalogo di servizi in continua crescita. A questo punto, il team di adozione del cloud può sfruttare tale pacchetto o altri nel catalogo durante la distribuzione. Una volta che la soluzione passa alla produzione, l'azienda ottiene i vantaggi aggiuntivi offerti dalla gestione operativa migliorata e dalle possibili rotture aziendali ridotte.

> [!NOTE]
> Per la creazione di un catalogo di servizi è necessario molto tempo e impegno da parte di più team. L'uso del catalogo di servizi o dell'elenco elementi consentiti come meccanismo di controllo rallenterà l'innovazione. Quando l'innovazione è una priorità, i cataloghi di servizi devono essere sviluppati in parallelo ad altre attività di adozione.

## <a name="defining-your-own-platform-operations"></a>Definizione di operazioni della piattaforma personalizzate

Gli strumenti di gestione e i processi possono migliorare le operazioni della piattaforma. Ma spesso non è sufficiente per ottenere lo stato desiderato di stabilità e affidabilità. La vera e propria piattaforma richiede una particolare attenzione ai pilastri di qualità dell'architettura. Quando una piattaforma giustifica un investimento più approfondito sulle operazioni, i cinque pilastri seguenti devono essere presi in considerazione prima che la piattaforma diventi parte di un catalogo di servizi:

1. Scalabilità: la capacità di un sistema di gestire un aumento del carico.
2. Disponibilità: la percentuale di tempo in cui un sistema è funzionante e funzionante.
3. Resilienza: la capacità di un sistema di correggere gli errori e continuare a funzionare.
4. Gestione: processi operativi che mantengono un sistema in esecuzione nell'ambiente di produzione.
5. Sicurezza: proteggere le applicazioni e i dati dalle minacce.

Il [Framework di architettura di Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) offre un approccio per la valutazione di carichi di lavoro specifici per l'adesione a questi pilastri, allo scopo di migliorare le operazioni complessive. Questi pilastri possono essere applicati sia alle operazioni della piattaforma che alle operazioni del carico di lavoro.

## <a name="getting-started-with-specific-platforms"></a>Introduzione a piattaforme specifiche

Per i clienti di Azure tipici, di seguito sono riportate piattaforme comuni, che possono facilmente giustificare un investimento in operazioni di piattaforma. I team di gestione cloud tendono a iniziare con questi requisiti quando compilano i requisiti delle operazioni della piattaforma o un catalogo di servizi completo.

### <a name="paas-data-operations"></a>Operazioni sui dati di PaaS

I dati sono spesso la prima piattaforma a garantire gli investimenti per le operazioni di piattaforma. Quando i dati sono ospitati in un ambiente di piattaforma distribuita come servizio (PaaS), gli stakeholder aziendali tendono a richiedere un RPO ridotto per ridurre al minimo la perdita di dati. A seconda della natura dell'applicazione, possono anche richiedere una riduzione dei RTO. In entrambi i casi, l'architettura che supporta le soluzioni dati basate su PaaS può facilmente supportare un livello superiore di supporto per la gestione.

Nella maggior parte degli scenari, il costo del miglioramento degli impegni di gestione è facile da giustificare, anche per le applicazioni che non sono cruciali. Questo miglioramento delle operazioni della piattaforma è così comune, che molti team di gestione cloud lo vedono più come una baseline avanzata, invece di considerarlo come un vero miglioramento delle operazioni della piattaforma.

### <a name="iaas-data-operations"></a>Operazioni sui dati di IaaS

Quando i dati sono ospitati in una soluzione di infrastruttura distribuita come servizio (IaaS) tradizionale, il lavoro necessario per migliorare RTO e RPO può essere notevolmente superiore. Tuttavia, il desiderio di ottenere migliori impegni di gestione da parte degli stakeholder aziendali è raramente influenzato dalla decisione di PaaS e IaaS. Se qualsiasi cosa, una conoscenza delle differenze fondamentali nell'architettura, può richiedere all'azienda di richiedere soluzioni PaaS o impegni che corrispondano a quanto disponibile nelle soluzioni PaaS. La modernizzazione di qualsiasi piattaforma di dati di IaaS deve essere considerata come il primo passaggio per le operazioni della piattaforma.

Quando la modernizzazione non è un'opzione, i team di gestione cloud in genere classificano in ordine di priorità le piattaforme dati basate su IaaS, come primo servizio necessario nel catalogo di servizi. Offrire all'azienda una scelta tra i server di dati autonomi e le soluzioni per i dati a disponibilità elevata e a livello di cluster rende più semplice la conversazione degli impegni aziendali. Una conoscenza di base dei miglioramenti operativi e dei costi maggiori, offrirà all'azienda la massima decisione per i processi aziendali e i carichi di lavoro di supporto.

### <a name="other-common-platform-operations"></a>Altre operazioni comuni della piattaforma

Oltre alle piattaforme dati, gli host di macchine virtuali tendono a essere una piattaforma comune per i miglioramenti delle operazioni. In genere, la piattaforma cloud e i team di gestione cloud investiranno i miglioramenti apportati agli host VMWare o alle soluzioni contenitore per migliorare la stabilità e l'affidabilità degli host, che supportano le VM, che alimentano i carichi di lavoro. Le operazioni appropriate in un host o in un contenitore possono migliorare la RPO/RTO di diversi carichi di lavoro. Questo approccio crea un miglioramento degli impegni aziendali, ma distribuisce l'investimento. Insieme, gli impegni migliorati e i costi ridotti rendono più semplice giustificare i miglioramenti apportati alla gestione del cloud e alle operazioni della piattaforma.

## <a name="next-steps"></a>Passaggi successivi

In parallelo con i miglioramenti apportati alle operazioni della piattaforma, i team di gestione cloud si concentrano anche sul miglioramento delle [operazioni del carico di lavoro](./workload.md) per il 20% o meno dei carichi di lavoro di produzione.

> [!div class="nextstepaction"]
> [Migliorare le operazioni del carico di lavoro](./workload.md)
