---
title: 'Prepararsi alla complessità culturale: allineamento di ruoli e responsabilità'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Preparazione alla complessità culturale: allineamento di ruoli e responsabilità.'
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 011d00038ea29c60601945441f21b14b8865f80d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833349"
---
# <a name="prepare-for-cultural-complexity-aligning-roles-and-responsibilities"></a>Prepararsi alla complessità culturale: allineamento di ruoli e responsabilità

La conoscenza della cultura aziendale necessaria per il funzionamento dei data center esistenti è importante per il successo di qualsiasi migrazione. In alcune organizzazioni la gestione dei data center è affidata a team operativi IT centralizzati, nell'ambito dei quali i ruoli e le responsabilità tendono a essere ben definiti e riconosciuti. Per le aziende di maggiori dimensioni, soprattutto se vincolate a requisiti di conformità di terze parti, la cultura aziendale tende a essere più complessa e ad avere contorni meno definiti. La complessità culturale può presentare ostacoli difficili da comprendere e impegnativi in termini di tempo.

In entrambi gli scenari, è una valida idea investire nella documentazione dei ruoli e delle responsabilità necessari per completare una migrazione. Questo articolo illustra alcuni ruoli e responsabilità osservati nella migrazione di un data center, da usare come modello per la documentazione in modo da rendere più comprensibili i vari passaggi dell'esecuzione.

## <a name="business-functions"></a>Funzioni aziendali

Qualsiasi migrazione include alcune funzioni chiave che vengono eseguite in modo più efficace dalle persone coinvolte nei processi aziendali, quando possibile. Spesso il personale IT è in grado di eseguire le attività seguenti, ma il personale coinvolto nei processi aziendali può contribuire a ridurre le barriere più avanti nel percorso di adozione. Questa integrazione dei ruoli garantisce anche un investimento reciproco dalle principali parti interessate nel corso del processo di migrazione.

| Process | Attività | Descrizione |
|---------|---------|---------|
| Valuta | Obiettivi aziendali | Definire i risultati aziendali da raggiungere con l'impegno di migrazione. |
| Valuta | Priorità | Garantire l'allineamento alle mutevoli priorità aziendali e condizioni di mercato. |
| Valuta | Giustificazione | Convalidare i presupposti che stimolano le motivazioni aziendali in continua evoluzione. |
| Valuta | Rischio | Aiutare il team di adozione del cloud a comprendere l'impatto dei rischi aziendali tangibili. |
| Valuta | Approvazione | Esaminare e approvare l'impatto aziendale delle proposte di modifica dell'architettura. |
| Eseguire l'ottimizzazione | Piano delle modifiche | Definire un piano per l'applicazione delle modifiche all'interno dell'azienda, inclusi i periodi di attività ridotta e i casi di blocco delle modifiche. |
| Eseguire l'ottimizzazione | Test | Allineare gli utenti esperti in grado di convalidare le prestazioni e le funzionalità. |
| Protezione e gestione | Impatto dell'interruzione | Aiutare il team di adozione del cloud a quantificare l'impatto dell'interruzione di un processo aziendale. |
| Protezione e gestione | Convalida dei contratti di servizio | Aiutare il team di adozione del cloud a definire i contratti di servizio e le tolleranze accettabili per le interruzioni delle attività aziendali. |

In ultima analisi, il team di adozione del cloud è responsabile di ognuna di queste attività. Tuttavia, la definizione della responsabilità e di una tempistica uniforme per completare queste attività in base a un ritmo stabilito può migliorare l'allineamento e la coesione degli stakeholder con l'azienda.

## <a name="common-roles-and-responsibilities"></a>Ruoli e responsabilità comuni

Ogni processo nell'ambito della trattazione dei principi di migrazione di Cloud Adoption Framework include un articolo che definisce le attività specifiche per allineare i ruoli e le responsabilità. Per maggiore chiarezza durante l'esecuzione, sarebbe opportuno definire una singola entità responsabile per ogni attività, insieme a tutte le parti responsabili del supporto di tali attività. L'elenco seguente contiene tuttavia una serie di ruoli e responsabilità comuni che hanno un impatto maggiore sull'esecuzione della migrazione. Questi ruoli devono essere identificati nella fase preliminare del processo di migrazione.

> [!NOTE]
> Nella tabella seguente, un'entità responsabile deve iniziare l'allineamento dei ruoli. Per un'esecuzione efficiente, tale colonna deve essere personalizzata in base ai processi esistenti. In teoria, sarebbe opportuno nominare una singola persona come entità responsabile.

| Process | Attività | DESCRIZIONE | Entità responsabile |
|---------|---------|---------|---------|
| Prerequisito | Digital estate | Allineare l'inventario esistente ai presupposti fondamentali, in base ai risultati aziendali. | Team di strategia del cloud |
| Prerequisito | Backlog di migrazione | Definire la priorità per la sequenza dei carichi di lavoro di cui eseguire la migrazione. | Team di strategia del cloud |
| Valuta | Architettura | Sfidare i presupposti iniziali per definire l'architettura di destinazione in base alle metriche di utilizzo. | Team di adozione del cloud |
| Valuta | Approvazione | Approvare l'architettura proposta. | Team di strategia del cloud |
| Migrazione | Accesso per la replica | Accedere agli host e agli asset locali esistenti per stabilire i processi di replica. | Team di adozione del cloud |
| Eseguire l'ottimizzazione | Pronto | Verificare che il sistema soddisfi i requisiti di prestazioni e costi prima della promozione. | Team di adozione del cloud |
| Eseguire l'ottimizzazione | Promozione | Autorizzazioni per promuovere un carico di lavoro alla produzione e reindirizzare il traffico della produzione. | Team di adozione del cloud |
| Protezione e gestione | Transizione operativa | Documentare i sistemi di produzione prima di avviare le operazioni di produzione. | Team di adozione del cloud |

> [!CAUTION]
> Per queste attività, le autorizzazioni influiscono fortemente sull'entità responsabile, che deve avere accesso diretto ai sistemi di produzione nell'ambiente esistente o deve avere la possibilità di proteggere l'accesso tramite altri attori responsabili. La determinazione di questa entità responsabile influisce direttamente sulla strategia di promozione durante i processi di migrazione e ottimizzazione.

## <a name="next-steps"></a>Passaggi successivi

Quando il team ha acquisito una conoscenza generale dei ruoli e delle responsabilità, è il momento di iniziare a preparare i dettagli tecnici della migrazione. La comprensione [della complessità tecnica e della gestione del cambiamento](./technical-complexity.md) può essere utile per preparare il team di adozione del cloud agli aspetti tecnici complessi della migrazione tramite l'allineamento a un processo di gestione incrementale del cambiamento.

> [!div class="nextstepaction"]
> [Complessità tecnica e gestione del cambiamento](./technical-complexity.md)
