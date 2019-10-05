---
title: Tenere traccia dei costi tra business unit, ambienti o progetti
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Rilevamento dei costi tra business unit, ambienti o progetti
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 67313af2166fbd8dab0f66abb8c6477079a049ad
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967747"
---
# <a name="track-costs-across-business-units-environments-or-projects"></a>Tenere traccia dei costi tra business unit, ambienti o progetti

[La creazione di un'organizzazione attenta ai costi](../../organize/cost-conscious-organization.md) richiede visibilità e un accesso (o ambito) definito correttamente per quanto riguarda i dati relativi ai costi. Questo articolo sulle procedure consigliate illustra gli approcci decisionali e di implementazione per la creazione di meccanismi di rilevamento.

![Struttura dei processi attenti ai costi](../../_images/ready/cost-optimization-process.png)

## <a name="establish-a-well-managed-environment-hierarchy"></a>Definire la gerarchia di un ambiente gestito correttamente

Il controllo dei costi, in modo molto simile alla governance e ad altri costrutti di gestione, dipende dalla corretta gestione dell'ambiente. La definizione di un ambiente di questo tipo, in particolare di uno complesso, richiede processi coerenti nella classificazione e nell'organizzazione di tutti gli asset.

Gli asset (noti anche come risorse) includono tutte le macchine virtuali, le origini dati e le applicazioni distribuite nel cloud. Azure offre diversi meccanismi per la classificazione e l'organizzazione degli asset. L'articolo [Ridimensionamento con più sottoscrizioni di Azure](../considerations/scaling-subscriptions.md) descrive in dettaglio le opzioni per organizzare le risorse in base a più criteri, stabilendo così un ambiente gestito correttamente. Questo articolo illustra l'applicazione di concetti fondamentali di Azure per fornire visibilità sui costi del cloud.

### <a name="classification"></a>classificazione

*L'assegnazione di tag* è un modo semplice per classificare gli asset. L'assegnazione di tag associa metadati a un asset. Tali metadati possono essere usati per classificare l'asset in base a vari punti dati. Quando i tag vengono usati per classificare gli asset nel quadro di operazioni di gestione dei costi, le aziende spesso necessitano dei tag seguenti: business unit, reparto, codice di fatturazione, geografia, ambiente, progetto e carico di lavoro o "categorizzazione dell'applicazione". Gestione costi di Azure può usare questi tag per creare visualizzazioni diverse dei dati sui costi.

L'assegnazione di tag è uno dei metodi di elezione per comprendere i dati contenuti in qualsiasi report sui costi. Si tratta di una parte fondamentale di qualsiasi ambiente gestito correttamente, oltre a rappresentare il primo passaggio per definire la governance corretta di qualsiasi ambiente.

Il primo passaggio per tenere traccia in modo accurato delle informazioni sui costi tra business unit, ambienti e progetti diversi consiste nel definire uno standard per l'assegnazione di tag. Il secondo passaggio consiste nell’assicurarsi che lo standard per l'assegnazione di tag venga applicato in modo coerente. Gli articoli seguenti consentono di eseguire ognuno di questi passaggi:

- [Sviluppare standard per la denominazione e l’assegnazione di tag](../considerations/naming-and-tagging.md)
- [Definire un MVP di governance per applicare gli standard per l'assegnazione di tag](../../govern/guides/complex/index.md)

### <a name="resource-organization"></a>Organizzazione delle risorse

Esistono diversi approcci per organizzare gli asset. Questa sezione descrive una procedura consigliata in base alle esigenze di un'azienda di grandi dimensioni, con strutture di costo distribuite tra business unit, geografie e organizzazioni IT. Una procedura consigliata simile per un'organizzazione più piccola e meno complessa è disponibile nella [Guida alla governance aziendale standard](../../govern/guides/standard/index.md).

Per un'azienda di grandi dimensioni, il modello seguente per i gruppi di gestione, le sottoscrizioni e i gruppi di risorse permette di creare una gerarchia che consenta a ogni team di disporre del livello di visibilità appropriato per svolgere le proprie mansioni. Quando l'azienda necessita di controlli dei costi per impedire il superamento del budget, può applicare alle sottoscrizioni presenti all'interno di questa struttura alcuni strumenti di governance come Azure Blueprints o Criteri di Azure, in modo da evitare rapidamente eventuali errori di costo futuri.

![Diagramma di organizzazione delle risorse per un’azienda di grandi dimensioni](../../_images/govern/large-enterprise-resource-organization.png)

Nel diagramma precedente, la radice della gerarchia del gruppo di gestione contiene un nodo per ogni business unit. In questo esempio, una multinazionale che necessita di visibilità sulle business unit internazionali decide di creare un nodo per la geografia di ogni business unit della gerarchia.

All'interno di ogni geografia è presente un nodo separato per gli ambienti di produzione e non di produzione, in modo da isolare i controlli di costi, accessi e governance. Per consentire operazioni più efficienti e investimenti più saggi, l'azienda usa le sottoscrizioni per isolare ulteriormente gli ambienti di produzione con diversi livelli di impegno in termini di prestazioni operative. Infine, l'azienda usa gruppi di risorse per acquisire unità distribuibili di una funzione, denominate applicazioni.

Il diagramma mostra le procedure consigliate, escludendo tuttavia le opzioni seguenti:

- Molte aziende limitano le operazioni a una singola area geopolitica. Questo approccio riduce la necessità di diversificare le discipline di governance o i dati sui costi in base ai requisiti di sovranità dei dati locali. In questi casi, non è necessario alcun nodo geografico.
- Alcune aziende preferiscono suddividere ulteriormente gli ambienti di sviluppo, test e controllo di qualità in sottoscrizioni separate.
- Quando una società integra un team CCoE (Cloud Center of Excellence), le sottoscrizioni dei servizi condivisi in ogni nodo geografico possono ridurre gli asset duplicati.
- Sforzi di adozione minori possono avere una gerarchia di gestione molto più ridotta. È comune vedere un singolo nodo radice per l'IT aziendale, con un singolo livello di nodi subordinati nella gerarchia per diversi ambienti. Anche se non si tratta di una violazione delle procedure consigliate per un ambiente gestito correttamente, questo rende più difficile fornire un modello di accesso con diritti minimi per il controllo dei costi e altre funzioni importanti.

La parte restante di questo articolo presuppone l'uso delle procedure consigliate nel diagramma precedente. Tuttavia, gli articoli seguenti possono essere utili per applicare l'approccio a un'organizzazione di risorse più adatta alla propria azienda:

- [Ridimensionamento con più sottoscrizioni di Azure](../considerations/scaling-subscriptions.md)
- [Distribuzione di un MVP di governance per standard di ambienti gestiti correttamente](../../govern/guides/complex/index.md)

## <a name="provide-the-right-level-of-cost-access"></a>Fornire il corretto livello di accesso ai costi

La gestione dei costi è un'attività del team. La sezione relativa alla conformità dell'organizzazione del Cloud Adoption Framework stabilisce un numero ridotto di team di base e definisce il modo in cui questi team supportano le attività di adozione del cloud. Questo articolo amplia le definizioni di team includendo l'ambito e i ruoli da assegnare ai membri di ogni team per ottenere il livello di visibilità appropriato sui dati di gestione dei costi.

- I *ruoli* definiscono le operazioni che un utente può eseguire per diversi asset.
- L'*ambito* definisce le risorse (utente, gruppo, entità servizio o identità gestita) per cui un utente può eseguire tali operazioni.

Come procedura consigliata generale, per l'assegnazione di utenti a vari ruoli e ambiti si consiglia un modello con privilegi minimi.

### <a name="roles"></a>Ruoli

Gestione costi di Azure supporta i seguenti ruoli predefiniti per ogni ambito:

- [Proprietario](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner). Può visualizzare i costi e gestire tutti gli elementi, inclusa la configurazione dei costi.
- [Collaboratore](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor). Può visualizzare i costi e gestire tutti gli elementi, inclusa la configurazione dei costi, ma escluso il controllo degli accessi.
- [Lettore](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader). Può visualizzare tutti gli elementi, inclusi i dati relativi ai costi e la configurazione, ma non apportare modifiche.
- [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor). Può visualizzare i costi e gestire la configurazione dei costi.
- [Lettore per Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) Può visualizzare la configurazione e i dati dei costi.

Come procedura consigliata generale, ai membri di tutti i team deve essere assegnato il ruolo di Collaboratore di Gestione costi. Questo ruolo concede l'accesso per creare e gestire i budget e le esportazioni, in modo da monitorare i costi e creare report in modo più efficace. Tuttavia, i membri del [team di strategia cloud](../../organize/cloud-strategy.md) devono essere impostati solo come Lettore per Gestione costi. Questo perché non sono interessati a impostare i budget nell'ambito dello strumento di Gestione costi di Azure.

### <a name="scope"></a>`Scope`

Le impostazioni seguenti relative all'ambito e ai ruoli permettono di creare la visibilità necessaria per la gestione dei costi. Questa procedura consigliata potrebbe richiedere modifiche minime per allinearsi alle decisioni dell'organizzazione in merito agli asset.

- [Team di adozione del cloud](../../organize/cloud-adoption.md). Le responsabilità per le modifiche di ottimizzazione in corso richiedono l'accesso come Collaboratore di Gestione costi a livello di gruppo di risorse.

  - **Ambiente operativo**. Come minimo, il team di adozione del cloud deve già disporre dell'accesso come [Collaboratore](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) a tutti i gruppi di risorse interessati o almeno ai gruppi correlati ad attività di sviluppo/test o di distribuzione in corso. Non è necessaria alcuna impostazione di ambito aggiuntiva.
  - **Ambienti di produzione**. Una volta stabilita la corretta suddivisione delle responsabilità, il team di adozione del cloud probabilmente non potrà continuare ad accedere ai gruppi di risorse correlati ai propri progetti. I gruppi di risorse che supportano le istanze di produzione dei rispettivi carichi di lavoro dovranno avere un ambito aggiuntivo per offrire al team visibilità sull'impatto delle proprie decisioni sui costi di produzione. L'impostazione dell'ambito di [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) per i gruppi di risorse di produzione per questo team consentirà al team di monitorare i costi e impostare i budget in base all'uso e agli investimenti in corso nei carichi di lavoro supportati.

- [Team di strategia del cloud](../../organize/cloud-strategy.md). Le responsabilità di rilevamento dei costi tra più progetti e business unit richiedono l'accesso come Lettore per Gestione costi al livello radice della gerarchia del gruppo di gestione.

  - Assegnare l'accesso come [Lettore per Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) a questo team nel gruppo di gestione. In questo modo verrà garantita la visibilità continua su tutte le distribuzioni associate alle sottoscrizioni regolate da tale gerarchia del gruppo di gestione.

- [Team di Governance cloud](../../organize/cloud-governance.md). Le responsabilità di gestione dei costi, allineamento del budget e creazione di report per tutte le attività di adozione richiede l'accesso come Collaboratore di Gestione costi a livello radice della gerarchia del gruppo di gestione.

  - In un ambiente gestito correttamente, il team di governance del cloud probabilmente possiede già un livello di accesso più elevato, rendendo non necessaria un'assegnazione di ambito aggiuntiva come [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).

- [Centro di eccellenza cloud](../../organize/cloud-center-of-excellence.md). La responsabilità della gestione dei costi correlati ai servizi condivisi richiede l'accesso come Collaboratore di Gestione costi a livello di sottoscrizione. Questo team può richiedere anche l'accesso come Collaboratore di Gestione costi a gruppi di risorse o sottoscrizioni che contengono asset distribuiti da automazione CCoE per comprendere il modo in cui tali automazioni influiscono sui costi.

  - **Servizi condivisi**. Quando un centro cloud di eccellenza è impegnato, la procedura consigliata suggerisce che gli asset gestiti da CCoE siano supportati da una sottoscrizione del servizio condiviso centralizzata in un modello hub/spoke. In questo scenario, è probabile che il CCoE disponga dell'accesso come collaboratore o proprietario a tale sottoscrizione, rendendo non necessaria un'assegnazione di ambito aggiuntiva come [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).
  - **Automazione/controlli CCoE**. Il CCoE fornisce in genere controlli e script di distribuzione automatici ai team di adozione del cloud. Il CCoE ha la responsabilità di comprendere il modo in cui questi acceleratori influiscono sui costi. Per ottenere tale visibilità, il team deve disporre dell'accesso come [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) a qualsiasi gruppo di risorse o sottoscrizione che esegua tali acceleratori.

- **Team Operazioni cloud**. La responsabilità della gestione dei costi in corso per gli ambienti di produzione richiede l'accesso come Collaboratore di Gestione costi a tutte le sottoscrizioni di produzione.

  - La raccomandazione generale consente di inserire asset di produzione e non di produzione in sottoscrizioni separate gestite da nodi della gerarchia del gruppo di gestione associata agli ambienti di produzione. In un ambiente gestito correttamente, i membri del team operativo probabilmente hanno già accesso come proprietari o collaboratori alle sottoscrizioni di produzione, rendendo superfluo il ruolo di [Collaboratore di Gestione costi](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).

## <a name="additional-cost-management-resources"></a>Risorse aggiuntive per la gestione dei costi

Gestione costi di Azure è uno strumento ben documentato per impostare i budget e ottenere visibilità sui costi del cloud per Azure o AWS. Dopo avere stabilito l'accesso alla gerarchia di un ambiente gestito correttamente, gli articoli seguenti possono aiutare a usare tale strumento per monitorare e controllare i costi.

### <a name="get-started-with-azure-cost-management"></a>Introduzione a Gestione costi di Azure

Per altre informazioni sull'introduzione a Gestione costi di Azure, vedere [Come ottimizzare gli investimenti per il cloud con Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json).

### <a name="use-azure-cost-management"></a>Usare Gestione costi di Azure

- [Creare e gestire i budget](https://docs.microsoft.com/azure/cost-management/tutorial-acm-create-budgets)
- [Esportare dati relativi ai costi](https://docs.microsoft.com/azure/cost-management/tutorial-export-acm-data)
- [Ottimizzare i costi in base a raccomandazioni](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations)
- [Usare avvisi per i costi per monitorare l'uso e le spese](https://docs.microsoft.com/azure/cost-management/cost-mgt-alerts-monitor-usage-spending)

### <a name="use-azure-cost-management-to-govern-aws-costs"></a>Usare Gestione costi di Azure per gestire i costi AWS

- [Integrazione di report relativi all'uso e ai costi di AWS](https://docs.microsoft.com/azure/cost-management/aws-integration-set-up-configure)
- [Gestire i costi AWS](https://docs.microsoft.com/azure/cost-management/aws-integration-manage)

### <a name="establish-access-roles-and-scope"></a>Definire l'accesso, i ruoli e l'ambito

- [Informazioni sull'ambito di gestione dei costi](https://docs.microsoft.com/azure/cost-management/understand-work-scopes)
- [Impostazione dell'ambito per un gruppo di risorse](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal)
