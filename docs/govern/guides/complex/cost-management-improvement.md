---
title: 'Guida alla governance per le aziende complesse: Migliorare la disciplina di gestione dei costi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: Migliorare la disciplina di gestione dei costi'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5dbb92053e12ec9aee795c54271ab45d56d6722c
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71220174"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-cost-management-discipline"></a>Guida alla governance per le aziende complesse: Migliorare la disciplina di gestione dei costi

In questo articolo viene avanzata la descrizione aggiungendo i controlli dei costi alla governance del prodotto minimo (MVP).

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

Il livello di adozione del cloud ha superato l'indicatore di tolleranza definito nell'MVP per la governance. L'aumento della spesa ora giustifica un investimento del tempo dal team di governance del cloud per monitorare e controllare i modelli di spesa.

Come chiaro promotore dell'innovazione, l'IT non viene più considerato principalmente un centro di costo. Poiché l'organizzazione IT offre un maggior valore, il CIO e il CFO accettano che il tempo è giusto per spostare il ruolo che svolge nell'azienda. Tra le varie modifiche, il CFO vuole testare un approccio al cloud accounting basato su pagamenti diretti per il ramo canadese di una delle business unit. Uno dei due data center ritirati ospitava esclusivamente asset per le operazioni canadesi di tale business unit. In questo modello la filiale canadese della business unit verrà fatturata direttamente per le spese operative correlate agli Asset ospitati. Questo modello consente di concentrarsi meno sulla gestione della spesa di un altro utente e sulla creazione di un valore. Tuttavia, prima di iniziare questa transizione, è necessario implementare gli opportuni strumenti per la gestione dei costi.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Nella fase precedente di questo scenario, il team IT ha iniziato attivamente a spostare in Azure i carichi di lavoro di produzione con i dati protetti.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- 5000 asset sono stati rimossi dai due data center contrassegnati per il ritiro. I responsabili dell'approvvigionamento e della sicurezza IT stanno effettuando il deprovisioning degli asset fisici rimanenti.
- I team di sviluppo di applicazioni hanno implementato pipeline di integrazione continua/recapito continuo per distribuire alcune applicazioni native del cloud, in modo significativo sull'esperienza dei clienti.
- Il team di BI ha creato processi di aggregazione, controllo, acquisizione di informazioni dettagliate e generazione di stime in grado di offrire vantaggi tangibili per le operazioni aziendali. I risultati delle stime danno un ampio contributo alla creatività per la realizzazione di nuovi prodotti e servizi.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

Il monitoraggio dei costi e la creazione di report devono essere aggiunti alla soluzione cloud. La creazione di report deve legare le spese operative dirette alle funzioni che utilizzano i costi del cloud. Dovrebbero inoltre consentire all'IT di monitorare le spese e fornire indicazioni tecniche sulla gestione dei costi. Per il ramo canadese, le spese verranno addebitate direttamente al reparto.

## <a name="changes-in-risk"></a>Modifiche al rischio

**Controllo budget:** esiste un rischio intrinseco che le capacità self-service comportino costi eccessivi e imprevisti sulla nuova piattaforma. I processi di governance per i costi di monitoraggio e i costi di migrazione in corso devono poter garantire un costante allineamento con il budget pianificato.

Questo rischio aziendale può tradursi in alcuni rischi tecnici:

- I costi effettivi possono superare quelli pianificati.
- Le condizioni aziendali possono cambiare. In tal caso, è possibile che una funzione aziendale debba usare più servizi cloud del previsto, portando ad anomalie di spesa. Sussiste il rischio che questi costi aggiuntivi vengano considerati in eccedenza rispetto a una modifica richiesta al piano. In caso di esito positivo, l'esperimento canadese dovrebbe contribuire a correggere questo rischio.
- Si può verificare un eccessivo provisioning dei sistemi con un conseguente eccesso di spesa.

## <a name="changes-to-the-policy-statements"></a>Modifiche alle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida.

- Tutti i costi del cloud devono essere monitorati in base a un piano settimanale dal team di governance del cloud. I report sulle deviazioni tra i costi del cloud e il piano stabilito devono essere condivisi con i responsabili IT e l'amministrazione con frequenza mensile. Tutti i costi del cloud e gli aggiornamenti del piano devono essere controllati ogni mese con i responsabili IT e l'amministrazione.
- Tutti i costi devono essere allocati in una funzione aziendale ai fini della rendicontazione.
- Gli asset del cloud devono essere monitorati costantemente per eventuali opportunità di ottimizzazione.
- Gli strumenti di Governance cloud devono limitare le opzioni delle dimensioni degli asset a un elenco approvato di configurazioni. Gli strumenti devono assicurare che tutti gli asset siano individuabili e tracciati dalla soluzione di monitoraggio dei costi.
- Durante la pianificazione della distribuzione, tutte le risorse richieste del cloud associate all'hosting dei flussi di lavoro di produzione dovrebbero essere documentate. Questa documentazione aiuterà a perfezionare i budget e a preparare altri strumenti di automazione per impedire l'uso di opzioni più dispendiose. Durante questo processo, è consigliabile prestare attenzione alle diverse opportunità di sconto offerte dal provider di servizi cloud, ad esempio istanze riservate o riduzioni dei costi di licenza.
- A tutti i proprietari di applicazioni è richiesta la partecipazione con training eseguito su procedure consigliate, al fine di ottimizzare i carichi di lavoro per controllare al meglio i costi del cloud.

## <a name="incremental-improvement-of-the-best-practices"></a>Miglioramento incrementale delle procedure consigliate

Questa sezione dell'articolo consentirà di migliorare la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

1. Apportare modifiche nel Enterprise Portal di Azure per fatturare l'amministratore del reparto per la distribuzione canadese.
2. Implementare Gestione costi di Azure.
    1. Stabilire il livello corretto dell'ambito di accesso in linea con il modello di sottoscrizione e il modello di raggruppamento delle risorse. Supponendo l'allineamento con il MVP di governance definito negli articoli precedenti, questo richiederebbe l'accesso all' **ambito dell'account di registrazione** per il team di governance del cloud in esecuzione su report di alto livello. Altri team esterni alla governance, come quello di approvvigionamento della filiale canadese, avranno bisogno dell'accesso all'**ambito del gruppo di risorse**.
    2. Stabilire un budget in Gestione costi di Azure.
    3. Esaminare e implementare i consigli iniziali. È consigliabile pianificare l'esecuzione ricorrente di un processo per la creazione di report.
    4. Configurare ed eseguire la funzionalità per la creazione di report di Gestione costi di Azure, sia nella fase iniziale sia con frequenza periodica.
3. Aggiornare Criteri di Azure.
    1. Aggiungere valori per tag di controllo, gruppo di gestione, sottoscrizione e gruppo di risorse per identificare tutte le deviazioni.
    2. Definire le opzioni relative alle dimensioni di SKU per limitare le distribuzioni agli SKU elencati nella documentazione relativa alla pianificazione della distribuzione.

## <a name="conclusion"></a>Conclusione

L'aggiunta dei processi e delle modifiche precedenti all'MVP di governance consente di correggere molti dei rischi associati alla governance dei costi. Nel loro insieme offrono le caratteristiche di visibilità, rendicontazione e ottimizzazione necessarie per controllare i costi.

## <a name="next-steps"></a>Passaggi successivi

Man mano che l'adozione del cloud aumenta e fornisce un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambiano. Per questa società fittizia, il passaggio successivo consiste nell'utilizzare questo investimento di governance per gestire più cloud.

> [!div class="nextstepaction"]
> [Miglioramento del cloud](./multicloud-improvement.md)
