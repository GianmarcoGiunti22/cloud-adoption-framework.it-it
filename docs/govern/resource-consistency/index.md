---
title: Panoramica della disciplina Coerenza delle risorse
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Panoramica della disciplina Coerenza delle risorse
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d4fc79c7829a0cc9058b07dd386e626a19cabb1b
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565985"
---
# <a name="resource-consistency-discipline-overview"></a>Panoramica della disciplina Coerenza delle risorse

La Coerenza delle risorse è una delle [cinque discipline della governance del cloud](../governance-disciplines.md) nell'ambito del [modello di governance Cloud Adoption Framework](../index.md). Questa disciplina riguarda le modalità di definizione dei criteri di gestione operativa di ambienti, applicazioni o carichi di lavoro. I team responsabili delle operazioni IT spesso si occupano del monitoraggio di applicazioni, carichi di lavoro e prestazioni degli asset. In genere, eseguono anche le attività necessarie per soddisfare le esigenze di scalabilità e correggere e prevenire dinamicamente le violazioni dei contratti di servizio tramite una procedura di correzione automatizzata. Nell'ambito delle cinque discipline della governance del cloud, la coerenza delle risorse consente una configurazione coerente delle risorse, in modo che possano essere individuabili dalle operazioni IT, incluse nelle soluzioni di ripristino e caricate in processi operativi ripetibili.

> [!NOTE]
> La governance per la coerenza delle risorse non sostituisce i team, i processi e le procedure IT esistenti che consentono alle organizzazioni di gestire le risorse basate sul cloud in modo efficace. Lo scopo principale di questa disciplina è identificare i rischi potenziali per l'azienda e fornire linee guida per l'attenuazione dei rischi al personale IT responsabile della gestione delle risorse nel cloud. Quando si sviluppano i criteri e i processi di governance, assicurarsi di coinvolgere nelle attività di pianificazione e revisione i team IT appropriati.

Questa sezione di Cloud Adoption Framework illustra come sviluppare una disciplina Coerenza delle risorse nell'ambito della strategia di governance del cloud. I principali destinatari di queste linee guida sono gli architetti dell'infrastruttura cloud delle organizzazioni e gli altri membri del team di governance del cloud. Tuttavia, le decisioni, i criteri e i processi che emergono da questa disciplina dovrebbero coinvolgere anche i membri pertinenti dei team IT, responsabili dell'implementazione e della gestione delle soluzioni di coerenza delle risorse dell'organizzazione.

Se l'organizzazione non dispone di competenze interne sulle strategie relative alla coerenza delle risorse, considerare l'opportunità di avvalersi di consulenti esterni come parte di questa disciplina. Prendere in considerazione anche la possibilità di coinvolgere [Microsoft Consulting Services](https://www.microsoft.com/enterprise/services), il servizio di adozione del cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) o altri esperti esterni di adozione del cloud per discutere sulle modalità ottimali per organizzare, tenere traccia e ottimizzare gli asset basati sul cloud.

## <a name="policy-statements"></a>Policy statements

Una disciplina Coerenza delle risorse si basa principalmente sulle definizioni dei criteri in base ai quali prendere decisioni operative e sui requisiti dell'architettura risultanti. Per esempi di definizioni dei criteri, vedere l'articolo [Definizioni dei criteri di esempio per la coerenza delle risorse](./policy-statements.md). Questi esempi possono essere usati come punto di partenza per definire i criteri di governance della propria organizzazione.

> [!CAUTION]
> I criteri di esempio sono stati sviluppati in base a esperienze comuni dei clienti. Per allineare questi criteri a specifiche esigenze di governance del cloud, eseguire i passaggi seguenti in modo da creare definizioni dei criteri in grado di soddisfare le esigenze specifiche della propria organizzazione.

## <a name="develop-governance-policy-statements"></a>Sviluppare dichiarazioni per i criteri di governance

I sei passaggi seguenti offrono esempi e potenziali opzioni da considerare nello sviluppo della governance per la coerenza delle risorse. Usare ogni passaggio come punto di partenza per le discussioni all'interno del team di governance del cloud e con i team responsabili delle attività aziendali e IT interessati in tutta l'organizzazione per stabilire i criteri e i processi necessari per gestire i rischi correlati alla coerenza delle risorse.

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
                        <h3>Modello di coerenza delle risorse</h3>
                        <p class="x-hidden-focus">Scaricare il modello per documentare una disciplina Coerenza delle risorse</p>
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
                        <p class="x-hidden-focus">Motivazioni e rischi comunemente associati alla disciplina Coerenza delle risorse.</p>
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
                        <p class="x-hidden-focus">Indicatori per capire se è il momento giusto per investire nella disciplina Coerenza delle risorse.</p>
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
                        <p class="x-hidden-focus">Processi consigliati per supportare la conformità ai criteri della disciplina Coerenza delle risorse.</p>
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
                        <p class="x-hidden-focus">Servizi di Azure che è possibile implementare per supportare la disciplina Coerenza delle risorse.</p>
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
