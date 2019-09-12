---
title: Definire le strutture del team
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definire le strutture del team
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: d87109d36075fb3d196b7bc681073141b6c1f44a
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906193"
---
# <a name="establish-team-structures"></a>Definire le strutture del team

Ogni funzionalità cloud viene fornita da qualcuno durante ogni tentativo di adozione del cloud. Queste assegnazioni e strutture del team possono svilupparsi in modo organico oppure possono essere progettate intenzionalmente in modo da corrispondere a una struttura definita del team.

Con l'aumentare delle esigenze di adozione, la necessità di bilanciare e struttura. Questo articolo fornisce esempi di strutture del team comuni in varie fasi di maturità organizzativa. Il grafico e l'elenco seguenti illustrano le strutture in base a fasi di maturazione tipiche. Usare questi esempi per trovare la struttura organizzativa più adatta alle proprie esigenze operative.

![Ciclo della maturità organizzativa](../_images/ready/org-ready-maturity.png)

Le strutture organizzative tendono a passare attraverso il modello di maturità comune descritto di seguito:

1. [Solo team di adozione cloud](#cloud-adoption-team-only)
2. [Procedura consigliata per MVP](#best-practice-minimum-viable-product-mvp)
3. [IT centrale](#central-it)
4. [Allineamento strategico](#strategic-alignment)
5. [Allineamento operativo](#operational-alignment)
6. [Centro cloud di eccellenza (CCoE)](#cloud-center-of-excellence)

La maggior parte delle aziende inizia con poco più di un *team di adozione del cloud*. Tuttavia, si consiglia di definire una struttura organizzativa che è molto simile alla struttura delle [procedure consigliate MVP](#best-practice-minimum-viable-product-mvp) .

## <a name="cloud-adoption-team-only"></a>Solo team di adozione cloud

Il nucleo di tutte le attività di adozione del cloud è il team di adozione del cloud. Questo team guida le modifiche tecniche che consentono l'adozione. A seconda degli obiettivi del lavoro di adozione, questo team può includere una gamma diversificata di membri del team che gestiscono un'ampia gamma di attività tecniche e aziendali.

![Team di adozione del cloud con team di governance e sicurezza](../_images/ready/org-ready-adoption-only.png)

Per le attività di adozione su scala ridotta o in primo piano, questo team potrebbe essere più piccolo di una persona. In un'attività su larga scala o in ritardo, è comune avere diversi team di adozione del cloud, ognuno con circa sei ingegneri. Indipendentemente dalle dimensioni o dalle attività, l'aspetto coerente di qualsiasi team di adozione del cloud è che fornisce i mezzi per caricare le soluzioni nel cloud. Per alcune organizzazioni, può trattarsi di una struttura organizzativa sufficiente. L'articolo del [team di adozione del cloud](./cloud-adoption.md) fornisce informazioni più approfondite sulla struttura, sulla composizione e sulla funzione del team di adozione del cloud.

> [!WARNING]
> Il funzionamento con un *solo* team di adozione del cloud (o più team di adozione del cloud) viene considerato un antipattern e deve essere evitato. Come minimo, considerare la [procedura consigliata per MVP](#best-practice-minimum-viable-product-mvp).

## <a name="best-practice-minimum-viable-product-mvp"></a>Procedura consigliata: prodotto minimo valido (MVP)

Si consiglia di disporre di due team per creare un equilibrio tra le attività di adozione del cloud. Questi due team sono responsabili di diverse funzionalità per tutto il lavoro di adozione.

- **Team di adozione del cloud** Questo team è responsabile per le soluzioni tecniche, l'allineamento aziendale, la gestione dei progetti e le operazioni per le soluzioni adottate.
- **Team di governance del cloud:** Per bilanciare il team di adozione del cloud, un team di governance del cloud è dedicato a garantire l'eccellenza nelle soluzioni adottate. Il team di governance del cloud è responsabile della maturità della piattaforma, delle operazioni della piattaforma, della governance e dell'automazione.

![Adozione cloud con contrappesi per la governance del cloud](../_images/ready/org-ready-best-practice.png)

Questo approccio collaudato è considerato MVP perché potrebbe non essere sostenibile. Ogni team indossa molti cappelli, come descritto nei [grafici *responsabili, contabili, consultati, informati* (RACI)](./raci-alignment.md).

Le sezioni seguenti descrivono una struttura organizzativa completa e collaudata, oltre ad approcci per allineare la struttura appropriata alla propria organizzazione.

## <a name="central-it"></a>IT centrale

Con l'adozione delle scale, il team di governance del cloud può lottare per restare al passo con il flusso di innovazione da più team di adozione del cloud. Questa condizione è particolarmente valida negli ambienti con requisiti di conformità, operazioni o sicurezza elevati. In questa fase è comune per le aziende spostare le responsabilità del cloud a un team IT centrale esistente. Se il team è in grado di rivalutare gli strumenti, i processi e gli utenti per supportare meglio l'adozione del cloud su larga scala, l'inclusione del team IT centrale può aggiungere un valore significativo. Gli esperti in materia di operazioni, automazione, sicurezza e amministrazione per modernizzare Central IT possono condurre innovazioni operative efficaci.

![Adozione del cloud con un modello IT centrale](../_images/ready/org-ready-central-it.png)

Sfortunatamente, la fase IT centrale può essere una delle fasi più rischioso della maturità organizzativa. Il team IT centrale deve passare alla tabella con una forte mentalità di crescita. Se il team Visualizza il cloud come opportunità per aumentare e adattare le proprie capacità, può fornire un valore elevato durante il processo. Tuttavia, se il team IT centrale considera l'adozione del cloud principalmente come una minaccia per il modello esistente, il team IT centrale diventa un ostacolo ai team di adozione del cloud e agli obiettivi aziendali supportati. Alcuni team IT centrali hanno dedicato mesi o addirittura anni a provare a forzare il cloud a eseguire l'allineamento con approcci locali, con solo risultati negativi. Il cloud non richiede che tutti gli elementi cambiano all'interno dell'IT centrale, ma è necessario apportare modifiche. Se la resistenza al cambiamento è prevalente all'interno del team IT centrale, questa fase della maturità può diventare rapidamente un antipattern culturale.

I piani di adozione del cloud fortemente incentrati sulla piattaforma distribuita come servizio (PaaS), DevOps o altre soluzioni che richiedono un minor supporto per le operazioni hanno minore probabilità di visualizzare il valore durante questa fase di maturità. Al contrario, questi tipi di soluzioni sono più probabili da ostacolare o bloccare mediante tentativi di centralizzare l'IT. Un livello di maturità più elevato, ad esempio un [centro cloud di eccellenza (CCoE)](#cloud-center-of-excellence), è più probabile che restituisca risultati positivi per questi tipi di attività di trasformazione. Per comprendere le differenze tra la Central IT nel cloud e una CCoE, vedere [cloud Center of Excellence](./cloud-center-excellence.md).

## <a name="strategic-alignment"></a>Allineamento strategico

Man mano che l'investimento nell'adozione del cloud cresce e vengono realizzati i valori aziendali, gli stakeholder aziendali spesso diventano più impegnati. Un team di strategia cloud definito, come illustrato nella figura seguente, allinea le parti interessate aziendali per massimizzare il valore realizzato dagli investimenti per l'adozione del cloud.

![Aggiungere un team di strategia cloud definito](../_images/ready/org-ready-strategy-aligned.png)

Quando la maturità si verifica a livello organico, a causa delle attività di adozione del cloud gestite dall'IT, l'allineamento strategico è in genere preceduto da una governance o da un team IT centrale. Quando gli sforzi di adozione del cloud sono responsabili dell'azienda, l'attenzione al modello operativo e all'organizzazione tende a essere eseguita in precedenza. Laddove possibile, i risultati aziendali e il team di strategia cloud devono essere definiti prima del processo.

## <a name="operational-alignment"></a>Allineamento operativo

La realizzazione del valore aziendale dagli sforzi di adozione del cloud richiede operazioni stabili. Le operazioni nel cloud possono richiedere nuovi strumenti, processi o competenze. Quando sono necessarie operazioni IT stabili per ottenere risultati aziendali, è importante aggiungere un team operativo cloud definito, come illustrato di seguito.

![Aggiungere un team operativo cloud definito](../_images/ready/org-ready-operations-aligned.png)

Le operazioni cloud possono essere recapitate dai ruoli operativi IT esistenti. Tuttavia, non è insolito che le operazioni cloud siano delegate ad altre parti al di fuori delle operazioni IT. I provider di servizi gestiti, i team DevOps e le business unit spesso assumono le responsabilità associate alle operazioni cloud, con supporto e Guardrails forniti dalle operazioni IT. Questo è sempre più comune per le attività di adozione del cloud che si concentrano principalmente sulle distribuzioni DevOps o PaaS.

## <a name="cloud-center-of-excellence"></a>Centro di eccellenza cloud

Al massimo stato di maturità, un centro cloud di eccellenza allinea i team intorno a un modello operativo moderno basato sul cloud. Questo approccio fornisce funzioni IT centrali come governance, sicurezza, piattaforma e automazione.

![Centro di eccellenza cloud](../_images/ready/org-ready-ccoe.png)

La differenza principale tra questa struttura e la struttura IT centrale è focalizzata sulla self-service. I team di questa struttura organizzano con lo scopo di delegare il controllo il più possibile. L'allineamento delle procedure di governance e conformità a soluzioni native del cloud crea Guardrails e meccanismi di protezione. A differenza del modello IT centrale, l'approccio nativo per il cloud massimizza l'innovazione e riduce al minimo il sovraccarico operativo. Per l'adozione di questo modello, è necessario un accordo reciproco per modernizzare i processi IT per le aziende e la leadership IT. Questo modello è improbabile che si verifichi in modo organico e spesso richiede il supporto tecnico.

## <a name="next-steps"></a>Passaggi successivi

Dopo l'allineamento a una determinata fase di maturità della struttura organizzativa, è possibile usare i [grafici Raci](./raci-alignment.md) per allineare la responsabilità e la responsabilità in ogni team.

> [!div class="nextstepaction"]
> [Allinea il grafico RACI appropriato](./raci-alignment.md)
