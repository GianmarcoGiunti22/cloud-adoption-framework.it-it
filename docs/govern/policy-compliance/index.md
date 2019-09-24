---
title: Preparare i criteri IT aziendali per il cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del concetto di criteri aziendali in relazione alla governance del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2c8907d3b80d6638ed7330063b231f22ae93943a
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223686"
---
<!-- markdownlint-disable MD026 -->

# <a name="prepare-corporate-it-policy-for-the-cloud"></a>Preparare i criteri IT aziendali per il cloud

La governance del cloud è il prodotto di un lavoro continuativo di adozione nel tempo, poiché una vera e propria trasformazione duratura non si verifica nel corso di una sola notte. Il tentativo di fornire una governance del cloud completa prima di affrontare i principali cambiamenti dei criteri aziendali con un metodo rapido e aggressivo produce raramente i risultati desiderati. In alternativa, è consigliabile un approccio incrementale.

La peculiarità di Cloud Adoption Framework è data dal ciclo di acquisto e da come tale ciclo possa consentire un'autentica trasformazione. Non essendo richiesti ingenti investimenti di capitale, i tecnici possono iniziare prima la sperimentazione e l'adozione. Nella maggior parte delle culture aziendali l'eliminazione dell'ostacolo all'adozione rappresentato dalle spese di investimento può portare a cicli di feedback più stretti, crescita organica ed esecuzione incrementale.

Il cambiamento verso l'adozione del cloud richiede un cambiamento nella governance. In molte organizzazioni la trasformazione dei criteri aziendali porta ad avere una governance migliore e velocità più elevate di conformità tramite modifiche incrementali ai criteri e applicazione automatizzata di tali modifiche, basata su funzionalità definite da configurare con il provider di servizi cloud.

Questo articolo illustra le attività principali che contribuiscono alla definizione dei criteri aziendali per abilitare un modello di governance esteso.

## <a name="define-corporate-policy-to-mature-cloud-governance"></a>Definire i criteri aziendali per una governance del cloud matura

Nell'ambito della governance tradizionale e incrementale i criteri aziendali creano la definizione operativa di governance. La maggior parte delle azioni di governance IT cerca di implementare la tecnologia per monitorare, applicare, operare e automatizzare tali criteri aziendali. La governance del cloud si basa su concetti simili.

![Governance aziendale e discipline di governance](../../_images/operational-transformation-govern-highres.png)

*Figura 1 - Governance aziendale e discipline di governance.*

L'immagine precedente illustra l'interazione tra rischi aziendali, criteri e conformità e monitoraggio e applicazione per creare una strategia di governance. È seguita dalle cinque discipline della governance del cloud da usare per realizzare tale strategia.

## <a name="review-existing-policies"></a>Revisione dei criteri esistenti

Nell'immagine precedente la strategia di governance (rischi, criteri e conformità, monitoraggio e applicazione) ha inizio riconoscendo i rischi aziendali. Comprendere come cambiano i [rischi aziendali](./business-risk.md) nel cloud è il primo passo per creare una strategia duratura per la governance del cloud. Lavorare con le business unit per ottenere una [valutazione accurata della tolleranza dell'azienda ai rischi](./risk-tolerance.md) consente di comprendere quale livello di rischio deve essere mitigato. Capire quali sono i nuovi rischi e qual è la soglia di tolleranza accettabile rende possibile potenziare una [revisione dei criteri esistenti](./cloud-policy-review.md), per determinare il livello necessario di governance appropriata per l'organizzazione.

> [!TIP]
> Se l'organizzazione è disciplinata da requisiti di conformità di terze parti, uno dei rischi aziendali maggiori da prendere in considerazione può essere un rischio di aderenza alla [conformità con le normative](./regulatory-compliance.md). Spesso questo rischio non può essere mitigato e può richiedere invece una rigorosa aderenza. Assicurarsi di riconoscere i requisiti di conformità di terze parti prima di iniziare una revisione dei criteri.

## <a name="an-incremental-approach-to-cloud-governance"></a>Approccio incrementale alla governance del cloud

Un approccio incrementale alla governance del cloud presuppone che non sia accettabile superare la [tolleranza dell'azienda ai rischi](./risk-tolerance.md). Al contrario, presuppone che il ruolo della governance sia quello di accelerare il cambiamento aziendale, aiutare i tecnici a comprendere le linee guida a livello di architettura e verificare che i [rischi aziendali](./business-risk.md) vengano comunicati e mitigati regolarmente. In alternativa, il ruolo tradizionale della governance può diventare un ostacolo all'adozione a livello di personale tecnico o dell'azienda nel suo complesso.

Con un approccio incrementale alla governance del cloud, talvolta si creano delle tensioni naturali tra i team che creano nuove soluzioni di business e quelli che tutelano l'azienda dai rischi. Tuttavia, in questo modello questi due team possono collaborare al miglioramento. Lavorando sullo stesso piano, il team di governance del cloud e quelli di adozione del cloud iniziano a collaborare per esporre, valutare e mitigare i rischi aziendali. Questo lavoro congiunto può diventare un modo naturale per ridurre gli attriti e rinsaldare la collaborazione tra i team.

## <a name="minimum-viable-product-mvp-for-policy"></a>Prodotto minimo funzionante (MVP) per i criteri

Il primo passaggio in una collaborazione emergente tra i team di governance e di adozione del cloud è un accordo sulla definizione di un prodotto minimo funzionante (MVP, Minimum Viable Product) per i criteri. Un MVP per la governance del cloud dovrebbe riconoscere che i rischi aziendali sono minimi all'inizio, ma tendono ad aumentare man mano che l'organizzazione adotta più servizi cloud nel corso del tempo.

Per un'organizzazione che distribuisce cinque macchine virtuali che non contengono dati con impatto aziendale elevato, ad esempio, i rischi per l'azienda sono contenuti. È solo più tardi nel processo di adozione del cloud, quando il numero delle macchine virtuali arriva a 1.000 e l'azienda inizia a spostare dati a elevato impatto, che i rischi aziendali aumentano.

Il prodotto minimo funzionante per i criteri tenta di definire una base necessaria per i criteri richiesti per distribuire le prime _x_ macchine virtuali o le prime _x_ applicazioni, dove _x_ è una quantità ridotta ma comunque significativa delle unità adottate. Questo set di criteri richiede alcuni vincoli, ma includerà gli aspetti fondamentali necessari per crescere rapidamente tra un intervento di adozione del cloud incrementale e quello successivo. Tramite lo sviluppo incrementale dei criteri, questa strategia di governance crescerà nel tempo. Attraverso cambiamenti lenti e impercettibili, il prodotto minimo funzionante per i criteri si trasformerà in una parità delle funzionalità con gli output dell'esercizio di revisione dei criteri.

## <a name="incremental-policy-growth"></a>Crescita incrementale dei criteri

La crescita incrementale dei criteri è il meccanismo chiave per la crescita dei criteri e della governance del cloud nel tempo. È anche il requisito chiave per l'adozione di un modello incrementale per la governance. Per il corretto funzionamento di questo modello, il team di governance deve attenersi a un'allocazione continuativa del tempo a ogni incremento, per essere in grado di valutare e implementare le discipline di governance in continua evoluzione.

**Requisiti per i periodi di incremento:** all'inizio di ogni iterazione, tutti i team di adozione del cloud creano un elenco degli asset che devono essere migrati o adottati nell'incremento corrente. Il team di governance del cloud dovrebbe consentire tempo sufficiente per esaminare l'elenco, convalidare le classificazioni dei dati per gli asset, valutare eventuali nuovi rischi associati a ogni asset, aggiornare le indicazioni per l'architettura e informare il team sulle modifiche. Queste attività richiedono in genere da 10 a 30 ore per ogni incremento. È inoltre previsto che questo livello di coinvolgimento richieda almeno un dipendente dedicato per la gestione della governance in uno sforzo di adozione del cloud su vasta scala.

**Requisiti per i periodi di rilascio:** all'inizio di ogni rilascio, i team di adozione del cloud e il team di strategia del cloud devono stabilire le priorità di un elenco di applicazioni o carichi di lavoro di cui eseguire la migrazione nell'iterazione corrente, insieme a eventuali attività di modifica aziendale. Questi punti dati consentono al team di governance del cloud di identificare tempestivamente i nuovi rischi aziendali, garantendo il tempo necessario per allinearsi con l'azienda e valutarne la tolleranza ai rischi.

## <a name="next-steps"></a>Passaggi successivi

Una strategia di governance del cloud efficace inizia dalla comprensione dei rischi aziendali.

> [!div class="nextstepaction"]
> [Informazioni sul rischio aziendale](./business-risk.md)
