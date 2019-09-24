---
title: Le cinque discipline della governance del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle cinque discipline della governance del cloud nel Framework di adozione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: f072870caf18eb460ccc3a34e02d7d1f44872406
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223153"
---
# <a name="the-five-disciplines-of-cloud-governance"></a>Le cinque discipline della governance del cloud

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsI">
    <li style="display: flex; flex-direction: column;">
        <div class="cardSize">
            <div class="cardPadding" style="padding-bottom:10px;">
                <div class="card" style="padding-bottom:10px;">
                    <div class="cardText" style="padding-left:0px;">
Qualsiasi modifica apportata a processi di business o piattaforme tecnologiche introduce dei rischi. I team di governance del cloud, i cui membri sono a volte noti come depositari del cloud, sono interessati a mitigare questi rischi e a garantire un'interruzione minima delle attività di adozione o innovazione.<br/><br/>Il modello di governance del Framework di adozione del cloud Guida queste decisioni (indipendentemente dalla piattaforma cloud scelta) concentrandosi sullo <a href="./corporate-policy.md">sviluppo dei criteri aziendali</a> e sulle <a href="#disciplines-of-cloud-governance">cinque discipline della governance del cloud</a>. Le <a href="./guides/index.md">Guide alla progettazione operativa</a> illustrano questo modello usando i servizi di Azure. Informazioni sulle discipline del modello di governance del Framework di adozione del cloud di seguito.
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="../_images/operational-transformation-govern-highres.png" style="display: flex; flex-direction: column; flex: 1 0 auto;">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardText" style="padding-left:0px;">
    <img src="../_images/operational-transformation-govern-highres.png" alt="Diagram of the Cloud Adoption Framework governance model: Corporate policy and governance disciplines">
    <br>
    <i>Figura 1: diagramma dei criteri aziendali e cinque discipline della governance del cloud.</i>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="disciplines-of-cloud-governance"></a>Discipline della governance del cloud

Con qualsiasi piattaforma cloud sono disponibili discipline di governance comuni che consentono di informare i criteri e allineare toolchain. Queste discipline guidano le decisioni relative al livello di automazione e all'applicazione dei criteri aziendali in tutte le piattaforme cloud.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsA">
<li style="display: flex; flex-direction: column;">
    <a href="./cost-management/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/cost-management.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Gestione dei costi</h3>
                        <p>Il costo è una delle preoccupazioni principali per gli utenti del cloud. Sviluppare criteri per il controllo dei costi per tutte le piattaforme cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./security-baseline/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/security-baseline.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Baseline di sicurezza</h3>
                        <p>La sicurezza è un argomento complesso, univoco per ogni società. Una volta stabiliti i requisiti di sicurezza, i criteri di governance del cloud e l'imposizione applicano tali requisiti nelle configurazioni di rete, dati e asset.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./identity-baseline/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/identity-baseline.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Baseline di identità</h3>
                        <p>Le incoerenze nell'applicazione dei requisiti di identità possono aumentare il rischio di violazione. La disciplina di base di identità è incentrata sulla garanzia che l'identità venga applicata in modo coerente alle attività di adozione del cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./resource-consistency/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/resource-consistency.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Coerenza delle risorse</h3>
                        <p>Le operazioni cloud dipendono dalla configurazione della risorsa coerente. Grazie agli strumenti di governance, le risorse possono essere configurate in modo coerente per gestire i rischi correlati a onboarding, Drift, individuabilità e ripristino.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./deployment-acceleration/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/deployment-acceleration.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Accelerazione della distribuzione</h3>
                        <p>Centralizzazione, standardizzazione e coerenza negli approcci alla distribuzione e alla configurazione migliorare le procedure di governance. Quando vengono fornite tramite gli strumenti di governance basati sul cloud, creano un fattore cloud che consente di accelerare le attività di distribuzione.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->
