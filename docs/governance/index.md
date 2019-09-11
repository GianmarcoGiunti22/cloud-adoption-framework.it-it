---
title: Governance in Microsoft Cloud Adoption Framework per Azure
description: Informazioni sulla governance in Microsoft Cloud Adoption Framework per Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: adaf4358cb3d3781b892c8a614ecaba6177c6d5a
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70817520"
---
# <a name="governance-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Governance in Microsoft Cloud Adoption Framework per Azure

Il cloud crea nuovi paradigmi per le tecnologie che supportano l'azienda. Questi nuovi paradigmi comportano inoltre l'adozione di un approccio diverso all'adozione, alla gestione e alla regolamentazione delle tecnologie. Quando interi data center possono essere virtualmente distrutti e ricreati con una sola riga di codice eseguita da un processo automatico, è necessario rivedere gli approcci tradizionali. Questo vale in particolare per la governance.

## <a name="get-started-with-cloud-governance"></a>Introduzione alla governance del cloud

La governance del cloud costituisce un processo iterativo. Per le organizzazioni in cui sono già implementati criteri per il controllo degli ambienti locali, è necessario che tali criteri vengano integrati con la governance del cloud. Il livello di integrazione dei criteri aziendali tra origini locali e cloud varia tuttavia in base alla maturità della governance del cloud e a un patrimonio digitale nel cloud. Con le risorse del cloud che cambiano nel corso del tempo, potrebbero cambiare anche i criteri e i processi di governance del cloud. Gli esercizi seguenti consentono di iniziare a porre le fondamenta per la governance.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./methodology.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Metodologia</h3>
Acquisire le nozioni di base della metodologia alla base della governance del cloud in Cloud Adoption Framework per iniziare a delineare le varie fasi fino alla soluzione dello stato finale.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./benchmark.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Benchmark</h3>
Valutare lo stato corrente e quello futuro per definire gli obiettivi per l'applicazione del framework.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./getting-started.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Base iniziale per la governance</h3>
Iniziare il percorso della governance con un set ridotto e facilmente implementabile di strumenti di governance. Queste fondamenta sono note come prodotto minimo funzionante (MVP, Minimum Viable Product).
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./best-practices.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Migliorare la base iniziale per la governance</h3>
Nell'intera implementazione del piano di adozione del cloud, aggiungere in modo iterativo controlli di governance per gestire rischi tangibili mentre si procede verso lo stato finale.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="objective-of-this-content"></a>Obiettivo di questo contenuto

Le linee guida in questa sezione di Cloud Adoption Framework vengono usate per due scopi:

- Fornire esempi di guide di governance di utilità pratica che rappresentano alcune delle esperienze comuni dei clienti. Ogni esempio include un'analisi dei rischi aziendali, criteri aziendali per la mitigazione dei rischi e linee guida di progettazione per implementare soluzioni tecniche. Le linee guida di progettazione sono ovviamente specifiche per Azure. Tutto il contenuto rimanente di queste guide può essere applicato nell'ambito di un approccio indipendente dal cloud o multi-cloud.
- Aiutare a creare soluzioni di governance personalizzate per soddisfare numerose esigenze aziendali, tra cui la governance di più cloud pubblici, tramite linee guida dettagliate sullo sviluppo di criteri, processi e strumenti aziendali.

Questo contenuto è destinato al team di governance del cloud, ma è utile anche per i cloud architect che devono sviluppare una base solida di governance del cloud.

## <a name="intended-audience"></a>Destinatari

Il contenuto di Cloud Adoption Framework interessa i reparti aziendali impegnati nelle attività di carattere commerciale, tecnologico e culturale. Questa sezione di Cloud Adoption Framework interagisce in maniera significativa con i settori di sicurezza IT, governance IT, amministrazione, rete, gestione delle identità, con i responsabili line-of-business e con i team di adozione del cloud. Le varie dipendenze tra queste figure professionali richiedono un approccio collaborativo da parte dei cloud architect nell'uso di queste linee guida. La collaborazione con questi team può essere un'attività una tantum, ma in alcuni casi le interazioni con queste altre figure professionali saranno ricorrenti.

Il cloud architect assume il ruolo di leader e mediatore per semplificare l'interazione tra le varie persone coinvolte. I contenuti di questa raccolta di guide sono stati progettati per consentire ai cloud architect di comunicare informazioni corrette alle persone appropriate e giungere così alle decisioni opportune. La trasformazione aziendale introdotta dal cloud dipende dalla capacità del cloud architect di aiutare il personale tecnico e commerciale a prendere decisioni appropriate.

**Specializzazione del cloud architect in questa sezione:** Ogni sezione di Cloud Adoption Framework rappresenta una diversa variante o specializzazione del ruolo di cloud architect. Questa sezione di Cloud Adoption Framework è rivolta ai Cloud Architect che vogliono mitigare o ridurre i rischi tecnici. Alcuni provider di servizi cloud si riferiscono a questi esperti con l'appellativo di *cloud custodian*. In questa guida, si preferisce chiamarli *cloud guardian* o, collettivamente, *team di governance del cloud*. In ogni guida di governance per i clienti gli articoli illustrano in che modo la composizione e il ruolo del team di governance del cloud può cambiare nel tempo.

## <a name="use-this-guide"></a>Uso di questa guida

Per chi vuole seguire questa guida dall'inizio alla fine, il contenuto presentato consente di sviluppare una solida strategia di governance del cloud in parallelo all'implementazione del cloud. Le linee guida accompagneranno il lettore alla scoperta della teoria e dell'implementazione di tale strategia.

Per un corso accelerato sulla teoria e sull'accesso rapido all'implementazione di Azure, iniziare con la [panoramica delle guide di governance](./journeys/index.md). Seguendo queste linee guida, è possibile iniziare in piccolo e migliorare iterativamente le esigenze di governance in parallelo con le iniziative di adozione del cloud.

## <a name="next-steps"></a>Passaggi successivi

Acquisire le nozioni di base della metodologia alla base della governance del cloud in Cloud Adoption Framework.

> [!div class="nextstepaction"]
> [Comprendere la metodologia](./methodology.md)
