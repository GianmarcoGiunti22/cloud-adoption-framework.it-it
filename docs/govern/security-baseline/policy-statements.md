---
title: Definizioni dei criteri di esempio per la baseline di sicurezza
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definizioni dei criteri di esempio per la baseline di sicurezza
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 253646b16d98a35c8cae8eb7f5c57aa60d55d580
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027575"
---
# <a name="security-baseline-sample-policy-statements"></a>Definizioni dei criteri di esempio per la baseline di sicurezza

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà risolto da questi criteri.
- **Definizione dei criteri**: Una spiegazione chiara e riepilogativa dei requisiti dei criteri.
- **Opzioni tecniche:** Suggerimenti pratici, specifiche o altre linee guida che i team IT e gli sviluppatori possono usare quando implementano i criteri.

Le istruzioni dei criteri di esempio seguenti affrontano i rischi aziendali comuni correlati alla sicurezza. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team aziendali, di sicurezza e IT per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="asset-classification"></a>Classificazione degli asset

**Rischio tecnico:** è possibile che gli asset non correttamente identificati come cruciali o che interessano dati sensibili non siano sufficientemente protetti, con conseguenti potenziali perdite di dati o interruzioni delle attività aziendali.

**Definizione dei criteri**: tutti gli asset distribuiti devono essere ordinati in categorie in base a criticità e classificazione dei dati. Le classificazioni devono essere esaminate dal team di governance del cloud e dal proprietario dell'applicazione prima della distribuzione nel cloud.

**Possibili opzioni di progettazione:** stabilire [standard di applicazione di tag alle risorse](../../decision-guides/resource-tagging/index.md) e assicurarsi che il personale IT li applichi in modo coerente alle risorse distribuite usando i [tag delle risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="data-encryption"></a>Crittografia dei dati

**Rischio tecnico:** esiste il rischio che i dati protetti vengano esposti durante l'archiviazione.

**Definizione dei criteri**: tutti i dati protetti devono essere crittografati quando inattivi.

**Possibili opzioni di progettazione:** vedere l'articolo [Panoramica della crittografia di Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview) per informazioni su come viene eseguita la crittografia dei dati inattivi nella piattaforma Azure.

## <a name="network-isolation"></a>Isolamento rete

**Rischio tecnico:** la connettività tra le reti e le subnet all'interno delle reti introduce potenziali vulnerabilità che possono comportare perdite di dati o interruzioni di servizi critici.

**Definizione dei criteri**: le subnet di rete contenenti dati protetti devono essere isolate dalle altre subnet. Il traffico di rete tra le subnet di dati protetti deve essere controllato regolarmente.

**Possibili opzioni di progettazione:** In Azure l'isolamento delle reti e delle subnet viene gestito con [Reti virtuali di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="secure-external-access"></a>Accesso esterno sicuro

**Rischio tecnico:** consentire l'accesso ai carichi di lavoro dalla rete Internet pubblica introduce un rischio di intrusione con conseguente esposizione non autorizzata dei dati e interruzione delle attività aziendali.

**Definizione dei criteri**: alle subnet contenenti dati protetti non deve essere possibile accedere direttamente tramite la rete Internet pubblica o tra data center. L'accesso a tali subnet deve essere instradato tramite una subnet intermedia. Tutti gli accessi a tali subnet devono passare attraverso una soluzione firewall in grado di eseguire la scansione dei pacchetti e applicare funzioni di blocco.

**Possibili opzioni di progettazione:** in Azure proteggere gli endpoint pubblici distribuendo una [rete perimetrale tra la rete Internet pubblica e la rete basata sul cloud](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz).

## <a name="ddos-protection"></a>Protezione da attacchi DDoS

**Rischio tecnico:** gli attacchi Distributed Denial of Service (DDoS) possono comportare un'interruzione delle attività aziendali.

**Definizione dei criteri**: distribuire meccanismi automatizzati di mitigazione degli attacchi DDoS in tutti gli endpoint di rete accessibili pubblicamente.

**Possibili opzioni di progettazione:** usare [Protezione DDoS di Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) per ridurre al minimo le interruzioni causate dagli attacchi DDoS.

## <a name="secure-on-premises-connectivity"></a>Proteggere la connettività locale

**Rischio tecnico:** il traffico non crittografato tra la rete cloud e l'ambiente locale tramite la rete Internet pubblica è vulnerabile alle intercettazioni e comporta quindi il rischio di esposizione dei dati.

**Definizione dei criteri**: tutte le connessioni tra le reti locali e cloud devono essere stabilite tramite una connessione VPN sicura crittografata o un collegamento WAN dedicato privato.

**Possibili opzioni di progettazione:** in Azure usare ExpressRoute o la VPN di Azure per stabilire connessioni private tra le reti locali e cloud.

## <a name="network-monitoring-and-enforcement"></a>Monitoraggio della rete e applicazione di controlli

**Rischio tecnico:** le modifiche alla configurazione della rete possono comportare nuove vulnerabilità e rischi di esposizione dei dati.

**Definizione dei criteri**: gli strumenti di governance devono controllare e soddisfare i requisiti di configurazione definiti dal team della baseline di sicurezza.

**Possibili opzioni di progettazione:** In Azure l'attività di rete può essere monitorata con [Azure Network Watcher](https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview), mentre il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-network-recommendations) consente di identificare le vulnerabilità di sicurezza. Criteri di Azure consente di limitare le risorse di rete e i criteri di configurazione delle risorse in base ai limiti definiti dal team responsabile della sicurezza.

## <a name="security-review"></a>Verifica della sicurezza

**Rischio tecnico:** nel corso del tempo, emergono nuove minacce alla sicurezza e tipi di attacchi, che aumentano il rischio di esposizione o di interruzione delle risorse cloud.

**Definizione dei criteri**: tendenze e potenziali exploit che possono influire sulle distribuzioni cloud devono essere esaminati regolarmente dal team responsabile della sicurezza in modo da fornire aggiornamenti per gli strumenti della baseline di sicurezza usati nel cloud.

**Possibili opzioni di progettazione:** pianificare riunioni periodiche con i membri principali dei team responsabili dell'IT e della governance al fine di verificare la sicurezza. Esaminare i dati di sicurezza e le metriche esistenti per stabilire i gap nei criteri correnti e gli strumenti di base della sicurezza e aggiornare i criteri per correggere eventuali nuovi rischi.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per elaborare criteri applicabili a rischi per la sicurezza specifici, in linea con i piani di adozione del cloud.

Per iniziare a sviluppare definizioni dei criteri personalizzate correlate alla baseline di sicurezza, scaricare il [modello di baseline di sicurezza](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri della Baseline di sicurezza.

> [!div class="nextstepaction"]
> [Stabilire i processi di conformità ai criteri](./compliance-processes.md)
