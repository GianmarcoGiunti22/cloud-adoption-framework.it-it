---
title: Topologia di rete hub-spoke
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Topologia di rete hub-spoke
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 48f73d7c7f2e7f3bba8183464c786a3e0744807c
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905499"
---
# <a name="hub-and-spoke-network-topology"></a>Topologia di rete hub-spoke

*Hub-spoke* è un modello di rete per la gestione efficiente dei comuni requisiti di comunicazione o sicurezza. Consente anche di evitare le limitazioni delle sottoscrizioni di Azure. Questo modello consente di risolvere i problemi seguenti:

- **Risparmio sui costi ed efficienza della gestione.** Centralizzando in un'unica posizione i servizi che possono essere condivisi da più carichi di lavoro, ad esempio appliance virtuali di rete e server DNS, l'IT può ridurre al minimo le risorse ridondanti e l'impegno richiesto dalla gestione.
- **Superamento dei limiti delle sottoscrizioni.** Per i carichi di lavoro di grandi dimensioni basati sul cloud, potrebbe essere necessario usare più risorse di quelle consentite in una singola sottoscrizione di Azure. Vedere [Limiti delle sottoscrizioni][Limits]. Il peering delle reti virtuali dei carichi di lavoro da sottoscrizioni diverse a un hub centrale consente di superare tali limiti.
- **Separazione delle attività**. È possibile distribuire singoli carichi di lavoro tra i team IT centrali e i team responsabili dei carichi di lavoro.

Gli ambienti cloud di dimensioni più piccole potrebbero non trarre vantaggio dalla struttura e dalle funzionalità aggiuntive offerte da questo modello. Tuttavia, per la maggior parte delle attività di adozione del cloud dovrebbe essere presa in considerazione l'implementazione di un'architettura di rete hub-spoke se vengono riscontrati alcuni dei problemi elencati in precedenza.

> [!NOTE]
> Il sito Architetture di riferimento di Azure contiene modelli di esempio che è possibile usare come base per implementare reti hub-spoke:
>
> - [Implementare una topologia di rete hub-spoke in Azure](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
> - [Implementare una topologia di rete hub-spoke con servizi condivisi in Azure](/azure/architecture/reference-architectures/hybrid-networking/shared-services)

## <a name="overview"></a>Panoramica

![Esempi di una topologia di rete hub-spoke][1]

Come illustrato nel diagramma, Azure supporta due tipi di progettazione hub-spoke. Supporta comunicazione, risorse condivise e criteri di sicurezza centralizzati ("hub VNet" nel diagramma) oppure un tipo di rete WAN virtuale ("WAN virtuale" nel diagramma) per le comunicazioni su larga scala da ramo a ramo e da ramo ad Azure.

L'hub è una zona della rete centrale che controlla e ispeziona il traffico in ingresso o in uscita tra zone: Internet, locale e spoke. La topologia hub-spoke consente al reparto IT di applicare in modo efficace i criteri di sicurezza in una posizione centrale, riducendo al contempo il rischio di configurazione non corretta ed esposizione.

L'hub contiene spesso i componenti dei servizi comuni utilizzati dagli spoke. Di seguito sono riportati alcuni esempi di servizi centrali comuni:

- Infrastruttura di Windows Server Active Directory, necessaria per l'autenticazione utente delle terze parti che accedono da reti non attendibili prima di ottenere l'accesso ai carichi di lavoro nello spoke. Include il componente correlato Active Directory Federation Services (AD FS).
- Servizio DNS per risolvere la denominazione per il carico di lavoro negli spoke, per accedere alle risorse in locale e in Internet se non viene usato [DNS di Azure][DNS].
- Infrastruttura a chiave pubblica (PKI) per implementare Single Sign-On nei carichi di lavoro.
- Controllo di flusso del traffico TCP e UDP tra le zone della rete degli spoke e Internet.
- Controllo di flusso tra gli spoke e le zone locali.
- Se necessario, controllo di flusso tra uno spoke e un altro.

È possibile ridurre al minimo la ridondanza, semplificare la gestione e ridurre i costi complessivi usando l'infrastruttura dell'hub condiviso per supportare più spoke.

Il ruolo di ogni spoke può essere quello di ospitare tipi diversi di carichi di lavoro. Gli spoke consentono anche un approccio modulare per le distribuzioni ripetibili degli stessi carichi di lavoro. Esempi sono sviluppo e test, test di accettazione degli utenti, gestione temporanea e produzione.

Gli spoke possono anche essere usati per isolare e consentire gruppi diversi all'interno dell'organizzazione, ad esempio gruppi Azure DevOps. In uno spoke è possibile distribuire un carico di lavoro di base o carichi di lavoro complessi multilivello con il controllo del traffico tra i livelli.

## <a name="subscription-limits-and-multiple-hubs"></a>Limiti della sottoscrizione e hub multipli

In Azure ogni componente, indipendentemente dal tipo, viene distribuito in una sottoscrizione di Azure. L'isolamento dei componenti di Azure in diverse sottoscrizioni di Azure può soddisfare i requisiti di diverse line-of-business, come la configurazione di livelli differenziati di accesso e autorizzazione.

Una singola implementazione di rete hub-spoke può essere ridimensionata fino a raggiungere un numero elevato di spoke. Tuttavia, come per ogni sistema IT, esistono limiti a livello di piattaforma. La distribuzione dell'hub è associata a una specifica sottoscrizione di Azure, che ha restrizioni e limiti, ad esempio un numero massimo di peering di rete virtuale. Per informazioni dettagliate, vedere [Sottoscrizione di Azure e limiti, quote e vincoli dei servizi][Limits].

Nei casi in cui i limiti possono costituire un problema, è possibile aumentare ulteriormente le prestazioni per l'architettura estendendo il modello da una singola rete hub-spoke a un cluster di hub e spoke. Più hub in una o più aree di Azure possono essere interconnessi usando il peering di rete virtuale, Azure ExpressRoute, una rete WAN virtuale o una VPN da sito a sito.

![Cluster di hub e spoke][2]

L'introduzione di più hub aumenta il costo e l'impegno di gestione del sistema. Questa scelta è giustificabile solo da esigenze di scalabilità, limiti del sistema o ridondanza e dalla replica a livello di area per prestazioni utente o ripristino di emergenza. Negli scenari in cui sono necessari più hub, tutti gli hub devono cercare di offrire lo stesso set di servizi per facilitare le operazioni.

## <a name="interconnection-between-spokes"></a>Interconnessione tra spoke

È possibile implementare carichi di lavoro complessi multilivello in un singolo spoke. È possibile implementare configurazioni a più livelli usando subnet (una per ogni livello) nella stessa rete virtuale e usando gruppi di sicurezza di rete per filtrare i flussi.

Un architetto potrebbe voler distribuire un carico di lavoro multilivello in più reti virtuali. Usando il peering di rete virtuale, gli spoke possono connettersi ad altri spoke nello stesso hub o in hub diversi.

Un esempio tipico di questo scenario è quello in cui i server di elaborazione delle applicazioni sono in uno spoke o rete virtuale, mentre il database viene distribuito in un altro spoke o rete virtuale. In questo caso, è facile interconnettere gli spoke con il peering di rete virtuale ed evitare in tal modo il transito dall'hub. Una soluzione è quella di eseguire un'attenta revisione dell'architettura e della sicurezza per assicurarsi che l'esclusione dell'hub non comporti anche quella di importanti punti di sicurezza e di controllo che potrebbero esistere solo nell'hub.

![Spoke interconnessi e connessi a un hub][3]

Gli spoke possono anche essere interconnessi a uno spoke che funge da hub. Questo approccio crea una gerarchia a due livelli: lo spoke nel livello superiore (livello 0) diventa l'hub degli spoke inferiori (livello 1) nella gerarchia. Gli spoke di un'implementazione di tipo hub-spoke devono inoltrare il traffico all'hub centrale in modo che il traffico possa transitare verso la destinazione nella rete locale o nella rete Internet pubblica. Un'architettura con due livelli di hub crea un routing complesso che elimina i vantaggi di una relazione hub-spoke semplice.

<!-- images -->

[0]: ./images/network-redundant-equipment.png "Esempi di sovrapposizione di componenti"
[1]: ./images/network-hub-spoke-high-level.png "Esempio generale di hub e spoke"
[2]: ./images/network-hub-spokes-cluster.png "Cluster di hub e spoke"
[3]: ./images/network-spoke-to-spoke.png "Da spoke a spoke"
[4]: ./images/network-hub-spoke-block-level-diagram.png "Diagramma a blocchi di hub e spoke"
[5]: ./images/network-users-groups-subsciptions.png "Utenti, gruppi, sottoscrizioni e progetti"
[6]: ./images/network-infrastructure-high-level.png "Diagramma dell'infrastruttura generale"
[7]: ./images/network-highlevel-perimeter-networks.png "Diagramma dell'infrastruttura generale"
[8]: ./images/network-vnet-peering-perimeter-neworks.png "Peering di rete virtuale e reti perimetrali"
[9]: ./images/network-high-level-diagram-monitoring.png "Diagramma generale per il monitoraggio"
[10]: ./images/network-high-level-workloads.png "Diagramma generale per il carico di lavoro"

<!-- links -->

[Limits]: /azure/azure-subscription-service-limits
[Roles]: /azure/role-based-access-control/built-in-roles
[VNet]: /azure/virtual-network/virtual-networks-overview
[network-security-groups]: /azure/virtual-network/virtual-networks-nsg
[DNS]: /azure/dns/dns-overview
[PrivateDNS]: /azure/dns/private-dns-overview
[VNetPeering]: /azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: /azure/virtual-network/virtual-networks-udr-overview
[RBAC]: /azure/role-based-access-control/overview
[azure-ad]: /azure/active-directory/active-directory-whatis
[VPN]: /azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: /azure/expressroute/expressroute-introduction
[ExRD]: /azure/expressroute/expressroute-erdirect-about
[vWAN]: /azure/virtual-wan/virtual-wan-about
[NVA]: /azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: /azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: /azure/azure-resource-manager/resource-group-overview
[DMZ]: /azure/best-practices-network-security
[ALB]: /azure/load-balancer/load-balancer-overview
[PIP]: /azure/virtual-network/resource-groups-networking#public-ip-address
[AFD]: /azure/frontdoor/front-door-overview
[AppGW]: /azure/application-gateway/application-gateway-introduction
[WAF]: /azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: /azure/monitoring-and-diagnostics/
[ActLog]: /azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: /azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: /azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: /azure/operations-management-suite/operations-management-suite-overview
[NPM]: /azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: /azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: /azure/app-service/
[HDI]: /azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: /azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: /azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: /azure/traffic-manager/traffic-manager-overview
