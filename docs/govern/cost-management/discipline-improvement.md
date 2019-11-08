---
title: Miglioramento della disciplina Gestione costi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Miglioramento della disciplina Gestione costi
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 1b59121bc0679475079dc1a7b5d3770cc87d7523
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753080"
---
# <a name="cost-management-discipline-improvement"></a>Miglioramento della disciplina Gestione costi

La disciplina Gestione costi affronta i rischi aziendali di base correlati alle spese che si sostengono quando si ospitano carichi di lavoro basati sul cloud. All'interno delle cinque discipline della governance del cloud, gestione costi è responsabile del controllo dei costi e dell'utilizzo delle risorse cloud con l'obiettivo di creare e gestire un ciclo di costo pianificato.

Questo articolo illustra le attività che un'azienda può eseguire per sviluppare e maturare la disciplina Gestione costi. Queste attività possono essere suddivise nelle fasi di pianificazione, costruzione, adozione e funzionamento dell'implementazione di una soluzione cloud, che vengono poi ripetute per consentire lo sviluppo di un [incremental approach to cloud governance (approccio incrementale alla governance del cloud)](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quattro fasi di adozione](../../_images/govern/adoption-phases.png)

*Figura 1-fasi di adozione dell'approccio incrementale alla governance del cloud.*

Non è possibile rendere conto dei requisiti di tutte le aziende in un singolo documento. Di conseguenza, questo articolo delinea le attività di esempio minime e potenziali suggerite per ogni fase del processo di maturazione della governance. L'obiettivo iniziale di queste attività è quello di semplificare la creazione di un [criterio MVP](../guides/index.md#an-incremental-approach-to-cloud-governance) e stabilire un Framework per migliorare i criteri incrementali. Il team di governance del cloud dovrà decidere quanto investire in queste attività per migliorare le funzionalità di governance della gestione dei costi.

> [!CAUTION]
> Né le attività minime o potenziali descritte in questo articolo sono allineate a criteri aziendali specifici o a requisiti di conformità di terze parti. Queste linee guida sono state progettate per facilitare le conversazioni che porteranno all'allineamento di entrambi i requisiti con un modello di governance del cloud.

## <a name="planning-and-readiness"></a>Pianificazione e preparazione

Questa fase di maturità della governance colma il divario tra i risultati aziendali e le strategie attuabili. Durante questo processo, il team di leadership definisce metriche specifiche, associa tali metriche al patrimonio digitale e inizia a pianificare l'impegno complessivo richiesto per la migrazione.

**Attività minime suggerite:**

- Valutare le opzioni della [toolchain della gestione dei costi](./toolchain.md).
- Sviluppare una bozza di documento relativo alle linee guida sull'architettura e distribuirla ai principali stakeholder.
- Educare e coinvolgere le persone e i team interessati dallo sviluppo delle linee guida sull'architettura.

**Attività potenziali:**

- Verificare le decisioni di budget che supportano la motivazione aziendale per la propria strategia cloud.
- Convalidare le metriche di apprendimento usate per segnalare l'allocazione corretta del finanziamento.
- Identificare il modello di cloud accounting desiderato che influisce sulla modalità di imputazione dei costi.
- Acquisire familiarità con il piano del patrimonio digitale e convalidare le aspettative relative alla determinazione accurata dei costi.
- Valutare le opzioni di acquisto per determinare se è preferibile "pagare in base al consumo" o assumere un impegno preliminare acquistando un contratto Enterprise Agreement.
- Allineare gli obiettivi aziendali ai budget pianificati e modificare i piani di budget, se necessario.
- Sviluppare un meccanismo di comunicazione di obiettivi e budget per tenere aggiornati gli stakeholder aziendali e tecnici alla fine di ogni ciclo di costo.

## <a name="build-and-predeployment"></a>Compilazione e pre-distribuzione

Per eseguire correttamente la migrazione di un ambiente, sono necessari diversi prerequisiti tecnici e non tecnici. Questo processo riguarda principalmente le decisioni, la conformità e l'infrastruttura di base preliminari a una migrazione.

**Attività minime suggerite:**

- Implementare la [gestione dei costi](./toolchain.md) eseguendo il rollup in una fase di pre-distribuzione.
- Aggiornare il documento relativo alle linee guida sull'architettura e distribuirlo ai principali stakeholder.
- Sviluppare materiali didattici e documentazione, comunicazioni di sensibilizzazione, incentivi e altri programmi per guidare l'adozione da parte degli utenti.
- Determinare se i requisiti di acquisto sono in linea con i budget e gli obiettivi.

**Attività potenziali:**

- Allineare i piani di budget alla [strategia della sottoscrizione](../../decision-guides/subscriptions/index.md) che definisce il modello di proprietà di base.
- Usare la [strategia di coerenza delle risorse](../../decision-guides/resource-consistency/index.md) per applicare le linee guida per l'architettura e i costi nel tempo.
- Determinare se eventuali anomalie dei costi influiscono sui piani di adozione e migrazione.

## <a name="adopt-and-migrate"></a>Adottare ed eseguire la migrazione

La migrazione è un processo incrementale incentrato sullo spostamento, il testing e l'adozione di applicazioni o carichi di lavoro in un patrimonio digitale esistente.

**Attività minime suggerite:**

- Eseguire la migrazione dell'ambiente di [gestione dei costi](./toolchain.md) dalla pre-distribuzione alla produzione.
- Aggiornare il documento relativo alle linee guida sull'architettura e distribuirlo ai principali stakeholder.
- Sviluppare materiali didattici e documentazione, comunicazioni di sensibilizzazione, incentivi e altri programmi per guidare l'adozione da parte degli utenti.

**Attività potenziali:**

- Implementare il modello di contabilità cloud.
- Verificare che i budget riflettano la spesa effettiva per ogni rilascio e apportare le modifiche necessarie.
- Monitorare le modifiche nei piani di budget e verificare con gli stakeholder se sono necessarie altre approvazioni.
- Aggiornare le modifiche al documento delle linee guida sull'architettura in modo da riflettere i costi effettivi.

## <a name="operate-and-post-implementation"></a>Operazioni e post-implementazione

Al termine della trasformazione, la governance e le operazioni devono essere attivate per il ciclo di vita naturale di un'applicazione o di un carico di lavoro. Questa fase di maturità della governance si basa principalmente sulle attività che vengono svolte in genere dopo che la soluzione è stata implementata e il ciclo di trasformazione ha iniziato a stabilizzarsi.

**Attività minime suggerite:**

- Personalizzare la [gestione dei costi](./toolchain.md) in base alle modifiche apportate alle esigenze di gestione dei costi dell'organizzazione.
- Valutare l'opportunità di automatizzare le notifiche e i report in modo da riflettere la spesa effettiva.
- Perfezionare le linee guida sull'architettura per fornire indicazioni precise sui processi di adozione futuri.
- Dedicarsi periodicamente alla formazione dei team interessati per assicurarsi che vengano costantemente rispettate le linee guida sull'architettura.

**Attività potenziali:**

- Eseguire un'analisi aziendale del cloud su base trimestrale per comunicare il valore offerto all'azienda e i costi associati.
- Modificare i piani su base trimestrale in base alle modifiche della spesa effettiva.
- Determinare l'allineamento finanziario con il conto Profitti e perdite per le sottoscrizioni di business unit.
- Analizzare mensilmente i metodi di identificazione del valore e dei costi nei report per gli stakeholder.
- Porre rimedio all'eventuale sottoutilizzo di alcuni asset e determinare se vale la pena mantenerli.
- Rilevare eventuali disallineamenti e anomalie tra la spesa pianificata e quella effettiva.
- Aiutare i team di adozione del cloud e il team di strategia cloud a comprendere e risolvere queste anomalie.

## <a name="next-steps"></a>Passaggi successivi

Ora che si è appreso il concetto di governance delle identità del cloud, esaminare la [toolchain della gestione dei costi](./toolchain.md) per identificare gli strumenti e le funzionalità di Azure di cui si avrà bisogno per sviluppare la disciplina di governance Gestione costi sulla piattaforma Azure.

> [!div class="nextstepaction"]
> [Toolchain della gestione dei costi per Azure](./toolchain.md)
