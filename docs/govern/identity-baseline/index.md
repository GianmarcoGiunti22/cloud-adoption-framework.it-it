---
title: Panoramica sulla disciplina Baseline di identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione su Baseline di identità in relazione alla governance del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: c134cd2a3cf17cd4e650f637fec2c417f3c29ff1
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566202"
---
# <a name="identity-baseline-discipline-overview"></a>Panoramica sulla disciplina Baseline di identità

La Baseline di identità è una delle [cinque discipline della governance del cloud](../governance-disciplines.md) nell'ambito del [modello di governance Cloud Adoption Framework](../index.md). L'identità è considerata sempre più il principale perimetro di sicurezza nel cloud: uno spostamento dal tradizionale focus sulla sicurezza della rete. I servizi di gestione delle identità forniscono i meccanismi fondamentali che supportano il controllo degli accessi e l'organizzazione all'interno degli ambienti IT; la disciplina Baseline di identità completa la [disciplina Baseline di sicurezza](../security-baseline/index.md) attraverso l'applicazione coerente dei requisiti di autenticazione e autorizzazione in tutte le azione di adozione del cloud.

> [!NOTE]
> La governance della Baseline di identità non sostituisce i team, i processi e le procedure IT esistenti che consentono all'organizzazione di gestire e proteggere i servizi di gestione delle identità. Lo scopo principale di questa disciplina è quello di identificare potenziali rischi aziendali correlati alle identità e fornire una guida per la riduzione dei rischi al personale IT responsabile dell'implementazione, della manutenzione e della gestione dell'infrastruttura di gestione dell'identità. Quando si sviluppano i criteri e i processi di governance, assicurarsi di coinvolgere nelle attività di pianificazione e revisione i team IT appropriati.

Questa sezione di Cloud Adoption Framework delinea l'approccio allo sviluppo della disciplina Baseline di identità come parte della strategia di governance del cloud. I principali destinatari di queste linee guida sono gli architetti dell'infrastruttura cloud delle organizzazioni e gli altri membri del team di governance del cloud. Tuttavia, le decisioni, i criteri e processi che emergono da questa disciplina dovrebbero coinvolgere anche i membri pertinenti dei team IT, responsabili dell'implementazione e della gestione delle soluzioni di gestione dell'identità dell'organizzazione.

Se l'organizzazione non dispone di competenze interne in materia di Baseline di identità e sicurezza, prendere in considerazione il ricorso a consulenti esterni come parte di questa disciplina. Valutare anche la possibilità di coinvolgere [Microsoft Consulting Services](https://www.microsoft.com/enterprise/services), il servizio di adozione cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) o altri partner esterni esperti di adozione del cloud per discutere i problemi relativi a questa disciplina.

## <a name="policy-statements"></a>Policy statements

Le informative sui criteri di utilità pratica e i requisiti dell'architettura risultanti sono il principale fondamento di una disciplina Baseline di identità. Per esempi di informative sui criteri, consultare l'articolo [Identity Baseline Policy Statements (Esempi di informative sui criteri di Baseline di identità)](./policy-statements.md). Questi esempi possono essere usati come punto di partenza per definire i criteri di governance della propria organizzazione.

> [!CAUTION]
> I criteri di esempio sono stati sviluppati in base a esperienze comuni dei clienti. Per allineare questi criteri a specifiche esigenze di governance del cloud, eseguire i passaggi seguenti in modo da creare definizioni dei criteri in grado di soddisfare le esigenze specifiche della propria organizzazione.

## <a name="develop-governance-policy-statements"></a>Sviluppare dichiarazioni per i criteri di governance

Le sei fasi seguenti offrono esempi e potenziali opzioni da considerare nello sviluppo della governance di Baseline di identità. Usare ogni passaggio come punto di partenza per le discussioni all'interno del team di governance del cloud e con i team aziendali e IT interessati in tutta l'organizzazione per stabilire i criteri e i processi necessari per gestire i rischi correlati all'identità.

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
                        <h3>Modello Baseline di identità</h3>
                        <p class="x-hidden-focus">Scaricare il modello per documentare una disciplina Baseline di identità</p>
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
                        <p class="x-hidden-focus">Motivazioni e rischi comunemente associati alla disciplina Baseline di identità.</p>
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
                        <p class="x-hidden-focus">Indicatori per capire se è il momento giusto per investire nella disciplina Baseline di identità.</p>
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
                        <p class="x-hidden-focus">Processi consigliati per supportare la conformità ai criteri della disciplina Baseline di identità.</p>
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
                        <p class="x-hidden-focus">Servizi di Azure che è possibile implementare per supportare la disciplina Baseline di identità.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Passaggi successivi

Iniziare con la valutazione dei [rischi aziendali](./business-risks.md) in un ambiente specifico.

> [!div class="nextstepaction"]
> [Informazioni sui rischi aziendali](./business-risks.md)
