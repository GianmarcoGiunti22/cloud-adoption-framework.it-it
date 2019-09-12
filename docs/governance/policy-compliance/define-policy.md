---
title: Definire i criteri aziendali per la governance del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come definire i criteri per riflettere e correggere i rischi.
author: BrianBlanchard
ms.author: brblanch
ms.date: 01/02/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 3030ecc46e708667285b8094d68a61f4115d138f
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70824704"
---
# <a name="define-corporate-policy-for-cloud-governance"></a>Definire i criteri aziendali per la governance del cloud

Dopo aver analizzato i rischi noti e le tolleranze di rischio correlate per il percorso di trasformazione cloud dell'organizzazione, il passaggio successivo consiste nel definire i criteri che risolveranno in modo esplicito tali rischi e definire i passaggi necessari per risolverli laddove possibile.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-corporate-it-policy-become-cloud-ready"></a>Come predisporre i criteri IT aziendali per il cloud?

Nell'ambito della governance tradizionale e incrementale i criteri aziendali creano la definizione operativa di governance. La maggior parte delle azioni di governance IT cerca di implementare la tecnologia per monitorare, applicare, operare e automatizzare tali criteri aziendali. La governance del cloud si basa su concetti simili.

![Governance aziendale e discipline di governance](../../_images/operational-transformation-govern-highres.png)

*Figura 1 - Governance aziendale e discipline di governance.*

L'immagine precedente illustra la relazione tra il rischio aziendale, i criteri e la conformità e i meccanismi di monitoraggio e applicazione che dovranno interagire nell'ambito della strategia di governance. Le cinque discipline della governance del cloud consentono di gestire queste interazioni e di realizzare la strategia.

La governance del cloud è il prodotto di un lavoro continuativo di adozione nel tempo, poiché una vera e propria trasformazione duratura non si verifica nel corso di una sola notte. Il tentativo di fornire una governance del cloud completa prima di affrontare i principali cambiamenti dei criteri aziendali con un metodo rapido e aggressivo produce raramente i risultati desiderati. In alternativa, è consigliabile un approccio incrementale.

Il ciclo di acquisto è diverso da quello di un Framework di adozione del cloud e può consentire una trasformazione autentica. Poiché non esiste un requisito di acquisizione di grosse spese in conto capitale, i tecnici possono iniziare a sperimentare e adottare prima di tutto. Nella maggior parte delle culture aziendali l'eliminazione dell'ostacolo all'adozione rappresentato dalle spese di investimento può portare a cicli di feedback più stretti, crescita organica ed esecuzione incrementale.

Il cambiamento verso l'adozione del cloud richiede un cambiamento nella governance. In molte organizzazioni, la trasformazione dei criteri aziendali porta ad avere una governance migliore e maggiori frequenze di conformità tramite modifiche incrementali ai criteri e all'applicazione automatizzata di tali modifiche, basata su funzionalità definite da configurare con il provider di servizi cloud.

<!-- markdownlint-enable MD026 -->

## <a name="review-existing-policies"></a>Revisione dei criteri esistenti

Poiché la governance è un processo continuo, i criteri devono essere periodicamente rivisti con il personale IT e le parti interessate per garantire che le risorse ospitate nel cloud continuino a mantenere la conformità con gli obiettivi e i requisiti aziendali complessivi. Capire quali sono i nuovi rischi e qual è la soglia di tolleranza accettabile rende possibile potenziare una [revisione dei criteri esistenti](what-is-a-cloud-policy-review.md), per determinare il livello necessario di governance appropriata per l'organizzazione.

> [!TIP]
> Se l'organizzazione usa i fornitori o altri partner commerciali attendibili, uno dei principali rischi aziendali da considerare potrebbe essere la mancanza di [conformità alla conformità normativa](what-is-regulatory-compliance.md) da parte di queste organizzazioni esterne. Questo rischio spesso non può essere risolto e può invece richiedere una rigorosa aderenza ai requisiti di tutte le parti. Assicurarsi di aver identificato e compreso i requisiti di conformità di terze parti prima di iniziare una revisione dei criteri.

## <a name="create-cloud-policy-statements"></a>Creare istruzioni dei criteri del cloud

I criteri IT basati sul cloud stabiliscono i requisiti, gli standard e gli obiettivi che i sistemi automatizzati e il personale IT dovranno supportare. Le decisioni relative ai criteri sono un fattore primario all'interno della [Progettazione dell'architettura cloud](align-governance-journeys.md) e nell'implementazione dei [processi di adesione ai criteri](processes.md).

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Anche se questi criteri possono essere integrati nella documentazione più ampia relativa ai criteri aziendali, le istruzioni per i criteri cloud discusse in tutte le indicazioni sul Framework di adozione del cloud tendono a essere un riepilogo più conciso dei rischi e dei piani da affrontare. Ogni definizione deve includere i tipi di informazioni seguenti:

- **Rischio aziendale**: Riepilogo del rischio che verrà risolto da questi criteri.
- **Definizione dei criteri**: Una spiegazione concisa dei requisiti dei criteri e gli obiettivi.
- **Indicazioni tecniche e di progettazione:** Suggerimenti pratici, specifiche o altro materiale sussidiario per supportare e applicare i criteri, che i team IT e gli sviluppatori possono usare per progettare e realizzare le distribuzioni cloud.

Se occorre assistenza per le attività iniziali con la definizione dei criteri, consultare le [discipline di governance](../governance-disciplines.md) introdotte nella panoramica della sezione di governance. Gli articoli per ognuna di queste discipline includono esempi di rischi aziendali comuni che si verificano durante il passaggio al cloud e i criteri di esempio usati per correggere i rischi (ad esempio, vedere le definizioni dei [criteri di esempio](../cost-management/policy-statements.md)della disciplina di gestione dei costi).

## <a name="incremental-governance-and-integrating-with-existing-policy"></a>Governance incrementale e integrazione con i criteri esistenti

Le aggiunte pianificate all'ambiente cloud devono sempre essere esaminate per conformità con i criteri esistenti e con i criteri di aggiornamento da considerare per eventuali problemi non trattati. È consigliabile anche eseguire con regolarità una [revisione dei criteri del cloud](what-is-a-cloud-policy-review.md) per garantire che i criteri del cloud siano sincronizzati con tutti i criteri aziendali nuovi e aggiornati.

La necessità di integrare i criteri del cloud con i criteri IT legacy, dipende in larga misura dalla maturità dei processi di governance del cloud e dalle dimensioni dei tuoi cloud. Consultare l'articolo sulle [governance incrementali e i criteri di MVP](index.md) per una discussione più ampia sulla gestione di integrazione dei criteri durante la trasformazione cloud.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver definito le vostre politiche, redigere una guida alla progettazione dell'architettura per fornire al personale IT e agli sviluppatori una guida pratica.

> [!div class="nextstepaction"]
> [Allinea la guida alla progettazione della governance ai criteri aziendali](./align-governance-journeys.md)
