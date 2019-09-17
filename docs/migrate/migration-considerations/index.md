---
title: Modello di migrazione di Cloud Adoption Framework
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Modello di migrazione di Cloud Adoption Framework
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: f8a5b1bc61fd44752bae7989ff19779f8ad61882
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024695"
---
# <a name="cloud-adoption-framework-migration-model"></a>Modello di migrazione di Cloud Adoption Framework

In questa sezione di Cloud Adoption Framework vengono illustrati i principi alla base del modello di migrazione proposto dal framework. Laddove possibile, questo contenuto tenta di mantenere una posizione indipendente dal fornitore, illustrando i processi e le attività che possono essere applicati a qualsiasi migrazione al cloud, indipendentemente dal fornitore scelto.

## <a name="understand-migration-motivations"></a>Comprendere i motivi della migrazione

La migrazione al cloud è un progetto di gestione del portfolio, astutamente camuffato da implementazione tecnica. Durante il processo di migrazione, si deciderà di spostare alcuni asset, di investire in altri e di ritirare asset obsoleti o inutilizzati. Come parte di questo processo, alcuni asset verranno ottimizzati, sottoposti a refactoring o sostituiti interamente. Ognuna di queste decisioni deve essere in linea con le motivazioni alla base della scelta di eseguire una migrazione al cloud. Le migrazioni di maggiore successo vanno oltre e prevedono l'allineamento di queste decisioni ai risultati aziendali desiderati.

Il modello di migrazione di Cloud Adoption Framework dipende dal fatto che l'organizzazione abbia completato un processo di idoneità aziendale per l'adozione del cloud. Assicurarsi di aver esaminato le indicazioni relative alla [pianificazione](../../strategy/index.md) e ai [preparativi](../../ready/index.md) in Cloud Adoption Framework per determinare le motivazioni aziendali o altre giustificazioni per una migrazione al cloud, oltre alla pianificazione organizzativa o alla formazione necessarie prima di eseguire un processo di migrazione su larga scala.

> [!NOTE]
> Anche se la pianificazione aziendale è importante, una mentalità orientata alla crescita è altrettanto importante. In parallelo alle attività di pianificazione aziendale condotte su scala più ampia dal team di strategia del cloud, è consigliabile che il team di adozione del cloud avvii la migrazione di un primo carico di lavoro come precursore per progetti di migrazione più estesi. Questa migrazione iniziale consentirà al team di acquisire esperienza pratica con le problematiche aziendali e tecniche che implica una migrazione.

## <a name="envision-an-end-state"></a>Prevedere uno stato finale

È importante stabilire una visione approssimativa dello stato finale prima di avviare i progetti di migrazione. Il diagramma seguente mostra un punto iniziale locale per infrastruttura, applicazioni e dati, che nel loro insieme definiscono il *digital estate*. Durante il processo di migrazione viene eseguita la transizione di questi asset usando una delle cinque strategie di migrazione descritte in [The five Rs of rationalization](../../digital-estate/5-rs-of-rationalization.md) (I cinque pilastri della razionalizzazione).

![Infografica delle opzioni di migrazione](../../_images/migrate/migration-options.png)

La migrazione e la modernizzazione dei carichi di lavoro possono essere gestite tramite semplici migrazioni con *rehosting* ("lift and shift") usando funzionalità di infrastruttura distribuita come servizio (IaaS), tramite il *refactoring*  con modifiche minime, fino alla *riprogettazione* per modificare ed estendere la funzionalità di codice e app per sfruttare i vantaggi delle tecnologie cloud.

Le strategie native del cloud e le strategie basate su una piattaforma distribuita come servizio (PaaS) prevedono la *ricostruzione* dei carichi di lavoro locali tramite le offerte e i servizi gestiti della piattaforma Azure. I carichi di lavoro per i quali sono disponibili offerte basate sul cloud di tipo software come servizio (SaaS) completamente gestite ed equivalenti possono spesso essere *sostituiti* integralmente da questi servizi come parte del processo di migrazione.

> [!NOTE]
> Durante l'anteprima pubblica di Cloud Adoption Framework, questa sezione del framework mette in primo piano la strategia di migrazione con rehosting. Anche se le soluzioni PaaS e SaaS vengono presentate come alternative quando appropriato, la trattazione è incentrata sulla migrazione dei carichi di lavoro basati su macchine virtuali tramite le funzionalità IaaS.
>
> Altre sezioni e future iterazioni di questo contenuto amplieranno le informazioni sugli altri approcci. Per una discussione generale sull'estensione dell'ambito della migrazione per includere strategie di migrazione più complesse, vedere l'articolo dedicato al bilanciamento del portfolio.

## <a name="incremental-migration"></a>Migrazione incrementale

Il modello di migrazione di Cloud Adoption Framework si basa su un processo di trasformazione del cloud incrementale. Presuppone che l'organizzazione inizi con un progetto di migrazione al cloud iniziale con ambito limitato, indicato comunemente come primo carico di lavoro. Questo progetto verrà esteso in modo iterativo per includere più carichi di lavoro man mano che i team operativi mettono a punto e migliorano i processi di migrazione.

Gli strumenti di migrazione al cloud, come [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview), consentono di eseguire la migrazione di interi data center costituiti da decine di migliaia di macchine virtuali. Le aziende e i processi operativi IT esistenti, tuttavia, raramente riescono a gestire questi ritmi elevati di modifica. Per questi motivi, molte organizzazioni scelgono di suddividere un progetto di migrazione in più iterazioni, spostando un solo carico di lavoro (o una raccolta di carichi di lavoro) per ogni iterazione.

I principi di questo modello incrementale si basano sull'esecuzione dei processi e dei prerequisiti a cui fa riferimento l'infografica seguente.

![Modello di migrazione di Cloud Adoption Framework](../../_images/operational-transformation-migrate.png)

L'applicazione coerente di questi principi rappresenta un obiettivo finale per i processi di migrazione al cloud e non deve essere considerata come punto di partenza obbligatorio. Con il maturare dei progetti di migrazione fare riferimento alle indicazioni in questa sezione per definire il processo ottimale a supporto delle specifiche esigenze dell'organizzazione.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a conoscere questo modello, [esaminare i prerequisiti per la migrazione](./prerequisites/index.md).

> [!div class="nextstepaction"]
> [Prerequisiti per la migrazione](./prerequisites/index.md)
