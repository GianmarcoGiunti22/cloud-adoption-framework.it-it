---
title: Decisioni relative alla progettazione delle risorse di calcolo per l'idoneità per Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisioni relative alla progettazione delle risorse di calcolo per l'idoneità per Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 0569dd472e3dd85c13bb3872a351d6eec4868e39
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025186"
---
# <a name="compute-design-decisions"></a>Decisioni relative alla progettazione delle risorse di calcolo

Determinare i requisiti di calcolo per l'hosting dei carichi di lavoro è una considerazione fondamentale di cui tenere conto durante la preparazione dell'adozione del cloud. I prodotti e i servizi di calcolo di Azure supportano un'ampia gamma di scenari e funzionalità di calcolo dei carichi di lavoro. Il modo in cui si configura l'ambiente della zona di destinazione per supportare i requisiti di calcolo dipende dai requisiti di governance, tecnici e aziendali del carico di lavoro.

## <a name="identify-compute-services-requirements"></a>Identificare i requisiti dei servizi di calcolo

Nell'ambito della valutazione e della preparazione della zona di destinazione è necessario identificare tutte le risorse di calcolo che dovranno essere supportate dalla stessa. Questo processo comporta la valutazione di tutte le applicazioni e di tutti i servizi che costituiscono i carichi di lavoro per determinare i requisiti di calcolo e hosting. Dopo aver identificato e documentato i requisiti, è possibile creare criteri per la zona di destinazione in modo da controllare i tipi di risorse consentiti in base alle esigenze del carico di lavoro.

Usare l'albero delle decisioni seguente come punto di partenza per determinare i requisiti dei servizi di calcolo per ogni applicazione o servizio che verrà distribuito nell'ambiente della zona di destinazione:

![Albero delle decisioni per i servizi di calcolo di Azure](../../_images/ready/compute-decision-tree.png)

> [!NOTE]
> Sono disponibili altre informazioni su come valutare le opzioni di calcolo per ogni applicazione o servizio nella [Guida all'architettura delle applicazioni Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview).

### <a name="key-questions"></a>Domande principali

Rispondere alle domande seguenti sui carichi di lavoro per prendere decisioni in base all'albero delle decisioni per i servizi di calcolo di Azure:

- **Si creano applicazioni e servizi completamente nuovi o si esegue la migrazione da carichi di lavoro locali esistenti?** Lo sviluppo di nuove applicazioni nell'ambito delle attività di adozione del cloud consente di sfruttare appieno le moderne tecnologie di hosting basate sul cloud a partire dalla fase di progettazione in poi.
- **Se si esegue la migrazione, i carichi di lavoro esistenti possono sfruttare le tecnologie cloud moderne?** La migrazione di carichi di lavoro locali richiede un'analisi. È possibile ottimizzare facilmente le applicazioni e i servizi esistenti in modo da sfruttare le tecnologie cloud moderne oppure è più adatto un approccio *lift-and-shift* per i carichi di lavoro?
- **Le applicazioni o i servizi possono sfruttare i vantaggi offerti dai contenitori?** Se le applicazioni sono adatte per l'hosting in contenitori, è possibile sfruttare le funzionalità di efficienza, ridimensionamento e orchestrazione delle risorse offerte [dai servizi contenitore di Azure](https://azure.microsoft.com/product-categories/containers). È possibile usare i servizi [archiviazione su disco di Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) e [File di Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) per l'archiviazione permanente per le applicazioni incluse in contenitori.
- **Le applicazioni sono basate sul Web o su API e usano PHP, ASP.NET, Node.js o tecnologie simili?** Le app Web possono essere distribuite in istanze gestite di [Servizio app di Azure](https://docs.microsoft.com/azure/app-service/overview), quindi non è necessario mantenere macchine virtuali per l'hosting.
- **Sarà necessario avere il controllo completo sul sistema operativo e sull'ambiente di hosting del carico di lavoro?** Se è necessario controllare l'ambiente di hosting, inclusi il sistema operativo, i dischi, il software in esecuzione in locale e altre configurazioni, è possibile usare [Macchine virtuali di Azure](https://azure.microsoft.com/services/virtual-machines) per ospitare le applicazioni e i servizi. Oltre a scegliere le dimensioni e i livelli di prestazioni delle macchine virtuali, le decisioni relative all'archiviazione su dischi virtuali influiranno sulle prestazioni e sui contratti di servizio correlati ai carichi di lavoro basati sull'infrastruttura distribuita come servizio (IaaS). Per altre informazioni, vedere la documentazione relativa ad [archiviazione su disco di Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview).
- **Il carico di lavoro implica funzionalità HPC (High Performance Computing)?** [Azure Batch](https://docs.microsoft.com/azure/batch/batch-technical-overview) offre la pianificazione dei processi e la scalabilità automatica delle risorse di calcolo come servizio di piattaforma, semplificando l'esecuzione di applicazioni parallele e HPC su larga scala nel cloud.
- **Le applicazioni useranno un'architettura di microservizi?** Le applicazioni che usano un'architettura basata su microservizi possono sfruttare diverse tecnologie di calcolo ottimizzate. I carichi di lavoro autonomi basati su eventi possono usare [Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview) per creare applicazioni scalabili e serverless che non necessitano di un'infrastruttura. Per le applicazioni che richiedono un maggiore controllo sull'ambiente in cui vengono eseguiti i microservizi, è possibile usare servizi contenitore come [Istanze di Azure Container](https://docs.microsoft.com/azure/container-instances/container-instances-overview), il [servizio Azure Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes) e [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).

> [!NOTE]
> La maggior parte dei servizi di calcolo di Azure viene usata in combinazione con Archiviazione di Azure. Consultare le [indicazioni sulle decisioni di archiviazione](./storage-guidance.md) per le decisioni correlate.

## <a name="common-compute-scenarios"></a>Scenari di calcolo comuni

La tabella seguente illustra alcuni scenari di uso comune e i servizi di calcolo consigliati per gestirli:

| **Scenario** | **Servizio di calcolo** |
| --- | --- |
| Si vuole effettuare il provisioning di macchine virtuali Linux e Windows in pochi secondi con le configurazioni desiderate. | [Macchine virtuali di Azure](https://azure.microsoft.com/services/virtual-machines) |
| Si vuole ottenere la disponibilità elevata grazie alla scalabilità automatica per creare migliaia di macchine virtuali in pochi minuti. | [Set di scalabilità di macchine virtuali](https://azure.microsoft.com/services/virtual-machine-scale-sets) |
| Si vuole semplificare la distribuzione, la gestione e le operazioni di Kubernetes. | [Servizio Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service) |
| Si vuole accelerare lo sviluppo di app con un'architettura serverless basata su eventi. | [Funzioni di Azure](https://azure.microsoft.com/services/functions) |
| Si vuole sviluppare microservizi e orchestrare contenitori in Windows e Linux. | [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric) |
| Si vuole creare rapidamente app cloud per il Web e i dispositivi mobili con una piattaforma completamente gestita. | [Servizio app di Azure](https://azure.microsoft.com/services/app-service) |
| Si vuole includere le app in contenitori ed eseguire facilmente i contenitori con un unico comando. | [Istanze di Azure Container](https://azure.microsoft.com/services/container-instances) |
| Si vuole ridimensionare la gestione delle risorse di calcolo e la pianificazione dei processi a livello del cloud con la possibilità di ridimensionamento fino a decine, centinaia o migliaia di macchine virtuali. | [Azure Batch](https://azure.microsoft.com/services/batch) |
| Si vuole creare API e applicazioni cloud scalabili e a disponibilità elevata per concentrarsi sulle app anziché sull'hardware. | [Servizi cloud di Azure](https://azure.microsoft.com/services/cloud-services) |

## <a name="regional-availability"></a>Disponibilità a livello di area

Azure consente di offrire servizi al livello necessario per raggiungere i clienti e i partner,  _ovunque si trovino_. Un fattore chiave nella pianificazione della distribuzione cloud consiste nel determinare l'area di Azure che ospiterà le risorse del carico di lavoro.

Alcune opzioni di calcolo, ad esempio Servizio app di Azure, sono in genere disponibili nella maggior parte delle aree di Azure. Alcuni servizi di calcolo tuttavia sono supportati solo in alcune aree. Alcuni tipi di macchine virtuali e i tipi di archiviazione associati hanno una disponibilità limitata a livello di area. Prima di decidere in quali aree distribuire le risorse di calcolo, è consigliabile fare riferimento alla [pagina relativa alle aree](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=azure-vmware-cloudsimple,cloud-services,batch,container-instances,app-service,service-fabric,functions,kubernetes-service,virtual-machine-scale-sets,virtual-machines)  per verificare lo stato più recente della disponibilità a livello di area.

Per altre informazioni sull'infrastruttura globale di Azure, vedere la  [pagina Aree di Azure](https://azure.microsoft.com/global-infrastructure/regions). È anche possibile consultare la pagina  [Prodotti disponibili in base all'area](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) per trovare dettagli specifici sui servizi globali disponibili in ogni area di Azure.

## <a name="data-residency-and-compliance-requirements"></a>Requisiti di conformità e residenza dei dati

Ai carichi di lavoro sono spesso applicati requisiti legali e contrattuali correlati all'archiviazione dei dati. Questi requisiti possono variare in base alla sede dell'organizzazione, alla giurisdizione in cui sono archiviati ed elaborati i file e i dati e al settore aziendale applicabile. I componenti degli obblighi relativi ai dati da considerare includono la classificazione dei dati, la posizione dei dati e le rispettive responsabilità per la protezione dei dati nel modello di responsabilità condivisa. Molte soluzioni di calcolo dipendono dalle risorse di archiviazione collegate. Questo requisito può anche influenzare le decisioni relative alle risorse di calcolo. Per comprendere meglio questi requisiti, consultare il white paper  [Ottenere la conformità in materia di sicurezza e residenza dei dati con Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Una parte del lavoro richiesto per la conformità potrebbe includere il controllo della posizione fisica delle risorse di calcolo. Le aree di Azure sono organizzate in gruppi denominati "aree geografiche". Un' [area geografica di Azure](https://azure.microsoft.com/global-infrastructure/geographies) assicura il rispetto dei requisiti di residenza, sovranità, conformità e resilienza dei dati entro limiti geografici e politici. Se i carichi di lavoro sono soggetti a sovranità dei dati o ad altri requisiti di conformità, è necessario distribuire le risorse di archiviazione in aree situate in un'area geografica di Azure conforme.

## <a name="establish-controls-for-compute-services"></a>Definire i controlli per i servizi di calcolo

Quando si prepara l'ambiente della zona di destinazione, è possibile stabilire i controlli che limitano le risorse che ciascun utente può distribuire. I controlli possono aiutare a gestire i costi e a limitare i rischi per la sicurezza, consentendo allo stesso tempo agli sviluppatori e ai team IT di distribuire e configurare le risorse necessarie per supportare i carichi di lavoro.

Dopo aver identificato e documentato i requisiti della zona di destinazione, è possibile usare [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) per controllare le risorse di calcolo che possono essere create dagli utenti. I controlli possono consistere nel [consentire o negare la creazione di tipi di risorse di calcolo](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). È ad esempio possibile limitare gli utenti consentendo loro di creare solo risorse di Servizio app di Azure o di Funzioni di Azure. È anche possibile usare i criteri per controllare le opzioni consentite quando viene creata una risorsa, ad esempio [limitare le SKU di macchine virtuali di cui è possibile eseguire il provisioning](https://docs.microsoft.com/azure/governance/policy/samples/allowed-skus-storage) o [consentire solo immagini di macchine virtuali specifiche](https://docs.microsoft.com/azure/governance/policy/samples/allowed-custom-images).

I criteri possono essere limitati a risorse, gruppi di risorse, sottoscrizioni e gruppi di gestione. È possibile includere i criteri nelle definizioni di [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) e applicarli ripetutamente all'interno dell'ambiente cloud.

