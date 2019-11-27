---
title: Distribuire una zona di destinazione della migrazione in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come distribuire una zona di destinazione della migrazione in Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, setup
ms.openlocfilehash: 59b57467eeae47b73fa24ce672d9e7e4f0ed4478
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251705"
---
# <a name="deploy-a-migration-landing-zone"></a>Distribuire un'area di destinazione della migrazione

*Zona di destinazione della migrazione* è un termine usato per indicare un ambiente sottoposto a provisioning e preparato per ospitare carichi di lavoro in fase di migrazione da un ambiente locale ad Azure. Una zona di destinazione della migrazione è il risultato finale della Guida all'installazione di Azure. Questo articolo associa tutti gli argomenti relativi all'idoneità illustrati in questa guida e applica le decisioni alla distribuzione della prima zona di destinazione della migrazione.

Le sezioni seguenti descrivono una zona di destinazione comunemente usata per stabilire un ambiente adatto all'uso durante una migrazione. L'ambiente o la zona di destinazione descritti in questo articolo vengono acquisiti anche in un progetto di Azure. È possibile usare il progetto relativo alla zona di destinazione della migrazione di Cloud Adoption Framework per distribuire l'ambiente definito con un solo clic.

## <a name="purpose-of-the-blueprint"></a>Scopo del progetto

Il progetto relativo alla zona di destinazione per la migrazione di Cloud Adoption Framework crea una zona di destinazione. Questa zona di destinazione è limitata intenzionalmente. È progettata per creare un punto iniziale coerente che fornisca spazio per l'apprendimento dell'infrastruttura come codice. Per alcune attività di migrazione, questa zona di destinazione potrebbe essere sufficiente per soddisfare le proprie esigenze. È anche probabile che sia necessario modificare un elemento del progetto per soddisfare vincoli univoci.

## <a name="blueprint-alignment"></a>Allineamento del progetto

La figura seguente mostra il progetto relativo alla zona di destinazione per la migrazione di Cloud Adoption Framework in relazione ai requisiti di conformità e complessità dell'architettura.

![Allineamento del progetto](../../_images/ready/blueprint-overview.png)

- La lettera A si trova all'interno di una linea curva che contrassegna l'ambito di questo progetto. L'ambito è concepito per indicare che il progetto copre una complessità limitata dal punto di vista dell'architettura, ma si basa su requisiti di conformità relativamente medi.
- I clienti che hanno requisiti elevati di complessità e rigidi a livello di conformità potrebbero avere un servizio migliore usando il progetto esteso di un partner oppure uno dei [campioni del progetto basato su standard](https://docs.microsoft.com/azure/governance/blueprints/samples).
- Le esigenze della maggior parte dei clienti rientreranno tra questi due estremi. La lettera B rappresenta il processo descritto negli articoli di [considerazioni sulla zona di destinazione](../considerations/index.md). Per i clienti che si trovano in questo spazio, è possibile usare le guide alle decisioni disponibili in questi articoli per identificare i nodi da aggiungere al progetto relativo alla zona di destinazione per la migrazione di Cloud Adoption Framework. Questo approccio consente di personalizzare il progetto in base alle esigenze.

## <a name="use-this-blueprint"></a>Usare il progetto

Prima di usare il progetto relativo alla zona di destinazione per la migrazione di Cloud Adoption Framework, esaminare i presupposti, le decisioni e le linee guida di implementazione seguenti.

## <a name="assumptions"></a>Presupposti

Quando è stata definita questa zona di destinazione iniziale, sono stati usati i presupposti o i vincoli seguenti. Se i presupposti sono allineati ai vincoli, è possibile usare il progetto per creare la prima zona di destinazione. Il progetto può anche essere esteso per creare un progetto relativo alla zona di destinazione che soddisfi vincoli univoci.

- **Limiti della sottoscrizione:** Questa operazione di adozione non prevede il superamento dei [limiti della sottoscrizione](https://docs.microsoft.com/azure/azure-subscription-service-limits). Due indicatori comuni sono il superamento di 25.000 macchine virtuali o 10.000 vCPU.
- **Conformità:** In questa area di destinazione non sono necessari requisiti di conformità di terze parti.
- **Complessità dell'architettura:** La complessità dell'architettura non richiede sottoscrizioni di produzione aggiuntive.
- **Servizi condivisi:** In Azure non sono presenti servizi condivisi esistenti che richiedono che questa sottoscrizione venga trattata come una spoke in un'architettura hub-spoke.

Se questi presupposti sembrano allineati all'ambiente corrente, il progetto potrebbe essere un punto ideale per iniziare a realizzare la zona di destinazione.

## <a name="decisions"></a>Decisioni

Le decisioni seguenti sono rappresentate nel progetto relativo alla zona di destinazione.

| Componente | Decisioni | Approcci alternativi |
|---------|---------|---------|
|Strumenti di migrazione|Verrà distribuito Azure Site Recovery e verrà creato un progetto Azure Migrate.|[Guida alle decisioni relative agli strumenti di migrazione](../../decision-guides/migrate-decision-guide/index.md)|
|Registrazione e monitoraggio|Verrà eseguito il provisioning dell'area di lavoro Operational Insights e dell'account di archiviazione di diagnostica.|         |
|Rete|Verrà creata una rete virtuale con subnet per gateway, firewall, jumpbox e zona di destinazione.|[Decisioni relative alla rete](../considerations/networking-options.md)|
|Identità|Si presuppone che la sottoscrizione sia già associata a un'istanza di Azure Active Directory.|[Procedure consigliate per la gestione delle identità](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json)         |
|Criteri|Questo progetto presuppone attualmente che non venga applicato alcun criterio di Azure.|         |
|Progettazione della sottoscrizione|N/D - Progettazione per una singola sottoscrizione di produzione.|[Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md)|
|Gruppi di gestione|N/D - Progettazione per una singola sottoscrizione di produzione.|[Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md)         |
|Gruppi di risorse|N/D - Progettazione per una singola sottoscrizione di produzione.|[Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md)         |
|Data|N/D|[Scegliere l'opzione SQL Server corretta in Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) e [informazioni aggiuntive sull'archivio dati di Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Archiviazione|N/D|[Indicazioni per Archiviazione di Azure](../considerations/storage-options.md)         |
|Standard di denominazione e assegnazione di tag|N/D|[Procedure consigliate di denominazione e assegnazione di tag](../azure-best-practices/naming-and-tagging.md)         |
|Gestione dei costi|N/D|[Tracciamento dei costi](../azure-best-practices/track-costs.md)|
|Calcolo|N/D|[Opzioni di calcolo](../considerations/compute-options.md)|

## <a name="customize-or-deploy-a-landing-zone-from-this-blueprint"></a>Personalizzare o distribuire una zona di destinazione da questo progetto

Scopri di più e Scarica un esempio di riferimento del Framework di adozione cloud migrazione del progetto di area di destinazione per la distribuzione o la personalizzazione dagli [esempi di progetti di Azure](https://docs.microsoft.com/azure/governance/blueprints/samples).

Gli esempi di progetti sono disponibili anche nel portale. Per informazioni dettagliate su come creare un progetto, vedere [progetti di Azure](./govern-org-compliance.md?tabs=azureblueprints#create-a-blueprint).

Per indicazioni sulla personalizzazione da apportare al progetto o alla zona di destinazione risultante, vedere gli articoli di [considerazioni sulla zona di destinazione](../considerations/index.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo la distribuzione di una zona di destinazione della migrazione, si è pronti per eseguire la migrazione dei carichi di lavoro ad Azure.
Per istruzioni su strumenti e processi necessari per eseguire la migrazione del primo carico di lavoro, vedere la [Guida alla migrazione di Azure](../../migrate/azure-migration-guide/index.md).

> [!div class="nextstepaction"]
> [Eseguire la migrazione del primo carico di lavoro con la Guida alla migrazione di Azure](../../migrate/azure-migration-guide/index.md)
