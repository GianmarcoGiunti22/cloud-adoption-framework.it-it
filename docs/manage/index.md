---
title: Introduzione alla gestione operativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla gestione operativa con Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: manage
ms.openlocfilehash: 3abc103e09a11af4cb822dde985b96c56bca6242
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025737"
---
# <a name="establishing-operational-management-practices-in-the-cloud"></a>Definizione di procedure per la gestione operativa nel cloud

L'adozione del cloud è un fattore importante per l'incremento del valore aziendale. È tuttavia possibile ottenere risultati reali in termini di valore aziendale solo se si definiscono interventi regolari e continui per garantire il corretto funzionamento degli asset tecnologici distribuiti nel cloud. Questa sezione di Cloud Adoption Framework illustra al lettore i diversi passaggi per la gestione operativa nel cloud.

## <a name="actionable-best-practices"></a>Procedure consigliate attuabili

Con le moderne soluzioni di gestione operativa le operazioni sono rappresentate in una visualizzazione multicloud. Gli asset gestiti in conformità alle procedure consigliate seguenti possono risiedere nel cloud, in un data center esistente o persino in un provider di servizi cloud concorrente. Il framework include attualmente due procedure consigliate di riferimento per facilitare la realizzazione di un sistema maturo per la gestione delle operazioni nel cloud:

* [Gestione del server di Azure](./azure-server-management/index.md): guida introduttiva all'integrazione degli strumenti e dei servizi cloud nativi necessari per la gestione delle operazioni.
* [Monitoraggio ibrido](./monitor/index.md): molti clienti hanno già sostenuto un notevole investimento per l'acquisto di System Center Operations Manager. Questa guida al monitoraggio ibrido è destinata a tali clienti e consente di analizzare e confrontare gli strumenti di creazione report cloud nativi con gli strumenti inclusi in Operations Manager. Grazie a questo confronto sarà più semplice decidere quali strumenti usare per la gestione operativa.

## <a name="cloud-operations"></a>Operazioni cloud

Entrambe queste procedure consigliate consentono di formulare una metodologia ufficiale futura per la gestione delle operazioni.

![Metodologia di gestione di Cloud Adoption Framework](../_images/manage/caf-manage.png)

**Allineamento del business:** nella metodologia di gestione tutti i carichi di lavoro vengono classificati in base alla criticità e al valore aziendale. Tale classificazione può quindi essere misurata attraverso un'analisi di impatto, che calcola il valore perso associato al degrado delle prestazioni o alle interruzioni dell'attività. Grazie a questo impatto tangibile sui ricavi, i team delle operazioni cloud possono collaborare con l'azienda alla definizione di un impegno in grado di bilanciare costi e prestazioni.

**Regole per le operazioni cloud**: una volta allineato il business, risulta molto più agevole tracciare e documentare le regole corrette per le operazioni cloud relative a ogni carico di lavoro. Le decisioni adottate per ogni regola possono quindi essere convertite in termini di impegno facilmente comprensibili per l'azienda. Grazie a questo approccio collaborativo gli stakeholder aziendali collaborano attivamente alla ricerca del giusto equilibrio tra costi e prestazioni.

* Inventario e visibilità: ai fini della gestione delle operazioni è necessario disporre almeno di strumenti per inventariare gli asset e ottenere visibilità sullo stato di esecuzione di ogni asset.
* Conformità operativa: la gestione periodica di configurazione, ridimensionamento, costi e prestazioni degli asset costituisce un fattore chiave per garantire prestazioni all'altezza delle aspettative.
* Protezione e ripristino: la riduzione delle interruzioni operative e l'accelerazione del ripristino consentono di evitare cali delle prestazioni e ripercussioni sui ricavi. Il rilevamento e il ripristino sono aspetti essenziali di questa regola.
* Operazioni della piattaforma: tutti gli ambienti IT comprendono un set di piattaforme comunemente usate. Tali piattaforme possono includere archivi dati, come SQL Server o HDInsights. Altre piattaforme comuni possono includere soluzioni basate su contenitori, come Kubernetes o il servizio Azure Kubernetes. Indipendentemente dalle piattaforme, la maturità delle operazioni è incentrata sulla personalizzazione delle operazioni in base a come tali piattaforme comuni vengono distribuite, configurate e utilizzate dai carichi di lavoro.
* Operazioni del carico di lavoro: al massimo livello di maturità operativa, i team delle operazioni cloud sono in grado di ottimizzare le operazioni per i carichi di lavoro fondamentali per il successo dell'azienda. Per i carichi di lavoro a criticità elevata, i dati disponibili possono essere utili per automatizzare la correzione, il ridimensionamento o la protezione dei carichi di lavoro in base al relativo utilizzo.

Altre indicazioni, come quelle incluse nel [Framework di analisi della progettazione (nome in codice: Principi di progettazione cloud)](https://docs.microsoft.com/azure/architecture/reliability) possono essere utili per prendere decisioni specifiche in merito all'architettura per singoli carichi di lavoro in conformità alle regole descritte in precedenza.

Questa sezione di Cloud Adoption Framework si baserà su ognuno di questi argomenti per sviluppare operazioni cloud mature all'interno dell'organizzazione.