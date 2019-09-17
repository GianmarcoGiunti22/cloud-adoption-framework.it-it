---
title: Guida al monitoraggio del cloud-strategia di monitoraggio per i modelli di distribuzione cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 3659f5e965e5a80c3b490f8b106a4cc30f1711a9
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030760"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guida al monitoraggio del cloud: Strategia di monitoraggio per i modelli di distribuzione cloud

Questo articolo include la strategia di monitoraggio consigliata per ognuno dei modelli di distribuzione cloud, in base ai criteri seguenti:

- È necessario un impegno continuo per Operations Manager o un'altra piattaforma di monitoraggio aziendale. Questo è dovuto all'integrazione con i processi, le conoscenze e le competenze delle operazioni IT o perché alcune funzionalità non sono ancora disponibili in monitoraggio di Azure.
- È necessario monitorare i carichi di lavoro sia in locale che nel cloud pubblico oppure solo nel cloud.
- La strategia di migrazione cloud include la modernizzazione delle operazioni IT e il passaggio alle soluzioni e ai servizi di monitoraggio cloud.
- Potrebbero essere presenti sistemi critici, gapped o fisicamente isolati, ospitati in un cloud privato o su hardware fisico e che devono essere monitorati.

Questa strategia include il supporto per il monitoraggio dell'infrastruttura (elaborazione, archiviazione e carichi di lavoro del server), l'applicazione (utente finale, le eccezioni e il client) e le risorse di rete per offrire una prospettiva di monitoraggio completa e orientata ai servizi.

## <a name="azure-cloud-monitoring"></a>Monitoraggio cloud di Azure

Monitoraggio di Azure è il servizio di piattaforma che mette a disposizione un'unica origine per il monitoraggio delle risorse di Azure. È progettato per le soluzioni cloud basate su Azure e che supportano una funzionalità aziendale basata sui carichi di lavoro delle macchine virtuali o su architetture complesse che usano microservizi e altre risorse della piattaforma. Monitora tutti i livelli dello stack, a partire da servizi tenant come Azure Active Directory Domain Services ed eventi a livello di sottoscrizione e integrità dei servizi di Azure. Monitora anche le risorse dell'infrastruttura, ad esempio macchine virtuali, archiviazione e risorse di rete, e, al livello superiore, l'applicazione. Monitorando ognuna di queste dipendenze e raccogliendo i segnali corretti che ognuno può emettere, offre l'osservabilità delle applicazioni e l'infrastruttura chiave necessaria.

La tabella seguente riepiloga l'approccio consigliato per il monitoraggio di ogni livello dello stack.

<!-- markdownlint-disable MD033 -->

Livello | Risorsa | Ambito | Metodo
---|---|---|----
Applicazione | Applicazione basata sul Web in esecuzione su .NET, .NET Core, Java, JavaScript e piattaforma node. js in una VM di Azure, app Azure Services, Azure Service Fabric, funzioni di Azure e servizi cloud di Azure | Monitorare un'applicazione Web Live per rilevare automaticamente le anomalie delle prestazioni, identificare le eccezioni e i problemi del codice e raccogliere dati di telemetria sull'usabilità. |  Application Insights
Contenitori | Azure Kubernetes Service/istanze di contenitore di Azure | Monitoraggio della capacità, della disponibilità e delle prestazioni dei carichi di lavoro in esecuzione su contenitori e istanze di contenitore. | Monitoraggio di Azure per i contenitori
Sistema operativo guest | Sistema operativo VM Linux e Windows | Monitoraggio della capacità, della disponibilità e delle prestazioni. Eseguire il mapping delle dipendenze ospitate in ogni VM, inclusa la visibilità delle connessioni di rete attive tra server, latenza di connessione in ingresso e in uscita e porte in qualsiasi architettura connessa a TCP. | Monitoraggio di Azure per le macchine virtuali
Risorse di Azure-PaaS | Servizi di database di Azure (ad esempio, SQL o mySQL) | Metriche delle prestazioni del database di Azure per SQL. | Abilitare la registrazione diagnostica per trasmettere i dati SQL ai log di monitoraggio di Azure.
Risorse di Azure-IaaS | 1. Archiviazione di Azure<br/> 2. Gateway applicazione di Azure<br/> 3. Azure Key Vault<br/> 4. Gruppi di sicurezza di rete<br/> 5. Gestione traffico di Azure | 1. Capacità, disponibilità e prestazioni.<br/> 2. Log di diagnostica e prestazioni (attività, accesso, prestazioni e firewall).<br/> 3. Monitorare come e quando viene eseguito l'accesso agli insiemi di credenziali delle chiavi e da chi.<br/> 4. Monitorare gli eventi quando vengono applicate le regole e il contatore delle regole per il numero di volte in cui una regola viene applicata a Deny o Allow.<br/>5. Monitorare la disponibilità dello stato dell'endpoint. | 1. Metriche di archiviazione per l'archiviazione BLOB.<br/> 2. Abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.<br/> 3. Abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure e abilitare la [soluzione Azure Key Vault Analytics](https://docs.microsoft.com/azure/azure-monitor/insights/azure-key-vault). <br/> 4. Abilitare la registrazione diagnostica dei gruppi di sicurezza di rete e configurare lo streaming nei log di monitoraggio di Azure.<br/> 5. Abilitare la registrazione diagnostica degli endpoint di gestione traffico e configurare lo streaming nei log di monitoraggio di Azure.
Rete| Comunicazione tra la macchina virtuale e uno o più endpoint (un'altra VM, un nome di dominio completo, un identificatore di risorsa uniforme o un indirizzo IPv4). | Monitorare la raggiungibilità, la latenza e le modifiche alla topologia di rete che si verificano tra la macchina virtuale e l'endpoint. | Azure Network Watcher
Sottoscrizione di Azure | Integrità del servizio di Azure e integrità delle risorse di base | <li> Azioni amministrative eseguite su un servizio o una risorsa.<br/><li> L'integrità del servizio con un servizio di Azure è in uno stato danneggiato o non disponibile.<br/><li> Problemi di integrità rilevati con una risorsa di Azure dal punto di vista del servizio di Azure.<br/><li> Operazioni eseguite con la scalabilità automatica di Azure che indicano un errore o un'eccezione. <br/><li> Operazioni eseguite con criteri di Azure che indicano che si è verificata un'azione consentita o negata.<br/><li> Record degli avvisi generati dal centro sicurezza di Azure. |Recapitato nel log attività per il monitoraggio e l'invio di avvisi tramite Azure Resource Manager.
Tenant di Azure|Azure Active Directory || Abilitare la registrazione diagnostica e configurare lo streaming nei log di monitoraggio di Azure.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Monitoraggio del cloud ibrido

Questa sezione è attualmente in fase di sviluppo per offrire un set completo di consigli destinati a soddisfare l'interesse per questo modello cloud e sarà disponibile a breve.  

## <a name="private-cloud-monitoring"></a>Monitoraggio del cloud privato

È possibile ottenere il monitoraggio olistico di Azure Stack con System Center Operations Manager. In particolare, è possibile monitorare i carichi di lavoro in esecuzione nel tenant, il livello di risorse, le macchine virtuali e l'infrastruttura che ospita Azure Stack (server fisici e commutatori di rete). È anche possibile ottenere il monitoraggio olistico con una combinazione di [funzionalità di monitoraggio dell'infrastruttura](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluse in Azure stack. Queste funzionalità consentono di visualizzare lo stato e gli avvisi per un'area Azure Stack e il [servizio monitoraggio di Azure](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) in Azure stack, che fornisce metriche e log dell'infrastruttura di livello base per la maggior parte dei servizi.

Se si è già investito in Operations Manager, usare il Management Pack Azure Stack per monitorare lo stato di disponibilità e integrità delle distribuzioni Azure Stack. Sono incluse le aree, i provider di risorse, gli aggiornamenti, le esecuzioni di aggiornamenti, le unità di scala, i nodi unità, i ruoli infrastruttura e le relative istanze (entità logiche costituite dalle risorse hardware). Usa le API REST del provider di risorse di integrità e aggiornamento per comunicare con Azure Stack. Per monitorare i server fisici e i dispositivi di archiviazione, usare l'Management Pack dei fornitori OEM (ad esempio, fornito da Lenovo, Hewlett Packard o dell). Operations Manager possibile monitorare in modo nativo i commutatori di rete per raccogliere statistiche di base tramite il protocollo SNMP. Il monitoraggio dei carichi di lavoro del tenant è possibile con il Management Pack di Azure seguendo due passaggi di base. Configurare la sottoscrizione che si desidera monitorare e quindi aggiungere i monitoraggi per tale sottoscrizione.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Raccolta dei dati appropriati](./data-collection.md)
