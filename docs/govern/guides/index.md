---
title: Guide di governance del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle guide di governance di utilità pratica fornite in Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: b5d5bca79d08a0084026c027a242086cefb0100f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025730"
---
# <a name="cloud-governance-guides"></a>Guide di governance del cloud

Le guide di governance di utilità pratica incluse in questa sezione illustrano l'approccio incrementale del modello di governance di Cloud Adoption Framework basato sulla [metodologia di governance](../methodology.md) descritta in precedenza. È possibile definire un approccio agile alla governance del cloud in grado di crescere per soddisfare le esigenze di qualsiasi scenario di governance.

## <a name="review-and-adopt-cloud-governance-best-practices"></a>Esaminare e adottare le procedure consigliate per la governance del cloud

Per iniziare un percorso di adozione del cloud, scegliere una delle guide di governance seguenti. Ogni guida illustra una serie di procedure consigliate, basate su un set di esperienze del cliente fittizie. I lettori che non hanno familiarità con l'approccio incrementale del modello di governance di Cloud Adoption Framework possono rivedere l'introduzione generale alla teoria della governance riportata di seguito prima di adottare una serie di procedure consigliate.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./standard/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida alla governance standard</h3>
                        <p>Una guida destinata alla maggior parte delle organizzazioni e basata sul modello a due sottoscrizioni consigliato, progettato per le distribuzioni in più aree, ma non per i cloud pubblici, sovrani e per enti pubblici.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./complex/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida alla governance per aziende complesse</h3>
                        <p>Una guida per aziende gestite da più business unit IT indipendenti o che si estendono su cloud pubblici, sovrani e per enti pubblici.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="an-incremental-approach-to-cloud-governance"></a>Approccio incrementale alla governance del cloud

## <a name="choosing-a-governance-guide"></a>Scelta di una guida alla governance

Le guide dimostrano come implementare un MVP per la governance. Da qui, ogni guida mostra come il team di governance del cloud può lavorare in anticipo rispetto ai team di adozione del cloud, come partner per accelerare le iniziative di adozione. Il modello di governance di Cloud Adoption Framework rappresenta una guida di riferimento per l'applicazione della governance, a partire dalle basi e attraverso evoluzioni e miglioramenti successivi.

Per iniziare un percorso di governance, scegliere una delle due opzioni seguenti. Le opzioni sono basate su esperienze dei clienti sintetizzate. I titoli sono basati sulla complessità dell'azienda per semplificare l'esplorazione. La decisione del lettore può essere tuttavia più complessa. Le tabelle seguenti illustrano le differenze tra le due opzioni.

> [!WARNING]
> Talvolta può essere necessario definire un punto di partenza più solido per il percorso di governance. In tal caso, prendere in considerazione l'approccio basato sul [data center virtuale di Azure](#azure-virtual-datacenter) descritto brevemente [di seguito](#azure-virtual-datacenter). Questo approccio è in genere consigliabile per le adozioni su larga scala, in particolare se la quantità di asset interessati è superiore a 10.000. Rappresenta anche la scelta standard per gli scenari di governance complessi, quando deve essere soddisfatto uno dei requisiti seguenti: conformità completa a soluzioni di terze parti, esperienza approfondita del settore o adeguamento a requisiti di conformità e criteri di governance IT consolidati.

> [!NOTE]
> È improbabile che una delle guide sia perfettamente indicata per una specifica situazione. Scegliere la guida maggiormente in linea e usarla come punto di partenza. Nell'intera guida vengono fornite informazioni aggiuntive che consentono di personalizzare le decisioni in base a specifici criteri.

### <a name="business-characteristics"></a>Caratteristiche dell'azienda

| Caratteristica | Organizzazione standard                                                                              | Azienda complessa                                                                                               |
|--------------------------------------------|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Geografia (paese o area geopolitica) | I clienti o il personale si trovano in gran parte in un'unica area geografica                                                      | I clienti o il personale si trovano in più aree geografiche o richiedono cloud sovrani.                                                             |
| Business unit interessate                    | Business unit che condividono un'infrastruttura IT comune                                                                                    | Più business unit che non condividono un'infrastruttura IT comune                                                                                        |
| Budget IT                                  | Singolo budget IT                                                                                        | Budget allocato tra più business unit e in diverse valute                                                                         |
| Investimenti IT                             | Gli investimenti come spese in conto capitale sono pianificati su base annua e riguardano in genere solo la manutenzione di base. | Gli investimenti come spese in conto capitale sono pianificati su base annua e spesso includono la manutenzione e un ciclo di aggiornamento di 3-5 anni. |

### <a name="current-state-before-adopting-cloud-governance"></a>Stato corrente prima di adottare la governance del cloud

| Stato | Azienda standard                                                                               | Azienda complessa                                                                                                          |
|---------------------------------------------|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| Data center o provider di hosting di terze parti | Meno di cinque data center                                                                                  | Più di cinque data center                                                                                                   |
| Rete                                  | Nessuna rete WAN o 1-2 provider WAN                                                                             | Rete complessa o WAN globale                                                                                             |
| Identità                                    | Foresta singola, dominio singolo. | Struttura complessa, più foreste, più domini.  |

### <a name="desired-future-state-after-incremental-improvement-of-cloud-governance"></a>Stato futuro desiderato dopo il miglioramento incrementale della governance del cloud

| Stato | Organizzazione standard                                                                        | Azienda complessa                                                                                        |
|----------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Gestione dei costi - Cloud accounting           | Modello di showback. La fatturazione è centralizzata tramite IT.                                                | Modello di chargeback. La fatturazione potrebbe essere distribuita tramite approvvigionamento IT.                                  |
| Baseline di sicurezza - Dati protetti           | Dati finanziari e proprietà intellettuale dell'azienda. Dati sui clienti limitati. Nessun requisito di conformità di terze parti.     | Più raccolte di dati finanziari e personali dei clienti. Potrebbe essere necessario tenere conto della conformità di terze parti. |

## <a name="azure-virtual-datacenter"></a>Data center virtuale di Azure

Il data center virtuale di Azure offre un approccio per ottenere il massimo dalle funzionalità della piattaforma cloud di Azure, rispettando al tempo stesso i requisiti di sicurezza e di governance dell'azienda.

Rispetto agli ambienti locali tradizionali, Azure consente ai team di sviluppo dei carichi di lavoro e ai relativi sponsor aziendali per sfruttare la maggiore flessibilità di distribuzione offerta dalle piattaforme cloud. Tuttavia, quando il processo di adozione del cloud si estende fino al punto da includere carichi di lavoro e dati mission-critical, questa flessibilità può entrare in conflitto con i requisiti di sicurezza aziendale e conformità ai criteri stabiliti dai team IT. Ciò è particolarmente vero per le grandi aziende che presentano requisiti normativi e di governance complessi.

L'approccio del data center virtuale di Azure è stato pensato per affrontare questi problemi prima di avviare il processo di adozione e offre modelli, architetture di riferimento, elementi di automazione di esempio e linee guida per aiutare a raggiungere un equilibrio tra i requisiti degli sviluppatori e quelli della governance IT durante il processo di adozione del cloud in azienda. L'idea centrale di questo approccio è rappresentata dal concetto stesso di data center virtuale, ovvero l'implementazione di limiti di isolamento per la propria infrastruttura cloud tramite l'applicazione di controlli di accesso e sicurezza, i criteri di rete e il monitoraggio della conformità.

Un data center virtuale può essere considerato come un cloud isolato all'interno della piattaforma Azure, in cui sono integrati i processi di gestione, i requisiti normativi e i processi di sicurezza imposti dai criteri di governance dell'azienda. Entro questi limiti virtuali, il data center virtuale di Azure offre modelli di esempio per la distribuzione dei carichi di lavoro, in modo da garantire conformità coerente, e fornisce indicazioni di base sull'implementazione della separazione dei ruoli e delle responsabilità di un'organizzazione nel cloud.

### <a name="azure-virtual-datacenter-assumptions"></a>Presupposti del data center virtuale di Azure

Anche se team più piccoli possono trarre vantaggio dai modelli e dalle raccomandazioni del data center virtuale di Azure, questo approccio è stato progettato per fornire linee guida ai gruppi IT delle grandi aziende, che gestiscono ambienti cloud di grandi dimensioni. Per le organizzazioni che soddisfano i criteri seguenti, è consigliabile prendere in considerazione le linee guida offerte dal data center virtuale di Azure durante la progettazione dell'infrastruttura cloud basata su Azure:

- L'azienda è tenuta a soddisfare requisiti di conformità alle normative in base ai quali è necessario disporre di funzionalità di monitoraggio e controllo centralizzate.
- È necessario mantenere criteri comuni, la conformità alla governance e il controllo IT centrale sui servizi essenziali.
- Il settore dipende da una piattaforma complessa che richiede controlli complessi e competenze di dominio approfondite per la regolamentazione. Questa situazione è più comune nelle grandi imprese in settori come finanza, petrolio e gas o produzione.
- I criteri di governance IT esistenti richiedono un adeguamento più rigoroso alle funzionalità esistenti, anche durante la fase di adozione iniziale.

Per altre informazioni, visitare la sezione relativa al [data center virtuale di Azure](../../reference/vdc.md) del sito di Cloud Adoption Framework.

## <a name="next-steps"></a>Passaggi successivi

Scegliere una di queste guide:

> [!div class="nextstepaction"]
> [Guida alla governance standard](./standard/index.md)
>
> [Guida alla governance per aziende complesse](./complex/index.md)
