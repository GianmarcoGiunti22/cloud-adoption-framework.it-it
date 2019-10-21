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
ms.openlocfilehash: b09c1dcbb36e5f630ca0ae86c95c5c874e29d60b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558207"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Accelerazione della migrazione con gli host VMWare

La migrazione di interi host VMWare può spostare più carichi di lavoro e diversi asset in un'unica operazione di migrazione. Le linee guida seguenti consentono di espandere l'ambito della [Guida alla migrazione di Azure](../azure-migration-guide/index.md) tramite una migrazione di host VMware.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

La maggior parte di questa operazione necessaria in questo ambito si verificherà durante i prerequisiti e i processi di migrazione di un'operazione di migrazione.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

Quando si esegue la migrazione del primo host VMWare ad Azure, esistono diversi prerequisiti che devono essere soddisfatti per preparare i requisiti di identità, rete e gestione. Una volta soddisfatti questi prerequisiti, ogni host aggiuntivo dovrebbe richiedere un minor sforzo di migrazione. Questi prerequisiti sono allineati ad alcuni sforzi chiave: proteggere l'ambiente di Azure, la gestione del cloud privato e la rete cloud privata.

### <a name="secure-your-azure-environment"></a>Proteggere l'ambiente Azure

Implementare la soluzione cloud appropriata per RBAC e la connettività di rete nell'ambiente Azure. La [Guida sicura dell'ambiente](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) può essere utile per questa implementazione.

### <a name="private-cloud-management"></a>Gestione del cloud privato

Sono necessarie due attività e un'attività facoltativa per definire la gestione del cloud privato. L' [escalation dei privilegi del cloud privato](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) e del [DNS del carico di lavoro e della configurazione DHCP sono le](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) procedure consigliate.

Se l'obiettivo è [eseguire la migrazione dei carichi di lavoro usando reti estese di livello 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json), questa terza procedura consigliata sarà obbligatoria.

### <a name="private-cloud-networking"></a>Rete cloud privata

Una volta stabiliti i requisiti di gestione, è possibile stabilire la rete del cloud privato utilizzando le seguenti procedure consigliate:

- [Connessione VPN al cloud privato](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connessione alla rete locale con ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connessione alla rete virtuale di Azure con ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare la risoluzione dei nomi DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Integrazione con il piano di adozione del cloud

Una volta soddisfatti i prerequisiti, ogni host VMWare verrà incluso nel piano di adozione del [cloud](../../plan/template.md). Nel piano di adozione del cloud aggiungere ogni host da migrare come [carico di lavoro distinto](../../plan/workloads.md). All'interno di ogni carico di lavoro, le macchine virtuali da migrare possono essere aggiunte come [Asset](../../plan/workloads.md). Per aggiungere in blocco i carichi di lavoro e le risorse al piano di adozione, vedere [aggiunta/modifica di elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Durante ogni iterazione, il team di adozione usa il backlog per eseguire la migrazione dei carichi di lavoro con priorità più elevata. Il processo non cambia realmente per gli host VMWare. Quando il carico di lavoro successivo nel backlog è un host VMWare, l'unica modifica sarà lo strumento utilizzato.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

Di seguito sono riportati alcuni esempi di strumenti che possono essere usati nell'attività di migrazione:

- [Strumenti VMWare nativi](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

In alternativa, è possibile eseguire la migrazione dei carichi di lavoro tramite un failover di ripristino di emergenza utilizzando gli strumenti seguenti:

- [Eseguire il backup di macchine virtuali del carico di lavoro](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare il cloud privato come sito di ripristino di emergenza con Zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurare il cloud privato come sito di ripristino di emergenza con VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
