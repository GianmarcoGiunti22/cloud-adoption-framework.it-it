---
title: Strategia di governance o di conformità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strategia di governance o di conformità
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 6c1ac4000f5b79d6b177e8703f5e58b6dd9c9e56
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022727"
---
# <a name="governance-or-compliance-strategy"></a>Strategia di governance o di conformità

Se in un processo di migrazione è richiesta governance o conformità, è necessario espandere l'ambito. Le indicazioni riportate di seguito consentono di espandere l'ambito della [Guida alla migrazione ad Azure](../azure-migration-guide/index.md) in modo da considerare diversi approcci di gestione dei requisiti di governance o conformità.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

Nei casi in cui si richieda governance o conformità, le attività più interessate sono quelle essenziali. Potrebbero essere necessarie rettifiche aggiuntive durante la valutazione, la migrazione e l'ottimizzazione.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

La configurazione dell'ambiente Azure di base potrebbe cambiare in modo significativo quando si integrano i requisiti di governance o conformità. Per comprendere come cambiano i prerequisiti, è importante conoscere la natura dei requisiti. Prima di iniziare qualsiasi migrazione che richieda governance o conformità, è necessario scegliere un approccio e implementarlo nell'ambiente cloud. Di seguito sono riportati alcuni approcci generali comunemente usati durante le migrazioni:

**Approccio di governance comune.** Per la maggior parte delle organizzazioni, il [modello di governance Cloud Adoption Framework](../../govern/guides/index.md) è un approccio sufficiente costituito dall'implementazione di un prodotto minimo funzionante, seguita da iterazioni mirate di maturità di governance per la gestione di rischi tangibili identificati nel piano di adozione. Questo approccio fornisce gli strumenti minimi necessari per stabilire una governance coerente, in modo che il team possa comprendere gli strumenti. Illustra quindi questi strumenti per risolvere i problemi comuni di governance.

**Progetti di conformità ISO 27001.** Per i clienti che devono rispettare gli standard di conformità ISO, gli [esempi di progetti di servizi condivisi ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-shared/index) possono fungere da prodotto minimo funzionante più efficace per produrre vincoli di governance più completi all'inizio del processo iterativo. L'[esempio di ambiente del servizio app/database SQL ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-ase-sql-workload) illustra il progetto per il mapping dei controlli e la distribuzione di un'architettura comune per l'ambiente di un'applicazione. Man mano che verranno rilasciati, gli altri progetti di conformità verranno riportati come riferimento anche in questo articolo.

**Data center virtuale.** Talvolta può essere necessario definire un punto di partenza più solido per il percorso di governance. In tal caso, prendere in considerazione il [data center virtuale di Azure](../../reference/vdc.md). Questo approccio è in genere consigliabile per le adozioni su scala aziendale, in particolare se la quantità di asset interessati è superiore a 10.000. Rappresenta anche la scelta standard per gli scenari di governance complessi, quando deve essere soddisfatto uno dei requisiti seguenti: conformità completa a soluzioni di terze parti, esperienza approfondita del settore o adeguamento a requisiti di conformità e criteri di governance IT consolidati.

### <a name="partnership-option-to-complete-prerequisites"></a>Opzione di partnership per il completamento dei prerequisiti

**Servizi Microsoft.** I servizi Microsoft presentano offerte di soluzioni che possono essere allineate al modello di governance, ai progetti di conformità o alle opzioni di data center virtuali di Cloud Adoption Framework per garantire il modello di governance o conformità più appropriato. Usare la soluzione [Secure Cloud Insights (SCI)](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) per stabilire un'immagine basata sui dati relativa a una distribuzione di clienti in Azure, convalidare la maturità di implementazione di Azure del cliente durante l'identificazione dell'ottimizzazione di architetture di distribuzione esistenti e rimuovere i rischi per la sicurezza e la disponibilità della governance. In base a Customer Insights, è consigliabile usare gli approcci seguenti:

- **Cloud Foundation:** definire l'architettura di base della governance, dei modelli e della progettazione di Azure con l'offerta della soluzione [Hybrid Cloud Foundation (HCF)](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf). Associare i requisiti del cliente all'architettura di riferimento più appropriata. Implementare un prodotto minimo funzionante costituito da servizi condivisi e carichi di lavoro IaaS.
- **Modernizzazione del cloud:** usare l'offerta della soluzione di [modernizzazione cloud](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) come approccio completo per spostare le applicazioni e l'infrastruttura in un servizio cloud pronto per l'azienda, nonché per eseguire l'ottimizzazione e la modernizzazione una volta nel cloud.
- **Innovazione con il cloud:** Coinvolgi i clienti tramite un approccio innovativo e univoco per la soluzione [cloud Center of Excellence (CCoE)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) che consente di compilare un'organizzazione IT moderna per offrire agilità su larga scala con DevOps, mantenendo al tempo stesso il controllo. Implementa un approccio agile per l'acquisizione dei requisiti aziendali e il riutilizzo dei pacchetti di distribuzione allineati ai criteri di sicurezza, conformità e gestione dei servizi e mantiene la piattaforma Azure allineata alle procedure operative.

## <a name="assess-process-changes"></a>Modifiche del processo di valutazione

Durante la valutazione, è necessario prendere decisioni aggiuntive per allinearsi all'approccio di governance richiesto. Il team di governance del cloud deve fornire a tutti i membri del team di adozione del cloud eventuali informative sui criteri, indicazioni sull'architettura o requisiti di governance/conformità prima della valutazione di un carico di lavoro.

### <a name="suggested-action-during-the-assess-process"></a>Azione suggerita durante il processo di valutazione

I requisiti di valutazione di governance e conformità sono troppo specifici del cliente per fornire indicazioni generali sui passaggi effettivi eseguiti durante la valutazione. È tuttavia preferibile che il processo includa attività e allocazioni di tempo per l'"allineamento ai requisiti di conformità/governance". Per altre informazioni su questi requisiti, vedere i collegamenti seguenti:

Per una conoscenza più approfondita della governance, esaminare la [panoramica delle cinque discipline sulla governance del cloud](../../govern/governance-disciplines.md). Questa sezione di Cloud Adoption Framework include anche modelli per documentare i criteri, le indicazioni e i requisiti per ognuna delle cinque sezioni:

- [Gestione dei costi](../../govern/cost-management/template.md)
- [Baseline di sicurezza](../../govern/security-baseline/template.md)
- [Coerenza delle risorse].. /.. /govern/resource-consistency/template.md)
- [Baseline di identità].. /.. /govern/identity-baseline/template.md)
- [Accelerazione della distribuzione](../../govern/deployment-acceleration/template.md)

Per indicazioni sullo sviluppo di linee guida sulla governance basate sul modello di governance di Cloud Adoption Framework, vedere [Implementazione di una strategia di governance del cloud](../../govern/corporate-policy.md).

## <a name="optimize-and-promote-process-changes"></a>Modifiche dei processi di ottimizzazione e promozione

Durante i processi di ottimizzazione e promozione, si consiglia al team di governance del cloud di investire tempo per testare e convalidare l'adesione agli standard di governance e conformità. Questo passaggio inoltre è il momento giusto per inserire i processi che consentono al team di governance del cloud di gestire i modelli che potrebbero fornire un'ulteriore [accelerazione della distribuzione](../../govern/deployment-acceleration/index.md) per progetti futuri.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Azione suggerita durante il processo di ottimizzazione e promozione

Durante questo processo, è consigliabile che il piano del progetto includa allocazioni di tempo per consentire al team di governance del cloud di eseguire una verifica della conformità per ogni carico di lavoro pianificato per la promozione alla produzione.

## <a name="next-steps"></a>Passaggi successivi

Come ultima voce dell'[elenco di controllo per l'espansione dell'ambito](./index.md), il lettore è invitato a tornare all'elenco di controllo e a rivalutare altri eventuali requisiti di ambito per la migrazione.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
