---
title: Decisioni relative alla progettazione della rete di idoneità per Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisioni relative alla progettazione della rete di idoneità per Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: a5303c426ec4eb7adaf8f22a37532c5b1dad14df
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224218"
---
# <a name="networking-design-decisions"></a>Decisioni relative alla progettazione della rete

La progettazione e l'implementazione delle funzionalità di rete di Azure costituiscono una parte essenziale dei lavori richiesti per l'adozione del cloud. È necessario prendere decisioni relative alla progettazione della rete per supportare correttamente i carichi di lavoro e i servizi che saranno ospitati nel cloud. I prodotti e i servizi di rete di Azure supportano un'ampia gamma di funzionalità di rete. Come strutturare questi servizi e le architetture di rete scelte dipende dai requisiti di connettività, governance e carico di lavoro dell'organizzazione.

## <a name="identify-workload-networking-requirements"></a>Identificare i requisiti di rete del carico di lavoro

Nell'ambito della valutazione e della preparazione dell'area di destinazione è necessario identificare le funzionalità di rete che devono essere supportate dalla stessa. Questo processo comporta la valutazione di tutte le applicazioni e dei servizi che costituiscono i carichi di lavoro per determinare i requisiti di controllo della rete di connettività. Una volta identificati e documentati i requisiti, è possibile creare criteri per l'area di destinazione in modo da controllare risorse e configurazione di rete consentite in base alle esigenze del carico di lavoro.

Usare l'albero delle decisioni seguente come punto di partenza per determinare gli strumenti o i servizi di rete da usare, per ogni applicazione o servizio che verrà distribuito nell'ambiente dell'area di destinazione:

![Albero delle decisioni dei servizi di rete di Azure](../../_images/ready/network-decision-tree.png)

### <a name="key-questions"></a>Domande principali

Rispondere alle domande seguenti sui carichi di lavoro per prendere decisioni in base all'albero delle decisioni dei servizi di rete di Azure:

- **I carichi di lavoro richiedono una rete virtuale?** I tipi di risorse della piattaforma gestita distribuita come servizio (PaaS, Platform as a Service) usano funzionalità di rete della piattaforma sottostante che non richiedono sempre una rete virtuale. Se i carichi di lavoro non richiedono funzionalità di rete avanzate e non è necessario distribuire risorse di infrastruttura distribuita come servizio (IaaS), le [funzionalità di rete native predefinite fornite dalle risorse PaaS](../../decision-guides/software-defined-network/paas-only.md) potrebbero soddisfare i requisiti di connettività del carico di lavoro e di gestione del traffico.
- **I carichi di lavoro richiedono la connettività tra le reti virtuali e il data center locale?** Azure fornisce due soluzioni per la creazione di funzionalità di rete ibrida:  Gateway VPN di Azure e Microsoft Azure ExpressRoute. [Gateway VPN di Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) connette le reti locali ad Azure tramite reti VPN da sito a sito, in modo simile a come si potrebbe configurare una connessione a una succursale remota. Gateway VPN ha una larghezza di banda massima di 1,25 GBps. [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) offre maggiore affidabilità e una latenza più bassa tramite connessione privata tra Azure e l'infrastruttura locale. Le opzioni relative alla larghezza di banda per ExpressRoute variano da 50 MBps a 100 GBps.
- **È necessario verificare e controllare il traffico in uscita usando i dispositivi di rete locali?** Per i carichi di lavoro nativi del cloud, è possibile usare [Firewall di Azure](https://docs.microsoft.com/azure/firewall/overview) o le [ NVA (network virtual appliances, appliance virtuali di rete)](https://azure.microsoft.com/solutions/network-appliances) di terze parti ospitate nel cloud per verificare e controllare il traffico proveniente dalla rete Internet pubblica. Tuttavia, molti criteri aziendali di sicurezza IT richiedono un traffico in uscita associato a Internet per passare attraverso dispositivi gestiti in modo centralizzato nell'ambiente locale dell'organizzazione. Il [tunneling forzato](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview) supporta questi scenari. Non tutti i servizi gestiti supportano il tunneling forzato. Servizi e funzionalità come [Ambiente del servizio app in Servizio app di Azure](https://docs.microsoft.com/azure/app-service/environment/intro), [Gestione API di Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts), [servizio Azure Kubernetes](https://docs.microsoft.com/azure/aks/intro-kubernetes), [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index), [Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/what-is-azure-databricks) e [Azure HDInsight](https://docs.microsoft.com/azure/hdinsight) supportano questa configurazione quando il servizio o la funzionalità vengono distribuiti all'interno di una rete virtuale.
- **C'è la necessità di connettere più reti virtuali?** È possibile usare il [peering di rete virtuale](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) per connettere più istanze di [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). Il peering può supportare le connessioni tra sottoscrizioni e aree geografiche. Per gli scenari in cui si forniscono servizi condivisi tra più sottoscrizioni o si ha la necessità di gestire un numero elevato di peering di rete è consigliabile adottare un'[architettura di rete hub-spoke](../../decision-guides/software-defined-network/hub-spoke.md) o usare [rete WAN virtuale di Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about). Il peering di rete virtuale fornisce connettività solo tra due reti con peering. Per impostazione predefinita, non fornisce connettività transitiva tra più peer.
- **I carichi di lavoro sono accessibili tramite Internet?** Azure offre servizi progettati per semplificare la gestione e la protezione dell'accesso esterno ad applicazioni e servizi:
  - [Firewall di Azure](https://docs.microsoft.com/azure/firewall/overview)
  - [Dispositivi di rete](https://azure.microsoft.com/solutions/network-appliances)
  - [Servizio Frontdoor di Azure](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
  - [Gateway applicazione Azure](https://docs.microsoft.com/azure/application-gateway)
  - [Gestione traffico di Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)
- **È necessario supportare la gestione DNS personalizzata?** [DNS di Azure](https://docs.microsoft.com/azure/dns/dns-overview) è un servizio di hosting per domini DNS che fornisce la risoluzione dei nomi tramite l'infrastruttura di Azure. Potrebbe essere necessario distribuire soluzioni aggiuntive, se i carichi di lavoro richiedono una risoluzione dei nomi che va oltre le funzionalità fornite da DNS di Azure. È consigliabile usare [Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/overview) per potenziare le funzionalità DNS di Azure se i carichi di lavoro richiedono anche servizi di Active Directory. Per maggiori funzionalità è anche possibile [distribuire macchine virtuali IaaS personalizzate](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances) per supportare i requisiti.

## <a name="common-networking-scenarios"></a>Scenari di rete comuni

La rete di Azure è costituita da più prodotti e servizi che forniscono diverse funzionalità di rete. È possibile confrontare i requisiti del carico di lavoro con gli scenari di rete indicati nella tabella seguente, come parte del processo di progettazione della rete, per identificare gli strumenti o i servizi di Azure da usare per fornire queste funzionalità di rete:

<!-- markdownlint-disable MD033 -->

| **Scenario** | **Prodotto di rete o servizio** |
| --- | --- |
| L'infrastruttura di rete deve connettere tutto, dalle macchine virtuali alle connessioni VPN in ingresso. | [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network) |
| Per bilanciare le connessioni in ingresso e in uscita e le richieste alle applicazioni o ai servizi. | [Servizio di bilanciamento del carico di Azure](https://docs.microsoft.com/azure/load-balancer) |
| Per ottimizzare il recapito da server farm applicazioni aumentando al contempo la sicurezza delle applicazioni con Web Application Firewall. | [Gateway applicazione Azure](https://docs.microsoft.com/azure/application-gateway) <br/>[Servizio Frontdoor di Azure](https://docs.microsoft.com/azure/frontdoor) |
| Per usare Internet in modo sicuro per accedere alle reti virtuali di Azure tramite gateway VPN a prestazioni elevate. | [Gateway VPN di Azure](https://docs.microsoft.com/azure/vpn-gateway) |
| Per assicurare risposte DNS velocissime e disponibilità elevatissima per tutte le esigenze a livello di dominio. | [DNS di Azure](https://docs.microsoft.com/azure/dns) |
| Per accelerare il recapito di contenuto a larghezza di banda elevata ai clienti in tutto il mondo, da applicazioni e contenuto archiviato ai video in streaming. | [Rete per la distribuzione di contenuti di Azure](https://docs.microsoft.com/azure/cdn) |
| Per proteggere le applicazioni Azure da attacchi Distributed Denial of Service. | [Protezione DDoS di Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) |
| Per distribuire il traffico in modo ottimale ai servizi nelle aree di Azure globali, garantendo al contempo disponibilità e tempi di risposta elevati. | [Gestione traffico di Azure](https://docs.microsoft.com/azure/traffic-manager)<br/>[Servizio Frontdoor di Azure](https://docs.microsoft.com/azure/frontdoor) |
| Per aggiungere la connettività di rete privata per accedere ai servizi cloud Microsoft dalle reti aziendali come se fossero reti locali e risiedessero nel data center. | [ExpressRoute di Azure](https://docs.microsoft.com/azure/expressroute) |
| Per monitorare e diagnosticare le condizioni a livello di scenario di rete. | [Azure Network Watcher](https://docs.microsoft.com/azure/network-watcher) |
| Per funzionalità di firewall native con disponibilità elevata incorporata, scalabilità cloud senza limiti e nessuna manutenzione. | [Firewall di Azure](https://docs.microsoft.com/azure/firewall) |
| Per connettere uffici, sedi commerciali e siti in modo sicuro. | [Rete WAN virtuale di Azure](https://docs.microsoft.com/azure/virtual-wan) |
| Per un punto di distribuzione scalabile e ottimizzato per la sicurezza per applicazioni Web basate su microservizi globali. | [Servizio Frontdoor di Azure](https://docs.microsoft.com/azure/frontdoor) |

<!-- markdownlint-enable MD033 -->

## <a name="choose-a-networking-architecture"></a>Scegliere un'architettura di rete

Dopo aver identificato i servizi di rete di Azure necessari per supportare i carichi di lavoro è necessario progettare l'architettura che combinerà questi servizi per fornire l'infrastruttura di rete cloud dell'area di destinazione. La [guida alle decisioni per le reti definite dal software](../../decision-guides/software-defined-network/index.md) Cloud Adoption Framework fornisce informazioni dettagliate su alcuni dei modelli di architettura di rete più comuni usati in Azure.

Nella tabella seguente sono riepilogati gli scenari principali supportati da questi modelli:

| **Scenario** | **Architettura di rete suggerita**
| --- | --- |
| Tutti i carichi di lavoro ospitati da Azure e distribuiti nell'area di destinazione sono completamente basati su PaaS, non richiedono una rete virtuale e non fanno parte di un più ampio sforzo di adozione del cloud che include le risorse IaaS. | [PaaS-only](../../decision-guides/software-defined-network/paas-only.md) |
| I carichi di lavoro ospitati in Azure distribuiscono risorse basate su IaaS, come le macchine virtuali, o richiedono una rete virtuale ma non richiedono la connettività all'ambiente locale. | [Nativa del cloud](../../decision-guides/software-defined-network/cloud-native.md) |
| I carichi di lavoro ospitati da Azure richiedono un accesso limitato alle risorse locali ma è necessario gestire le connessioni cloud come non attendibili. | [Reti perimetrali nel cloud](../../decision-guides/software-defined-network/cloud-dmz.md) |
| I carichi di lavoro ospitati da Azure richiedono un accesso limitato alle risorse locali; si prevede di implementare criteri di sicurezza maturi e una connettività sicura tra il cloud e l'ambiente locale. | [Ibrido](../../decision-guides/software-defined-network/hybrid.md) |
| Per distribuire e gestire un numero elevato di macchine virtuali e carichi di lavoro, superando potenzialmente i [limiti della sottoscrizione di Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits) è necessario condividere i servizi tra le sottoscrizioni oppure è necessaria una struttura più segmentata per ruolo, applicazione o separazione delle autorizzazioni. | [Hub-spoke](../../decision-guides/software-defined-network/hub-spoke.md) |
| Sono disponibili molte succursali che devono connettersi tra loro e ad Azure. | [Rete WAN virtuale di Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) |

### <a name="azure-virtual-datacenter"></a>Data center virtuale di Azure

Oltre a usare uno di questi modelli di architettura, se il gruppo IT aziendale gestisce ambienti cloud di grandi dimensioni è consigliabile consultare le [linee guida per il data center virtuale di Azure](../../reference/vdc.md) quando si progetta un'infrastruttura cloud basata su Azure. Data Center virtuale di Azure offre un approccio combinato per rete, sicurezza, gestione e l'infrastruttura se l'organizzazione soddisfa i criteri seguenti:

- L'azienda è tenuta a soddisfare la conformità alle normative in base ai quali è necessario disporre di funzionalità di monitoraggio e controllo centralizzate.
- L'ambiente cloud sarà costituito da più di 10.000 macchine virtuali IaaS o da un numero di servizi PaaS di uguale entità.
- È necessario implementare funzionalità di distribuzione flessibili per i carichi di lavoro per supportare i team operativi e di sviluppo, mantenendo al tempo stesso la conformità alla governance e ai criteri comuni e il controllo IT centralizzato sui servizi di base.
- Il settore in cui opera l'azienda dipende da una piattaforma complessa che richiede un'esperienza approfondita del settore, ad esempio finanziario, petrolifero o manufatturiero.
- I criteri di governance IT esistenti richiedono un adeguamento più rigoroso alle funzionalità esistenti, anche durante la fase di adozione iniziale.

## <a name="follow-azure-networking-best-practices"></a>Seguire le procedure di rete consigliate di Azure

Come parte del processo di progettazione della rete, vedere gli articoli seguenti:

- [Pianificazione della rete virtuale](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come pianificare le reti virtuali in base ai requisiti di isolamento, connettività e località.
- [Procedure consigliate di Azure per la sicurezza di rete](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulle procedure consigliate di Azure che consentono di migliorare la sicurezza della rete.
- [Procedure consigliate per la rete quando si esegue la migrazione di carichi di lavoro ad Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-networking?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni aggiuntive su come implementare la rete di Azure per supportare i carichi di lavoro basati su IaaS e PaaS.
