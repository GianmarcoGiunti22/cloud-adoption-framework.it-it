---
title: 'Data Center virtuali: una prospettiva di rete'
description: Informazioni su come creare un data center virtuale in Azure.
author: tracsman
ms.author: jonor
ms.date: 06/12/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 718c93b560b38eaae6556e549a0c6f6bb97b807b
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048254"
---
# <a name="virtual-datacenters-a-network-perspective"></a>Data Center virtuali: una prospettiva di rete

## <a name="overview"></a>Panoramica

La migrazione delle applicazioni locali ad Azure offre alle organizzazioni il vantaggio di un'infrastruttura protetta e conveniente, anche se la migrazione avviene con modifiche minime. Per trarre il meglio dall'agilità del cloud computing, le aziende devono tuttavia sviluppare la propria architettura per poter sfruttare le funzionalità di Azure.

Microsoft Azure offre servizi e infrastruttura a scalabilità elevata con funzionalità e affidabilità di livello aziendale. Questi servizi e infrastruttura offrono molte opzioni di connettività ibrida, in modo che i clienti possano scegliere di accedervi tramite la rete Internet pubblica o tramite una connessione Azure ExpressRoute privata. I partner Microsoft mettono inoltre a disposizione funzionalità avanzate offrendo servizi di sicurezza e appliance virtuali ottimizzati per Azure.

I clienti possono scegliere di accedere a questi servizi cloud tramite Internet o con Azure ExpressRoute, che offre connettività di rete privata. Grazie alla piattaforma Microsoft Azure, i clienti possono estendere facilmente la propria infrastruttura nel cloud e creare architetture a più livelli. I partner Microsoft mettono inoltre a disposizione funzionalità avanzate offrendo servizi di sicurezza e appliance virtuali ottimizzati per Azure.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-the-virtual-datacenter"></a>Che cos'è il data center virtuale?

Agli inizi, il cloud era essenzialmente una piattaforma di hosting per applicazioni rivolte al pubblico. Le aziende hanno iniziato a comprendere il valore del cloud e a spostare le applicazioni line-of-business interne nel cloud. Questi tipi di applicazioni hanno introdotto considerazioni aggiuntive in riferimento a sicurezza, affidabilità, prestazioni e costi, che hanno reso necessaria una maggiore flessibilità nella modalità di erogazione dei servizi cloud. Sono state così poste le basi per i nuovi servizi di infrastruttura e di rete progettati per offrire questa flessibilità, ma anche per nuove funzionalità per la scalabilità, il ripristino di emergenza e altre esigenze.

Le prime soluzioni cloud erano progettate per ospitare singole applicazioni relativamente isolate in ambito pubblico. Questo approccio è andato bene per alcuni anni, ma, man mano che i vantaggi delle soluzioni cloud si facevano evidenti e sempre più carichi di lavoro su vasta scala venivano ospitati nel cloud, Affrontare i problemi di sicurezza, affidabilità, prestazioni e costi delle distribuzioni in una o più aree è diventato fondamentale durante tutto il ciclo di vita del servizio cloud.

Il diagramma distribuzione cloud seguente illustra un esempio di lacune nella sicurezza nella **casella rossa** La **casella gialla** Mostra lo spazio per l'ottimizzazione delle appliance virtuali di rete tra i carichi di lavoro.

![0][0]

Un data center virtuale è un concetto Nato dalla necessità di ridimensionarsi per supportare i carichi di lavoro aziendali, bilanciando la necessità di gestire i problemi introdotti durante il supporto di applicazioni su larga scala nel cloud pubblico.

Un'implementazione di data center virtuale non rappresenta solo i carichi di lavoro dell'applicazione nel cloud, ma anche la rete, la sicurezza, la gestione e l'infrastruttura (ad esempio, DNS e servizi directory). Poiché sempre più carichi di lavoro di un'azienda si spostano in Azure, è importante considerare l'infrastruttura di supporto e gli oggetti in cui vengono inseriti questi carichi di lavoro. Un'attenta valutazione di come le risorse sono strutturate può evitare il proliferare di centinaia di "isole di carichi di lavoro" che devono essere gestite separatamente, ognuna con i propri flussi di dati, modelli di sicurezza e problematiche di conformità.

Il concetto di data center virtuale è un set di consigli e procedure consigliate per l'implementazione di una raccolta di entità separate ma correlate con funzioni, funzionalità e infrastruttura di supporto comuni. Visualizzando i carichi di lavoro tramite l'obiettivo di un data center virtuale, è possibile realizzare costi ridotti a causa di economie di scalabilità, sicurezza ottimizzata tramite componenti e centralizzazione del flusso di dati, oltre a operazioni più semplici, gestione e controlli di conformità.

> [!NOTE]
> È importante comprendere che un data center virtuale **non** è un prodotto Azure discreto, ma la combinazione di varie funzionalità e funzionalità per soddisfare i requisiti esatti. Un data center virtuale è un modo per considerare i carichi di lavoro e l'utilizzo di Azure per ottimizzare le risorse e le capacità nel cloud. Si tratta di un approccio modulare alla creazione di servizi IT in Azure, rispettando allo stesso tempo i ruoli e le responsabilità dell'organizzazione.

Un'implementazione di data center virtuale può aiutare le aziende a ottenere carichi di lavoro e applicazioni in Azure per gli scenari seguenti:

- Hosting di più carichi di lavoro correlati
- Migrazione dei carichi di lavoro da un ambiente locale ad Azure
- Implementazione di requisiti di sicurezza e accesso condivisi o centralizzati nei carichi di lavoro
- Combinazione di Azure DevOps e IT centralizzato in modo appropriato per un'organizzazione di grandi dimensioni

La chiave per sbloccare i vantaggi di un data center virtuale è un hub centralizzato e una topologia di rete spoke con una combinazione di servizi e funzionalità di Azure:

- [Rete virtuale di Azure][VNet],
- [Gruppi di sicurezza di rete][network-security-groups],
- [Peering di rete virtuale][VNetPeering],
- [Route definite dall'utente][user-defined-routes]e
- Identità di Azure con il [controllo degli accessi in base al ruolo (RBAC)][RBAC] e, facoltativamente, il [Firewall][AzFW]di Azure, il [DNS][DNS]di Azure, la [porta anteriore di Azure][AFD]e la [rete WAN virtuale][vWAN]

## <a name="who-should-implement-a-virtual-datacenter"></a>Chi deve implementare un data center virtuale?

Qualsiasi cliente di Azure che ha deciso di adottare il cloud può trarre vantaggio dall'efficienza della configurazione di un set di risorse per l'uso comune per tutte le applicazioni. A seconda della grandezza, anche le singole applicazioni possono trarre vantaggio dall'utilizzo di modelli e componenti utilizzati per creare un'implementazione virtuale del Data Center.

Se l'organizzazione dispone di team o reparti centralizzati per IT, rete, sicurezza o conformità, l'implementazione di un data center virtuale può contribuire a applicare punti di criteri, separazione dei compiti e garantire l'uniformità dei componenti comuni sottostanti fornendo i team di applicazioni hanno la libertà e il controllo più appropriati per le proprie esigenze.

Le organizzazioni che cercano DevOps possono anche usare i concetti relativi ai data center virtuali per fornire sacche di risorse di Azure autorizzate e garantire il controllo totale all'interno del gruppo (sottoscrizione o gruppo di risorse in una sottoscrizione comune), ma il i limiti di rete e di sicurezza sono conformi in base a quanto definito da un criterio centralizzato in un VNet Hub e in un gruppo di risorse.

<!-- markdownlint-enable MD026 -->

## <a name="considerations-for-implementing-a-virtual-datacenter"></a>Considerazioni per l'implementazione di un data center virtuale

Quando si progetta un'implementazione di data center virtuale, è necessario prendere in considerazione diversi aspetti fondamentali:

### <a name="identity-and-directory-service"></a>Identità e servizio directory

L'identità e i servizi directory sono aspetti chiave di tutti i data center, sia locali che nel cloud. L'identità è correlata a tutti gli aspetti di accesso e autorizzazione ai servizi all'interno di un'implementazione del data center virtuale. Per fare in modo che solo utenti e processi autorizzati accedano all'account e alle risorse di Azure, Azure usa diversi tipi di credenziali per l'autenticazione, tra cui password (per accedere all'account Azure), chiavi crittografiche, firme digitali e certificati. [Azure multi-factor authentication][multi-factor-authentication] è un ulteriore livello di sicurezza per l'accesso ai servizi di Azure. Multi-Factor Authentication offre un'autenticazione avanzata con una gamma di semplici opzioni di verifica (telefonata, SMS o notifica tramite app per dispositivi mobili) e consente ai clienti di scegliere il metodo che preferiscono.

Qualsiasi azienda di grandi dimensioni deve definire un processo di gestione delle identità che descriva la gestione delle singole identità, l'autenticazione, l'autorizzazione, i ruoli e i privilegi all'interno o nell'implementazione del data center virtuale. Gli obiettivi di questo processo saranno da un lato l'aumento della sicurezza e della produttività e dall'altro la riduzione dei costi, dei tempi di inattività e delle attività manuali ripetitive.

Le organizzazioni aziendali possono richiedere una combinazione complessa di servizi per diverse linee di business e i dipendenti hanno spesso ruoli diversi quando sono soggetti a progetti diversi. Un data center virtuale richiede una collaborazione efficace tra diversi team, ognuno con definizioni di ruolo specifiche, per ottenere i sistemi in esecuzione con una gestione efficace. L'insieme di responsabilità, accesso e diritti può essere complesso. La gestione delle identità in un data center virtuale viene implementata tramite [Azure Active Directory (Azure ad)][azure-ad] e il controllo degli accessi in base al ruolo (RBAC).

Un servizio directory è un'infrastruttura di informazioni condivisa per individuare, gestire, amministrare e organizzare quotidianamente elementi e risorse di rete. Queste risorse possono includere volumi, cartelle, file, stampanti, utenti, gruppi, dispositivi e altri oggetti. Ogni risorsa presente nella rete è considerata un oggetto dal server di directory. Le informazioni su una risorsa vengono archiviate come raccolta di attributi associati a tale risorsa o oggetto.

Tutti i servizi aziendali online di Microsoft si basano su Azure Active Directory (Azure AD) per le esigenze di gestione delle identità e degli accessi. Azure Active Directory è una soluzione cloud completa di gestione di identità e accessi ad alta disponibilità che riunisce servizi di directory di base, governance delle identità avanzata e gestione dell'accesso alle applicazioni. Azure AD può essere integrato con Active Directory locale per abilitare Single Sign-On per tutte le applicazioni basate sul cloud e ospitate in locale. Gli attributi utente di Active Directory locale possono essere automaticamente sincronizzati con Azure AD.

Non è necessario un singolo amministratore globale per assegnare tutte le autorizzazioni in un'implementazione virtuale del Data Center. Al contrario, ogni reparto specifico, gruppo di utenti o servizi nel servizio directory può disporre delle autorizzazioni necessarie per gestire le proprie risorse all'interno di un'implementazione virtuale del Data Center. La struttura delle autorizzazioni deve essere ben bilanciata. Troppe autorizzazioni possono ostacolare le prestazioni, mentre autorizzazioni non sufficienti o approssimative possono aumentare i rischi per la sicurezza. Il controllo degli accessi in base al ruolo (RBAC) di Azure consente di risolvere questo problema, offrendo una gestione degli accessi con granularità fine per le risorse in un'implementazione di data center virtuale.

#### <a name="security-infrastructure"></a>Infrastruttura di sicurezza

L'infrastruttura di sicurezza si riferisce alla separazione del traffico in un segmento di rete virtuale specifico dell'implementazione di un data center virtuale. Questa infrastruttura specifica il modo in cui il traffico in ingresso e in uscita viene controllato in un'implementazione virtuale del Data Center. Azure si basa su un'architettura multi-tenant che impedisce il traffico non autorizzato e non intenzionale tra le distribuzioni usando l'isolamento VNet, gli elenchi di controllo di accesso (ACL), i bilanciamenti del carico, i filtri IP e i criteri di flusso del traffico. Network Address Translation (NAT) separa il traffico di rete interno da quello esterno.

L'infrastruttura di Azure alloca le risorse di infrastruttura ai carichi di lavoro dei tenant e gestisce le comunicazioni verso e dalle macchine virtuali (VM). L'hypervisor di Azure impone la separazione di memoria e processi tra le VM e instrada in modo sicuro il traffico di rete ai tenant del sistema operativo guest.

#### <a name="connectivity-to-the-cloud"></a>Connettività al cloud

Un'implementazione del data center virtuale richiede la connettività a reti esterne per offrire servizi a clienti, partner e utenti interni. quindi è in genere necessaria la connettività non solo a Internet, ma anche alle reti e ai data center locali.

I clienti controllano i servizi che hanno accesso a e sono accessibili dalla rete Internet pubblica usando il [firewall di Azure][AzFW] o altri tipi di appliance di rete virtuale (appliance virtuali), criteri di routing personalizzati usando [route definite dall'utente][user-defined-routes]e rete filtraggio usando [gruppi di sicurezza di rete][network-security-groups]. È consigliabile che tutte le risorse con connessione Internet siano protette anche dallo [standard di protezione DDoS di Azure][DDoS].

È possibile che le aziende debbano connettere l'implementazione del data center virtuale ai data center locali o ad altre risorse. La connettività tra Azure e le reti locali è quindi un aspetto fondamentale della progettazione di un'architettura efficace. Le aziende hanno due modi diversi per creare questa interconnessione: transito su Internet o tramite connessioni private dirette.

Una [**VPN da sito a sito di Azure**][VPN] è un servizio di interconnessione su Internet tra le reti locali e un'implementazione di data center virtuale, stabilita tramite connessioni crittografate sicure (tunnel IPSec/IKE). La connessione da sito a sito di Azure è flessibile, veloce da creare e non richiede ulteriore approvvigionamento, perché tutte le connessioni vengono stabilite tramite Internet.

Per un numero elevato di connessioni VPN, la rete [**WAN virtuale di Azure**][vWAN] è un servizio di rete che fornisce connettività da ramo a ramo ottimizzata e automatizzata tramite Azure. La rete WAN virtuale consente di connettersi per configurare i dispositivi Branch per la comunicazione con Azure. La connessione e la configurazione possono essere eseguite manualmente oppure usando i dispositivi di provider preferiti tramite un partner di rete WAN virtuale. L'uso di dispositivi di provider preferiti consente la facilità d'uso, semplifica le operazioni di connettività e agevola la gestione della configurazione. Il dashboard predefinito della rete WAN di Azure offre informazioni dettagliate immediate per la risoluzione dei problemi, che consentono di risparmiare tempo e permette di visualizzare con facilità la connettività da sito a sito su larga scala.

[**ExpressRoute**][ExR] è un servizio di connettività di Azure che consente connessioni private tra un'implementazione virtuale del Data Center e qualsiasi rete locale. Le connessioni ExpressRoute non sfruttano la rete Internet pubblica e offrono un livello di sicurezza superiore, maggiore affidabilità e velocità più elevate (fino a 10 Gbps), oltre a una latenza coerente. ExpressRoute è utile per le implementazioni di data center virtuali, in quanto i clienti di ExpressRoute possono ottenere i vantaggi delle regole di conformità associate alle connessioni private. Con [ExpressRoute Direct][ExRD]è possibile connettersi direttamente ai router Microsoft a 100 Gbps per i clienti con esigenze di larghezza di banda più elevate.

Per distribuire le connessioni ExpressRoute, in genere è necessario un provider di servizi ExpressRoute. Per i clienti che devono iniziare rapidamente, è normale usare inizialmente la VPN da sito a sito per stabilire la connettività tra un'implementazione del data center virtuale e le risorse locali e quindi eseguire la migrazione alla connessione ExpressRoute quando il fisico l'interconnessione con il provider di servizi è stata completata.

#### <a name="connectivity-within-the-cloud"></a>*Connettività all'interno del cloud*

Il [peering][VNetPeering] di [reti virtuali][VNet] e VNet sono i servizi di connettività di rete di base all'interno di un'implementazione virtuale di Data Center. Un VNet garantisce un limite naturale di isolamento per le risorse del data center virtuale e il peering VNet consente l'intercomunicazione tra diversi reti virtuali all'interno della stessa area di Azure o anche tra aree. Il controllo del traffico all'interno di una VNet e tra reti virtuali deve corrispondere a un set di regole di sicurezza specificato tramite gli elenchi di controllo di accesso ([gruppi di sicurezza di rete][network-security-groups]), le [appliance virtuali di rete][NVA]e le tabelle di routing personalizzate ([route definite dall'utente][user-defined-routes]).

## <a name="virtual-datacenter-overview"></a>Panoramica del data center virtuale

### <a name="topology"></a>Topologia

*Hub e spoke* è un modello per la progettazione della topologia di rete per l'implementazione di un data center virtuale.

![1][1]

Come illustrato, è possibile usare due tipi di progettazione hub e spoke in Azure. Per la comunicazione, le risorse condivise e i criteri di sicurezza centralizzati (hub VNet nel diagramma) o un tipo di WAN virtuale (WAN virtuale nel diagramma) per le comunicazioni da ramo a ramo su larga scala e da ramo a Azure.

L'hub è la zona della rete centrale che controlla e ispeziona il traffico in ingresso o in uscita tra zone diverse: Internet, locale e gli spoke. La topologia hub-spoke consente al reparto IT di applicare in modo efficace i criteri di sicurezza in una posizione centrale, riducendo al contempo il rischio di configurazione non corretta ed esposizione.

L'hub spesso contiene i componenti del servizio comuni utilizzati dai spoke. Di seguito sono riportati alcuni esempi di servizi centrali comuni:

- Infrastruttura di Windows Active Directory necessaria per l'autenticazione utente delle terze parti che accedono da reti non attendibili prima di ottenere l'accesso ai carichi di lavoro nello spoke. Include il componente correlato Active Directory Federation Services (AD FS).
- Servizio DNS per risolvere la denominazione per il carico di lavoro negli spoke, per accedere alle risorse in locale e in Internet se non viene usato [DNS di Azure][DNS].
- Infrastruttura a chiave pubblica (PKI) per implementare Single Sign-On nei carichi di lavoro.
- Controllo di flusso del traffico TCP e UDP tra le zone della rete degli spoke e Internet.
- Controllo di flusso tra gli spoke e le zone locali.
- Se necessario, controllo di flusso tra uno spoke e un altro.

Il data center virtuale riduce il costo complessivo usando l'infrastruttura dell'hub condiviso tra più spoke.

Il ruolo di ogni spoke può essere quello di ospitare tipi diversi di carichi di lavoro. Gli spoke consentono anche un approccio modulare per le distribuzioni ripetibili degli stessi carichi di lavoro. Ad esempio, sviluppo e test, test di accettazione utente, pre-produzione e produzione. Gli spoke possono anche essere usati per isolare e consentire gruppi diversi all'interno dell'organizzazione, ad esempio gruppi Azure DevOps. In uno spoke è possibile distribuire un carico di lavoro di base o carichi di lavoro complessi multilivello con il controllo del traffico tra i livelli.

#### <a name="subscription-limits-and-multiple-hubs"></a>Limiti della sottoscrizione e hub multipli

In Azure ogni componente, indipendentemente dal tipo, viene distribuito in una sottoscrizione di Azure. L'isolamento dei componenti di Azure in diverse sottoscrizioni di Azure può soddisfare i requisiti di diverse line-of-business, come la configurazione di livelli differenziati di accesso e autorizzazione.

Una singola implementazione virtuale di data center può essere scalata fino a un numero elevato di spoke, sebbene, come per ogni sistema IT, esistano limiti di piattaforma. La distribuzione dell'hub è associata a una sottoscrizione di Azure specifica, che presenta restrizioni e limiti, ad esempio un numero massimo di peering di VNet. per informazioni dettagliate, vedere [sottoscrizione di Azure e limiti, quote e vincoli dei servizi][limits] . Nei casi in cui i limiti possono costituire un problema, è possibile aumentare ulteriormente le prestazioni per l'architettura estendendo il modello da un singolo hub-spoke a un cluster di hub e spoke. Più hub in una o più aree di Azure possono essere interconnessi usando Peering reti virtuali, ExpressRoute, la rete WAN virtuale o una VPN da sito a sito.

![2][2]

L'introduzione di più hub aumenta il costo e l'impegno di gestione del sistema È giustificato solo dalla scalabilità, dai limiti di sistema o dalla ridondanza e dalla replica a livello di area per le prestazioni dell'utente finale o il ripristino di emergenza. Negli scenari in cui sono necessari più hub, tutti gli hub devono cercare di offrire lo stesso set di servizi per facilitare le operazioni.

#### <a name="interconnection-between-spokes"></a>Interconnessione tra spoke

All'interno di un singolo spoke, è possibile implementare carichi di lavoro multilivello complessi. Le configurazioni a più livelli possono essere implementate usando subnet (una per ogni livello) nella stessa VNet e filtrando i flussi usando i gruppi di sicurezza di rete.

Un architetto potrebbe voler distribuire un carico di lavoro multilivello in più reti virtuali. Usando il peering di rete virtuale, gli spoke possono connettersi ad altri spoke nello stesso hub o in hub diversi. Un esempio tipico di questo scenario è quello in cui i server di elaborazione delle applicazioni sono in uno spoke o rete virtuale, mentre il database viene distribuito in un altro spoke o rete virtuale. In questo caso, è facile interconnettere gli spoke con il peering di rete virtuale ed evitare in tal modo il transito dall'hub. Per assicurarsi che il bypass dell'hub non ignori importanti punti di sicurezza o di controllo che potrebbero esistere solo nell'hub, è necessario eseguire un'attenta analisi della sicurezza e dell'architettura.

![3][3]

Gli spoke possono anche essere interconnessi a uno spoke che funge da hub. Questo approccio crea una gerarchia a due livelli: lo spoke nel livello superiore (livello 0) diventa l'hub degli spoke inferiori (livello 1) nella gerarchia. I spoke di un'implementazione virtuale del Data Center sono necessari per l'invio del traffico all'hub centrale, in modo che il traffico possa transitare alla propria destinazione nella rete locale o nella rete Internet pubblica. Un'architettura con due livelli di hub introduce un routing complesso che rimuove i vantaggi di una semplice relazione hub-spoke.

Sebbene in Azure siano consentite topologie complesse, uno dei principi fondamentali del concetto di data center virtuale è la ripetibilità e la semplicità. Per ridurre al minimo il lavoro di gestione, la semplice progettazione hub-spoke è l'architettura di riferimento del data center virtuale consigliata.

### <a name="components"></a>Componenti

Un data center virtuale è costituito da quattro tipi di componenti di base: **infrastruttura**, **reti perimetrali**, **carichi di lavoro**e **monitoraggio**.

Ogni tipo di componente è costituito da diverse funzionalità e risorse di Azure. L'implementazione del data center virtuale è costituita da istanze di più tipi di componenti e da più varianti dello stesso tipo di componente. È possibile, ad esempio, avere più istanze di carico di lavoro diverse separate in modo logico che rappresentano applicazioni diverse. Questi diversi tipi di componenti e istanze vengono usati per creare in definitiva un data center virtuale.

![4][4]

L'architettura concettuale di alto livello precedente di un data center virtuale Mostra tipi di componenti diversi usati in zone diverse della topologia hub-spoke. Il diagramma illustra i componenti dell'infrastruttura in svariate parti dell'architettura.

È consigliabile in generale che i diritti e i privilegi di accesso siano basati sui gruppi. Gestire i gruppi piuttosto che singoli utenti semplifica la manutenzione dei criteri di accesso, offrendo un modo coerente per gestirli tra i team e aiuta a ridurre al minimo gli errori di configurazione. L'assegnazione e la rimozione di utenti nei gruppi appropriati consente di mantenere aggiornati i privilegi di un utente specifico.

Ogni gruppo di ruoli deve avere un prefisso univoco nel nome per identificare più facilmente il gruppo associato a un determinato carico di lavoro. Un carico di lavoro che ospita un servizio di autenticazione, ad esempio, potrebbe avere gruppi denominati **AuthServiceNetOps**, **AuthServiceSecOps**, **AuthServiceDevOps** e **AuthServiceInfraOps**. I ruoli centralizzati o i ruoli non correlati a un servizio specifico possono essere preceduti da **Corp**. Un esempio è **CorpNetOps**.

Molte organizzazioni usano una variante dei gruppi seguenti per una suddivisione primaria dei ruoli:

- Il gruppo IT centrale **Corp** ha i diritti di proprietà per controllare i componenti dell'infrastruttura (ad esempio, rete e sicurezza) e quindi deve avere il ruolo Collaboratore nella sottoscrizione (e avere il controllo dell'hub) e i diritti di Collaboratore Rete negli spoke. Le grandi organizzazioni spesso suddividono queste responsabilità di gestione tra più team, ad esempio un gruppo per le operazioni di rete **CorpNetOps**, dedicato esclusivamente alle rete, e un gruppo per le operazioni di sicurezza **CorpSecOps**, responsabile del firewall e dei criteri di sicurezza. In questo caso specifico è necessario creare due gruppi diversi per l'assegnazione di questi ruoli personalizzati.
- Il gruppo dedicato a sviluppo e test **AppDevOps** ha la responsabilità di distribuire i carichi di lavoro di app o servizi. Questo gruppo prende il ruolo di collaboratore macchina virtuale per le distribuzioni IaaS o uno o più ruoli del collaboratore PaaS. Vedere [ruoli predefiniti per le risorse di Azure][Roles]. Facoltativamente, il team di sviluppo/test potrebbe avere la necessità di visibilità sui criteri di sicurezza (gruppi di sicurezza di rete) e sui criteri di routing (route definite dall'utente) all'interno dell'hub o di un spoke specifico. Oltre ai ruoli di collaboratore per i carichi di lavoro, questo gruppo avrà anche bisogno del ruolo di lettore di rete.
- Il gruppo dedicato a operazioni e manutenzione **CorpInfraOps** o **AppInfraOps** ha la responsabilità di gestire i carichi di lavoro in produzione. Questo gruppo deve essere un collaboratore della sottoscrizione per i carichi di lavoro in qualsiasi sottoscrizione di produzione. Alcune organizzazioni potrebbero anche valutare la necessità di un gruppo aggiuntivo come team di supporto per l'escalation con il ruolo di collaboratore della sottoscrizione nella produzione e nella sottoscrizione dell'hub centrale, per risolvere potenziali problemi di configurazione nell'ambiente di produzione.

Un data center virtuale è progettato in modo che i gruppi creati per il gruppo IT centrale, che gestiscono l'hub, dispongano di gruppi corrispondenti a livello di carico di lavoro. Oltre a gestire solo le risorse dell'hub, i gruppi IT centrali possono controllare l'accesso esterno e le autorizzazioni di primo livello per la sottoscrizione. I gruppi del carico di lavoro sono inoltre in grado di controllare le risorse e le autorizzazioni dei rispettivi VNet indipendentemente dalla Central IT.

Un data center virtuale viene partizionato per ospitare in modo sicuro più progetti in diverse linee di business. Tutti i progetti richiedono ambienti isolati diversi (sviluppo, test di accettazione utente, produzione). Sottoscrizioni di Azure separate per ognuno di questi ambienti offrono un naturale isolamento.

![5][5]

Il diagramma precedente illustra la relazione tra i progetti, gli utenti, i gruppi di un'organizzazione e gli ambienti in cui vengono distribuiti i componenti di Azure.

Nell'ambito IT un ambiente (o livello) è in genere un sistema in cui vengono distribuite ed eseguite più applicazioni. Le aziende di grandi dimensioni usano un ambiente di sviluppo (in cui le modifiche vengono apportate e testate) e un ambiente di produzione (cosa usano gli utenti finali). Tali ambienti sono separati, spesso con diversi ambienti di staging, per consentire la distribuzione a fasi (rollout), il test e il ripristino dello stato precedente in caso di problemi. Le architetture di distribuzione variano in modo significativo, ma in genere il processo di base, che prevede l'avvio con lo sviluppo (DEV) e la fine con la produzione (PROD), è ancora seguito.

Un'architettura comune per questi tipi di ambienti multilivello è costituita da Azure DevOps per lo sviluppo e il test, UAT per gli ambienti di gestione temporanea e di produzione. Le organizzazioni possono sfruttare uno o più tenant di Azure AD per definire l'accesso e i diritti per questi ambienti. Il diagramma precedente illustra un caso in cui vengono usati due diversi tenant di Azure AD: uno per Azure DevOps e il test di accettazione utente e l'altro esclusivamente per la produzione.

La presenza di tenant di Azure AD diversi impone la separazione tra gli ambienti. Lo stesso gruppo di utenti (ad esempio, l'IT centrale) deve eseguire l'autenticazione con un URI diverso per accedere a un tenant di Azure AD diverso e modificare i ruoli o le autorizzazioni degli ambienti Azure DevOps o di produzione di un progetto. La presenza di autenticazioni utente diverse per accedere ad ambienti diversi riduce le possibili interruzioni e gli altri problemi causati dagli errori umani.

#### <a name="component-type-infrastructure"></a>Tipo di componente: infrastruttura

Questo tipo di componente è quello in cui si trova la maggior parte dell'infrastruttura di supporto e a cui i team di IT centralizzato, sicurezza e conformità dedicano la maggior parte del tempo.

![6][6]

I componenti dell'infrastruttura forniscono un'interconnessione per i diversi componenti di un'implementazione di data center virtuale e sono presenti sia nell'hub che negli spoke. La responsabilità della gestione e della manutenzione dei componenti dell'infrastruttura è in genere affidata al team dell'IT centrale o della sicurezza.

Una delle attività principali del team dell'infrastruttura IT è di garantire la coerenza degli schemi degli indirizzi IP in tutta l'organizzazione. Lo spazio di indirizzi IP privato assegnato a un'implementazione del data center virtuale deve essere coerente e non sovrapposto agli indirizzi IP privati assegnati nelle reti locali.

Anche se NAT nei router perimetrali locali o negli ambienti di Azure può evitare i conflitti di indirizzi IP, crea complicazioni nei componenti dell'infrastruttura. La semplicità di gestione è uno degli obiettivi principali del data center virtuale, pertanto l'uso di NAT per gestire le problematiche IP non è una soluzione consigliata.

I componenti dell'infrastruttura contengono le funzionalità seguenti:

- [**Identità e servizi di directory**][azure-ad]. L'accesso a ogni tipo di risorsa in Azure è controllato da un'identità archiviata in un servizio directory. Il servizio directory archivia non solo l'elenco di utenti, ma anche i diritti di accesso alle risorse in una sottoscrizione di Azure specifica. Questi servizi possono esistere solo nel cloud o essere sincronizzati con l'identità locale archiviata in Active Directory.
- [**Rete virtuale**][VPN]. Le reti virtuali sono uno dei principali componenti del data center virtuale e consentono di creare un limite di isolamento del traffico nella piattaforma Azure. Una rete virtuale è costituita da uno o più segmenti di rete virtuale, ognuno con un prefisso di rete IP specifico (una subnet). La rete virtuale definisce un'area perimetrale interna in cui le macchine virtuali IaaS e i servizi PaaS possono stabilire comunicazioni private. Le VM (e i servizi PaaS) in una rete virtuale non possono comunicare direttamente con le VM (e i servizi PaaS) in una rete virtuale diversa, anche se entrambe le reti virtuali vengono create dallo stesso cliente e nella stessa sottoscrizione. L'isolamento è una proprietà essenziale che assicura che le macchine virtuali e le comunicazioni dei clienti rimangano private entro una rete virtuale.
- [**Route definite dall'utente**][user-defined-routes]. Per impostazione predefinita, il traffico in una rete virtuale viene instradato in base alla tabella di routing di sistema. Una route definita dall'utente è una tabella di routing personalizzata che gli amministratori di rete possono associare a una o più subnet per sovrascrivere il comportamento della tabella di routing di sistema e definire un percorso di comunicazione all'interno di una rete virtuale. La presenza di route definite dall'utente garantisce che il traffico in uscita dal transito spoke attraverso VM personalizzate specifiche o appliance virtuali di rete e i bilanciamenti del carico siano presenti sia nell'hub che negli spoke.
- [**Gruppi di sicurezza di rete**][network-security-groups]. Un gruppo di sicurezza di rete è un elenco di regole di sicurezza che fungono da filtraggio del traffico su origini IP, destinazioni IP, protocolli, porte di origine IP e porte di destinazione IP. Il gruppo di sicurezza di rete può essere applicato a una subnet, a una scheda NIC virtuale associata a una macchina virtuale di Azure o a entrambe. I gruppi di sicurezza di rete sono essenziali per implementare un controllo di flusso corretto nell'hub e negli spoke. Il livello di sicurezza concesso dal gruppo di sicurezza di rete è una funzione di quali porte si aprono e per quale scopo. I clienti devono applicare filtri aggiuntivi per ogni VM con firewall basati su host, ad esempio IPtables o Windows Firewall.
- [**DNS**][DNS]. La risoluzione dei nomi delle risorse nella reti virtuali di un'implementazione di data center virtuale viene fornita tramite DNS. Azure fornisce servizi DNS per la risoluzione dei nomi sia [pubblica][DNS] che [privata][PrivateDNS] . Le zone private consentono la risoluzione dei nomi sia all'interno di una rete virtuale che tra diverse reti virtuali. È possibile avere zone private che si estendono non solo su più reti virtuali nella stessa area, ma anche in diverse aree e sottoscrizioni. Per la risoluzione pubblica, DNS di Azure offre un servizio di hosting per i domini DNS, che fornisce la risoluzione dei nomi usando l'infrastruttura di Microsoft Azure. Ospitando i domini in Azure, è possibile gestire i record DNS usando le stesse credenziali, API, strumenti e fatturazione come per gli altri servizi Azure.
- [**Gestione della**][RGMgmt] [**sottoscrizione**][SubMgmt] e del gruppo di risorse. Una sottoscrizione definisce un limite naturale per creare più gruppi di risorse in Azure. Le risorse in una sottoscrizione vengono assemblate insieme in contenitori logici noti come gruppi di risorse. Il gruppo di risorse rappresenta un gruppo logico per organizzare le risorse di un'implementazione virtuale del Data Center.
- [**RBAC**][RBAC]. Tramite il controllo degli accessi in base al ruolo, è possibile eseguire il mapping dei ruoli aziendali ai diritti di accesso a risorse di Azure specifiche e consentire agli utenti solo un determinato subset di azioni. Con il controllo degli accessi in base al ruolo, è possibile concedere l'accesso assegnando i ruoli appropriati a utenti, gruppi e applicazioni nell'ambito pertinente. L'ambito di un'assegnazione di ruolo può essere una sottoscrizione di Azure, un gruppo di risorse o una singola risorsa. Il controllo degli accessi in base al ruolo consente l'ereditarietà delle autorizzazioni. Un ruolo assegnato a un ambito padre concede anche l'accesso agli elementi figlio contenuti al suo interno. Usando il controllo degli accessi in base al ruolo, è possibile separare i compiti e concedere agli utenti solo la quantità di accesso di cui hanno bisogno per svolgere il proprio lavoro. Ad esempio, usare il controllo degli accessi in base al ruolo per consentire a un dipendente di gestire le macchine virtuali in una sottoscrizione, mentre un altro utente può gestire i database SQL della stessa sottoscrizione.
- [**Peering VNet**][VNetPeering]. La funzionalità fondamentale usata per creare l'infrastruttura di un data center virtuale è il peering VNet, un meccanismo che connette due reti virtuali (reti virtuali) nella stessa area tramite la rete del Data Center di Azure o usando il backbone globale di Azure tra le aree .

#### <a name="component-type-perimeter-networks"></a>Tipo di componente: reti perimetrali

I componenti della [rete perimetrale][DMZ] consentono la connettività di rete tra le reti dei data center locali o fisici, insieme a qualsiasi connettività da e verso Internet. Sono anche i componenti a cui probabilmente i team responsabili della rete e della sicurezza dedicano più tempo.

I pacchetti in ingresso devono attraversare le appliance di sicurezza nell'hub prima di raggiungere i server back-end negli spoke. Esempi sono il firewall, IDS e IPS. Prima di lasciare la rete, anche i pacchetti diretti a Internet dai carichi di lavoro devono attraversare le appliance di sicurezza nella rete perimetrale. Le finalità di questa operazione sono l'applicazione dei criteri, l'ispezione e il controllo.

I componenti di tipo rete perimetrale offrono le funzionalità seguenti:

- [Reti virtuali][VNet], [route definite dall'utente][user-defined-routes] e [gruppi di sicurezza di rete][network-security-groups]
- [Appliance virtuali di rete][NVA]
- [Servizio di bilanciamento del carico di Azure][ALB]
- [Gateway applicazione Azure][AppGW] con [Web Application Firewall (WAF)][AppGWWAF]
- [IP pubblici][PIP]
- [Sportello anteriore di Azure][AFD] con [Web Application Firewall (WAF)][AFDWAF]
- [Firewall di Azure][AzFW]

I team dedicati all'IT centrale e alla sicurezza hanno in genere la responsabilità della definizione dei requisiti e delle operazioni delle reti perimetrali.

![7][7]

Il diagramma precedente illustra l'applicazione di due perimetri con accesso a Internet e una rete locale, entrambi residenti nell'hub DMZ. Nell'hub DMZ la rete perimetrale a Internet può essere ridimensionata per supportare un numero elevato di LOB, usando più farm di Web Application Firewall (WAFs) o firewall di Azure. Nell'hub consente anche la connettività tramite VPN o ExpressRoute in base alle esigenze.

[**Reti virtuali**][VNet]. L'hub si basa in genere su una rete virtuale con più subnet per ospitare i diversi tipi di servizi che filtrano ed esaminano il traffico verso o da Internet tramite appliance virtuali di rete, WAF e istanze del gateway applicazione di Azure.

[**Route definite dall'utente**][user-defined-routes] Con le route definite dall'utente, i clienti possono distribuire firewall, ID/IP e altre appliance virtuali e instradare il traffico di rete attraverso queste appliance di sicurezza per l'applicazione dei criteri di sicurezza, il controllo e l'ispezione. Le route definite dall'utente possono essere create sia nell'hub che negli spoke per garantire che il traffico venga transitato attraverso le VM personalizzate specifiche, le appliance virtuali di rete e i bilanciamenti del carico usati da un'implementazione del data center virtuale. Per garantire che il traffico generato dalle macchine virtuali che risiedono nel raggio di transito ai dispositivi virtuali corretti, è necessario impostare una route definita dall'utente nelle subnet della spoke impostando l'indirizzo IP front-end del servizio di bilanciamento del carico interno come hop successivo. Il servizio di bilanciamento del carico interno distribuisce il traffico interno alle appliance virtuali (pool back-end di bilanciamento del carico).

Il [**firewall di Azure**][AzFW] è un servizio di sicurezza di rete gestito e basato sul cloud che protegge le risorse della rete virtuale di Azure. È un firewall con stato completo distribuito come servizio con disponibilità elevata e scalabilità cloud senza limiti. È possibile creare, applicare e registrare criteri di connettività di applicazione e di rete in modo centralizzato tra le sottoscrizioni e le reti virtuali. Firewall di Azure usa un indirizzo IP pubblico statico per le risorse della rete virtuale consentendo ai firewall esterni di identificare il traffico proveniente dalla rete virtuale. Il servizio è completamente integrato con Monitoraggio di Azure per la registrazione e l'analisi.

[**Appliance virtuali di rete**][NVA]. Nell'hub la rete perimetrale con accesso a Internet in genere viene gestita tramite un'istanza di Firewall di Azure oppure una farm di firewall o web application firewall (WAF).

Line-of-business diverse usano in genere numerose applicazioni Web che tendono a essere soggette a svariate vulnerabilità e potenziali exploit. I web application firewall sono uno speciale tipo di prodotto usato per rilevare gli attacchi contro le applicazioni Web (HTTP/HTTPS) in modo più approfondito di quanto farebbe un firewall generico. Rispetto alla tradizionale tecnologia firewall, i Web application firewall hanno un set di funzionalità specifiche per proteggere i server Web interni dalle minacce.

Sia Firewall di Azure che un firewall delle appliance virtuali di rete usano un piano di amministrazione comune, con un set di regole di sicurezza per proteggere i carichi di lavoro ospitati negli spoke e controllare l'accesso alle reti locali. Firewall di Azure ha incorporata la scalabilità, mentre i firewall delle appliance virtuali di rete possono essere ridimensionati manualmente dietro un servizio di bilanciamento del carico. In genere, una farm di firewall ha un software meno specializzato rispetto a un WAF, ma ha un ambito dell'applicazione più ampio per filtrare ed esaminare ogni tipo di traffico in uscita o in ingresso. Se viene usato un approccio basato sulle appliance virtuali di rete, queste ultime sono disponibili e possono essere distribuite da Azure Marketplace.

Usare un set di firewall di Azure (o di appliance virtuali di rete) per il traffico che ha origine in Internet e un altro per il traffico che ha origine in locale. L'uso di un solo set di firewall per entrambi i tipi di traffico è un rischio per la sicurezza, perché non viene creato un perimetro di sicurezza tra i due set di traffico. L'uso di livelli di firewall separati riduce la complessità del controllo delle regole di sicurezza e indica chiaramente la corrispondenza tra le regole e le richieste di rete in ingresso.

È consigliabile usare un set di istanze di Firewall di Azure (o di appliance virtuali di rete) per il traffico che ha origine in Internet e un altro per il traffico che ha origine in locale. L'uso di un solo set di firewall per entrambi i tipi di traffico è un rischio per la sicurezza, perché non viene creato un perimetro di sicurezza tra i due set di traffico. L'uso di livelli di firewall separati riduce la complessità del controllo delle regole di sicurezza e indica chiaramente la corrispondenza tra le regole e le richieste di rete in ingresso.

[**Azure Load Balancer**][ALB] offre un servizio di livello 4 (TCP, UDP) a disponibilità elevata, che consente di distribuire il traffico in ingresso tra le istanze del servizio definite in un set con carico bilanciato. Il traffico inviato al servizio di bilanciamento del carico dagli endpoint front-end (endpoint IP pubblici o endpoint IP privati) può essere ridistribuito con o senza conversione degli indirizzi in un set di pool di indirizzi IP back-end (esempi sono appliance virtuali di rete o macchine virtuali).

Azure Load Balancer possibile verificare anche l'integrità delle varie istanze del server e quando un'istanza non riesce a rispondere a un probe, il servizio di bilanciamento del carico interrompe l'invio del traffico all'istanza non integra. In un data center virtuale viene distribuito un servizio di bilanciamento del carico esterno nell'hub e negli spoke. Nell'hub, il servizio di bilanciamento del carico consente di instradare in modo efficiente il traffico ai servizi negli spoke e negli spoke i servizi di bilanciamento del carico vengono usati per gestire il traffico delle applicazioni.

Il front-end di [**Azure**][AFD] (AFD) è la piattaforma di accelerazione delle applicazioni Web a disponibilità elevata e scalabile di Microsoft, Load Balancer http globale, protezione delle applicazioni e rete per la distribuzione di contenuti. In esecuzione in più di 100 posizioni alla periferia della rete globale di Microsoft, AFD consente di creare, usare e scalare in orizzontale l'applicazione Web dinamica e il contenuto statico. Il servizio Frontdoor di Azure assicura all'applicazione prestazioni per l'utente finale di livello superiore, automazione della manutenzione regionale unificata, automazione della continuità aziendale e ripristino di emergenza, informazioni client/utente unificate, memorizzazione nella cache e informazioni dettagliate sul servizio. La piattaforma garantisce prestazioni, affidabilità e contratti di servizio di supporto tecnico, oltre a certificazioni di conformità e procedure di sicurezza controllabili sviluppate, gestite e supportate in modo nativo da Azure.

[**Gateway applicazione**][AppGW] Microsoft Azure gateway applicazione è un'appliance virtuale dedicata che offre un servizio di controller per la distribuzione di applicazioni (ADC), che offre diverse funzionalità di bilanciamento del carico di livello 7 per l'applicazione. Consente di ottimizzare la produttività delle Web farm eseguendo l'offload al gateway applicazione della terminazione SSL con utilizzo elevato di CPU. Offre anche altre funzionalità di routing di livello 7, tra cui la distribuzione round robin del traffico in ingresso, l'affinità di sessione basata su cookie, il routing basato su percorso URL e la possibilità di ospitare più siti Web dietro un unico gateway applicazione. Nello SKU WAF del gateway applicazione è incluso anche un Web application firewall (WAF). Questo SKU offre alle applicazioni Web la protezione da exploit e vulnerabilità Web comuni. Il gateway applicazione può essere configurato come gateway con connessione Internet, come gateway solo interno o come una combinazione di queste due opzioni.

[**Indirizzi IP pubblici**][PIP]. Alcune funzionalità di Azure consentono di associare gli endpoint di servizio a un indirizzo IP pubblico in modo che la risorsa sia accessibile da Internet. Questo endpoint usa il processo NAT (Network Address Translation) per instradare il traffico fino all'indirizzo e alla porta interni nella rete virtuale di Azure. È questa la modalità primaria che consente al traffico esterno di passare attraverso la rete virtuale. Gli indirizzi IP pubblici possono essere configurati per determinare il traffico autorizzato a passare e come/dove viene convertito nella rete virtuale.

[**Protezione DDoS di Azure standard**][DDoS] offre funzionalità di mitigazione aggiuntive per il livello di [servizio Basic][DDoS] , ottimizzate in modo specifico per le risorse di rete virtuale di Azure. Protezione DDoS Standard è semplice da abilitare e non richiede alcuna modifica alle applicazioni. I criteri di protezione sono ottimizzati tramite il monitoraggio del traffico dedicato e algoritmi di apprendimento automatico. I criteri vengono applicati agli indirizzi IP pubblici associati alle risorse distribuite nelle reti virtuali, ad esempio le istanze di Azure Load Balancer, del gateway applicazione di Azure e di Azure Service Fabric. La telemetria in tempo reale è disponibile tramite le viste di Monitoraggio di Azure durante un attacco e come informazione cronologica. È possibile aggiungere protezione al livello dell'applicazione tramite il web application firewall del gateway applicazione di Azure. La protezione viene fornita per gli indirizzi IP pubblici di Azure IPv4.

#### <a name="component-type-monitoring"></a>Tipo di componente: monitoraggio

I componenti di monitoraggio forniscono visibilità e avvisi da tutti gli altri tipi di componenti. Tutti i team devono avere accesso al monitoraggio per i componenti e i servizi a cui hanno accesso. Se è presente un help desk centralizzato o team operativi, questi dovranno avere accesso integrato ai dati forniti da tali componenti.

Azure offre tipi diversi di servizi di registrazione e monitoraggio per tenere traccia del comportamento delle risorse ospitate di Azure. La governance e il controllo dei carichi di lavoro in Azure si basano non solo sulla raccolta dei dati dei log, ma anche sulla possibilità di attivare azioni in base a specifici eventi segnalati.

[**Monitoraggio di Azure**][Monitor]. Azure include più servizi che singolarmente eseguono un'attività o un ruolo specifico nell'area di monitoraggio. Insieme, questi servizi offrono una soluzione completa per la raccolta, l'analisi e l'utilizzo dei dati di telemetria dall'applicazione e dalle risorse di supporto di Azure sottostanti. Possono anche essere usati per monitorare le risorse locali critiche in modo da fornire un ambiente di monitoraggio ibrido. Conoscere gli strumenti e i dati disponibili è il primo passo per sviluppare una strategia di monitoraggio completa per l'applicazione.

In Azure sono disponibili due tipi principali di lo:

- Il [log attività di Azure][ActLog], denominato in precedenza **log operativi**, fornisce informazioni approfondite sulle operazioni eseguite sulle risorse nella sottoscrizione di Azure. Questi log segnalano gli eventi del piano di controllo per le sottoscrizioni. Ogni risorsa di Azure genera log di controllo.

- I [log di diagnostica di monitoraggio di Azure][DiagLog] sono log generati da una risorsa che fornisce dati avanzati e frequenti sul funzionamento di tale risorsa. Il contenuto di questi log varia in base al tipo di risorsa.

![9][9]

È importante tenere traccia dei log per i gruppi di sicurezza di rete, in particolare queste informazioni:

- I [registri eventi][nsg-log] forniscono informazioni sulle regole del gruppo di sicurezza di rete applicate alle VM e ai ruoli delle istanze in base all'indirizzo Mac.
- I [registri dei contatori][nsg-log] verificano quante volte ogni regola dei gruppi di sicurezza di rete è stata eseguita per negare o consentire il traffico.

Tutti i log possono essere archiviati negli account di archiviazione di Azure a scopo di controllo, analisi statica o backup. Quando i log vengono archiviati in un account di archiviazione di Azure, i clienti possono usare tipi diversi di framework per recuperare, preparare, analizzare e visualizzare questi dati per segnalare lo stato e l'integrità delle risorse cloud.

Le grandi imprese devono avere già acquisito un framework standard per il monitoraggio dei sistemi locali e possono estendere tale framework per integrare i log generati dalle distribuzioni cloud. Con [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-queries) le organizzazioni possono tenere tutte le registrazioni nel cloud. Poiché Log Analytics viene implementato come servizio basato sul cloud, è possibile renderlo operativo rapidamente con un investimento minimo nei servizi di infrastruttura. Log Analytics si integra anche con i componenti di System Center, ad esempio System Center Operations Manager, per estendere gli investimenti per la gestione esistenti nel cloud.

Log Analytics è un servizio di Azure che consente di raccogliere, correlare, cercare e modificare i dati dei log e delle prestazioni generati da sistemi operativi, applicazioni e componenti cloud dell'infrastruttura. Fornisce ai clienti informazioni operative in tempo reale usando la ricerca integrata e i dashboard personalizzati per analizzare tutti i record in tutti i carichi di lavoro nell'implementazione del data center virtuale.

[Azure Network Watcher][NetWatch] offre strumenti per monitorare, diagnosticare e visualizzare le metriche e abilitare o disabilitare i log per le risorse in una rete virtuale di Azure. È un servizio con più sfaccettature che consente le funzionalità seguenti e altro ancora:

- Monitorare la comunicazione tra una macchina virtuale e un endpoint
- Visualizzare le risorse in una rete virtuale e le relative relazioni
- Diagnosticare i problemi di filtro del traffico di rete da o verso una macchina virtuale
- Diagnosticare i problemi di routing di rete da una macchina virtuale
- Diagnosticare i problemi delle connessioni in uscita da una macchina virtuale
- Acquisire i pacchetti da e verso una macchina virtuale
- Diagnosticare i problemi relativi a un gateway di rete virtuale e alle connessioni di Azure
- Determinare le latenze relative tra aree di Azure e provider di servizi Internet
- Visualizzare le regole di sicurezza per un'interfaccia di rete
- Visualizzare le metriche di rete
- Analizzare il traffico da o verso un gruppo di sicurezza di rete
- Visualizzare i log di diagnostica per le risorse di rete

La soluzione [monitoraggio prestazioni rete][NPM] all'interno di Operations Management Suite è in grado di fornire informazioni dettagliate sulla rete end-to-end. tra cui una singola visualizzazione delle reti di Azure e delle reti locali, con monitoraggi specifici per ExpressRoute e servizi pubblici.

#### <a name="component-type-workloads"></a>Tipo di componente: carichi di lavoro

Nei componenti di tipo carico di lavoro si trovano le applicazioni e i servizi effettivi. Sono anche i componenti a cui i team di sviluppo di applicazioni dedicano più tempo.

Le possibilità dei carichi di lavoro sono infinite. I seguenti sono solo alcuni dei possibili tipi di carichi di lavoro:

**Applicazioni line-of-business interne:** Le applicazioni line-of-business sono applicazioni di computer cruciali per le operazioni in corso di un'azienda. Le applicazioni line-of-business presentano alcune caratteristiche comuni:

- **Interattivo per natura:** I dati vengono immessi e vengono restituiti i risultati o i report.
- **Basato sui dati:** Carichi di lavoro con utilizzo intensivo dei dati con accesso frequente a database o ad altre risorse di archiviazione.
- **Integrazione:** Carichi di lavoro che offrono l'integrazione con altri sistemi all'interno o all'esterno dell'organizzazione.

**Siti Web rivolte ai clienti (Internet o con connessione interna)** : la maggior parte delle applicazioni che interagiscono con Internet sono siti Web. Azure offre la possibilità di eseguire un sito Web in una macchina virtuale IaaS o da un sito di [app Web di Azure][WebApps] (PaaS). Le app Web di Azure supportano l'integrazione con le reti virtuali che consentono la distribuzione delle app Web in una zona di rete spoke. I siti Web interni non devono esporre un endpoint Internet pubblico perché le risorse sono accessibili tramite indirizzi privati non instradabili tramite Internet dal VNet privato.

**Big Data e analisi:** Quando i dati devono essere ridimensionati in un volume elevato, i database potrebbero non essere ridimensionati correttamente. La tecnologia Hadoop offre un sistema per eseguire parallelamente le query distribuite in un numero elevato di nodi. I clienti hanno la possibilità di eseguire carichi di lavoro di dati in macchine virtuali IaaS o PaaS ([HDInsight][HDI]). HDInsight supporta la distribuzione in un VNet basato sul percorso, può essere distribuito in un cluster in una spoke di un data center virtuale.

**Eventi e messaggistica:** [Hub eventi di Azure][EventHubs] è un servizio di inserimento di dati di telemetria con iperscalabilità che raccoglie, trasforma e archivia milioni di eventi. In quanto piattaforma di streaming distribuita, offre bassa latenza e tempo di conservazione configurabile, permettendo di inserire quantità molto elevate di dati di telemetria in Azure e leggere tali dati da più applicazioni. Con Hub eventi, un solo flusso può supportare pipeline sia in tempo reale che basate su batch.

È possibile implementare un servizio di messaggistica cloud altamente affidabile tra applicazioni e servizi tramite il [bus di servizio di Azure][ServiceBus]. che offre la messaggistica negoziata asincrona tra il client e il server, insieme a funzionalità di messaggistica e pubblicazione e sottoscrizione FIFO (First-In-First-Out) strutturate.

![10][10]

### <a name="making-a-virtual-datacenter-highly-available-multiple-virtual-datacenters"></a>Creazione di un datacenter virtuale a disponibilità elevata: più data center virtuali

Fino a questo punto, questo articolo è incentrato sulla progettazione di un singolo data center virtuale, che descrive i componenti e l'architettura di base che contribuiscono alla resilienza. Funzionalità di Azure, ad esempio Azure Load Balancer, appliance virtuali, set di disponibilità, set di scalabilità e altri meccanismi contribuiscono a un sistema che consente di creare livelli di SLA solidi nei servizi di produzione.

Tuttavia, poiché un singolo data center virtuale viene in genere implementato all'interno di una singola area, può essere vulnerabile a eventuali interruzioni principali che influiscono sull'intera area. I clienti che richiedono contratti di servizio elevati devono proteggere i servizi tramite distribuzioni dello stesso progetto in due o più implementazioni di data center virtuali dislocate in aree diverse.

Oltre alle problematiche relative ai contratti di contratto, esistono diversi scenari comuni in cui la distribuzione di più implementazioni di data center virtuali ha senso:

- Presenza a livello di area o globale
- Ripristino di emergenza.
- Meccanismo per deviare il traffico tra data center

#### <a name="regionalglobal-presence"></a>Presenza a livello di area/globale

I data center di Azure sono presenti in molte aree in tutto il mondo. Quando selezionano più data center di Azure, i clienti devono considerare due fattori correlati: le distanze geografiche e la latenza. Per offrire la migliore esperienza utente, valutare la distanza geografica tra ogni implementazione del data center virtuale, nonché la distanza tra ogni implementazione virtuale del Data Center e gli utenti finali.

L'area in cui sono ospitate le implementazioni dei data center virtuali deve essere conforme ai requisiti normativi stabiliti da qualsiasi giurisdizione legale in cui opera l'organizzazione.

#### <a name="disaster-recovery"></a>Ripristino di emergenza

La progettazione di un piano di ripristino di emergenza dipende dai tipi di carichi di lavoro e dalla possibilità di sincronizzare lo stato dei carichi di lavoro tra implementazioni di data center virtuali diverse. Idealmente, la maggior parte dei clienti desiderano un meccanismo di failover rapido e questo potrebbe richiedere la sincronizzazione dei dati delle applicazioni tra distribuzioni che eseguono più implementazioni di data center virtuali. Tuttavia, quando si progettano piani di ripristino di emergenza, è importante tenere presente che la maggior parte delle applicazioni è sensibile alla latenza che può essere causata da questa sincronizzazione dei dati.

Il monitoraggio della sincronizzazione e dell'heartbeat delle applicazioni nelle diverse implementazioni di data center virtuali richiede la comunicazione attraverso la rete. Due implementazioni in aree diverse possono essere connesse tramite:

- Peering VNet: il peering VNet può connettere hub tra le aree.
- Peering privato di ExpressRoute quando gli hub in ogni implementazione di data center virtuale sono connessi allo stesso circuito ExpressRoute.
- Più circuiti ExpressRoute connessi tramite il backbone aziendale e più implementazioni di data center virtuali connesse ai circuiti ExpressRoute.
- Connessioni VPN da sito a sito tra la zona Hub delle implementazioni dei data center virtuali in ogni area di Azure.

In genere, le connessioni Peering reti virtuali o ExpressRoute sono il tipo preferito di connettività di rete a causa dei livelli più alti di larghezza di banda e latenza coerente durante il transito attraverso il backbone Microsoft.

È consigliabile che i clienti eseguano test di qualifica della rete per verificare la latenza e la larghezza di banda di queste connessioni e decidano se sia appropriata la replica dei dati sincrona o asincrona in base ai risultati. È anche importante valutare attentamente questi risultati in relazione all'obiettivo del tempo di ripristino (RTO, Recovery Time Objective) ottimale.

#### <a name="disaster-recovery-diverting-traffic-from-one-region-to-another"></a>Ripristino di emergenza: deviare il traffico da un'area a un'altra

[Gestione traffico di Azure][traffic-manager] controlla periodicamente l'integrità dei servizi degli endpoint pubblici nelle diverse implementazioni di data center virtuali e, se tali endpoint hanno esito negativo, viene indirizzato automaticamente al data center virtuale secondario usando il Domain Name System ( DNS).

Poiché usa DNS, Gestione traffico è destinato solo all'uso con gli endpoint pubblici di Azure. Il servizio viene in genere usato per controllare o deviare il traffico verso le macchine virtuali e le app Web di Azure nell'istanza integra di un'implementazione del data center virtuale. Gestione traffico è resiliente anche in caso di errore di un'intera area di Azure e può controllare la distribuzione del traffico utente per gli endpoint di servizio in diversi data center virtuali in base a diversi criteri. Ad esempio, l'errore di un servizio in un'implementazione di data center virtuale specifica o la selezione dell'implementazione del data center virtuale con la latenza di rete più bassa.

### <a name="summary"></a>Summary

Un data center virtuale è un approccio alla migrazione del Data Center per creare un'architettura scalabile in Azure che ottimizza l'uso delle risorse cloud, riduce i costi e semplifica la governance del sistema. Un data center virtuale si basa su una topologia di rete hub-spoke, che fornisce servizi condivisi comuni nell'hub e che consente l'utilizzo di applicazioni e carichi di lavoro specifici negli spoke. Un data center virtuale corrisponde anche alla struttura dei ruoli aziendali, in cui diversi reparti, ad esempio l'IT centrale, DevOps, e le operazioni e la manutenzione interagiscono tra loro durante l'esecuzione dei ruoli specifici. Un data center virtuale soddisfa i requisiti per una migrazione "Lift-and-Shift", ma offre anche molti vantaggi per le distribuzioni cloud native.

## <a name="references"></a>Riferimenti

In questo documento sono state illustrate le funzionalità seguenti. Per altre informazioni, seguire i collegamenti.

<!-- markdownlint-disable MD033 -->

|Funzionalità di rete|Bilanciamento del carico.|Connettività|
|-|-|-|
|[Reti virtuali di Azure][VNet]</br>[Gruppi di sicurezza di rete][network-security-groups]</br>[Log del gruppo di sicurezza di rete][nsg-log]</br>[Route definite dall'utente][user-defined-routes]</br>[Appliance virtuali di rete][NVA]</br>[Indirizzi IP pubblici][PIP]</br>[DDoS di Azure][DDoS]</br>[Firewall di Azure][AzFW]</br>[DNS di Azure][DNS]|[Sportello anteriore di Azure][AFD]</br>[Azure Load Balancer (L3)][ALB]</br>[Gateway applicazione (L7)][AppGW]</br>[Web Application Firewall] WAF</br>[Gestione traffico di Azure][traffic-manager]</br></br></br></br></br> |[Peering reti virtuali][VNetPeering]</br>[Rete privata virtuale][VPN]</br>[Rete WAN virtuale][vWAN]</br>[ExpressRoute][ExR]</br>[ExpressRoute Direct][ExRD]</br></br></br></br></br>

|Identità</br>|Monitorare</br>|Procedure consigliate</br>|
|-|-|-|
|[Azure Active Directory][azure-ad]</br>[Multi-Factor Authentication][multi-factor-authentication]</br>[Controlli di accesso di base del ruolo][RBAC]</br>[Ruoli predefiniti Azure AD][Roles]</br></br></br> |[Network Watcher][NetWatch]</br>[Monitoraggio di Azure][Monitor]</br>[Log attività][ActLog]</br>[Log di diagnostica][DiagLog]</br>[Microsoft Operations Management Suite][OMS]</br>[Monitoraggio delle prestazioni di rete][NPM]|[Procedure consigliate per le reti perimetrali][DMZ]</br>[Gestione delle sottoscrizioni][SubMgmt]</br>[Gestione dei gruppi di risorse][RGMgmt]</br>[Limiti della sottoscrizione di Azure][limits] </br></br></br>|

|Altri servizi di Azure|
|-|
|[App Web di Azure][WebApps]</br>[HDInsight (Hadoop)][HDI]</br>[Hub eventi][EventHubs]</br>[Bus di servizio][ServiceBus]|

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Fasi successive

- Esplora il [peering VNet][VNetPeering], la tecnologia di base per le progettazioni di hub e spoke Virtual Datacenter.
- Implementare [Azure ad][azure-ad] per iniziare a usare l'esplorazione [RBAC][RBAC] .
- Sviluppare un modello di gestione della sottoscrizione e delle risorse per rispettare la struttura, i requisiti e i criteri dell'organizzazione. L'attività più importante è la pianificazione. Per quanto pratica, pianificare riorganizzazioni, fusioni, nuove linee di prodotti e altre considerazioni.

<!-- images -->

[0]: ../_images/vdc/networking-redundant-equipment.png "Esempi di sovrapposizione di componenti"
[1]: ../_images/vdc/networking-vdc-high-level.png "Esempio di alto livello di hub e spoke in un'implementazione di data center virtuale"
[2]: ../_images/vdc/networking-hub-spokes-cluster.png "Cluster di hub e spoke"
[3]: ../_images/vdc/networking-spoke-to-spoke.png "Da spoke a spoke"
[4]: ../_images/vdc/networking-vdc-block-level-diagram.png "Diagramma del livello di blocco di un'implementazione del data center virtuale"
[5]: ../_images/vdc/networking-users-groups-subscriptions.png "Utenti, gruppi, sottoscrizioni e progetti"
[6]: ../_images/vdc/networking-infrastructure-high-level.png "Diagramma dell'infrastruttura generale"
[7]: ../_images/vdc/networking-high-level-perimeter-networks.png "Diagramma dell'infrastruttura generale"
[8]: ../_images/vdc/networking-vnet-peering-perimeter-networks.png "Peering reti virtuali e reti perimetrali"
[9]: ../_images/vdc/networking-high-level-diagram-monitoring.png "Diagramma generale per il monitoraggio"
[10]: ../_images/vdc/networking-high-level-workloads.png "Diagramma generale per il carico di lavoro"

<!-- links -->

[limits]: https://docs.microsoft.com/azure/azure-subscription-service-limits
[Roles]: https://docs.microsoft.com/azure/role-based-access-control/built-in-roles
[VNet]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[network-security-groups]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg
[DNS]: https://docs.microsoft.com/azure/dns/dns-overview
[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[VNetPeering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[multi-factor-authentication]: https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication
[azure-ad]: https://docs.microsoft.com/azure/active-directory/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[vWAN]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview
[DMZ]: https://docs.microsoft.com/azure/best-practices-network-security
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
