---
title: Usare la bonifica per creare le zone di destinazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come usare la bonifica per creare le zone di destinazione.
author: arnaudlh
ms.author: arnaul
ms.date: 10/16/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 99d5e42f8c7e506ba28617022f2a8076c9501979
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73239770"
---
# <a name="use-terraform-to-build-your-landing-zones"></a>Usare la bonifica per creare le zone di destinazione

Azure fornisce servizi nativi per la distribuzione di zone di destinazione. Anche altri strumenti di terze parti possono aiutare a eseguire questa operazione. Uno di questi strumenti che i clienti e i partner usano spesso per distribuire le zone di destinazione sono la bonifica di Hashicorp. Questa sezione illustra come usare un'area di destinazione prototipo per distribuire funzionalità di registrazione, contabilità e sicurezza fondamentali per una sottoscrizione di Azure.

## <a name="purpose-of-the-landing-zone"></a>Scopo della zona di destinazione

L'area di destinazione di base del Framework di adozione del cloud per la bonifica ha un set limitato di responsabilità e funzionalità per l'applicazione di registrazione, contabilità e sicurezza. Questa zona di destinazione è stata progettata in modo da usare componenti standard noti come moduli di bonifica per applicare la coerenza tra le risorse distribuite nell'ambiente.

## <a name="using-standard-modules"></a>Uso di moduli standard

Il riutilizzo dei componenti è un principio fondamentale di infrastruttura come codice. I moduli sono strumentali nella definizione di standard e coerenza per la distribuzione di risorse all'interno di e tra ambienti diversi. Il set di moduli utilizzati per distribuire questa prima area di destinazione è disponibile nel [Registro di sistema](https://registry.terraform.io/search?q=aztfmod)ufficiale.

## <a name="architecture-diagram"></a>Diagramma dell'architettura

La prima zona di destinazione distribuisce i componenti seguenti nella sottoscrizione:

![Area di destinazione di base con bonifica](../../_images/ready/foundations-terraform-landingzone.png)

## <a name="capabilities"></a>Capabilities

I componenti distribuiti e il relativo scopo includono quanto segue:

| Componente | Responsabilità |
|---------|---------|
| Gruppi di risorse | Gruppi di risorse principali necessari per la base |
| Registrazione attività | Controllo di tutte le attività di sottoscrizione e di archiviazione: </br> -Account di archiviazione </br> -Hub eventi |  
| Registrazione diagnostica | Tutti i log operazioni conservati per un numero specifico di giorni: </br> -Account di archiviazione </br> -Hub eventi |
| Log Analytics | Archivia tutti i log operazioni </br> Distribuire soluzioni comuni per la revisione approfondita delle procedure consigliate per le applicazioni: </br> - NetworkMonitoring </br> -Della valutazione </br> -ADReplication </br> - AgentHealthAssessment </br> - DnsAnalytics </br> - KeyVaultAnalytics
| Centro sicurezza | Metriche e avvisi relativi all'igiene della sicurezza inviati alla posta elettronica e al numero di telefono |

## <a name="use-this-blueprint"></a>Usare il progetto

Prima di usare l'area di destinazione di Cloud Adoption Framework, esaminare i presupposti, le decisioni e le linee guida di implementazione seguenti.

## <a name="assumptions"></a>Presupposti

Quando è stata definita questa area di destinazione iniziale, sono stati presi in considerazione i vincoli o i presupposti seguenti. Se i presupposti sono allineati ai vincoli, è possibile usare il progetto per creare la prima zona di destinazione. Il progetto può anche essere esteso per creare un progetto relativo alla zona di destinazione che soddisfi vincoli univoci.

- **Limiti della sottoscrizione:** Questa operazione di adozione è improbabile che superi i [limiti della sottoscrizione](https://docs.microsoft.com/azure/azure-subscription-service-limits). Due indicatori comuni sono il superamento di 25.000 macchine virtuali o 10.000 vCPU.
- **Conformità:** Per questa area di destinazione non sono necessari requisiti di conformità di terze parti.
- **Complessità dell'architettura:** La complessità dell'architettura non richiede sottoscrizioni di produzione aggiuntive.
- **Servizi condivisi:** In Azure non sono presenti servizi condivisi esistenti che richiedono che questa sottoscrizione venga trattata come una spoke in un'architettura hub-spoke.

Se questi presupposti corrispondono all'ambiente corrente, questo progetto potrebbe essere un metodo efficace per iniziare a creare la zona di destinazione.

## <a name="design-decisions"></a>Decisioni di progettazione

Le decisioni seguenti sono rappresentate nell'area di destinazione di bonifica:

| Componente | Decisioni | Approcci alternativi |
| --- | --- | --- |
|Registrazione e monitoraggio | Verrà usata l'area di lavoro Log Analytics di monitoraggio di Azure. Verrà eseguito il provisioning di un account di archiviazione di diagnostica e di hub eventi. |         |
|Rete | N/A-la rete verrà implementata in un'altra area di destinazione. |[Decisioni relative alla rete](../considerations/networking-options.md) |
|Identità | Si presuppone che la sottoscrizione sia già associata a un'istanza di Azure Active Directory. | [Procedure consigliate per la gestione delle identità](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices) |
| Policy | Questa zona di destinazione presuppone attualmente che non venga applicato alcun criterio di Azure. | |
|Progettazione della sottoscrizione | N/D - Progettazione per una singola sottoscrizione di produzione. | [Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md) |
| Gruppi di gestione | N/D - Progettazione per una singola sottoscrizione di produzione. |[Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md) |
| Gruppi di risorse | N/D - Progettazione per una singola sottoscrizione di produzione. | [Ridimensionamento delle sottoscrizioni](../azure-best-practices/scaling-subscriptions.md) |
| Dati | N/D | [Scegliere l'opzione SQL Server corretta in Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) e [informazioni aggiuntive sull'archivio dati di Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Archiviazione|N/D|[Indicazioni per Archiviazione di Azure](../considerations/storage-options.md) |
| Standard di denominazione | Quando viene creato l'ambiente, viene creato anche un prefisso univoco. Le risorse che richiedono un nome univoco globale, ad esempio gli account di archiviazione, usano questo prefisso. Il nome personalizzato verrà aggiunto con un suffisso casuale. L'utilizzo dei tag è obbligatorio come descritto nella tabella seguente. | [Procedure consigliate di denominazione e assegnazione di tag](../azure-best-practices/naming-and-tagging.md) |
| Gestione dei costi | N/D | [Tracciamento dei costi](../azure-best-practices/track-costs.md) |
| Calcolo | N/D | [Opzioni di calcolo](../considerations/compute-options.md) |

### <a name="tagging-standards"></a>Standard di assegnazione di tag

Il set di tag minimo seguente deve essere presente in tutte le risorse e nei gruppi di risorse:

| Nome del tag | Description | Chiave | Valore di esempio |
|--|--|--|--|
| Business Unit | Divisione di livello principale della società che possiede la sottoscrizione o carico di lavoro a cui appartiene la risorsa. | BusinessUnit | Finanza, MARKETING, {nome prodotto}, CORP, condiviso |
| Cost Center | Centro di costo di contabilità associato a questa risorsa.| CostCenter | Numero |
| Ripristino di emergenza | Criticità aziendale dell'applicazione, del carico di lavoro o del servizio. | DR | ABILITATO PER IL RIPRISTINO DI EMERGENZA, NON ABILITATO PER IL RIPRISTINO DI EMERGENZA |
| Ambiente | Ambiente di distribuzione dell'applicazione, del carico di lavoro o del servizio. |  ENV | Prod, dev, QA, stage, test, training |
| Nome del proprietario | Proprietario dell'applicazione, del carico di lavoro o del servizio.| Proprietario | email |
| DeploymentType | Definisce la modalità di manutenzione delle risorse. | deploymentType | Manuale, bonifica |
| Versione | Versione del progetto distribuito | version | v 0.1 |
| Nome dell'applicazione | Nome dell'applicazione, del servizio o del carico di lavoro associato alla risorsa. | ApplicationName | "nome app" |

## <a name="customize-and-deploy-your-first-landing-zone"></a>Personalizzare e distribuire la prima zona di destinazione

È possibile [clonare l'area di destinazione di base di bonifica](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready). È facile iniziare a usare la zona di destinazione modificando le variabili di bonifica. In questo esempio si usa **blueprint_foundations. sandbox. auto. tfvars**, quindi la bonifica imposta automaticamente i valori in questo file.

Esaminiamo le diverse sezioni variabili.

In questo primo oggetto vengono creati due gruppi di risorse nell'area `southeastasia`, denominata "-hub-Core-sec" e "-hub-Core-sec" insieme a un prefisso aggiunto in fase di esecuzione.

```hcl
resource_groups_hub = {
    HUB-CORE-SEC    = {
        name = "-hub-core-sec"
        location = "southeastasia"
    }
    HUB-OPERATIONS  = {
        name = "-hub-operations"
        location = "southeastasia"
    }
}
```

Successivamente, si specificano le aree in cui è possibile impostare le fondamenta. Qui, `southeastasia` verrà usato per distribuire tutte le risorse.

```hcl
location_map = {
    region1   = "southeastasia"
    region2   = "eastasia"
}
```

Viene quindi specificato il periodo di memorizzazione per i log delle operazioni e i log della sottoscrizione di Azure. Questi dati verranno archiviati in account di archiviazione separati e in un hub eventi, i cui nomi vengono generati in modo casuale perché devono essere univoci.

```hcl
azure_activity_logs_retention = 365
azure_diagnostics_logs_retention = 60
```

In tags_hub, viene specificato il set minimo di tag che verrà applicato a tutte le risorse create.

```hcl
tags_hub = {
    environment     = "DEV"
    owner           = "Arnaud"
    deploymentType  = "Terraform"
    costCenter      = "65182"
    BusinessUnit    = "SHARED"
    DR              = "NON-DR-ENABLED"
}
```

Viene quindi specificato il nome di log Analytics e un set di soluzioni che analizzeranno la distribuzione. In questo caso, è stato mantenuto il monitoraggio della rete, Valutazione AD e la replica, Analisi DNS e Analisi insieme di credenziali delle chiavi.

```hcl

analytics_workspace_name = "lalogs"

solution_plan_map = {
    NetworkMonitoring = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/NetworkMonitoring"
    },
    ADAssessment = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/ADAssessment"
    },
    ADReplication = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/ADReplication"
    },
    AgentHealthAssessment = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/AgentHealthAssessment"
    },
    DnsAnalytics = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/DnsAnalytics"
    },
    KeyVaultAnalytics = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/KeyVaultAnalytics"
    }
}

```

Successivamente, sono stati configurati i parametri di avviso per il Centro sicurezza di Azure.

```hcl
# Azure Security Center Configuration
security_center = {
    contact_email   = "joe@contoso.com"
    contact_phone   = "+6500000000"
}
```

## <a name="getting-started"></a>Inizia ora

Dopo aver esaminato la configurazione, è possibile distribuire la configurazione come si distribuisce un ambiente di bonifica. È tuttavia consigliabile usare il Rover, ovvero un contenitore Docker che consente la distribuzione da Windows, Linux o MacOS. È possibile iniziare a usare il [repository GitHub di Rover](https://github.com/aztfmod/rover).

## <a name="next-steps"></a>Passaggi successivi

La zona di destinazione di base pone le fondamenta per un ambiente complesso in modo decomposto. Questa edizione fornisce un set di funzionalità molto semplici che possono essere estese da:

- Aggiunta di altri moduli al progetto.
- Sovrapposizione di zone di destinazione aggiuntive.

Il livello delle aree di destinazione è una procedura consigliata per separare i sistemi, il controllo delle versioni di ogni componente in uso e la rapida innovazione e stabilità per la distribuzione di infrastruttura come codice.

Nelle architetture di riferimento future verrà illustrato questo concetto per una topologia hub-spoke.

> [!div class="nextstepaction"]
> [Esaminare l'esempio di area di destinazione di base usando la bonifica](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready)
