---
title: Definizioni dei criteri di esempio per la baseline di sicurezza
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definizioni dei criteri di esempio per la baseline di sicurezza
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 312a3f4e6577b0a0db525e6428bf7e1b2616b625
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160523"
---
# <a name="security-baseline-sample-policy-statements"></a>Definizioni dei criteri di esempio per la baseline di sicurezza

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà indirizzato da questo criterio.
- **Istruzione per i criteri:** Una chiara spiegazione di riepilogo dei requisiti dei criteri.
- **Opzioni tecniche:** Raccomandazioni di utilità pratica, specifiche o altre istruzioni che i team IT e gli sviluppatori possono usare per l'implementazione dei criteri.

Le istruzioni dei criteri di esempio seguenti affrontano i rischi aziendali comuni correlati alla sicurezza. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team aziendali, di sicurezza e IT per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="asset-classification"></a>Classificazione degli asset

**Rischio tecnico:** Gli asset che non sono stati identificati correttamente come cruciali o che coinvolgono dati sensibili potrebbero non ricevere protezioni sufficienti, causando potenziali perdite di dati o problemi aziendali.

**Istruzione per i criteri:** Tutti gli asset distribuiti devono essere classificati in base alla criticità e alla classificazione dei dati. Le classificazioni devono essere esaminate dal team di governance del cloud e dal proprietario dell'applicazione prima della distribuzione nel cloud.

**Possibili opzioni di progettazione:** Definire [gli standard di tag delle risorse](../../decision-guides/resource-tagging/index.md) e assicurarsi che il personale IT li applichi costantemente alle risorse distribuite usando i [tag delle risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="data-encryption"></a>Crittografia dei dati

**Rischio tecnico:** Il rischio che i dati protetti vengano esposti durante l'archiviazione.

**Istruzione per i criteri:** Tutti i dati protetti devono essere crittografati quando sono inattivi.

**Possibili opzioni di progettazione:** Vedere l'articolo [Panoramica della crittografia di Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview) per una descrizione del modo in cui viene eseguita la crittografia dei dati inattivi sulla piattaforma Azure. Devono essere considerati anche controlli aggiuntivi come la crittografia dei dati dell'account e il controllo della modifica delle impostazioni dell'account di archiviazione.

## <a name="network-isolation"></a>Isolamento rete

**Rischio tecnico:** La connettività tra le reti e le subnet all'interno delle reti introduce potenziali vulnerabilità che possono causare perdite di dati o interruzione di servizi cruciali.

**Istruzione per i criteri:** Le subnet di rete contenenti dati protetti devono essere isolate dalle altre subnet. Il traffico di rete tra le subnet di dati protetti deve essere controllato regolarmente.

**Possibili opzioni di progettazione:** In Azure, l'isolamento della rete e della subnet viene gestito tramite le [reti virtuali di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="secure-external-access"></a>Accesso esterno sicuro

**Rischio tecnico:** Consentendo l'accesso ai carichi di lavoro dalla rete Internet pubblica, viene introdotto il rischio di intrusione, causando un'esposizione non autorizzata ai dati o un'eventuale interferenza aziendale.

**Istruzione per i criteri:** Non è possibile accedere direttamente a nessuna subnet contenente dati protetti tramite Internet pubblico o tra più data center. L'accesso a tali subnet deve essere instradato tramite subnet intermedie. Tutti gli accessi a tali subnet devono passare attraverso una soluzione firewall in grado di eseguire la scansione dei pacchetti e applicare funzioni di blocco.

**Possibili opzioni di progettazione:** In Azure proteggere gli endpoint pubblici distribuendo una rete perimetrale [tra la rete Internet pubblica e la rete basata sul cloud](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Prendere in considerazione la distribuzione, la configurazione e l'automazione del [firewall di Azure](https://docs.microsoft.com/azure/firewall).

## <a name="ddos-protection"></a>Protezione da attacchi DDoS

**Rischio tecnico:** Gli attacchi di tipo Denial of Service (DDoS) distribuiti possono causare interruzioni aziendali.

**Istruzione per i criteri:** Distribuire meccanismi di mitigazione DDoS automatici a tutti gli endpoint di rete accessibili pubblicamente. Nessun sito Web pubblico supportato da IaaS dovrebbe essere esposto a Internet senza DDoS.

**Possibili opzioni di progettazione:** Usare la [protezione DDoS di Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) standard per ridurre al minimo le rotture dovute ad attacchi DDoS.

## <a name="secure-on-premises-connectivity"></a>Proteggere la connettività locale

**Rischio tecnico:** Il traffico non crittografato tra la rete cloud e l'ambiente locale tramite Internet pubblico è vulnerabile all'intercettazione, introducendo il rischio di esposizione dei dati.

**Istruzione per i criteri:** Tutte le connessioni tra le reti locali e cloud devono essere applicate tramite una connessione VPN crittografata protetta o un collegamento WAN privato dedicato.

**Possibili opzioni di progettazione:** In Azure usare ExpressRoute o la VPN di Azure per stabilire connessioni private tra le reti locali e cloud.

## <a name="network-monitoring-and-enforcement"></a>Monitoraggio della rete e applicazione di controlli

**Rischio tecnico:** Le modifiche alla configurazione di rete possono comportare nuove vulnerabilità e rischi per l'esposizione dei dati.

**Istruzione per i criteri:** Gli strumenti di governance devono controllare e applicare i requisiti di configurazione di rete definiti dal team di base di sicurezza.

**Possibili opzioni di progettazione:** In Azure è possibile monitorare l'attività di rete con [azure Network Watcher](https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview)e il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-network-recommendations) può aiutare a identificare le vulnerabilità della sicurezza. Criteri di Azure consente di limitare le risorse di rete e i criteri di configurazione delle risorse in base ai limiti definiti dal team responsabile della sicurezza.

## <a name="security-review"></a>Verifica della sicurezza

**Rischio tecnico:** Nel tempo, emergono nuove minacce per la sicurezza e tipi di attacco, aumentando il rischio di esposizione o distruzione delle risorse cloud.

**Istruzione per i criteri:** Le tendenze e i potenziali exploit che possono influenzare le distribuzioni cloud devono essere esaminati regolarmente dal team di sicurezza per fornire aggiornamenti agli strumenti di base della sicurezza usati nel cloud.

**Possibili opzioni di progettazione:** Stabilire una riunione di revisione della sicurezza regolare che includa i membri del team IT e di governance pertinenti. Esaminare i dati di sicurezza e le metriche esistenti per stabilire i gap nei criteri correnti e gli strumenti di base della sicurezza e aggiornare i criteri per correggere eventuali nuovi rischi. Sfrutta [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) e il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) per ottenere informazioni dettagliate di utilità pratica sulle minacce emergenti specifiche per le distribuzioni.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per elaborare criteri applicabili a rischi per la sicurezza specifici, in linea con i piani di adozione del cloud.

Per iniziare a sviluppare definizioni dei criteri personalizzate correlate alla baseline di sicurezza, scaricare il [modello di baseline di sicurezza](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri della Baseline di sicurezza.

> [!div class="nextstepaction"]
> [Stabilire i processi di conformità ai criteri](./compliance-processes.md)
