---
title: 'Guida alla governance per le aziende complesse: Informazioni aggiuntive sulla descrizione'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle linee guida prescrittiva per la governance in aziende complesse.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ac099f89fe68d33ae5272e19ff97587a833c9002
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908956"
---
# <a name="governance-guide-for-complex-enterprises-prescriptive-guidance-explained"></a>Guida alla governance per le aziende complesse: Informazioni aggiuntive sulla descrizione

La guida alla governance inizia con un set di [criteri aziendali](./initial-corporate-policy.md)iniziali. Questi criteri vengono usati per stabilire un prodotto minimo funzionante (MVP, Minimum Viable Product) per la governance che sia conforme alle [procedure consigliate](./index.md).

Questo articolo illustra le strategie di alto livello necessarie per creare un MVP per la governance. L'elemento centrale dell'MVP per la governance è la disciplina [Accelerazione della distribuzione](../../deployment-acceleration/index.md). Gli strumenti e i modelli applicati in questa fase consentiranno di migliorare i miglioramenti incrementali necessari per espandere la governance in futuro.

## <a name="governance-mvp-initial-governance-foundation"></a>MVP governance (iniziale governance Foundation)

Un'adozione rapida dei criteri di governance e aziendali è possibile, grazie ad alcuni semplici principi e a strumenti di governance basati sul cloud. Di seguito sono descritte le prime tre discipline a cui fare riferimento in qualsiasi processo di governance. Ogni disciplina verrà illustrata più avanti in questo articolo.

Per iniziare, questo articolo illustra le strategie di alto livello alla base delle discipline Baseline di identità, Baseline di sicurezza e Accelerazione della distribuzione necessarie per creare un MVP per la governance, che verrà utilizzato come base per qualsiasi processo di adozione.

![Esempio di un MVP per la governance incrementale](../../../_images/governance/governance-mvp.png)

## <a name="implementation-process"></a>Processo di implementazione

L'implementazione dell'MVP per la governance dipende direttamente da identità, sicurezza e rete. Una volta risolte le dipendenze, il team di governance del cloud deciderà alcuni aspetti della governance. Le decisioni prese dal team di governance del cloud e dai team di supporto verranno implementate tramite un unico pacchetto di asset di applicazione.

![Esempio di un MVP per la governance incrementale](../../../_images/governance/governance-mvp-implementation-flow.png)

Questa implementazione può essere descritta anche usando un semplice elenco di controllo:

1. Sollecitare decisioni relative alle dipendenze principali: identità, rete e crittografia.
1. Determinare il modello da usare durante l'imposizione dei criteri aziendali.
1. Determinare i modelli di governance appropriati per la coerenza delle risorse, l'assegnazione di tag alle risorse e le discipline per la registrazione e la creazione di report.
1. Implementare gli strumenti di governance conformi al modello di imposizione dei criteri scelto per applicare decisioni dipendenti e di governance.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Applicazione di modelli di governance

Il team di governance del cloud sarà responsabile delle decisioni e delle implementazioni seguenti. Molti richiedono input di altri team, ma il team di governance del cloud è probabilmente proprietario sia della decisione che dell'implementazione. Le sezioni seguenti illustrano le decisioni prese per questo caso d'uso e i dettagli relativi a ogni decisione.

### <a name="subscription-design"></a>Progettazione della sottoscrizione

La decisione sulla progettazione di sottoscrizioni da usare determina il modo in cui le sottoscrizioni di Azure vengono strutturate e il modo in cui i gruppi di gestione di Azure verranno usati per gestire in modo efficiente l'accesso, i criteri e la conformità In questo racconto, il team di governance ha scelto il modello di progettazione **[misto](../../../decision-guides/subscriptions/index.md#mixed-patterns)** di sottoscrizione.

- Quando si presentano nuove richieste per le risorse di Azure, è consigliabile stabilire un "reparto" per ogni unità aziendale principale in ogni area geografica operativa. All'interno di ciascun reparto, devono essere create "sottoscrizioni" per ogni archetipo di applicazione.
- Un archetipo di applicazione consente di raggruppare le applicazioni con esigenze simili. Ecco alcuni esempi comuni: Applicazioni con dati protetti, applicazioni regolate (ad esempio HIPAA o FedRAMP), applicazioni a basso rischio, applicazioni con dipendenze locali, SAP o altre applicazioni mainframe in Azure o applicazioni che estendono SAP o mainframe locale applicazioni. Ogni organizzazione ha esigenze specifiche che dipendono dalla classificazione dei dati e dai tipi di applicazioni che supportano le attività aziendali. Il mapping delle dipendenze del patrimonio digitale consente di definire gli archetipi di applicazione in un'organizzazione.
- Nell'ambito della progettazione delle sottoscrizioni, è opportuno concordare una convenzione di denominazione comune in base ai due punti precedenti dell'elenco.

### <a name="resource-consistency"></a>Coerenza delle risorse

Le decisioni relative alla coerenza delle risorse determinano gli strumenti, i processi e gli sforzi necessari per garantire la distribuzione, la configurazione e la gestione delle risorse di Azure in una sottoscrizione. In questa descrizione, è stata scelta la **[coerenza gerarchica](../../../decision-guides/resource-consistency/index.md#hierarchical-consistency)** come modello di coerenza delle risorse primario.

- Per ogni applicazione è necessario creare gruppi di risorse. Per ogni archetipo di applicazione è necessario creare gruppi di gestione. A tutte le sottoscrizioni nel gruppo di gestione associato è necessario applicare Criteri di Azure.
- Come parte del processo di distribuzione, i modelli di coerenza delle risorse per tutti gli asset devono essere archiviati nel controllo del codice sorgente.
- Ogni gruppo di risorse deve essere allineato a un'applicazione o a un carico di lavoro specifico.
- La gerarchia dei gruppi di gestione di Azure definita deve rappresentare la responsabilità di fatturazione e la proprietà delle applicazioni in base a gruppi nidificati.
- Un'implementazione estesa di Criteri di Azure può richiedere al team più tempo del previsto e non offrire particolare valore a questo punto. È tuttavia opportuno creare e applicare semplici criteri predefiniti per imporre le prime definizioni dei criteri di governance del cloud. Ciò consente di definire l'implementazione di requisiti di governance specifici che può quindi essere applicata a tutti gli asset distribuiti.

### <a name="resource-tagging"></a>Tag delle risorse

Le decisioni relative ai tag delle risorse determinano il modo in cui i metadati vengono applicati alle risorse di Azure all'interno di una sottoscrizione per supportare operazioni, gestione e contabilità. In questa descrizione, il modello di **[Contabilità](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns)** è stato scelto come modello predefinito per l'assegnazione di tag delle risorse.

- Gli asset distribuiti devono essere contrassegnati con i valori per:
  - Reparto/unità di fatturazione
  - Geografia
  - Classificazione dei dati
  - Criticità
  - Contratto di servizio
  - Ambiente
  - Archetipo dell'applicazione
  - Applicazione
  - Proprietario dell'applicazione
- Questi valori, insieme al gruppo di gestione e alla sottoscrizione di Azure associati a un asset distribuito, saranno alla base delle decisioni relative a governance, operazioni e sicurezza.

### <a name="logging-and-reporting"></a>Registrazione e creazione di report

La registrazione e la creazione di report determinano il modo in cui i dati di log del negozio e il modo in cui gli strumenti di monitoraggio e creazione di report sono informati sullo stato operativo. In questo argomento viene suggerito un modello di **[monitoraggio ibrido](../../../decision-guides/log-and-report/index.md)** per la registrazione e la creazione di report, ma non è richiesto alcun team di sviluppo.

- Attualmente non sono stati definiti requisiti di governance relativi a punti dati specifici da raccogliere per la registrazione o la creazione di report. Questo aspetto è specifico di questo scenario fittizio e deve essere considerato un antimodello. Gli standard di registrazione devono essere determinati e applicati appena possibile.
- È necessario eseguire altre analisi prima del rilascio di eventuali dati protetti o carichi di lavoro cruciali.
- Prima di supportare i dati protetti o i carichi di lavoro di importanza critica, è necessario concedere l'accesso all'area di lavoro usata per la registrazione alla soluzione di monitoraggio operativo locale esistente. Le applicazioni devono soddisfare i requisiti di sicurezza e registrazione associati all'uso del tenant, se l'applicazione deve essere supportata con un contratto di servizio definito.

## <a name="incremental-of-governance-processes"></a>Incrementale dei processi di governance

Alcune delle definizioni dei criteri non possono o non devono essere controllate da strumenti automatizzati. Altri criteri richiederanno un impegno periodico da parte dei team responsabili della sicurezza IT e della baseline di identità locale. Il team di governance del cloud dovrà sorvegliare i processi seguenti per implementare le ultime otto istruzioni dei criteri:

**Modifiche ai criteri aziendali:** Il team di governance del cloud apporterà modifiche alla progettazione MVP della governance per adottare i nuovi criteri. L'MVP per la governance consentirà l'imposizione automatica dei nuovi criteri.

**Accelerazione adozione:** Il team di governance del cloud sta esaminando gli script di distribuzione tra più team. Ha mantenuto un set di script da utilizzare come modelli di distribuzione. Tali modelli possono essere usati dai team di adozione del cloud e dai team di DevOps per definire più rapidamente le distribuzioni. Ogni script contiene i requisiti per l'applicazione dei criteri di governance e non richiede alcun impegno aggiuntivo da parte dei tecnici di adozione del cloud. Come responsabili di questi script, possono implementare più rapidamente le modifiche dei criteri. Possono anche essere considerati come acceleratori del processo di adozione. Ciò garantisce distribuzioni coerenti senza un'imposizione rigorosa della conformità.

**Formazione per ingegneri:** Il team di governance del cloud offre sessioni di formazione bisettimanali e ha creato due video per i tecnici. Entrambe le risorse sono utili ai tecnici per implementare più velocemente la cultura della governance e la modalità di esecuzione delle distribuzioni. Il team sta aggiungendo risorse di formazione per dimostrare la differenza tra le distribuzioni di produzione e non di produzione, che aiutano gli ingegneri a comprendere il modo in cui i nuovi criteri influiscono sull'adozione. Ciò garantisce distribuzioni coerenti senza un'imposizione rigorosa della conformità.

**Pianificazione della distribuzione:** Prima di distribuire gli asset contenenti dati protetti, il team di governance del cloud sarà responsabile della revisione degli script di distribuzione per convalidare l'allineamento della governance. I team esistenti con le distribuzioni approvate in precedenza verranno controllati tramite strumenti automatici.

**Controllo mensile e creazione di report:** Ogni mese, il team di governance del cloud esegue un controllo di tutte le distribuzioni cloud per convalidare l'allineamento continuo ai criteri. Eventuali deviazioni individuate vengono documentate e condivise con i team di adozione del cloud. Quando non si rischia un'interruzione dell'attività o una perdita dei dati, i criteri vengono imposti automaticamente. Al termine del controllo, il team di governance del cloud compila un report per il team strategico Cloud e ogni team di adozione del cloud per comunicare la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

**Revisione trimestrale dei criteri:** Ogni trimestre, il team di governance del cloud e il team di strategia cloud per esaminare i risultati del controllo e suggerire le modifiche ai criteri aziendali. Molti di questi suggerimenti sono il risultato di strategie di miglioramento costanti e dell'osservazione dei modelli di utilizzo. Le modifiche ai criteri approvate vengono integrate negli strumenti di governance durante i cicli di controllo successivi.

## <a name="alternative-patterns"></a>Modelli alternativi

Se uno qualsiasi dei modelli scelti in questa guida alla governance non è allineato ai requisiti del lettore, sono disponibili alternative a ogni modello:

- [Modelli di crittografia](../../../decision-guides/encryption/index.md)
- [Modelli di identità](../../../decision-guides/identity/index.md)
- [Modelli di registrazione e creazione di report](../../../decision-guides/log-and-report/index.md)
- [Modelli di imposizione dei criteri](../../../decision-guides/policy-enforcement/index.md)
- [Modelli di coerenza delle risorse](../../../decision-guides/resource-consistency/index.md)
- [Modelli di assegnazione di tag alle risorse](../../../decision-guides/resource-tagging/index.md)
- [Modelli di Software Defined Networking](../../../decision-guides/software-defined-network/index.md)
- [Modelli di progettazione delle sottoscrizioni](../../../decision-guides/subscriptions/index.md)

## <a name="next-steps"></a>Passaggi successivi

Dopo aver implementato queste linee guida, ogni team di adozione del cloud può contare su una solida base di conoscenze relative alla governance. Il team di governance del cloud collaborerà in parallelo per aggiornare continuamente i criteri aziendali e le discipline di governance.

Entrambi i team utilizzeranno gli indicatori di tolleranza per identificare il set successivo di miglioramenti necessari per continuare a supportare l'adozione del cloud. Il passaggio successivo per questa società è il miglioramento incrementale della linea di base di governance per supportare le applicazioni con requisiti di autenticazione a più fattori legacy o di terze parti.

> [!div class="nextstepaction"]
> [Migliorare la disciplina della linea di base di identità](./identity-baseline-evolution.md)
