---
title: Guida alla governance per aziende standard
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guida alla governance per aziende standard
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 059e60e44ccf393bb731005bd4a579f3e3e41951
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547587"
---
# <a name="standard-enterprise-governance-guide"></a>Guida alla governance per aziende standard

## <a name="overview-of-best-practices"></a>Panoramica delle procedure consigliate

Questa guida segue le esperienze di una società fittizia attraverso le diverse fasi di evoluzione della governance. È basata su esperienze di clienti reali. Le procedure consigliate si basano sui vincoli e sulle esigenze della società fittizia.

Come punto di partenza rapido, questa panoramica definisce un prodotto minimo funzionante (MVP) per la governance basato su procedure consigliate. Fornisce inoltre i collegamenti ad alcuni miglioramenti della governance che offrono altre procedure consigliate in base all'emergere di nuovi rischi tecnici o aziendali.

> [!WARNING]
> Questo MVP è solo un punto di partenza, fondato su un insieme di ipotesi. Anche questo insieme minimo di procedure consigliate è basato su criteri aziendali determinati da rischi commerciali e tolleranze di rischio speciali. Per determinare se queste ipotesi si applicano alla propria situazione, vedere lo [scenario più approfondito](./narrative.md) che segue questo articolo.

### <a name="governance-best-practices"></a>Procedure consigliate per la governance

Queste procedure consigliate consentono a un'organizzazione di porre le basi per aggiungere in modo rapido e coerente misure di tutela per la governance tra sottoscrizioni di Azure.

### <a name="resource-organization"></a>Organizzazione delle risorse

Il diagramma seguente mostra la gerarchia dell'MVP per la governance per organizzare le risorse.

![Diagramma dell'organizzazione delle risorse](../../../_images/govern/resource-organization.png)

Tutte le applicazioni devono essere distribuite nell'area appropriata della gerarchia di gruppi di gestione, sottoscrizioni e gruppi di risorse. Durante la pianificazione della distribuzione, il team di governance del cloud creerà i nodi necessari nella gerarchia per i team responsabili dell'adozione del cloud.

1. Un gruppo di gestione per ogni tipo di ambiente (ad esempio produzione, sviluppo e test).
2. Due sottoscrizioni, una per la produzione e un'altra non per la produzione.
3. È necessario applicare una [nomenclatura coerente](../../../ready/considerations/naming-and-tagging.md) a ogni livello di questa gerarchia di gruppi.
4. I gruppi di risorse dovrebbero essere distribuiti in modo da tenere conto del ciclo di vita dei relativi contenuti: tutti quelli sviluppati, gestiti e ritirati insieme devono stare insieme. Per altre informazioni sulle procedure consigliate per i gruppi di risorse, vedere [qui](../../../decision-guides/resource-consistency/index.md).
5. La [scelta dell'area](../../../decision-guides/regions/index.md) è particolarmente importante, perché bisogna considerare la possibilità di implementare procedure di rete, monitoraggio e controllo per il failover/failback, oltre alla disponibilità [degli SKU necessari](https://azure.microsoft.com/global-infrastructure/services).

Ecco un esempio di questo modello in uso:

![Esempio di organizzazione delle risorse per una società midmarket](../../../_images/govern/mid-market-resource-organization.png)

Questi modelli lasciano un certo spazio per la crescita senza complicare inutilmente la gerarchia.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

## <a name="iterative-governance-improvements"></a>Miglioramenti iterativi della governance

Una volta distribuito l'MVP, è possibile integrare rapidamente livelli aggiuntivi di governance nell'ambiente. Ecco alcuni modi per trasformare l'MVP e soddisfare specifiche esigenze aziendali:

- [Baseline di sicurezza dei dati protetti](./security-baseline-improvement.md)
- [Configurazioni delle risorse per applicazioni cruciali](./resource-consistency-improvement.md)
- [Controlli per Gestione dei costi](./cost-management-improvement.md)
- [Controlli per l'evoluzione multi-cloud](./multicloud-improvement.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>Che cosa offrono queste linee guida?

Nell'MVP vengono definiti strumenti e procedure della disciplina di [accelerazione della distribuzione](../../deployment-acceleration/index.md) per applicare rapidamente criteri aziendali. In particolare, l'MVP usa Azure Blueprints, Criteri di Azure e gruppi di gestione di Azure per applicare alcuni criteri aziendali di base, secondo quanto definito nello scenario per questa società fittizia. Questi criteri aziendali vengono applicati tramite modelli di Resource Manager e criteri di Azure per stabilire una baseline minima per identità e sicurezza.

![Esempio di un MVP per la governance incrementale](../../../_images/govern/governance-mvp.png)

## <a name="incremental-improvement-of-governance-practices"></a>Miglioramento incrementale delle procedure di governance

Nel corso del tempo, questo MVP per la governance verrà usato per migliorare le procedure necessarie. Con il progredire dell'adozione, aumentano i rischi aziendali. Le varie discipline all'interno del modello di governance Cloud Adoption Framework cambieranno per mitigare questi rischi. Gli articoli successivi di questa serie illustrano il miglioramento incrementale dei criteri aziendali che interessano la società fittizia. Questi miglioramenti si verificano in tre discipline:

- Gestione dei costi, con il ridimensionarsi dell'adozione.
- Baseline di sicurezza, man mano che vengono distribuiti dati protetti.
- Coerenza delle risorse, man mano che il team responsabile delle operazioni IT inizia a supportare carichi di lavoro cruciali.

![Esempio di MVP per una governance incrementale](../../../_images/govern/governance-improvement.png)

## <a name="next-steps"></a>Passaggi successivi

Ora che si ha familiarità con l'MVP per la governance e un'idea dei miglioramenti da apportare, consultare lo scenario associato per altre informazioni sul contesto.

> [!div class="nextstepaction"]
> [Consultare lo scenario associato](./narrative.md)
