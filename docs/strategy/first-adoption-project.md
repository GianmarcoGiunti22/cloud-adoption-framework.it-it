---
title: Primo progetto di adozione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sull'implementazione del primo progetto di adozione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: e0ddf68f959130df11305a9791c553aa48009c01
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753807"
---
<!-- markdownlint-disable MD026 -->

# <a name="first-cloud-adoption-project"></a>Primo progetto di adozione del cloud

Si tratta di una curva di apprendimento e di un impegno temporale associato alla pianificazione dell'adozione del cloud. Anche per i team esperti, la pianificazione corretta richiede tempo: il tempo per allineare le parti interessate, il tempo per raccogliere e analizzare i dati, il tempo per convalidare le decisioni a lungo termine e il tempo per allineare le persone, i processi e la tecnologia. Nella maggior parte delle attività di adozione, la pianificazione cresce in parallelo con l'adozione, migliorando con ogni versione e con ogni migrazione del carico di lavoro nel cloud. È importante comprendere la differenza tra un piano di adozione del cloud e una strategia di adozione del cloud. È necessaria una strategia ben definita per facilitare e guidare l'implementazione di un piano di adozione del cloud.

Il Framework di adozione del cloud per Azure delinea i processi per l'adozione del cloud e il funzionamento dei carichi di lavoro ospitati nel cloud. Ognuno dei processi nelle fasi definizione strategia, piano, pronto, adozione e funzionamento richiede piccole espansioni di competenze tecniche, aziendali e operative. Alcune di queste competenze possono derivare dall'apprendimento diretto. Tuttavia, molti di essi vengono acquisiti con maggiore efficacia grazie all'esperienza pratica.

L'avvio di un primo processo di adozione in parallelo con lo sviluppo del piano offre alcuni vantaggi:

- Definire un mindset di crescita per incoraggiare l'apprendimento e l'esplorazione
- Offrire un'opportunità al team di sviluppare le competenze necessarie
- Creare situazioni che incoraggino nuovi approcci alla collaborazione
- Identificare gap di competenze e potenziali esigenze di partnership
- Fornire input tangibili al piano

## <a name="first-project-criteria"></a>Primo criterio progetto

Il primo progetto di adozione dovrebbe allinearsi alle [motivazioni](./motivations.md) dell'adozione del cloud. Quando possibile, il primo progetto deve anche dimostrare lo stato di avanzamento verso un [risultato aziendale](./business-outcomes/business-outcome-template.md)definito.

## <a name="first-project-expectations"></a>Previsioni del primo progetto

Il progetto per la prima adozione del team può comportare una distribuzione di produzione di qualche tipo. Ma questo non è sempre il caso. Stabilire in anticipo le aspettative appropriate. Di seguito sono riportate alcune aspettative da impostare:

- Questo progetto è un'origine di formazione.
- Questo progetto può comportare distribuzioni di produzione, ma richiederà prima di tutto un ulteriore sforzo.
- L'output di questo progetto è un set di requisiti chiari per fornire una soluzione di produzione a lungo termine.

## <a name="first-project-examples"></a>Esempi di primo progetto

Per supportare i criteri precedenti, questo elenco fornisce un esempio di un primo progetto per ogni categoria di motivazione:

- **Eventi aziendali critici:** Quando un evento di business critico è la motivazione principale, l'implementazione di uno strumento come [Azure Site Recovery](../migrate/azure-migration-guide/migrate.md?tabs=Tools#azure-site-recovery) potrebbe essere un primo progetto valido. Durante la migrazione è possibile usare questo strumento per eseguire rapidamente la migrazione delle risorse del Data Center. Tuttavia, durante il primo progetto, è possibile utilizzarlo esclusivamente come strumento di ripristino di emergenza, riducendo le dipendenze dalle risorse di ripristino di emergenza nel Data Center.

- **Motivazioni della migrazione:** Quando la migrazione è la motivazione principale, è consigliabile iniziare con la migrazione di un carico di lavoro non critico. La Guida all' [installazione di Azure](../ready/azure-setup-guide/index.md) e la guida alla [migrazione di Azure](../migrate/azure-migration-guide/index.md) possono fornire linee guida per la migrazione del primo carico di lavoro.

- **Motivazioni dell'innovazione:** Quando l'innovazione è la motivazione principale, la creazione di un ambiente di sviluppo/test mirato può essere un ottimo primo progetto.

Altri esempi di progetti di adozione sono i seguenti:

- **Ripristino di emergenza e continuità aziendale (DRBC):** Oltre Azure Site Recovery, è possibile implementare più strategie DRBC come primo progetto.
- Non **produzione:** Distribuire un'istanza di non produzione di un carico di lavoro.
- **Archivio:** L'archiviazione a freddo può applicare un ceppo alle risorse del Data Center. Lo stato di trasferimento dei dati nel cloud è una rapida vittoria.
- **Fine del supporto (EOS):** La migrazione degli asset che hanno raggiunto la fine del supporto è un'altra rapida vittoria che crea competenze tecniche. Potrebbe inoltre garantire una riduzione dei costi rispetto ai contratti di supporto costosi o ai costi di licenza.
- **Interfaccia desktop virtuale (VDI):** La creazione di desktop virtuali per i dipendenti remoti può offrire una rapida vittoria. In alcuni casi, questo primo progetto di adozione può anche ridurre la dipendenza da reti private costose a favore della connettività Internet pubblica.
- **Sviluppo/test:** Rimuovi sviluppo/test da ambienti locali per offrire agli sviluppatori controllo, agilità e capacità self-service.
- **App semplici (meno di cinque):** Modernizza ed Esegui la migrazione di una semplice app per ottenere rapidamente esperienza per sviluppatori e operazioni.
- **Lab delle prestazioni:** Quando è necessario ottenere prestazioni elevate in un ambiente lab, usare il cloud per eseguire il provisioning rapido ed economico di questi laboratori per un breve periodo di tempo.
- **Piattaforma dati:** Creazione di un data Lake con calcolo scalabile per carichi di lavoro di analisi, creazione di report o Machine Learning e migrazione a database gestiti tramite metodi di dump/ripristino o servizi di migrazione dei dati.

## <a name="next-steps"></a>Passaggi successivi

Una volta avviato il primo progetto di adozione del cloud, il team di strategia cloud può rivolgere l'attenzione al [piano di adozione del cloud](../plan/index.md)a lungo termine.

> [!div class="nextstepaction"]
> [Creazione del piano di adozione del cloud](../plan/index.md)
