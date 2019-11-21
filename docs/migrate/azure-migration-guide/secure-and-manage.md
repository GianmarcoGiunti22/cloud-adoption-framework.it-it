---
title: Protezione e gestione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Protezione e gestione
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: bd06a0e878b98ff52c7d2c5ab8a3b978758a2ef6
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251615"
---
# <a name="secure-and-manage"></a>Protezione e gestione

Dopo la migrazione di un ambiente ad Azure, è importante esaminare la sicurezza e i metodi usati per gestire l'ambiente. Azure fornisce molte funzionalità per soddisfare queste esigenze nella soluzione.

# <a name="azure-monitortabmonitor"></a>[Monitoraggio di Azure](#tab/monitor)

Monitoraggio di Azure ottimizza la disponibilità e le prestazioni delle applicazioni in uso offrendo una soluzione completa per raccogliere e analizzare la telemetria e intervenire di conseguenza dal cloud e dagli ambienti locali. È utile per ottenere informazioni sulle prestazioni delle applicazioni e identificare in modo proattivo i problemi delle applicazioni e delle risorse da cui dipendono.

## <a name="use-and-configure-azure-monitor"></a>Usare e configurare Monitoraggio di Azure

1. Passare a **Monitoraggio** nel portale di Azure.
2. Selezionare **Metriche**, **Log** o **Integrità dei servizi** per le panoramiche.
3. Selezionare le informazioni pertinenti.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Go to Azure Monitor" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

- [Panoramica di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview)

::: zone-end

# <a name="azure-service-healthtabservicehealth"></a>[Integrità dei servizi di Azure](#tab/servicehealth)

Integrità dei servizi di Azure fornisce supporto e indicazioni personalizzati quando si verificano nei servizi di Azure problemi che hanno impatto sull'utente. Può inviare notifiche, aiutare a comprendere l'impatto dei problemi e fornire informazioni aggiornate durante la risoluzione del problema. Può anche semplificare la preparazione per la manutenzione pianificata e per le modifiche che potrebbero influire sulla disponibilità delle risorse.

Integrità dei servizi di Azure include le informazioni seguenti:

- **Stato di Azure:** visualizzazione completa dell'integrità dei servizi di Azure.
- **Integrità dei servizi:** visualizzazione personalizzata dell'integrità dei servizi di Azure.
- **Integrità risorse:** visualizzazione più dettagliata dell'integrità delle singole risorse messe a disposizione dai servizi di Azure.

Combinate, queste esperienze offrono una panoramica completa dell'integrità di Azure con un livello di dettaglio pertinente per l'utente.

## <a name="access-service-health"></a>Accedere a Integrità dei servizi

1. Passare a **Monitoraggio** nel portale di Azure.
2. Selezionare **Integrità dei servizi**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/serviceIssues]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere [Documentazione di Integrità dei servizi di Azure](https://docs.microsoft.com/azure/service-health).

::: zone-end

# <a name="azure-advisortabadvisor"></a>[Azure Advisor](#tab/advisor)

Azure Advisor è un consulente cloud personalizzato che illustra come seguire le procedure consigliate per ottimizzare le distribuzioni di Azure. Analizza la configurazione e la telemetria delle risorse. Propone le soluzioni utili per migliorare le prestazioni, la sicurezza e la disponibilità elevata delle risorse, cercando al tempo stesso le opportunità ottimali per ridurre la spesa complessiva di Azure.

## <a name="access-azure-advisor"></a>Accedere ad Azure Advisor

1. Passare ad **Advisor** nel portale di Azure o cercare la risorsa.
2. Selezionare **Disponibilità elevata**, **Sicurezza**, **Prestazioni** o **Costo**

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorMenuBlade/overview]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

[Panoramica](https://docs.microsoft.com/azure/advisor/advisor-overview)

::: zone-end

# <a name="azure-security-centertabsecurity"></a>[Centro sicurezza di Azure](#tab/security)

Centro sicurezza di Azure è un sistema di gestione della sicurezza delle infrastrutture unificato che potenzia la sicurezza dei data center e fornisce protezione avanzata dalle minacce per i carichi di lavoro ibridi nel cloud, di Azure o meno, e in locale.

## <a name="access-azure-security-center"></a>Accedere a Centro sicurezza di Azure

1. Passare a **Centro sicurezza** nel portale di Azure o cercare la risorsa.
2. Selezionare **Raccomandazioni**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/0]" submitText="Go to Security Center" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

[Overview](https://docs.microsoft.com/azure/security-center/security-center-intro)

::: zone-end

# <a name="azure-backuptabbackup"></a>[Backup di Azure](#tab/backup)

Backup di Azure è il servizio basato su Azure che consente di eseguire il backup, la protezione e il ripristino dei dati in Microsoft Cloud. Backup di Azure sostituisce la soluzione di backup locale o esterna esistente con una soluzione basata sul cloud affidabile, sicura e conveniente.

## <a name="enable-backup-for-an-azure-vm"></a>Abilitare il backup per una VM di Azure

1. Nel portale di Azure selezionare **Macchine virtuali** e quindi la macchina virtuale che si vuole replicare.
1. In **Operazioni** selezionare **Backup**.
1. Creare o selezionare un insieme di credenziali di Servizi di ripristino esistente.
1. Selezionare **Crea (o modifica) un nuovo criterio**.
1. Configurare la pianificazione e il periodo di conservazione.
1. Selezionare **OK**.
1. Selezionare **Abilita backup**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

[Overview](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup)

::: zone-end

# <a name="azure-site-recoverytabsiterecovery"></a>[Azure Site Recovery](#tab/siterecovery)

All'inizio di questa guida è stato illustrato come è possibile usare Azure Site Recovery come parte dell'esecuzione della migrazione. Questo servizio è anche un componente fondamentale nella strategia di ripristino di emergenza al termine della migrazione.

Il servizio Azure Site Recovery consente di replicare in una copia ospitata in un'area secondaria le macchine virtuali e i carichi di lavoro ospitati in un'area di Azure primaria. Quando si verifica un'interruzione nell'area primaria, è possibile eseguire il failover nella copia in esecuzione nell'area secondaria e continuare ad accedere alle applicazioni e ai servizi da quest'area. Dopo la risoluzione del problema nella copia principale della macchina virtuale, è possibile eseguire il failback in tale area.

## <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Replicare una macchina virtuale di Azure in un'altra area con il servizio Site Recovery

La procedura seguente illustra come usare il servizio Site Recovery per replicare una macchina virtuale di Azure in un'altra area (da Azure ad Azure):

>
> [!TIP]
> A seconda dello scenario, la procedura esatta potrebbe essere leggermente diversa.
>

## <a name="enable-replication-for-the-azure-vm"></a>Abilitare la replica per la macchina virtuale di Azure

1. Nel portale di Azure selezionare **Macchine virtuali** e quindi la macchina virtuale che si vuole replicare.
1. In **Operazioni** selezionare **Ripristino di emergenza**.
1. In **Configure disaster recovery** (Configura ripristino di emergenza)  >  **Area di destinazione** selezionare l'area di destinazione in cui si vuole eseguire la replica.
1. Per questa guida introduttiva, accettare le altre impostazioni predefinite.
1. Selezionare **Abilita replica**. Verrà avviato un processo per abilitare la replica per la macchina virtuale.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

## <a name="verify-settings"></a>Verificare le impostazioni

Al termine del processo di replica, è possibile controllare lo stato della replica, verificarne l'integrità e testare la distribuzione.

1. Nel menu della macchina virtuale selezionare **Ripristino di emergenza**.
2. Verificare l'integrità della replica, i punti di ripristino creati, nonché le aree di origine e di destinazione sulla mappa.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Altre informazioni

- [Panoramica di Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Replicare una macchina virtuale di Azure in un'altra area](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

::: zone-end
