---
title: Meccanismi di controllo dei costi incentrati sulla migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come configurare budget e pagamenti e comprendere le fatture per le risorse di Azure.
author: bandersmsft
ms.author: banders
ms.date: 08/08/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 38e412bda80e68b0c5cb7e53ad52c078fa39f8fb
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378422"
---
# <a name="migration-focused-cost-control-mechanisms"></a>Meccanismi di controllo dei costi incentrati sulla migrazione

Il cloud ha introdotto alcuni cambiamenti relativi al modo in cui si lavora, indipendentemente dal ruolo che si svolge all'interno del team tecnologico. I costi sono un esempio significativo di tale cambiamento. In passato solo i responsabili finanziari e IT si preoccupavano del costo degli asset IT (infrastruttura, app e dati). Il cloud consente a tutti i membri dell'IT di prendere le decisioni che meglio supportano l'utente finale. Tuttavia, insieme a questa capacità, si riceve la responsabilità di essere attenti ai costi quando si prendono tali decisioni.

In questo articolo vengono introdotti gli strumenti che consentono di prendere decisioni tenendo conto dei costi prima, durante e dopo una migrazione ad Azure.

Gli strumenti descritti in questo articolo sono:

> - Azure Migrate
> - Calcolatore prezzi di Azure
> - Calcolatore del costo totale di proprietà di Azure
> - Gestione costi di Azure
> - Azure Advisor

I processi descritti in questo articolo possono richiedere anche una collaborazione con i responsabili IT, il reparto finanza o i proprietari di applicazioni line-of-business. Per indicazioni relative alla collaborazione con tali ruoli, vedere l'articolo di Cloud Adoption Framework su come costituire un'organizzazione attenta ai costi (previsto per il terzo trimestre del 2019).

<!-- markdownlint-disable MD024 MD025 -->

# <a name="estimate-vm-costs-prior-to-migrationtabestimatevmcosts"></a>[Stimare i costi delle macchine virtuali prima della migrazione](#tab/EstimateVMCosts)

Prima di eseguire la migrazione di qualsiasi asset (infrastruttura, app o dati), è possibile stimare i costi e perfezionare il dimensionamento in base ai criteri di prestazioni osservati per tali asset. La stima dei costi ha due scopi: consente il controllo dei costi e fornisce un checkpoint per garantire che i budget correnti siano in grado di soddisfare i requisiti di prestazioni necessari.

## <a name="cost-calculators"></a>Calcolatori dei costi

Per i calcoli manuali dei costi, sono disponibili due pratici calcolatori che possono fornire una rapida stima dei costi basata sull'architettura del carico di lavoro di cui eseguire la migrazione.

- Il [calcolatore prezzi](https://azure.microsoft.com/pricing/calculator) di Azure fornisce stime dei costi in base ai prodotti di Azure immessi manualmente.
- Le decisioni a volte richiedono un confronto tra i costi futuri per il cloud e i costi locali correnti. Il [calcolatore del costo totale di proprietà (TCO)](https://azure.microsoft.com/pricing/tco/calculator) può fornire tale confronto.

Questi calcolatori dei costi manuali possono essere usati in modo autonomo per prevedere la spesa e i risparmi potenziali. Possono anche essere usati insieme agli strumenti di previsione dei costi di Azure Migrate per regolare le aspettative di costo in modo da adattarsi ad architetture alternative o a vincoli di prestazioni.

## <a name="azure-migrate-calculations"></a>Calcoli di Azure Migrate

**Prerequisiti:** il resto di questa scheda presuppone che il lettore abbia già popolato Azure Migrate con una raccolta di asset (infrastruttura, app e dati) di cui eseguire la migrazione. L'articolo precedente sulle valutazioni fornisce le istruzioni per la raccolta dei dati iniziali. Dopo aver inserito i dati, seguire i passaggi successivi per stimare i costi mensili in base ai dati raccolti.

Azure Migrate calcola le **stime dei costi mensili** in base ai dati acquisiti dall'agente di raccolta e da Mapping dei servizi. La procedura seguente consentirà di caricare le stime dei costi:

1. Passare al pannello Valutazione di Azure Migrate nel portale.
1. Nella pagina **Panoramica** del progetto selezionare **+Crea valutazione**.
1. Fare clic su **Visualizza tutto** per rivedere le proprietà di valutazione.
1. Creare il gruppo e specificarne il nome.
1. Selezionare le macchine virtuali da aggiungere al gruppo.
1. Fare clic su **Crea valutazione** per creare il gruppo e la valutazione.
1. Dopo aver creato la valutazione, visualizzarla in Panoramica > Dashboard.
1. Nella sezione Dettagli valutazione del pannello di spostamento selezionare **Dettagli dei costi**.

La stima risultante, illustrata di seguito, identifica i costi mensili di calcolo e archiviazione, che spesso rappresentano la parte più significativa dei costi del cloud.

![compute-storage-monthly-cost-estimate.png](./media/manage-costs/compute-storage-monthly-cost-estimate.png)
*Figura 1 - Immagine della visualizzazione Dettagli dei costi di una valutazione in Azure Migrate.*

## <a name="additional-resources"></a>Risorse aggiuntive

- [Configurare ed esaminare una valutazione con Azure Migrate](https://docs.microsoft.com/azure/migrate/tutorial-assess-vmware#set-up-an-assessment)
- Per un piano più completo sulla gestione dei costi in un numero maggiore di asset (infrastruttura, app e dati), vedere il [modello di governance di Cloud Adoption Framework](../../govern/guides/index.md). In particolare, vedere le indicazioni relative alla [disciplina Gestione costi](../../govern/cost-management/index.md) e al [miglioramento di Gestione costi nella guida alla governance per aziende complesse](../../govern/guides/complex/cost-management-improvement.md).

# <a name="estimate-and-optimize-vm-costs-during-and-after-migrationtabestimateoptimize"></a>[Stimare e ottimizzare i costi delle macchine virtuali durante e dopo la migrazione](#tab/EstimateOptimize)

La stima dei costi prima della migrazione costituisce un solido riferimento per le aspettative sui costi. Offre inoltre la possibilità di prendere in considerazione le esigenze in termini di prestazioni e costi di ogni asset (infrastruttura, app e dati) di cui eseguire la migrazione. Tuttavia, si tratta comunque di una stima. Dopo aver eseguito la migrazione dell'asset e averlo sottoposto a carico, è possibile eseguire calcoli più accurati sui costi in base al carico effettivo o sintetizzato.

## <a name="azure-advisor-cost-recommendations"></a>Consigli di Azure Advisor sui costi

Entro 24 ore dalla migrazione degli asset (infrastruttura, app e dati) ad Azure, Azure Advisor inizia a monitorare le prestazioni di ogni asset per fornire un feedback sull'asset in questione. Un elemento di feedback raccolto è relativo al saldo tra i costi e l'utilizzo.

La procedura seguente fornisce consigli sui costi per gli asset (infrastruttura, app e dati) nelle sottoscrizioni correnti:

1. Passare al pannello di **Azure Advisor** nel portale. A tale scopo, selezionare **Advisor** nel riquadro di spostamento sinistro del portale di Azure. Se Advisor non è visibile nel riquadro sinistro, selezionare **Tutti i servizi**. Nel riquadro del menu dei servizi, in **Monitoraggio e gestione**, selezionare **Advisor**.
1. Nel dashboard di Advisor viene visualizzato un riepilogo dei consigli per tutte le sottoscrizioni selezionate. È possibile scegliere le sottoscrizioni per le quali si vuole ottenere i consigli usando come filtro il menu a discesa delle sottoscrizioni.
1. Per visualizzare i consigli sui costi, fare clic sulla scheda Costo.

## <a name="azure-cost-management"></a>Gestione costi di Azure

Gestione costi di Azure può offrire una panoramica più olistica delle abitudini di spesa, tra cui la vista dettagliata dei costi e delle tendenze di spesa nel tempo. Per le migrazioni complesse o di grandi dimensioni, questa vista può fornire le informazioni necessarie per prendere decisioni di ampia portata sulla gestione dei costi.

Prerequisiti: il resto di questa scheda presuppone che il lettore abbia completato la configurazione di Gestione costi di Azure durante il completamento della guida alla configurazione di Azure. Per altri dettagli sulla configurazione di Gestione costi di Azure, vedere questo [articolo nella guida alla configurazione di Azure](../../ready/azure-setup-guide/manage-costs.md). Dopo aver inserito i dati, seguire i passaggi successivi per stimare i costi mensili in base ai dati raccolti.

La procedura seguente consentirà di caricare i dati di analisi dei costi di Gestione costi di Azure per le sottoscrizioni:

1. Passare al pannello **Gestione costi e fatturazione** nel portale. Se Gestione costi e fatturazione non è visibile nel riquadro sinistro, fare clic su **Tutti i servizi**. Nel riquadro del menu dei servizi, in **Monitoraggio e gestione**, fare clic su **Gestione costi e fatturazione**.
1. Nel pannello Gestione costi e fatturazione selezionare **Gestione costi** nel riquadro di spostamento sinistro del pannello aperto per iniziare ad analizzare e ottimizzare i costi del cloud.
1. Nel pannello Gestione costi selezionare **Analisi dei costi**.
    1. Usare l'etichetta **Ambito** per passare a un ambito diverso nell'analisi dei costi.

Questa analisi consentirà di esaminare i costi totali, il budget (se disponibile) e i costi accumulati. Ogni calcolo può essere visualizzato per servizio, per risorsa e nel tempo. L'aspetto ancora più importante è rappresentato dal fatto che i costi possono essere analizzati in base ai tag. L'assegnazione di nomi e tag appropriati agli asset (infrastruttura, app e dati) è il punto di partenza fondamentale di tutti i processi affidabili di governance e gestione dei costi. I tag appropriati consentono una migliore gestione dei costi e una percezione più chiara dell'impatto delle ottimizzazioni delle prestazioni e dei costi.

## <a name="additional-resources"></a>Risorse aggiuntive

- Per un piano più completo sulla gestione dei costi in un numero maggiore di asset (infrastruttura, app e dati), vedere il [modello di governance di Cloud Adoption Framework](../../govern/guides/index.md). In particolare, vedere le indicazioni relative alla [disciplina Gestione costi](../../govern/cost-management/index.md) e al [miglioramento incrementale di Gestione costi nella guida alla governance per aziende complesse](../../govern/guides/complex/cost-management-improvement.md).
- Per altre informazioni su Azure Advisor, vedere [Ridurre i costi del servizio con Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations).
- Per altre informazioni su Gestione costi di Azure, vedere [Comprendere e utilizzare gli ambiti](https://docs.microsoft.com/azure/cost-management/understand-work-scopes) ed [Esplorare e analizzare i costi con l'analisi dei costi](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis).

# <a name="tips-and-tricks-to-optimize-coststabtipstricks"></a>[Suggerimenti e consigli per ottimizzare i costi](#tab/TipsTricks)

Oltre agli strumenti indicati in questo articolo, sono disponibili alcuni suggerimenti e consigli che possono risultare utili per ridurre rapidamente i costi complessivi del cloud. Di seguito sono riportati alcuni suggerimenti di carattere generale da tenere presenti:

## <a name="avoid-unnecessary-spending"></a>Evitare le spese non necessarie

La maggior parte degli asset (infrastruttura, app e dati) in un data center esistente può essere teoricamente migrata al cloud. Ciò non significa tuttavia che sia necessario eseguirne la migrazione. Durante la valutazione di ogni carico di lavoro, verificare che sia necessario eseguire la migrazione del carico di lavoro in questione. L'articolo di Cloud Adoption Framework sulla [razionalizzazione incrementale](../../digital-estate/rationalize.md) può essere utile per determinare gli asset di cui eseguire la migrazione.

## <a name="reduce-waste"></a>Ridurre gli sprechi

Dopo aver distribuito l'infrastruttura in Azure, è importante assicurarsi che sia in uso. Il modo più semplice per iniziare subito a risparmiare è analizzare le risorse e rimuovere quelle non in uso

## <a name="reduce-overprovisioning"></a>Ridurre il provisioning eccessivo

Anche con gli approcci migliori alla stima, è probabile che siano presenti asset (infrastruttura, app e dati) con provisioning eccessivo e asset sottoutilizzati. L'esame di tali asset tramite gli strumenti nelle due schede precedenti consente di identificare i possibili metodi di riduzione delle dimensioni degli asset per ottenere una migliore corrispondenza ai requisiti di prestazioni e ridurre i costi.

## <a name="take-advantage-of-available-discounts"></a>Sfruttare gli sconti disponibili

Rivolgersi al rappresentante Microsoft per comprendere come sfruttare le opzioni di sconto correnti. Di seguito sono riportati alcuni esempi di sconti usati comunemente per ridurre i costi.

## <a name="azure-reservations"></a>Prenotazioni di Azure

Le [prenotazioni di Azure](https://docs.microsoft.com/azure/billing/billing-save-compute-costs-reservations) consentono di effettuare il pagamento anticipato della capacità di calcolo delle macchine virtuali o dei database SQL per un periodo di uno o tre anni. Il pagamento anticipato consentirà di ottenere uno sconto sulle risorse usate. Le prenotazioni di Azure possono ridurre in modo significativo i costi di calcolo delle macchine virtuali o dei database SQL, ovvero fino al 72% rispetto ai prezzi con pagamento in base al consumo, a fronte di un impegno anticipato di uno o tre anni. Le prenotazioni offrono uno sconto a livello di fatturazione e non hanno alcuna ripercussione sullo stato di runtime delle macchine virtuali o dei database SQL.

## <a name="use-azure-hybrid-benefit"></a>Usare il vantaggio Azure Hybrid

Se si hanno già licenze di Windows Server o SQL Server nelle distribuzioni locali, è possibile usare il programma [Vantaggio Azure Hybrid](https://azure.microsoft.com/pricing/hybrid-benefit) per risparmiare in Azure. Con il vantaggio per Windows Server, ogni licenza copre il costo del sistema operativo (fino a un massimo di due macchine virtuali) e si pagano semplicemente i costi di calcolo di base. È possibile usare le licenze esistenti di SQL Server per risparmiare fino al 55% sulle opzioni di database SQL basate su vCore. Le opzioni includono SQL Server in Macchine virtuali di Azure e SQL Server Integration Services.

## <a name="low-priority-vms-with-batch"></a>Macchine virtuali con priorità bassa con Batch

Per i processi in background con priorità più bassa, Batch consente di gestire le macchine virtuali del servizio in background e ridurre i costi. È tuttavia importante comprendere l'effetto sulle prestazioni delle [macchine virtuali con priorità bassa con Batch](https://docs.microsoft.com/azure/batch/batch-low-pri-vms) prima di scegliere questa opzione scontata.

## <a name="additional-resources"></a>Risorse aggiuntive

Per un piano più completo sulla gestione dei costi in un numero maggiore di asset (infrastruttura, app e dati), vedere il [modello di governance di Cloud Adoption Framework](../../govern/guides/index.md). In particolare, vedere le indicazioni relative alla [disciplina Gestione costi](../../govern/cost-management/index.md) e al [miglioramento incrementale di Gestione costi nella guida alla governance per aziende complesse](../../govern/guides/complex/cost-management-improvement.md).
