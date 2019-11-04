---
title: Guida alle decisioni relative alle sottoscrizioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle sottoscrizioni di piattaforme cloud come servizio di base nelle migrazioni di Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 4f024a95afcb993bd0fe314737ee4d2f97daffb0
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73238780"
---
# <a name="subscription-decision-guide"></a>Guida alle decisioni relative alle sottoscrizioni

Una progettazione efficace delle sottoscrizioni consente alle organizzazioni di stabilire una struttura per organizzare gli asset in Azure durante l'adozione del cloud.

Ogni risorsa in Azure, ad esempio una macchina virtuale o un database, è associata a una sottoscrizione. Per l'adozione di Azure è quindi necessario creare una sottoscrizione di Azure e associarla a un account e quindi distribuire le risorse nella sottoscrizione. Per una panoramica di questi concetti, vedere [Concetti fondamentali di Azure](../../ready/considerations/fundamental-concepts.md).

Con l'incremento del digital estate in Azure, è probabilmente necessario creare altre sottoscrizioni per soddisfare i requisiti. Azure consente di definire una gerarchia di gruppi di gestione per organizzare le sottoscrizioni e applicare facilmente i criteri più adatti alle risorse appropriate. Per altre informazioni, vedere [Ridimensionamento con più sottoscrizioni di Azure](../../ready/azure-best-practices/scaling-subscriptions.md).

Alcuni esempi di base relativi all'uso dei gruppi di gestione per separare carichi di lavoro diversi includono:

- **Carichi di lavoro di produzione e non di produzione:** alcune organizzazioni creano gruppi di gestione per separare le sottoscrizioni di produzione e non di produzione. I gruppi di gestione consentono a questi clienti di gestire più facilmente ruoli e criteri. Ad esempio, una sottoscrizione non di produzione può consentire agli sviluppatori l'accesso come **collaboratore**, mentre nell'ambiente di produzione hanno solo l'accesso come **lettore**.
- **Servizi interni o esterni:** in modo molto simile ai carichi di lavoro di produzione e non di produzione, le aziende hanno spesso requisiti, criteri e ruoli diversi per servizi interni ed esterni destinati ai clienti.

Questa guida alle decisioni consente di prendere in considerazione diversi approcci per organizzare la gerarchia dei gruppi di gestione.

## <a name="subscription-design-patterns"></a>Schemi progettuali per sottoscrizioni

Poiché ogni organizzazione è diversa, i gruppi di gestione di Azure sono progettati per essere flessibili. La modellazione del cloud estate in base alla gerarchia dell'organizzazione consente di definire e applicare i criteri ai livelli più elevati della gerarchia e fare affidamento sull'ereditarietà per garantire che tali criteri vengano applicati automaticamente ai gruppi di gestione ai livelli inferiori della gerarchia. Anche se è possibile spostare le sottoscrizioni tra diversi gruppi di gestione, è utile progettare una gerarchia iniziale dei gruppi di gestione che rispecchi le esigenze organizzative previste.

Prima di finalizzare la progettazione di una sottoscrizione, considerare anche come le valutazioni relative alla [coerenza delle risorse](../resource-consistency/index.md) potrebbero influenzare le scelte di progettazione.

> [!NOTE]
> Con i Contratti Enterprise (EA) di Azure è possibile definire un'altra gerarchia organizzativa ai fini della fatturazione. Questa gerarchia è diversa dalla gerarchia dei gruppi di gestione, incentrata sull'offerta di un modello di ereditarietà per applicare facilmente alle risorse criteri adeguati e il controllo di accesso.

I modelli di sottoscrizione seguenti riflettono un incremento iniziale della complessità della progettazione delle sottoscrizioni, seguito da diverse gerarchie più avanzate ben allineabili all'organizzazione:

### <a name="single-subscription"></a>Singola sottoscrizione

Una sottoscrizione singola per account potrebbe essere sufficiente per le organizzazioni che devono distribuire un numero ridotto di risorse ospitate nel cloud. Questo è il primo modello di sottoscrizione che viene implementato all'inizio del processo di adozione del cloud, in modo da consentire alle distribuzioni basate sul modello di verifica o sperimentali su scala ridotta di esplorare le funzionalità del cloud.

### <a name="production-and-nonproduction-pattern"></a>Modello di produzione e non di produzione

Dopo aver predisposto la distribuzione di un carico di lavoro in un ambiente di produzione, è necessario aggiungere un'altra sottoscrizione. In questo modo sarà possibile mantenere i dati di produzione e gli altri asset esterni agli ambienti di sviluppo/test. È anche possibile applicare facilmente due diversi set di criteri tra le risorse nelle due sottoscrizioni.

![Modello di sottoscrizione per produzione e non produzione](../../_images/ready/basic-subscription-model.png)

### <a name="workload-separation-pattern"></a>Modello di separazione del carico di lavoro

Quando un'organizzazione aggiunge nuovi carichi di lavoro al cloud, la diversa proprietà delle sottoscrizioni o la separazione di base delle responsabilità può comportare più sottoscrizioni nei gruppi di gestione di produzione e non produzione. Anche se questo approccio offre una separazione di base del carico di lavoro, non sfrutta in modo significativo il modello di ereditarietà per applicare automaticamente i criteri in un subset delle sottoscrizioni.

![Modello di separazione del carico di lavoro](../../_images/ready/management-group-hierarchy.png)

### <a name="application-category-pattern"></a>Modello di categoria delle applicazioni

Con l'aumento del footprint cloud di un'organizzazione, vengono in genere create sottoscrizioni aggiuntive per supportare le applicazioni che presentano differenze significative a livello di criticità aziendale, requisiti di conformità, controlli di accesso o esigenze di protezione dei dati. Partendo dal modello di sottoscrizione per produzione e non produzione, a seconda dei casi le sottoscrizioni che supportano queste categorie di applicazioni vengono organizzate nel gruppo di gestione di produzione o non produzione. Queste sottoscrizioni appartengono e vengono amministrate in genere dal personale della centrale operativa IT.

![Modello di categoria delle applicazioni](../../_images/infra-subscriptions/application.png)

Ogni organizzazione classificherà le applicazioni in modo diverso, spesso separandole in base a specifiche applicazioni o servizi oppure alle caratteristiche degli archetipi delle applicazioni. Questa categorizzazione spesso è progettata per supportare carichi di lavoro che probabilmente utilizzano la maggior parte dei limiti delle risorse di una sottoscrizione o per separare carichi di lavoro cruciali e assicurarsi che non entrino in competizione con altri carichi di lavoro a cui si applicano tali limiti. Alcuni carichi di lavoro che possano giustificare una sottoscrizione separata in questo modello includono:

- Carichi di lavoro cruciali.
- Applicazioni che fanno parte dei costi del venduto nell'azienda. Esempio: ogni istanza del widget dell'azienda X contiene un modulo IoT di Azure che invia dati di telemetria. In questo caso può essere necessaria una sottoscrizione dedicata a scopi di contabilità/governance come parte dei costi del venduto.
- Applicazioni soggette a requisiti normativi, come HIPAA o FedRAMP.

### <a name="functional-pattern"></a>Modello funzionale

Il modello funzionale organizza le sottoscrizioni e gli account in base alle caratteristiche funzionali, ad esempio finanza, vendite o supporto IT, usando una gerarchia dei gruppi di gestione.

### <a name="business-unit-pattern"></a>Modello business unit

Questo modello di business unit raggruppa le sottoscrizioni e gli account in base a categoria di profitti e perdite, business unit, divisione, centro di profitti o una struttura aziendale simile usando una gerarchia dei gruppi di gestione.

### <a name="geographic-pattern"></a>Modello geografico

Per le organizzazioni con operazioni globali, il modello geografico raggruppa le sottoscrizioni e gli account in base alle aree geografiche usando una gerarchia dei gruppi di gestione.

## <a name="mixed-patterns"></a>Modelli misti

Le gerarchie dei gruppi di gestione possono supportare fino a sei livelli di profondità. Offrono quindi la flessibilità necessaria per creare una gerarchia che combina diversi modelli per soddisfare le esigenze dell'organizzazione. Ad esempio, il diagramma seguente mostra una gerarchia organizzativa che combina un modello di business unit con uno geografico.

![Modello di sottoscrizione misto](../../_images/infra-subscriptions/mixed.png)

## <a name="related-resources"></a>Risorse correlate

- [Gestione dell'accesso alle risorse in Azure](../../govern/resource-consistency/resource-access-management.md)
- [Più livelli di governance nelle aziende di grandi dimensioni](../../govern/guides/complex/multiple-layers-of-governance.md)
- [Più aree geografiche](../regions/index.md)

## <a name="next-steps"></a>Passaggi successivi

La progettazione delle sottoscrizioni è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
