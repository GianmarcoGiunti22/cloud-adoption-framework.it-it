---
title: Guida alle decisioni relative alla coerenza delle risorse
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla coerenza delle risorse nell'ambito della pianificazione di una migrazione ad Azure.
author: doodlemania2
ms.author: dermar
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: c6ad3e6b14ffde5f3c09feb6047a2d0bbe981314
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564811"
---
# <a name="resource-consistency-decision-guide"></a>Guida alle decisioni relative alla coerenza delle risorse

La [progettazione delle sottoscrizioni](../subscriptions/index.md) di Azure definisce la modalità di organizzazione degli asset cloud in relazione alla struttura, alle procedure di accounting e ai requisiti per i carichi di lavoro dell'organizzazione. Oltre a questo livello di struttura, per soddisfare i requisiti a livello di criteri di governance dell'organizzazione per l'intero ambiente cloud è richiesta la capacità di organizzare, distribuire e gestire le risorse in modo coerente all'interno di una sottoscrizione.

![Grafico delle opzioni relative alla coerenza delle risorse, dalla meno complessa alla più complessa, allineato con i collegamenti sotto](../../_images/decision-guides/decision-guide-resource-consistency.png)

Passare a: [Raggruppamento di base](#basic-grouping) | [Coerenza di distribuzione](#deployment-consistency) | [Coerenza dei criteri](#policy-consistency) | [Coerenza gerarchica](#hierarchical-consistency) | [Coerenza automatizzata](#automated-consistency)

Le decisioni relative al livello di requisiti di coerenza delle risorse dell'ambiente cloud sono guidate principalmente da questi fattori: le dimensioni del digital estate dopo la migrazione, i requisiti dell'azienda o dell'ambiente che non si adattano perfettamente agli approcci di progettazione delle sottoscrizioni esistenti o la necessità di applicare la governance nel tempo dopo la distribuzione delle risorse.

Man mano che questi fattori acquisiscono maggiore importanza, diventano più rilevanti i vantaggi derivanti dal garantire coerenza per la distribuzione, il raggruppamento e la gestione delle risorse basate su cloud. Ottenere livelli più avanzati di coerenza delle risorse per soddisfare requisiti maggiori richiede maggiore sforzo per l'applicazione di automazione, strumenti e coerenza, con conseguente maggior tempo dedicato al rilevamento e alla gestione delle modifiche.

## <a name="basic-grouping"></a>Raggruppamento di base

In Azure i [gruppi di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) sono un meccanismo principale di organizzazione delle risorse che consente di raggruppare le risorse in modo logico all'interno di una sottoscrizione.

I gruppi di risorse fungono da contenitori per le risorse con un ciclo di vita comune e vincoli di gestione condivisi, ad esempio requisiti di criteri o di controllo degli accessi in base al ruolo. I gruppi di risorse non possono essere nidificati e le risorse possono appartenere a un solo gruppo di risorse. Tutte le azioni del piano di controllo si applicano a tutte le risorse di un gruppo. Con l'eliminazione di un gruppo di risorse, ad esempio, vengono eliminate anche tutte le risorse al suo interno. Per scegliere il modello di gestione dei gruppi di risorse, valutare quanto segue:

1. I contenuti del gruppo di risorse vengono sviluppati insieme?
1. I contenuti del gruppo di risorse vengono gestiti, aggiornati e monitorati insieme e queste attività vengono svolte dalle stesse persone o dagli stessi team?
1. I contenuti del gruppo di risorse vengono ritirati insieme?

Se la risposta è _NO_ a una di queste domande, la risorsa in questione dovrebbe essere inserita altrove, in un altro gruppo di risorse.

> [!IMPORTANT]
> I gruppi di risorse sono anche specifici per area, però spesso le risorse si trovano in aree diverse all'interno dello stesso gruppo, perché vengono gestite insieme, come descritto sopra. Per altre informazioni sulla selezione dell'area, vedere la [Guida alla decisione sulle aree](../regions/index.md).

## <a name="deployment-consistency"></a>Coerenza di distribuzione

La piattaforma Azure offre un sistema, basato sul meccanismo di raggruppamento delle risorse di base, che consente di usare modelli per distribuire le risorse nell'ambiente cloud. È possibile usare i modelli per creare convenzioni di denominazione e organizzazione coerenti per distribuire i carichi di lavoro, applicando i vari aspetti della progettazione della distribuzione e gestione delle risorse.

I [modelli di Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) consentono di distribuire ripetutamente le risorse in uno stato coerente usando una configurazione e una struttura dei gruppi di risorse predeterminate. Con questi modelli è possibile definire facilmente un set di standard come base delle distribuzioni.

Ad esempio, si può usare un modello standard per distribuire un carico di lavoro di server Web che contiene due macchine virtuali come server Web combinati con un servizio di bilanciamento del carico per distribuire il traffico tra i server. È quindi possibile riutilizzare questo modello per creare set di macchine virtuali e bilanciamento del carico strutturalmente identici ogni volta che è necessario questo tipo di carico di lavoro, cambiando solo il nome e l'indirizzo IP della distribuzione.

È anche possibile distribuire questi modelli a livello di codice e integrarli con i sistemi CI/CD.

## <a name="policy-consistency"></a>Coerenza dei criteri

Per assicurare che i criteri di governance siano applicati al momento della creazione delle risorse, parte della progettazione del raggruppamento delle risorse prevede l'uso di una configurazione comune per distribuire le risorse.

Combinando gruppi di risorse e modelli di Resource Manager standardizzati, è possibile applicare standard relativi alle impostazioni necessarie in una distribuzione e alle regole di [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) da applicare a ogni gruppo di risorse o risorsa.

Supponiamo ad esempio che esista un requisito in base al quale tutte le macchine virtuali distribuite all'interno della sottoscrizione devono connettersi a una subnet comune gestita dal team IT centrale. È possibile creare un modello standard per la distribuzione di macchine virtuali del carico di lavoro, che crea un gruppo di risorse separato per il carico di lavoro e vi distribuisce le macchine virtuali necessarie. Questo gruppo di risorse deve avere una regola dei criteri che consente di aggiungere alla subnet condivisa solo le interfacce di rete all'interno del gruppo di risorse.

Per una discussione più approfondita in merito all'applicazione delle decisioni relative ai criteri in una distribuzione cloud, vedere [Imposizione dei criteri](../policy-enforcement/index.md).

## <a name="hierarchical-consistency"></a>Coerenza gerarchica

I gruppi di risorse consentono di supportare livelli di gerarchia aggiuntivi all'interno dell'organizzazione all'interno della sottoscrizione, applicando regole di Criteri di Azure e controlli di accesso a livello di gruppo di risorse. Tuttavia, man mano che aumentano le dimensioni dell'ambiente cloud, potrebbe presentarsi la necessità di supportare requisiti di governance per le sottoscrizioni più complessi di quelli che possono essere supportati mediante la gerarchia azienda/reparto/account/sottoscrizione del contratto Enterprise di Azure.

I [gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups) consentono di organizzare le sottoscrizioni in strutture organizzative più elaborate, raggruppando le sottoscrizioni in una gerarchia distinta dalla gerarchia del contratto aziendale. Questa gerarchia alternativa consente di applicare meccanismi di controllo di accesso e applicazione dei criteri a più sottoscrizioni e alle risorse in esse contenute. Le gerarchie di gruppi di gestione possono essere usate per allineare le sottoscrizioni dell'ambiente cloud ai requisiti operativi o di governance aziendale. Per altre informazioni, vedere la [guida alle decisioni relative alle sottoscrizioni](../subscriptions/index.md).

## <a name="automated-consistency"></a>Coerenza automatizzata

Per le distribuzioni cloud di grandi dimensioni, la governance globale diventa tanto più importante quanto più complessa. È fondamentale applicare automaticamente i requisiti di governance durante la distribuzione delle risorse, oltre a soddisfare i requisiti aggiornati per le distribuzioni esistenti.

[Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) consente alle organizzazioni di supportare la governance globale di ambienti cloud estesi in Azure. Blueprints va oltre le funzionalità fornite da modelli di Azure Resource Manager standard, permettendo di creare orchestrazioni di distribuzione complete in grado di distribuire le risorse e applicare regole dei criteri. Blueprints supporta il controllo delle versioni, la possibilità di aggiornare tutte le sottoscrizioni in cui è stato usato il progetto e la possibilità di bloccare le sottoscrizioni distribuite per evitare la creazione e la modifica non autorizzate di risorse.

Questi pacchetti di distribuzione consentono ai team IT e di sviluppo di distribuire rapidamente nuovi carichi di lavoro e risorse di rete conformi alle variazioni dei requisiti relativi ai criteri organizzativi. Blueprints può anche essere integrato in pipeline CI/CD per applicare standard di governance modificati alle distribuzioni quando vengono aggiornate.

## <a name="next-steps"></a>Passaggi successivi

La coerenza delle risorse è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
