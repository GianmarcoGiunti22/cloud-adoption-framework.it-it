---
title: 'Guida alla governance per le aziende complesse: Descrizione del supporto'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Questa descrizione stabilisce un caso d'uso per la governance durante un percorso di adozione del cloud di un'azienda complessa.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: acc82a629adf32cd9a7bfe638b0ad176f1de7933
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967664"
---
# <a name="governance-guide-for-complex-enterprises-the-supporting-narrative"></a>Guida alla governance per le aziende complesse: Descrizione del supporto

La descrizione seguente stabilisce un caso d'uso per la [governance durante il percorso di adozione cloud di un'azienda complessa](./index.md). Prima di agire sulle raccomandazioni nella Guida, è importante comprendere i presupposti e i ragionamenti che si riflettono in questa descrizione. È quindi possibile allineare meglio la strategia di governance al percorso di adozione del cloud dell'organizzazione.

## <a name="back-story"></a>Scenario

I clienti stanno chiedendo un'esperienza migliore di interazione con questa società. L'esperienza attuale causato un'erosione del mercato, spingendo il consiglio di amministrazione ad assumere un Chief Digital Officer (CDO). Il CDO sta lavorando con i reparti marketing e vendite per promuovere una trasformazione digitale che consentirà di offrire esperienze migliorate. Inoltre, diverse business unit hanno recentemente assunto data scientist per il data farming e per migliorare molte delle esperienze manuali attraverso l'apprendimento e la stima. Ove possibile, l'IT supporta queste iniziative. Tuttavia, sono in corso attività "IT ombra" al di fuori dei necessari controlli di governance e di sicurezza.

L'organizzazione IT sta anche affrontando problematiche specifiche. Il reparto Finanza sta pianificando continue riduzioni del budget IT nei prossimi cinque anni, con conseguenti tagli di spesa necessari a partire da quest'anno. Di contro, il GDPR e altri requisiti di sovranità sui dati stanno costringendo l'IT a investire in asset in altri paesi per localizzare i dati. Due dei data center esistenti sono in ritardo sull'aggiornamento dell'hardware e questo causa ulteriori problemi in termini di soddisfazione dei dipendenti e dei clienti. Altri tre data center richiedono aggiornamenti hardware durante l'esecuzione del piano di cinque anni. Il CFO sta spingendo il CIO a considerare il cloud come alternativa per quei data center, per sbloccare spese in conto capitale.

Il CIO ha idee innovative che potrebbero aiutare la società, ma le attività sue e dei suoi team sono limitate a risolvere le emergenze e controllare i costi. Durante un pranzo con il CDO e uno dei responsabili delle business unit, la conversazione sulla migrazione cloud ha suscitato l'interesse dei colleghi del CIO. I tre responsabili intendono supportarsi reciprocamente usando il cloud per raggiungere i propri obiettivi di business e hanno intrapreso le fasi di esplorazione e pianificazione dell'adozione del cloud.

## <a name="business-characteristics"></a>Caratteristiche dell'azienda

Il profilo di business della società è il seguente:

- Le vendite e le operazioni si estendono su più aree geografiche con clienti internazionali in più mercati.
- L'azienda è cresciuta attraverso l'acquisizione e opera attraverso tre business unit in funzione della base di clienti di destinazione. La determinazione del budget è un intreccio complesso tra le esigenze di business unit e funzioni.
- Per l'azienda, la maggior parte delle attività IT è considerata come un deflusso di capitali o un centro di costo.

## <a name="current-state"></a>Stato corrente

Questo è lo stato corrente delle attività IT e cloud della società:

- L'IT gestisce più di 20 data center di proprietà privata in tutto il mondo.
- A causa della crescita organica e di più aree geografiche, esistono alcuni team IT con requisiti di conformità e sovranità dei dati univoci che influiscano su una singola unità aziendale che opera all'interno di una specifica area geografica.
- Ogni data center è connesso da una serie di linee dedicate regionali, che creano una rete WAN ad accoppiamento debole.
- L'accesso al cloud è avvenuto tramite la migrazione di tutti gli account di posta elettronica degli utenti finali a Office 365. Questa migrazione è stata completata più di sei mesi fa. Da allora, solo pochi altri asset IT sono stati distribuiti nel cloud.
- Il team di sviluppo primario di CDO sta lavorando in una capacità di sviluppo/test per ottenere informazioni sulle funzionalità native del cloud.
- Una business unit sta sperimentando implementazioni di Big Data nel cloud. Il team di business intelligence all'interno del reparto IT partecipa all'iniziativa.
- I criteri di governance IT esistenti affermano che i dati personali dei clienti e i dati finanziari devono essere ospitati in asset di proprietà dell'azienda. Questi criteri impediscono l'adozione del cloud per le app cruciali o i dati protetti.
- Gli investimenti IT sono controllati in gran parte dalle spese di capitale. e sono pianificati di anno in anno. Spesso includono piani di manutenzione ordinaria e cicli di aggiornamento prestabiliti da tre a cinque anni a seconda del data center.
- Gli investimenti in tecnologia non allineati con il piano annuale vengono affrontati per la maggior parte con iniziative IT ombra. In genere queste iniziative sono gestite dalle business unit e finanziate con le spese operative della business unit.

## <a name="future-state"></a>Stato futuro

Sono previste le modifiche seguenti per gli anni successivi:

- Il CIO rappresenta un impegno a modernizzare i criteri sui dati personali e finanziari per supportare obiettivi futuri. Due membri del team di governance IT hanno visibilità sull'iniziativa.
- CIO vuole usare la migrazione cloud come funzione di forzatura per migliorare la coerenza e la stabilità tra le business unit e le aree geografiche. Tuttavia, lo stato futuro deve rispettare i requisiti di conformità esterni che richiederebbero una deviazione dagli approcci standard da parte di specifici team IT.
- Se gli esperimenti iniziali dei team di sviluppo applicazioni e di business intelligence mostreranno indicatori di successo, ognuno dei due team intende rilasciare nel cloud soluzioni di produzione su scala ridotta nei prossimi 24 mesi.
- Il CIO e il CFO hanno incaricato un architetto e il Vicepresidente Infrastrutture di creare un'analisi dei costi e uno studio di fattibilità. Queste iniziative consentiranno di determinare se l'azienda può e dovrebbe spostare 5.000 asset nel cloud nei 36 mesi successivi. Una migrazione corretta consentirebbe al CIO di eliminare due data center, riducendo i costi di oltre 100 milioni di dollari nel corso del piano quinquennale. Se tre o quattro data center possono ottenere risultati simili, il budget sarà di nuovo in attivo e il CIO disporrà di risorse per finanziare iniziative più innovative.
    costi ![On-locali rispetto ai costi di Azure che dimostrano un ritorno di $100M USD nei prossimi cinque anni @ no__t-1
- Oltre a questo risparmio sui costi, la società prevede di modificare la gestione di alcuni investimenti IT riposizionando le spese di capitale vincolate come una spesa operativa al suo interno. Questa modifica consentirà un maggiore controllo dei costi, che permetterà al reparto IT di accelerare altri progetti pianificati.

## <a name="next-steps"></a>Passaggi successivi

La società ha elaborato criteri aziendali per strutturare l'implementazione della governance. Tali criteri aziendali guidano molte delle decisioni tecniche.

> [!div class="nextstepaction"]
> [Esaminare i criteri aziendali iniziali](./initial-corporate-policy.md)
