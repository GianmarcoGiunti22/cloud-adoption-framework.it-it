---
title: Crea il consenso sul valore aziendale dell'innovazione nel cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scopri come creare il consenso sul valore aziendale dell'innovazione nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 643da95396a4983c2642fabcf21340264d0cd1c9
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683332"
---
# <a name="building-consensus-on-the-business-value-of-innovation"></a>Creazione di consenso sul valore aziendale dell'innovazione

Il primo passaggio per sviluppare una nuova innovazione è quello di identificare il modo in cui l'innovazione indurrà un valore aziendale. Questa esercitazione pone una serie di domande che evidenziano l'importanza di investire più tempo nella definizione del valore aziendale.

## <a name="qualifying-questions"></a>Domande valide

Prima di sviluppare qualsiasi soluzione (nel cloud o in locale), convalidare i criteri dei valori aziendali:

1. Quali sono le esigenze definite per i clienti che si sta cercando di risolvere con questa soluzione?
2. Quali sono le opportunità che questa soluzione creerà per l'azienda?
3. Quali sono i risultati aziendali da raggiungere con questa soluzione?
4. Quali sono le motivazioni aziendali da usare con questa soluzione?

Se le risposte a tutte e quattro le domande sono ben documentate, potrebbe non essere necessario il resto di questo esercizio. Fortunatamente, la documentazione può essere facilmente testata. Per testare sia la documentazione che l'allineamento generale, ospitare una breve riunione con le parti interessate aziendali impegnate e una breve riunione separata con il team di sviluppo impegnato. In entrambe le riunioni, porre le quattro domande precedenti e confrontare i risultati.

> [!NOTE]
> La documentazione esistente **non deve** essere condivisa con nessuno dei due team prima della riunione. Se il vero allineamento esiste, è necessario fare riferimento alle ipotesi di GUID (o meglio ancora, ricitate) dai membri di ogni gruppo.

> [!WARNING]
> Non facilitare la riunione. Si tratta di un test di allineamento, non di un esercizio di creazione dell'allineamento. Quando si avvia la riunione, assicurarsi che i partecipanti siano consapevoli dell'obiettivo di testare l'allineamento direzionale con i contratti esistenti all'interno del team. Stabilire solo un limite di tempo. Eseguire il commit a cinque minuti per domanda e impostare un timer per ciascuno di essi. Chiudere la domanda in cinque minuti, anche se la risposta non è concordata.

Se le risposte sono allineate in direzione direzionale, ma rappresentano i diversi linguaggi e gli interessi di ogni gruppo, considerare questo esercizio come una vittoria. Si è pronti per procedere allo sviluppo della soluzione.

Se una o due delle risposte sono allineate in senso direzionale, è consigliabile riuscire a pagare. Si è ancora meglio allineati rispetto alla maggior parte delle organizzazioni. Un successo futuro è molto probabile, con un minor investimento continuo nell'allineamento. Esaminare ognuna delle sezioni seguenti per le idee che possono essere utili per creare un ulteriore allineamento.

Se uno dei due team non riesce a rispondere a tutte e quattro le domande in 30 minuti, è probabile che l'allineamento e gli sforzi seguenti abbiano un notevole effetto su questo sforzo e altri. Prestare attenzione a ognuna delle sezioni seguenti.

## <a name="address-the-big-picture-first"></a>Affronta prima di tutto l'immagine principale

Il Framework di adozione del cloud segue un percorso prestabilito attraverso la strategia, il piano, la preparazione e l'adozione. L'innovazione nel cloud rientra nella fase di adozione di questo processo. Quando le risposte alle domande 3 e 4 precedenti (risultati e motivazioni) sono allineate in modo non corretto, significa che si è verificato un problema durante la fase di strategia del ciclo di vita dell'adozione del cloud. È probabile che molti degli scenari seguenti siano in gioco.

- **Opportunità di allineamento:** Quando gli stakeholder aziendali non sono in grado di accettare le motivazioni e i risultati aziendali relativi a un lavoro di innovazione nel cloud, è un sintomo di una sfida più grande. Gli esercizi nella [fase della strategia cloud](../strategy/index.md) possono essere utili per lo sviluppo dell'allineamento tra gli stakeholder aziendali. Si consiglia inoltre di fare in modo che le stesse parti interessate formino un [team di strategia cloud](../organize/cloud-strategy.md) che soddisfi regolarmente.

- **Opportunità di comunicazione:** Quando il team di sviluppo non è in grado di accettare motivazioni e risultati aziendali, potrebbe essere un sintomo di Gap di comunicazione strategici. La revisione della strategia cloud con il team di adozione del cloud può risolvere rapidamente questo blocco. Diverse settimane dopo la revisione, il team deve ripetere l'esercizio delle domande idonee.

- **Opportunità di assegnazione delle priorità:** Una strategia cloud è essenzialmente un'ipotesi a livello esecutivo. Le migliori strategie cloud sono aperte a iterazione e commenti e suggerimenti. Se entrambi i team conoscono la strategia ma non riescono comunque a allineare le risposte a queste domande, le priorità potrebbero non essere allineate. Una sessione con il team di adozione del cloud e il team di strategia cloud potrebbe aiutare gli sforzi di entrambi i gruppi. Durante questa sessione, il team di adozione del cloud condivide le proprie risposte allineate alle domande sul quadro generale. Da qui, una conversazione tra il team di adozione cloud e il team di strategia cloud può evidenziare le opportunità per allineare meglio le priorità.

Queste opportunità di Big Picture spesso rivelano modi per allineare meglio questa soluzione alla strategia cloud. Questo esercizio presenta due risultati comuni:

- Queste conversazioni possono comportare miglioramenti nella strategia cloud e una migliore rappresentazione di questa importante esigenza dei clienti. Una modifica di questo tipo può comportare un maggiore supporto esecutivo per il team.
- Viceversa, questa conversazione potrebbe indicare che l'investimento in un'altra soluzione è più adatto al team di adozione del cloud. In questo caso, è consigliabile eseguire la migrazione di questa soluzione prima di continuare a investire nell'innovazione. In alternativa, è possibile che venga indicato che è necessario un approccio per lo sviluppo di un cittadino per testare prima il valore aziendale. In entrambi i casi, il team può evitare di realizzare un investimento significativo con ritorni aziendali limitati.

## <a name="address-solution-alignment"></a>Indirizzo allineamento soluzione

È abbastanza comune per le risposte alle domande 1 e 2 (necessità del cliente e opportunità aziendali) di essere allineate in modo non corretto. Questo è particolarmente comune durante le fasi iniziali di ideazione e sviluppo. Trovare un equilibrio tra una definizione troppo lunga e una definizione troppo limitata è difficile per molti team di sviluppo. Nel Framework di adozione del cloud, gli approcci snelli come i cicli di feedback Build-Measure-Learn sono suggeriti come il modo migliore per rispondere a queste domande. Nell'elenco seguente vengono illustrate le opportunità e gli approcci per la creazione dell'allineamento.

- **Opportunità di ipotesi:** Per le varie parti interessate e i team di sviluppo è frequente avere un numero eccessivo di aspettative per una soluzione. Quando si verifica questa situazione, è un segno che l'ipotesi è troppo vaga. Seguendo le linee guida per la [compilazione con l'empatia del cliente](./considerations/build.md) per costruire un'ipotesi più chiara.
- **Opportunità di compilazione:** Quando i team sono allineati in modo non corretto perché non sono in grado di risolvere la necessità del cliente, in genere indica che il team è stato [ritardato da un picco tecnico prematuro](./considerations/build.md#reduce-complexity-and-delay-technical-spikes). Per far concentrare il team sul cliente, avviare la prima iterazione e compilare un piccolo MVP per risolvere parte dell'ipotesi. Per altre indicazioni per aiutare il team a proseguire, vedere [sviluppo di invenzioni digitali](./considerations/invention.md).
- **Opportunità di formazione:** Quando uno dei due team è allineato in modo non corretto perché sono necessari requisiti tecnici profondi e requisiti funzionali avanzati, viene visualizzata un'opportunità di formazione nelle metodologie agile. Quando le impostazioni cultura del team non sono pronte per i processi Agile, può essere difficile innovare e rimanere al passo con il mercato. Per le risorse di formazione sulle procedure DevOps e agile, vedere:
  - [Evolve le tue procedure DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices)
  - [Creare applicazioni con Azure DevOps](https://docs.microsoft.com/learn/paths/build-applications-with-azure-devops)
  - [Distribuire applicazioni con Azure DevOps](https://docs.microsoft.com/learn/paths/deploy-applications-with-azure-devops/)

L'uso di questa metodologia e degli strumenti di gestione del backlog in ogni sezione elencata in precedenza consente di creare l'allineamento della soluzione.

## <a name="next-steps"></a>Passaggi successivi

Una volta che la proposta del valore aziendale è allineata e comunicata correttamente, è possibile iniziare a compilare la soluzione. Tornare agli [esercizi di innovazione](./index.md) per informazioni aggiuntive sui passaggi successivi.

> [!div class="nextstepaction"]
> [Tornare agli esercizi innovativi per i passaggi successivi](./index.md)
