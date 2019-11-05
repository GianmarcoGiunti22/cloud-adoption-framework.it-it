---
title: Cos'è la classificazione dei dati?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: La classificazione dei dati consente di determinare e assegnare valore ai dati dell'organizzazione ed è un punto di partenza comune per la governance.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 513fa8c7ea57909657584815f12b37e07c02f5d0
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72980229"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-data-classification"></a>Cos'è la classificazione dei dati?

La classificazione dei dati consente di determinare e assegnare valore ai dati dell'organizzazione ed è un punto di partenza comune per la governance. Il processo di classificazione dei dati suddivide i dati in base alla sensibilità e all'effetto aziendale per identificare i rischi. Quando i dati vengono classificati, è possibile gestirli in modi che proteggono dati sensibili o importanti da furto o perdita.

## <a name="understand-data-risks-then-manage-them"></a>Informazioni sui rischi per i dati e su come gestirli

Prima di poter gestire il rischio, è necessario comprenderlo. Nel caso di rischio di violazione dei dati, l'identificazione è basata principalmente sulla classificazione dei dati. La classificazione dei dati è il processo di associazione di una caratteristica dei metadati a ogni asset in una proprietà digitale, che identifica il tipo di dati associato a tale asset.

Qualsiasi asset identificato come potenziale candidato per la migrazione o la distribuzione nel cloud deve avere metadati documentati per registrare la classificazione dei dati, la criticità aziendale e la responsabilità della fatturazione. Questi tre punti di classificazione risultano molto utili per comprendere e mitigare i rischi.

## <a name="classifications-microsoft-uses"></a>Classificazioni utilizzate da Microsoft

Di seguito è riportato un elenco delle classificazioni usate da Microsoft. A seconda del settore o dei requisiti di sicurezza esistenti, gli standard di classificazione dei dati potrebbero già esistere all'interno dell'organizzazione. Se non esiste alcun standard, è consigliabile usare questa classificazione di esempio per comprendere meglio il proprio profilo di rischio e la proprietà digitale.

- **Non business:** Dati della vita personale che non appartengono a Microsoft.
- **Pubblico:** Dati aziendali liberamente disponibili e approvati per l'utilizzo pubblico.
- **Generale:** Dati aziendali non destinati a un pubblico pubblico.
- **Riservato:** Dati aziendali che possono causare danni a Microsoft in caso di overshareing.
- **Riservatezza elevata:** Dati aziendali che comportano gravi danni a Microsoft in caso di Overshare.

## <a name="tagging-data-classification-in-azure"></a>Assegnazione di tag alla classificazione di dati in Azure

I tag delle risorse rappresentano un approccio efficace per l'archiviazione dei metadati ed è possibile usare questi tag per applicare le informazioni di classificazione dei dati alle risorse distribuite. Sebbene l'assegnazione di tag alle risorse cloud per classificazione non sia una sostituzione per un processo formale di classificazione dei dati, fornisce uno strumento prezioso per la gestione delle risorse e l'applicazione dei criteri. [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection) è una soluzione eccellente che consente di classificare _i dati_ , indipendentemente da dove si trova (in locale, in Azure o altrove). Considerarlo come parte di una strategia di classificazione complessiva.

Per altre informazioni sull'aggiunta di tag alle risorse in Azure, vedere [uso dei tag per organizzare le risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="next-steps"></a>Passaggi successivi

Applicare le classificazioni dei dati durante una delle guide di governance di utilità pratica.

> [!div class="nextstepaction"]
> [Scegliere una guida alla governance praticabile](../guides/index.md)
