---
title: Cos'è la classificazione dei dati?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Cos'è la classificazione dei dati?
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d293aa5b4427b8f714175b85c6bb5197b53f107a
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027131"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-data-classification"></a>Cos'è la classificazione dei dati?

La classificazione dei dati consente di determinare e assegnare valore ai dati dell'organizzazione ed è un punto di partenza comune per la governance. Il processo di classificazione dei dati suddivide i dati in base alla sensibilità e all'effetto aziendale per identificare i rischi. Una volta classificati, i dati possono essere gestiti in modi che proteggono dati sensibili o importanti da furto o perdita.

## <a name="understand-data-risks-then-manage-them"></a>Informazioni sui rischi per i dati e su come gestirli

Prima di poter gestire il rischio, è necessario comprenderlo. Nel caso di rischio di violazione dei dati, l'identificazione è basata principalmente sulla classificazione dei dati. La classificazione dei dati è il processo di associazione di una caratteristica di metadati a ogni asset di un patrimonio digitale, che identifica il tipo di dati associati a tale asset.

Microsoft suggerisce che qualsiasi asset identificato come candidato potenziale per la migrazione o la distribuzione nel cloud debba disporre di metadati documentati per registrare la classificazione dei dati, il livello di criticità aziendale e la responsabilità di fatturazione. Questi tre punti di classificazione risultano molto utili per comprendere e mitigare i rischi.

## <a name="microsofts-data-classification"></a>Classificazione dei dati Microsoft

Di seguito è riportato un elenco delle classificazioni usate da Microsoft. A seconda del settore di appartenenza o dei requisiti di sicurezza esistenti, è possibile che siano già definiti standard per la classificazione dei dati nell'ambito dell'organizzazione. Se non esiste alcun standard, si invita a usare questa classificazione di esempio per comprendere meglio il proprio profilo di rischio e le proprie proprietà digitali.

- **Non business:** Dati provenienti da una vita personale che non appartiene a Microsoft.
- **Pubblico**: Dati aziendali liberamente disponibili e approvati per l'utilizzo pubblico.
- **Generale:** Dati aziendali non destinati a un pubblico pubblico.
- **Riservati:** Dati aziendali che potrebbero causare danni a Microsoft in caso di Overshare.
- **Riservatezza elevata:** Dati aziendali che comportano gravi danni a Microsoft in caso di Overshare.

## <a name="tagging-data-classification-in-azure"></a>Assegnazione di tag alla classificazione di dati in Azure

Ogni provider di servizi cloud deve offrire un meccanismo per la registrazione dei metadati relativi a qualsiasi asset. Nel caso di Azure, i tag delle risorse rappresentano l'approccio consigliato per l'archiviazione di metadati e questi tag possono essere usati per applicare le informazioni di classificazione dei dati alle risorse distribuite. Sebbene l'assegnazione di tag alle risorse cloud in base alla classificazione non sia una sostituzione per un processo formale di classificazione dei dati, fornisce uno strumento utile per la gestione delle risorse e l'applicazione dei criteri.

Per altre informazioni sull'assegnazione di tag alle risorse, vedere l'articolo [Usare tag per organizzare le risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="next-steps"></a>Passaggi successivi

Applicare le classificazioni dei dati durante una delle guide di governance di utilità pratica.

> [!div class="nextstepaction"]
> [Scegliere una guida alla governance praticabile](../guides/index.md)
