---
title: panoramica della disciplina di accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione dell'accelerazione della distribuzione in relazione alla governance del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 9de6f01a4252383c1d7619078568964fe8e685c9
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566360"
---
# <a name="deployment-acceleration-discipline-overview"></a>panoramica della disciplina di accelerazione della distribuzione

L'accelerazione della distribuzione è una delle [cinque discipline della governance del cloud](../governance-disciplines.md) nell'ambito del [modello di governance Cloud Adoption Framework](../index.md). Questa disciplina è incentrata sulle modalità di definizione dei criteri per definire la configurazione o la distribuzione di risorse. All'interno delle cinque discipline della governance del cloud, l'accelerazione della distribuzione include distribuzione, allineamento della configurazione e riusabilità degli script, tramite attività manuali o tramite attività DevOps completamente automatizzate. In entrambi i casi, i criteri rimangono in gran parte gli stessi. Man mano che questo disciplina viene perfezionata, il team di governance del cloud può fungere da partner nelle strategie DevOps e di distribuzione promuovendo l'accelerazione delle distribuzioni e la rimozione degli ostacoli per l'adozione del cloud tramite l'applicazione di asset riutilizzabili.

Questo articolo illustra il processo di accelerazione della distribuzione in un'azienda durante la pianificazione, la creazione, l'adozione e le fasi operative dell'implementazione di una soluzione cloud. Non è possibile rendere conto in un documento di tutti i requisiti per tutte le aziende. Ogni sezione di questo articolo descrive quindi solo attività minime e potenziali. L'obiettivo di queste attività è quello di consentire la creazione di un [prodotto minimo funzionante per i criteri](../policy-compliance/index.md#minimum-viable-product-mvp-for-policy), stabilendo un framework per il miglioramento [incrementale dei criteri](../policy-compliance/index.md#incremental-policy-growth). Il team di governance del cloud deve stabilire in che misura investire in queste attività per migliorare la posizione dell'accelerazione della distribuzione.

> [!NOTE]
> La disciplina di accelerazione della distribuzione non sostituisce i team, i processi e le procedure IT esistenti che consentono alle organizzazioni di distribuire e configurare le risorse basate sul cloud in modo efficace. Lo scopo principale di questa disciplina è identificare i rischi potenziali per l'azienda e fornire indicazioni per l'attenuazione dei rischi al personale IT responsabile della gestione delle risorse nel cloud. Quando si sviluppano i criteri e i processi di governance, assicurarsi di coinvolgere nelle attività di pianificazione e revisione i team IT appropriati.

I principali destinatari di queste linee guida sono gli architetti dell'infrastruttura cloud delle organizzazioni e gli altri membri del team di governance del cloud. Le decisioni, i criteri e i processi che emergono da questa disciplina, tuttavia, devono coinvolgere anche i membri appropriati dei team delle attività aziendali e IT, soprattutto i responsabili della distribuzione e della configurazione dei carichi di lavoro basati sul cloud.

## <a name="policy-statements"></a>Policy statements

Una disciplina di accelerazione della distribuzione si basa principalmente sulle definizioni dei criteri in base ai quali prendere decisioni operative e sui requisiti dell'architettura risultanti. Per esempi di definizioni dei criteri, vedere l'articolo [Definizioni dei criteri per l'accelerazione della distribuzione](./policy-statements.md). Questi esempi possono essere usati come punto di partenza per definire i criteri di governance della propria organizzazione.

> [!CAUTION]
> I criteri di esempio sono stati sviluppati in base a esperienze comuni dei clienti. Per allineare questi criteri a specifiche esigenze di governance del cloud, eseguire i passaggi seguenti in modo da creare definizioni dei criteri in grado di soddisfare le esigenze specifiche della propria organizzazione.

## <a name="develop-governance-policy-statements"></a>Sviluppare dichiarazioni per i criteri di governance

I sei passaggi seguenti consentono di definire i criteri di governance per controllare la distribuzione e la configurazione delle risorse nell'ambiente cloud.

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
                        <h3>Modello di accelerazione della distribuzione</h3>
                        <p class="x-hidden-focus">Scaricare il modello per documentare una disciplina Accelerazione della distribuzione</p>
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
                        <p class="x-hidden-focus">Motivazioni e rischi comunemente associati alla disciplina Accelerazione della distribuzione.</p>
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
                        <p class="x-hidden-focus">Indicatori per capire se è il momento giusto per investire nella disciplina Accelerazione della distribuzione.</p>
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
                        <p class="x-hidden-focus">Processi consigliati per supportare la conformità ai criteri della disciplina Accelerazione della distribuzione.</p>
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
                        <p class="x-hidden-focus">Servizi di Azure che è possibile implementare per supportare la disciplina Accelerazione della distribuzione.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Passaggi successivi

Iniziare con la valutazione dei [rischi aziendali](./business-risks.md) in un ambiente specifico.

> [!div class="nextstepaction"]
> [Informazioni sui rischi aziendali](./business-risks.md)

<!-- markdownlint-enable MD033 -->
