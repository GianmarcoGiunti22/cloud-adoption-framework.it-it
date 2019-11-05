---
title: Accelerazione della migrazione con gli host VMWare
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Accelerazione della migrazione con gli host VMWare
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 66a39d53adeaf73e96cf04bdc5f80fc9574b675a
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72980203"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Accelerazione della migrazione con gli host VMWare

La migrazione di interi host VMWare può spostare più carichi di lavoro e diversi asset in un'unica operazione di migrazione. Le linee guida seguenti consentono di espandere l'ambito della [Guida alla migrazione di Azure](../azure-migration-guide/index.md) tramite una migrazione di host VMware. La maggior parte degli sforzi richiesti in questa espansione dell'ambito si verifica durante i prerequisiti e i processi di migrazione di un'operazione di migrazione.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

Quando si esegue la migrazione del primo host VMWare ad Azure, è necessario soddisfare una serie di prerequisiti per preparare i requisiti di identità, rete e gestione. Una volta soddisfatti questi prerequisiti, per eseguire la migrazione di ogni host aggiuntivo dovrebbe essere necessaria una quantità di risorse notevolmente inferiore. Le sezioni seguenti forniscono maggiori dettagli sui prerequisiti.

### <a name="secure-your-azure-environment"></a>Proteggere l'ambiente Azure

Implementare la soluzione cloud appropriata per il controllo degli accessi in base al ruolo e la connettività di rete nell'ambiente Azure. La [Guida sicura dell'ambiente](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) può essere utile per questa implementazione.

### <a name="private-cloud-management"></a>Gestione del cloud privato

Sono necessarie due attività e un'attività facoltativa per definire la gestione del cloud privato. L' [escalation dei privilegi del cloud privato](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) e del [DNS del carico di lavoro e della configurazione DHCP sono le](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) procedure consigliate.

Se l'obiettivo è [eseguire la migrazione dei carichi di lavoro usando reti estese di livello 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json), è necessaria anche questa terza procedura consigliata.

### <a name="private-cloud-networking"></a>Funzionalità di rete del cloud privato

Una volta stabiliti i requisiti di gestione, è possibile stabilire la rete cloud privata utilizzando le procedure consigliate seguenti:

- [Connessione VPN al cloud privato](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connessione alla rete locale con ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connessione alla rete virtuale di Azure con ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare la risoluzione dei nomi DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Integrazione con il piano di adozione del cloud

Dopo aver soddisfatto gli altri prerequisiti, è necessario includere ogni host VMWare nel piano di adozione del [cloud](../../plan/template.md). Nel piano di adozione del cloud aggiungere ogni host da migrare come [carico di lavoro distinto](../../plan/workloads.md). All'interno di ogni carico di lavoro aggiungere le macchine virtuali da migrare come [Asset](../../plan/workloads.md). Per aggiungere i carichi di lavoro e le risorse al piano di adozione in blocco, vedere [aggiunta/modifica di elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Durante ogni iterazione, il team di adozione usa il backlog per eseguire la migrazione dei carichi di lavoro con priorità più elevata. Il processo non cambia realmente per gli host VMWare. Quando il carico di lavoro successivo nel backlog è un host VMWare, l'unica modifica sarà lo strumento utilizzato.

È possibile usare gli strumenti seguenti nell'operazione di migrazione:

- [Strumenti VMWare nativi](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

In alternativa, è possibile eseguire la migrazione dei carichi di lavoro tramite un failover di ripristino di emergenza utilizzando gli strumenti seguenti:

- [Eseguire il backup di macchine virtuali del carico di lavoro](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare il cloud privato come sito di ripristino di emergenza con Zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare il cloud privato come sito di ripristino di emergenza con VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Passaggi successivi

Tornare all'elenco di controllo dell'ambito espanso per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
