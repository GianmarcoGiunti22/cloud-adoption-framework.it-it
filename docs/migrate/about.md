---
title: Migrazione cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione al contenuto relativo alla migrazione al cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ab28d38aafdddc0206b9fc7abc98cb489bba5d1b
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751280"
---
# <a name="cloud-migration-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Migrazione al cloud in Microsoft Cloud Adoption Framework per Azure

La migrazione al cloud è il processo di spostamento di asset digitali esistenti in una piattaforma cloud. In questo approccio, gli asset esistenti vengono replicati nel cloud con modifiche minime. Quando un'applicazione o un carico di lavoro diventa operativo nel cloud, si esegue la transizione degli utenti dalla soluzione esistente alla soluzione cloud. La migrazione al cloud è un modo per bilanciare in modo efficace un portfolio cloud. Questo è spesso l'approccio più agile e rapido nel breve termine. Può tuttavia non essere possibile sfruttare alcuni vantaggi del cloud tramite questo approccio senza ulteriori modifiche future. Le aziende di grandi e medie dimensioni scelgono questo approccio per accelerare il cambiamento, evitare spese in conto capitale pianificate e ridurre i costi di esercizio.

## <a name="cloud-migration-guidance"></a>Indicazioni sulla migrazione al cloud

Le linee guida in questa sezione di Cloud Adoption Framework sono progettate per due scopi:

- Illustrare ai clienti percorsi per la migrazione che rappresentano alcune delle loro esperienze comuni. Ogni percorso include il processo e gli strumenti necessari per ottenere risultati positivi nel processo di migrazione al cloud. Le linee guida di progettazione sono ovviamente specifiche per Azure. Tutte le altre raccomandazioni in queste guide possono essere applicate come parte di un approccio indipendente dal cloud o multi-cloud.
- Aiutare i lettori a creare piani di migrazione personalizzati in grado di soddisfare numerose esigenze aziendali, tra cui la migrazione a più cloud pubblici, tramite linee guida dettagliate sullo sviluppo di processi, ruoli e responsabilità e controlli di gestione delle modifiche.

Questo contenuto è destinato al team di adozione del cloud, ma è utile anche per i Cloud Architect che devono sviluppare una base solida di migrazione al cloud.

## <a name="intended-audience"></a>Destinatari

Le linee guida di Cloud Adoption Framework interessano i reparti aziendali impegnati nelle attività di carattere commerciale, tecnologico e culturale. Questa sezione interessa in particolare i proprietari delle applicazioni, il personale preposto alla gestione del cambiamento (ad esempio il personale di gestione dei progetti Agile e PMO), i responsabili delle attività finanziarie e line-of-business e il team di adozione del cloud. Vi sono varie dipendenze tra queste figure professionali che richiederanno un approccio collaborativo da parte dei Cloud Architect che usano queste linee guida. La collaborazione con questi team può essere un'attività una tantum, ma in alcuni casi può richiedere interazioni ricorrenti con queste altre figure professionali.

Il Cloud Architect assume il ruolo di leader e mediatore per semplificare l'interazione tra le varie persone coinvolte. I contenuti di questa raccolta di guide sono stati progettati per consentire ai Cloud Architect di comunicare informazioni corrette alle persone appropriate e giungere così alle decisioni opportune. La trasformazione aziendale resa possibile dal cloud dipende dalla capacità del Cloud Architect di aiutare il personale tecnico e aziendale a prendere le decisioni appropriate.

**Specializzazione dell'architetto del cloud in questa sezione:** Ogni sezione del Framework di adozione del cloud rappresenta una specializzazione o una variante diversa del ruolo di architetto del cloud. Questa sezione è stata progettata per i Cloud Architect con esperienza dell'ambiente locale esistente e dell'impatto che può avere sulle opzioni di migrazione.

**Separazione dei compiti:** In molte aziende, la separazione dei compiti esiste per limitare l'accesso ai sistemi di produzione o ai segmenti dell'ambiente aziendale. In tal caso, il processo di migrazione diventa più complesso. In alcuni contesti, tali ruoli e responsabilità possono richiedere più Cloud Architect per gestire l'intero processo di migrazione.

**Opzioni di partnership:** in ognuno di questi processi, i team dovranno acquisire nuove competenze e adottare nuovi approcci. L'espansione delle competenze tecniche tra i membri del team esistenti è un'opzione durante l'esecuzione. o, in alternativa, assumere altro personale. La partnership con terze parti può spesso essere utile per ottenere risultati in modo più rapido e ridurre i rischi. Le [opzioni di partnership](./migration-considerations/assess/partnership-options.md) possono facilitare la scelta dell'opzione di collaborazione ottimale.

## <a name="next-steps"></a>Passaggi successivi

Per chi vuole seguire queste linee guida dall'inizio alla fine, il contenuto presentato consentirà di sviluppare una solida strategia di migrazione al cloud. Le linee guida accompagneranno il lettore alla scoperta della teoria e dell'implementazione di tale strategia.

Come primo passaggio, utilizzare la guida alla [migrazione di Azure](./azure-migration-guide/index.md) per comprendere il set standard di strumenti e approcci necessari per la migrazione in un caso d'uso comune. Dopo aver acquisito le informazioni di base, i lettori potranno ampliare le proprie conoscenze con [scenari di migrazione complessi](./expanded-scope/index.md), [procedure consigliate per la migrazione](./azure-best-practices/index.md) e [considerazioni sulla migrazione](./migration-considerations/index.md).

> [!div class="nextstepaction"]
> [Guida alla migrazione ad Azure](./azure-migration-guide/index.md)
