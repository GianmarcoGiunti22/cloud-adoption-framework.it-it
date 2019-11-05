---
title: 'Impegno aziendale: gestione e operazioni del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Impegno aziendale: gestione e operazioni del cloud'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: f5461ea659ae2363e98ddf45d8623e21f1ce0d90
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565202"
---
# <a name="business-commitment-in-cloud-management"></a>Impegno aziendale nella gestione cloud

La definizione dell' _impegno aziendale_ è un esercizio di bilanciamento delle priorità. L'obiettivo è allineare il livello di gestione operativo corretto a un costo operativo accettabile. Per trovare il saldo sono necessari alcuni punti dati e calcoli, descritti in questo articolo.

![Bilancia costo e resilienza](../../_images/manage/business-commitment-scale.png)

Gli impegni alla stabilità aziendale, attraverso la resilienza tecnica o un altro influsso di contratto di servizio (SLA), costituiscono una decisione di motivazione aziendale. Per la maggior parte dei carichi di lavoro in un ambiente, è sufficiente un livello di base di gestione cloud. Per gli altri, un aumento dei costi da 2x a 4x è facilmente giustificato a causa del potenziale impatto di eventuali interruzioni aziendali.

Gli articoli precedenti di questa serie possono essere utili per comprendere la classificazione e l'effetto delle interruzioni per diversi carichi di lavoro. Questo articolo consente di calcolare i ritorni. Come illustrato nell'immagine precedente, ogni livello di gestione del cloud presenta punti di flessione in cui i costi possono aumentare più velocemente rispetto all'aumento della resilienza. Questi punti di flessione richiederanno decisioni aziendali dettagliate e impegni aziendali.

## <a name="determine-a-proper-commitment-with-the-business"></a>Determinare un impegno appropriato per l'azienda

Per ogni carico di lavoro nel portfolio, il team operativo cloud e il team di strategia cloud devono essere allineati al livello di gestione fornito direttamente dal team operativo cloud.

Poiché si sta definendo un impegno con l'azienda, è necessario allineare alcuni aspetti fondamentali:

- Prerequisiti per operazioni IT
- Responsabilità di gestione
- Locazione cloud
- Fattori di costo soft
- ROI per evitare perdite
- Convalida del livello di gestione

Per semplificare il processo decisionale, nella parte restante di questo articolo vengono descritti in modo più dettagliato ognuno di questi aspetti.

## <a name="it-operations-prerequisites"></a>Prerequisiti per operazioni IT

La [Guida di gestione di Azure](../azure-management-guide/index.md) descrive gli strumenti di gestione disponibili in Azure. Prima di raggiungere un impegno con l'azienda, è necessario determinare una linea di base di gestione di livello standard accettabile da applicare a tutti i carichi di lavoro gestiti. VIENE quindi calcolato un costo di gestione standard per ognuno dei carichi di lavoro gestiti nel portfolio IT, in base ai conteggi dei core della CPU, allo spazio su disco e ad altre variabili correlate agli asset. VIENE anche stimato un contratto di contratto composito per ogni carico di lavoro, in base all'architettura.

> [!TIP]
> I team operativi IT usano spesso un valore minimo predefinito del 99,9% di tempo di attività per il contratto di contratto iniziale composito. Potrebbero anche scegliere di normalizzare i costi di gestione in base al carico di lavoro medio, specialmente per le soluzioni con esigenze minime di archiviazione e registrazione. La media dei costi di alcuni carichi di lavoro con criticità media può offrire un punto di partenza per le conversazioni iniziali.

<!-- -->

> [!TIP]
> Se si usa la [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud, i campi di gestione delle operazioni devono essere aggiornati per riflettere questi prerequisiti. Questi campi includono il _livello di impegno_, il contratto di _SLA composito_e il _costo mensile_. Il costo mensile dovrebbe rappresentare il costo degli strumenti di gestione operativi aggiunti su base mensile.

La linea di base di Operations Management funge da punto di partenza iniziale per la convalida in ognuna delle sezioni seguenti.

## <a name="management-responsibility"></a>Responsabilità di gestione

In un ambiente locale tradizionale, il costo della gestione dell'ambiente viene comunemente considerato un costo affondato di proprietà delle operazioni IT. Nel cloud, la gestione è una decisione intenzionale con un effetto preventivo diretto. I costi di ogni funzione di gestione possono essere attribuiti in modo più diretto a ogni carico di lavoro distribuito nel cloud. Questo approccio consente un maggiore controllo, ma crea un requisito per i team operativi cloud e i team di strategia cloud per il primo commit a un accordo sulle responsabilità.

Le organizzazioni potrebbero anche scegliere di [esternalizzare alcune delle funzioni di gestione in corso a un provider di servizi](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Questi provider di servizi possono usare [Azure Lighthouse](https://azure.com/lighthouse) per offrire alle organizzazioni un controllo più preciso sulla concessione dell'accesso alle risorse, oltre a una maggiore visibilità sulle azioni eseguite dai provider di servizi.

- **Responsabilità delegata:** Poiché non è necessario centralizzare e presupporre un sovraccarico della gestione operativa, le operazioni IT per molte organizzazioni stanno considerando i nuovi approcci. Un approccio comune viene definito _responsabilità delegata_. In un centro cloud del modello di eccellenza, le operazioni della piattaforma e l'automazione della piattaforma offrono strumenti di gestione self-service che possono essere usati dai team operativi aziendali, indipendentemente da un team operativo IT centrale. Questo approccio offre agli stakeholder aziendali il controllo completo sui budget correlati alla gestione. Consente inoltre al team di cloud Center of Excellence (CCOE) di garantire che un set minimo di Guardrails sia stato implementato correttamente. In questo modello, funge da broker e da una guida per aiutare le aziende a prendere decisioni sagge. Le operazioni aziendali supervisionano le operazioni quotidiane dei carichi di lavoro dipendenti.

- **Responsabilità centralizzata:** I requisiti di conformità, la complessità tecnica e alcuni modelli di servizi condivisi potrebbero richiedere un modello _it centrale_ . In questo modello continua a esercitare le proprie responsabilità di gestione delle operazioni. La progettazione ambientale, i controlli di gestione e gli strumenti di governance possono essere gestiti e controllati in modo centralizzato, limitando il ruolo di stakeholder aziendali nell'esecuzione di impegni di gestione. Tuttavia, la visibilità sul costo e sull'architettura degli approcci cloud rende molto più semplice per la comunicazione centralizzata il costo e il livello di gestione per ogni carico di lavoro.

- **Modello misto:** La classificazione è alla base di un _modello misto_ di responsabilità di gestione. Le aziende che si trovano in una trasformazione da locale a cloud possono richiedere un modello operativo locale per un periodo di tempo. Le aziende con requisiti di conformità severi o che dipendono da contratti a lungo termine con fornitori di outsourcing IT potrebbero richiedere un modello operativo centralizzato.

  Indipendentemente dai vincoli, le aziende odierne devono innovare. Quando una rapida innovazione deve prosperare, nel mezzo di un modello centralizzato di responsabilità centrale, un approccio con modello misto potrebbe garantire un equilibrio. Con questo approccio, Central IT fornisce un modello operativo centralizzato per tutti i carichi di lavoro cruciali o che contengono informazioni riservate. Allo stesso tempo, tutte le altre classificazioni del carico di lavoro possono essere inserite in un ambiente cloud progettato per le responsabilità delegate. L'approccio di responsabilità centralizzato funge da modello operativo generale. Il business ha quindi la flessibilità di adottare un modello operativo specializzato, in base al livello di supporto e alla sensibilità richiesti.

Il primo passaggio consiste nell'eseguire il commit di un approccio di responsabilità, che quindi definisce gli impegni seguenti.

**Quale organizzazione sarà responsabile per la gestione delle operazioni quotidiane per questo carico di lavoro?**

## <a name="cloud-tenancy"></a>Locazione cloud

Per la maggior parte delle aziende, la gestione è più semplice quando tutti gli asset si trovano in un singolo tenant. Tuttavia, alcune organizzazioni potrebbero dover gestire più tenant. Per informazioni sul motivo per cui un'azienda potrebbe richiedere un ambiente Azure multi-tenant, vedere [centralizzare le operazioni di gestione con il faro di Azure](../centralize-operations.md).

**Questo carico di lavoro si trova in un singolo tenant di Azure, insieme a tutti gli altri carichi di lavoro?**

## <a name="soft-cost-factors"></a>Fattori di costo soft

Nella sezione successiva viene illustrato un approccio ai ritorni comparati associati a livelli di processi di gestione e strumenti. Alla fine di questa sezione, ogni carico di lavoro analizzato misura il costo della gestione rispetto all'impatto delle attività di business. Questo approccio offre un modo relativamente semplice per comprendere se è garantito un investimento in approcci di gestione più completi.

Prima di eseguire i numeri, è importante esaminare i fattori di costo flessibile. I fattori di costo flessibile producono un risultato, ma tale risultato è difficile da misurare attraverso risparmi diretti a costi ridotti, che sarebbero visibili in un'istruzione profit-and-loss. I fattori di costo molle sono importanti perché possono indicare la necessità di investire in un livello di gestione più elevato rispetto a quelli fiscalmente prudenti.

Alcuni esempi di fattori di costo morbido includono:

- Utilizzo giornaliero del carico di lavoro da parte della lavagna o del CEO.
- Utilizzo del carico di lavoro di un'alta _percentuale_ di clienti che determina un maggiore effetto sui ricavi altrove.
- Effetti sulla soddisfazione dei dipendenti.

Il punto dati successivo necessario per eseguire un impegno è costituito da un elenco di fattori di costo flessibile. Questi fattori non devono essere documentati in questa fase, ma gli stakeholder aziendali devono essere consapevoli dell'importanza di questi fattori e della loro esclusione dai calcoli seguenti.

## <a name="calculate-loss-avoidance-roi"></a>Calcolare il ROI di evitare la perdita

Quando viene calcolato il ritorno relativo ai costi di gestione delle operazioni, il team IT responsabile delle operazioni cloud deve completare i prerequisiti indicati in precedenza e presupporre un livello minimo di gestione per tutti i carichi di lavoro.

Il prossimo impegno da effettuare è l'accettazione da parte dell'azienda dei costi associati all'offerta gestita da base.

**L'azienda accetta di investire nell'offerta di base per soddisfare gli standard minimi delle operazioni cloud?**

Se l'azienda non accetta questo livello di gestione, è necessario definire una soluzione che consenta all'azienda di procedere senza influire materialmente sulle operazioni cloud di altri carichi di lavoro.

Se l'azienda vuole un livello di gestione superiore rispetto a quello standard, il resto di questa sezione consentirà di convalidare l'investimento e i ritorni associati (sotto forma di prevenzione della perdita).

### <a name="increased-levels-of-management-design-principles-and-service-catalog"></a>Livelli di gestione più elevati: principi di progettazione e catalogo di servizi

Per le soluzioni gestite, oltre alla linea di base di gestione è possibile applicare diversi principi di progettazione e soluzioni di modello. Ognuno dei principi di progettazione per l'affidabilità e la resilienza aggiunge il costo operativo al carico di lavoro. Per fare in modo che l'IT e l'azienda accettino questi impegni aggiuntivi, è importante comprendere le potenziali perdite che possono essere evitate grazie a un aumento degli investimenti.

Nei calcoli seguenti verranno illustrate le formule che consentono di comprendere meglio le differenze tra le perdite e gli investimenti di gestione più elevati. Per informazioni sul calcolo del costo di una maggiore gestione, vedere [automazione del carico di lavoro](./workload.md) e automazione della [piattaforma](./platform.md).

> [!TIP]
> Se si usa la [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud, aggiornare i campi di gestione Ops in modo che riflettano ogni conversazione. Questi campi includono il _livello di impegno_, il contratto di _SLA composito_e il _costo mensile_. Il costo mensile dovrebbe rappresentare il costo mensile degli strumenti di gestione operativi aggiunti. Dopo l'aggiornamento, i campi aggiorneranno le formule ROI e ognuno dei campi seguenti.

### <a name="estimate-outage-hours-per-year"></a>Interruzione della stima (ore all'anno)

Il contratto di servizio composito è il contratto di servizio basato sulla distribuzione di ogni asset nel carico di lavoro. Tale campo determina l' _interruzione stimata_ (con etichetta _est. interruzione_ nella cartella di lavoro). Per calcolare le interruzioni stimate in ore all'anno senza utilizzare la cartella di lavoro, applicare la formula seguente:

> _Interruzioni stimate = (1-percentuale del &#215; contratto di servizio composto) numero di ore in un anno_

La cartella di lavoro usa il valore predefinito di _8.760 ore all'anno_.

### <a name="standard-loss-impact"></a>Effetti sulla perdita standard

L'effetto della _perdita standard_ (con l'indicazione dell' _effetto standard_ nella cartella di lavoro) prevede l'incidenza finanziaria di eventuali interruzioni, presupponendo che la _stima delle interruzioni stimate_ risulti accurata. Per calcolare questa previsione senza utilizzare la cartella di lavoro, applicare la formula seguente:

> _Effetto standard = interruzione stimata @ tre 9. &#215; tempo di inefficacia del valore_

Si tratta di una linea di base per i costi, qualora gli stakeholder aziendali scelgano di investire in un livello di gestione più elevato.

### <a name="composite-sla-impact"></a>Effetto del contratto di contratto composito

L'effetto del contratto di lavoro _composito_ (con l' _effetto del livello di impegno_ nella cartella di lavoro) fornisce un effetto fiscale aggiornato, in base alle modifiche apportate al contratto di esecuzione. Questo calcolo consente di confrontare l'effetto finanziario proiettato di entrambe le opzioni. Per calcolare questo effetto della previsione senza il foglio di calcolo, applicare la formula seguente:

> _Effetto contratto di servizio composito &#215; = tempo di interruzione stimato-effetto valore_

Il valore rappresenta le potenziali perdite che devono essere evitate dal livello di impegno modificato e dal nuovo contratto di Service composito.

### <a name="comparison-basis"></a>Base di confronto

La _base di confronto_ valuta l'effetto standard e l'effetto del contratto di contratto composito per determinare quale sia il più appropriato nella colonna restituita.

### <a name="return-on-loss-avoidance"></a>Return in merito alla perdita

Se il costo della gestione di un carico di lavoro supera le potenziali perdite, l'investimento proposto nella gestione cloud potrebbe non essere fruttuoso. Per confrontare il _ritorno in merito alla perdita_, vedere la colonna denominata _ROI annuale * *_ * *. Per calcolare la colonna in modo autonomo, utilizzare la formula seguente:

> _Ritorno in caso di mancata riduzione = (base di confronto- &#215; (costo mensile &#247; 12)) &#215; (costo mensile 12))_

A meno che non vi siano altri fattori di costo contenuto da considerare, questo confronto può suggerire rapidamente se è necessario un investimento più approfondito sulle operazioni cloud, sulla resilienza, sull'affidabilità o su altre aree.

## <a name="validate-the-commitment"></a>Convalidare l'impegno

A questo punto del processo, sono stati applicati gli impegni, ovvero responsabilità centralizzata o delegata, il tenant di Azure e il livello di impegno. Ogni impegno deve essere convalidato e documentato per garantire che il team operativo cloud, il team di strategia cloud e le parti interessate aziendali siano allineati a questo impegno per gestire il carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Una volta creati gli impegni, i team operativi responsabili possono iniziare a configurare il carico di lavoro in questione. Per iniziare, valutare i vari approcci per l' [inventario e la visibilità](./inventory.md).

> [!div class="nextstepaction"]
> [Opzioni di inventario e visibilità](./inventory.md)
