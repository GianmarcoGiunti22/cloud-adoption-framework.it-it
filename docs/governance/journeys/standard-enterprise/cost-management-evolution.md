---
title: 'Guida aziendale standard: Migliorare la disciplina di gestione dei costi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida aziendale standard: Migliorare la disciplina di gestione dei costi'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 078d484becaf62cd07ec124d818891c8a52b8dbc
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908800"
---
# <a name="standard-enterprise-guide-improve-the-cost-management-discipline"></a>Guida aziendale standard: Migliorare la disciplina di gestione dei costi

In questo articolo viene avanzata la descrizione aggiungendo i controlli dei costi all'MVP di governance.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

L'adozione del cloud ha superato l'indicatore di tolleranza dei costi definito nell'MVP della governance. Ciò è positivo, dato che corrisponde alle migrazioni dal data center "DR". L'aumento della spesa ora giustifica un investimento del tempo dal team di governance del cloud.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Nella fase precedente di questo scenario, IT ha ritirato il 100% dei data center DR. Lo sviluppo dell'applicazione e i team di business intelligence (BI) sono pronti per il traffico di produzione.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- il team di migrazione ha iniziato la migrazione delle macchine virtuali all'esterno del data center di produzione.
- I team di sviluppo dell'applicazione eseguono attivamente il push di applicazioni di produzione al cloud, tramite le pipeline CI/CD. Tali applicazioni si possono ridimensionare in modo reattivo in base alle esigenze dell'utente.
- Il team business intelligence al suo interno ha fornito diversi strumenti di analisi predittiva nel cloud. I volumi di dati aggregati nel cloud continuano a crescere.
- Tale crescita supporta i risultati aziendali di esecuzione del commit. Tuttavia, i costi hanno iniziato ad aumentare velocemente. I budget previsti stanno crescendo più rapidamente di quanto ci si aspettava. Il Direttore finanziario (CFO) deve migliorare gli approcci per i costi di gestione.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

Il monitoraggio dei costi e la creazione dei report deve essere aggiunta alla soluzione cloud. IT svolge ancora la funzione di fornitore di servizi di accesso a terze parti. Ciò significa che il pagamento per i servizi cloud, continua a provenire dall'approvvigionamento IT. Tuttavia, la creazione di report deve legare le spese operative dirette alle funzioni che utilizzano i costi del cloud. Questo modello viene indicato come un modello di contabilità cloud "Show back".

I cambiamenti che riguardano lo stato attuale e quello futuro espongono a nuovi rischi che richiedono nuove definizioni di criteri.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Controllo budget:** esiste un rischio intrinseco che le capacità self-service comportino costi eccessivi e imprevisti sulla nuova piattaforma. I processi di governance per i costi di monitoraggio e i costi di migrazione in corso devono poter garantire un costante allineamento con il budget pianificato.

Questo rischio aziendale può comportare alcuni rischi tecnici:

- i costi effettivi potrebbero superare il piano.
- Le condizioni aziendali possono cambiare. In tal caso, è possibile che una funzione aziendale debba usare più servizi cloud del previsto, portando ad anomalie di spesa. Sussiste il rischio che questa spesa aggiuntiva venga considerata in eccedenza, a differenza di una rettifica necessaria per il piano.
- I sistemi potrebbero avere un provisioning eccessivo, che causerebbe la spesa in eccesso.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida.

- Tutti i costi del cloud dovrebbero essere monitorati rispetto al piano dal team di governance del cloud con frequenza settimanale. I report sulle deviazioni tra i costi del cloud e il piano stabilito devono essere condivisi con i responsabili IT e l'amministrazione con frequenza mensile. Tutti i costi del cloud e gli aggiornamenti del piano devono essere controllati ogni mese con i responsabili IT e l'amministrazione.
- Tutti i costi devono essere allocati in una funzione aziendale ai fini della rendicontazione.
- Gli asset del cloud devono essere monitorati costantemente per eventuali opportunità di ottimizzazione.
- Gli strumenti di governance del cloud devono limitare le opzioni di ridimensionamento delle risorse a un elenco approvato di configurazioni. Gli strumenti devono assicurare che tutti gli asset siano individuabili e tracciati dalla soluzione di monitoraggio dei costi.
- Durante la pianificazione della distribuzione, tutte le risorse richieste del cloud associate all'hosting dei flussi di lavoro di produzione dovrebbero essere documentate. Questa documentazione aiuterà a ridefinire i budget e a preparare altre soluzioni di automazione per impedire l'uso delle opzioni più costose. Durante questo processo si dovrebbero prendere in considerazione diversi strumenti di sconto offerti dal provider di servizi cloud, come istanze riservate o riduzioni dei costi di licenza.
- A tutti i proprietari di applicazioni è richiesta la partecipazione con training eseguito su procedure consigliate, al fine di ottimizzare i carichi di lavoro per controllare al meglio i costi del cloud.

## <a name="incremental-improvement-of-the-best-practices"></a>Miglioramento incrementale delle procedure consigliate

In questa sezione dell'articolo verrà modificata la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

1. Implementare Gestione costi di Azure.
    1. Stabilire l'ambito corretto dell'accesso in linea con il criterio di sottoscrizione e la disciplina di Coerenza delle risorse. Supponendo l'allineamento con l'MVP di governance definito negli articoli precedenti, è necessario l'accesso all' **ambito dell'account di registrazione** per il team di governance del cloud in esecuzione su report di alto livello. Altri team al di fuori della governance possono richiedere l'accesso **Ambito del gruppo di risorse**.
    1. Stabilire un budget in Gestione costi di Azure.
    1. Esaminare e implementare gli elementi consigliati. Disporre di un processo ricorrente per supportare la creazione di report.
    1. Configurare ed eseguire Creazione di report di Gestione costi di Azure, sia nella fase iniziale sia con frequenza periodica.
2. Aggiornare i Criteri di Azure
    1. Controllare l'assegnazione di tag, il gruppo di gestione, la sottoscrizione e i valori del gruppo di risorse per identificare ogni deviazione.
    1. Definire le opzioni relative alle dimensioni di SKU per limitare le distribuzioni agli SKU elencati nella documentazione relativa alla pianificazione della distribuzione.

## <a name="conclusion"></a>Conclusione

L'aggiunta di questi processi e modifiche all'MVP di governance consente di correggere molti dei rischi associati alla governance dei costi. Nel loro insieme offrono le caratteristiche di visibilità, rendicontazione e ottimizzazione necessarie per controllare i costi.

## <a name="next-steps"></a>Passaggi successivi

Quando l'adozione del cloud continua e offre un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambieranno. Per la società fittizia in questa guida, il passaggio successivo consiste nell'utilizzare questo investimento di governance per gestire più cloud.

> [!div class="nextstepaction"]
> [Evoluzione multicloud](./multicloud-evolution.md)
