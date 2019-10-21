---
title: Stimare i costi del cloud prima della migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del processo di stima dei costi del cloud prima della migrazione.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: be4fe4616b4f0599075ceac2b9c0838949b350c8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548477"
---
# <a name="estimate-cloud-costs"></a>Stimare i costi del cloud

Durante la migrazione, sono numerosi i fattori che influiscono sulle decisioni e sulle attività di esecuzione. Per comprendere quali di queste opzioni sono ideali a seconda della situazione, questo articolo illustra diverse opzioni per stimare i costi del cloud.

## <a name="digital-estate-size"></a>Portata del digital estate

La portata del digital estate influisce direttamente sulle decisioni di migrazione. Le migrazioni che coinvolgono meno di 250 macchine virtuali possono essere stimate molto più facilmente rispetto a una migrazione che interessa più di 10.000 macchine virtuali. È fortemente consigliabile selezionare un carico di lavoro più ridotto come prima migrazione. Questo consente al team di apprendere come stimare i costi di una semplice operazione di migrazione prima di provare a stimare migrazioni di carichi di lavoro più grandi e complesse.

È opportuno notare, tuttavia, che le migrazioni più ridotte e a singolo carico di lavoro possono comunque coinvolgere una quantità molto variabile di risorse di supporto. Se la migrazione riguarda meno di 1.000 macchine virtuali, uno strumento come [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-overview) è probabilmente sufficiente per raccogliere dati sui costi di inventario e previsione. Le opzioni aggiuntive relative agli strumenti per la stima dei costi sono descritte nell'articolo sui [calcoli dei costi del digital estate](../../../digital-estate/calculate.md).

Per più di 1000 unità di proprietà digitali, è comunque possibile suddividere una stima in quattro o cinque iterazioni eseguibili, rendendo gestibile il processo di stima. Per estate di dimensioni maggiori o quando è richiesto un livello superiore di accuratezza delle previsioni, sarà probabilmente necessario un approccio più completo, come quello illustrato nella sezione "[Digital estate](../../../digital-estate/index.md)" del framework di adozione del cloud.

## <a name="accounting-models"></a>Modelli di contabilità

Modelli di contabilità

Se si ha familiarità con i processi di approvvigionamento IT tradizionali, la stima nel cloud potrebbe sembrare estranea. Quando si adottano tecnologie cloud, l'acquisizione viene spostata da un modello di spesa in conto capitale rigido e strutturato a un modello di spesa operativa fluida. Nel modello di spesa in conto capitale tradizionale, il team IT tenterà di consolidare la potenza di acquisto per più carichi di lavoro in vari programmi per centralizzare un pool di risorse IT condivise che potrebbero supportare ognuna di tali soluzioni. Nel modello cloud delle spese operative, i costi possono essere attribuiti direttamente alle esigenze di supporto di singoli carichi di lavoro, team o business unit. Questo approccio consente di attribuire più direttamente i costi ai clienti interni a cui viene fornita assistenza. Quando si stimano i costi, è importante comprendere innanzitutto la quantità di questa nuova funzionalità di contabilità che verrà usata dal team IT.

Per coloro che vogliono replicare l'approccio legacy per le spese in conto capitale per la contabilità, usare gli output di uno dei due approcci suggeriti nella sezione ["Portata del digital estate"](#digital-estate-size)" per ottenere un costo annuale. Successivamente, moltiplicare il costo annuale per il ciclo di aggiornamento hardware tipico della società. Il ciclo di aggiornamento hardware è la frequenza con cui un'azienda sostituisce il vecchio hardware, in genere misurata in anni. La frequenza di esecuzione annuale moltiplicata per il ciclo di aggiornamento hardware crea una struttura di costo simile a un modello di investimento per spese in conto capitale.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver stimato i costi, può iniziare la migrazione. Tuttavia, sarebbe opportuno rivedere le [opzioni di collaborazione e supporto](./partnership-options.md) prima di iniziare la migrazione.

> [!div class="nextstepaction"]
> [Informazioni sulle opzioni di partnership](./partnership-options.md)
