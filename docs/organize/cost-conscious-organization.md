---
title: Creazione di un'organizzazione con costi ridotti
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle procedure consigliate per la creazione di un'organizzazione con costi ridotti.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.openlocfilehash: 6c01ec344d6c02fa9c576e5e674b8fddf59849fe
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566806"
---
# <a name="build-a-cost-conscious-organization"></a>Creazione di un'organizzazione con costi ridotti

Come illustrato nelle [motivazioni: perché ci si sta muovendo nel cloud?](../strategy/motivations.md), esistono molti motivi validi per l'adozione del cloud da parte di una società. Quando la riduzione dei costi è un driver principale, è importante creare un'organizzazione con costi ridotti.

Garantire che la coscienza dei costi non sia un'attività una sola volta. Come altri argomenti di adozione del cloud, è iterativo. Il diagramma seguente illustra questo processo per concentrarsi su tre attività interdipendenti: *visibilità*, *responsabilità*e *ottimizzazione*. Questi processi si rivelano a livello macro e micro, descritti in dettaglio in questo articolo.

![processo con costi ridotti](../_images/ready/cost-optimization-process.png)
*Figura 1-struttura dell'organizzazione con costi* ridotti.

## <a name="general-cost-conscious-processes"></a>Processi a costi generali

- **Visibilità:** Per fare in modo che un'organizzazione possa essere consapevole dei costi, è necessaria visibilità sui costi. La visibilità in un'organizzazione con costi ridotti richiede report coerenti per i team che adottano il cloud, i team finanziari che gestiscono i budget e i team di gestione responsabili dei costi. Questa visibilità viene eseguita stabilendo:
  - Ambito di Reporting appropriato.
  - Organizzazione delle risorse appropriata (gruppi di gestione, gruppi di risorse, sottoscrizioni).
  - Cancellare le strategie di assegnazione di tag.
  - Controlli di accesso appropriati (RBAC).

- **Responsabilità:** La responsabilità è importante come visibilità. La responsabilità inizia con un budget chiaro per le attività di adozione. I budget devono essere ben stabiliti, comunicati chiaramente e basati su aspettative realistiche. La responsabilità richiede un processo iterativo e un mindset di crescita per favorire il livello di responsabilità corretto.

- **Ottimizzazione:** L'ottimizzazione è l'azione che crea riduzioni dei costi. Durante l'ottimizzazione, le allocazioni delle risorse vengono modificate per ridurre il costo del supporto di vari carichi di lavoro. Questo processo richiede iterazione e sperimentazione. Ogni riduzione del costo riduce le prestazioni. Trovare il giusto equilibrio tra il controllo dei costi e le aspettative in termini di prestazioni degli utenti finali richiede l'input da più parti.

Le sezioni seguenti descrivono i ruoli che il team di *strategia cloud*, il *team di adozione cloud,* il *team di governance del cloud*e il *cloud Center of Excellence* (CCoE) svolgono nello sviluppo di un'organizzazione con costi ridotti.

## <a name="cloud-strategy-team"></a>Team di strategia cloud

La creazione della coscienza dei costi nelle attività di adozione del cloud inizia a livello di leadership. Per essere efficace a lungo termine, il [team di strategia cloud](./cloud-strategy.md) deve includere un membro del team finanziario. Se la struttura finanziaria è responsabile per i costi della soluzione, i responsabili devono essere invitati a partecipare anche al team. Oltre alle attività principali che vengono in genere assegnate al team di strategia cloud, è necessario che tutti i membri del team di strategia cloud siano anche responsabili di:

- **Visibilità:** Il team di strategia cloud e il [team di governance del cloud](./cloud-governance.md) devono comprendere i costi effettivi delle attività di adozione del cloud. Data la visualizzazione a livello esecutivo di questo team, devono avere accesso a più ambiti di costo per analizzare le decisioni di spesa. In genere, un dirigente necessita di visibilità sui costi totali in tutti i "spesa" del cloud. Tuttavia, come membri attivi del team di strategia cloud, dovrebbero anche poter visualizzare i costi per ogni business unit o per ogni unità di fatturazione per convalidare showback, chargeback o altri [modelli di contabilità cloud](../strategy/cloud-accounting.md).

- **Responsabilità:** È necessario stabilire i budget tra i team di strategia cloud, [governance del cloud](./cloud-governance.md)e [adozione del cloud](./cloud-adoption.md) in base alle attività di adozione previste. Quando si verificano deviazioni dal budget, il team di strategia cloud e il team di governance del cloud devono collaborare per determinare rapidamente la migliore linea di azione per correggere le deviazioni.

- **Ottimizzazione:** Durante le attività di ottimizzazione, il team di strategia cloud può rappresentare l'investimento e il valore restituito di carichi di lavoro specifici. Se un carico di lavoro ha un valore strategico o un impatto finanziario sull'azienda, le attività di ottimizzazione dei costi dovrebbero essere monitorate attentamente. Se non esiste alcun impatto strategico sull'organizzazione e nessun costo intrinseco per le prestazioni ridotte di un carico di lavoro, il team di strategia cloud può approvare la sovraottimizzazione. Per prendere queste decisioni, il team deve essere in grado di visualizzare i costi per ambito progetto.

## <a name="cloud-adoption-team"></a>Team di adozione del cloud

Il [team di adozione del cloud](./cloud-adoption.md) è al centro di tutte le attività di adozione. Quindi, sono la prima linea di difesa contro la spesa. Questo team ha un ruolo attivo in tutte e tre le fasi di coscienza dei costi.

- **Visibilità**

  - **Conoscenza:** È importante che il team di adozione del cloud abbia visibilità sugli obiettivi di risparmio dei costi del lavoro richiesto. Semplicemente indicando che il lavoro di adozione del cloud contribuirà a ridurre i costi è una ricetta per gli errori. Una visibilità *specifica* è importante. Se, ad esempio, l'obiettivo è quello di ridurre il 7% dei costi operativi del 3% o annuali del 7%, divulgare tali destinazioni in modo tempestivo e chiaro.
  - **Telemetria:** Questo team deve avere visibilità sull'effetto delle proprie decisioni. Durante le attività di migrazione o innovazione, le loro decisioni hanno un effetto diretto su costi e prestazioni. Il team deve bilanciare questi due fattori di concorrenza. Il monitoraggio delle prestazioni e il monitoraggio dei costi che hanno come ambito i progetti attivi del team sono importanti per fornire la visibilità necessaria.

- **Responsabilità:** Il team di adozione del cloud deve essere a conoscenza di qualsiasi budget preimpostato associato alle attività di adozione. Quando i costi reali non si allineano al budget, c'è la possibilità di creare responsabilità. La responsabilità non equivale a penalizzare il team di adozione per il superamento del budget, perché la franchigia del budget può derivare dalle decisioni di prestazioni necessarie. Al contrario, la responsabilità significa informare il team sugli obiettivi e sul modo in cui le loro decisioni incidono sugli obiettivi. Inoltre, la responsabilità include la fornitura di una finestra di dialogo in cui il team è in grado di comunicare sulle decisioni che hanno causato la sovraspesa. Se tali decisioni sono allineate in modo non corretto con gli obiettivi del progetto, questa operazione consente di collaborare con il team di strategia cloud per prendere decisioni migliori.

- **Ottimizzazione:** Questo sforzo è un comportamento di bilanciamento del carico, in quanto l'ottimizzazione delle risorse può ridurre le prestazioni dei carichi di lavoro supportati. Talvolta non è possibile realizzare risparmi previsti o con budget per un carico di lavoro perché il carico di lavoro non viene eseguito in modo adeguato con le risorse con budget. In questi casi, il team di adozione del cloud deve prendere decisioni sagge e segnalare le modifiche al team di strategia cloud e al team di governance del cloud in modo che sia possibile correggere i budget o le decisioni di ottimizzazione.

## <a name="cloud-governance-team"></a>Team di governance del cloud

In genere, il [team di governance del cloud](./cloud-governance.md) è responsabile della gestione dei costi nell'intero lavoro di adozione del cloud. Come illustrato nell'argomento [disciplina gestione costi](../govern/cost-management/index.md) della metodologia di governance del Framework di adozione del cloud, gestione costi è il primo dei cinque disciplinari della governance del cloud. Questi articoli illustrano una serie di responsabilità più approfondite per il team di governance del cloud.

Questo sforzo è incentrato sulle seguenti attività correlate allo sviluppo di un'organizzazione con costi ridotti:

- **Visibilità:** Il team di governance del cloud lavora come peer del team di strategia cloud per pianificare i budget per l'adozione del cloud. Questi due team collaborano anche per verificare regolarmente le spese effettive. Il team di governance del cloud è responsabile della verifica dei dati di telemetria coerenti e affidabili dei costi e delle prestazioni.

- **Responsabilità:** Quando si verificano deviazioni di budget, il team di strategia cloud e il team di governance del cloud devono collaborare per determinare rapidamente la migliore linea di azione per correggere le deviazioni. In genere, il team di governance del cloud agirà su tali decisioni. Talvolta è possibile che l'azione richieda una semplice ripetizione del training per il [team di adozione del cloud](./cloud-adoption.md)interessato. Il team di governance del cloud consente anche di ottimizzare le risorse distribuite, modificare le opzioni di riduzione o persino implementare opzioni di controllo dei costi automatizzate, ad esempio il blocco della distribuzione di asset non pianificati.

- **Ottimizzazione:** Dopo la migrazione o la creazione di asset nel cloud, è possibile usare gli strumenti di monitoraggio per valutare le prestazioni e l'utilizzo di tali asset. I dati di monitoraggio e delle prestazioni appropriati possono identificare gli asset che devono essere ottimizzati. Il team di governance del cloud è responsabile di garantire la distribuzione coerente degli strumenti di monitoraggio e di report dei costi. Consentono inoltre ai team di adozione di identificare le opportunità di ottimizzazione in base ai dati di telemetria relativi alle prestazioni e ai costi.

## <a name="cloud-center-of-excellence"></a>Centro di eccellenza cloud

Sebbene non sia in genere responsabile della gestione dei costi, i CCoE possono avere un impatto significativo sulle organizzazioni con costi ridotti. Molte decisioni IT fondamentali influiscono sui costi su larga scala. Quando il CCoE fa parte della loro parte, i costi possono essere ridotti per più sforzi di adozione del cloud.

- **Visibilità:** Tutti i gruppi di gestione o i gruppi di risorse che ospitano asset IT di base devono essere visibili al team CCoE. Il team può usare questi dati per le opportunità di ottimizzazione per la farm.

- **Responsabilità:** Sebbene non sia in genere responsabile per i costi, il CCoE può tenere conto per la creazione di soluzioni ripetibili per ridurre al minimo i costi e ottimizzare le prestazioni.

- **Ottimizzazione:** Data la visibilità di CCoE a più distribuzioni, il team si trova in una posizione ideale per suggerire suggerimenti per l'ottimizzazione e per consentire ai team di adozione di ottimizzare meglio le risorse.

## <a name="next-steps"></a>Passaggi successivi

La pratica di queste responsabilità a ogni livello dell'azienda aiuta a guidare un'organizzazione con costi ridotti. Per iniziare a operare su queste linee guida, esaminare l' [Introduzione alla conformità organizzativa](./index.md) per identificare le strutture del team corrette.

> [!div class="nextstepaction"]
> [Identificare le strutture del team corrette](./index.md)
