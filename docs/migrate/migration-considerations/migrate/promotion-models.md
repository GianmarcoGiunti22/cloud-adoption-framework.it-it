---
title: Modelli di promozione - Promozione, processo di gestione temporanea o modello in più fasi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sull'impatto della promozione sulle attività di migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: b251e5159f6e6728e0b5a7ce807eaba0ea85696a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548441"
---
# <a name="promotion-models---single-step-staged-or-flight"></a>Modelli di promozione - singolo passaggio, gestione temporanea o anteprima

La migrazione di un carico di lavoro viene spesso descritta come un'attività singola. In realtà si tratta di una raccolta di attività più piccole che facilitano lo spostamento di un asset digitale nel cloud. Una delle ultime attività in una migrazione è la promozione di un asset alla produzione. La promozione è il punto in cui il sistema di produzione cambia per gli utenti finali. Spesso può comportare semplicemente la modifica del routing di rete con il reindirizzamento degli utenti finali al nuovo asset di produzione. La promozione è anche il punto in cui le operazioni IT o le operazioni cloud spostano l'obiettivo dei processi di gestione operativa dal sistema di produzione precedente ai nuovi sistemi di produzione.

Sono disponibili diversi modelli di promozione. Questo articolo ne illustra tre tra quelli più comuni usati nelle migrazioni cloud. La scelta di un modello di promozione modifica le attività visibili nei processi di migrazione e ottimizzazione. Il modello di promozione pertanto dovrebbe essere deciso all'inizio di un rilascio.

## <a name="impact-of-promotion-model-on-migrate-and-optimize-activities"></a>Impatto del modello di promozione sulle attività di migrazione e ottimizzazione

In ognuno dei modelli di promozione seguenti lo strumento di migrazione scelto replica e sottopone al processo di gestione temporanea gli asset che costituiscono un carico di lavoro. Dopo il processo di gestione temporanea, ogni modello considera l'asset in modo leggermente diverso.

- **Promozione in un singolo passaggio.** In un modello di promozione in un *singolo passaggio* il processo di gestione temporanea ricopre anche il ruolo del processo di promozione. Dopo che tutti gli asset sono stati sottoposti al processo di gestione temporanea, il traffico degli utenti finali viene reindirizzato e il processo di gestione temporanea si trasforma in produzione. In tal caso, la promozione è parte del processo di migrazione. Questo è il modello di migrazione più veloce. Questo approccio tuttavia rende più difficile l'integrazione di solide attività di test o di ottimizzazione. Questo tipo di modello presuppone inoltre che il team di migrazione abbia accesso all'ambiente di gestione temporanea e di produzione, il che compromette i requisiti di separazione dei compiti in alcuni ambienti.
  > [!NOTE]
  >Il sommario di questo sito elenca l'attività di promozione come parte del processo di ottimizzazione. In un modello in un singolo passaggio la promozione si verifica durante il processo di migrazione. Quando si usa questo modello, i ruoli e le responsabilità devono essere aggiornati per riflettere questa caratteristica.
- **Con gestione temporanea.** In un modello di promozione con *gestione temporanea* il carico di lavoro viene considerato migrato dopo che è stato sottoposto al processo di gestione temporanea, ma non è ancora stato promosso. Prima della promozione, il carico di lavoro migrato viene sottoposto a una serie di test di prestazioni, test aziendali e modifiche di ottimizzazione. Viene quindi promosso in una data futura insieme a un piano di test aziendale. Questo approccio migliora il bilanciamento tra costi e prestazioni, facilitando al tempo stesso l'ottenimento della convalida aziendale.
- **In più fasi.** Il modello di promozione *in più fasi* è una combinazione dei modelli in un singolo passaggio e con gestione temporanea. In un modello di promozione in più fasi gli asset nel carico di lavoro vengono considerati come asset di produzione dopo il passaggio al processo di gestione temporanea. Dopo un periodo concentrato di test automatizzati, il traffico di produzione viene indirizzato al carico di lavoro. Si tratta tuttavia di un subset del traffico. Questo traffico funge da prima fase di produzione e test. Supponendo che il carico di lavoro venga eseguito dal punto di vista delle funzionalità e delle prestazioni, viene eseguita la migrazione di traffico aggiuntivo. Dopo che tutto il traffico di produzione è stato spostato nei nuovi asset, il carico di lavoro viene considerato completamente promosso.

Il modello di promozione scelto influisce sulla sequenza di attività da eseguire, nonché sui ruoli e sulle responsabilità del team di adozione del cloud. Può anche avere impatto sulla composizione di uno o più sprint.

## <a name="single-step-promotion"></a>Promozione in un singolo passaggio

Questo modello usa gli strumenti di automazione della migrazione per replicare, sottoporre al processo di gestione temporanea e promuovere gli asset. Gli asset vengono replicati in un ambiente di gestione temporanea indipendente controllato dallo strumento di migrazione. Dopo la replica di tutti gli asset, lo strumento può eseguire un processo automatizzato per promuovere in un singolo passaggio gli asset nella sottoscrizione scelta. Nel corso del processo di gestione temporanea, lo strumento continua la replica dell'asset, riducendo al minimo la perdita di dati tra i due ambienti. Dopo la promozione di un asset, il collegamento tra il sistema di origine e il sistema replicato viene interrotto. Con questo approccio, se vengono apportate modifiche aggiuntive nei sistemi di origine iniziali, tali modifiche andranno perse.

**Vantaggi.** I vantaggi di questo approccio includono:

- Questo modello introduce un minor numero di modifiche nei sistemi di destinazione.
- La replica continua riduce al minimo la perdita di dati.
- Se un processo di gestione temporanea ha esito negativo, può essere eliminato e ripetuto rapidamente.
- La replica e i test di gestione temporanea ripetuti consentono un processo di script e test incrementale.

**Svantaggi.** Gli aspetti negativi di questo approccio includono:

- Gli asset con gestione temporanea nella sandbox isolata dagli strumenti non consentono modelli di test complessi.
- Durante la replica, lo strumento di migrazione usa la larghezza di banda nel data center locale. L'applicazione del processo di gestione temporanea a un volume elevato di asset per un periodo prolungato ha un impatto esponenziale sulla larghezza di banda disponibile, danneggiando il processo di migrazione e riducendo potenzialmente le prestazioni dei carichi di lavoro di produzione nell'ambiente locale.

## <a name="staged-promotion"></a>Promozione con gestione temporanea

In questo modello la sandbox del processo di gestione temporanea gestita dallo strumento di migrazione viene usata per scopi di test limitati. Gli asset replicati vengono quindi distribuiti nell'ambiente cloud, che funge da ambiente di gestione temporanea esteso. Gli asset migrati vengono eseguiti nel cloud, mentre gli asset aggiuntivi vengono replicati e sottoposti a gestione temporanea e quindi a migrazione. Quando i carichi di lavoro diventano disponibili, vengono avviati test più completi. Dopo che è stata eseguita la migrazione di tutti gli asset associati a una sottoscrizione, la sottoscrizione e tutti i carichi di lavoro ospitati vengono promossi alla produzione. In questo scenario non viene apportata alcuna modifica ai carichi di lavoro durante il processo di promozione. Al contrario, le modifiche tendono a essere a livello di rete e di identità, indirizzando gli utenti al nuovo ambiente e revocando l'accesso del team di adozione del cloud.

**Vantaggi.** I vantaggi di questo approccio includono:

- Questo modello offre opportunità di test aziendali più accurati.
- Il carico di lavoro può essere studiato più accuratamente per ottimizzare le prestazioni e i costi degli asset.
- È possibile replicare un numero maggiore di asset in limiti di tempo e larghezza di banda simili.

**Svantaggi.** Gli aspetti negativi di questo approccio includono:

- Lo strumento di migrazione scelto non può semplificare la replica continuativa dopo la migrazione.
- Per sincronizzare le piattaforme dati durante l'intervallo di tempo del processo di gestione temporanea, è necessario un mezzo di replica dati secondario.

## <a name="flight-promotion"></a>Promozione in più fasi

Questo modello è simile al modello di promozione con gestione temporanea. Esiste tuttavia una differenza fondamentale. Quando la sottoscrizione è pronta per la promozione, il routing degli utenti finali avviene in processi di gestione temporanea o in più fasi. A ogni fase, altri utenti vengono reindirizzati ai sistemi di produzione.

**Vantaggi.** I vantaggi di questo approccio includono:

- Questo modello riduce i rischi associati a un'attività di migrazione o promozione estesa. Gli errori nella soluzione migrata possono essere identificati con un impatto minore sui processi aziendali.
- Consente di monitorare le richieste di prestazioni del carico di lavoro nell'ambiente cloud per un periodo di tempo prolungato, aumentando l'accuratezza delle decisioni di dimensionamento degli asset.
- È possibile replicare un numero maggiore di asset in limiti di tempo e larghezza di banda simili.

**Svantaggi.** Gli aspetti negativi di questo approccio includono:

- Lo strumento di migrazione scelto non può semplificare la replica continuativa dopo la migrazione.
- Per sincronizzare le piattaforme dati durante l'intervallo di tempo del processo di gestione temporanea, è necessario un mezzo di replica dati secondario.

## <a name="next-steps"></a>Passaggi successivi

Dopo che il team di adozione del cloud ha definito e accettato un modello di promozione, può iniziare la [correzione degli asset](./remediate.md).

> [!div class="nextstepaction"]
> [Correzione degli asset prima della migrazione](./remediate.md)
