---
title: Valutare la tolleranza ai rischi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione dei rischi aziendali associati a una trasformazione cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: cd8bee6cf7cf0ff06cb2846b440263cc83757f5f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027540"
---
# <a name="evaluate-risk-tolerance"></a>Valutare la tolleranza ai rischi

Ogni decisione aziendale business comporta nuovi rischi. Qualsiasi investimento comporta il rischio di perdite. I nuovi prodotti o servizi comportano rischi di fallimento sul mercato. Le modifiche apportate a prodotti o servizi correnti potrebbero ridurre la quota di mercato. La trasformazione cloud non offre una soluzione magica per i rischi aziendali quotidiani. Al contrario, le soluzioni connesse (cloud o locali) creano nuovi rischi. La distribuzione di asset in qualsiasi struttura connessa in rete espande anche il potenziale profilo di rischio esponendo le vulnerabilità della sicurezza a una più ampia community globale. Fortunatamente, i provider di servizi cloud sono a conoscenza delle modifiche, degli aumenti e dell'aggiunta dei rischi. Investono molto per ridurre e gestire questi rischi per conto dei clienti.

L'argomento di questo articolo non sono i rischi del cloud, Viene invece illustrato il rischio aziendale associato a diverse forme di trasformazione cloud. Più avanti in questo articolo, viene illustrato come determinare la tolleranza al rischio dell'azienda.

<!-- markdownlint-disable MD026 -->

## <a name="what-business-risks-are-associated-with-a-cloud-transformation"></a>Quali rischi aziendali sono associati a una trasformazione cloud?

I veri rischi aziendali sono basati sui dettagli delle trasformazioni specifiche. Molti rischi comuni forniscono un avviatore di conversazione per comprendere i rischi specifici dell'azienda.

> [!IMPORTANT]
> Prima di leggere quanto segue, tenere presente che ognuno di questi rischi può essere gestito. L'obiettivo di questo articolo è informare e preparare i lettori per le discussioni più produttive sulla gestione dei rischi.

- **Violazione dei dati:** il rischio più grave associato a qualsiasi trasformazione è quello relativo alla protezione dei dati. Le perdite di dati possono causare danni significativi all'azienda, causando la perdita di clienti, la riduzione delle attività aziendali o anche la responsabilità legale. Qualsiasi modifica al modo in cui i dati vengono archiviati, elaborati o usati comporta un rischio. Le trasformazioni cloud creano un elevato livello di modifica rispetto alla gestione dei dati, quindi il rischio non dovrebbe essere preso in considerazione. La [linea di base di sicurezza](../security-baseline/index.md), la [classificazione dei dati](./data-classification.md)e la [razionalizzazione incrementale](../../digital-estate/rationalize.md#incremental-rationalization) possono aiutare a gestire questo rischio.

- **Interrompi servizio:** Le operazioni aziendali e le esperienze dei clienti si basano principalmente sulle operazioni tecniche. Le trasformazioni cloud creeranno modifiche nelle operazioni IT. In alcune organizzazioni, la modifica è ridotta e facilmente adattabile. In altre organizzazioni, queste modifiche potrebbero richiedere la ricreazione degli strumenti, la ripetizione del training o nuovi approcci per supportare le operazioni cloud. Maggiore è il cambiamento, più grande è il potenziale impatto sulle operazioni aziendali e sull'esperienza dei clienti. La gestione di questo rischio richiederà il coinvolgimento dell'azienda nella pianificazione della trasformazione. Pianificazione della versione e prima selezione del carico di lavoro nell'articolo sulla [razionalizzazione incrementale](../../digital-estate/rationalize.md#incremental-rationalization) discutere i modi per scegliere i carichi di lavoro per i progetti di trasformazione. Il ruolo dell'azienda in questa attività consiste nel comunicare il rischio per le operazioni aziendali di modificare i carichi di lavoro con priorità. La scelta dei carichi di lavoro con un minore effetto sulle operazioni ridurrà il rischio complessivo.

- **Controllo budget:** I modelli di costo cambiano nel cloud. Questa modifica può creare rischi associati a sovraccarichi dei costi o a un aumento del costo dei beni venduti (PIGNONi), in particolare le spese operative con attributi diretti. Quando l'azienda lavora a stretto contatto con esso, è possibile creare una trasparenza relativa ai costi e ai servizi utilizzati da diverse business unit, programmi o progetti. [Gestione costi](../cost-management/index.md) fornisce esempi di come le aziende possono collaborare in questo argomento.

Quelli precedenti sono alcuni dei rischi più comuni indicati dai clienti. Il team di governance del cloud e i team di adozione del cloud possono iniziare a sviluppare un profilo di rischio, perché i carichi di lavoro vengono migrati e sono pronti per la versione di produzione. Prepararsi a conversazioni per definire, perfezionare e gestire i rischi in base ai risultati aziendali desiderati e al lavoro di trasformazione.

## <a name="understanding-risk-tolerance"></a>Informazioni sulla tolleranza ai rischi

L'identificazione dei rischi è un processo abbastanza diretto. I rischi correlati all'IT sono generalmente standard in tutti i settori. Tuttavia, la tolleranza per questi rischi è specifica di ogni organizzazione. È qui che le discussioni tra azienda e IT tendono a interrompersi. Ogni parte coinvolta sta essenzialmente parlando una lingua diversa. I confronti e le domande seguenti sono pensati per dare inizio a discussioni che consentono a ogni parte di comprendere e calcolare meglio la tolleranza ai rischi.

## <a name="simple-use-case-for-comparison"></a>Caso d'uso semplice per il confronto

Per conoscere la tolleranza ai rischi, verranno esaminati i dati dei clienti. Se una società di qualsiasi settore pubblica i dati dei clienti in un server non protetto, il rischio tecnico di tali dati viene compromesso o rubato è approssimativamente lo stesso. Tuttavia, la tolleranza di tale rischio può variare a seconda della natura e del potenziale valore dei dati.

- Le società che operano nei settori sanitario e finanziario negli Stati Uniti sono regolate da rigidi requisiti di conformità di terze parti. Si presuppone che i dati personali o i dati correlati all'assistenza sanitaria siano estremamente riservati. Questi tipi di società, se coinvolti nello scenario di rischio precedente, incorrono in gravi conseguenze. La loro tolleranza sarà estremamente bassa. I dati dei clienti pubblicati all'interno o all'esterno della rete dovranno essere regolati da tali criteri di conformità di terze parti.
- Una società di giochi i cui dati del cliente sono limitati a un nome utente, a tempi di riproduzione e a punteggi elevati non ha la probabilità di subire conseguenze significative, se coinvolgono il comportamento rischioso riportato sopra. Sebbene i dati non protetti siano a rischio, l'effetto di tale rischio è ridotto. Pertanto, in questo caso la tolleranza per il rischio è elevata.
- Un'azienda di medie dimensioni che fornisce servizi di pulizia di tappeti a migliaia di clienti entrerebbe tra questi due estremi di tolleranza. Qui, i dati dei clienti possono essere più affidabili, contenenti dettagli come l'indirizzo o il numero di telefono. Entrambi possono essere considerati dati personali e devono essere protetti. Potrebbe tuttavia non essere previsto alcun requisito di governance specifico che imponga di proteggere i dati. Dal punto di vista dell'IT, la risposta è semplice: proteggere i dati. Dal punto di vista dell'azienda, potrebbe non essere così semplice. L'azienda avrà bisogno di altre informazioni prima di poter determinare un livello di tolleranza a questo rischio.

Nella sezione successiva vengono riportate alcune domande di esempio che possono aiutare le aziende a determinare un livello di tolleranza di rischio per il caso di utilizzo precedente o per altri.

## <a name="risk-tolerance-questions"></a>Domande sulla tolleranza di rischio

Questa sezione elenca le conversazioni che provocano le domande in tre categorie: conseguenze della perdita, probabilità di perdita e costi di correzione. Quando l'azienda e il partner IT devono affrontare ciascuna di queste aree, è possibile determinare facilmente la decisione di impegnarsi per la gestione dei rischi e la tolleranza complessiva a un particolare rischio.

**Perdita di conseguenze:** domande per determinare l'impatto di un rischio. Può essere difficile (talvolta impossibile) rispondere a queste domande. Quantificare l'impatto è l'ideale, ma in alcuni casi la discussione da sola è sufficiente a comprendere la tolleranza. Anche gli intervalli sono accettabili, soprattutto se includono i presupposti che li hanno determinati.

- Questo rischio viola i requisiti di conformità di terze parti?
- Questo rischio viola i criteri aziendali interni?
- Questo rischio potrebbe comportare la perdita di clienti o della quota di mercato? In tal caso, è possibile quantificare questo costo?
- Questo rischio potrebbe comportare esperienze negative per i clienti? È probabile che queste esperienze influiscano sulla realizzazione di vendite o ricavi?
- Questo rischio potrebbe comportare nuove responsabilità legali? In tal caso, esiste una precedenza per il risarcimento dei danni in questi tipi di casi?
- Questo rischio potrebbe arrestare le operazioni aziendali? In questo caso, per quanto tempo le operazioni sarebbero ferme?
- Questo rischio potrebbe rallentare le operazioni aziendali? In tal caso, quanto è lento e quanto tempo?
- In questa fase della trasformazione, si tratta di un rischio occasionale o si ripeterà?
- La frequenza di questo rischio aumenta o diminuisce con l'avanzamento della trasformazione?
- La probabilità di questo rischio aumenta o diminuisce nel corso del tempo?
- Il rischio è per natura soggetto a variazioni nel tempo? Il rischio passerà o peggiorerà, se non viene affrontato?

Queste domande di base ne susciteranno molte altre. Dopo aver avuto un dialogo costruttivo, è consigliabile registrare e, se possibile, quantificare i rischi pertinenti.

**Costi di correzione del rischio:** Domande per determinare il costo della rimozione o ridurre al minimo il rischio. Queste domande possono essere piuttosto dirette, soprattutto se poste in successione.

- È disponibile una soluzione definitiva? Quanto costa?
- Sono disponibili opzioni per prevenire o ridurre al minimo questo rischio? Qual è la fascia di costo di tali soluzioni?
- Che cosa serve all'azienda per scegliere la migliore soluzione definiva?
- Che cosa serve all'azienda per convalidare i costi?
- Quali altri vantaggi possono derivare dalla soluzione che rimuoverebbe questo rischio?

Queste domande su come semplificare le soluzioni tecniche necessarie per gestire o rimuovere i rischi. ma comunicano tali soluzioni in modo che l'azienda possa integrarle rapidamente in un processo decisionale.

**Probabilità di perdita:** domande per determinare la probabilità che il rischio diventi reale. Questa è la parte più difficile quantificare. È invece consigliabile che il team di governance del cloud crei categorie per la comunicazione della probabilità, in base ai dati di supporto. Le domande seguenti consentono di creare categorie significative per il team.

- Sono state eseguite ricerche riguardanti la probabilità che questo rischio diventi reale?
- Il fornitore può fornire riferimenti o statistiche sulla probabilità di un effetto?
- Esistono altre società del settore o del segmento verticale pertinente che hanno corso questo rischio?
- In generale, esistono altre società che hanno corso questo rischio?
- Questo rischio è dovuto esclusivamente a qualcosa che la società ha fatto in modo non adeguato?

Dopo aver risposto a queste domande con domande come determinato dal team di governance del cloud, è probabile che i raggruppamenti della probabilità emergano. Ecco alcuni esempi di raggruppamento da cui iniziare:

- **Nessuna indicazione:** Una ricerca insufficiente è stata completata per determinare la probabilità.
- **Rischio basso:** La ricerca corrente indica che il rischio è improbabile.
- **Rischio futuro:** La probabilità corrente è bassa. Tuttavia, l'adozione continua richiederebbe una nuova analisi.
- **Rischio medio:** È probabile che il rischio influirà sull'azienda.
- **Rischio elevato:** Nel corso del tempo, è sempre più probabile che l'azienda realizzi questo rischio.
- **Rischio in calo:** Il rischio è medio-alto. Tuttavia, le azioni all'interno o all'azienda stanno riducendo la probabilità di un effetto.

**Determinazione della tolleranza:**

i tre gruppi di domande precedenti dovrebbero fornire dati sufficienti per determinare i livelli di tolleranza iniziali. Quando il rischio e la probabilità sono bassi e i costi di correzione dei rischi sono elevati, è improbabile che l'azienda investa nella correzione. Quando il rischio e la probabilità sono elevati, è probabile che l'azienda consideri un investimento, purché i costi non superino i rischi potenziali.

## <a name="next-steps"></a>Passaggi successivi

Questo tipo di discussione può aiutare l'azienda e l'IT valutare più efficacemente la tolleranza. Queste discussioni possono essere usare durante la creazione di criteri MVP e durante l'analisi incrementale dei criteri.

> [!div class="nextstepaction"]
> [Definire i criteri aziendali](./policy-definition.md)
