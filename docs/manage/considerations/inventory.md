---
title: Inventario e visibilità-gestione e operazioni di cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Inventario e visibilità-gestione e operazioni di cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 60c6b72590cc5f912572109f0cce10366413fdf0
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565103"
---
# <a name="inventory-and-visibility-in-cloud-management"></a>Inventario e visibilità nella gestione cloud

La gestione operativa presenta una dipendenza chiara dai dati. Una gestione coerente richiede informazioni sugli elementi gestiti (inventario) e sul modo in cui i carichi di lavoro e gli asset gestiti cambiano nel tempo (visibilità). Chiare informazioni dettagliate sull'inventario e sulla visibilità consentono al team di gestire l'ambiente in modo efficace. Tutte le altre attività e processi di gestione operativa si basano su queste due aree.

Alcune frasi classiche sull'importanza delle misurazioni impostano il tono di questo articolo:

- Gestire le questioni.
- È possibile gestire solo gli elementi che è possibile misurare.
- Se non è possibile misurarlo, potrebbe non essere rilevante.

La disciplina di inventario e visibilità si basa su queste frasi senza tempo. Prima di poter stabilire in modo efficace i processi di gestione operativa, è importante raccogliere i dati e creare il livello di visibilità giusto per i team giusti.

## <a name="common-customer-challenges"></a>Problemi comuni dei clienti

A meno che non vengano applicati in modo coerente i processi di inventario e visibilità, i team di gestione operativi possono soffrire di un volume superiore di interruzioni aziendali, tempi di recupero più lunghi e maggiori quantità di lavoro richiesto per risolvere i problemi e valutare i problemi. Poiché le modifiche influiscono negativamente sulle applicazioni con priorità più elevata e su un numero maggiore di asset, ciascuna di queste metriche cresce ancora più rapidamente.

Queste problematiche derivano da un numero ridotto di domande a cui è possibile rispondere solo tramite dati e telemetria coerenti:

- In che modo le prestazioni dello stato attuale deviano dalla telemetria delle prestazioni operative standard?
- Quali asset causano le interruzioni aziendali a livello di carico di lavoro?
- Quali asset devono essere corretti per tornare a prestazioni accettabili del carico di lavoro o del processo aziendale?
- Quando è stata avviata la deviazione? Qual è il trigger?
- Quali modifiche sono state apportate alle risorse sottostanti? Da chi?
- Le modifiche erano intenzionali? Dannoso?
- In che modo le modifiche influiscono sulla telemetria delle prestazioni?

È difficile, se non impossibile, rispondere a queste domande senza una ricca origine centralizzata per i log e i dati di telemetria. Per abilitare la gestione del cloud garantendo la configurazione coerente necessaria per centralizzare i dati, il servizio di base deve innanzitutto iniziare definendo i processi. I processi devono acquisire il modo in cui tale configurazione impone la raccolta dei dati per supportare i componenti di inventario e visibilità nella sezione successiva.

## <a name="components-of-inventory-and-visibility"></a>Componenti di inventario e visibilità

La creazione di visibilità su qualsiasi piattaforma cloud richiede alcuni componenti chiave:

- Responsabilità e visibilità
- Inventario
- Registrazione centrale
- Rilevamento modifiche
- Telemetria delle prestazioni

### <a name="responsibility-and-visibility"></a>Responsabilità e visibilità

Quando si stabiliscono impegni per ogni carico di lavoro, la [responsabilità di gestione](./commitment.md#management-responsibility) è un fattore chiave. La responsabilità delegata crea una necessità di visibilità delegata. Il primo passaggio verso l'inventario e la visibilità consiste nel garantire che le parti responsabili abbiano accesso ai dati corretti. Prima di implementare tutti gli strumenti nativi del cloud per la visibilità, assicurarsi che ogni strumento di monitoraggio sia stato configurato con un accesso e un ambito appropriati per ogni team operativo.

### <a name="inventory"></a>Inventario

Se non si sa che esiste un asset, è difficile gestire l'asset. Prima di poter gestire un asset o un carico di lavoro, è necessario che sia in inventario e classificato. Il primo passaggio tecnico verso le operazioni stabili è la convalida dell'inventario e della classificazione di tale inventario.

### <a name="central-logging"></a>Registrazione centrale

La registrazione centralizzata è essenziale per la visibilità richiesta quotidianamente dai team di Operations Management. Tutti gli asset distribuiti nel cloud devono registrare i log in una posizione centrale. In Azure la posizione centrale è log Analytics. La centralizzazione delle unità di registrazione segnala la gestione delle modifiche, l'integrità dei servizi, la configurazione e la maggior parte degli altri aspetti degli interventi IT.

L'applicazione dell'utilizzo coerente della registrazione centrale è il primo passo verso la creazione di operazioni ripetibili. L'imposizione può essere eseguita tramite criteri aziendali. Quando possibile, tuttavia, l'applicazione deve essere automatizzata per garantire la coerenza.

### <a name="change-tracking"></a>Rilevamento modifiche

Change è una costante in un ambiente tecnologico. La consapevolezza e la comprensione delle modifiche tra più carichi di lavoro sono essenziali per le operazioni affidabili. Qualsiasi soluzione di gestione del cloud deve includere un mezzo per comprendere quando, come e perché apportare modifiche tecniche. Senza questi punti dati, le attività correttive sono significativamente compromesse.

### <a name="performance-telemetry"></a>Telemetria delle prestazioni

Gli impegni aziendali sulla gestione del cloud sono basati sui dati. Per mantenere correttamente gli impegni, il team operativo cloud deve prima comprendere i dati di telemetria relativi alla stabilità, alle prestazioni e alle operazioni del carico di lavoro e alle risorse che supportano il carico di lavoro.

L'integrità e le operazioni in corso della rete, del DNS, dei sistemi operativi e di altri aspetti fondamentali dell'ambiente sono punti dati critici che determinano l'integrità complessiva di tutti i carichi di lavoro.

## <a name="processes"></a>Processi

Forse più importante delle funzionalità della piattaforma di gestione cloud, i processi di gestione del cloud realizzeranno gli impegni operativi con l'azienda. Qualsiasi metodologia di gestione del cloud deve includere, almeno, i processi seguenti:

- **Monitoraggio reattivo:** Quando le deviazioni influiscono negativamente sulle operazioni aziendali, chi risolve tali deviazioni? Quali azioni intraprendono per correggere le deviazioni?
- **Monitoraggio proattivo:** Quando vengono rilevate deviazioni, ma le operazioni aziendali non sono interessate, come vengono risolte le deviazioni e da chi?
- **Creazione di report sull'impegno:** In che modo l'adesione all'impegno aziendale è stata comunicata agli stakeholder aziendali?
- **Revisioni del budget:** Qual è il processo di revisione di tali impegni rispetto ai costi di budget? Qual è il processo di modifica della soluzione distribuita o degli impegni per la creazione dell'allineamento?
- **Percorsi di escalation:** Quali percorsi di escalation sono disponibili quando uno dei processi precedenti non riesce a soddisfare le esigenze dell'azienda?

Sono disponibili diversi altri processi relativi all'inventario e alla visibilità. L'elenco precedente è stato progettato per provocare il pensiero all'interno del team operativo. La risposta a queste domande consentirà di sviluppare alcuni dei processi necessari, nonché di generare domande più approfondite.

## <a name="responsibilities"></a>Responsabilità

Quando si sviluppano processi per il monitoraggio operativo, è ugualmente importante determinare le responsabilità per il funzionamento giornaliero e il normale supporto di ogni processo.

In un'organizzazione IT centrale, fornisce le competenze operative. Le aziende sarebbero di natura consultiva, quando i problemi richiedono la correzione.

In un cloud Center of Excellence Organization, le operazioni aziendali forniranno le competenze necessarie per la gestione di questi processi. SI concentrerebbe sull'automazione e il supporto dei team, in quanto operano nell'ambiente.

Ma queste sono le responsabilità comuni. Le organizzazioni richiedono spesso una combinazione di responsabilità per soddisfare gli impegni aziendali.

## <a name="act-on-inventory-and-visibility"></a>Agire sull'inventario e sulla visibilità

Indipendentemente dalla piattaforma cloud, i cinque componenti di inventario e visibilità vengono usati per gestire la maggior parte dei processi operativi. Tutte le discipline successive si compileranno sui dati acquisiti. Negli articoli successivi di questa serie vengono illustrati i modi per agire su tali dati e integrare altre origini dati.

### <a name="share-visibility"></a>Visibilità della condivisione

I dati senza azione producono un piccolo ritorno. La gestione cloud potrebbe espandersi oltre gli strumenti e i processi nativi del cloud. Per gestire processi più ampi, potrebbe essere necessario migliorare una linea di base di gestione del cloud per includere Reporting, integrazione della gestione dei servizi IT o centralizzazione dei dati. Per la gestione del cloud potrebbe essere necessario includere uno o più degli elementi seguenti durante le varie fasi della maturità operativa.

### <a name="report"></a>Report

I processi offline e la comunicazione sugli impegni per gli stakeholder aziendali richiedono spesso la creazione di report. La creazione di report Self-Service o periodici può essere un componente necessario di una linea di base di gestione migliorata.

### <a name="it-service-management-itsm-integration"></a>Integrazione di IT Service Management (ITSM)

L'integrazione con ITSM è spesso il primo esempio di azione sull'inventario e sulla visibilità. Quando si verificano deviazioni rispetto ai modelli di prestazioni previsti, l'integrazione di ITSM utilizza gli avvisi della piattaforma cloud per attivare i ticket in uno strumento di gestione dei servizi separato per attivare le attività di correzione. Alcuni modelli operativi potrebbero richiedere l'integrazione di ITSM come aspetto della linea di base di gestione migliorata.

### <a name="data-centralization"></a>Centralizzazione dei dati

Esistono diversi motivi per cui un'azienda potrebbe richiedere più tenant all'interno di un singolo provider di servizi cloud. In questi scenari, la centralizzazione dei dati è un componente obbligatorio della linea di base di gestione avanzata, perché può fornire visibilità in ogni tenant o ambiente.

## <a name="next-steps"></a>Passaggi successivi

La conformità operativa si basa sulle funzionalità di inventario applicando automazione e controlli di gestione. Vedere come viene eseguito il mapping della [conformità operativa](./operational-compliance.md) ai processi.

> [!div class="nextstepaction"]
> [Pianificare la conformità operativa](./operational-compliance.md)
