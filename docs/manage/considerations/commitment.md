---
title: Criticità aziendale-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticità aziendale-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: e9ac7b930018e8eb8a8d750692de808be943db0c
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558129"
---
# <a name="business-commitment-in-cloud-management"></a>Impegno aziendale nella gestione cloud

Definire un impegno aziendale è un esercizio di bilanciamento delle priorità. L'obiettivo è allineare il livello di gestione operativo corretto a un costo operativo accettabile. Per trovare il saldo sono necessari alcuni punti dati e calcoli, descritti nelle sezioni riportate di seguito.

![Bilancia costo e resilienza](../../_images/manage/business-commitment-scale.png)

Gli impegni alla stabilità aziendale (tramite resilienza tecnica o altri influiscano sul contratto di contratto) rappresentano una decisione di motivazione aziendale. Per la maggior parte dei carichi di lavoro in un ambiente, è sufficiente un livello di base di gestione cloud. Per gli altri, un aumento del costo di 2 &ndash;4x è facilmente giustificato a causa del potenziale impatto di eventuali interruzioni aziendali. Gli articoli precedenti di questa serie aiutano a comprendere la classificazione e l'effetto delle interruzioni per diversi carichi di lavoro. Questo articolo fornirà assistenza per il calcolo dei ritorni. Come illustrato nell'immagine seguente, a ogni livello di gestione cloud sono presenti punti di flessione in cui i costi possono aumentare più velocemente rispetto all'aumento della resilienza. Questi punti di flessione richiederanno decisioni aziendali dettagliate e impegni aziendali.

## <a name="determining-a-proper-commitment-with-the-business"></a>Determinazione di un impegno appropriato per l'azienda

Per ogni carico di lavoro nel portfolio, il team operativo cloud e il team di strategia cloud devono essere allineati al livello di gestione fornito direttamente dal team operativo cloud.

Di seguito sono riportati gli aspetti chiave da allineare quando si stabilisce un impegno con l'azienda:

- Prerequisiti per operazioni IT
- Responsabilità di gestione
- Locazione cloud
- Fattori di costo soft
- ROI per evitare perdite
- Convalidare il livello di gestione

Nella parte restante di questo articolo verrà descritto ognuno di questi criteri per contribuire a prendere una decisione.

## <a name="it-operations-prerequisites"></a>Prerequisiti per operazioni IT

La [Guida di gestione di Azure](../azure-management-guide/index.md) illustra gli strumenti di gestione disponibili in Azure. Prima di raggiungere un impegno con l'azienda, è necessario determinare una linea di base di gestione del livello standard accettabile da applicare a tutti i carichi di lavoro gestiti. VIENE quindi calcolato un costo di gestione standard per ognuno dei carichi di lavoro gestiti nel portfolio IT, in base ai conteggi dei core della CPU, allo spazio su disco e ad altre variabili correlate agli asset. VIENE anche stimato un contratto di contratto composito per ogni carico di lavoro in base all'architettura.

> [!TIP]
> I team operativi IT utilizzeranno spesso un valore predefinito minimo del 99,9% di tempo di attività per il contratto di contratto iniziale composito. Possono anche scegliere di normalizzare i costi di gestione in base al carico di lavoro medio, specialmente per le soluzioni con esigenze minime di archiviazione e registrazione. La media dei costi di alcuni carichi di lavoro con criticità media può offrire un punto di partenza per le conversazioni iniziali.

> [!TIP]
> Per i lettori che usano la [cartella di lavoro di gestione delle operazioni](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud, i campi di gestione delle operazioni devono essere aggiornati per riflettere questi prerequisiti. Questi campi includono il livello di impegno, il contratto di SLA composito e il costo mensile. Il costo mensile dovrebbe rappresentare il costo degli strumenti di gestione operativi aggiunti su base mensile.

La linea di base di Operations Management fungerà da punto di partenza iniziale per la convalida in ognuna delle sezioni seguenti.

## <a name="management-responsibility"></a>Responsabilità di gestione

In un ambiente locale tradizionale, il costo della gestione dell'ambiente viene comunemente considerato un costo affondato di proprietà delle operazioni IT. Nel cloud, la gestione è una decisione intenzionale con un effetto preventivo diretto. I costi di ogni funzione di gestione possono essere attribuiti in modo più diretto a ogni carico di lavoro distribuito nel cloud. Questo approccio consente un maggiore controllo, ma crea un requisito per i team operativi cloud e i team di strategia cloud per il primo commit a un accordo relativo alle responsabilità.

**Responsabilità delegata:** Poiché non è necessario centralizzare e presupporre un sovraccarico della gestione operativa, le operazioni IT per molte organizzazioni stanno considerando i nuovi approcci. Un approccio comune viene definito responsabilità delegata. In un centro cloud del modello di eccellenza, le operazioni della piattaforma e l'automazione della piattaforma offrono strumenti di gestione self-service che possono essere sfruttati da team operativi aziendali, indipendentemente da un team operativo IT centrale. Questo approccio fornisce agli stakeholder aziendali il controllo completo sui budget correlati alla gestione. Consente inoltre a CCoE di garantire che un set minimo di Guardrails venga implementato correttamente. In questo modello, funge da broker e da una guida per aiutare le aziende a prendere decisioni sagge. Le operazioni aziendali supervisionano le operazioni quotidiane dei carichi di lavoro dipendenti.

**Responsabilità centralizzata:** I requisiti di conformità, la complessità tecnica e alcuni modelli di servizi condivisi possono richiedere un modello IT centrale. In questo modello continua a mantenere le responsabilità di gestione delle operazioni. Di conseguenza, la progettazione ambientale, i controlli di gestione e gli strumenti di governance possono essere gestiti e controllati centralmente, in modo da limitare il ruolo degli stakeholder aziendali quando si effettuano impegni di gestione. Tuttavia, la visibilità dei costi e dell'architettura degli approcci cloud rende molto più semplice per la comunicazione centralizzata il costo e il livello di gestione per ogni carico di lavoro.

**Modello misto:** La classificazione è alla base di un modello misto per gestire le responsabilità. Le aziende che si trovano in una trasformazione da locale a cloud possono richiedere un modello operativo locale per un periodo di tempo. Le altre società con requisiti di conformità severi o che dipendono da contratti a lungo termine con fornitori di outsourcing IT possono richiedere un modello operativo centralizzato. Nonostante questi tipi di vincoli, le aziende devono innovare. Quando una rapida innovazione deve prosperare, nel mezzo di un modello di responsabilità centrale IT centralizzato, la classificazione e un modello misto possono fornire un equilibrio. Con questo approccio, Central IT fornisce un modello operativo centralizzato per tutti i carichi di lavoro cruciali o che contengono informazioni riservate. Tuttavia, tutte le altre classificazioni del carico di lavoro possono essere inserite in un ambiente cloud progettato per le responsabilità delegate. L'approccio di responsabilità centralizzato funge da modello operativo generale. Il business ha quindi la flessibilità necessaria per sfruttare un modello operativo specifico, in base al livello di supporto e alla sensibilità richiesti.

Il primo passaggio consiste nel impegnarsi in un approccio di responsabilità, che consente di definire i seguenti impegni.

**Quale organizzazione sarà responsabile per la gestione delle operazioni quotidiane per questo carico di lavoro?**

## <a name="cloud-tenancy"></a>Locazione cloud

Sebbene non sia consigliabile, non è insolito che un'azienda supporti risorse in più tenant. L'articolo su Lighthouse for multi-tenant offre alcuni esempi di motivi per gli ambienti Azure multi-tenant. In base agli esempi contenuti in questo articolo, il prossimo impegno è la locazione.

**Questo carico di lavoro si trova in un singolo tenant di Azure, insieme a tutti gli altri carichi di lavoro?**

## <a name="soft-cost-factors"></a>Fattori di costo soft

Nella sezione successiva di questo articolo viene descritto un approccio ai ritorni comparative associati ai livelli di processi di gestione e agli strumenti. Alla fine di questa sezione, ogni carico di lavoro analizzato misura il costo della gestione rispetto all'impatto previsto delle rotture aziendali. Questo approccio fornirà un metodo relativamente semplice per comprendere se l'investimento in approcci di gestione più completi è garantito.

Prima di eseguire i numeri, è importante esaminare i fattori di costo flessibile. I fattori di costo flessibile producono un risultato, ma tale risultato è difficile da misurare attraverso risparmi diretti a costi ridotti, che sarebbero visibili in un'istruzione profit and loss. I fattori di costo molle sono importanti perché possono indicare la necessità di investire in un livello di gestione più elevato rispetto a quelli fiscalmente prudenti.

Alcuni esempi di questi fattori includono:

- Usare quotidianamente un carico di lavoro da parte della lavagna o del CEO.
- L'utilizzo di un carico di lavoro da parte del primo _x%_ dei clienti che comporta un maggiore effetto sui ricavi altrove.
- Effetti sulla soddisfazione dei dipendenti.

Il punto dati successivo necessario per effettuare un impegno è un elenco di fattori di costo flessibile. Questi elementi non devono essere documentati in questa fase, ma lo stakeholder aziendale deve essere a conoscenza dell'importanza di questi fattori e della loro esclusione dai calcoli seguenti.

## <a name="calculate-loss-avoidance-roi"></a>Calcolare il ROI di evitare la perdita

Quando si calcola il ritorno relativo ai costi di gestione delle operazioni, il team IT responsabile delle operazioni cloud deve completare i prerequisiti indicati in precedenza e assumere un livello minimo di gestione per tutti i carichi di lavoro.

Il prossimo impegno da effettuare è l'accettazione da parte dell'azienda dei costi associati all'offerta gestita da base.

**L'azienda accetta di investire nell'offerta di base per soddisfare gli standard minimi delle operazioni cloud?**

Se l'azienda non accetta questo livello di gestione, è necessario definire una soluzione che consenta all'azienda di procedere senza influire materialmente sulle operazioni cloud di altri carichi di lavoro.

Se l'azienda vuole un livello superiore rispetto a quello standard, il resto di questa sezione consentirà di convalidare l'investimento e i ritorni associati (sotto forma di evitare la perdita).

### <a name="increased-levels-of-management-design-principles-and-service-catalog"></a>Livelli di gestione più elevati: principi di progettazione e catalogo di servizi

Per le soluzioni gestite, esistono diversi principi di progettazione e soluzioni di modello che è possibile applicare oltre alla baseline di gestione. Ognuno dei principi di progettazione per l'affidabilità e la resilienza aggiunge il costo operativo al carico di lavoro. Per fare in modo che l'IT e l'azienda accettino questi impegni aggiuntivi, è importante comprendere le potenziali perdite che possono essere evitate grazie a un aumento degli investimenti.

Nei calcoli seguenti verranno illustrate le formule per comprendere meglio il confronto tra le perdite e gli investimenti di gestione più elevati. Per informazioni sul calcolo del costo di una maggiore gestione, vedere gli articoli sull' [automazione del carico di lavoro](./workload.md) e l'automazione della [piattaforma](./platform.md).

> [!TIP]
> Per i lettori che usano la [cartella di lavoro di gestione delle operazioni](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud, i campi di gestione delle operazioni devono essere aggiornati in modo da riflettere le singole conversazioni. Questi campi includono il livello di impegno, il contratto di SLA composito e il costo mensile. Il costo mensile dovrebbe rappresentare il costo degli strumenti di gestione operativi aggiunti su base mensile. Una volta aggiornati, questi campi aggiorneranno le formule ROI e ognuno dei campi seguenti.

### <a name="estimate-outage-hours-per-year"></a>Interruzione della stima (ore all'anno)

Il "contratto di servizio composito" è il contratto di servizio basato sulla distribuzione di ogni asset nel carico di lavoro. Il campo condurrà l'interruzione stimata (con etichetta est. Interruzione di * * * nella cartella di lavoro. Per calcolare le interruzioni stimate in ore all'anno senza utilizzare la cartella di lavoro, applicare la formula seguente:

**Interruzioni stimate = (1-percentuale di SLA composita)/* numero di ore in un anno* *

Nella cartella di lavoro viene usato il valore predefinito di 8.760 ore all'anno.

### <a name="standard-loss-impact"></a>Effetti sulla perdita standard

L'effetto della perdita standard (intitolato "Impact standard" nella cartella di lavoro) prevede l'incidenza finanziaria di qualsiasi interruzione, presupponendo che la stima di "interruzione stimata" risulti precisa. Per calcolare questa previsione senza utilizzare la cartella di lavoro, applicare la formula seguente:

**Effetto standard = interruzione stimata @ tre 9 di tempo di incirca/* ora/valore* *

Si tratta di una linea di base per i costi, qualora gli stakeholder aziendali scelgano di investire in un livello di gestione più elevato.

### <a name="composite-sla-impact"></a>Effetto del contratto di contratto composito

L'effetto del contratto di lavoro composto (intitolato "effetto del livello di impegno" nella cartella di lavoro) fornisce un effetto fiscale aggiornato, in base alle modifiche apportate al contratto di tempo. In questo modo è possibile confrontare l'effetto finanziario proiettato di entrambe le opzioni. Per calcolare questo effetto previsto senza il foglio di calcolo, applicare la formula seguente.

**Effetti contratto di servizio composito = interruzioni stimate/* tempo/valore* *

Il valore rappresenta le potenziali perdite che devono essere evitate dal livello di impegno modificato e dal nuovo contratto di Service composito.

### <a name="comparison-basis"></a>Base di confronto

La base di confronto valuta l'effetto standard e l'effetto del contratto di contratto composito per determinare quale sia il più appropriato nella colonna restituita.

### <a name="return-on-loss-avoidance"></a>Return in merito alla perdita

Se il costo della gestione di un carico di lavoro supera le perdite potenziali, l'investimento proposto nella gestione cloud potrebbe non essere fruttuoso. Per confrontare "Return on Loss inevitance", vedere la colonna denominata "Annual ROI * * * *". Per calcolare la colonna in modo autonomo, usare la formula seguente:

**Ritorni in caso di perdita = (base di confronto-(costo mensile/* 12))//(costo mensile/* 12)) **

A meno che non vi siano altri fattori di costo contenuto da considerare, questo confronto può suggerire rapidamente se è necessario un investimento più approfondito sulle operazioni cloud, sulla resilienza, sull'affidabilità o su altre aree.

## <a name="validate-the-commitment"></a>Convalidare l'impegno

A questo punto del processo, sono stati applicati gli impegni, ovvero responsabilità centralizzata o delegata, il tenant di Azure e il livello di impegno.
Ogni impegno deve essere convalidato e documentato per garantire che il team operativo cloud, il team di strategia cloud e le parti interessate aziendali siano allineati a questo impegno per gestire il carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Una volta creati gli impegni, i team operativi responsabili possono iniziare la configurazione per il carico di lavoro in questione. Per iniziare, valutare i vari approcci per l' [inventario e la visibilità](./inventory.md).

> [!div class="nextstepaction"]
> [Opzioni di inventario e visibilità](./inventory.md)
