---
title: 'Guida alla governance per le aziende complesse: Più livelli di governance'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: Più livelli di governance'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4efd5b3de5551297a6ef5813a5108f3ad039472c
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222295"
---
# <a name="governance-guide-for-complex-enterprises-multiple-layers-of-governance"></a>Guida alla governance per le aziende complesse: Più livelli di governance

Quando le aziende di grandi dimensioni richiedono più livelli di governance, esistono livelli maggiori di complessità che devono essere presi in considerazione nell'MVP di governance e nei miglioramenti di governance successivi.

Esempi comuni di tali complessità includono:

- Funzioni di governance distribuita.
- IT aziendale a supporto delle organizzazioni IT della Business Unit.
- IT aziendale a supporto delle organizzazioni IT distribuite geograficamente.

Questo articolo illustra alcuni modi per esplorare questo tipo di complessità.

## <a name="large-enterprise-governance-is-a-team-sport"></a>Governance per aziende di grandi dimensioni come sport di squadra

Grandi imprese stabilite spesso hanno team o dipendenti che si concentrano sulle discipline indicate in questa guida. In questa guida viene illustrato un approccio per rendere la governance uno sport del team.

In molte grandi aziende, le cinque discipline della governance del cloud possono essere blocchi da adottare. Lo sviluppo di competenze cloud in identità, sicurezza, operazioni, distribuzioni e configurazione all'interno di un'azienda richiede tempo. L'implementazione in modo completo dei criteri di governance IT e di sicurezza IT può contribuire a rallentare l'innovazione per mesi o addirittura anni. L'equilibrio tra la necessità di innovazione delle imprese e la necessità della governance di proteggere le risorse esistenti è delicato.

Le funzionalità intrinseche del cloud possono rimuovere i blocchi per l'innovazione, ma anche aumentare i rischi. In questa guida alla governance è stato illustrato come la società di esempio ha creato Guardrails per gestire i rischi. Invece di affrontare ogni disciplina necessaria per proteggere l'ambiente, il team di governance del cloud conduce un approccio basato sui rischi per gestire ciò che potrebbe essere distribuito, mentre gli altri team sviluppano le esigenze di maturazione del cloud. Soprattutto, mentre ogni team raggiunge la maturità cloud, la governance applica in modo completo le proprie soluzioni. Poiché ogni team ha maturato e aggiunto alla soluzione complessiva, il team di governance del cloud può aprire le attività di gestione temporanea, consentendo un'innovazione e un'adozione aggiuntive.

Questo modello illustra la crescita di una partnership tra il team di governance del cloud e i team aziendali esistenti (sicurezza, governance IT, rete, identità e altri). La guida inizia con l'MVP di governance e cresce fino a uno stato finale olistico attraverso le iterazioni di governance.

## <a name="requirements-to-supporting-such-a-team-sport"></a>Requisiti per il supporto di questo sport di squadra

Il primo requisito di un modello di governance multistrato consiste nel comprendere la gerarchia di governance. La risposta alle domande seguenti consentirà di comprendere la gerarchia di governance generale:

- Dove si posiziona la contabilità del cloud (fatturazione per i servizi cloud) tra le unità aziendali?
- Dove si posizionano le responsabilità di governance nel panorama IT aziendale e tra ogni business unit?
- Quali tipi di ambiente vengono gestiti da ciascuna di queste unità IT?

## <a name="central-governance-of-a-distributed-governance-hierarchy"></a>Governance centrale di una gerarchia di governance distribuita

Strumenti come i gruppi di gestione consentono all'IT aziendale di creare una struttura gerarchica che corrisponde alla gerarchia di governance. Strumenti come Azure Blueprints possono applicare le risorse a diversi livelli di quella gerarchia. Azure Blueprints può disporre di versioni e varie di queste possono essere applicate a gruppi di gestione, abbonamenti o gruppi di risorse. Ognuno di questi concetti viene descritto più nei dettagli nell'MVP della governance.

L'aspetto importante di ogni strumento è la capacità di applicare più progetti a una gerarchia. Questo permette alla governance di diventare un processo a più livelli. L'esempio seguente mostra questa applicazione gerarchica di governance:

- **IT aziendale:** l'IT aziendale crea un insieme di standard e politiche che si applicano a tutta l'adozione del cloud. Ciò si concretizza in un progetto "Baseline". L'IT aziendale è quindi proprietaria della gerarchia del gruppo dirigente, assicurando che una versione della baseline sia applicata a tutte le sottoscrizioni della gerarchia.
- **Regione o Business Unit IT:** diversi team IT possono applicare un ulteriore livello di governance creando il loro progetto. Questi progetti creerebbero politiche e standard cumulativi. Una volta sviluppato, l'IT aziendale potrebbe applicare questi progetti ai nodi applicabili all'interno della gerarchia dei gruppi di gestione.
- **Team di adozione del cloud:** Le decisioni dettagliate e l'implementazione delle applicazioni o dei carichi di lavoro possono essere eseguite da ogni team di adozione del cloud, entro il contesto dei requisiti di governance. A volte il team può anche richiedere ulteriori modelli di coerenza di Azure Resource per accelerare le attività di adozione.

I dettagli relativi all'attuazione della governance a ogni livello richiederanno un coordinamento tra i vari gruppi di lavoro. I miglioramenti apportati alla governance MVP e alla governance descritti in questa guida consentono di allineare il coordinamento.
