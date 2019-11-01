---
title: Classificare in ordine di priorità e definire i carichi di lavoro per un piano di adozione cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Classificare in ordine di priorità e definire i carichi di lavoro per un piano di adozione cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 8e58c0e95517d49e9c8685539407127880b5d090
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240187"
---
# <a name="prioritize-and-define-workloads-for-a-cloud-adoption-plan"></a>Classificare in ordine di priorità e definire i carichi di lavoro per un piano di adozione cloud

La definizione di una priorità chiara e praticabile è uno dei segreti dell'adozione del cloud corretta. La tentazione naturale consiste nel investire tempo nella definizione di tutti i carichi di lavoro potenzialmente interessati durante l'adozione del cloud. Questa operazione è tuttavia controproducente, soprattutto nelle prime fasi del processo di adozione.

È invece consigliabile che il team si concentri sulla priorità e la documentazione dei primi 10 carichi di lavoro. Una volta avviata l'implementazione del piano di adozione, il team può gestire un elenco dei prossimi 10 carichi di lavoro con priorità più alta. Questo approccio fornisce informazioni sufficienti per pianificare le iterazioni successive.

La limitazione del piano a 10 carichi di lavoro favorisce l'agilità e l'allineamento delle priorità quando cambiano i criteri di business. Questo approccio fa anche spazio al team di adozione del cloud per apprendere e perfezionare le stime. L'aspetto più importante è la rimozione di un'ampia pianificazione come ostacolo per una modifica aziendale efficace.

## <a name="what-is-a-workload"></a>Che cos'è un carico di lavoro?

Nel contesto di un'adozione del cloud, un carico di lavoro è una raccolta di risorse IT (server, VM, applicazioni, dati o Appliance) che supportano collettivamente un processo definito. I carichi di lavoro possono supportare più di un processo. I carichi di lavoro possono inoltre dipendere da altri asset condivisi o piattaforme più grandi. Tuttavia, un carico di lavoro deve avere definito limiti relativi agli asset dipendenti e ai processi che dipendono dal carico di lavoro. Spesso è possibile visualizzare i carichi di lavoro monitorando il traffico di rete tra le risorse IT.

## <a name="prerequisites"></a>Prerequisiti

Gli input strategici dall'elenco dei prerequisiti rendono più semplice l'esecuzione delle attività seguenti. Per informazioni sulla raccolta dei dati illustrati in questo articolo, esaminare i [prerequisiti](./prerequisites.md).

## <a name="initial-workload-prioritization"></a>Priorità iniziale del carico di lavoro

Durante il processo di [razionalizzazione incrementale](../digital-estate/rationalize.md), il team deve accordarsi su un approccio "potenza di 10", che è costituito da 10 carichi di lavoro prioritari. Questi carichi di lavoro servono come limite iniziale per la pianificazione dell'adozione.

Se si decide che la razionalizzazione di una proprietà digitale non è necessaria, è consigliabile che i team di adozione del cloud e il team di strategia cloud accettino un elenco di 10 applicazioni che fungeranno da obiettivo iniziale della migrazione. Si consiglia inoltre che questi 10 carichi di lavoro contengano una combinazione di carichi di lavoro semplici (meno di 10 Asset in una distribuzione autonoma) e carichi di lavoro più complessi. Questi 10 carichi di lavoro avvierà il processo di assegnazione delle priorità del carico di lavoro.

> [!NOTE]
> La potenza di 10 funge da limite iniziale per la pianificazione, in modo da concentrare l'energia e gli investimenti nelle fasi iniziali dell'analisi. Tuttavia, l'operazione di analisi e definizione dei carichi di lavoro potrebbe causare modifiche nell'elenco dei carichi di lavoro prioritari.

## <a name="add-workloads-to-your-cloud-adoption-plan"></a>Aggiungere i carichi di lavoro al piano di adozione del cloud

Nell'articolo precedente, [piano di adozione del cloud e Azure DevOps](./template.md), è stato creato un piano di adozione del cloud in Azure DevOps.

È ora possibile rappresentare i carichi di lavoro nella potenza di 10 elenchi nel piano di adozione del cloud. Il modo più semplice per eseguire questa operazione è tramite la modifica bulk in Microsoft Excel. Per preparare la workstation per la modifica bulk, vedere [aggiungere o modificare in blocco elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Il passaggio 5 dell'articolo indica di selezionare l' **elenco di input**. In alternativa, selezionare **elenco query**. Quindi, dall'elenco **a discesa selezionare una query** , selezionare la query **modello di carico di lavoro** . Tale query carica tutti gli sforzi correlati alla migrazione di un singolo carico di lavoro nel foglio di calcolo.

Dopo aver caricato gli elementi di lavoro per il modello del carico di lavoro, attenersi alla seguente procedura per iniziare ad aggiungere nuovi carichi di lavoro:

1. Copiare tutti gli elementi che hanno il tag del **modello del carico di lavoro** nella colonna all'estrema destra.
2. Incollare le righe copiate sotto l'ultima voce della tabella.
3. Modificare la cella del titolo per la nuova funzionalità da **modello di carico di lavoro** al nome del nuovo carico di lavoro.
4. Incollare la cella del nuovo nome del carico di lavoro nella colonna Tag per tutte le righe al di sotto della nuova funzionalità. Prestare attenzione a non modificare i tag o il nome delle righe correlate alla funzionalità del **modello di carico di lavoro** effettivo. Questi elementi di lavoro sono necessari quando si aggiunge il carico di lavoro successivo al piano di adozione del cloud.
5. Andare al passaggio 8 nelle istruzioni per la modifica bulk per pubblicare il foglio di elaborazione. Questo passaggio consente di creare tutti gli elementi di lavoro necessari per eseguire la migrazione del carico di lavoro.

Ripetere i passaggi da 1 a 5 per ognuno dei carichi di lavoro nell'elenco della potenza di 10.

## <a name="define-workloads"></a>Definire i carichi di lavoro

Una volta definite le priorità iniziali e i carichi di lavoro sono stati aggiunti al piano, ognuno dei carichi di lavoro può essere definito tramite un'analisi qualitativa più approfondita. Prima di includere tutti i carichi di lavoro nel piano di adozione del cloud, provare a fornire i punti dati seguenti per ogni carico di lavoro.

### <a name="business-inputs"></a>Input aziendali

| Punto dati | Description | Input |
|---|---|---|
| Nome del carico di lavoro | Questo carico di lavoro viene chiamato? |         |
| Descrizione del carico di lavoro | In una frase, cosa fa questo carico di lavoro? |         |
| Motivazioni di adozione | Quali sono le motivazioni dell'adozione del cloud interessate da questo carico di lavoro? |         |
| Sponsor principale | Di questi stakeholder interessati, chi è lo sponsor primario che richiede le motivazioni precedenti? |         |
| Business unit | Quale Business Unit è responsabile del costo di questo carico di lavoro? |         |
| Processi aziendali | Quali processi aziendali saranno interessati dalle modifiche apportate al carico di lavoro? |         |
| Team aziendali | Quali team aziendali saranno interessati da modifiche? |         |
| Stakeholder aziendali | Sono presenti dirigenti la cui azienda sarà interessata da modifiche? |         |
| Risultati aziendali | In che modo l'azienda misura il successo di questa operazione? |         |
| Metriche | Quali metriche verranno usate per tenere traccia del successo? |         |
| Adeguamento | Sono previsti requisiti di conformità di terze parti per questo carico di lavoro? |         |
| Proprietari dell'applicazione | Chi è responsabile dell'effetto aziendale di qualsiasi applicazione associata a questo carico di lavoro? |         |
| Periodi di blocco aziendale | Ci sono casi in cui l'azienda non consentirà la modifica? |         |
| Aree geografiche | Tutte le aree geografiche interessate da questo carico di lavoro? |         |

### <a name="technical-inputs"></a>Input tecnici

| Punto dati | Description | Input |
|---|---|---|
| Approccio di adozione | Si tratta di un'adozione candidata per la migrazione o l'innovazione? |         |
| Lead Ops applicazione | Elenca le parti responsabili delle prestazioni e della disponibilità di questo carico di lavoro. |         |
| Contratti di servizio | Elencare tutti i contratti di servizio (RTO/RPO requirements). |         |
| Criticità | Elenca la criticità dell'applicazione corrente. |         |
| Classificazione dei dati | Elenca la classificazione della riservatezza dei dati. |         |
| Aree geografiche operative | Elencare le aree geografiche in cui il carico di lavoro è o deve essere ospitato. |         |
| applicazioni | Consente di specificare un elenco iniziale o un conteggio di tutte le applicazioni incluse in questo carico di lavoro. |         |
| VM | Specificare un elenco iniziale o un numero di macchine virtuali o server inclusi nel carico di lavoro. |         |
| Origini dati | Consente di specificare un elenco iniziale o un conteggio di tutte le origini dati incluse nel carico di lavoro. |         |
| Dipendenze | Elencare tutte le dipendenze di asset non incluse nel carico di lavoro. |         |
| Geografia del traffico utente | Elencare le aree geografiche con una raccolta significativa di traffico utente. |         |

## <a name="confirm-priorities"></a>Confermare le priorità

In base ai dati assemblati, il team di strategia cloud e il team di adozione del cloud devono soddisfare per rivalutare le priorità. Il chiarimento dei punti dati aziendali potrebbe richiedere modifiche alle priorità. La complessità tecnica o le dipendenze possono comportare modifiche correlate alle allocazioni del personale, alle sequenze temporali o alla sequenziazione di attività tecniche.

Dopo una revisione, entrambi i team dovrebbero essere comodi per confermare le priorità risultanti. Questo set di priorità documentata, convalidata e confermata è il backlog di adozione del cloud con priorità.

## <a name="next-steps"></a>Passaggi successivi

Per qualsiasi carico di lavoro nel backlog di adozione del cloud con priorità, il team è ora pronto per [allineare le risorse](./assets.md).

> [!div class="nextstepaction"]
> [Allineare le risorse per i carichi di lavoro con priorità](./assets.md)
