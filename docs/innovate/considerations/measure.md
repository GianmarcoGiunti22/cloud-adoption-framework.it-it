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
ms.openlocfilehash: 00928171c3bfba1638a7e8e43ea08df4745754d2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557648"
---
# <a name="measure-for-customer-impact"></a>Misura per l'effetto del cliente

Esistono diversi modi per misurare l'effetto del cliente. Questo articolo consente di definire misure che consentono di convalidare le ipotesi create durante il tentativo [di compilazione con l'empatia del cliente](./build.md).

## <a name="strategic-metrics"></a>Metriche strategiche

Durante la [fase di strategia](../../strategy/index.md) del ciclo di vita dell'adozione del cloud, i lettori sono guidati attraverso la creazione e la documentazione delle [motivazioni](../../strategy/motivations.md) e dei [risultati aziendali](../../strategy/business-outcomes/index.md). Questi esercizi forniscono un set di metriche da usare come test dell'effetto del cliente. Quando l'innovazione ha esito positivo, verrà generato un risultato allineato agli obiettivi strategici.

Prima di stabilire le metriche di apprendimento, definire un numero ridotto di metriche strategiche che questa innovazione dovrebbe avere un effetto. In genere, queste metriche strategiche si allineano a una o più delle seguenti aree di risultato: [agilità aziendale](../../strategy/business-outcomes/agility-outcomes.md), [coinvolgimento dei clienti](../../strategy/business-outcomes/engagement-outcomes.md), [copertura dei clienti](../../strategy/business-outcomes/reach-outcomes.md), [effetti finanziari](../../strategy/business-outcomes/fiscal-outcomes.md)o nel caso di innovazione operativa: [soluzione Prestazioni](../../strategy/business-outcomes/fiscal-outcomes.md).

Documentare le metriche concordate e tenere traccia dell'effetto di frequente. Tuttavia, non si prevede che i risultati di queste metriche emergano per diverse iterazioni. Per allineare le aspettative, vedere [impegno nell'iterazione](./index.md#commitment-to-iteration) .

Oltre alla motivazione e alle metriche dei risultati aziendali, la parte restante di questo articolo è incentrata sulle metriche di apprendimento progettate per guidare l'individuazione trasparente e le iterazioni mirate al cliente. Per allineare le aspettative, vedere [impegno per la trasparenza](./index.md#commitment-to-transparency) .

## <a name="learning-metrics"></a>Metriche di apprendimento

Quando la prima versione di un prodotto MVP minimo viene condivisa con i clienti, preferibilmente alla fine della prima iterazione di sviluppo, non vi sarà alcun effetto sulle metriche strategiche. Diverse iterazioni in un secondo momento, è possibile che il team stia ancora faticando a modificare i comportamenti abbastanza per avere un effetto significativo sulle metriche strategiche. Durante i processi di apprendimento, ad esempio i cicli Build-Measure-Learn, è consigliabile che il team adotti le metriche di formazione. Queste metriche possono essere rilevate in modo più semplice e sfruttate nelle opportunità di apprendimento.

### <a name="customer-flow-and-learning-metrics"></a>Metriche di formazione e flusso del cliente

Se una soluzione MVP convalida un'ipotesi incentrata sul cliente, la soluzione indurrà alcune modifiche ai comportamenti dei clienti. Questi comportamenti tra le varie coorti dei clienti faranno raggiungere i risultati aziendali. Fortunatamente, la modifica dei comportamenti dei clienti è spesso un processo in più passaggi. Ogni passaggio offre un'opportunità per misurare l'effetto, in modo che il team di adozione possa apprendere e creare una soluzione migliore.

Per conoscere le modifiche apportate ai comportamenti dei clienti, è necessario mappare il flusso desiderato creato da una soluzione MVP.

![Flusso del cliente usato per determinare le metriche di apprendimento](../../_images/innovate/customer-flow-learning-metrics.png)

Nella maggior parte dei casi, un flusso di clienti avrà un punto di partenza facilmente definito e non più di due punti finali. Tra i punti di inizio e di fine sono disponibili diverse metriche di apprendimento da usare come misure nel ciclo di feedback:

1. **Punto iniziale-trigger iniziale:** Il punto di partenza è lo scenario che innesca la necessità della soluzione. Quando la soluzione viene compilata con l'empatia del cliente, il trigger iniziale dovrebbe ispirare un cliente a provare la soluzione MVP.
2. **Necessità del cliente soddisfatta:** L'ipotesi viene convalidata quando è stata soddisfatta una necessità del cliente tramite la soluzione.
3. **Passaggi della soluzione:** Ogni passaggio necessario per spostare il cliente dal trigger iniziale a un risultato positivo è un passaggio della soluzione. Ogni passaggio produce una metrica di apprendimento in base alle decisioni dei clienti per passare al passaggio successivo.
4. **Adozione di singoli risultati:** Al successivo rilevamento del trigger, se il cliente torna alla soluzione per fare in modo che la richiesta venga soddisfatta nuovamente, viene raggiunta l'adozione individuale.
5. **Indicatore di risultato aziendale:** Quando un cliente si comporta in modo positivo per contribuire al risultato aziendale definito, viene osservato un indicatore di risultato aziendale.
6. **Vera innovazione:** Quando "indicatori di risultato aziendale" e "adozione singola" si verificano entrambi sulla scala desiderata, è stata rilevata una vera innovazione.

Ogni passaggio del flusso del cliente genera metriche di apprendimento. Dopo ogni iterazione (o versione), viene testata una nuova versione dell'ipotesi. Allo stesso tempo, le modifiche apportate alla soluzione vengono testate per riflettere le rettifiche nell'ipotesi. Quando i clienti seguono il percorso previsto in un determinato passaggio, viene registrata una metrica positiva. Quando i clienti deviano dal percorso prestabilito per soddisfare le proprie esigenze, viene registrata una metrica negativa.

Questi contatori di allineamento e deviazione creano metriche di apprendimento. Ognuno di essi deve essere registrato e rilevato come il team di adozione del cloud progredisce verso la realizzazione dei risultati aziendali e la vera innovazione. Nel prossimo articolo, l' [apprendimento con i partner dei clienti](./learn.md) illustra i modi per sfruttare queste metriche per apprendere e creare soluzioni migliori.

### <a name="grouping-and-observing-customer-partners"></a>Raggruppamento e osservazione dei partner clienti

La prima misura per definire le metriche di apprendimento è la definizione del partner del cliente. Qualsiasi cliente che partecipa ai cicli di innovazione è qualificato come partner clienti. Per misurare accuratamente il comportamento, è importante definire i partner clienti in un modello di coorte. In questo modello, i clienti sono raggruppati per comprendere meglio il modo in cui rispondono alle modifiche apportate all'MVP. I partner clienti vengono in genere raggruppati in base ai punti dati come i seguenti:

- **Gruppo di sperimentazione o messa a fuoco:** Raggruppamento basato su un cliente che partecipa a un esperimento specifico per testare le modifiche nel tempo.
- **Segmento:** Raggruppamento dei clienti in base alle dimensioni dell'azienda.
- **Verticale:** Raggruppamento dei clienti in base al settore verticale che rappresentano.
- **Singoli dati demografici:** Raggruppamento basato sui dati demografici personali come età o posizione fisica.

Questo tipo di raggruppamento consente di convalidare le metriche di apprendimento tra varie sezioni di questi clienti che scelgono di collaborare con l'utente durante le attività di innovazione. Tutte le metriche successive devono essere osservate in base a un raggruppamento definibile del cliente.

## <a name="next-steps"></a>Passaggi successivi

Poiché le metriche di apprendimento vengono accumulate, il team può iniziare a [imparare con i clienti](./learn.md).

> [!div class="nextstepaction"]
> [Scopri con i clienti](./learn.md)

Alcuni dei concetti in questo articolo si basano sugli argomenti descritti per la prima volta nell' [avvio snello](http://theleanstartup.com/book), scritto da Eric Ries.
