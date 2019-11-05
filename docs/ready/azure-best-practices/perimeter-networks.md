---
title: Reti perimetrali
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Reti perimetrali
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 95a2bf325615c7eb765ad747d0aad16f008e015d
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564029"
---
# <a name="perimeter-networks"></a>Reti perimetrali

Le [reti perimetrali][perimeter-network] consentono la connettività sicura tra le reti cloud e le reti dei data center locali o fisici, oltre alla connettività da e verso Internet.

Per rendere efficaci le reti perimetrali, è necessario che i pacchetti in ingresso attraversino le appliance di sicurezza ospitate in subnet sicure prima di raggiungere i server back-end. Il firewall, i sistemi di rilevamento intrusioni e i sistemi di prevenzione intrusioni sono solo alcuni esempi. Prima di lasciare la rete, anche i pacchetti diretti a Internet dai carichi di lavoro devono attraversare le appliance di sicurezza nella rete perimetrale. Le finalità di questa operazione sono l'applicazione dei criteri, l'ispezione e il controllo.

Le reti perimetrali usano le funzionalità e i servizi di Azure seguenti:

- [Reti virtuali][virtual-networks], [route definite dall'utente][user-defined-routes] e [gruppi di sicurezza di rete][network-security-groups]
- [Appliance virtuali di rete (appliance virtuali)][NVA]
- [Servizio di bilanciamento del carico di Azure][ALB]
- [Gateway][AppGW] e web application firewall di applicazione Azure [(WAF)][AppGWWAF]
- [IP pubblici][PIP]
- [Frontdoor di Azure][AFD] con [web application firewall][AFDWAF]
- [Firewall di Azure][AzFW]

> [!NOTE]
> Le architetture di riferimento di Azure forniscono modelli di esempio che è possibile usare per implementare le proprie reti perimetrali:
>
> - [Implementare una rete perimetrale tra Azure e il data center locale](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid)
> - [Implementare una rete perimetrale tra Azure e Internet](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz)

I team IT e di sicurezza centrali in genere sono responsabili della definizione dei requisiti per il funzionamento delle reti perimetrali.

![Esempio di una topologia di rete hub-spoke][7]

Il diagramma precedente mostra una [topologia di rete Hub e spoke](./hub-spoke-network-topology.md) di esempio che implementa l'applicazione di due perimetri con accesso a Internet e a una rete locale. Entrambi i perimetri risiedono nell'hub della rete perimetrale. In tale hub la rete perimetrale verso Internet può aumentare le prestazioni per supportare molte applicazioni line-of-business, usando più farm di WAF e istanze di Firewall di Azure che contribuiscono a proteggere le reti virtuali spoke. L'hub consente anche la connettività tramite VPN o Azure ExpressRoute in base alle esigenze.

## <a name="virtual-networks"></a>Reti virtuali

Le reti perimetrali di solito si basano su una [rete virtuale][virtual-networks] con più subnet per ospitare i diversi tipi di servizi che filtrano e ispezionano il traffico verso o da Internet tramite appliance virtuali di rete, WAF e istanze del gateway applicazione di Azure.

## <a name="user-defined-routes"></a>Route definite dall'utente

Usando [route definite dall'utente][user-defined-routes], i clienti possono distribuire firewall, sistemi di rilevamento intrusioni o sistemi di prevenzione intrusioni e altre appliance virtuali. I clienti possono quindi instradare il traffico di rete attraverso queste appliance di sicurezza per l'applicazione dei criteri relativi ai limiti di sicurezza, il controllo e l'ispezione. È possibile creare route definite dall'utente per garantire che il traffico passi attraverso le macchine virtuali personalizzate, le appliance virtuali di rete e i servizi di bilanciamento del carico specificati.

In un esempio di rete hub-spoke, la garanzia che il traffico generato dalle macchine virtuali che risiedono nel spoke passa attraverso le appliance virtuali corrette nell'Hub richiede una route definita dall'utente definita nelle subnet della spoke. Tale route imposta l'indirizzo IP front-end del servizio di bilanciamento del carico interno come hop successivo. Il servizio di bilanciamento del carico interno distribuisce il traffico interno alle appliance virtuali (pool back-end di bilanciamento del carico).

## <a name="azure-firewall"></a>Firewall di Azure

[Firewall di Azure][AzFW] è un servizio gestito basato sul cloud che consente di proteggere le risorse della rete virtuale di Azure. È un firewall gestito con stato completo con disponibilità elevata incorporata e scalabilità cloud senza limiti. È possibile creare, applicare e registrare criteri di connettività di applicazione e di rete in modo centralizzato tra le sottoscrizioni e le reti virtuali.

Firewall di Azure usa un indirizzo IP pubblico statico per le risorse della rete virtuale consentendo ai firewall esterni di identificare il traffico proveniente dalla rete virtuale. Il servizio interagisce con Monitoraggio di Azure per la registrazione e l'analisi.

## <a name="network-virtual-appliances"></a>Appliance virtuali di rete

Le reti perimetrali con accesso a Internet in genere vengono gestite tramite un'istanza di Firewall di Azure oppure una farm di firewall o [web application firewall][AFDWAF].

Line-of-business diverse usano in genere numerose applicazioni Web che tendono a essere soggette a svariate vulnerabilità e potenziali exploit. Un web application firewall rileva gli attacchi contro le applicazioni Web (HTTP/HTTPS) in modo più approfondito di quanto farebbe un firewall generico. Rispetto alla tradizionale tecnologia firewall, i web application firewall hanno un set di funzionalità specifiche che contribuiscono a proteggere i server Web interni dalle minacce.

Un'istanza di Firewall di Azure e un firewall delle [appliance virtuali di rete][NVA] usano un piano di amministrazione comune con un set di regole di sicurezza per contribuire a proteggere i carichi di lavoro ospitati negli spoke e controllare l'accesso alle reti locali. Firewall di Azure ha la scalabilità incorporata, mentre i firewall delle appliance virtuali di rete possono essere ridimensionati manualmente dietro un servizio di bilanciamento del carico.

Una farm di firewall di solito ha un software meno specializzato rispetto a un WAF, ma ha un ambito di applicazione più ampio per filtrare e ispezionare ogni tipo di traffico in uscita e in ingresso. Se si usa un approccio che prevede appliance virtuali di rete, è possibile trovare e distribuire il software da Azure Marketplace.

Usare un set di istanze di Firewall di Azure (o appliance virtuali di rete) per il traffico che ha origine in Internet e un altro set per il traffico che ha origine in locale. L'uso di un solo set di firewall per entrambi i tipi di traffico costituisce un rischio per la sicurezza perché non viene fornito alcun perimetro di sicurezza tra i due set di traffico di rete. L'uso di livelli di firewall separati riduce la complessità del controllo delle regole di sicurezza e indica chiaramente la corrispondenza tra le regole e le richieste di rete in ingresso.

## <a name="azure-load-balancer"></a>Servizio di bilanciamento del carico di Azure

[Azure Load Balancer][ALB] offre un servizio a disponibilità elevata di livello 4 (TCP/UDP) in grado di distribuire il traffico in ingresso tra le istanze del servizio definite in set con carico bilanciato. Il traffico inviato al servizio di bilanciamento del carico dagli endpoint front-end (endpoint IP pubblici o endpoint IP privati) può essere ridistribuito con o senza conversione degli indirizzi in un pool di indirizzi IP back-end (ad esempio, appliance virtuali di rete o macchine virtuali).

Azure Load Balancer può anche verificare l'integrità delle varie istanze del server. Quando un'istanza non riesce a rispondere a un probe, il servizio di bilanciamento del carico smette di inviare il traffico all'istanza non integra.

Come esempio di utilizzo di una topologia di rete hub-spoke, è possibile distribuire un servizio di bilanciamento del carico esterno sia nell'hub che negli spoke. Nell'hub il servizio di bilanciamento del carico instrada in modo efficiente il traffico ai servizi negli spoke. Nei spoke i servizi di bilanciamento del carico gestiscono il traffico dell'applicazione.

## <a name="azure-front-door-service"></a>Servizio Frontdoor di Azure

Il [servizio Frontdoor di Azure][AFD] è un servizio Microsoft a scalabilità e disponibilità elevata di piattaforma di accelerazione dell'applicazione Web e bilanciamento del carico HTTPS globale. È possibile usare il servizio Frontdoor di Azure per compilare, gestire e scalare orizzontalmente l'applicazione Web dinamica e il contenuto statico. È in esecuzione in oltre 100 posizioni sul perimetro della rete globale Microsoft.

Il servizio Frontdoor di Azure assicura all'applicazione automazione della manutenzione regionale/con indicatore data e ora unificata, automazione della continuità aziendale e ripristino di emergenza, informazioni client/utente unificate, memorizzazione nella cache e informazioni dettagliate sul servizio. La piattaforma garantisce prestazioni, affidabilità e contratti di servizio di supporto tecnico, oltre a certificazioni di conformità e procedure di sicurezza controllabili sviluppate, gestite e supportate in modo nativo da Azure.

## <a name="application-gateway"></a>gateway applicazione

Il [gateway applicazione di Azure][AppGW] è un'appliance virtuale dedicata che offre un controller gestito per la distribuzione di applicazioni e varie funzionalità di bilanciamento del carico di livello 7 per l'applicazione.

Il gateway applicazione consente di ottimizzare la produttività delle Web farm eseguendo l'offload al gateway applicazione della terminazione SSL con utilizzo elevato di CPU. Offre anche altre funzionalità di routing di livello 7, tra cui la distribuzione round robin del traffico in ingresso, l'affinità di sessione basata su cookie, il routing basato su percorso URL e la possibilità di ospitare più siti Web dietro un unico gateway applicazione.

Lo SKU WAF del gateway applicazione include un web application firewall. Questo SKU offre alle applicazioni Web la protezione da exploit e vulnerabilità Web comuni. È possibile configurare il gateway applicazione come gateway con connessione Internet, come gateway solo interno o come una combinazione di queste due opzioni.

## <a name="public-ips"></a>Indirizzi IP pubblici

Alcune funzionalità di Azure consentono di associare gli endpoint di servizio a un indirizzo [IP pubblico][PIP] in modo che la risorsa sia accessibile da Internet. Questo endpoint usa il processo NAT (Network Address Translation) per instradare il traffico fino all'indirizzo e alla porta interni nella rete virtuale di Azure. È questa la modalità primaria che consente al traffico esterno di passare attraverso la rete virtuale. Gli indirizzi IP pubblici possono essere configurati per determinare il traffico autorizzato a passare e come/dove viene convertito nella rete virtuale.

## <a name="azure-ddos-protection-standard"></a>Protezione DDoS di Azure Standard

[Protezione DDoS di Azure Standard][DDoS] offre funzionalità aggiuntive di mitigazione tramite il livello di [servizio Basic][DDoS] ottimizzate in modo specifico per le risorse della rete virtuale di Azure. Protezione DDoS Standard è semplice da abilitare e non richiede alcuna modifica alle applicazioni.

È possibile ottimizzare i criteri di protezione tramite il monitoraggio del traffico dedicato e algoritmi di Machine Learning. I criteri vengono applicati agli indirizzi IP pubblici associati alle risorse distribuite nelle reti virtuali, ad esempio le istanze di Azure Load Balancer, del gateway applicazione di Azure e di Azure Service Fabric.

La telemetria in tempo reale è disponibile tramite le viste di Monitoraggio di Azure sia durante un attacco sia a fini cronologici. È possibile aggiungere protezione al livello dell'applicazione tramite il web application firewall nel gateway applicazione di Azure. La protezione viene fornita per gli indirizzi IP pubblici di Azure IPv4.

<!-- images -->

[0]: ../../_images/azure-best-practices/network-redundant-equipment.png "Esempi di sovrapposizione di componenti"
[1]: ../../_images/azure-best-practices/network-hub-spoke-high-level.png "Esempio generale di hub e spoke"
[2]: ../../_images/azure-best-practices/network-hub-spokes-cluster.png "Cluster di hub e spoke"
[3]: ../../_images/azure-best-practices/network-spoke-to-spoke.png "Da spoke a spoke"
[4]: ../../_images/azure-best-practices/network-hub-spoke-block-level-diagram.png "Diagramma del livello di blocco di hub e spoke"
[5]: ../../_images/azure-best-practices/network-users-groups-subscriptions.png "Utenti, gruppi, sottoscrizioni e progetti"
[6]: ../../_images/azure-best-practices/network-infrastructure-high-level.png "Diagramma dell'infrastruttura generale"
[7]: ../../_images/azure-best-practices/network-high-level-perimeter-networks.png "Diagramma dell'infrastruttura generale"
[8]: ../../_images/azure-best-practices/network-vnet-peering-perimeter-networks.png "Peering reti virtuali e reti perimetrali"
[9]: ../../_images/azure-best-practices/network-high-level-diagram-monitoring.png "Diagramma generale per il monitoraggio"
[10]: ../../_images/azure-best-practices/network-high-level-workloads.png "Diagramma generale per il carico di lavoro"

<!-- links -->

[Limits]: https://docs.microsoft.com/azure/azure-subscription-service-limits
[Roles]: https://docs.microsoft.com/azure/role-based-access-control/built-in-roles
[virtual-networks]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[network-security-groups]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg
[DNS]: https://docs.microsoft.com/azure/dns/dns-overview
[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[VNetPeering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[azure-ad]: https://docs.microsoft.com/azure/active-directory/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[vWAN]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[SubMgmt]: https://docs.microsoft.com/azure/architecture/cloud-adoption/reference/azure-scaffold
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview
[perimeter-network]: https://docs.microsoft.com/azure/best-practices-network-security
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[DDoS]: https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/virtual-network-public-ip-address
[AFD]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AFDWAF]: https://docs.microsoft.com/azure/frontdoor/waf-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction
[AppGWWAF]: https://docs.microsoft.com/azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/
[ActLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: https://docs.microsoft.com/azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview
[NPM]: https://docs.microsoft.com/azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: https://docs.microsoft.com/azure/app-service/
[HDI]: https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview
