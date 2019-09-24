---
title: 'Guida aziendale standard: Miglioramento della coerenza delle risorse'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida aziendale standard: Miglioramento della coerenza delle risorse'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: bede887bcb4589b286920a79016701961a04b8b6
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222230"
---
# <a name="standard-enterprise-guide-improving-resource-consistency"></a>Guida aziendale standard: Miglioramento della coerenza delle risorse

In questo articolo viene avanzata la descrizione tramite l'aggiunta di controlli di coerenza delle risorse per supportare app mission-critical.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

Le esperienze dei clienti, gli strumenti di previsione e le infrastrutture migrate continuano a evolversi. L'azienda è ora pronta a iniziare a usare questi asset in un ambiente di produzione.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Nella fase precedente di questo scenario, i team di BI e sviluppo delle applicazioni erano quasi pronti a integrare dati finanziari e dei clienti nei carichi di lavoro di produzione. Il team IT stava ritirando il data center di ripristino di emergenza.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- L'IT ha ritirato al 100% il data center di ripristino di emergenza, in anticipo rispetto alla pianificazione. Nel processo, un set di asset nel Data Center di produzione è stato identificato come candidati alla migrazione cloud.
- I team di sviluppo delle applicazioni sono ora pronti per il traffico dell'ambiente di produzione.
- Il team di BI è pronto a reinserire stime e informazioni dettagliate nei sistemi operativi nel data center di produzione.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

Prima di usare distribuzioni di Azure nei processi aziendali di produzione, le operazioni nel cloud devono evolversi. In combinazione, sono necessarie modifiche di governance aggiuntive per garantire che gli asset possano essere gestiti correttamente.

I cambiamenti che riguardano lo stato attuale e quello futuro espongono a nuovi rischi che richiedono nuove definizioni di criteri.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Interruzione aziendale:** vi è un rischio intrinseco che qualsiasi nuova piattaforma possa causare l'interruzione di processi aziendali cruciali. Il team responsabile delle operazioni IT e i team che si occupano in vari modi delle adozioni del cloud sono relativamente inesperti per quanto riguarda le operazioni nel cloud. Questa operazione aumenta il rischio di interruzione e deve essere risolta e regolata.

Questo rischio aziendale può tradursi in diversi rischi tecnici:

1. Eventuali intrusioni dall'esterno o attacchi Denial of Service potrebbero causare un'interruzione delle attività aziendali.
2. Gli asset mission-critical potrebbero non essere individuati correttamente e pertanto potrebbero non essere gestiti correttamente.
3. Gli asset non individuati o mal definiti possono non essere supportati dai processi di gestione operativa esistenti.
4. La configurazione delle risorse distribuite potrebbe non soddisfare le aspettative delle prestazioni.
5. La registrazione potrebbe non essere effettuata e centralizzata correttamente per consentire la risoluzione dei problemi di prestazioni.
6. Le procedure di ripristino possono non riuscire o impiegare più tempo del previsto.
7. Processi di distribuzione incoerenti potrebbero produrre lacune a livello di sicurezza che possono causare perdite di dati o interruzioni.
8. Deviazioni di configurazione e patch non applicate potrebbero produrre lacune a livello di sicurezza non intenzionali che possono causare perdite di dati o interruzioni.
9. La configurazione potrebbe non soddisfare i requisiti dei contratti di servizio definiti o quelli di ripristino concordati.
10. I sistemi operativi o le applicazioni distribuite potrebbero non soddisfare i requisiti di protezione avanzata.
11. I numerosi team che lavorano nel cloud pongono un rischio di incoerenza.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida. L'elenco può sembrare lungo, ma l'adozione di questi criteri può essere più semplice di quanto non sembri.

1. tutti gli asset distribuiti devono essere ordinati in categorie in base a criticità e classificazione dei dati. Le classificazioni devono essere esaminate dal team di governance del cloud e dal proprietario dell'applicazione prima della distribuzione nel cloud.
2. Le subnet che contengono applicazioni cruciali devono essere protette tramite una soluzione firewall in grado di rilevare le intrusioni e rispondere agli attacchi.
3. Gli strumenti di governance devono controllare e soddisfare i requisiti di configurazione della rete definiti dal team di gestione della sicurezza.
4. Gli strumenti di governance devono convalidare che tutti gli asset correlati alle app cruciali o ai dati protetti siano inclusi nel monitoraggio per l'esaurimento e l'ottimizzazione delle risorse.
5. Gli strumenti di governance devono convalidare che venga raccolto il livello appropriato di dati di registrazione per tutti i dati protetti o le applicazioni cruciali.
6. Il processo di governance deve convalidare che il backup, il ripristino e il rispetto dei contratti di servizio vengano implementati correttamente per le applicazioni cruciali e i dati protetti.
7. Gli strumenti di governance devono limitare le distribuzioni di macchine virtuali solo alle immagini approvate.
8. Gli strumenti di governance devono soddisfare il requisito in base al quale gli aggiornamenti automatici non devono essere applicati a tutti gli asset distribuiti che supportano applicazioni cruciali. Le violazioni devono essere esaminate con i team di gestione operativa e risolte in base ai criteri relativi alle operazioni. Gli asset che non vengono aggiornati automaticamente devono essere inclusi in processi di proprietà del team responsabile delle operazioni IT.
9. Gli strumenti di governance devono convalidare l'assegnazione di tag correlati a costo, criticità, contratto di servizio, applicazione e classificazione dei dati. Tutti i valori devono essere allineati ai valori predefiniti gestiti dal team di governance.
10. I processi di governance devono includere controlli in fase di distribuzione e in base a cicli regolari per garantire la coerenza tra tutti gli asset.
11. Tendenze ed exploit che possono influire sulle distribuzioni cloud devono essere esaminati regolarmente dal team responsabile della sicurezza in modo da fornire aggiornamenti per gli strumenti di gestione della sicurezza usati nel cloud.
12. Prima della distribuzione nell'ambiente di produzione, tutti i dati protetti e le app cruciali devono essere aggiunti alla soluzione di monitoraggio operativo designata. Gli asset che non possono essere individuati dagli strumenti per le operazioni IT scelti non devono essere distribuiti nell'ambiente di produzione. Qualsiasi modifica necessaria per rendere gli asset individuabili deve essere apportata ai processi di distribuzione pertinenti per garantire che gli asset siano individuabili nelle distribuzioni future.
13. Quando viene individuato, i team di gestione operativi ridimensionano gli asset, per garantire che le risorse soddisfino i requisiti di prestazioni.
14. Gli strumenti di distribuzione devono essere approvati dal team di governance del cloud per garantire la governance continua degli asset distribuiti.
15. Gli script di distribuzione devono essere conservati in un repository centrale accessibile dal team di governance del cloud per la revisione e il controllo periodici.
16. I processi di revisione della governance devono convalidare che gli asset distribuiti siano configurati correttamente in base ai requisiti relativi a contratti di servizio e ripristino.

## <a name="incremental-improvement-of-governance-practices"></a>Miglioramento incrementale delle procedure di governance

In questa sezione dell'articolo verrà modificata la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

1. Il team operativo cloud definisce gli strumenti di monitoraggio operativo e gli strumenti di correzione automatici. Il team di governance del cloud supporterà tali processi di individuazione. In questo caso di utilizzo, il team operativo cloud ha scelto monitoraggio di Azure come strumento principale per il monitoraggio di applicazioni cruciali.
2. Creare un archivio in Azure DevOps per l'archiviazione e il controllo delle versioni di tutti i modelli di Resource Manager e le configurazioni tramite script pertinenti.
3. Implementazione dell'insieme di credenziali di servizi di ripristino di Azure:
    1. Definire e distribuire l'insieme di credenziali di servizi di ripristino di Azure per i processi di backup e ripristino.
    2. Creare un modello di Resource Manager per la creazione di un insieme di credenziali in ogni sottoscrizione.
4. Aggiornare Criteri di Azure per tutte le sottoscrizioni:
    1. Controllare e applicare la criticità e la classificazione dei dati in tutte le sottoscrizioni per identificare quelle con asset cruciali.
    2. Controllare e imporre l'uso delle sole immagini approvate.
5. Implementazione di Monitoraggio di Azure:
    1. Una volta identificato un carico di lavoro di importanza critica, creare un'area di lavoro di monitoraggio di Azure.
    2. Durante i test di distribuzione, il team operativo cloud distribuisce gli agenti necessari e i test di individuazione.
6. Aggiornare Criteri di Azure per tutte le sottoscrizioni che contengono applicazioni cruciali.
    1. Controllare e imporre l'applicazione di un gruppo di sicurezza di rete per tutte le schede di interfaccia di rete e subnet. I team responsabili delle reti e della sicurezza IT definiscono il gruppo di sicurezza di rete.
    2. Controllare e imporre l'uso di reti virtuali e subnet di rete approvate per ogni interfaccia di rete.
    3. Controllare e imporre la limitazione delle tabelle di routing definite dall'utente.
    4. Controllare e applicare la distribuzione degli agenti di Monitoraggio di Azure per tutte le macchine virtuali.
    5. Controllare e applicare che gli insiemi di credenziali dei servizi di ripristino di Azure esistano nella sottoscrizione.
7. Configurazione del firewall:
    1. Identificare una configurazione di Firewall di Azure che soddisfi i requisiti di sicurezza. In alternativa, identificare un dispositivo di terze parti compatibile con Azure.
    1. Creare un modello di Resource Manager per distribuire il firewall con le configurazioni necessarie.
8. Azure Blueprints:
    1. Creare un progetto Azure Blueprints denominato `protected-data`.
    2. Aggiungere il firewall e i modelli dell'insieme di credenziali di Azure al progetto.
    3. Aggiungere i nuovi criteri per le sottoscrizioni con dati protetti.
    4. Pubblicare il progetto in qualsiasi gruppo di gestione che ospiterà le applicazioni cruciali.
    5. Applicare il nuovo progetto a ogni sottoscrizione interessata, nonché ai progetti esistenti.

## <a name="conclusion"></a>Conclusione

Questi processi aggiuntivi e le modifiche apportate all'MVP di governance consentono di correggere molti dei rischi associati alla governance delle risorse. Insieme, aggiungono controlli di ripristino, ridimensionamento e monitoraggio che semplificano le operazioni basate sul cloud.

## <a name="next-steps"></a>Passaggi successivi

Quando l'adozione del cloud continua e offre un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambieranno. Per la società fittizia in questa guida, il trigger successivo si verifica quando la scalabilità della distribuzione supera 100 risorse al cloud o la spesa mensile supera $1.000 al mese. A questo punto, il team di governance del cloud aggiunge i controlli di gestione dei costi.

> [!div class="nextstepaction"]
> [Miglioramento della gestione dei costi](./cost-management-improvement.md)
