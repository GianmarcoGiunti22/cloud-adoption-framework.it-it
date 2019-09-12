---
title: Raccogliere i dati di inventario per un digital estate
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Come raccogliere i dati di inventario per un digital estate.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 616bf15db1fac01966573cd5822717c59286434b
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829293"
---
# <a name="gather-inventory-data-for-a-digital-estate"></a>Raccogliere i dati di inventario per un digital estate

Lo sviluppo di un inventario è il primo passaggio della [pianificazione delle proprietà digitali](index.md). In questo processo, un elenco di asset IT che supportano funzioni aziendali specifiche viene raccolto per un'analisi e una razionalizzazione successive. In questo articolo si presuppone che un approccio di analisi dal basso verso l'alto sia più appropriato per la pianificazione. Per altre informazioni, consultare [Approcci per la pianificazione del digital estate](./approach.md).

## <a name="take-inventory-of-a-digital-estate"></a>Raccogliere i dati di inventario per un digital estate

L'inventario che supporta un'area digitale cambia a seconda della trasformazione digitale desiderata e del percorso di trasformazione corrispondente.

- **Migrazione cloud:**  Spesso è consigliabile che durante una migrazione cloud si raccolga l'inventario dagli strumenti di analisi che creano un elenco centralizzato di tutte le macchine virtuali e i server. Alcuni strumenti possono anche creare mapping di rete e dipendenze, che consentono di definire l'allineamento del carico di lavoro.

- **Innovazione dell'applicazione:** L'inventario durante un tentativo di innovazione di applicazioni abilitate per il cloud inizia con il cliente. L'esecuzione il mapping dell'esperienza del cliente dall'inizio alla fine è un buon punto di partenza. L'allineamento di tale mappa ad applicazioni, API, dati e altre risorse consente di creare un inventario dettagliato per l'analisi.

- **Innovazione dei dati:** Gli sforzi di innovazione dei dati abilitati per il cloud si concentrano sul prodotto o sul servizio. Un inventario include anche un mapping delle opportunità per l'interferenza del mercato, oltre alle funzionalità necessarie.

## <a name="accuracy-and-completeness-of-an-inventory"></a>Accuratezza e completezza di un inventario

Un inventario viene raramente completato nella prima iterazione. Si consiglia vivamente al team della strategia cloud di allineare le parti interessate e gli utenti esperti per convalidare l'inventario. Quando possibile, usare strumenti aggiuntivi come analisi della rete e delle dipendenze per identificare gli asset a cui viene inviato il traffico, ma che non sono inclusi nell'inventario.

## <a name="next-steps"></a>Passaggi successivi

Dopo che un inventario è stato compilato e convalidato, è possibile razionalizzarlo. La razionalizzazione dell'inventario è il passaggio successivo per la pianificazione delle proprietà digitali.

> [!div class="nextstepaction"]
> [Razionalizzare il digital estate](rationalize.md)
