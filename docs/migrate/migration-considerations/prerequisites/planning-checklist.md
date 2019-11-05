---
title: Elenco di controllo della pianificazione dell'ambiente di migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Convalidare l'idoneità dell'ambiente prima della migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7a71b5694849533b6a01b98d9e14d5022e7287f8
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564562"
---
# <a name="migration-environment-planning-checklist-validate-environmental-readiness-prior-to-migration"></a>Elenco di controllo della pianificazione dell'ambiente di migrazione: convalidare la conformità ambientale prima della migrazione

Come passaggio iniziale del processo di migrazione, è necessario creare l'ambiente appropriato nel cloud per ricevere, ospitare e supportare gli asset di migrazione. Questo articolo fornisce un elenco di elementi da convalidare nell'ambiente corrente prima della migrazione.

L'elenco di controllo seguente è allineato alle indicazioni fornite nella [sezione relativa alla preparazione](../../../ready/index.md) in Cloud Adoption Framework. Esaminare questa sezione per indicazioni sull'esecuzione di una delle seguenti attività.

## <a name="effort-type-assumption"></a>Supposizione del tipo di lavoro richiesto

Questo articolo e l'elenco di controllo suppongono un approccio di _rehosting_ o _transizione nel cloud_ per la migrazione al cloud.

## <a name="governance-alignment"></a>Allineamento della governance

La prima decisione e anche la più importante relativa a un ambiente pronto per la migrazione è la scelta dell'allineamento della governance. Valutare se è stato raggiunto un consenso per l'allineamento della governance con l'impostazione della migrazione. Come minimo, il team di adozione del cloud deve comprendere se questa migrazione ha come destinazione un singolo ambiente con governance limitata, una factory di ambiente completamente regolamentata o una variante intermedia di queste due opzioni. Per altre opzioni e indicazioni sull'allineamento della governance, vedere l'articolo sull'[allineamento di governance e conformità](../../expanded-scope/governance-or-compliance.md).

## <a name="cloud-readiness-implementation"></a>Implementazione dell'idoneità per il cloud

Che si scelga o meno di allinearsi a una strategia di governance del cloud più ampia per la migrazione iniziale, sarà necessario assicurarsi che l'ambiente di distribuzione cloud sia configurato per supportare i carichi di lavoro.

Se si prevede di allineare la migrazione a una strategia di governance del cloud dall'inizio, sarà necessario applicare le [cinque discipline di governance del cloud](../../../govern/governance-disciplines.md) per fornire informazioni sulle decisioni relative a criteri, toolchain e meccanismi di alineamento dell'ambiente cloud a requisiti aziendali complessivi. Consultare le [guide di progettazione per la governance di utilità pratica](../../../govern/guides/index.md) di Cloud Adoption Framework per gli esempi di implementazione di questo modello con i servizi di Azure.

Se le migrazioni iniziali non sono strettamente allineate a una strategia di governance del cloud più ampia, sarà ancora necessario gestire i problemi generali di organizzazione, accesso e pianificazione dell'infrastruttura. Consultare la [Guida all'installazione di Azure](../../../ready/azure-setup-guide/index.md) per informazioni sulle decisioni di conformità del cloud.

> [!CAUTION]
> Si consiglia vivamente di sviluppare una strategia di governance per tutti gli aspetti che esulano dalla migrazione iniziale del carico di lavoro.

Indipendentemente dal livello di allineamento della governance, sarà necessario prendere decisioni sugli argomenti seguenti.

### <a name="resource-organization"></a>Organizzazione delle risorse

In base alla decisione di allineamento per la governance, è necessario stabilire un approccio per l'organizzazione e la distribuzione delle risorse prima della migrazione.

### <a name="nomenclature"></a>Nomenclatura

Prima della migrazione, è necessario stabilire un approccio uniforme per la denominazione delle risorse, insieme a schemi di denominazione coerenti.

### <a name="resource-governance"></a>Governance delle risorse

Prima di eseguire la migrazione, è necessario scegliere gli strumenti per la governance delle risorse. Gli strumenti non devono essere completamente implementati, ma è necessario selezionare e testare un orientamento. È consigliabile che il team di governance del cloud definisca e richieda l'implementazione di un prodotto minimo funzionante per gli strumenti di governance prima della migrazione.

## <a name="network"></a>Rete

I carichi di lavoro basati sul cloud richiederanno il provisioning di reti virtuali per supportare l'accesso amministrativo e degli utenti finali. In base alle decisioni relative all'organizzazione e alla governance delle risorse, è necessario scegliere una strategia per la rete e allinearla ai requisiti di sicurezza IT. Inoltre, le decisioni relative alla rete devono essere allineate a eventuali vincoli di reti ibride necessari per gestire i carichi di lavoro nel backlog di migrazione e supportare gli accessi alle risorse ospitate in locale.

## <a name="identity"></a>Identità

I servizi di identità basati sul cloud sono un prerequisito per offrire la gestione delle identità e degli accessi (IAM) per le risorse cloud. Prima di procedere, allineare la strategia di gestione delle identità ai piani di adozione del cloud. Ad esempio, quando si esegue la migrazione di asset locali esistenti, è consigliabile supportare un approccio di identità ibride con la [sincronizzazione delle directory](../../../decision-guides/identity/index.md) per consentire un set coerente di credenziali utente negli ambienti locali e cloud durante e dopo la migrazione.

## <a name="next-steps"></a>Passaggi successivi

Se l'ambiente soddisfa i requisiti minimi, può essere considerato approvato per l'idoneità per la migrazione. La [complessità culturale e la gestione del cambiamento](./cultural-complexity.md) consentono di allineare i ruoli e le responsabilità per garantire aspettative appropriate durante l'esecuzione del piano.

> [!div class="nextstepaction"]
> [Complessità culturale e gestione del cambiamento](./cultural-complexity.md)
