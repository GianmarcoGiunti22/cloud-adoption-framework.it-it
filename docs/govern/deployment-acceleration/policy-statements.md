---
title: Esempi di istruzioni dei criteri di Accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esempi di istruzioni dei criteri di Accelerazione della distribuzione
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4a2b1666332ca884dfb95b2b2372f3b5518bd635
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028180"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Esempi di istruzioni dei criteri di Accelerazione della distribuzione

Le istruzioni individuali dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazione seguenti:

- **Rischi tecnici.** Riepilogo del rischio che verrà risolto da questi criteri.
- **Istruzione dei criteri.** Una spiegazione chiara e riepilogativa dei requisiti dei criteri.
- **Opzioni di progettazione.** Suggerimenti pratici, specifiche o altre linee guida che i team IT e gli sviluppatori possono usare quando implementano i criteri.

Le istruzioni dei criteri di esempio seguenti riguardano i rischi aziendali comuni relativi alla configurazione. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dipendenza dalla distribuzione manuale o configurazione dei sistemi

**Rischio tecnico:** Basarsi sull'intervento dell'utente durante la distribuzione o la configurazione aumenta la probabilità di errori umani e riduce ripetibilità e prevedibilità della configurazione e delle distribuzioni del sistema. Tale operazione comporta in genere anche alla distribuzione più lenta delle risorse di sistema.

**Definizione dei criteri**: Tutte le risorse distribuite nel cloud devono essere distribuite tramite modelli o script di automazione laddove possibile.

**Possibili opzioni di progettazione:** [I modelli di Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#template-deployment) forniscono un approccio di infrastruttura come codice alla distribuzione delle risorse in Azure. [Blocchi predefiniti di Azure](https://github.com/mspnp/template-building-blocks/wiki) fornisce uno strumento da riga di comando e set di modelli di Resource Manager progettati per semplificare la distribuzione delle risorse di Azure.

## <a name="lack-of-visibility-into-system-issues"></a>Mancanza di visibilità per problemi di sistema

**Rischio tecnico:** Monitoraggio e diagnostica insufficienti per i sistemi aziendali impediscono al personale operativo di identificare, monitorare e aggiornare i problemi prima che si verifichi un'interruzione del sistema; ciò può aumentare notevolmente il tempo necessario per risolvere in modo corretto un'interruzione del servizio.

**Definizione dei criteri**: verranno implementati i criteri seguenti:

- Misure di diagnostica e metriche chiave saranno identificate per tutti i componenti e sistemi di produzione, gli strumenti di monitoraggio e diagnostica verranno applicati a questi sistemi e monitorati regolarmente dal personale operativo.
- Le operazioni considereranno l'utilizzo degli strumenti di monitoraggio e diagnostica in ambienti non di produzione, ad esempio staging e QA, per identificare i problemi di sistema prima che si verifichino nell'ambiente di produzione.

**Possibili opzioni di progettazione:** [Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor), che include anche Log Analytics e Application Insights, fornisce strumenti per la raccolta e l'analisi dei dati di telemetria per agevolare la comprensione delle prestazioni delle applicazioni e identificare in modo proattivo i problemi che li interessano e le risorse da cui dipendono.

## <a name="configuration-security-reviews"></a>Verifiche di protezione della configurazione

**Rischio tecnico:** Nel corso del tempo, nuovi problemi o minacce di sicurezza possono aumentare i rischi di accesso non autorizzato a risorse sicure.

**Definizione dei criteri**: I processi di governance del cloud devono includere un esame trimestrale condotto con i team che si occupano della gestione della configurazione per identificare gli attori dannosi o i modelli di uso da evitare nella configurazione degli asset del cloud.

**Possibili opzioni di progettazione:** Stabilire una riunione di revisione trimestrale per la sicurezza che includa i membri del team governance e il personale IT responsabile della configurazione delle risorse e delle applicazioni cloud. Esaminare i dati e le metriche di sicurezza esistenti per stabilire i gap nei criteri e negli strumenti di accelerazione della distribuzione corrente e aggiornare i criteri per correggere eventuali nuovi rischi.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per sviluppare criteri che consentano di risolvere rischi aziendali specifici, che si allineano con i piani di adozione del cloud.

Per iniziare a sviluppare le proprie istruzioni di criteri personalizzate correlate alla gestione delle identità, scaricare [Identity Baseline template](./template.md) (modello di Baseline di identità).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Accelerazione della distribuzione.

> [!div class="nextstepaction"]
> [Establish policy compliance processes](./compliance-processes.md) (Stabilire i processi di conformità ai criteri)
