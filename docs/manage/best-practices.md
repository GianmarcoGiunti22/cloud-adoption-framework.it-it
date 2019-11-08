---
title: Introduzione alla gestione operativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comprendere la gestione operativa all'interno del Framework di adozione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 38dfd1951982e23cce2108ccc62877dae06d3cbe
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751630"
---
# <a name="establish-operational-management-practices-in-the-cloud"></a>Definire le procedure operative di gestione nel cloud

L'adozione del cloud è un fattore importante per l'incremento del valore aziendale. È tuttavia possibile ottenere risultati concreti in termini di valore aziendale solo se si definiscono interventi regolari e continui per garantire il corretto funzionamento degli asset tecnologici distribuiti nel cloud. Questa sezione del Framework di adozione cloud consente di eseguire in modo semplificato le varie transizioni nella gestione operativa del cloud.

## <a name="actionable-best-practices"></a>Procedure consigliate attuabili

Le moderne soluzioni di Operations Management creano una visualizzazione multicloud delle operazioni. Gli asset gestiti tramite le seguenti procedure consigliate possono risiedere nel cloud, in un data center esistente o anche in un provider di cloud in competizione. Attualmente, il Framework include due riferimenti alle procedure consigliate per guidare la maturità di gestione delle operazioni nel cloud:

- [Gestione del server di Azure](./azure-server-management/index.md): Guida al caricamento per incorporare gli strumenti e i servizi nativi del cloud necessari per gestire le operazioni.
- [Monitoraggio ibrido](./monitor/index.md): molti clienti hanno già effettuato un investimento sostanziale in System Center Operations Manager. Per questi clienti, questa guida al monitoraggio ibrido può aiutarli a confrontare e contrastare gli strumenti di creazione di report nativi del cloud con strumenti Operations Manager. Questo confronto rende più semplice decidere quali strumenti usare per la gestione operativa.

## <a name="cloud-operations"></a>Operazioni cloud

Entrambe queste procedure consigliate si basano su una metodologia di stato futuro per la gestione delle operazioni, come illustrato nel diagramma seguente:

![Gestire la metodologia del Framework di adozione del cloud](../_images/manage/caf-manage.png)

**Allineamento aziendale:** Nella metodologia di gestione tutti i carichi di lavoro sono classificati in base alla criticità e al valore aziendale. Tale classificazione può quindi essere misurata attraverso un'analisi di impatto, che calcola il valore perso associato al degrado delle prestazioni o alle interruzioni dell'attività. Grazie a questo impatto tangibile sui ricavi, i team delle operazioni cloud possono collaborare con l'azienda alla definizione di un impegno in grado di bilanciare costi e prestazioni.

**Discipline per le operazioni cloud:** Una volta allineata l'azienda, è molto più semplice tenere traccia e creare report sulle discipline appropriate delle operazioni cloud per ogni carico di lavoro. Prendere decisioni in ogni disciplina può quindi essere convertita in termini di impegno che possono essere facilmente comprensibili per l'azienda. Grazie a questo approccio collaborativo gli stakeholder aziendali collaborano attivamente alla ricerca del giusto equilibrio tra costi e prestazioni.

- **Inventario e visibilità:** La gestione delle operazioni richiede almeno un mezzo di inventario delle risorse e la creazione della visibilità nello stato di esecuzione di ogni asset.
- **Conformità operativa:** Una gestione regolare di configurazione, ridimensionamento, costo e prestazioni delle risorse è fondamentale per mantenere le aspettative in termini di prestazioni.
- **Proteggi e Ripristina:** Ridurre al minimo le interruzioni operative e velocizzare il ripristino aiutare l'azienda a evitare perdite di prestazioni e effetti negativi sui ricavi. Il rilevamento e il ripristino sono aspetti essenziali di questa regola.
- **Operazioni della piattaforma:** Tutti gli ambienti IT contengono un set di piattaforme di uso comune. Queste piattaforme possono includere archivi dati, ad esempio SQL Server o Azure HDInsight. Altre piattaforme comuni possono includere soluzioni di contenitori come Azure Kubernetes Service (AKS). Indipendentemente dalla piattaforma, la maturità delle operazioni della piattaforma è incentrata sulla personalizzazione delle operazioni in base alla modalità di distribuzione, configurazione e utilizzo delle piattaforme comuni da parte dei carichi di lavoro.
- **Operazioni del carico di lavoro:** Al massimo livello di maturità operativa, i team operativi cloud sono in grado di ottimizzare le operazioni per i carichi di lavoro cruciali per il successo dell'azienda. Per questi carichi di lavoro ad alta criticità, i dati disponibili possono aiutare ad automatizzare la correzione, il dimensionamento o la protezione dei carichi di lavoro in base al relativo utilizzo.

Indicazioni aggiuntive, ad esempio il [Framework di revisione della progettazione (nome in codice: principi di progettazione del cloud)](https://docs.microsoft.com/azure/architecture/framework/resiliency/overview), consentono di prendere decisioni di architettura dettagliate su ogni carico di lavoro, all'interno delle discipline descritte in precedenza.

Questa sezione del Framework di adozione del cloud verrà compilata su ognuno degli argomenti precedenti per promuovere le operazioni cloud mature all'interno dell'organizzazione.
