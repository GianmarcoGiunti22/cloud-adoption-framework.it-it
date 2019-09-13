---
title: Guida alla governance per aziende complesse
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guida alla governance per aziende complesse
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c3962409f71f82319a6e5efc2313c03a44456298
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908422"
---
# <a name="governance-guide-for-complex-enterprises"></a>Guida alla governance per aziende complesse

## <a name="overview-of-best-practices"></a>Panoramica delle procedure consigliate

Questa guida segue le esperienze di una società fittizia attraverso le diverse fasi di evoluzione della governance. È basata su esperienze di clienti reali. Le procedure consigliate si basano sui vincoli e sulle esigenze della società fittizia.

Come punto di partenza rapido, questa panoramica definisce un prodotto minimo funzionante (MVP) per la governance basato su procedure consigliate. Fornisce inoltre i collegamenti ad alcuni miglioramenti della governance che offrono altre procedure consigliate in base all'emergere di nuovi rischi tecnici o aziendali.

> [!WARNING]
> Questo MVP è solo un punto di partenza, fondato su un insieme di ipotesi. Anche questo insieme minimo di procedure consigliate è basato su criteri aziendali determinati da rischi commerciali e tolleranze di rischio speciali. Per determinare se queste ipotesi si applicano alla propria situazione, vedere lo [scenario più approfondito](./narrative.md) che segue questo articolo.

### <a name="governance-best-practices"></a>Procedure consigliate per la governance

Queste procedure consigliate consentono a un'organizzazione di porre le basi per aggiungere in modo rapido e coerente misure di tutela per la governance tra più sottoscrizioni di Azure.

### <a name="resource-organization"></a>Organizzazione delle risorse

Il diagramma seguente mostra la gerarchia dell'MVP per la governance per organizzare le risorse.

![Diagramma dell'organizzazione delle risorse](../../../_images/governance/resource-organization.png)

Tutte le applicazioni devono essere distribuite nell'area appropriata della gerarchia di gruppi di gestione, sottoscrizioni e gruppi di risorse. Durante la pianificazione della distribuzione, il team di governance del cloud creerà i nodi necessari nella gerarchia per i team responsabili dell'adozione del cloud.

1. Definire un gruppo di gestione per ogni business unit con una gerarchia dettagliata che rifletta area geografica e tipo di ambiente (ad esempio produzione o non produzione).
1. Creare una sottoscrizione per ogni combinazione univoca di business unit, area geografica, ambiente e "Categorizzazione delle applicazioni".
1. Creare un gruppo di risorse distinto per ogni applicazione.
1. Applicare una [nomenclatura coerente](../../../ready/considerations/name-and-tag.md) a ogni livello di questa gerarchia di gruppi.

![Diagramma dell'organizzazione delle risorse per le grandi imprese](../../../_images/governance/large-enterprise-resource-organization.png)

Questi modelli lasciano un certo spazio per la crescita senza complicare inutilmente la gerarchia.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

<!-- See comments for suggestion to possibly add here -->

## <a name="incremental-governance-improvements"></a>Miglioramenti incrementali della governance

Una volta distribuito l'MVP, è possibile integrare livelli aggiuntivi di governance nell'ambiente. Ecco alcuni modi per trasformare l'MVP e soddisfare specifiche esigenze aziendali:

- [Baseline di sicurezza dei dati protetti](./security-baseline-evolution.md)
- [Configurazioni delle risorse per applicazioni cruciali](./resource-consistency-evolution.md)
- [Controlli per Gestione dei costi](./cost-management-evolution.md)
- [Controlli per il miglioramento incrementale del multicloud](./multicloud-evolution.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>Che cosa offrono queste linee guida?

Nell'MVP vengono definiti strumenti e procedure della disciplina di [accelerazione della distribuzione](../../deployment-acceleration/index.md) per applicare rapidamente criteri aziendali. In particolare, l'MVP usa Azure Blueprints, Criteri di Azure e gruppi di gestione di Azure per applicare alcuni criteri aziendali di base, secondo quanto definito nello scenario per questa società fittizia. Questi criteri aziendali vengono applicati tramite modelli di Azure Resource Manager e criteri di Azure per stabilire una baseline minima per identità e sicurezza.

![Esempio di un MVP per la governance incrementale](../../../_images/governance/governance-mvp.png)

## <a name="incremental-improvements-to-governance-practices"></a>Miglioramenti incrementali apportati alle procedure di governance

Nel corso del tempo, questo MVP per la governance verrà usato per migliorare in modo incrementale le procedure necessarie. Con il progredire dell'adozione, aumentano i rischi aziendali. Le varie discipline all'interno del modello di governance Cloud Adoption Framework verranno adattate per mitigare questi rischi. Gli articoli successivi di questa serie illustrano i cambiamenti dei criteri aziendali che interessano la società fittizia. Questi cambiamenti si verificano in quattro discipline:

- Baseline di identità, con le dipendenze della migrazione che cambiano nello scenario.
- Gestione dei costi, con il ridimensionarsi dell'adozione.
- Baseline di sicurezza, man mano che vengono distribuiti dati protetti.
- Coerenza delle risorse, man mano che il team responsabile delle operazioni IT inizia a supportare carichi di lavoro cruciali.

![Esempio di MVP per una governance incrementale](../../../_images/governance/governance-evolution-large.png)

## <a name="next-steps"></a>Passaggi successivi

Ora che si ha familiarità con l'MVP per la governance e un'idea dei cambiamenti previsti per il futuro, consultare lo scenario associato per altre informazioni sul contesto.

> [!div class="nextstepaction"]
> [Consultare lo scenario associato](./narrative.md)
