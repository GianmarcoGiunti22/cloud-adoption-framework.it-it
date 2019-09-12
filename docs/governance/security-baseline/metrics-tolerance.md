---
title: 'Baseline di sicurezza: metriche, indicatori e tolleranza ai rischi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Baseline di sicurezza: metriche, indicatori e tolleranza ai rischi'
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2dd35082f24536c42609c415bfae7b658161e8fb
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70823521"
---
# <a name="security-baseline-metrics-indicators-and-risk-tolerance"></a>Baseline di sicurezza: metriche, indicatori e tolleranza ai rischi

Questo articolo è progettato per aiutare l'utente a quantificare la tolleranza al rischio aziendale in relazione alla Baseline di sicurezza. La definizione di metriche e indicatori consente di creare un business case per effettuare un investimento riguardo alla disciplina Baseline di sicurezza.

## <a name="metrics"></a>metrics

La Baseline di sicurezza si concentra in genere sull'identificazione di potenziali vulnerabilità nelle distribuzioni cloud. Nell'ambito dell'analisi dei rischi è necessario raccogliere dati relativi all'ambiente di sicurezza per determinare l'entità dei rischi e l'importanza degli investimenti nella governance della baseline di sicurezza per le distribuzioni cloud pianificate.

Ogni organizzazione dispone di ambienti di sicurezza e requisiti diversi, oltre a potenziali origini di dati sulla sicurezza diverse. Sono riportati alcuni esempi di metriche utili che è necessario raccogliere per valutare la tolleranza ai rischi all'interno della disciplina Baseline di sicurezza:

- **Classificazione dei dati:** Numero di servizi e dati archiviati nel cloud non classificati in base a privacy, conformità o standard di impatto aziendale dell'organizzazione.
- **Numero di archivi dati sensibili:** Numero di endpoint o database di archiviazione che contengono dati sensibili e che devono essere protetti.
- **Numero di archivi dati non crittografati:** Numero di archivi dati sensibili che non sono crittografati.
- **Superficie di attacco:** Numero totale di origini dati, servizi e applicazioni che saranno ospitate nel cloud. Che percentuale di origini dati è classificata come sensibile? Che percentuale di applicazioni e servizi è cruciale?
- **Standard interessati:** Numero di standard di sicurezza definiti dal team di sicurezza.
- **Risorse coperte:** Risorse distribuite coperte da standard di sicurezza.
- **Conformità agli standard generali:** Percentuale di conformità agli standard di sicurezza.
- **Attacchi per gravità:** Quanti tentativi coordinati di interrompere i servizi ospitati nel cloud, ad esempio tramite attacchi Distributed Denial of Service (DDoS), subisce l'infrastruttura? Quali sono le dimensioni e la gravità di questi attacchi?
- **Malware Protection:** Percentuale di macchine virtuali (VM) distribuite che dispongono di tutto il software anti-malware, firewall o altro software di sicurezza necessario.
- **Latenza patch:** Quanto tempo è trascorso dall'applicazione di patch per il sistema operativo e software nelle macchine virtuali.
- **Raccomandazioni sull'integrità della sicurezza:** Numero di elementi consigliati relativi al software di sicurezza per la risoluzione di standard di integrità per le risorse distribuite, organizzati in base alla gravità.

## <a name="risk-tolerance-indicators"></a>Indicatori sulla tolleranza ai rischi

Le piattaforme cloud offrono un set di baseline di funzionalità che consente a piccoli team di distribuzione di configurare le impostazioni di sicurezza di base senza una pianificazione approfondita aggiuntiva. Di conseguenza, i carichi di lavoro di sviluppo/test o sperimentali di piccole dimensioni che non includono dati sensibili rappresentano un livello di rischio relativamente basso e probabilmente non hanno bisogno di molto secondo i criteri di base della sicurezza formale. Tuttavia, i rischi per la sicurezza aumentano non appena dati importanti o funzionalità cruciali vengono spostate nel cloud, mentre la tolleranza per tali rischi diminuisce rapidamente. Maggiore è la quantità di funzionalità e dati che vengono distribuiti nel cloud, più è probabile la necessità di un maggiore investimento nella disciplina Baseline di sicurezza.

Nelle prime fasi di adozione del cloud è necessario lavorare con il team addetto alla sicurezza IT e con gli azionisti aziendali per identificare i [rischi aziendali](business-risks.md) correlati alla sicurezza, quindi definire una baseline accettabile per la tolleranza ai rischi di sicurezza. Questa sezione del Framework di adozione del cloud fornisce esempi, ma i rischi e le basi di riferimento dettagliati per la società o le distribuzioni potrebbero essere diversi.

Dopo aver creato una baseline, è necessario stabilire i benchmark minimi che rappresentano un aumento inaccettabile dei rischi identificati. Questi benchmark fungono da trigger per quando è necessario intervenire per correggere questi rischi. Di seguito sono riportati alcuni esempi del modo in cui le metriche di sicurezza, ad esempio quelle descritte in precedenza, possono giustificare un maggiore investimento nella disciplina Baseline di sicurezza.

- **Attivazione dei carichi di lavoro di importanza critica.** Una società che distribuisce carichi di lavoro cruciali nel cloud deve investire nella disciplina Baseline di sicurezza per evitare potenziali interruzioni del servizio o esposizione di dati sensibili.
- **Trigger dati protetti.** Una società che ospita nel cloud dati che possono essere classificati come riservati, privati o comunque soggetti a problemi normativi. È necessaria una disciplina Baseline di sicurezza per garantire che tali dati non siano soggetti a rischi di perdita, esposizione o furto.
- **Trigger External attacks.** Una società che sperimenta gravi attacchi contro la loro infrastruttura di rete _x_ volte al mese può trarre vantaggio dalla disciplina della linea di base di sicurezza.
- **Trigger di conformità agli standard.** Una società con più dell' _x%_ di risorse per la conformità agli standard di sicurezza deve investire nella disciplina della linea di base di sicurezza per garantire che gli standard vengano applicati in modo coerente nell'infrastruttura IT.
- **Trigger dimensioni cloud.** Società che ospita più di _x_ applicazioni, servizi o origini dati. Le distribuzioni cloud di grandi dimensioni possono trarre vantaggio dagli investimenti nella disciplina Baseline di sicurezza per garantire che la superficie di attacco complessiva sia adeguatamente protetta da accessi non autorizzati o altre minacce esterne.
- **Trigger di conformità del software di sicurezza.** Una società in cui è installato un software di protezione inferiore all' _x%_ delle macchine virtuali distribuite. È possibile usare una disciplina Baseline di sicurezza per garantire che il software sia installato in modo coerente in tutto il software.
- **Trigger di applicazione di patch.** Azienda in cui sono state distribuite le macchine virtuali o i servizi in cui le patch del sistema operativo o del software non sono state applicate negli ultimi _x_ giorni. È possibile usare una disciplina Baseline di sicurezza per garantire che l'applicazione di patch venga mantenuta aggiornata all'interno di una pianificazione obbligatoria.
- **Incentrato sulla sicurezza.** Alcune società dispongono di requisiti rigorosi in termini di sicurezza e riservatezza, anche per carichi di lavoro di test e sperimentali. Queste società hanno la necessità di investire nella disciplina Baseline di sicurezza prima di poter iniziare qualsiasi distribuzione.

Le metriche e i trigger esatti usati per misurare la tolleranza ai rischi e il livello di investimento nella disciplina della linea di base di sicurezza saranno specifici per l'organizzazione, ma gli esempi precedenti dovrebbero fungere da base utile per discutere nel team di governance del cloud.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare le metriche e gli indicatori di tolleranza in linea con il piano di adozione del cloud attuale.

Esaminare i criteri di base di sicurezza di esempio come punto di partenza per sviluppare criteri che risolvono i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

> [!div class="nextstepaction"]
> [Esaminare i criteri di esempio](./policy-statements.md)
