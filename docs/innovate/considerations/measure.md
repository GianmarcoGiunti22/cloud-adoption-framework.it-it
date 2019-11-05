---
title: 'Innovazione nel cloud: misura'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione nel cloud-misure di contenuto
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: c050e34feecfe26431c7105eef46d000fbb32cf8
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565609"
---
# <a name="measure-for-customer-impact"></a>Misura per l'effetto del cliente

Esistono diversi modi per misurare l'effetto del cliente. Questo articolo consentirà di definire le metriche per convalidare le ipotesi che derivano da un impegno di [compilazione con l'empatia dei clienti](./build.md).

## <a name="strategic-metrics"></a>Metriche strategiche

Durante la [fase di strategia](../../strategy/index.md) del ciclo di vita dell'adozione del cloud, vengono esaminate le [motivazioni](../../strategy/motivations.md) e i [risultati aziendali](../../strategy/business-outcomes/index.md). Queste procedure forniscono un set di metriche in base ai quali testare l'effetto del cliente. Quando l'innovazione ha esito positivo, si tende a visualizzare i risultati allineati agli obiettivi strategici.

Prima di stabilire le metriche di apprendimento, definire un numero ridotto di metriche strategiche di cui si vuole influire questa innovazione. In genere queste metriche strategiche si allineano a una o più delle seguenti aree di risultato: [agilità aziendale](../../strategy/business-outcomes/agility-outcomes.md), [coinvolgimento dei clienti](../../strategy/business-outcomes/engagement-outcomes.md), [copertura dei clienti](../../strategy/business-outcomes/reach-outcomes.md), [effetti finanziari](../../strategy/business-outcomes/fiscal-outcomes.md)o in caso di innovazione operativa: [soluzione prestazioni](../../strategy/business-outcomes/fiscal-outcomes.md).

Documentare le metriche concordate e tenere traccia dell'effetto di frequente. Tuttavia, non si prevede che i risultati di queste metriche emergano per diverse iterazioni. Per ulteriori informazioni sull'impostazione e l'allineamento delle aspettative tra le parti coinvolte, vedere [impegno per l'iterazione](./index.md#commitment-to-iteration).

Oltre alla motivazione e alle metriche dei risultati aziendali, la parte restante di questo articolo è incentrata sulle metriche di apprendimento progettate per guidare l'individuazione trasparente e le iterazioni incentrate sul cliente. Per ulteriori informazioni su questi aspetti, vedere [impegno per la trasparenza](./index.md#commitment-to-transparency).

## <a name="learning-metrics"></a>Metriche di apprendimento

Quando la prima versione di un prodotto MVP minimo viene condivisa con i clienti, preferibilmente alla fine della prima iterazione di sviluppo, non vi sarà alcun effetto sulle metriche strategiche. Diverse iterazioni in un secondo momento, è possibile che il team stia ancora faticando a modificare i comportamenti abbastanza per influenzare in modo sostanziale le metriche strategiche. Durante i processi di apprendimento, ad esempio i cicli Build-Measure-Learning, si consiglia al team di adottare le metriche di apprendimento. Queste metriche di rilevamento e opportunità di formazione.

### <a name="customer-flow-and-learning-metrics"></a>Metriche di formazione e flusso del cliente

Se una soluzione MVP convalida un'ipotesi incentrata sul cliente, la soluzione indurrà alcune modifiche ai comportamenti dei clienti. Queste modifiche del comportamento tra le coorti dei clienti devono migliorare i risultati aziendali. Tenere presente che la modifica del comportamento dei clienti è in genere un processo costituito da più passaggi. Poiché ogni passaggio consente di misurare l'effetto, il team di adozione può proseguire l'apprendimento e creare una soluzione migliore.

Per conoscere le modifiche apportate al comportamento dei clienti, è necessario mappare il flusso che si spera di visualizzare da una soluzione MVP.

![Flusso del cliente usato per determinare le metriche di apprendimento](../../_images/innovate/customer-flow-learning-metrics.png)

Nella maggior parte dei casi, un flusso di clienti avrà un punto di partenza facilmente definito e non più di due punti finali. Tra i punti di inizio e di fine sono disponibili diverse metriche di apprendimento da usare come misure nel ciclo di feedback:

1. **Punto iniziale-trigger iniziale:** Il punto di partenza è lo scenario che innesca la necessità di questa soluzione. Quando la soluzione viene compilata con l'empatia del cliente, il trigger iniziale dovrebbe ispirare un cliente a provare la soluzione MVP.
2. **Necessità del cliente soddisfatta:** L'ipotesi viene convalidata quando è stata soddisfatta una necessità del cliente tramite la soluzione.
3. **Passaggi della soluzione:** Questo termine fa riferimento ai passaggi necessari per spostare il cliente dal trigger iniziale a un risultato positivo. Ogni passaggio produce una metrica di apprendimento basata sulla decisione del cliente di passare al passaggio successivo.
4. **Adozione di singoli risultati:** Al successivo rilevamento del trigger, se il cliente torna alla soluzione per soddisfare le proprie esigenze, è stata raggiunta l'adozione individuale.
5. **Indicatore di risultato aziendale:** Quando un cliente si comporta in modo da contribuire al risultato aziendale definito, viene osservato un indicatore di risultato aziendale.
6. **Vera innovazione:** Quando gli *indicatori di risultato aziendale* e l' *adozione individuale* si verificano entrambi sulla scala desiderata, è stata realizzata una vera innovazione.

Ogni passaggio del flusso del cliente genera metriche di apprendimento. Dopo ogni iterazione (o versione), viene testata una nuova versione dell'ipotesi. Allo stesso tempo, le modifiche apportate alla soluzione vengono testate per riflettere le rettifiche nell'ipotesi. Quando i clienti seguono il percorso previsto in un determinato passaggio, viene registrata una metrica positiva. Quando i clienti deviano dal percorso prestabilito, viene registrata una metrica negativa.

Questi contatori di allineamento e deviazione creano metriche di apprendimento. Ognuno di essi deve essere registrato e rilevato come il team di adozione del cloud progredisce verso i risultati aziendali e la vera innovazione. In [Learn with customers](./learn.md)verranno illustrate le procedure per applicare queste metriche per apprendere e creare soluzioni migliori.

### <a name="grouping-and-observing-customer-partners"></a>Raggruppamento e osservazione dei partner clienti

La prima misura per la definizione delle metriche di apprendimento è la definizione del partner del cliente. Qualsiasi cliente che partecipa ai cicli di innovazione è qualificato come partner clienti. Per misurare accuratamente il comportamento, è necessario usare un modello di coorte per definire i partner clienti. In questo modello, i clienti vengono raggruppati per affinare la conoscenza delle risposte alle modifiche apportate all'MVP. Questi gruppi sono in genere simili ai seguenti:

- **Gruppo di sperimentazione o messa a fuoco:** Raggruppamento dei clienti in base alla loro partecipazione a un esperimento specifico progettato per testare le modifiche nel tempo.
- **Segmento:** Raggruppamento dei clienti in base alle dimensioni dell'azienda.
- **Verticale:** Raggruppamento dei clienti in base al *settore verticale* che rappresentano.
- **Singoli dati demografici:** Raggruppamento basato sui dati demografici personali, ad esempio età e posizione fisica.

Questi tipi di raggruppamenti consentono di convalidare le metriche di apprendimento tra varie sezioni di questi clienti che scelgono di collaborare con l'utente durante le attività di innovazione. Tutte le metriche successive devono essere derivate dal raggruppamento dei clienti definibile.

## <a name="next-steps"></a>Passaggi successivi

Con l'accumulo della metrica di apprendimento, il team può iniziare a [imparare con i clienti](./learn.md).

> [!div class="nextstepaction"]
> [Scopri con i clienti](./learn.md)

Alcuni dei concetti in questo articolo si basano sugli argomenti descritti per la prima volta nell' [avvio snello](http://theleanstartup.com/book), scritto da Eric Ries.
