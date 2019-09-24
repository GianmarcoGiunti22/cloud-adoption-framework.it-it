---
title: Definizioni dei criteri di esempio per la coerenza delle risorse
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definizioni dei criteri di esempio per la coerenza delle risorse
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: f2e15ad1640bec4e289c49a1f9dcf83de7c04ec3
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221977"
---
# <a name="resource-consistency-sample-policy-statements"></a>Definizioni dei criteri di esempio per la coerenza delle risorse

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà risolto da questi criteri.
- **Definizione dei criteri**: Una spiegazione chiara e riepilogativa dei requisiti dei criteri.
- **Opzioni di progettazione**: Suggerimenti pratici, specifiche o altre linee guida che i team IT e gli sviluppatori possono usare quando implementano i criteri.

Le istruzioni dei criteri di esempio seguenti riguardano i rischi aziendali comuni relativi alla coerenza delle risorse. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="tagging"></a>Assegnazione di tag

**Rischio tecnico:** senza i tag dei metadati appropriati associati alle risorse distribuite, il reparto responsabile delle operazioni IT non può definire le priorità per il supporto o l'ottimizzazione delle risorse in base al contratto di servizio richiesto, all'importanza per le operazioni aziendali o ai costi operativi. Ciò può comportare l'errata allocazione delle risorse IT e possibili ritardi nella risoluzione degli eventi imprevisti.

**Definizione dei criteri**: verranno implementati i criteri seguenti:

- Agli asset distribuiti devono essere assegnati tag con i valori seguenti:
  - Costo
  - Criticità
  - Contratto di servizio
  - Ambiente
- Gli strumenti di governance devono convalidare l'assegnazione di tag correlati a costo, criticità, contratto di servizio, applicazione e ambiente. Tutti i valori devono essere allineati ai valori predefiniti gestiti dal team di governance.

**Possibili opzioni di progettazione:** in Azure i [tag di metadati standard nome-valore](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) sono supportati per la maggior parte dei tipi di risorse. Si usa [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) per applicare tag specifici nell'ambito della creazione delle risorse.

## <a name="ungoverned-subscriptions"></a>Sottoscrizioni non gestite

**Rischio tecnico:** la creazione arbitraria di sottoscrizioni e gruppi di gestione può portare a sezioni isolate delle risorse cloud non correttamente soggette ai criteri di governance stabiliti.

**Definizione dei criteri**: La creazione di nuove sottoscrizioni o gruppi di gestione per le applicazioni cruciali o i dati protetti richiederà una revisione da parte del team di governance del cloud. Le modifiche approvate verranno integrate in un'assegnazione di progetto appropriata.

**Possibili opzioni di progettazione:** consentire l'accesso amministrativo ai [gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups) dell'organizzazione solo ai membri approvati del team di governance che controlleranno la creazione di sottoscrizioni e il processo di controllo degli accessi.

## <a name="manage-updates-to-virtual-machines"></a>Gestire gli aggiornamenti delle macchine virtuali

**Rischio tecnico:** le macchine virtuali che non sono aggiornate con gli aggiornamenti e le patch software più recenti sono vulnerabili a problemi di sicurezza o di prestazioni, che possono portare a interruzioni del servizio.

**Definizione dei criteri**: gli strumenti di governance devono imporre l'abilitazione degli aggiornamenti automatici per tutte le macchine virtuali distribuite. Le violazioni devono essere esaminate con i team di gestione operativa e risolte in base ai criteri relativi alle operazioni. Gli asset che non vengono aggiornati automaticamente devono essere inclusi in processi di proprietà del team responsabile delle operazioni IT.

**Possibili opzioni di progettazione:** per le macchine virtuali ospitate in Azure, è possibile implementare una gestione coerente degli aggiornamenti usando la [Soluzione Gestione aggiornamenti in Azure](https://docs.microsoft.com/azure/automation/automation-update-management).

## <a name="deployment-compliance"></a>Conformità della distribuzione

**Rischio tecnico:** Gli script di distribuzione e gli strumenti di automazione che non sono completamente controllati dal team di governance del cloud possono comportare distribuzioni di risorse che violano i criteri.

**Definizione dei criteri**: verranno implementati i criteri seguenti:

- Gli strumenti di distribuzione devono essere approvati dal team di governance del cloud per garantire la governance continua degli asset distribuiti.
- Gli script di distribuzione devono essere conservati nel repository centrale accessibile dal team di governance del cloud per la revisione e il controllo periodici.

**Possibili opzioni di progettazione:** l'uso coerente di [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints) per gestire le distribuzioni automatizzate consente distribuzioni coerenti delle risorse di Azure che rispettano gli standard e i criteri di governance dell'organizzazione.

## <a name="monitoring"></a>Monitoraggio

**Rischio tecnico:** l'implementazione non appropriata o la strumentazione incoerente del monitoraggio possono impedire il rilevamento di problemi di integrità dei carichi di lavoro o di altre violazioni della conformità dei criteri.

**Definizione dei criteri**: verranno implementati i criteri seguenti:

- Gli strumenti di governance devono verificare che tutte le risorse siano incluse nel monitoraggio per l'esaurimento delle risorse, la sicurezza, la conformità e l'ottimizzazione.
- Gli strumenti di governance devono verificare che venga raccolto il livello appropriato di dati di registrazione per tutte le applicazioni e i dati.

**Possibili opzioni di progettazione:** Monitoraggio di [Azure](https://docs.microsoft.com/azure/azure-monitor/overview) è il servizio di monitoraggio predefinito in Azure e il monitoraggio coerente può essere applicato tramite i [progetti di Azure](https://docs.microsoft.com/azure/governance/blueprints) durante la distribuzione delle risorse.

## <a name="disaster-recovery"></a>Ripristino di emergenza

**Rischio tecnico:** errori delle risorse, eliminazioni o danneggiamenti possono causare interruzioni di applicazioni o servizi cruciali e la perdita di dati sensibili.

**Definizione dei criteri**: è necessario implementare soluzioni di backup e ripristino per tutte le applicazioni cruciali e tutti i dati protetti per ridurre al minimo l'impatto aziendale di interruzioni o errori di sistema.

**Possibili opzioni di progettazione:** Il servizio [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) fornisce funzionalità di backup, ripristino e replica che consentono di ridurre al minimo la durata delle interruzioni negli scenari di continuità aziendale e ripristino di emergenza (BCdR).

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per elaborare criteri applicabili a rischi aziendali specifici, in linea con i piani di adozione del cloud.

Per iniziare a sviluppare le definizioni dei criteri personalizzate correlate alla coerenza delle risorse, scaricare il [modello di coerenza delle risorse](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Coerenza delle risorse.

> [!div class="nextstepaction"]
> [Establish policy compliance processes](./compliance-processes.md) (Stabilire i processi di conformità ai criteri)
