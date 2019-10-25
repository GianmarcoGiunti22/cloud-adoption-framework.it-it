---
title: Funzionalità di governance del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descrive la formazione delle funzionalità di governance del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 33572e5de14c4d59e6281124cf488ca0e0c36aef
ms.sourcegitcommit: 15898374495761bfb76cee719e0f9189856884e6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888849"
---
# <a name="cloud-governance-capabilities"></a>Funzionalità di governance del cloud

Qualsiasi tipo di modifica genera nuovi rischi. Le funzionalità di governance del cloud assicurano che i rischi e la tolleranza ai rischi siano valutati e gestiti Questa funzionalità garantisce la corretta identificazione dei rischi che non possono essere tollerati dall'azienda. Le persone che forniscono questa funzionalità possono quindi convertire i rischi in regole aziendali. I criteri di governance vengono quindi eseguiti tramite discipline definite eseguite dai membri del personale che forniscono le funzionalità di governance del cloud.

## <a name="possible-sources-for-this-capability"></a>Possibili origini per questa funzionalità

A seconda dei risultati aziendali desiderati, le competenze necessarie per fornire funzionalità complete di governance del cloud possono essere fornite da:

- Governance IT
- Architettura aziendale
- Operazioni IT
- Infrastruttura IT
- Rete
- Identità
- Virtualizzazione
- Continuità aziendale/ripristino di emergenza
- Proprietari di applicazioni al suo interno

La funzionalità di governance del cloud identifica i rischi correlati alle versioni correnti e future. Questa funzionalità è illustrata nel tentativo di valutare i rischi, capire i potenziali effetti e prendere decisioni sulla tolleranza del rischio. In questo modo, i piani possono essere aggiornati rapidamente per riflettere le mutevoli esigenze della [funzionalità di adozione del cloud](./cloud-adoption.md).

## <a name="key-responsibilities"></a>Responsabilità principali

Il compito principale di qualsiasi funzionalità di governance del cloud è quello di bilanciare le forze in competizione di trasformazione e mitigazione dei rischi. Inoltre, la governance del cloud garantisce che l' [adozione del cloud](./cloud-adoption.md) sia in grado di riconoscere i dati e le linee guida sull'architettura e sulla classificazione degli asset che governano tutti Il Team collaborerà anche con il [centro cloud di eccellenza](./cloud-center-of-excellence.md) per applicare approcci automatici alla regolamentazione degli ambienti cloud.

Queste attività vengono in genere eseguite dalla funzionalità di governance del cloud su base mensile.

**Attività di pianificazione preliminare:**

- Comprendere i [rischi aziendali](../govern/policy-compliance/risk-tolerance.md) introdotti dal piano
- Rappresenta la [tolleranza dell'azienda per il rischio](../govern/policy-compliance/risk-tolerance.md)
- Supporto per la creazione di un [MVP di governance](../govern/guides/index.md)

**Attività mensili in corso:**

- Informazioni [sui rischi aziendali](../govern/policy-compliance/risk-tolerance.md) introdotti durante ogni versione
- Rappresenta la [tolleranza dell'azienda per il rischio](../govern/policy-compliance/risk-tolerance.md)
- Contribuire al miglioramento incrementale dei [criteri e dei requisiti di conformità](../govern/policy-compliance/index.md)

## <a name="meeting-cadence"></a>Cadenza riunione

La funzionalità di governance del cloud viene in genere fornita da un team funzionante. Il tempo di impegno di ogni membro del team rappresenterà un'alta percentuale delle pianificazioni giornaliere. I contributi non saranno limitati alle riunioni e ai cicli di feedback.

## <a name="additional-participants"></a>Altri partecipanti

Di seguito sono riportati i partecipanti che parteciperanno spesso alle attività di governance del cloud:

- I leader della gestione intermedia e i collaboratori diretti nei ruoli principali che sono stati designati per rappresentare l'azienda consentiranno di valutare le tolleranze dei rischi.
- Le funzionalità di governance del cloud sono fornite da un'estensione della [funzionalità di strategia cloud](./cloud-strategy.md). Proprio come il CIO e i leader aziendali sono tenuti a partecipare alle funzionalità di strategia cloud, è previsto che i loro dipendenti diretti partecipino alle attività di governance del cloud.
- I dipendenti aziendali membri della Business Unit che collaborano a stretto contatto con la leadership della line-of-business devono essere autorizzati a prendere decisioni in merito a rischi aziendali e tecnici.
- I dipendenti di Information Technology (IT) e Information Security (IS) che comprendono gli aspetti tecnici della trasformazione cloud possono essere utilizzati in una capacità girevole anziché essere un provider coerente di funzionalità di governance del cloud.

## <a name="maturation-of-cloud-governance-capability"></a>Maturazione della funzionalità di governance del cloud

Alcune organizzazioni di grandi dimensioni hanno team dedicati esistenti che si concentrano sulla governance IT. Questi team sono specializzati nella gestione dei rischi nel portfolio IT attraverso metodologie come ITIL o ITSM. Quando questi team esistono, i modelli di maturità seguenti possono essere accelerati rapidamente. Tuttavia, il team di governance IT è invitato a esaminare il modello di governance del cloud per comprendere il modo in cui la governance si sposta leggermente nel cloud. Gli articoli chiave includono l' [estensione dei criteri aziendali al cloud](../govern/corporate-policy.md) e le [cinque discipline della governance del cloud](../govern/governance-disciplines.md).

**Nessuna governance:** Le organizzazioni si spostano spesso nel cloud senza piani chiari per la governance. Prima di tutto, le problematiche relative alla sicurezza, ai costi, alla scalabilità e alle operazioni iniziano ad avviare conversazioni sulla necessità di un modello di governance e di persone per il personale dei processi associati a tale modello. Iniziare le conversazioni prima che diventino problematiche è sempre un buon primo passo per superare l'antipattern di "No governance". La sezione sulla [definizione dei criteri aziendali](../govern/corporate-policy.md) consente di semplificare le conversazioni.

**Governance bloccata:** Quando la sicurezza, i costi, la scalabilità e le operazioni non rispondono, i progetti e gli obiettivi aziendali tendono a essere bloccati. La mancanza di governance corretta genera paura, incertezze e dubbi tra gli stakeholder e i tecnici. Arrestare questa operazione nelle tracce intervenendo in anticipo. Le due guide di governance definite nel Framework di adozione cloud possono essere utili per avviare Small, impostare inizialmente i criteri di limitazione per ridurre al minimo le incertezze e la governance matura nel tempo. Scegliere una guida [aziendale complessa](../govern/guides/complex/index.md) o una [Guida aziendale standard](../govern/guides/standard/index.md).

**Governance volontaria:** In ogni azienda tende a essere brave anime. Questi ultimi sono disposti a entrare e aiutare il team a imparare dagli errori. Spesso questo è il modo in cui viene avviata la governance, soprattutto in aziende più piccole Queste brave anime tentano di risolvere alcuni problemi e spingono i team di adozione del cloud verso un set di procedure consigliate coerente e ben gestito.

Gli sforzi di questi individui sono molto migliori rispetto agli scenari di "non governance" o "governance bloccata". Sebbene il loro lavoro debba essere elogiato, questo approccio non dovrebbe essere confuso con la governance. Una governance appropriata richiede più del supporto sporadico per garantire la coerenza, che rappresenta l'obiettivo di un approccio di governance valido. Le linee guida nelle [cinque discipline della governance del cloud](../govern/governance-disciplines.md) possono contribuire allo sviluppo di questa disciplina.

**Custode del cloud:** Questo moniker è diventato un badge di onore per molti architetti di cloud specializzati nella governance delle fasi iniziali. Quando le procedure di governance iniziano per la prima volta, i risultati appaiono simili a quelli dei volontari di governance. Esiste tuttavia una differenza fondamentale. Un custode del cloud ha un piano in mente. In questa fase della maturità, il team dedica tempo alla pulizia dei pasticci creati dagli architetti del cloud che hanno prima di loro. Tuttavia, il custode del cloud allinea il lavoro a un [criterio aziendale](../govern/corporate-policy.md)ben strutturato. Usano anche strumenti di automazione della governance, come quelli descritti nell' [MVP della governance](../govern/guides/complex/index.md).

Un'altra differenza fondamentale tra un custode del cloud e un volontario di governance è il supporto per la leadership. Il volontario mette in eccedenza alcune ore rispetto alle aspettative regolari, a causa della loro missione di apprendimento e di esecuzione. Il custode del cloud ottiene supporto da parte della leadership per ridurre i compiti giornalieri per garantire che le allocazioni di tempo possano essere investite nel miglioramento della governance del cloud.

**Sorveglianza cloud:** Poiché le procedure di governance si solidificano e vengono accettate dai team di adozione del cloud, il ruolo degli architetti del cloud che specializzano i cambiamenti di governance è un po', così come il ruolo del team di governance cloud In genere, le procedure più mature ottengono l'attenzione di altri esperti in materia che possono contribuire a rafforzare le protezioni fornite dalle implementazioni della governance.

Sebbene la differenza sia sottile, si tratta di una distinzione importante per lo sviluppo di una cultura IT orientata alla governance. Un custode del cloud mette a posto i pasticci di cloud architect innovativi e i due ruoli hanno obiettivi naturalmente in conflitto e opposti. Un guardiano del cloud si occupa di mantenere sicuro il cloud, in modo che altri cloud architect possano procedere più rapidamente, senza troppi pasticci.

I tutori cloud iniziano a usare approcci di governance più avanzati per accelerare la distribuzione della piattaforma e aiutare i team a soddisfare le proprie esigenze ambientali, in modo da potersi spostare più velocemente. Esempi di queste funzioni più avanzate sono riportate nei miglioramenti incrementali apportati all'MVP della governance, ad esempio il [miglioramento della linea di base di sicurezza](../govern/guides/complex/security-baseline-improvement.md).

**Acceleratori cloud:** I sorveglianti cloud e i depositari del cloud raccolgono naturalmente gli script e le automazioni che accelerano la distribuzione di ambienti, piattaforme o persino componenti di varie applicazioni. La cura e la condivisione di questi script oltre alle responsabilità di governance centralizzata sviluppano un livello elevato di rispetto per questi architetti.

I professionisti della governance che condividono apertamente gli script curati aiutano a offrire progetti tecnologici più velocemente e a incorporare la governance nell'architettura dei carichi di lavoro. Questo carico di lavoro influenza e supporta i modelli di progettazione efficaci elevare gli acceleratori cloud a un rango superiore di specialisti di governance.

**Governance globale:** Quando le organizzazioni dipendono dalle esigenze IT a livello globale, è possibile che si verifichino deviazioni significative in operazioni e governance in diverse aree geografiche. Le richieste di business unit e anche i requisiti di sovranità dei dati locali possono causare l'interferenza delle procedure consigliate per la governance. In questi scenari, un modello di governance a più livelli consente la coerenza minima e la governance localizzata. L'articolo su [più livelli di governance](../govern/guides/complex/multiple-layers-of-governance.md) offre maggiori informazioni sul raggiungimento di questo livello di maturità.

Ogni azienda è univoca, quindi le loro esigenze di governance. Scegli il livello di maturità che ti serve per la tua organizzazione e usa il Framework di adozione del cloud per guidare le procedure, i processi e gli strumenti per aiutarti a trovarti.

## <a name="next-steps"></a>Passaggi successivi

Con la maturità del cloud governance, i team potranno adottare il cloud a ritmi sempre più rapidi. Gli sforzi continui di adozione del cloud tendono a attivare la maturità negli interventi IT. Questa maturazione può anche richiedere lo sviluppo di [funzionalità per le operazioni cloud](./cloud-operations.md).

> [!div class="nextstepaction"]
> [Sviluppare funzionalità per le operazioni cloud](./cloud-operations.md)
