---
title: Metriche di Coerenza delle risorse, indicatori e tolleranza al rischio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Metriche di Coerenza delle risorse, indicatori e tolleranza al rischio
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 387cc7b320e50628e2f10c25ab49f200878d3636
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222956"
---
# <a name="resource-consistency-metrics-indicators-and-risk-tolerance"></a>Metriche di Coerenza delle risorse, indicatori e tolleranza al rischio

Questo articolo consente di quantificare la tolleranza ai rischi aziendali in relazione alla coerenza delle risorse. La definizione di metriche e indicatori consente di creare un business case per effettuare un investimento riguardo alla disciplina Coerenza delle risorse.

## <a name="metrics"></a>metrics

La disciplina Coerenza delle risorse è incentrata sulla capacità di affrontare i rischi correlati alla gestione operativa delle distribuzioni cloud. Nell'ambito dell'analisi dei rischi è necessario raccogliere i dati relativi alle operazioni IT per determinare l'entità dei rischi e l'importanza degli investimenti nella Coerenza delle risorse per le distribuzioni cloud pianificate.

Ogni organizzazione dispone di diversi scenari operativi, ma gli elementi seguenti rappresentano esempi utili delle metriche da raccogliere durante la valutazione della tolleranza al rischio riguardo alla disciplina Coerenza delle risorse:

- **Asset cloud.** Numero totale delle risorse distribuite sul cloud.
- **Risorse senza tag.** Numero di risorse prive di accounting obbligatorio, impatto aziendale o tag dell'organizzazione.
- **Asset sottoutilizzati.** Numero di risorse in cui la memoria, la CPU o le funzionalità di rete sono tutte costantemente sottoutilizzate.
- **Esaurimento delle risorse.** Numero di risorse in cui memoria, CPU o funzionalità di rete sono state esaurite dal carico.
- **Tempo di risorse.** Tempo trascorso dall'ultima implementazione o modifica della risorsa.
- **Macchine virtuali in condizioni critiche.** Numero di macchine virtuali distribuite dove sono stati rilevati uno o più problemi critici che devono essere risolti per ripristinarne il normale funzionamento.
- **Avvisi in base alla gravità.** Numero totale di avvisi su un asset distribuito, suddivisi per livello di gravità.
- **Collegamenti di rete non integri.** Numero di risorse con problemi di connettività di rete.
- **Endpoint di servizio non integri.** Numero di problemi con gli endpoint di rete esterni.
- **Eventi imprevisti di integrità del servizio del provider cloud.** Numero di interruzioni o problemi di prestazione causati dal provider cloud.
- **Contratti di servizio.** Possono includere gli impegni di Microsoft in termini di tempo di attività e connettività dei servizi di Azure e gli impegni dell'azienda nei confronti di clienti interni ed esterni.
- **Disponibilità del servizio.** Percentuale del tempo effettivo dei carichi di lavoro ospitati nel cloud rispetto al tempo di attività previsto.
- **Obiettivo del tempo di ripristino (RTO).** Il tempo massimo accettabile in cui un'applicazione può rimanere non disponibile dopo un evento imprevisto.
- **Obiettivo del punto di ripristino (RPO).** La durata massima di perdita dei dati accettabile durante un'emergenza. Per esempio, se si archiviano i dati in un singolo database, senza replica in altri database, e si eseguono backup orari, si potrebbero perdere fino a un'ora di dati.
- **Tempo medio per il ripristino (MTTR).** Il tempo medio necessario per il ripristino di un componente dopo un guasto.
- **Tempo medio tra gli errori (MTBF).** L'intervallo di tempo in cui è ragionevole aspettarsi che un componente rimanga in esecuzione tra un'interruzione del servizio e l'altra. Questa metrica può essere utile per calcolare la frequenza con cui un servizio non sarà più disponibile.
- **Stato backup.** Numero di backup attivamente in fase di sincronizzazione.
- **Integrità ripristino.** Numero di operazioni di ripristino eseguite correttamente.

## <a name="risk-tolerance-indicators"></a>Indicatori sulla tolleranza al rischio

Le piattaforme cloud offrono un set di funzionalità baseline che consentono la distribuzione di team per gestire efficacemente le distribuzioni di piccole dimensioni senza una pianificazione o processi approfonditi aggiuntivi. Di conseguenza, i primi carichi di lavoro sperimentali o di Sviluppo/test che includono asset basati sul cloud rappresentano un livello di rischio basso e probabilmente non necessitano di molto in termini di criteri formali di Coerenza delle risorse.

Tuttavia, man mano che aumentano le dimensioni del cloud diventa molto più difficile la gestione delle complessità degli asset. Con altri asset nel cloud, la capacità di identificare il proprietario delle risorse e il controllo delle risorse diventa fondamentale per ridurre al minimo i rischi. Man mano che aumentano i carichi di lavoro cruciali distribuiti nel cloud, il tempo di attività di servizio diventa più importante e la tolleranza per le interruzioni del servizio può essere ridotta rapidamente.

Nelle prime fasi di adozione del cloud è necessario lavorare con il team addetto alla sicurezza IT e con gli azionisti aziendali per identificare i [rischi commerciali](./business-risks.md) correlati alla Coerenza delle risorse, quindi definire una baseline accettabile per la tolleranza ai rischi di sicurezza. Questa sezione del Framework di adozione del cloud fornisce esempi, ma i rischi e le basi di riferimento dettagliati per la società o le distribuzioni potrebbero essere diversi.

Dopo aver creato una baseline, è necessario stabilire i benchmark minimi che rappresentano un aumento inaccettabile dei rischi identificati. Questi benchmark fungono da trigger per quando è necessario intervenire per correggere questi rischi. Di seguito sono riportati alcuni esempi del modo in cui le metriche operative, ad esempio quelle descritte in precedenza, possono giustificare un maggiore investimento nella disciplina Coerenza delle risorse.

- **Tag e trigger di denominazione.** Una società con più di _x_ risorse prive di informazioni obbligatorie per l'assegnazione di tag o non rispettando gli standard di denominazione dovrebbe considerare l'investimento nella disciplina della coerenza delle risorse per migliorare questi standard e garantire la coerenza dell'applicazione a asset distribuiti nel cloud.
- **Trigger di risorse con provisioning eccessivo.** Se una società dispone di più dell' _x%_ di risorse che usano regolarmente piccole quantità di memoria disponibile, CPU o funzionalità di rete, è consigliabile investire nella disciplina della coerenza delle risorse per ottimizzare l'utilizzo delle risorse per questi elementi.
- **Trigger risorse sottoposte a provisioning.** Se una società ha più del _x%_ di risorse che esauriscono regolarmente la maggior parte delle capacità di memoria, CPU o rete disponibili, è consigliabile investire nella disciplina della coerenza delle risorse per garantire che questi asset dispongano delle risorse necessarie per prevenire interruzioni del servizio.
- **Trigger Age della risorsa.** Una società con più di _x_ risorse che non sono state aggiornate in oltre _y_ mesi può trarre vantaggio dall'investimento nella disciplina della coerenza delle risorse per garantire che le risorse attive siano applicate a patch e integre, durante il ritiro obsolete o in caso contrario, risorse inutilizzate.
- **Trigger del contratto di servizio.** Una società che non è in grado di soddisfare i propri contratti di servizio con i clienti esterni o i partner interni deve investire nella disciplina di accelerazione della distribuzione per ridurre i tempi di inattività del sistema.
- **Trigger del tempo di ripristino.** Se un'azienda supera le soglie da rispettare per il tempo di ripristino in seguito un errore di sistema, dovrebbe investire per migliorare la disciplina Accelerazione della distribuzione e la progettazione dei sistemi in modo da ridurre o eliminare i guasti o l'effetto dei tempi di inattività dei singoli componenti.
- **Trigger di integrità della macchina virtuale.** Una società con più di _x%_ di macchine virtuali che riscontrano un problema di integrità critico deve investire nella disciplina della coerenza delle risorse per identificare i problemi e migliorare la stabilità della macchina virtuale.
- **Trigger di integrità della rete.** Una società con più dell' _x%_ di subnet di rete o endpoint che riscontrano problemi di connettività deve investire nella disciplina della coerenza delle risorse per identificare e risolvere i problemi di rete.
- **Trigger di code coverage backup.** Una società con la _percentuale_ di risorse mission-critical senza backup aggiornati potrebbe trarre vantaggio da un investimento maggiore nella disciplina della coerenza delle risorse per garantire una strategia di backup coerente.
- **Trigger di integrità di backup.** Una società che ha riscontrato un errore superiore alla _x%_ delle operazioni di ripristino dovrebbe investire nella disciplina della coerenza delle risorse per identificare i problemi relativi al backup e garantire la protezione delle risorse importanti.

Le metriche e i trigger esatti usati per misurare la tolleranza ai rischi e il livello di investimento nella disciplina della coerenza delle risorse saranno specifici per l'organizzazione, ma gli esempi precedenti dovrebbero fungere da base utile per discutere nell'ambito della governance del cloud Team.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare le metriche e gli indicatori di tolleranza in linea con il piano di adozione del cloud attuale.

Esaminare i criteri di coerenza delle risorse di esempio come punto di partenza per sviluppare criteri che risolvono i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

> [!div class="nextstepaction"]
> [Esaminare i criteri di esempio](./policy-statements.md)
