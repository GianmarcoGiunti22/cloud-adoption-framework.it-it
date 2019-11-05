---
title: Esempi di istruzioni dei criteri di Accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esempi di istruzioni dei criteri di Accelerazione della distribuzione
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a307c29a640332fdf82a69ec06eab27589f77304
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566357"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Esempi di istruzioni dei criteri di Accelerazione della distribuzione

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà indirizzato da questo criterio.
- **Istruzione per i criteri:** Una chiara spiegazione di riepilogo dei requisiti dei criteri.
- **Opzioni di progettazione:** Raccomandazioni di utilità pratica, specifiche o altre istruzioni che i team IT e gli sviluppatori possono usare per l'implementazione dei criteri.

Le istruzioni dei criteri di esempio seguenti riguardano i rischi aziendali comuni relativi alla configurazione. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dipendenza dalla distribuzione manuale o configurazione dei sistemi

**Rischio tecnico:** Basandosi sull'intervento umano durante la distribuzione o la configurazione aumenta la probabilità di errori umani e riduce la ripetibilità e la prevedibilità delle distribuzioni e della configurazione di sistema. Tale operazione comporta in genere anche alla distribuzione più lenta delle risorse di sistema.

**Istruzione per i criteri:** Tutti gli asset distribuiti nel cloud devono essere distribuiti usando modelli o script di automazione laddove possibile.

**Opzioni di progettazione potenziali:** i [modelli Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) offrono un approccio di infrastruttura come codice per la distribuzione delle risorse in Azure. È anche possibile usare la funzione di [bonifica](https://docs.microsoft.com/azure/terraform/terraform-overview) come strumento di distribuzione locale coerente e basato sul cloud.

## <a name="lack-of-visibility-into-system-issues"></a>Mancanza di visibilità per problemi di sistema

**Rischio tecnico:** Il monitoraggio e la diagnostica insufficienti per i sistemi aziendali impediscono al personale operativo di identificare e correggere i problemi prima che si verifichi un'interruzione del sistema e possono aumentare significativamente il tempo necessario per risolvere correttamente un'interruzione del servizio.

**Istruzione per i criteri:** Verranno implementati i criteri seguenti:

- Misure di diagnostica e metriche chiave saranno identificate per tutti i componenti e sistemi di produzione, gli strumenti di monitoraggio e diagnostica verranno applicati a questi sistemi e monitorati regolarmente dal personale operativo.
- Le operazioni considereranno l'utilizzo degli strumenti di monitoraggio e diagnostica in ambienti non di produzione, ad esempio staging e QA, per identificare i problemi di sistema prima che si verifichino nell'ambiente di produzione.

**Opzioni di progettazione potenziali:** [monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor), che include anche log Analytics e Application Insights, fornisce strumenti per la raccolta e l'analisi dei dati di telemetria per comprendere il modo in cui le applicazioni vengono eseguite e proattive identificare i problemi che interessano le risorse e le risorse da cui dipendono. Inoltre, il [log attività di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) segnala tutte le modifiche apportate a livello di piattaforma e deve essere monitorato/controllato per le modifiche non conformi.

## <a name="configuration-security-reviews"></a>Verifiche di protezione della configurazione

**Rischio tecnico:** Nel tempo, le nuove minacce per la sicurezza o le preoccupazioni possono aumentare i rischi di accesso non autorizzato alle risorse protette.

**Istruzione per i criteri:** I processi di governance del cloud devono includere la revisione mensile con i team di gestione della configurazione per identificare gli attori dannosi o i modelli di utilizzo che devono essere evitati dalla configurazione delle

**Possibili opzioni di progettazione:** Stabilire una riunione di revisione della sicurezza mensile che includa i membri del team di governance e il personale IT responsabile della configurazione delle applicazioni e delle risorse cloud. Esaminare i dati e le metriche di sicurezza esistenti per stabilire i gap nei criteri e negli strumenti di accelerazione della distribuzione corrente e aggiornare i criteri per correggere eventuali nuovi rischi.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per elaborare criteri applicabili a rischi aziendali specifici, in linea con i piani di adozione del cloud.

Per iniziare a sviluppare le proprie istruzioni di criteri personalizzate correlate alla gestione delle identità, scaricare [Identity Baseline template](../identity-baseline/template.md) (modello di Baseline di identità).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Accelerazione della distribuzione.

> [!div class="nextstepaction"]
> [Stabilire i processi di conformità ai criteri](./compliance-processes.md)
