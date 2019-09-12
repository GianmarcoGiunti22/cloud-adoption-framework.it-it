---
title: Eseguire una verifica di criteri cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come condurre una revisione dei criteri cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ec3cc2eda1cd3c67b2d5e8c2f7dc04a8867622aa
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70826940"
---
<!-- markdownlint-disable MD026 -->

# <a name="conduct-a-cloud-policy-review"></a>Eseguire una verifica di criteri cloud

Una revisione dei criteri cloud è il primo passo verso la [maturità della governance](../index.md) nel cloud. L'obiettivo di questo processo è quello di modernizzare i criteri IT aziendali esistenti. Al termine, i criteri aggiornati forniscono un livello equivalente di gestione dei rischi per le risorse basate sul cloud. Questo articolo descrive il processo di revisione dei criteri per il cloud e la sua importanza.

## <a name="why-perform-a-cloud-policy-review"></a>Perché eseguire una revisione dei criteri per il cloud?

La maggior parte delle aziende gestisce l'IT tramite l'esecuzione di processi allineati ai criteri di governance. Nelle piccole imprese questi criteri possono essere aneddotici e basarsi su processi definiti in modo vago. Di pari passo con l'espansione delle aziende, i criteri e i processi tendono a essere documentati più chiaramente ed eseguiti in modo coerente.

Man mano che le organizzazioni maturano i propri criteri IT aziendali, le dipendenze dalle decisioni tecniche prese in precedenza tendono a diffondersi come criteri di governance. Ad esempio, è comune che i processi di ripristino di emergenza includano criteri che impongono il backup su nastro esterno. Questa decisione presuppone una dipendenza da un tipo di tecnologia (backup su nastro) che potrebbe non essere più la soluzione ideale.

Le trasformazioni cloud creano un punto di flessione naturale per riconsiderare le decisioni relative ai criteri legacy del passato. Le funzionalità tecniche e i processi predefiniti cambiano notevolmente nel cloud, così come i rischi ereditati. Utilizzando l'esempio precedente, il criterio di backup su nastro è stato associato al rischio di un singolo punto di errore mantenendo i dati in un'unica posizione e la necessità di ridurre al minimo il profilo di rischio mitigando questo rischio. In una distribuzione cloud sono disponibili diverse opzioni per la stessa mitigazione dei rischi, con obiettivi del tempi di ripristino (RTO, Recovery Time Objective) molto inferiori. Ad esempio:

- Una soluzione nativa del cloud potrebbe abilitare la replica geografica del database SQL di Azure.
- Una soluzione ibrida può usare Azure Site Recovery per replicare un carico di lavoro IaaS in più data center.

Quando si esegue una trasformazione per il cloud, spesso i criteri determinano molti degli strumenti, dei servizi e dei processi disponibili per i team di adozione del cloud. Se questi criteri si basano su tecnologie legacy, possono intralciare gli sforzi del team mirati all'attuazione delle modifiche. Nel peggiore dei casi i criteri importanti vengono completamente ignorati dal team di migrazione per abilitare soluzioni alternative. Nessuno dei due è un risultato accettabile.

## <a name="the-cloud-policy-review-process"></a>Processo di revisione dei criteri per il cloud

Le revisioni dei criteri cloud allineano la governance IT e i criteri di sicurezza IT esistenti con le [cinque discipline della governance cloud](../index.md): [Gestione costi](../cost-management/index.md), [Baseline di sicurezza](../security-baseline/index.md), [Baseline di identità](../identity-baseline/index.md), [Coerenza delle risorse](../resource-consistency/index.md) e [Accelerazione della distribuzione](../deployment-acceleration/index.md).

Per ognuna di queste discipline, il processo di revisione segue questi passaggi:

1. Rivedere i criteri locali esistenti correlati alla disciplina specifica, prestando particolare attenzione a due punti dati chiave: dipendenze legacy e rischi aziendali identificati.
2. Valutare ogni rischio aziendale ponendo una semplice domanda: "Il rischio aziendale sussiste ancora in un modello di cloud?"
3. Se il rischio persiste, riscrivere il criterio documentando la mitigazione necessaria e non la soluzione tecnica.
4. Rivedere i criteri aggiornati con i team di adozione del cloud per comprendere le potenziali soluzioni per la mitigazione richiesta.

## <a name="example-of-a-policy-review-for-a-legacy-policy"></a>Esempio di una revisione dei criteri per un criterio legacy

Per fornire un esempio del processo, è possibile usare nuovamente il criterio di backup su nastro presentato nella sezione precedente:

- Un criterio aziendale impone i backup su nastro esterni per tutti i sistemi di produzione. In questo criterio è possibile vedere due punti dati di interesse:
  - Dipendenza legacy da una soluzione di backup su nastro
  - Rischio aziendale presunto associato all'archiviazione dei backup nella stessa posizione fisica delle attrezzature di produzione.
- Il rischio sussiste ancora? Sì. Anche nel cloud una dipendenza da una singola funzionalità crea un rischio. Ci sono minori probabilità che interessi l'azienda rispetto alla soluzione in locale, ma tale rischio esiste comunque.
- Riscrivere il criterio. In caso di emergenza a livello di data center, deve esistere un modo per ripristinare i sistemi di produzione entro 24 ore dall'interruzione del servizio in un altro data center e in un'area geografica diversa.
- Procedere alla revisione con i team di adozione del cloud. A seconda della soluzione implementata, ci sono più modi per rispettare questo criterio di Coerenza delle risorse.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sull'inclusione della classificazione dei dati nella strategia di governance del cloud.

> [!div class="nextstepaction"]
> [Classificazione dei dati](./what-is-data-classification.md)
