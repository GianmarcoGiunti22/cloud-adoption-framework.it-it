---
title: Informazioni sui rischi aziendali durante la migrazione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sui rischi aziendali durante la migrazione del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 26f110e808039fe17ac4186cdafa9e6a200f6fee
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029600"
---
<!-- markdownlint-disable MD026 -->

# <a name="understand-business-risk-during-cloud-migration"></a>Informazioni sui rischi aziendali durante la migrazione del cloud

Comprendere quali sono i rischi per l'azienda è uno degli aspetti più importanti di qualsiasi trasformazione per il cloud. Criteri per le unità di rischio e influiscono sui requisiti di monitoraggio e imposizione. Inoltre, influenzano in modo determinante il modo in cui viene gestito il digital estate, in locale o nel cloud.

<!-- markdownlint-enable MD026 -->

## <a name="relativity-of-risk"></a>Relatività dei rischi

Il rischio è relativo. Una piccola impresa con poche risorse IT in un edificio chiuso ha un rischio minimo. Ma basta aumentare il numero di utenti e aggiungere una connessione Internet con accesso a tali risorse perché il rischio sia superiore. E quando questa piccola impresa entra a far parte delle Fortune 500, i rischi sono esponenzialmente maggiori. Con l'aumentare dei profitti, dei processi aziendali, del numero di dipendenti e degli asset IT, i rischi aumentano e si combinano. Gli asset IT che consentono di generare profitti sono a rischio tangibile di arrestare tale flusso di profitti in caso di interruzione. Ogni istante di inattività equivale a una perdita. Allo stesso modo, mentre i dati si accumulano, cresce il rischio di danneggiare i clienti.

Nel mondo locale tradizionale, i team di governance IT si concentrano sulla valutazione dei rischi, sulla creazione di processi per la gestione di tali rischi e sulla distribuzione di sistemi per garantire che le misure correttive vengano implementate correttamente. Questi sforzi lavorano per bilanciare i rischi necessari per operare in un ambiente aziendale moderno e connesso.

## <a name="understand-business-risks-in-the-cloud"></a>Informazioni sui rischi aziendali nel cloud

Durante una trasformazione sono presenti gli stessi rischi relativi.

- Durante la sperimentazione iniziale alcune risorse vengono distribuite con pochi dati o con dati irrilevanti. I rischi sono minimi.
- Quando viene distribuito il primo carico di lavoro, il rischio aumenta leggermente. Questo rischio è facilmente monitorabile scegliendo un'applicazione a basso rischio intrinsecamente con una base utente di piccole dimensioni.
- Man mano che sempre più carichi di lavoro sono online, i rischi mutano a ogni rilascio. Con sempre più app operative, il rischio cambia.
- Quando un'azienda porta online le prime 10-20 applicazioni, il profilo di rischio è molto diverso rispetto a quando la millesima applicazione va in produzione nel cloud.

Gli asset che si sono accumulati in un patrimonio locale tradizionale accumulato probabilmente nel tempo. Il livello di maturità dell'azienda e dei team IT con molta probabilità è cresciuto in modo analogo. Questa crescita parallela può tendere a creare un bagaglio di criteri superflui.

Durante una trasformazione per il cloud, sia i team aziendali che quelli IT hanno l'opportunità di reimpostare tali criteri e crearne di nuovi con una mentalità più matura.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-a-business-risk-mvp"></a>Che cos'è un prodotto minimo funzionante per i rischi aziendali?

Un **prodotto minimo valido** viene comunemente usato per definire per definire l'unità più piccola di un elemento che può produrre un valore tangibile. In un MVP per i rischi aziendali, il team di governance del cloud inizia con il presupposto che alcune risorse verranno distribuite in un ambiente cloud in un determinato momento. Si tratta di informazioni sconosciute sulle risorse che si trovano al momento e il team potrebbe non essere sicuro dei tipi di dati che verranno archiviati in tali asset.

Quando si pianificano i rischi aziendali, il team di governance del cloud potrebbe creare per il peggiore scenario ed eseguire il mapping di tutti i criteri possibili al cloud. Tuttavia, l'identificazione di tutti i potenziali rischi aziendali per tutti gli scenari di utilizzo del cloud può richiedere molto tempo e fatica, ritardando potenzialmente l'implementazione della governance ai carichi di lavoro cloud. Non è consigliabile, ma è un'opzione.

Viceversa, un approccio MVP può consentire al team di definire un punto di partenza iniziale e un set di presupposti che sarebbero veri per la maggior parte o per tutti gli asset. Questo MVP per il rischio aziendale supporterà le distribuzioni iniziali con scalabilità ridotta o test cloud, quindi verrà usato come base per identificare e correggere gradualmente i nuovi rischi quando si verificano esigenze aziendali o aggiungere ulteriori carichi di lavoro all'ambiente cloud. Questo processo consente di applicare la governance durante il processo di adozione del cloud.

Di seguito sono riportati alcuni esempi di base dei rischi aziendali che possono essere inclusi come parte di un MVP:

- Tutti gli asset sono al rischio di essere terminati (tramite errori, errori o manutenzione).
- Tutti gli asset sono a rischio di generare una spesa troppo lunga.
- Tutti gli asset potrebbero essere compromessi da password vulnerabili.
- Qualsiasi asset con tutte le porte aperte esposte a Internet è a rischio di compromissione.

Gli esempi precedenti sono intesi a stabilire un MVP per i rischi aziendali in linea teorica. L'elenco effettivo sarà specifico per ogni ambiente.
Una volta stabilito il MVP per i rischi aziendali, questi possono essere convertiti in [criteri](./index.md) per correggere ogni rischio.

<!-- markdownlint-enable MD026 -->

## <a name="incremental-risk-mitigation"></a>Mitigazione dei rischi incrementale

Quando l'organizzazione distribuisce più carichi di lavoro nel cloud, i team di sviluppo utilizzeranno quantità sempre maggiori di risorse cloud. A ogni iterazione vengono creati e gestiti i nuovi asset. A ogni rilascio, i carichi di lavoro vengono preparati per la promozione della produzione. Ognuno di questi cicli può presentare potenziali rischi aziendali non identificati in precedenza.

Supponendo che un MVP per i rischi aziendali sia il punto di partenza per le attività iniziali di adozione del cloud, la governance può maturare in parallelo con l'uso crescente delle risorse cloud. Quando il team di governance del cloud opera in parallelo con i team di adozione del cloud, la crescita dei rischi aziendali può essere risolta Man mano che vengono identificati, fornendo un modello costante stabile per lo sviluppo della maturità di governance.

Ogni asset gestito in modo temporaneo può essere facilmente classificato in base al rischio. I documenti di classificazione dei dati possono essere compilati o creati in parallelo con i cicli di gestione temporanea. Il profilo di rischio e i punti di esposizione possono essere documentati in modo analogo. Nel tempo, una vista molto chiara dei rischi aziendali verrà messa a fuoco nell'intera organizzazione.

Con ogni iterazione, il team di governance del cloud può collaborare con il team di strategia cloud per comunicare rapidamente i nuovi rischi, le strategie di mitigazione, i compromessi e i costi potenziali. Questo consente ai partecipanti aziendali e ai responsabili IT di collaborare per prendere decisioni mature e ben informate, che ispireranno la maturità dei criteri. Quando richiesto, le modifiche ai criteri generano nuovi elementi di lavoro per la maturità dei sistemi di infrastruttura fondamentali. Quando sono richieste modifiche ai sistemi di gestione temporanea, i team di adozione del cloud hanno tempo a sufficienza per apportare le modifiche, mentre l'azienda testa i sistemi di gestione temporanea e sviluppa un piano di adozione per gli utenti.

Questo approccio riduce al minimo i rischi, assicurando al team la possibilità di muoversi rapidamente. Garantisce inoltre che i rischi vengano risolti e risolti tempestivamente prima della distribuzione.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come valutare la tolleranza al rischio durante l'adozione del cloud.

> [!div class="nextstepaction"]
> [Valutare la tolleranza ai rischi](./risk-tolerance.md)
