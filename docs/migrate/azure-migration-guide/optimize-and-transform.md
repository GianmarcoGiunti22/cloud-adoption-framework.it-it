---
title: Ottimizzazione e trasformazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ottimizzazione e trasformazione
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: e6c5f0aa120339ecd2c3a968503b5ee0be824307
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024738"
---
# <a name="optimize-and-transform"></a>Ottimizzazione e trasformazione

Ora che i servizi sono stati migrati in Azure, la fase successiva include la revisione della soluzione per le possibili aree di ottimizzazione. Questo potrebbe includere la revisione della progettazione della soluzione, il ridimensionamento corretto dei servizi e l'analisi dei costi.

Questa fase è anche un'opportunità per ottimizzare l'ambiente ed eseguire possibili trasformazioni dell'ambiente. Ad esempio, è possibile che sia stata eseguita una migrazione "rehost" e ora che i servizi sono in esecuzione in Azure è possibile riesaminare la configurazione delle soluzioni o i servizi usati ed eventualmente eseguire un "refactoring" per modernizzare e aumentare la funzionalità del soluzione.

# <a name="right-size-assetstaboptimize"></a>[Ridimensionamento corretto](#tab/optimize)

Tutti i servizi di Azure che forniscono un modello di costo basato sul consumo possono essere ridimensionati tramite il portale di Azure, l'interfaccia della riga di comando o PowerShell. La prima fase per dimensionare correttamente un servizio consiste nel verificarne le metriche di utilizzo. Il servizio Monitoraggio di Azure consente di accedere a queste metriche. Potrebbe essere necessario configurare la raccolta delle metriche per il servizio che si sta analizzando e considerare un momento appropriato per raccogliere dati significativi in base ai modelli del carico di lavoro.

1. Passare a **Monitoraggio**.
1. Selezionare **Metriche** e configurare il grafico per visualizzare le metriche per il servizio da analizzare.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/metrics]" submitText="Go to Monitor" :::

::: zone-end

Di seguito sono riportati alcuni servizi comuni che è possibile ridimensionare.

## <a name="resize-a-virtual-machine"></a>Ridimensionare una macchina virtuale

Azure Migrate esegue un'analisi di ridimensionamento corretto come parte della fase di valutazione della premigrazione. Le macchine virtuali di cui è stata eseguita la migrazione tramite questo strumento saranno probabilmente già ridimensionate in base ai requisiti di premigrazione.

Tuttavia, per le macchine virtuali create o migrate con altri metodi o nei casi in cui è necessario modificare i requisiti della macchina virtuale post-migrazione, è possibile ottimizzare ulteriormente il ridimensionamento della macchina virtuale.

1. Passare a **Macchine virtuali**.
1. Selezionare la macchina virtuale da usare dall'elenco.
1. Selezionare **Dimensioni** e le nuove dimensioni da usare dall'elenco. Potrebbe essere necessario modificare i filtri per individuare le dimensioni necessarie.
1. Selezionare **Ridimensiona**.

Si noti che il ridimensionamento delle macchine virtuali di produzione può causare l'interruzione del servizio. Provare ad applicare il ridimensionamento corretto per le macchine virtuali prima di promuoverle alla produzione.


::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

- [Gestire le prenotazioni per le risorse di Azure](https://docs.microsoft.com/azure/billing/billing-manage-reserved-vm-instance)
- [Ridimensionare una macchina virtuale Windows](https://docs.microsoft.com/azure/virtual-machines/windows/resize-vm)
- [Ridimensionare una macchina virtuale Linux tramite l'interfaccia della riga di comando di Azure](https://docs.microsoft.com/azure/virtual-machines/linux/change-vm-size)

I partner possono usare il Centro per i partner per esaminare l'utilizzo.

- [Ridimensionamento della macchina virtuale di Microsoft Azure per l'utilizzo massimo delle prenotazioni](https://docs.microsoft.com/partner-center/azure-usage)

::: zone-end

## <a name="resize-a-storage-account"></a>Ridimensionare un account di archiviazione

1. Passare a **Account di archiviazione**.
1. Selezionare l'account di archiviazione da usare.
1. Selezionare **Configura** e modificare le proprietà dell'account di archiviazione in base ai requisiti.
1. Selezionare **Salva**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Storage%2FStorageAccounts]" submitText="Go to Storage Accounts" :::

::: zone-end

## <a name="resize-a-sql-database"></a>Ridimensionare un Database SQL

1. Passare a **Database SQL** o **SQL Server** e quindi selezionare il server.
1. Selezionare il database da usare.
1. Selezionare **Configura** e le nuove dimensioni del livello di servizio da usare.
1. Selezionare **Applica**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Sql%2Fservers%2Fdatabases]" submitText="Go to SQL Databases" :::

::: zone-end

# <a name="cost-managementtabmanagecost"></a>[Gestione dei costi](#tab/ManageCost)

È importante eseguire analisi dei costi periodiche ed esaminarle. Questo consentirà di ridimensionare le risorse in base alle proprie esigenze per bilanciare il carico di lavoro e i costi.

Gestione costi di Azure funziona con Azure Advisor per fornire elementi consigliati di ottimizzazione dei costi. Azure Advisor consente di ottimizzare e migliorare l'efficienza identificando le risorse inattive e sottoutilizzate.

1. Selezionare **Gestione dei costi e fatturazione**.
1. Selezionare **Raccomandazioni Advisor** e la scheda **Costi**.
1. Usare l'**Impatto** e il **Risparmio annuale potenziale** per esaminare i potenziali vantaggi.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/ModernBillingMenuBlade/Overview]" submitText="Go to Cost Management + Billing" :::

::: zone-end

È anche possibile usare **Advisor** e selezionare la scheda **Costi** per identificare le raccomandazioni per le potenziali riduzioni dei costi.

> [!TIP]
> Per i servizi che non richiedono una disponibilità continua, l'implementazione di una soluzione per avviare, arrestare o sospendere il servizio in base alle proprie esigenze può aiutare a gestire il costo (ad esempio, Macchine virtuali di Azure o Azure SQL Data Warehouse).
>

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

- [Esercitazione: Ottimizzare i costi grazie agli elementi consigliati](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations)
- [Evitare addebiti imprevisti con la gestione dei costi e della fatturazione di Azure](https://docs.microsoft.com/azure/billing/billing-getting-started)
- [Esplorare e analizzare i costi con l'analisi dei costi](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis)

::: zone-end
