---
title: Guide all'architettura decisionale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle guide all'architettura decisionale nel Framework di adozione del Cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 2ca59288d74b8a7578a91a160f3c3960ac3cedda
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71023852"
---
# <a name="architectural-decision-guides"></a>Guide all'architettura decisionale

Le guide all'architettura decisionale nel Framework di adozione del Cloud descrivono i modelli e gli schemi che aiutano quando si crea una guida alla progettazione della governance del cloud. Ogni guida è incentrata su un componente fondamentale dell'infrastruttura delle distribuzioni cloud ed elenca gli schemi e i modelli in grado di supportare scenari specifici.

Quando si inizia a definire la governance del cloud per l'organizzazione, i percorsi di governance attuabili forniscono una roadmap di base. Tuttavia, questi percorsi fanno ipotesi sui requisiti e le priorità che potrebbero non riflettere quelle della propria organizzazione.

Tali guide decisionali integrano i percorsi di esempio di governance, fornendo schemi e modelli alternativi che aiutano ad allineare con le proprie esigenze le scelte di progettazione architetturale prese nella guida di progettazione di esempio.

## <a name="decision-guidance-categories"></a>Categorie di indicazioni per le decisioni

Ognuna delle categorie seguenti rappresenta una tecnologia di base di tutte le distribuzioni cloud. I percorsi di governance di esempio prendono decisioni di progettazione relative a queste tecnologie in base alle esigenze delle aziende di esempio e alcune di queste decisioni potrebbero non corrispondere alle esigenze specifiche dell'organizzazione. Le sezioni seguenti illustrano opzioni alternative per ognuna di queste categorie, consentendo di scegliere uno schema o un modello più adatto alle proprie esigenze.

[Sottoscrizioni](./subscriptions/index.md): pianificare la struttura della sottoscrizione e la struttura dell'account della distribuzione cloud in modo che corrisponda alle proprietà, alla fatturazione e alle capacità di gestione dell'organizzazione.

[Identità](./identity/index.md): integrare servizi di identità basati sul cloud con le risorse di identità esistenti per supportare il processo di autorizzazione e il controllo di accesso all'interno dell'ambiente IT.

[Imposizione dei criteri](./policy-enforcement/index.md): definire e applicare regole di criteri dell'organizzazione per le risorse e i carichi di lavoro distribuiti nel cloud in linea con i requisiti di governance.

[Coerenza delle risorse](./resource-consistency/index.md): assicurarsi che la distribuzione e l'organizzazione delle risorse basate su cloud siano allineate per far rispettare i requisiti di gestione delle risorse e dei criteri.

[Tag delle risorse](./resource-tagging/index.md): organizzare le risorse basate sul cloud per supportare i modelli di fatturazione, gli approcci di accounting cloud, la gestione e per ottimizzare l'utilizzo e i costi delle risorse. Il tag delle risorse richiede uno schema di denominazione e metadati coerente e ben organizzato.

[Reti definite dal software](./software-defined-network/index.md): distribuire i carichi di lavoro sicuri nel cloud usando una distribuzione rapida e la modifica della capacità di rete virtualizzata. Software defined networks (SDNs) può supportare flussi di lavoro agili, isolare le risorse e integrare i sistemi basati su cloud con l'infrastruttura IT esistente.

[Crittografia](./encryption/index.md): proteggere i dati sensibili con crittografia in modo da allinearsi ai requisiti di conformità e dei criteri di sicurezza dell'organizzazione.

[Log e report](./logging-and-reporting/index.md): monitorare i dati di log generati dalle risorse basate sul cloud. L'analisi dei dati fornisce informazioni dettagliate correlate all'integrità per le operazioni, la manutenzione e lo stato di conformità dei carichi di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come le sottoscrizioni e gli account servono da base di una distribuzione cloud.

> [!div class="nextstepaction"]
> [Progettazione delle sottoscrizioni](./subscriptions/index.md)
