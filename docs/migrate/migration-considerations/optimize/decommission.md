---
title: Rimuovere gli asset ritirati
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Rimuovere gli asset ritirati
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ae2538263af35e8fdb2cf5c861a2c7b0537108d4
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833362"
---
# <a name="decommission-retired-assets"></a>Rimuovere gli asset ritirati

Dopo che un carico di lavoro è stato promosso alla produzione, gli asset che ospitavano in precedenza il carico di lavoro di produzione non sono più necessari per supportare le operazioni aziendali. A questo punto, gli asset precedenti vengono considerati ritirati. È quindi possibile rimuovere gli asset ritirati, riducendo i costi operativi. La rimozione di una risorsa può comportare semplicemente la disattivazione e l'eliminazione responsabile dell'asset. La rimozione delle risorse tuttavia può talvolta avere conseguenze indesiderate. Le indicazioni seguenti consentono di rimuovere correttamente le risorse ritirate, con interruzioni minime dell'attività.

## <a name="cost-savings-realization"></a>Realizzazione del risparmio sui costi

Quando il risparmio sui costi è la motivazione principale per una migrazione, la rimozione è un passaggio importante. Finché non viene rimosso, un asset continua a consumare energia, supporto ambientale e altre risorse che comportano costi. Dopo la rimozione dell'asset, iniziano a realizzarsi i risparmi sui costi.

## <a name="continued-monitoring"></a>Monitoraggio continuo

Dopo che un carico di lavoro migrato viene promosso, gli asset da ritirare devono continuare a essere monitorati per verificare che non venga eseguito il routing di traffico di produzione aggiuntivo agli asset errati.

## <a name="testing-windows-and-dependency-validation"></a>Finestre di test e convalida delle dipendenze

Anche con una pianificazione ottimale, i carichi di lavoro di produzione possono comunque contenere dipendenze da asset che si presume siano ritirati. In questi casi, la disattivazione di un asset ritirato potrebbe causare errori di sistema imprevisti. Di conseguenza, la terminazione di un asset deve essere considerata con lo stesso livello di rigore di un'attività di manutenzione del sistema. Devono essere stabilite finestre di test e interruzione appropriate per agevolare la terminazione della risorsa.

## <a name="holding-period-and-data-validation"></a>Periodo di conservazione e convalida dei dati

Non è insolito che si verifichino perdite di dati nelle migrazioni durante i processi di replica. Questo vale soprattutto per i dati meno recenti che non vengono usati con frequenza. Dopo che un asset ritirato è stato disattivato, è comunque consigliabile mantenerlo per un periodo di tempo come backup temporaneo dei dati. Le aziende dovrebbero prevedere almeno 30 giorni di conservazione e test prima di eliminare le risorse ritirate.

## <a name="next-steps"></a>Passaggi successivi

Dopo la rimozione degli asset ritirati, la migrazione è completa. Questa è una buona occasione per migliorare il processo di migrazione. Un'[analisi retrospettiva](./retrospective.md) coinvolge il team di adozione del cloud in una revisione della versione allo scopo di apprendere e migliorare.

> [!div class="nextstepaction"]
> [Analisi retrospettiva](./retrospective.md)
