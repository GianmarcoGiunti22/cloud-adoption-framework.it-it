---
title: Creare un modello finanziario per la trasformazione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Come creare un modello finanziario per la trasformazione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 60d49cbb970b5fd20512e342961284115dbef984
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825107"
---
# <a name="create-a-financial-model-for-cloud-transformation"></a>Creare un modello finanziario per la trasformazione del cloud

Creare un modello finanziario che rappresenti accuratamente l'intero valore aziendale di una trasformazione del cloud può essere complicato. I modelli finanziari e le motivazioni aziendali tendono a variare per le diverse organizzazioni. In questo articolo vengono stabilite alcune formule e vengono evidenziati alcuni aspetti che in genere si verificano quando gli strateghi creano modelli finanziari.

## <a name="return-on-investment"></a>Ritorno sugli investimenti

Return on Investment (ROI) è spesso un criterio importante per il gruppo C-Suite o la bacheca. Il ROI consente di confrontare diversi modi di investire risorse di capitale limitate. La formula per il ROI è piuttosto semplice. I dettagli necessari per creare ogni input per la formula potrebbero non essere semplici. In pratica, il ritorno sugli investimenti è la quantità di ritorno prodotta in seguito a un investimento iniziale. Viene in genere rappresentato come percentuale:

![ROI Equals (guadagno da investimento meno costo di investimento) diviso per costo di investimento](../_images/formula-roi.png)

Nelle sezioni successive verranno illustrati i dati necessari per calcolare l'investimento iniziale e il guadagno da investimenti (guadagni).

## <a name="calculating-initial-investment"></a>Calcolo dell'investimento iniziale

Gli investimenti iniziali sono le spese di capitale e i costi operativi necessari per completare una trasformazione. La classificazione dei costi può variare a seconda delle preferenze del direttore delle finanze e dei modelli di contabilità. Questa categoria include tuttavia elementi come servizi professionali da trasformare, licenze software usate solo durante la trasformazione, il costo dei servizi cloud durante la trasformazione e potenzialmente il costo dei dipendenti stipendiati durante la trasformazione .

Aggiungere questi costi per creare una stima dell'investimento iniziale.

## <a name="calculating-the-gain-from-investment"></a>Calcolo del guadagno dell'investimento

Il calcolo del guadagno dall'investimento spesso richiede una seconda formula specifica per i risultati aziendali e le modifiche tecniche associate. Il calcolo dei guadagni è più difficile del calcolo delle riduzioni dei costi.

Per calcolare i guadagni, sono necessarie due variabili:

![Guadagno da investimenti equivalenti Delta di ricavi e Delta di costo](../_images/formula-gain-from-investment.png)

Queste variabili sono descritte nelle sezioni seguenti.

## <a name="revenue-deltas"></a>Delta dei ricavi

I delta dei ricavi dovrebbero prevedere la collaborazione con gli stakeholder aziendali. Una volta che le parti interessate dell'azienda accettano un effetto sui ricavi, possono essere usate per migliorare la posizione di guadagno.

## <a name="cost-deltas"></a>Delta dei costi

I Delta di costo rappresentano la quantità di aumento o diminuzione che verrà causata dalla trasformazione. Le variabili indipendenti possono influenzare i delta dei costi. Gli utili si basano prevalentemente su costi fissi come la riduzione delle spese in conto capitale, i costi evitati, la riduzione dei costi operativi e la riduzione degli ammortamenti. Le sezioni seguenti descrivono alcuni Delta di costo da considerare.

### <a name="depreciation-reduction-or-acceleration"></a>Riduzione o accelerazione dell'ammortamento

Per indicazioni sugli ammortamenti, contattare il direttore delle finanze o il team finanziario. Le informazioni seguenti sono destinate a fungere da riferimento generale sull'argomento relativo all'ammortamento.

Quando si investe capitale nell'acquisizione di un asset, tale investimento può essere usato a scopi finanziari o fiscali per generare vantaggi continui per tutta la vita utile prevista dell'asset. Alcune aziende vedono gli ammortamenti come un vantaggio fiscale positivo. Gli altri lo vedono come una spesa continuativa, simile ad altre spese ricorrenti attribuite al budget IT annuale.

Rivolgersi all'ufficio finanziario per verificare se l'eliminazione dell'ammortamento è possibile e se è un contributo positivo ai delta dei costi.

### <a name="physical-asset-recovery"></a>Recupero di asset fisico

In alcuni casi, gli asset dismessi possono essere venduti come fonte di ricavi. Questi ricavi sono spesso legati alla riduzione dei costi per semplicità. Ma si tratta effettivamente di un aumento dei ricavi e può essere tassato come tali. Rivolgersi all'ufficio finanziario per valutare l'attuabilità di questa alternativa e come contabilizzare i ricavi risultanti.

### <a name="operational-cost-reductions"></a>Riduzione dei costi operativi

Le spese ricorrenti necessarie per il funzionamento di un'azienda sono spesso denominate spese operative. Si tratta di una categoria ampia. Nella maggior parte dei modelli di contabilità sono inclusi:

- Gestione licenze software.
- Spese di hosting.
- Bollette elettriche.
- Affitti immobiliari.
- Spese di raffreddamento.
- Il personale temporaneo è necessario per le operazioni.
- Noleggi di apparecchiature.
- Parti di sostituzione.
- Contratti di manutenzione.
- Ripristinare i servizi.
- Servizi di continuità aziendale e ripristino di emergenza (BCDR).
- Altre spese che non richiedono l'approvazione delle spese di capitale.

Questa categoria fornisce uno dei Delta di guadagno più elevati. Quando si sta prendendo in considerazione una migrazione cloud, il tempo investito per rendere esauriente questo elenco viene raramente sprecato. Rivolgersi alle domande del team CIO e Finance per assicurarsi che tutti i costi operativi siano considerati.

### <a name="cost-avoidance"></a>Costi evitati

Quando è previsto un dispendio operativo, ma non ancora in un budget approvato, potrebbe non rientrare in una categoria di riduzione dei costi. Se, ad esempio, le licenze VMware e Microsoft devono essere rinegoziate e pagate il prossimo anno, non sono ancora costi completi. Le riduzioni dei costi previsti vengono considerate come costi operativi per i calcoli di costo Delta. In modo informale, tuttavia, devono essere detti "riduzione dei costi" fino al completamento dell'approvazione della negoziazione e del budget.

### <a name="soft-cost-reductions"></a>Riduzioni dei costi flessibili

In alcune aziende, i costi flessibili come le riduzioni nella complessità operativa o nelle riduzioni del personale a tempo pieno per la gestione di un Data Center possono anche essere inclusi nei delta di costo. Tuttavia, l'inclusione di costi flessibili potrebbe non essere un'idea corretta. Quando si includono riduzioni dei costi flessibili, si inserisce un presupposto non documentato che la riduzione creerà un risparmio di costi tangibile. I progetti tecnologici comportano raramente un recupero di costi effettivi.

### <a name="headcount-reductions"></a>Riduzione di organico

Il risparmio di tempo per il personale è spesso incluso nella riduzione dei costi flessibili. Quando il risparmio di tempo viene mappato alla riduzione effettiva dello stipendio o del personale IT, questi possono essere calcolati separatamente come riduzioni degli effettivi.

Ciò premesso, le competenze necessarie in locale vengono in genere mappate a un set di competenze simile (o di livello superiore) necessario nel cloud. Quindi, le persone non sono in genere disposte dopo una migrazione cloud.

Si verifica un'eccezione quando la capacità operativa viene fornita da terze parti o da un provider di servizi gestiti (MSP). Se i sistemi IT sono gestiti da terze parti, i costi operativi potrebbero essere sostituiti da una soluzione nativa del cloud o da un MSP nativo del cloud. È probabile che un MSP nativo del cloud funzioni in modo più efficiente e potenzialmente a un costo inferiore. In tal caso, le riduzioni dei costi operativi appartengono ai calcoli a costi fissi.

### <a name="capital-expense-reductions-or-avoidance"></a>Riduzione o costi evitati di spesa in conto capitale

Le spese di capitale sono leggermente diverse dalle spese operative. In genere, questa categoria è determinata dai cicli di aggiornamento o dall'espansione dei data center. Un esempio di espansione del Data Center è un nuovo cluster ad alte prestazioni che ospita una soluzione Big Data o data warehouse. Questa spesa rientrerebbe in genere in una categoria di spese di capitale. I cicli di aggiornamento di base sono più comuni. Alcune società hanno cicli di aggiornamento hardware rigidi, ovvero gli asset vengono ritirati e sostituiti in un ciclo regolare (in genere ogni tre, cinque o otto anni). Questi cicli spesso coincidono con i cicli di lease degli asset o con la durata prevista delle apparecchiature. Quando si verifica un ciclo di aggiornamento, viene disegnata una spesa di capitale per l'acquisizione di nuove apparecchiature.

Se un ciclo di aggiornamento viene approvato e viene definito un budget, la trasformazione cloud potrebbe contribuire a eliminare il costo. Se un ciclo di aggiornamento è pianificato ma non ancora approvato, la trasformazione cloud potrebbe evitare una spesa in conto capitale. Entrambe le riduzioni verranno aggiunte al delta dei costi.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sui modelli di [Contabilità cloud](./cloud-accounting.md) .

> [!div class="nextstepaction"]
> [Contabilità cloud](./cloud-accounting.md)
