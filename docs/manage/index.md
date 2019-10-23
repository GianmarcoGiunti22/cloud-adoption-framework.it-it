---
title: Gestione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Gestione del cloud in Cloud Adoption Framework
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: operate
layout: LandingPage
ms.openlocfilehash: 2ae964d2b145a9d241cc647b939771f219b0379e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547286"
---
# <a name="cloud-management-in-the-cloud-adoption-framework"></a>Gestione del cloud in Cloud Adoption Framework

Per definire una [strategia per il cloud](../strategy/index.md) è necessario un solido ciclo di pianificazione, preparazione e adozione. Ma i risultati aziendali tangibili si ottengono con l'operatività continua degli asset digitali. Senza un piano che preveda l'operatività affidabile e ben gestita delle soluzioni cloud, quelle iniziative genereranno poco valore. Gli esercizi seguenti aiutano a sviluppare l'approccio aziendale e tecnico per una gestione del cloud che garantisca operatività continua.

## <a name="getting-started"></a>Introduzione

Per prepararsi per questa fase del ciclo di vita di adozione del cloud, il framework suggerisce gli esercizi seguenti:

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-management-guide/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Stabilire una baseline di gestione</h3>
Definire le classificazioni di criticità, gli strumenti di gestione del cloud e i processi necessari per la gestione delle operazioni con il minimo impegno.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./considerations/business-alignment.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Definire gli impegni aziendali</h3>
Documentare i carichi di lavoro supportati per stabilire gli impegni operativi con l'azienda e concordare gli investimenti in gestione del cloud per ogni carico di lavoro.
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
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Espandere la baseline di gestione</h3>
In base agli impegni aziendali e alle decisioni operative, adottare le procedure consigliate incluse per implementare i necessari strumenti di gestione del cloud.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./design-principles.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Operazioni avanzate e principi di progettazione</h3>
Le piattaforme o i carichi di lavoro che richiedono un livello più elevato di impegno aziendale possono imporre una revisione più approfondita dell'architettura per soddisfare i requisiti di resilienza e affidabilità.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="scalable-cloud-management-methodology"></a>Metodologia scalabile di gestione del cloud

I passaggi descritti sopra definiscono approcci fattibili per attuare la metodologia di gestione di Cloud Adoption Framework.

![Metodologia per la gestione in Cloud Adoption Framework](../_images/manage/caf-manage.png)

## <a name="creating-a-balanced-cloud-portfolio"></a>Creazione di un portfolio cloud bilanciato

Come descritto nell'articolo sull'[allineamento aziendale](./considerations/business-alignment.md), non tutti i carichi di lavoro sono cruciali. Ogni portfolio include vari gradi di esigenze di gestione operativa. L'allineamento aziendale aiuta a capire l'impatto sul business e a negoziare i costi di gestione con l'organizzazione per garantire la disponibilità dei processi e degli strumenti più appropriati per la gestione operativa.

## <a name="objective-of-this-content"></a>Obiettivo di questo contenuto

Le linee guida in questa sezione di Cloud Adoption Framework vengono usate per due scopi:

- Fornire esempi di approcci fattibili alla gestione delle operazioni che rappresentino comuni esperienze spesso riscontrate dai clienti.
- Aiutare a creare soluzioni di gestione personalizzate basate sugli impegni aziendali.

Questo contenuto è destinato al team di operazioni del cloud, ma è utile anche per i cloud architect che devono sviluppare una base solida di operazioni e principi di progettazione del cloud.

## <a name="intended-audience"></a>Destinatari

Il contenuto di Cloud Adoption Framework interessa i reparti aziendali impegnati nelle attività di carattere commerciale, tecnologico e culturale. Questa sezione di Cloud Adoption Framework interagisce in maniera significativa con i settori di operazioni IT, governance IT, amministrazione, rete, gestione delle identità, con i responsabili line-of-business e con i team di adozione del cloud. Le varie dipendenze tra queste figure professionali richiedono un approccio collaborativo da parte dei cloud architect nell'uso di queste linee guida. La collaborazione con questi team può essere un'attività una tantum.

Il cloud architect assume il ruolo di leader e mediatore per semplificare l'interazione tra le varie persone coinvolte. I contenuti di questa raccolta di guide sono stati progettati per consentire ai cloud architect di comunicare informazioni corrette alle persone appropriate e giungere così alle decisioni opportune. La trasformazione aziendale introdotta dal cloud dipende dalla capacità del cloud architect di aiutare il personale tecnico e commerciale a prendere decisioni appropriate.

**Specializzazione del cloud architect in questa sezione:** Ogni sezione di Cloud Adoption Framework rappresenta una diversa variante o specializzazione del ruolo di cloud architect. Questa sezione di Cloud Adoption Framework è rivolta ai cloud architect interessati alle operazioni e alla gestione delle soluzioni da distribuire. All'interno del framework questi specialisti vengono spesso indicati come *team di operazioni cloud* che si occupano di *operazioni cloud*.

## <a name="use-this-guide"></a>Uso di questa guida

Per chi vuole seguire questa guida dall'inizio alla fine, il contenuto presentato consente di sviluppare una solida strategia di operazioni cloud. Le linee guida accompagneranno il lettore alla scoperta della teoria e dell'implementazione di tale strategia.

<!-- For a crash course on the theory and quick access to Azure implementation, get started with the [governance guides overview](./guide/index.md). Using this guidance, you can start small and iteratively improve your governance needs in parallel with cloud adoption efforts. -->

## <a name="next-steps"></a>Passaggi successivi

Applicare la metodologia per [definire chiari impegni aziendali](./considerations/business-alignment.md).

> [!div class="nextstepaction"]
> [Stabilire chiari impegni aziendali](./considerations/business-alignment.md)
