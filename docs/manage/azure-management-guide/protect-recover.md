---
title: Protezione e ripristino in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Assicurare la stabilità aziendale riducendo i tempi di ripristino
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 83ac1abd6ce35b62f64722d101f599726c7b26b3
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565423"
---
# <a name="protect-and-recover-in-azure"></a>Protezione e ripristino in Azure

La terza e ultima disciplina di una baseline di gestione del cloud riguarda _protezione e ripristino_.

![Baseline di gestione del cloud](../../_images/manage/management-baseline.png)

Nell'articolo [Conformità operativa in Azure](./operational-compliance.md) l'obiettivo è ridurre la probabilità che si verifichi un'interruzione per il business. L'articolo corrente mira a ridurre la durata e l'impatto delle interruzioni che non è possibile prevenire.

Per qualsiasi ambiente di livello aziendale, la tabella seguente include il minimo consigliato per qualsiasi baseline di gestione:

|Process  |Strumento  |Scopo  |
|---------|---------|---------|
|Proteggere i dati|Backup di Azure|Eseguire il backup di dati e macchine virtuali nel cloud.|
|Proteggere l'ambiente|Centro sicurezza di Azure|Rafforzare la sicurezza e offrire una protezione avanzata dalle minacce nei carichi di lavoro ibridi.|

::: zone target="docs"

## <a name="azure-backup"></a>Backup di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-backuptabupdbackupatemanagement"></a>[Backup di Azure](#tab/UpdbackupateManagement)

::: zone-end

Con Backup di Azure è possibile il backup e il ripristino dei dati, oltre a proteggerli, nel cloud Microsoft. Backup di Azure sostituisce la soluzione di backup locale o esterna esistente con una soluzione basata sul cloud. Questa nuova soluzione è affidabile, sicura e conveniente. Backup di Azure può anche essere usato per proteggere e ripristinare gli asset locali tramite un'unica soluzione coerente.

### <a name="enable-backup-for-an-azure-vm"></a>Abilitare il backup per una VM di Azure

1. Nel portale di Azure selezionare **Macchine virtuali** e quindi la macchina virtuale che si vuole replicare.
1. Nel riquadro **Operazioni** selezionare **Backup**.
1. Creare o selezionare un insieme di credenziali di Servizi di ripristino di Azure esistente.
1. Selezionare **Crea (o modifica) un nuovo criterio**.
1. Configurare la pianificazione e il periodo di conservazione.
1. Selezionare **OK**.
1. Selezionare **Abilita backup**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

[Overview](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup)

## <a name="azure-site-recovery"></a>Azure Site Recovery

::: zone-end
::: zone target="chromeless"

## <a name="azure-site-recoverytabsiterecovery"></a>[Azure Site Recovery](#tab/siterecovery)

::: zone-end

Azure Site Recovery è un componente fondamentale della strategia di ripristino di emergenza.

Site Recovery replica le VM e i carichi di lavoro ospitati in un'area di Azure primaria. La replica avviene in una copia ospitata in un'area secondaria. Quando si verifica un'interruzione nell'area primaria, viene eseguito il failover nella copia in esecuzione nell'area secondaria. È quindi possibile continuare ad accedere alle applicazioni e ai servizi da questa posizione. Questo approccio proattivo può ridurre significativamente i tempi di ripristino. Quando l'ambiente di ripristino non è più necessario, il traffico di produzione può tornare nell'ambiente originale.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery"></a>Replicare una VM di Azure in un'altra area con il servizio Site Recovery

La procedura seguente illustra come usare il servizio Site Recovery per eseguire una replica da Azure ad Azure, ossia una replica di una VM di Azure in un'altra area.
>
> [!TIP]
> A seconda dello scenario, la procedura esatta potrebbe essere leggermente diversa.
>

### <a name="enable-replication-for-the-azure-vm"></a>Abilitare la replica per la macchina virtuale di Azure

1. Nel portale di Azure selezionare **Macchine virtuali** e quindi la macchina virtuale che si vuole replicare.
1. Nel riquadro **Operazioni** selezionare **Ripristino di emergenza**.
1. Selezionare **Configura ripristino di emergenza** > **Area di destinazione** e scegliere l'area di destinazione per la replica.
1. Per questo argomento di avvio rapido, accettare i valori predefiniti per tutte le altre opzioni.
1. Selezionare **Abilita replica** per avviare un processo per abilitare la replica per la macchina virtuale.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Verificare le impostazioni

Al termine del processo di replica, è possibile controllare lo stato della replica, verificarne l'integrità e testare la distribuzione.

1. Nel menu della macchina virtuale selezionare **Ripristino di emergenza**.
1. Verificare l'integrità della replica, i punti di ripristino creati, nonché le aree di origine e di destinazione sulla mappa.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="learn-more"></a>Altre informazioni

- [Panoramica di Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Replicare una macchina virtuale di Azure in un'altra area](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
