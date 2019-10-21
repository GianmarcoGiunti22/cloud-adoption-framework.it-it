---
title: Introduzione alla gestione operativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla gestione operativa con Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 23b9064b91744d5464f89ed4edf64c8d656514a5
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558103"
---
# <a name="establishing-operational-management-practices-in-the-cloud"></a>Definizione di procedure per la gestione operativa nel cloud

L'adozione del cloud è un fattore importante per l'incremento del valore aziendale. È tuttavia possibile ottenere risultati concreti in termini di valore aziendale solo se si definiscono interventi regolari e continui per garantire il corretto funzionamento degli asset tecnologici distribuiti nel cloud. Questa sezione di Cloud Adoption Framework illustra al lettore i diversi passaggi per la gestione operativa nel cloud.

## <a name="actionable-best-practices"></a>Procedure consigliate attuabili

Le moderne soluzioni di Operations Management creano una visualizzazione multicloud delle operazioni. Gli asset gestiti tramite le seguenti procedure consigliate possono risiedere nel cloud, in un data center esistente o anche in un provider di cloud in competizione. Il framework include attualmente due procedure consigliate di riferimento per facilitare la realizzazione di un sistema maturo per la gestione delle operazioni nel cloud:

- [Gestione del server di Azure](./azure-server-management/index.md): Guida introduttiva per incorporare gli strumenti e i servizi nativi del cloud necessari per gestire le operazioni.
- [Monitoraggio ibrido](./monitor/index.md): molti clienti hanno già effettuato un investimento sostanziale in System Center Operations Manager. Questa guida al monitoraggio ibrido è destinata a tali clienti e consente di analizzare e confrontare gli strumenti di creazione report cloud nativi con gli strumenti inclusi in Operations Manager. Grazie a questo confronto sarà più semplice decidere quali strumenti usare per la gestione operativa.

## <a name="cloud-operations"></a>Operazioni cloud

Entrambe queste procedure consigliate si basano su una metodologia di stato futura per la gestione delle operazioni.

![Gestire la metodologia del Framework di adozione del cloud](../_images/manage/caf-manage.png)

**Allineamento aziendale:** Nella metodologia di gestione tutti i carichi di lavoro sono classificati in base alla criticità e al valore aziendale. Tale classificazione può quindi essere misurata attraverso un'analisi di impatto, che calcola il valore perso associato al degrado delle prestazioni o alle interruzioni dell'attività. Grazie a questo impatto tangibile sui ricavi, i team delle operazioni cloud possono collaborare con l'azienda alla definizione di un impegno in grado di bilanciare costi e prestazioni.

**Discipline per le operazioni cloud:** Una volta allineata l'azienda, è molto più semplice tenere traccia e creare report sulle discipline appropriate delle operazioni cloud per ogni carico di lavoro. Le decisioni adottate per ogni regola possono quindi essere convertite in termini di impegno facilmente comprensibili per l'azienda. Grazie a questo approccio collaborativo gli stakeholder aziendali collaborano attivamente alla ricerca del giusto equilibrio tra costi e prestazioni.

- **Inventario e visibilità:** La gestione delle operazioni richiede almeno un mezzo di inventario delle risorse e la creazione della visibilità nello stato di esecuzione di ogni asset.
- **Conformità operativa:** La gestione regolare di configurazione, ridimensionamento, costi e prestazioni delle risorse è fondamentale per mantenere le aspettative in termini di prestazioni.
- **Proteggi e Ripristina:** Riducendo al minimo le interruzioni operative e velocizzando il ripristino, è possibile evitare perdite di prestazioni e conseguenze dei ricavi. Il rilevamento e il ripristino sono aspetti essenziali di questa regola.
- **Operazioni della piattaforma:** Tutti gli ambienti IT contengono un set di piattaforme di uso comune. Tali piattaforme possono includere archivi dati, come SQL Server o HDInsight. Altre piattaforme comuni possono includere soluzioni basate su contenitori, come Kubernetes o il servizio Azure Kubernetes. Indipendentemente dalle piattaforme, la maturità delle operazioni è incentrata sulla personalizzazione delle operazioni in base a come tali piattaforme comuni vengono distribuite, configurate e utilizzate dai carichi di lavoro.
- **Operazioni del carico di lavoro:** Al massimo livello di maturità operativa, i team operativi cloud sono in grado di ottimizzare le operazioni per i carichi di lavoro cruciali per il successo dell'azienda. Per i carichi di lavoro a criticità elevata, i dati disponibili possono essere utili per automatizzare la correzione, il ridimensionamento o la protezione dei carichi di lavoro in base al relativo utilizzo.

Altre informazioni aggiuntive, come il [Framework di revisione della progettazione (nome in codice: principi di progettazione cloud)](https://docs.microsoft.com/azure/architecture/reliability) , possono contribuire a prendere decisioni di architettura dettagliate per ogni carico di lavoro, all'interno delle discipline precedenti.

Questa sezione di Cloud Adoption Framework si baserà su ognuno di questi argomenti per sviluppare operazioni cloud mature all'interno dell'organizzazione.
