---
title: Prerequisiti per la migrazione ad Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Prerequisiti per la migrazione ad Azure
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: de42ed98f4b7101b2de10240988e9964f57cd415
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818915"
---
::: zone target="chromeless"

# <a name="prerequisites"></a>Prerequisiti

::: zone-end

::: zone target="docs"

# <a name="prerequisites-for-migrating-to-azure"></a>Prerequisiti per la migrazione ad Azure

::: zone-end

Le risorse in questa sezione consentiranno di preparare l'ambiente attuale per la migrazione ad Azure.

# <a name="overviewtaboverview"></a>[Overview](#tab/Overview)

I motivi per eseguire la migrazione ad Azure includono la rimozione dei rischi associati all'hardware legacy, la riduzione delle spese in conto capitale, la liberazione dello spazio dal data center e la rapida realizzazione del ritorno sugli investimenti (ROI).

- **Eliminare l'hardware legacy.** È possibile che siano presenti applicazioni ospitate in un'infrastruttura il cui ciclo di vita o supporto sta per terminare, sia in locale che in un provider di hosting. La migrazione al cloud offre una soluzione interessante alla sfida, in quanto la possibilità di eseguire la migrazione "così com'è" consente al team di risolvere rapidamente la sfida attuale del ciclo di vita dell'infrastruttura e quindi di rivolgere l'attenzione alla pianificazione a lungo termine per il ciclo di vita delle applicazioni e all'ottimizzazione nel cloud.
- **Affrontare il caso del fine del supporto per il software.** Potrebbero essere presenti applicazioni che dipendono da altri sistemi operativi o software prossimi alla fine del supporto. Il passaggio ad Azure può fornire opzioni di supporto estese per queste dipendenze o altre opzioni di migrazione che consentono di ridurre al minimo i requisiti di refactoring per supportare le applicazioni in futuro. Ad esempio, vedere le [opzioni di supporto esteso per Windows Server 2008 e SQL Server 2008](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support).
- **Ridurre le spese in conto capitale.** Ospitare la propria infrastruttura server richiede un notevole investimento in hardware, software, energia elettrica e personale. La migrazione a una soluzione cloud può fornire riduzioni significative nelle spese in conto capitale. Per ottenere le massime riduzioni delle spese in conto capitale, potrebbe essere necessaria una riprogettazione della soluzione. Tuttavia, una migrazione "così com'è" è un ottimo primo passaggio.
- **Liberare spazio nel data center.** È possibile scegliere Azure per espandere la capacità del proprio data center. Un modo per farlo è usare il cloud come estensione delle funzionalità locali.
- **Realizzare rapidamente il ritorno sugli investimenti.** La creazione di un ritorno sugli investimenti (ROI) è molto più semplice con le soluzioni cloud, poiché il modello di pagamento cloud fornisce informazioni dettagliate sull'utilizzo e promuove una cultura per la realizzazione del ROI.

Ogni scenario precedente può essere costituito da punti di ingresso per estendere il footprint cloud usando un'altra metodologia (riallocare, effettuare il refactoring, riprogettare, ricostruire o sostituire).

## <a name="migration-characteristics"></a>Caratteristiche della migrazione

La guida presuppone che prima di questa migrazione, il digital estate fosse costituito principalmente da un'infrastruttura ospitata in locale e potesse includere applicazioni aziendali critiche ospitate. Una volta completata la migrazione, è possibile che i dati abbiano un aspetto molto simile a quello in locale, ma con l'infrastruttura ospitata nelle risorse cloud. In alternativa, il patrimonio ideale di dati è una variante dei dati attuali, perché include aspetti dell'infrastruttura locale con componenti che sono stati sottoposti a refactoring per ottimizzare e sfruttare i vantaggi della piattaforma cloud.

L'obiettivo di questo percorso di migrazione è ottenere:

- Correzione della fine del ciclo di vita dell'hardware legacy.
- Riduzione delle spese in conto capitale.
- Ritorno sugli investimenti.

> [!NOTE]
> Un ulteriore vantaggio di questo percorso di migrazione è il modello di supporto software aggiuntivo per Windows 2008, Windows 2008 R2 e SQL Server 2008 e SQL Server 2008 R2. Per altre informazioni, vedere:
>
> - [Windows Server 2008 e Windows Server 2008 R2](https://www.microsoft.com/cloud-platform/windows-server-2008).
> - [SQL Server 2008 e SQL Server 2008 R2](https://www.microsoft.com/sql-server/sql-server-2008).

# <a name="understand-migration-approachestabapproach"></a>[Informazioni sugli approcci di migrazione](#tab/Approach)

La strategia e gli strumenti usati per eseguire la migrazione di un'applicazione in Azure dipenderanno in gran parte dalle motivazioni aziendali, dai requisiti tecnologici e dalla tempistica, nonché da una conoscenza approfondita del carico di lavoro e degli asset effettivi (infrastruttura, app e dati) di cui verrà eseguita la migrazione.

Prima di determinare la strategia di migrazione cloud, analizzare le applicazioni candidate per identificare la compatibilità con le tecnologie di hosting del cloud. Usare la [Guida alle decisioni relative agli strumenti di migrazione](../../decision-guides/migrate-decision-guide/index.md) del framework di adozione del cloud per iniziare a usare questo processo.

Una migrazione incentrata su IaaS, in cui i server (insieme alle applicazioni e ai dati associati) vengono riallocati nel cloud usando macchine virtuali (VM), è spesso l'approccio più semplice per spostare i carichi di lavoro nel cloud. Considerare che la corretta configurazione, la protezione e la gestione delle VM, tuttavia, possono richiedere tempi e competenze IT superiori rispetto all'utilizzo di servizi PaaS in Azure. Se si sta valutando la possibilità di usare macchine virtuali di Azure, assicurarsi di tenere conto delle operazioni di manutenzione continua necessarie per le attività di applicazione di patch, aggiornamento e gestione relative all'ambiente di VM.

Quando si valutano i carichi di lavoro per la migrazione, identificare le applicazioni che non richiedono una modifica sostanziale per l'esecuzione con tecnologie PaaS come il Servizio app di Azure o gli agenti di orchestrazione come il servizio Azure Kubernetes. Queste app devono essere le prime candidate per la modernizzazione e l'ottimizzazione del cloud.

## <a name="learn-more"></a>Altre informazioni

- [Guida alle decisioni relative agli strumenti di migrazione del framework di adozione del cloud](../../decision-guides/migrate-decision-guide/index.md)
- [Le 5 R della razionalizzazione](../../digital-estate/5-rs-of-rationalization.md)

# <a name="planning-checklisttabchecklist"></a>[Elenco di controllo per la pianificazione](#tab/Checklist)

Prima di avviare una migrazione, è necessario completare alcuni prerequisiti. I dettagli esatti di queste attività variano a seconda dell'ambiente di cui viene eseguita la migrazione. Generalmente, viene applicato l'elenco di controllo seguente:

> [!div class="checklist"]
>
> - **Identificare gli stakeholder:** identificare le persone chiave che hanno un ruolo da svolgere o un interesse nel risultato della migrazione.
> - **Identificare le attività cardine principali:** per pianificare in modo efficace le sequenze temporali della migrazione, identificare le attività cardine da soddisfare.
> - **Identificare la strategia di migrazione:** determinare quale delle 5 R di razionalizzazione sarà usata.
> - **Valutare l'idoneità tecnica:** convalidare la preparazione tecnica e l'idoneità alla migrazione e determinare il livello di assistenza che è possibile richiedere a partner esterni o al supporto tecnico di Azure.
> - **Pianificare la migrazione:** eseguire la valutazione e la pianificazione dettagliate necessarie per preparare gli asset (infrastruttura, app e dati), nonché l'infrastruttura di Azure per la migrazione.
> - **Testare la migrazione:** convalidare il piano di migrazione eseguendo la migrazione di test con ambito limitato.
> - **Eseguire la migrazione dei servizi:** Eseguire la migrazione effettiva.
> - **Dopo la migrazione:** comprendere cosa è necessario intraprendere dopo la migrazione dell'ambiente ad Azure.

Supponendo di scegliere un approccio rehost alla migrazione, saranno rilevanti anche le attività seguenti:

> [!div class="checklist"]
>
> - **Allineamento della governance:** è stato raggiunto un consenso per l'allineamento della governance con l'impostazione della migrazione?
> - **Rete:** è necessario selezionare e allineare una strategia di rete ai requisiti di sicurezza IT.
> - **Identità:** è necessario allineare una strategia di identità ibrida per adattarsi alla gestione delle identità e al piano di adozione del cloud.

::: zone target="docs"

<!-- markdownlint-disable MD024 -->

## <a name="learn-more"></a>Altre informazioni

- [Le 5 R della razionalizzazione](../../digital-estate/5-rs-of-rationalization.md)
- [Guida alle decisioni relative agli strumenti di migrazione](../../decision-guides/migrate-decision-guide/index.md)
- [Elenco di controllo per la pianificazione del framework di adozione del cloud](../migration-considerations/prerequisites/planning-checklist.md)

::: zone-end
