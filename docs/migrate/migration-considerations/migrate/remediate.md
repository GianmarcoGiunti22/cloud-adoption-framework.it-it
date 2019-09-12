---
title: Correzione degli asset prima della migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Correzione degli asset incompatibili prima della migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 54621d366f0ae0a3e2e3504532ace183bc7f49c4
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833453"
---
# <a name="remediate-assets-prior-to-migration"></a>Correggere gli asset prima della migrazione

Durante il processo di valutazione della migrazione, il team cerca di identificare le eventuali configurazioni che possono determinare l'incompatibilità di un asset con il provider di servizi cloud selezionato. La fase di *correzione* è un checkpoint del processo di migrazione che consente di assicurarsi che tali incompatibilità siano state risolte. Questo articolo illustra, a scopo di riferimento, alcune attività di correzione comuni. Definisce inoltre una procedura di base da seguire per decidere se la correzione rappresenta un valido investimento.

## <a name="common-remediation-tasks"></a>Attività di correzione comuni

In qualsiasi ambiente aziendale esiste il debito tecnico. In alcuni casi si tratta di un normale risultato previsto. Le decisioni relative all'architettura adatte a un ambiente locale possono non essere del tutto appropriate per una piattaforma cloud. In ogni caso, per preparare gli asset per la migrazione può essere necessario eseguire attività di correzione comuni. Di seguito sono riportati alcuni esempi:

- **Aggiornamenti secondari degli host.** Talvolta è necessario aggiornare un host obsoleto prima della replica.
- **Aggiornamenti secondari dei sistemi operativi guest.** È più probabile che un sistema operativo richieda patch o aggiornamenti prima della replica.
- **Modifiche al contratto di servizio.** Le operazioni di backup e il ripristino cambiano in maniera significativa in una piattaforma cloud. È probabile che gli asset richiedano modifiche secondarie ai processi di backup per assicurare la continuità operativa nel cloud.
- **Migrazione PaaS.** In alcuni casi può essere necessaria una distribuzione PaaS di una struttura di dati o di un'applicazione per accelerare la distribuzione. Per preparare la soluzione per la distribuzione PaaS possono essere richieste alcune modifiche di minore entità.
- **Modifiche al codice PaaS.** Capita spesso che le applicazioni personalizzate richiedano modifiche secondarie al codice per essere pronte per la distribuzione PaaS. Può ad esempio essere necessario includere metodi per la scrittura in un disco locale o configurare l'uso dello stato della sessione in memoria.
- **Modifiche alla configurazione delle applicazioni.** Le applicazioni di cui è stata eseguita la migrazione possono richiedere modifiche alle variabili, ad esempio i percorsi di rete degli asset dipendenti, modifiche agli account del servizio o aggiornamenti agli indirizzi IP dipendenti.
- **Modifiche secondarie ai percorsi di rete.** Può essere necessario modificare i modelli di routing in modo da instradare correttamente il traffico utenti verso i nuovi asset.
    > [!NOTE]
    > Non si tratta del routing di produzione verso i nuovi asset, ma della configurazione per consentire il routing appropriato verso gli asset in generale.

## <a name="large-scale-remediation-tasks"></a>Attività di correzione su larga scala

Quando un data center viene gestito correttamente, con le patch e gli aggiornamenti appropriati, è probabile che non vi siano particolari necessità di correzione. Gli ambienti che richiedono maggiori interventi di correzione sono quelli delle aziende di grandi dimensioni o delle organizzazioni che hanno subito ridimensionamenti IT di notevole entità, alcuni ambienti di servizi gestiti legacy e gli ambienti con numerose acquisizioni. Negli ambienti di questo tipo, le attività di correzione possono rappresentare una parte significativa dell'impegno di migrazione. Quando le attività di correzione seguenti vengono eseguite frequentemente e influiscono negativamente sulla velocità o la coerenza della migrazione, può essere opportuno suddividere le attività di correzione tra team e carichi di lavoro paralleli (in modo analogo alle attività di adozione e governance del cloud).

- **Aggiornamenti frequenti degli host.** Quando è necessario aggiornare un numero elevato di host per completare la migrazione di un carico di lavoro, è probabile che il team dedicato alla migrazione riscontri dei ritardi. Può quindi essere opportuno suddividere le applicazioni interessate e risolvere le correzioni prima di includere tali applicazioni nei rilasci pianificati.
- **Aggiornamenti frequenti dei sistemi operativi guest.** Nelle aziende di grandi dimensioni sono spesso presenti server che eseguono versioni obsolete di Linux o Windows. Oltre agli evidenti rischi di sicurezza legati al funzionamento di un sistema operativo obsoleto, vi sono anche problemi di incompatibilità che impediscono la migrazione dei carichi di lavoro interessati. Quando un numero elevato di macchine virtuali richiede la correzione del sistema operativo, può essere opportuno suddividere queste attività in un'iterazione parallela.
- **Modifiche rilevanti al codice.** Le applicazioni personalizzate meno recenti possono richiedere un numero di modifiche più significativo per la preparazione alla distribuzione PaaS. In questi casi, può essere opportuno rimuoverle completamente dal backlog della migrazione e gestirle in un programma completamente separato.

## <a name="decision-framework"></a>Framework decisionale

Le attività di correzione per i carichi di lavoro più piccoli possono essere semplici e questo è uno dei motivi per cui è consigliabile scegliere un carico di lavoro ridotto per la migrazione iniziale. Tuttavia, con il progressivo avanzamento delle attività di migrazione, le dimensioni dei carichi di lavoro da gestire aumentano e le attività di correzione possono richiedere molto tempo e processi costosi. Ad esempio, le attività di correzione per una migrazione di Windows Server 2003 che coinvolge un pool di oltre 5000 macchine virtuali possono provocare ritardi di mesi nella migrazione. Quando sono richieste correzioni di tale entità, può essere utile formulare le domande seguenti per guidare il processo decisionale:

- Tutti i carichi di lavoro interessati dalle attività di correzione sono stati identificati e annotati nel backlog della migrazione?
- Per i carichi di lavoro non interessati dalle attività di correzione, una migrazione genererà un ritorno sugli investimenti (ROI) analogo?
- Gli asset interessati possono essere corretti in conformità alla tempistica originale della migrazione? Quale effetto avrebbero le modifiche alla tempistica sul ROI?
- È economicamente fattibile correggere gli asset in parallelo con le attività di migrazione?
- Il personale dispone di larghezza di banda sufficiente per svolgere entrambe le attività di correzione e migrazione? È opportuno coinvolgere un partner per svolgere una di queste attività o addirittura entrambe?

Se queste domande non producono risposte favorevoli, può essere opportuno prendere in considerazione alcuni approcci alternativi che esulano dalla strategia di rehosting IaaS di base:

- **Containerizzazione.** Alcuni asset possono essere ospitati in un ambiente suddiviso in contenitori senza attività di correzione. Questo approccio può avere come risultato prestazioni non molto efficienti e non risolve i problemi di sicurezza o conformità.
- **Automazione.** A seconda dei requisiti dei carichi di lavoro e delle attività di correzione, può essere più vantaggioso creare script per la distribuzione in nuovi asset adottando un approccio DevOps.
- **Ricostruzione.** Quando i costi delle attività di correzione e il valore aziendale sono molto elevati, può essere opportuno ridefinire l'architettura di un carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Al termine della fase di correzione, le [attività di replica](./replicate.md) sono pronte.

> [!div class="nextstepaction"]
> [Replicare gli asset](./replicate.md)
