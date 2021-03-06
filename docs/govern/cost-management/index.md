---
title: Panoramica della disciplina Gestione costi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione della disciplina Gestione costi in relazione alla governance del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: ac6c3cb0a26cebf655a1161a3fd54197c795c283
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566415"
---
# <a name="cost-management-discipline-overview"></a>Panoramica della disciplina Gestione costi

Gestione costi è una delle [cinque discipline della governance del cloud](../governance-disciplines.md) nell'ambito del [modello di governance Cloud Adoption Framework](../index.md). Per molti clienti, la gestione dei costi è una delle principali preoccupazioni riguardo all'adozione di tecnologie cloud. Trovare il giusto equilibrio tra esigenze di prestazioni, tempi di implementazione e costi dei servizi cloud può rivelarsi un'impresa difficile. Ciò è particolarmente importante per le trasformazioni aziendali di maggiore entità in cui vengono implementate tecnologie cloud. Questa sezione illustra l'approccio da adottare per sviluppare una disciplina Gestione costi come parte di una strategia di governance del cloud.

> [!NOTE]
> La disciplina di governance Gestione costi non sostituisce i team di gestione aziendale, le pratiche contabili e le procedure già esistenti nell'ambito della gestione finanziaria dei costi correlati all'IT di un'organizzazione. Lo scopo principale di questa disciplina è identificare i potenziali rischi del cloud in relazione alla spesa IT e fornire indicazioni per la mitigazione di tali rischi ai team responsabili delle attività aziendali e dell'IT che sono incaricati della distribuzione e della gestione delle risorse cloud.

I principali destinatari di queste linee guida sono gli architetti dell'infrastruttura cloud delle organizzazioni e gli altri membri del team di governance del cloud. Tuttavia, le decisioni, i criteri e i processi che emergono da questa disciplina dovrebbero coinvolgere anche i membri appropriati dei team che si occupano delle attività aziendali e dell'IT, soprattutto i responsabili della proprietà, della gestione e dei pagamenti relativi ai carichi di lavoro basati sul cloud.

## <a name="policy-statements"></a>Policy statements

Una disciplina Gestione costi si basa principalmente sulle definizioni dei criteri in base ai quali prendere decisioni operative e sui requisiti dell'architettura risultanti. Per esempi di definizioni dei criteri, vedere l'articolo [Definizioni dei criteri di esempio per la gestione dei costi](./policy-statements.md). Questi esempi possono essere usati come punto di partenza per definire i criteri di governance della propria organizzazione.

> [!CAUTION]
> I criteri di esempio sono stati sviluppati in base a esperienze comuni dei clienti. Per allineare questi criteri a specifiche esigenze di governance del cloud, eseguire i passaggi seguenti in modo da creare definizioni dei criteri in grado di soddisfare le esigenze specifiche della propria organizzazione.

## <a name="develop-governance-policy-statements"></a>Sviluppare dichiarazioni per i criteri di governance

I sei passaggi seguenti consentono di definire i criteri di governance per controllare i costi nel proprio ambiente.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsE">
<li style="display: flex; flex-direction: column;">
    <a href="./template.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-template.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Modello di gestione dei costi</h3>
                        <p class="x-hidden-focus">Scaricare il modello per documentare una disciplina Gestione costi</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li><li style="display: flex; flex-direction: column;">
    <a href="./business-risks.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-risks.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Rischi aziendali</h3>
                        <p class="x-hidden-focus">Motivazioni e rischi comunemente associati alla disciplina Gestione costi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./metrics-tolerance.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-metrics.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Indicatori e metriche</h3>
                        <p class="x-hidden-focus">Indicatori per capire se è il momento giusto per investire nella disciplina Gestione costi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./compliance-processes.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-enforce.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Processi di adesione ai criteri</h3>
                        <p class="x-hidden-focus">Processi consigliati per supportare la conformità ai criteri della disciplina Gestione costi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./discipline-improvement.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-maturity.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Livello di maturità</h3>
                        <p class="x-hidden-focus">Allineare il livello di maturità della gestione del cloud alle fasi di adozione del cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./toolchain.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-toolchain.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Toolchain</h3>
                        <p class="x-hidden-focus">Servizi di Azure che è possibile implementare per supportare la disciplina Gestione costi.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Passaggi successivi

Iniziare con la valutazione dei rischi aziendali in un determinato ambiente.

> [!div class="nextstepaction"]
> [Informazioni sui rischi aziendali](./business-risks.md)

<!-- markdownlint-enable MD033 -->
