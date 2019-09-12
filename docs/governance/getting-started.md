---
title: Definire una fondazione di governance cloud iniziale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Inizia a usare il cloud governance stabilendo una Fondazione cloud governance iniziale.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: f12ef1603ae0749aa893f0631481ec30ed881379
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906066"
---
# <a name="establish-an-initial-cloud-governance-foundation"></a>Definire una fondazione di governance cloud iniziale

La definizione della governance cloud è un'operazione iterativa molto ampia. È difficile trovare un equilibrio efficace tra velocità e controllo, soprattutto durante le fasi iniziali dell'adozione del cloud. Il materiale sussidiario per la governance nel Framework di adozione del cloud contribuisce a garantire il giusto equilibrio tramite un approccio agile all'adozione.

Questo articolo fornisce due opzioni per stabilire una base iniziale per la governance. Entrambe le opzioni assicurano che i vincoli di governance possano essere ridimensionati ed espansi quando il piano di adozione viene implementato e i requisiti vengono definiti in modo più chiaro. Per impostazione predefinita, la base iniziale presuppone una posizione di isolamento e controllo. Inoltre, si concentra maggiormente sull'organizzazione delle risorse rispetto alla governance delle risorse. Questo punto di partenza leggero viene chiamato un _prodotto minimo valido (MVP)_ per la governance. L'obiettivo dell'MVP consiste nel ridurre le barriere alla definizione di una posizione di governance iniziale e quindi consentire una rapida maturazione della soluzione per risolvere diversi rischi tangibili.

## <a name="already-using-the-cloud-adoption-framework"></a>Uso già del Framework di adozione del cloud

Se si è stati seguiti insieme al Framework di adozione del cloud, è possibile che sia già stato distribuito un MVP di governance. Le linee guida sono un aspetto fondamentale di qualsiasi modello operativo. È presente durante ogni fase del ciclo di vita dell'adozione del cloud. Di conseguenza, il [Framework di adozione del cloud](../index.md) fornisce indicazioni che inseriscono la governance in attività correlate all'implementazione del [piano di adozione del cloud](../plan/index.md). Un esempio di questa integrazione della governance prevede l'uso di progetti per distribuire una o più zone di destinazione presenti nelle linee guida [pronte](../ready/index.md) . Un altro esempio è materiale sussidiario per la [scalabilità orizzontale delle sottoscrizioni](../ready/considerations/scaling-subscriptions.md). Se è stata seguita una di queste raccomandazioni, le sezioni MVP seguenti sono semplicemente una revisione delle decisioni di distribuzione esistenti. Dopo una rapida verifica, passare a una [soluzione avanzata per la governance iniziale e applicare i controlli per le procedure consigliate](./best-practices.md).

## <a name="establish-an-initial-governance-foundation"></a>Definire una base di governance iniziale

Di seguito sono riportati due esempi diversi di fondazioni di governance iniziali (detti anche MVP di governance) per applicare una valida base per la governance alle distribuzioni nuove o esistenti. Per iniziare, scegliere il MVP più allineato alle esigenze aziendali:

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./journeys/standard-enterprise/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida alla governance standard</h3>
                        <p>Guida per la maggior parte delle organizzazioni basata sul modello a due sottoscrizioni consigliato, progettato per le distribuzioni in più aree, ma non per i cloud pubblici e governativi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./journeys/complex-enterprise/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida alla governance per le aziende complesse</h3>
                        <p>Guida per le aziende gestite da più unità aziendali IT indipendenti o che si estendono su cloud pubblici e sovrani/governativi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Passaggi successivi

Una volta attuata una Fondazione governance, applicare consigli appropriati per migliorare la soluzione e proteggersi da rischi tangibili.

> [!div class="nextstepaction"]
> [Migliorare la base di governance iniziale](./best-practices.md)
