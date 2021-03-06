---
title: Panoramica sulla disciplina Baseline di sicurezza
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Panoramica sulla disciplina Baseline di sicurezza
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: a0b0ed642e11fc3ffc81db7fd1095853a5458b1d
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565934"
---
# <a name="security-baseline-discipline-overview"></a>Panoramica sulla disciplina Baseline di sicurezza

La Baseline di sicurezza è una delle [cinque discipline della governance del cloud](../governance-disciplines.md) nell'ambito del [modello di governance Cloud Adoption Framework](../index.md). La sicurezza è un componente di qualsiasi distribuzione IT e il cloud solleva preoccupazioni specifiche relative alla sicurezza. Molte aziende sono soggette a requisiti normativi in base ai quali la protezione dei dati sensibili è una delle principali priorità organizzative nell'ambito di una trasformazione cloud. L'identificazione delle potenziali minacce alla sicurezza dell'ambiente cloud e la definizione di processi e procedure per affrontare queste minacce dovrebbero essere prioritarie per qualsiasi team responsabile della sicurezza IT o della sicurezza informatica. La disciplina Baseline di sicurezza garantisce che i requisiti tecnici e i vincoli di sicurezza vengano applicati in modo coerente agli ambienti cloud, man mano che tali requisiti evolvono.

> [!NOTE]
> La governance della baseline di sicurezza non sostituisce i team, i processi e le procedure IT esistenti che l'organizzazione usa per proteggere le risorse distribuite nel cloud. Lo scopo principale di questa disciplina è identificare i rischi per l'azienda correlati alla sicurezza e fornire indicazioni per l'attenuazione dei rischi al personale IT responsabile dell'infrastruttura di sicurezza. Quando si sviluppano i criteri e i processi di governance, assicurarsi di coinvolgere nelle attività di pianificazione e revisione i team IT appropriati.

Questo articolo illustra l'approccio da adottare per sviluppare una disciplina Baseline di sicurezza come parte della strategia di governance del cloud. I principali destinatari di queste linee guida sono gli architetti dell'infrastruttura cloud delle organizzazioni e gli altri membri del team di governance del cloud. Le decisioni, i criteri e i processi che emergono da questa disciplina, tuttavia, devono coinvolgere anche i membri appropriati dei team della sicurezza e IT, soprattutto i responsabili tecnici dell'implementazione dei servizi di gestione delle identità, di crittografia e di rete.

Prendere le decisioni appropriate in materia di sicurezza è fondamentale per il successo delle distribuzioni cloud e, più in generale, dell'azienda. Se l'organizzazione non ha competenze interne in materia di sicurezza informatica, prendere in considerazione il ricorso a consulenti per la sicurezza esterni come componente di questa disciplina. Prendere in considerazione anche la possibilità di coinvolgere [Microsoft Consulting Services](https://www.microsoft.com/enterprise/services), il servizio di adozione cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) o altri esperti esterni di adozione cloud per discutere i problemi relativi a questa disciplina.

## <a name="policy-statements"></a>Policy statements

Una disciplina Baseline di sicurezza si basa principalmente sulle definizioni dei criteri in base ai quali prendere decisioni operative e sui requisiti dell'architettura risultanti. Per esempi di definizioni dei criteri, vedere l'articolo [Definizioni dei criteri di esempio per la baseline di sicurezza](./policy-statements.md). Questi esempi possono essere usati come punto di partenza per definire i criteri di governance della propria organizzazione.

> [!CAUTION]
> I criteri di esempio sono stati sviluppati in base a esperienze comuni dei clienti. Per allineare questi criteri a specifiche esigenze di governance del cloud, eseguire i passaggi seguenti in modo da creare definizioni dei criteri in grado di soddisfare le esigenze specifiche della propria organizzazione.

## <a name="develop-governance-policy-statements"></a>Sviluppare dichiarazioni per i criteri di governance

I sei passaggi seguenti offrono esempi e potenziali opzioni da considerare nello sviluppo della governance per la baseline di sicurezza. Usare ogni passaggio come punto di partenza per le discussioni all'interno del team di governance del cloud e con i team responsabili delle attività aziendali, dell'IT e della sicurezza interessati in tutta l'organizzazione per stabilire i criteri e i processi necessari per gestire i rischi correlati alla sicurezza.

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
                        <h3>Modello di baseline di sicurezza</h3>
                        <p class="x-hidden-focus">Scaricare il modello per documentare una disciplina Baseline di sicurezza</p>
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
                        <p class="x-hidden-focus">Motivazioni e rischi comunemente associati alla disciplina Baseline di sicurezza.</p>
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
                        <p class="x-hidden-focus">Indicatori per capire se è il momento giusto per investire nella disciplina Baseline di sicurezza.</p>
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
                        <p class="x-hidden-focus">Processi consigliati per supportare la conformità ai criteri nella disciplina Baseline di sicurezza.</p>
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
                        <p class="x-hidden-focus">Servizi di Azure che è possibile implementare per supportare la disciplina Baseline di sicurezza.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Passaggi successivi

Iniziare con la valutazione dei rischi aziendali in un determinato ambiente.

> [!div class="nextstepaction"]
> [Informazioni sui rischi aziendali](./business-risks.md)
