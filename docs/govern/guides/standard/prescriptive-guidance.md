---
title: 'Guida aziendale standard: Informazioni aggiuntive sulla descrizione'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle linee guida prescrittiva per la governance nelle aziende standard.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8f9bd9d7dadbd880265cc441b1e927ab835165cb
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223826"
---
# <a name="standard-enterprise-guide-prescriptive-guidance-explained"></a>Guida aziendale standard: Informazioni aggiuntive sulla descrizione

La guida alla governance inizia con un set di [criteri aziendali](./initial-corporate-policy.md)iniziali. Questi criteri vengono usati per stabilire un MVP di governance che riflette le [procedure consigliate](./index.md).

Questo articolo illustra le strategie di alto livello necessarie per creare un MVP per la governance. L'elemento centrale dell'MVP per la governance è la disciplina [Accelerazione della distribuzione](../../deployment-acceleration/index.md). Gli strumenti e i modelli applicati in questa fase consentiranno di migliorare i miglioramenti incrementali necessari per espandere la governance in futuro.

## <a name="governance-mvp-initial-governance-foundation"></a>MVP governance (iniziale governance Foundation)

Un'adozione rapida dei criteri di governance e aziendali è possibile, grazie ad alcuni semplici principi e a strumenti di governance basati sul cloud. Queste sono le prime tre discipline da affrontare nei processi di governance. Ogni disciplina verrà descritta più avanti in questo articolo.

Per iniziare, questo articolo illustra le strategie di alto livello alla base delle discipline Baseline di identità, Baseline di sicurezza e Accelerazione della distribuzione necessarie per creare un MVP per la governance, che verrà utilizzato come base per qualsiasi processo di adozione.

![Esempio di un MVP per la governance incrementale](../../../_images/govern/governance-mvp.png)

## <a name="implementation-process"></a>Processo di implementazione

L'implementazione dell'MVP per la governance dipende direttamente da identità, sicurezza e rete. Una volta risolte le dipendenze, il team di governance del cloud deciderà alcuni aspetti della governance. Le decisioni prese dal team di governance del cloud e dai team di supporto verranno implementate tramite un unico pacchetto di asset di applicazione.

![Esempio di un MVP per la governance incrementale](../../../_images/govern/governance-mvp-implementation-flow.png)

Questa implementazione può essere descritta anche usando un semplice elenco di controllo:

1. Sollecitare decisioni relative alle dipendenze principali: Identità, rete, monitoraggio e crittografia.
2. Determinare il modello da usare durante l'imposizione dei criteri aziendali.
3. Determinare i modelli di governance appropriati per la coerenza delle risorse, l'assegnazione di tag alle risorse e le discipline per la registrazione e la creazione di report.
4. Implementare gli strumenti di governance conformi al modello di imposizione dei criteri scelto per applicare decisioni dipendenti e di governance.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Applicazione di modelli di governance

Il team di governance del cloud è responsabile delle decisioni e delle implementazioni seguenti. Molti richiedono input da altri team, ma il team di governance del cloud è probabilmente proprietario sia della decisione che dell'implementazione. Le sezioni seguenti illustrano le decisioni prese per questo caso d'uso e i dettagli relativi a ogni decisione.

### <a name="subscription-design"></a>Progettazione della sottoscrizione

La decisione sulla progettazione di sottoscrizioni da usare determina il modo in cui le sottoscrizioni di Azure vengono strutturate e il modo in cui i gruppi di gestione di Azure verranno usati per gestire in modo efficiente l'accesso, i criteri e la conformità In questa descrizione, il team di governance ha scelto il modello di progettazione della sottoscrizione di [produzione e](../../../decision-guides/subscriptions/index.md#production-and-nonproduction-pattern) non di produzione.

- I reparti non sono necessari nello scenario corrente. Le distribuzioni devono essere vincolate all'interno di una singola unità di fatturazione. Nella fase di adozione, è possibile che non sia presente un contratto Enterprise sulla centralizzazione della fatturazione. È probabile che questo livello di adozione sia gestito da una singola sottoscrizione di Azure con pagamento a consumo.
- Indipendentemente dall'utilizzo del portale EA o dall'esistenza di un contratto Enterprise Agreement, è comunque necessario definire e concordare un modello di sottoscrizione per ridurre al minimo il superamento della fatturazione amministrativa.
- Nell'ambito della progettazione delle sottoscrizioni, è opportuno concordare una convenzione di denominazione comune in base ai due punti precedenti.

### <a name="resource-consistency"></a>Coerenza delle risorse

Le decisioni relative alla coerenza delle risorse determinano gli strumenti, i processi e gli sforzi necessari per garantire la distribuzione, la configurazione e la gestione delle risorse di Azure in una sottoscrizione. In questa descrizione, la **[coerenza della distribuzione](../../../decision-guides/resource-consistency/index.md#deployment-consistency)** è stata scelta come modello di coerenza delle risorse primario.

- I gruppi di risorse vengono creati per le applicazioni che usano l'approccio del ciclo di vita: tutto ciò che viene creato, mantenuto e ritirato insieme dovrebbe risiedere in un singolo gruppo di risorse. Per ulteriori informazioni sui gruppi di risorse, vedere [qui](../../../decision-guides/resource-consistency/index.md#basic-grouping).
- A tutte le sottoscrizioni nel gruppo di gestione associato è necessario applicare Criteri di Azure.
- Come parte del processo di distribuzione, i modelli di coerenza delle risorse di Azure per tutti i gruppi di risorse devono essere archiviati nel controllo del codice sorgente.
- Ogni gruppo di risorse è associato a un carico di lavoro specifico o a un'applicazione basata sull'approccio del ciclo di vita descritto in precedenza.
- I gruppi di gestione di Azure consentono l'aggiornamento delle progettazioni di governance man mano che maturano i criteri aziendali.
- Un'implementazione estesa di Criteri di Azure può richiedere al team più tempo del previsto e non offrire particolari vantaggi a questo punto. È tuttavia opportuno creare e applicare semplici criteri predefiniti per imporre le poche definizioni dei criteri di governance del cloud. Questi criteri consentono di definire l'implementazione di requisiti di governance specifici che può quindi essere applicata a tutti gli asset distribuiti.

>[!IMPORTANT]
>Ogni volta che una risorsa in un gruppo di risorse non condivide più lo stesso ciclo di vita, deve essere spostata in un altro gruppo di risorse. Tra gli esempi sono inclusi i database comuni e i componenti di rete. Sebbene possano gestire l'applicazione in fase di sviluppo, possono anche essere utilizzati per altri scopi e devono pertanto esistere in altri gruppi di risorse.

### <a name="resource-tagging"></a>Tag delle risorse

Le decisioni relative ai tag delle risorse determinano il modo in cui i metadati vengono applicati alle risorse di Azure all'interno di una sottoscrizione per supportare operazioni, gestione e contabilità. In questa descrizione, il modello di **[classificazione](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns)** è stato scelto come modello predefinito per l'assegnazione di tag delle risorse.

- Gli asset distribuiti devono essere contrassegnati con:
  - Classificazione dei dati
  - Criticità
  - Contratto di servizio
  - Ambiente
- Questi quattro valori sono alla base delle decisioni relative a governance, operazioni e sicurezza.
- Se questa guida alla governance è implementata per una business unit o un team all'interno di un'azienda di grandi dimensioni, l'assegnazione di tag deve includere anche i metadati per l'unità di fatturazione.

### <a name="logging-and-reporting"></a>Registrazione e creazione di report

La registrazione e la creazione di report determinano il modo in cui i dati di log del negozio e il modo in cui gli strumenti di monitoraggio e creazione di report sono informati sullo stato operativo. In questa descrizione viene suggerito un [modello nativo del cloud](../../../decision-guides/logging-and-reporting/index.md#cloud-native)* * per la registrazione e la creazione di report.

## <a name="incremental-improvement-of-governance-processes"></a>Miglioramento incrementale dei processi di governance

Con la modifica della governance, alcune istruzioni dei criteri non possono o non devono essere controllate dagli strumenti automatici. Altri criteri comporteranno l'intervento del team responsabile della sicurezza IT e del team di gestione dell'identità locale. Per gestire i nuovi rischi man mano che si verificano, il team di governance del cloud sorveglierà i processi seguenti.

**Accelerazione adozione:** Il team di governance del cloud sta esaminando gli script di distribuzione tra più team. Ha mantenuto un set di script da utilizzare come modelli di distribuzione. Tali modelli vengono usati dai team di adozione del cloud e dai team di DevOps per definire più rapidamente le distribuzioni. Ognuno di questi script contiene i requisiti necessari per applicare un set di criteri di governance senza sforzi aggiuntivi da parte dei tecnici di adozione del cloud. Come curatori di questi script, il team di governance del cloud può implementare più rapidamente le modifiche ai criteri. In seguito alla cura degli script, il team di governance del cloud viene considerato come fonte di accelerazione dell'adozione. Ciò consente di ottenere coerenza tra le distribuzioni, senza necessariamente imporre la conformità.

**Formazione per ingegneri:** Il team di governance del cloud offre sessioni di formazione bisettimanali e ha creato due video per i tecnici. Questi materiali consentono ai tecnici di implementare più velocemente la cultura della governance e la modalità di esecuzione delle attività di distribuzione. Il team sta aggiungendo risorse di formazione che mostrano la differenza tra le distribuzioni di produzione e non di produzione, in modo che i tecnici siano in grado di comprendere in che modo i nuovi criteri avranno effetto sull'adozione. Ciò consente di ottenere coerenza tra le distribuzioni, senza necessariamente imporre la conformità.

**Pianificazione della distribuzione:** Prima di distribuire gli asset contenenti dati protetti, il team di governance del Cloud esamina gli script di distribuzione per convalidare l'allineamento della governance. I team esistenti con le distribuzioni approvate in precedenza verranno controllati tramite strumenti automatici.

**Controllo mensile e creazione di report:** Ogni mese, il team di governance del cloud esegue un controllo di tutte le distribuzioni cloud per convalidare l'allineamento continuo ai criteri. Eventuali deviazioni individuate vengono documentate e condivise con i team di adozione del cloud. Quando non si rischia un'interruzione dell'attività o una perdita dei dati, i criteri vengono imposti automaticamente. Al termine del controllo, il team di governance del cloud compila un report per il team strategico Cloud e ogni team di adozione del cloud per comunicare la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

**Revisione trimestrale dei criteri:** Ogni trimestre, il team di governance del cloud e il team di strategia cloud esaminano i risultati del controllo e suggeriscono le modifiche ai criteri aziendali. Molti di questi suggerimenti sono il risultato di strategie di miglioramento costanti e dell'osservazione dei modelli di utilizzo. Le modifiche ai criteri approvate vengono integrate negli strumenti di governance durante i cicli di controllo successivi.

## <a name="alternative-patterns"></a>Modelli alternativi

Se uno qualsiasi dei modelli selezionati in questa guida alla governance non è allineato ai requisiti del lettore, sono disponibili alternative a ogni modello:

- [Modelli di crittografia](../../../decision-guides/encryption/index.md)
- [Modelli di identità](../../../decision-guides/identity/index.md)
- [Modelli di registrazione e creazione di report](../../../decision-guides/logging-and-reporting/index.md)
- [Modelli di imposizione dei criteri](../../../decision-guides/policy-enforcement/index.md)
- [Modelli di coerenza delle risorse](../../../decision-guides/resource-consistency/index.md)
- [Modelli di assegnazione di tag alle risorse](../../../decision-guides/resource-tagging/index.md)
- [Modelli di Software Defined Networking](../../../decision-guides/software-defined-network/index.md)
- [Modelli di progettazione delle sottoscrizioni](../../../decision-guides/subscriptions/index.md)

## <a name="next-steps"></a>Passaggi successivi

Dopo aver implementato queste linee guida, ogni team di adozione del cloud può contare su una solida base di conoscenze relative alla governance. Allo stesso tempo, il team di governance del cloud si impegna a aggiornare continuamente i criteri aziendali e le discipline di governance.

I due team utilizzeranno gli indicatori di tolleranza per identificare il set successivo di miglioramenti necessari per continuare a supportare l'adozione del cloud. Per la società fittizia in questa guida, il passaggio successivo consiste nel migliorare la linea di base di sicurezza per supportare lo stato di trasferimento dei dati protetti nel cloud.

> [!div class="nextstepaction"]
> [Migliorare la disciplina della linea di base di sicurezza](./security-baseline-improvement.md)
