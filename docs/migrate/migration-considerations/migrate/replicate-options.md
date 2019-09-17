---
title: Opzioni di replica
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione nel cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7433ddd9a1c3bb6bd62f9d065c79bbb0b1f52f1b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022713"
---
# <a name="replication-options"></a>Opzioni di replica

Prima della migrazione, è necessario assicurarsi che i sistemi primari siano sicuri e che continueranno a essere eseguiti senza problemi. Qualsiasi tempo di inattività interrompe utenti o clienti e comporta maggiori costi in termini di tempo e denaro. La migrazione non è semplice come spegnere le macchine virtuali in locale e copiarle in Azure. Gli strumenti di migrazione devono tenere conto della replica asincrona o sincrona per garantire che i sistemi attivi possano essere copiati in Azure senza tempi di inattività. Nella maggior parte dei casi, i sistemi devono essere conservati in contemporanea con controparti locali. Potrebbe essere necessario testare le risorse migrate in partizioni isolate in Azure, per garantire che i carichi di lavoro funzionino come previsto.

Il contenuto all'interno del framework di adozione del cloud presuppone che Azure Migrate (o Azure Site Recovery) sia lo strumento più appropriato per la replica di asset nel cloud. Tuttavia, sono disponibili altre opzioni. Questo articolo illustra le opzioni che consentono di eseguire il processo decisionale.

## <a name="azure-site-recovery-also-known-as-azure-migrate"></a>Azure Site Recovery (noto anche come Azure Migrate)

[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) orchestra e gestisce il ripristino di emergenza per le Macchine virtuali di Azure, i server fisici e le macchine virtuali locali. È anche possibile usare Site Recovery per gestire la migrazione di computer locali e di altri provider di servizi cloud in Azure. Eseguire la replica dei computer locali in Azure o delle Macchine virtuali di Azure in un'area secondaria. Eseguire quindi il failover della VM dal sito primario al secondario e completare il processo di migrazione. Con Azure Site Recovery, è possibile realizzare diversi scenari di migrazione:

- **Eseguire la migrazione da locale ad Azure.** Eseguire la migrazione da macchine virtuali VMware, macchine virtuali Hyper-V e server fisici locali ad Azure. A tale scopo, effettuare una procedura simile a quella che si esegue per un ripristino di emergenza completo. Semplicemente non si esegue il failback dei computer da Azure al sito locale.
- **Eseguire la migrazione tra aree di Azure.** Migrare le Macchine virtuali di Azure da un'area di Azure a un'altra. Una volta completata la migrazione, configurare il ripristino di emergenza per le VM di Azure nell'area secondaria in cui è eseguita la migrazione.
- **Eseguire la migrazione da un altro cloud ad Azure.** È possibile eseguire la migrazione delle istanze di calcolo di cui è stato effettuato il provisioning in altri provider di servizi cloud in Macchine virtuali di Azure. Ai fini della migrazione, Site Recovery gestisce queste istanze come i server fisici.

![Azure Site Recovery](../../../_images/migrate/asr-replication-image.png)
*Azure Site Recovery trasferisce asset in Azure o in altri cloud*

Dopo aver valutato l'infrastruttura locale e cloud per la migrazione, Azure Site Recovery contribuisce alla strategia di migrazione tramite la replica di computer locali. Con i semplici passaggi seguenti è possibile configurare la migrazione di macchine virtuali locali, server fisici e istanze di VM cloud in Azure:

- Verificare i prerequisiti.
- Preparare le risorse di Azure.
- Preparare le istanze di macchine virtuali o cloud locali per la migrazione.
- Distribuire un server di configurazione.
- Abilitare la replica per le VM.
- Eseguire un failover di test per verificare che tutto funzioni correttamente.
- Eseguire un unico failover in Azure.

## <a name="azure-database-migration-service"></a>Azure Database Migration Service

Questo servizio consente di ridurre la complessità della migrazione al cloud usando un singolo servizio completo invece di tanti strumenti diversi. Il [Servizio Migrazione del database di Azure](https://docs.microsoft.com/azure/dms/dms-overview) è stato progettato come soluzione end-to-end senza problemi per il trasferimento di database di SQL Server locali sul cloud. È un servizio completamente gestito progettato per abilitare le migrazioni senza interruzioni da più origini di database alle piattaforme di dati di Azure con tempi di inattività minimi. Integra alcune funzionalità degli strumenti e dei servizi esistenti, offrendo ai clienti una soluzione completa e a disponibilità elevata.

Il servizio usa Data Migration Assistant per generare report di valutazione che offrono indicazioni utili in merito alle modifiche necessarie prima di eseguire una migrazione. È compito dell'utente eseguire le correzioni necessarie. Quando si è pronti per iniziare il processo di migrazione, il Servizio Migrazione del database di Azure esegue tutti i passaggi associati. È possibile avviare i progetti di migrazione con tranquillità sapendo che il processo si avvale delle procedure consigliate stabilite da Microsoft.

## <a name="next-steps"></a>Passaggi successivi

Al termine della replica, è possibile iniziare le [attività di gestione temporanea](./stage.md).

> [!div class="nextstepaction"]
> [Attività di gestione temporanea durante una migrazione](./stage.md)
