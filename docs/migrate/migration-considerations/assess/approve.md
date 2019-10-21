---
title: Approvare le modifiche dell'architettura prima della migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sull'importanza dell'approvazione prima della migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: cdc6abe2be94bb0d91047d4d64a0774bac6a8e0e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549213"
---
# <a name="approve-architecture-changes-before-migration"></a>Approvare le modifiche dell'architettura prima della migrazione

Durante il processo di valutazione della migrazione, ogni carico di lavoro viene valutato, progettato e stimato per sviluppare un piano di stato futuro per il carico di lavoro. È possibile che per alcuni carichi di lavoro di cui viene eseguita la migrazione nel cloud non vengano apportate modifiche all'architettura. La gestione della configurazione e dell'architettura locali può ridurre i rischi e semplificare il processo di migrazione. Non tutte le applicazioni però possono essere eseguite nel cloud senza modifiche dell'architettura. Se sono necessarie modifiche dell'architettura, questo articolo può aiutare a classificare la modifica e può fornire alcune indicazioni sulle attività di approvazione appropriate.

## <a name="business-impact-and-approval"></a>Impatto aziendale e approvazione

Durante la migrazione, è probabile che alcuni elementi vengano modificati in modi che hanno impatto sull'azienda. Sebbene non sia talvolta possibile evitare modifiche, le sorprese in seguito a modifiche riservate o non documentate dovrebbero essere. Per mantenere il supporto per gli stakeholder durante l'operazione di migrazione, è importante evitare sorprese. Cogliere di sorpresa i proprietari di applicazioni o gli stakeholder aziendali può comportare il rallentamento o l'arresto dell'attività di adozione del cloud.

Prima della migrazione, è importante preparare il proprietario aziendale del carico di lavoro per tutte le modifiche che potrebbero influire sui processi aziendali, ad esempio le modifiche apportate a:

- Contratti di servizio.
- Criteri di accesso o requisiti di sicurezza che hanno impatto sull'utente finale.
- Procedure di conservazione dei dati.
- Prestazioni delle applicazioni principali.

Anche nei casi in cui è possibile eseguire la migrazione di un carico di lavoro senza modifiche o con modifiche minime, può comunque registrarsi un impatto sull'azienda. I processi di replica possono rallentare le prestazioni dei sistemi di produzione. Le modifiche apportate all'ambiente durante la preparazione per la migrazione possono causare limitazioni delle prestazioni di rete o di routing. Molti altri impatti possono essere dovuti ad attività di replica, gestione temporanea o promozione.

Le normali attività di approvazione consentono di ridurre al minimo o di evitare le sorprese in seguito agli effetti prodotti sull'azienda da modifiche o da riduzioni delle prestazioni. Il team di adozione del cloud deve eseguire un processo di approvazione delle modifiche alla fine del processo di valutazione, prima di iniziare il processo di migrazione.

## <a name="existing-culture"></a>Impostazioni cultura esistenti

I team IT usano probabilmente meccanismi esistenti per la gestione delle modifiche che coinvolgono gli asset locali. Questi meccanismi in genere sono regolati da processi di gestione delle modifiche tradizionali basati su ITIL (Information Technology Infrastructure Library). In molte migrazioni aziendali questi processi coinvolgono il comitato consultivo per le modifiche (CAB), che è responsabile della revisione, della documentazione e dell'approvazione di tutte le richieste di modifiche (RFC) correlate all'IT.

Il CAB include in genere esperti di più team IT e aziendali, che offrono un'ampia gamma di prospettive e una revisione dettagliata di tutte le modifiche correlate all'IT. Un processo di approvazione CAB è un modo collaudato per ridurre i rischi e ridurre al minimo l'impatto prodotto sulle aziende da modifiche che coinvolgono carichi di lavoro stabili gestiti da operazioni IT.

## <a name="technical-approval"></a>Approvazione tecnica

Il livello di preparazione dell'organizzazione per l'approvazione delle modifiche tecniche è tra le cause più comuni di migrazione nel cloud non riuscita. Esiste una maggiore incidenza di progetti bloccati da una serie di approvazioni tecniche che non di deficit in una piattaforma cloud. La preparazione dell'organizzazione per l'approvazione delle modifiche tecniche è un requisito importante per l'esito della migrazione. Di seguito sono riportate alcune procedure consigliate per garantire che l'organizzazione sia pronta per l'approvazione tecnica.

### <a name="itil-change-advisory-board-challenges"></a>Problemi del comitato consultivo per le modifiche ITIL

Ogni approccio di gestione delle modifiche prevede un proprio set di controlli e di processi di approvazione. La migrazione è una serie di modifiche continue che iniziano con un elevato livello di ambiguità e sviluppano una maggiore chiarezza nel corso dell'esecuzione. Di conseguenza, la migrazione è più adatta agli approcci di gestione del cambiamento basati su procedure agili, con il team di strategia del cloud che funge da proprietario del prodotto.

Tuttavia, la scala e la frequenza delle modifiche durante una migrazione nel cloud non si adattano bene alla natura dei processi ITIL. I requisiti di un'approvazione CAB possono mettere a rischio la riuscita di una migrazione, rallentando o arrestando il processo. Inoltre, nelle fasi iniziali della migrazione l'ambiguità è elevata e l'esperienza in materia tende a essere bassa. Per le prime migrazioni o i primi rilasci di carichi di lavoro, il team di adozione del cloud è spesso in modalità di apprendimento. Di conseguenza, potrebbe essere difficile per il team fornire i tipi di dati necessari per ottenere un'approvazione CAB.

Le procedure consigliate seguenti consentono al CAB di mantenere un livello di flessibilità durante la migrazione senza diventare un ostacolo fastidioso.

### <a name="standardize-change"></a>Standardizzare le modifiche

Per un team di adozione del cloud potrebbe essere allettante prendere in esame decisioni di architettura dettagliate per ogni carico di lavoro di cui viene eseguita la migrazione nel cloud. È altrettanto allettante usare la migrazione nel cloud come catalizzatore per effettuare il refactoring delle decisioni di architettura precedenti. Per le organizzazioni che eseguono la migrazione di poche centinaia di macchine virtuali o poche dozzine di carichi di lavoro, entrambi gli approcci possono essere gestiti correttamente. Quando si esegue la migrazione di un data center costituito da 1000 o più asset, ognuno di questi approcci viene considerato ad alto rischio con riduzione significativa della probabilità di successo. La modernizzazione, il refactoring e la riprogettazione di ogni applicazione richiedono set di competenze diversi e una varietà significativa di modifiche, tutte attività che creano dipendenze da interventi umani su larga scala. Ognuna di queste dipendenze introduce rischi nel processo di migrazione.

L'articolo sulla [razionalizzazione del digital estate](../../../digital-estate/rationalize.md) illustra l'agilità e il risparmio di tempo associati a presupposti di base quando si razionalizza un digital estate. Esiste poi il vantaggio aggiuntivo derivante dalla modifica standardizzata. Scegliendo un approccio di razionalizzazione predefinito per gestire l'attività di migrazione, il comitato consultivo per il cloud o il proprietario del prodotto può rivedere e approvare l'applicazione di una modifica a un lungo elenco di carichi di lavoro. In questo modo si riduce l'approvazione tecnica di ogni carico di lavoro solo a quelli che richiedono una modifica significativa dell'architettura per garantire la compatibilità con il cloud.

### <a name="clarify-expectations-and-roles-of-approvers"></a>Chiarire le aspettative e i ruoli dei responsabili approvazione

Prima della valutazione del primo carico di lavoro, il team di strategia del cloud deve documentare e comunicare le aspettative di chiunque sia coinvolto nell'approvazione della modifica. Questa semplice attività può evitare costosi ritardi quando il team di adozione del cloud è totalmente impegnato.

### <a name="seek-approval-early"></a>Cercare presto l'approvazione

Quando possibile, la modifica tecnica deve essere rilevata e documentata durante il processo di valutazione. Indipendentemente dai processi di approvazione, il team di adozione del cloud deve coinvolgere presto i responsabili approvazione. Prima inizia l'approvazione delle modifiche, minori saranno le probabilità che il processo di approvazione blocchi le attività di migrazione.

## <a name="next-steps"></a>Passaggi successivi

Con l'ausilio di queste procedure consigliate, dovrebbe essere più semplice integrare nelle attività di migrazione un processo di approvazione corretto e a basso rischio. Dopo l'approvazione delle modifiche dei carichi di lavoro, il team di adozione del cloud è pronto per la [migrazione dei carichi di lavoro](../migrate/index.md).

> [!div class="nextstepaction"]
> [Eseguire la migrazione dei carichi di lavoro](../migrate/index.md)
