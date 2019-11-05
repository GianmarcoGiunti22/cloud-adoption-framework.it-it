---
title: Centro di eccellenza cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descrive la formazione di un cloud Center of Excellence (CCoE).
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: c1819bafaed5e75e6667754d598b075eb3204925
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564306"
---
# <a name="cloud-center-of-excellence"></a>Centro di eccellenza cloud

L'agilità aziendale e tecnica sono gli obiettivi principali della maggior parte delle organizzazioni IT. Cloud Center of Excellence (CCoE) è una funzione che crea un equilibrio tra la velocità e la stabilità.

## <a name="function-structure"></a>Struttura Function

CCoE richiede la collaborazione tra le funzionalità seguenti:

- Adozione del cloud (in particolare architetti di soluzioni)
- Strategia cloud (in particolare il programma e i Project Manager)
- Governance del cloud
- Piattaforma cloud
- Automazione del cloud

## <a name="impact-and-cultural-change"></a>Effetti e modifiche culturali

Quando questa funzione è strutturata e supportata correttamente, i partecipanti possono accelerare le attività di innovazione e migrazione riducendo al tempo stesso il costo complessivo del cambiamento e aumentando la flessibilità aziendale. Quando è stata implementata correttamente, questa funzione può produrre riduzioni evidenti nel time-to-Market. Poiché le procedure del team sono maturate, gli indicatori di qualità miglioreranno, tra cui affidabilità, efficienza delle prestazioni, sicurezza, gestibilità e soddisfazione dei clienti. Questi miglioramenti in termini di efficienza, agilità e qualità sono particolarmente importanti se l'azienda prevede di implementare attività di migrazione cloud su larga scala o se si desidera utilizzare il cloud per promuovere le innovazioni associate alla differenziazione del mercato.

In caso di esito positivo, un modello CCoE creerà un significativo cambiamento culturale. Il presupposto fondamentale di un approccio CCoE è che funge da broker, partner o rappresentante per l'azienda. Questo modello rappresenta un cambiamento di paradigma rispetto alla vista tradizionale come unità operativa o livello di astrazione tra le risorse aziendali e IT.

La figura seguente fornisce un'analogia per questa modifica culturale. Senza un approccio CCoE, tende a concentrarsi sulla fornitura di controllo e responsabilità centrale, agendo come semafori in un'intersezione. Quando il CCoE ha esito positivo, lo stato attivo è la libertà e la responsabilità delegata, che è più simile a una rotonda in un'intersezione.

![Analogie per uno spostamento di paradigma CCoE](../_images/ready/ccoe-paradigm-shift.png)

Nessuno degli approcci illustrati nell'immagine di analogia precedente è corretto o errato. si tratta solo di visualizzazioni alternative di responsabilità e gestione. Se il desiderio è quello di definire un modello self-service che consenta alle unità aziendali di prendere decisioni proprie rispettando una serie di linee guida e controlli ripetuti e ripetibili, un modello CCoE può rientrare nella strategia tecnologica.

## <a name="key-responsibilities"></a>Responsabilità principali

Il compito principale del team CCoE è quello di accelerare l'adozione del cloud tramite soluzioni native o ibride cloud.

L'obiettivo di CCoE è:

- Consente di creare un'organizzazione IT moderna tramite approcci Agile per acquisire e implementare i requisiti aziendali.
- Usare i pacchetti di distribuzione riutilizzabili che si allineano ai criteri di sicurezza, conformità e gestione dei servizi.
- Mantenere una piattaforma Azure funzionale in linea con le procedure operative.
- Esaminare e approvare l'uso di strumenti nativi del cloud.
- Nel corso del tempo, standardizzare e automatizzare le soluzioni e i componenti della piattaforma necessari di frequente.

## <a name="meeting-cadence"></a>Cadenza riunione

CCoE è una funzione gestita da quattro team ad alta richiesta. È importante consentire la collaborazione biologica e tenere traccia della crescita tramite un catalogo di repository/soluzioni comune. Ottimizza le interazioni naturali, ma Riduci al minimo le riunioni. Quando questa funzione è matura, i team devono tentare di limitare le riunioni dedicate. La partecipazione a riunioni ricorrenti, ad esempio le riunioni di rilascio ospitate dal team di adozione del cloud, fornirà input di dati. In parallelo, una riunione dopo ogni piano di rilascio è condivisa può offrire un punto di tocco minimo per questo team.

## <a name="solutions-and-controls"></a>Soluzioni e controlli

Ogni membro di CCoE è incaricato di comprendere i vincoli, i rischi e le protezioni necessari che hanno portato al set corrente di controlli IT. Gli sforzi collettivi dei CCoE devono trasformare tale comprensione in soluzioni o controlli nativi (o ibridi) cloud, che consentono di ottenere risultati aziendali in modalità self-service desiderati. Man mano che vengono create, le soluzioni vengono condivise con diversi team sotto forma di controlli o automazione che funge da Guardrails per varie attività. Tali Guardrails consentono di instradare le attività di flusso libero dei diversi team, delegando al tempo stesso le responsabilità per i partecipanti a diversi sforzi di migrazione o innovazione.

Esempi di questa transizione:

| Scenario | Soluzione pre-CCoE | Soluzione post-CCoE |
|---------|---------|---------|
| Provisioning di un SQL Server di produzione | I team di rete, IT e piattaforma dati eseguono il provisioning di diversi componenti nel corso di giorni o addirittura settimane. | Il team che richiede il server distribuisce un'istanza di PaaS del database SQL di Azure. In alternativa, è possibile usare un modello preapprovato per distribuire tutte le risorse IaaS nel cloud in poche ore. |
| Provisioning di un ambiente di sviluppo | I team di rete, IT, sviluppo e DevOps accettano le specifiche e distribuiscono un ambiente. | Il team di sviluppo definisce le proprie specifiche e distribuisce un ambiente basato sul budget allocato. |
| Aggiornare i requisiti di sicurezza per migliorare la protezione dei dati | I team di rete, IT e sicurezza aggiornano diversi dispositivi di rete e macchine virtuali in più ambienti per aggiungere protezioni. | Gli strumenti di governance del cloud vengono usati per aggiornare i criteri che possono essere applicati immediatamente a tutti gli asset in tutti gli ambienti cloud. |

## <a name="negotiations"></a>Negoziazioni

La radice di qualsiasi impegno CCoE è un processo di negoziazione continuo. Il team di CCoE negozia con le funzioni IT esistenti per ridurre il controllo centrale. I compromessi per l'azienda in questa negoziazione sono la libertà, l'agilità e la velocità. Il valore di compromesso per i team IT esistenti viene fornito come nuove soluzioni. Le nuove soluzioni offrono al team IT esistente uno o più dei seguenti vantaggi:

- Possibilità di automatizzare i problemi comuni.
- Miglioramenti della coerenza (riduzione delle frustrazioni quotidiane).
- Opportunità di apprendere e distribuire nuove soluzioni tecniche.
- Riduzioni negli eventi imprevisti con gravità elevata, ovvero un minor numero di correzioni rapide o risposte per cercapersone per il ritardo notturno.
- Possibilità di ampliare il proprio ambito tecnico, affrontando argomenti più ampi.
- Partecipazione a soluzioni aziendali di livello più alto, per affrontare l'effetto della tecnologia.
- Riduzione delle attività di manutenzione umile.
- Aumento della strategia tecnologica e dell'automazione.

In Exchange per questi vantaggi, la funzione IT esistente può scambiare i valori seguenti, sia reali che percepiti:

- Senso del controllo dei processi di approvazione manuale.
- Senso di stabilità dal controllo delle modifiche.
- Rilevamento della sicurezza del processo dal completamento delle attività ricorrenti necessarie.
- Senso di coerenza che deriva dalla conformità ai fornitori di soluzioni IT esistenti.

Nelle aziende che fanno parte del cloud integro, questo processo di negoziazione è una conversazione dinamica tra i peer e la collaborazione tra i team IT. I dettagli tecnici possono essere complessi, ma sono gestibili quando sono in grado di comprendere l'obiettivo e supportano le attività CCoE. Quando è minore del supporto, la sezione seguente sull'abilitazione di CCoE Success può aiutare a superare i blocchi culturali.

## <a name="enable-ccoe-success"></a>Abilita CCoE riuscita

Prima di procedere con questo modello, è importante convalidare la tolleranza della società per una mentalità di crescita e la comodità con il rilascio di responsabilità centrali. Come indicato in precedenza, lo scopo di un CCoE è quello di scambiare il controllo per l'agilità e la velocità.

Questo tipo di modifica richiede tempo, sperimentazione e negoziazione. Durante questo processo di maturazione, saranno presenti urti e set back. Tuttavia, se il team rimane diligente e non è scoraggiato dalla sperimentazione, esiste una probabilità elevata di successo nel miglioramento della flessibilità, della velocità e dell'affidabilità. Uno dei fattori più importanti per l'esito positivo o negativo di un CCoE è il supporto della leadership e degli stakeholder principali.

### <a name="key-stakeholders"></a>Principali parti interessate

La leadership IT è il primo e più ovvio stakeholder. I responsabili IT svolgeranno una parte importante. Tuttavia, durante questo processo, è necessario il supporto del CIO e di altri leader IT a livello esecutivo.

Meno ovvio è la necessità di stakeholder aziendali. La flessibilità aziendale e il time-to-Market sono motivazioni chiave per la formazione CCoE. Di conseguenza, le parti interessate principali dovrebbero avere un interesse per queste aree. Esempi di stakeholder aziendali includono leader line-of-business, dirigenti finanziari, dirigenti operativi e proprietari di prodotti aziendali.

### <a name="business-stakeholder-support"></a>Supporto per stakeholder aziendali

Le attività CCoE possono essere accelerate con supporto da parte degli stakeholder aziendali. La maggior parte delle attività di CCoE è incentrata sulla creazione di miglioramenti a lungo termine per l'agilità e la velocità aziendali. La definizione dell'effetto dei modelli operativi correnti e del valore dei miglioramenti è utile come strumento di negoziazione e guida per CCoE. Per il supporto di CCoE è consigliabile documentare gli elementi seguenti:

- Definire un set di risultati aziendali e obiettivi previsti come risultato della flessibilità aziendale e della velocità.
- Definire chiaramente i punti di dolore creati dai processi IT correnti, ad esempio velocità, agilità, stabilità e problemi di costo.
- Definire chiaramente l'effetto cronologico di questi punti deboli (ad esempio la perdita di quota di mercato, i guadagni del competitore in funzioni e funzioni, esperienze dei clienti non soddisfacenti e aumenti del budget).
- Definire opportunità di miglioramento aziendale bloccate dai punti di dolore e dai modelli operativi correnti.
- Stabilire le tempistiche e le metriche correlate a tali opportunità.

Questi punti dati non sono un attacco. Contribuiscono invece a CCoE apprendere dal passato e a definire un backlog realistico e pianificare il miglioramento.

**Supporto continuo e Engagement:** I team CCoE possono dimostrare i ritorni rapidi in alcune aree. Tuttavia, gli obiettivi di livello superiore, come la flessibilità aziendale e il time-to-Market, possono richiedere molto più tempo. Durante la fase di maturazione, c'è un rischio elevato di CCoE che sta per essere scoraggiato o che è stato estratto per concentrarsi su altre attività IT.

Durante i primi sei-nove mesi di attività CCoE, è consigliabile che gli stakeholder aziendali allochino il tempo per soddisfare il mese con la leadership IT e il CCoE. Non è necessaria una cerimonia formale per queste riunioni. È sufficiente ricordare che i membri di CCoE e la loro leadership dell'importanza di questo programma possono continuare a guidare CCoE success.

Inoltre, è consigliabile che gli stakeholder aziendali siano informati dello stato di avanzamento e dei blocchi riscontrati dal team CCoE. Molti dei loro sforzi appariranno come minuzie tecniche. Tuttavia, è importante per gli stakeholder aziendali comprendere lo stato di avanzamento del piano, in modo che possano impegnarsi quando il team perde il vapore o si distrae da altre priorità.

### <a name="it-stakeholder-support"></a>Supporto per stakeholder IT

**Supporto della visione:** Un lavoro CCoE di successo richiede una grande quantità di negoziazione con i membri del team IT esistenti. Quando questa operazione viene eseguita correttamente, tutto contribuisce alla soluzione e si trova in modo confortevole con la modifica. In tal caso, è possibile che alcuni membri del team IT esistente desiderino mantenere il controllo dei meccanismi per diversi motivi. Il supporto di stakeholder IT sarà fondamentale per il successo della CCoE quando si verificano tali situazioni. L'incoraggiamento e il rinforzo degli obiettivi complessivi della CCoE è importante per la risoluzione dei blocchi alla negoziazione corretta. In rare occasioni, è possibile che gli stakeholder IT debbano anche intervenire e suddividere un deadlock o un voto vincolato per far progredire il CCoE.

**Mantieni lo stato attivo:** Un CCoE può essere un impegno significativo per qualsiasi team IT vincolato alle risorse. La rimozione di architetti avanzati da progetti a breve termine per concentrarsi sui guadagni a lungo termine può creare difficoltà per i membri del team che non fanno parte del CCoE. È importante che la leadership IT e gli stakeholder IT restino incentrati sull'obiettivo della CCoE. Il supporto dei responsabili IT e degli stakeholder IT è necessario per annullare l'assegnazione di priorità alle problematiche delle operazioni quotidiane a favore dei compiti CCoE.

**Creare un buffer:** Il team di CCoE proverà con nuovi approcci. Alcuni di questi approcci non si allineano bene con le operazioni esistenti o i vincoli tecnici. Quando gli esperimenti hanno esito negativo, c'è un rischio reale di CCoE che si verificano o ricorsi da altri team. L'incoraggiamento e il buffering del team dalle conseguenze delle opportunità di apprendimento "Fast fail" è importante. È ugualmente importante tenere il conto del team per un mindset di crescita, assicurandosi che l'apprendimento venga appreso da tali esperimenti e che si trovino soluzioni migliori.

## <a name="next-steps"></a>Passaggi successivi

Cloud Center of Excellence richiede sia le funzionalità della [piattaforma cloud](./cloud-platform.md) che le [funzionalità di automazione del cloud](./cloud-automation.md). Il passaggio successivo consiste nell'allineare le [funzionalità della piattaforma cloud](./cloud-platform.md).

> [!div class="nextstepaction"]
> [Allineare le funzionalità della piattaforma cloud](./cloud-platform.md)
