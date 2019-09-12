---
title: Motivazioni e rischi aziendali della gestione dei costi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivazioni e rischi aziendali della gestione dei costi
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 328352ac7ccd8cacbc92cc09ce0c07e2843afcf1
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829124"
---
# <a name="cost-management-motivations-and-business-risks"></a>Motivazioni e rischi aziendali della gestione dei costi

Questo articolo illustra i motivi per cui i clienti in genere adottano una disciplina Gestione costi all'interno di una strategia di governance del cloud. L'articolo offre anche alcuni esempi di rischi aziendali che determinano le definizioni dei criteri.

<!-- markdownlint-disable MD026 -->

## <a name="is-cost-management-relevant"></a>La gestione dei costi è rilevante?

In termini di governance dei costi, l'adozione del cloud crea una svolta. La gestione dei costi in un ambiente locale tradizionale si basa su cicli di aggiornamento, acquisizioni di data center, rinnovi di host e problemi di manutenzione ricorrenti. È possibile prevedere, pianificare e perfezionare ognuno di questi costi in modo da allinearli ai budget annui per le spese in conto capitale.

Per le soluzioni cloud, molte aziende tendono ad adottare un approccio più reattivo alla gestione dei costi. In molti casi, le aziende acquistano in anticipo o si impegnano a usare una quantità determinata di servizi cloud. Questo modello presuppone che ottenere sconti più alti possibile, in base a quanto l'azienda prevede di spendere con un fornitore di servizi cloud specifico, crei la percezione di un ciclo di costo pianificato e proattivo. Tale percezione, tuttavia, diventa realtà solo se l'azienda implementa anche discipline di gestione dei costi mature.

Il cloud offre funzionalità self-service mai viste nei data center locali tradizionali. Queste nuove funzionalità garantiscono alle aziende più flessibilità, meno limitazioni e maggiore apertura all'adozione di nuove tecnologie. Lo svantaggio delle funzionalità self-service, tuttavia, è la possibilità che gli utenti finali superino inconsapevolmente i budget allocati o che, al contrario, per intervenute modifiche ai piani, inaspettatamente non usino la quantità di servizi cloud prevista. La possibilità di uno spostamento in una o nell'altra direzione giustifica gli investimenti in una disciplina Gestione costi all'interno del team di governance.

## <a name="business-risk"></a>Rischio aziendale

La disciplina Gestione costi affronta i rischi aziendali di base correlati alle spese che si sostengono quando si ospitano carichi di lavoro basati sul cloud. Collaborare con l'azienda per identificare questi rischi e monitorarne la rilevanza durante la pianificazione e l'implementazione delle distribuzioni cloud.

I rischi si differenziano per l'organizzazione, ma i rischi correlati ai costi comuni che è possibile usare come punto di partenza per le discussioni all'interno del team di governance del cloud sono i seguenti:

- **Controllo budget:** Il mancato controllo del budget può portare a una spesa eccessiva con un fornitore di servizi cloud.
- **Perdita di utilizzo:** I preacquisti o i preimpegni che non vengono usati possono causare investimenti inutili.
- **Anomalie di spesa:** Picchi imprevisti in entrambe le direzioni possono indicare un utilizzo improprio.
- **Asset con provisioning eccessivo:** Se le risorse vengono distribuite in una configurazione che supera le esigenze di un'applicazione o di una macchina virtuale (VM, Virtual Machine), i costi possono aumentare e si possono creare sprechi.

## <a name="next-steps"></a>Passaggi successivi

Usando il [modello di gestione cloud](./template.md), documentare i rischi aziendali che probabilmente verranno introdotti dal piano di adozione del Cloud corrente.

Dopo aver stabilito in modo realistico i rischi aziendali, il passaggio successivo consiste nel documentare le metriche e gli indicatori principali della tolleranza ai rischi dell'azienda allo scopo di monitorare tale tolleranza.

> [!div class="nextstepaction"]
> [Indicatori, metriche e tolleranza ai rischi](./metrics-tolerance.md)
