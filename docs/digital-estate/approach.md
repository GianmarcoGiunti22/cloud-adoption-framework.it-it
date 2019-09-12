---
title: Approcci per la pianificazione del digital estate
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sui diversi approcci alla pianificazione delle proprietà digitali.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: d4f420274b27646e94c64c2e5347bff50124c9dd
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829345"
---
# <a name="approaches-to-digital-estate-planning"></a>Approcci per la pianificazione del digital estate

La pianificazione delle proprietà digitali può assumere diverse forme a seconda dei risultati desiderati e delle dimensioni del patrimonio esistente. È possibile adottare diversi approcci. È importante definire le aspettative in relazione all'approccio all'inizio dei cicli di pianificazione. Le aspettative non chiare spesso portano a ritardi associati ad esercizi aggiuntivi di raccolta dell'inventario. Questo articolo illustra tre approcci all'analisi.

## <a name="workload-driven-approach"></a>Approccio basato su carichi di lavoro

L'approccio per la valutazione dall'alto verso il basso valuta gli aspetti della sicurezza. La sicurezza include la categorizzazione dei dati (alto, medio o basso), conformità, sovranità e requisiti di rischio per la sicurezza. Questo approccio valuta la complessità dell'architettura di alto livello. Valuta gli aspetti quali l'autenticazione, la struttura dei dati, i requisiti di latenza, le dipendenze e la permanenza presunta dell'applicazione.

L'approccio dall'alto verso il basso misura inoltre i requisiti operativi dell'applicazione, ad esempio i livelli di servizio, l'integrazione, le finestre di manutenzione, il monitoraggio e le informazioni dettagliate. Quando tutti questi aspetti sono stati analizzati e presi in considerazione, il punteggio risultante che riflette la difficoltà relativa della migrazione di questa applicazione a ognuna delle piattaforme cloud: IaaS, PaaS e SaaS.

Inoltre, la valutazione dall'alto verso il basso valuta i vantaggi finanziari dell'applicazione, ad esempio efficienza operativa, TCO, ritorno sugli investimenti e altre metriche finanziarie appropriate. La valutazione esamina anche la stagionalità dell'applicazione (ad esempio, ci sono tempi dell'anno in cui i picchi di domanda?) e il carico di calcolo complessivo.

Esamina anche i tipi di utenti supportati (casuale/esperto, accesso sempre/occasionalmente) e la scalabilità e l'elasticità richieste. Infine, la valutazione conclude esaminando i requisiti di continuità aziendale e resilienza, nonché le dipendenze per l'esecuzione dell'applicazione in caso di interruzione del servizio.

> [!TIP]
> Questo approccio richiede interviste e analisi di carattere aneddotico con stakeholder aziendali e tecnici. La disponibilità degli individui chiave è il rischio maggiore per la tempistica. La natura aneddotica delle origini dati rende più difficile l'elaborazione di stime accurate di costi o tempi. Pianificare in anticipo le pianificazioni e convalidare i dati raccolti.

## <a name="asset-driven-approach"></a>Approccio basato su asset

L'approccio basato su Asset fornisce un piano basato sulle risorse che supportano un'applicazione per la migrazione. Con questo approccio, si esegue il pull dei dati di utilizzo statistici da un database di gestione della configurazione (CMDB) o da altri strumenti di valutazione dell'infrastruttura.

Questo approccio, in genere, presuppone un modello IaaS di distribuzione come base. In questo processo, l'analisi valuta gli attributi di ogni asset: memoria, numero di processori (core CPU), spazio di archiviazione del sistema operativo, unità dati, schede di interfaccia di rete (NIC), IPv6, bilanciamento carico di rete, clustering, versione del sistema operativo, versione del database (se necessario), domini supportati e componenti di terze parti o pacchetti software, tra gli altri. Gli asset di cui si esegue l'inventario in questo approccio vengono quindi allineati ai carichi di lavoro o alle applicazioni per il raggruppamento e il mapping delle dipendenze.

> [!TIP]
> Questo approccio richiede un'ingente origine di dati di utilizzo statistico. Il tempo necessario per analizzare l'inventario e raccogliere i dati rappresenta il rischio maggiore per i tempi. Le origini dati di basso livello possono perdere le dipendenze tra applicazioni o asset. Dedicare almeno un mese per l'analisi dell'inventario. Convalidare le dipendenze prima della distribuzione.

## <a name="incremental-approach"></a>Approccio incrementale

È consigliabile un approccio incrementale, come per molti processi nel Framework di adozione del cloud. Nel caso della pianificazione delle proprietà digitali, che corrisponde a un processo in più fasi:

- **Analisi dei costi iniziale:** Se è necessaria la convalida finanziaria, iniziare con un approccio basato sulle risorse, descritto in precedenza, per ottenere un calcolo dei costi iniziale per l'intera area digitale, senza alcuna razionalizzazione. Questo consente di stabilire un benchmark per il peggiore dei casi.

- **Pianificare la migrazione:** Dopo aver assemblato un team di strategia cloud, creare un backlog di migrazione iniziale usando un approccio basato sul carico di lavoro che si basa sulla conoscenza collettiva e su interviste di stakeholder limitati. Questo approccio crea rapidamente una valutazione del carico di lavoro leggera per favorire la collaborazione.

- **Pianificazione della versione:** A ogni rilascio, il backlog di migrazione viene eliminato e riassegnata in ordine di priorità per concentrarsi sull'effetto aziendale più rilevante. Durante questo processo, i successivi cinque a dieci carichi di lavoro vengono selezionati come versioni con priorità. A questo punto, il team di strategia cloud investe il tempo per completare un approccio esaustivo basato sui carichi di lavoro. Ritardare questa valutazione fino a quando non viene allineata una versione migliore rispetto al tempo delle parti interessate. Inoltre, ritarda l'investimento in un'analisi completa finché l'azienda non inizia a vedere i risultati delle attività precedenti.

- **Analisi esecuzione:** Prima di eseguire la migrazione, la modernizzazione o la replica di qualsiasi asset, valutarla singolarmente e come parte di una versione collettiva. A questo punto, i dati dell'approccio iniziale basato su asset possono essere analizzati per assicurare un dimensionamento e vincoli operativi precisi.

> [!TIP]
> Questo approccio incrementale consente una pianificazione semplificata e risultati accelerati. È importante che tutte le parti coinvolte comprendano l'approccio al processo decisionale ritardato. È ugualmente importante che le ipotesi eseguite in ogni fase siano documentate in modo da evitare la perdita di dettagli.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver selezionato un approccio, è possibile raccogliere l'inventario.

> [!div class="nextstepaction"]
> [Raccogliere i dati di inventario](inventory.md)
