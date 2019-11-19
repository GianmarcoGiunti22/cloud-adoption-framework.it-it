---
title: Stabilire processi di conformità ai criteri
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definire i processi per garantire la conformità ai criteri aziendali.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6671efc087d718a44de97062dcf8c32498cfdb81
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74159850"
---
<!-- markdownlint-disable MD026 -->

# <a name="establish-policy-adherence-processes"></a>Stabilire processi di conformità ai criteri

Dopo la definizione delle istruzioni dei criteri cloud e l'elaborazione di una guida di progettazione, è necessario creare una strategia per garantire che la distribuzione cloud sia conforme ai requisiti dei criteri. Questa strategia dovrà includere i processi di revisione e comunicazione continui del team di governance del cloud, definire i criteri per il momento in cui le violazioni dei criteri richiedono un'azione e definire i requisiti per i sistemi di monitoraggio e conformità automatici che faranno rilevare le violazioni e attivare le azioni correttive.

Vedere le sezioni relative ai criteri aziendali delle [guide di governance](../guides/index.md) utilizzabili per esempi di come il processo di conformità dei criteri rientra in un piano di governance del cloud.

## <a name="prioritize-policy-adherence-processes"></a>Classificare i processi di conformità ai criteri

Quanto investimento nello sviluppo dei processi è necessario per supportare gli obiettivi dei criteri? A seconda delle dimensioni e del livello di maturità della distribuzione cloud, l'impegno necessario per stabilire i processi che supportano la conformità, e i costi associati per farlo, possono variare notevolmente.

Per distribuzioni di piccole dimensioni costituite da risorse di sviluppo e test, i requisiti dei criteri possono essere semplici e richiedere poche risorse dedicate. D'altra parte, una distribuzione cloud matura e cruciale con esigenze di sicurezza e prestazioni di alta priorità può richiedere un team di personale, processi interni completi e strumenti di monitoraggio personalizzati per supportare gli obiettivi dei criteri.

Come primo passaggio nella definizione della strategia di conformità ai criteri, bisogna valutare il modo in cui i processi descritti di seguito possono supportare i requisiti dei criteri. Determinare l'impegno che vale la pena investire in questi processi e quindi usare queste informazioni per stabilire budget realistici e piani del personale che soddisfino queste esigenze.

## <a name="establish-cloud-governance-team-processes"></a>Definire i processi del team di governance del cloud

Prima di definire i trigger per la correzione della conformità dei criteri, è necessario stabilire i processi complessivi che verranno usati dal team e il modo in cui le informazioni verranno condivise ed Escalate tra il personale IT e il team di governance del cloud.

### <a name="assign-cloud-governance-team-members"></a>Assegnare i membri del team di governance del cloud

Il team di governance del cloud fornirà indicazioni continue sulla conformità dei criteri e gestirà i problemi relativi ai criteri che emergono quando si distribuiscono e si gestiscono le risorse cloud. Quando si compila questo team, invitare i membri del personale che hanno esperienza nelle aree coperte dalle istruzioni dei criteri definite e i rischi identificati.

Per le distribuzioni di test iniziali, questo può essere limitato a pochi amministratori di sistema responsabili della definizione delle nozioni di base della governance. Con la maturità dei processi di governance, esaminare regolarmente l'appartenenza del team di linee guida per assicurarsi che sia possibile risolvere correttamente nuovi rischi potenziali e requisiti dei criteri. Identificare i membri del personale IT e del personale aziendale con esperienza o interesse per aree specifiche di governance e includerle nei team su base permanente o temporanea, se necessario.

### <a name="reviews-and-policy-iteration"></a>Revisioni e iterazione dei criteri

Con la distribuzione di risorse e carichi di lavoro aggiuntivi, il team di governance del cloud dovrà garantire che i nuovi carichi di lavoro o gli asset siano conformi ai requisiti dei criteri. Valutare i nuovi requisiti dei team di sviluppo del carico di lavoro per garantire che le distribuzioni pianificate siano allineate alle guide di progettazione e aggiornare i criteri per supportare tali requisiti quando appropriato.

Pianificare la valutazione di nuovi rischi potenziali e aggiornare le istruzioni di criteri e le guide di progettazione in base alle esigenze. Collaborare con i team IT e del carico di lavoro per valutare regolarmente le nuove funzionalità e i servizi di Azure. Pianificare anche i cicli di revisione regolari ognuno dei cinque disciplinari di governance per garantire che i criteri siano correnti e conformi.

### <a name="education"></a>Istruzione

La conformità ai criteri richiede che il personale e gli sviluppatori IT comprendano i requisiti dei criteri che influiscono sulle proprie aree di responsabilità. Pianificare di riservare risorse per documentare le decisioni e i requisiti e formare tutti i team pertinenti sulle guide di progettazione che supportano i requisiti dei criteri.

Quando i criteri cambiano, è necessario aggiornare regolarmente la documentazione e i materiali di formazione e assicurarsi che gli sforzi di formazione comunichino requisiti e materiale sussidiario aggiornati al personale IT pertinente.

In diverse fasi del percorso Cloud, può essere opportuno consultare i partner e i programmi di formazione professionale per migliorare l'istruzione del team, sia tecnicamente che procedurale. Inoltre, molti ritengono che le certificazioni formali siano un'aggiunta preziosa al portfolio di formazione e che debbano essere prese in considerazione.

### <a name="establish-escalation-paths"></a>Stabilire percorsi di escalation

Se una risorsa diventa non conforme, chi riceve la notifica? Se il personale IT rileva un problema di conformità dei criteri, chi dovrebbe contattare? Verificare che il processo di escalation al team di governance del cloud sia chiaramente definito. Verificare che questi canali di comunicazione siano mantenuti aggiornati in modo da riflettere modifiche del personale e dell'organizzazione.

## <a name="violation-triggers-and-actions"></a>Trigger di violazione e azioni

Dopo aver definito il team di governance del cloud e i relativi processi, è necessario definire in modo esplicito quali sono le violazioni di conformità che attivano le azioni e le azioni da eseguire.

### <a name="define-triggers"></a>Definire i trigger

Per ognuna delle istruzioni dei criteri, esaminare i requisiti per determinare cosa costituisce una violazione dei criteri. Generare i trigger usando le informazioni già configurate come parte del processo di definizione dei criteri.

- **Tolleranza al rischio:** Creare trigger di violazione basati sulle metriche e sugli indicatori di rischio definiti come parte dell' [analisi della tolleranza di rischio](./risk-tolerance.md).
- **Requisiti dei criteri definiti:** Le istruzioni dei criteri possono fornire contratti di servizio, continuità aziendale e ripristino di emergenza (BCDR) o requisiti di prestazioni che devono essere usati come base per i trigger di conformità.

### <a name="define-actions"></a>Definire le azioni

Ogni trigger di violazione deve avere un'azione corrispondente. Quando si verifica una violazione, le azioni attivate devono informare sempre un membro del team IT o di governance del cloud appropriato. Questa notifica può condurre a una revisione manuale del problema di conformità o a un processo di correzione predefinito a seconda del tipo e della gravità della violazione rilevata.

Alcuni esempi di trigger di violazione e azioni:

| Disciplina di governance cloud | Trigger di esempio | Azione di esempio |
|-----------------------------|----------------|---------------|
| Gestione dei costi | Spesa mensile per il cloud superiore di oltre il 20% rispetto al previsto. | Inviare una notifica al responsabile dell'unità di fatturazione che inizierà a esaminare l'utilizzo delle risorse. |
| Baseline di sicurezza | Rilevare attività utente sospette. | Inviare una notifica al team di sicurezza IT e disabilitare l'account utente sospetto. |
| Coerenza delle risorse | L'utilizzo della CPU per un carico di lavoro è superiore al 90%. | Inviare una notifica al team operativo IT e ridimensionare le risorse aggiuntive per gestire il carico. |

## <a name="automation-of-monitoring-and-compliance"></a>Automazione del monitoraggio e della conformità

Dopo aver definito i trigger di violazione di conformità e le azioni, è possibile iniziare a pianificare il modo migliore per usare strumenti di registrazione e reporting e altre funzionalità della piattaforma cloud per automatizzare la strategia di monitoraggio e di conformità dei criteri.

Per informazioni sulla scelta del modello di monitoraggio migliore per la distribuzione, vedere la [Guida alla decisione relativa alla registrazione e alla creazione di report](../../decision-guides/logging-and-reporting/index.md).

## <a name="next-steps"></a>Passaggi successivi

Scopri di più sulla conformità alle normative nel cloud.

> [!div class="nextstepaction"]
> [Conformità alle normative](./regulatory-compliance.md)
