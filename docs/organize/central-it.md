---
title: Funzionalità IT centrali
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla formazione delle funzionalità IT centrali.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: d1d59b105dd6d75b0c5b5ed12d711473fd4995c8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549109"
---
# <a name="central-it-capabilities"></a>Funzionalità IT centrali

Poiché l'adozione del cloud si ridimensiona, le funzionalità di governance del cloud possono non essere sufficienti per gestire le attività di adozione. Quando l'adozione è graduale, i team tendono a sviluppare in modo organico le competenze e i processi necessari per il cloud nel tempo.

Tuttavia, quando un team di adozione del cloud sfrutta il cloud per ottenere un risultato aziendale ad alto profilo, l'adozione graduale si verifica raramente. Esito positivo. Questo vale anche per l'adozione del cloud, ma si verifica a livello di cloud. Quando l'adozione del cloud si espande da un team a più team in modo relativamente rapido, è necessario ulteriore supporto del personale IT esistente. Tuttavia, i membri del personale potrebbero non avere il training e l'esperienza necessari per supportare il cloud usando gli strumenti IT nativi del cloud. Questa guida spesso determina la formazione di un team IT centrale che controlla il cloud.

> [!CAUTION]
> Sebbene si tratta di un passaggio di maturità comune, può presentare un elevato rischio di adozione, bloccando potenzialmente l'innovazione e le attività di migrazione se non vengono gestite in modo efficace. Vedere la sezione dei rischi riportata di seguito per informazioni su come mitigare il rischio di centralizzazione che diventa un antipattern culturale.

## <a name="possible-sources-for-central-it-expertise"></a>Possibili origini per competenze IT centrali

Le competenze necessarie per fornire funzionalità IT centralizzate potrebbero essere fornite da:

- Un team IT centrale esistente
- Enterprise Architects
- Operazioni IT
- Governance IT
- Infrastruttura IT
- Rete
- Identità
- Virtualizzazione
- Continuità aziendale e ripristino di emergenza
- Proprietari di applicazioni al suo interno

> [!WARNING]
> Central IT deve essere applicato solo nel cloud quando il recapito esistente in locale si basa su un modello IT centrale. Se il modello locale corrente è basato sul controllo delegato, considerare un approccio CCoE (cloud Center of Excellence) per un'alternativa più compatibile.

## <a name="key-responsibilities"></a>Responsabilità principali

Adatta le procedure IT esistenti per garantire che le attività di adozione provochino ambienti ben gestiti e ben gestiti nel cloud.

Le attività seguenti vengono in genere eseguite regolarmente:

### <a name="strategic-tasks"></a>Attività strategiche

- Recensione
  - [risultati aziendali](../strategy/business-outcomes/index.md)
  - [modelli finanziari](../strategy/financial-models.md)
  - [motivazioni per l'adozione del cloud](../strategy/motivations.md)
  - [rischi aziendali](../govern/policy-compliance/risk-tolerance.md)
  - [razionalizzazione delle proprietà digitali](../digital-estate/index.md)
- Monitorare i piani di adozione e lo stato di avanzamento rispetto al [backlog della migrazione con priorità](../migrate/migration-considerations/assess/release-iteration-backlog.md).
- Identificare e classificare in ordine di priorità le modifiche della piattaforma necessarie per supportare il backlog di migrazione.
- Agire come un livello intermedio o di conversione tra le esigenze di adozione del cloud e i team IT esistenti.
- Sfrutta i team IT esistenti per accelerare le funzionalità della piattaforma e abilitare l'adozione.

### <a name="technical-tasks"></a>Attività tecniche

- Crea e Gestisci la piattaforma cloud per supportare le soluzioni.
- Definire e implementare l'architettura della piattaforma.
- Gestisci e Gestisci la piattaforma cloud.
- Migliorare costantemente la piattaforma.
- Continua a usare nuove innovazioni nella piattaforma cloud.
- Offri nuove funzionalità cloud per supportare la creazione di valori aziendali.
- Suggerisci soluzioni self-service.
- Assicurarsi che le soluzioni soddisfino i requisiti di governance e conformità esistenti.
- Creare e convalidare la distribuzione dell'architettura della piattaforma.
- Esaminare i piani di rilascio per le origini dei nuovi requisiti della piattaforma.

## <a name="meeting-cadence"></a>Cadenza riunione

Le competenze IT centrali provengono in genere da un team funzionante. Si prevede che i partecipanti commettano la maggior parte delle pianificazioni quotidiane per il lavoro di allineamento. I contributi non sono limitati alle riunioni e ai cicli di feedback.

## <a name="central-it-risks"></a>Rischi IT centrali

Ognuna delle funzionalità e delle fasi del cloud di maturità organizzativa è preceduta dalla parola "cloud". Central è l'unica eccezione. Si tratta di una situazione essenziale quando tutti gli asset IT possono essere ospitati in poche località, gestiti da un numero ridotto di team e controllati tramite una singola piattaforma di gestione delle operazioni. Le procedure aziendali globali e l'economia digitale hanno notevolmente ridotto le istanze di questi ambienti gestiti centralmente.

Nella visualizzazione moderna, le risorse vengono distribuite a livello globale. Le responsabilità sono delegate. Operations Management viene fornito da una combinazione di personale interno, provider di servizi gestiti e provider di servizi cloud. Nell'economia digitale, le procedure di gestione IT stanno passando a un modello di controllo self-service e delegato con Guardrails Clear per applicare la governance. Central IT può essere un prezioso collaboratore all'adozione del cloud diventando un broker cloud e un partner per l'innovazione e la flessibilità aziendale.

La Central IT come funzione è ben posizionata in modo da avere una conoscenza e procedure utili dei modelli locali esistenti e applicare tali procedure al recapito cloud. Tuttavia, questo processo richiederà modifiche. Nuovi processi, nuove competenze e nuovi strumenti sono necessari per supportare l'adozione del cloud su larga scala. Quando l'IT centrale si adatta, diventa un importante partner per le attività di adozione del cloud. Tuttavia, se la centralità non si adatta al cloud o tenta di usare il cloud come catalizzatore per i controlli strettamente granulari, l'IT centrale diventa rapidamente un blocco per l'adozione, l'innovazione e la migrazione.

Le misure di questo rischio sono velocità e flessibilità. Il Cloud semplifica l'adozione rapida di nuove tecnologie. Quando è possibile distribuire nuove funzionalità cloud in pochi minuti, ma le revisioni centrali IT aggiungono settimane o mesi al processo di distribuzione, questi processi centralizzati diventano un ostacolo fondamentale per il successo aziendale. Quando viene rilevato questo indicatore, prendere in considerazione strategie alternative per il recapito IT.

### <a name="exceptions"></a>Eccezioni

Molti settori richiedono una rigida aderenza alla conformità di terze parti. Alcuni requisiti di conformità richiedono anche un controllo IT centralizzato. Il recapito di queste misure di conformità può aggiungere tempi ai processi di distribuzione, specialmente per le nuove tecnologie che non sono state usate in modo esteso. In questi scenari, prevedere ritardi nella distribuzione durante le fasi iniziali dell'adozione. Situazioni analoghe sono disponibili per le aziende che gestiscono dati sensibili dei clienti, ma che potrebbero non essere soggette a requisiti di conformità di terze parti.

### <a name="operating-within-the-exceptions"></a>Funzionamento all'interno delle eccezioni

Quando sono necessari processi IT centralizzati e questi processi creano Checkpoint appropriati nell'adozione di nuove tecnologie, questi Checkpoint di innovazione possono comunque essere risolti rapidamente. I requisiti di governance e conformità sono progettati per proteggere gli elementi sensibili, non per proteggere tutto. Il cloud offre semplici meccanismi per l'acquisizione e la distribuzione di risorse isolate, mantenendo al tempo stesso Guardrails appropriati.

Un team IT centrale maturo mantiene le protezioni necessarie, ma negozia le procedure che ancora consentono l'innovazione. La dimostrazione di questo livello di maturità dipende dalla classificazione e dall'isolamento appropriati delle risorse.

### <a name="example-narrative-of-operating-within-exceptions-to-empower-adoption"></a>Descrizione di esempio del funzionamento all'interno delle eccezioni per consentire l'adozione

Questo racconto di esempio illustra l'approccio adottato da un team IT centrale maturo per potenziare l'adozione.

Contoso, LLC ha adottato un modello IT centrale per il supporto delle risorse cloud aziendali. Per distribuire questo modello, hanno implementato controlli rigidi per vari servizi condivisi, ad esempio connessioni di rete in ingresso. Questa saggia azione consente di ridurre l'esposizione dell'ambiente cloud e di fornire un singolo dispositivo "Break-Glass" per bloccare tutto il traffico in caso di violazione. I criteri di base di sicurezza specificano che tutto il traffico in ingresso deve passare attraverso un dispositivo condiviso gestito dal team IT centrale.

Tuttavia, uno dei team di adozione del cloud ora richiede un ambiente con una connessione di rete in ingresso dedicata e appositamente configurata per sfruttare una tecnologia cloud specifica. Un team IT centrale non maturo può semplicemente rifiutare la richiesta e classificare in ordine di priorità i processi esistenti rispetto alle esigenze di adozione. Il team IT centrale di Contoso è diverso. Hanno rapidamente identificato una semplice soluzione in quattro parti per questo dilemma: classificazione, negoziazione, isolamento e automazione.

**Classificazione:** Poiché il team di adozione del cloud era nelle prime fasi della creazione di una nuova soluzione e non aveva dati sensibili o esigenze di supporto cruciale, le risorse nell'ambiente venivano classificate come a basso rischio e non critiche. Una classificazione efficace è un segno di maturità nell'IT centrale. La classificazione di tutti gli asset e gli ambienti consente di definire criteri più chiari.

**Negoziazione:** Solo la classificazione non è sufficiente. I servizi condivisi sono stati implementati per operare in modo coerente con asset sensibili e cruciali. La modifica delle regole comprometterebbe i criteri di governance e conformità progettati per gli asset che necessitano di una maggiore protezione. Il potenziamento dell'adozione non può avvenire a scapito della stabilità, della sicurezza o della governance. Ciò ha portato a una negoziazione con il team di adozione per rispondere a domande specifiche. Un team di DevOps guidato dall'azienda può fornire la gestione delle operazioni per questo ambiente? Questa soluzione richiede l'accesso diretto ad altre risorse interne? Se il team di adozione del cloud ha dimestichezza con questi compromessi, il traffico in ingresso potrebbe essere possibile.

**Isolamento:** Poiché l'azienda può fornire la propria gestione operativa in corso e poiché la soluzione non si basa sul traffico diretto ad altre risorse interne, può essere isolata in una nuova sottoscrizione. Tale sottoscrizione viene inoltre aggiunta a un nodo separato della nuova gerarchia del gruppo di gestione.

**Automazione:** Un altro segno di maturità in questo team è costituito dai principi di automazione. Il team USA criteri di Azure per automatizzare l'applicazione dei criteri. Usano anche i progetti di Azure per automatizzare la distribuzione di componenti della piattaforma comuni e applicare la conformità alla baseline di identità definita. Per questa sottoscrizione e per gli altri utenti del nuovo gruppo di gestione, i criteri e i modelli sono leggermente diversi. I criteri che bloccano la larghezza di banda in ingresso sono stati rimossi. Sono stati sostituiti dai requisiti per instradare il traffico attraverso la sottoscrizione ai servizi condivisi, ad esempio il traffico in ingresso, per applicare l'isolamento del traffico. Poiché gli strumenti di gestione delle operazioni locali non possono accedere a questa sottoscrizione, gli agenti per tale strumento non sono più necessari. Tutti gli altri Guardrails di governance richiesti da altre sottoscrizioni nella gerarchia del gruppo di gestione vengono ancora applicati, garantendo un numero sufficiente di Guardrails.

L'approccio creativo maturo del team IT centrale di Contoso ha fornito una soluzione che non ha compromesso la governance o la conformità, ma è stata comunque incoraggiata l'adozione. Questo approccio di Service Broker anziché possedere approcci nativi del cloud a centralizzato è il primo passo verso la creazione di un vero centro cloud di eccellenza (CCoE). L'adozione di questo approccio per l'evoluzione rapida dei criteri esistenti consentirà il controllo centralizzato quando necessario e Guardrails di governance quando sarà accettabile una maggiore flessibilità. Il bilanciamento di queste due considerazioni attenua i rischi associati alla centrale IT nel cloud.

## <a name="next-steps"></a>Passaggi successivi

Poiché l'IT centrale matura nel cloud, il passaggio successivo della maturità è in genere più flessibile per le [operazioni cloud](./cloud-operations.md). La disponibilità degli strumenti per la gestione delle operazioni native del cloud e i costi operativi inferiori per le soluzioni PaaS-First spesso portano i team aziendali (o, più specificamente, i team DevOps all'interno dell'azienda), presumendo la responsabilità delle operazioni cloud.

> [!div class="nextstepaction"]
> [Funzionalità per le operazioni cloud](./cloud-operations.md)
