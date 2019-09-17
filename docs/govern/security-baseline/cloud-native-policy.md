---
title: Criteri di base della sicurezza nativi del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criteri di Baseline di sicurezza Cloud Native
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: aef22e31d632a585e59dd946c5c0ef71c13d46de
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026575"
---
# <a name="cloud-native-security-baseline-policy"></a>Criteri di base della sicurezza nativi del cloud

La [baseline di sicurezza](./index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina è incentrata sugli argomenti di sicurezza generale, inclusi la protezione di rete, le risorse digitali, i dati e così via. Come descritto nella [Guida alla revisione dei criteri](../policy-compliance/cloud-policy-review.md), il Framework di adozione del cloud include tre livelli di criteri di **esempio**: Principio di progettazione cloud nativo, aziendale e cloud conforme per ciascuna disciplina. Questo articolo illustra i criteri di esempio nativi del cloud per la disciplina della linea di base di sicurezza.

> [!NOTE]
> Microsoft non intende dettare criteri aziendali o IT. Questo articolo è pensato per agevolare la preparazione di una revisione dei criteri aziendali. Si presuppone che questo criterio di esempio venga esteso, convalidato e testato in base ai criteri aziendali prima di provare a usarlo. Si sconsiglia qualsiasi uso di questo criterio di esempio nello stato in cui si trova.

## <a name="policy-alignment"></a>Allineamento dei criteri

Questo criterio di esempio sintetizza uno scenario nativo del cloud, ovvero gli strumenti e le piattaforme fornite da Azure sono sufficienti per gestire i rischi aziendali interessati da una distribuzione. In questo scenario, si presume che una semplice configurazione dei servizi di Azure predefiniti offra una protezione sufficiente delle risorse.

## <a name="cloud-security-and-compliance"></a>Conformità e sicurezza del cloud

Azure integra la sicurezza in ogni suo aspetto, offrendo vantaggi esclusivi che derivano da una intelligence globale per la sicurezza, controlli relativi ai clienti e un'infrastruttura dotata di protezione avanzata. Questa combinazione avanzata contribuisce alla protezione delle applicazioni e dei dati e al supporto del lavoro richiesto per la conformità e offre una sicurezza a costi contenuti per organizzazioni di qualsiasi dimensione. Questo approccio consente di creare una solida posizione di partenza per qualsiasi criterio di sicurezza, ma non nega la necessità di pratiche di sicurezza ugualmente elevate relative ai servizi di protezione in uso.

### <a name="built-in-security-controls"></a>Criteri di sicurezza integrati

È difficile mantenere un'infrastruttura di protezione solida quando i controlli relativi alla sicurezza non sono intuitivi e devono essere configurati separatamente. Azure offre criteri di sicurezza integrati per un'ampia gamma di servizi che consentono di proteggere rapidamente i dati e i carichi di lavoro, oltre a gestire i rischi in ambienti ibridi. Anche le soluzioni partner integrate agevolano la transizione delle protezioni esistenti alla piattaforma cloud.

### <a name="cloud-native-identity-policies"></a>Criteri di identità nativi del cloud

L'identità è percepita come il nuovo livello limite per la sicurezza, sostituendo in questo ruolo la prospettiva tradizionale incentrata sulla rete. I perimetri di rete sono diventati sempre più porosi e la difesa perimetrale non può essere così efficace come prima dell'avvento di BYOD (Bring Your Own Device) e delle applicazioni cloud. La gestione delle identità di Azure e il controllo degli accessi garantiscono un accesso facile e sicuro a tutte le applicazioni.

Un esempio di criteri nativi del cloud per l'identità tra le directory cloud e locali può includere requisiti simili ai seguenti:

- Accesso autorizzato alle risorse con controllo degli accessi in base al ruolo (RBAC), autenticazione a più fattori e Single Sign-On (SSO).
- Attenuazione rapida delle identità utente sospette di compromissione.
- JIT (just-in-Time), sufficiente accesso concesso in base a attività per attività, per limitare l'esposizione delle credenziali di amministratore con privilegi eccessivi.
- Identità utente estesa e accesso ai criteri tra più ambienti tramite Azure Active Directory.

Sebbene sia importante capire le [Baseline sull'identità](../identity-baseline/index.md) nel contesto delle Baseline sulla sicurezza, è bene sottolineare che le [cinque discipline della governance del cloud](../index.md) considerano le [Baseline sull'identità](../identity-baseline/index.md) come una disciplina a sé, che non fa parte della Baseline sulla sicurezza.

### <a name="network-access-policies"></a>Criteri di accesso alla rete

Il controllo della rete comprende la configurazione, la gestione e la protezione degli elementi della rete, come la rete virtuale, il bilanciamento del carico, il DNS e i gateway. Questi controlli sono un mezzo di comunicazione e interoperabilità dei servizi. Azure dispone di una infrastruttura di rete solida e protetta per supportare i requisiti di connettività di applicazioni e servizi. La connettività di rete è possibile tra le risorse residenti in Azure, le risorse locali e quelle ospitate in Azure, nonché da e verso Internet e Azure.

I criteri nativi del cloud per i controlli di rete possono includere requisiti simili ai seguenti:

- Le connessioni ibride alle risorse locali (anche se tecnicamente possibile in Azure) potrebbero non essere consentite in un criterio nativo del cloud. Se dovesse essere necessario usare una connessione ibrida, si consiglia di fare riferimento a un esempio di criteri di protezione aziendale più solido.
- Gli utenti possono stabilire connessioni protette ad Azure e al suo interno tramite reti virtuali e gruppi di sicurezza di rete.
- Firewall nativo di Azure per Windows consente di proteggere gli host dal traffico di rete dannoso, limitando l'accesso alla porta. Un esempio valido di questo criterio è un requisito per bloccare (o non abilitare) il traffico direttamente a una macchina virtuale tramite la porta RDP-TCP/UDP 3389.
- Servizi come le applicazioni applicazione Azure gateway web application firewall (WAF) e protezione DDoS di Azure proteggono le applicazioni e garantiscono la disponibilità per le macchine virtuali in esecuzione in Azure. Queste funzionalità non devono essere disabilitate o usate impropriamente.

### <a name="data-protection"></a>Protezione dati

Uno degli aspetti fondamentali della protezione dei dati nel cloud consiste nel tenere conto dei possibili stati in cui possono trovarsi i dati e dei controlli disponibili per ogni stato. Per quanto concerne le procedure consigliate per la sicurezza dei dati e la crittografia in Azure, le raccomandazioni verteranno sugli stati dei dati seguenti:

- I controlli di crittografia dei dati sono integrati nei servizi dalle macchine virtuali all'archiviazione e nel database SQL.
- Mentre i dati si spostano fra cloud e clienti, è possibile proteggerli tramite protocolli di crittografia standard del settore.
- Azure Key Vault consente agli utenti di proteggere e controllare le chiavi di crittografia e altre chiavi segrete usate da app e servizi cloud.
- Azure Information Protection consente di classificare, etichettare e proteggere i dati sensibili presenti nelle app.

Anche se queste funzionalità sono integrate in Azure, quanto descritto in precedenza richiede una configurazione specifica e potrebbe comportare costi aggiuntivi. L'allineamento di ogni funzionalità nativa del cloud con una [strategia di classificazione dei dati](../policy-compliance/data-classification.md) è molto suggerito.

### <a name="security-monitoring"></a>Monitoraggio della protezione

Il monitoraggio della sicurezza è una strategia attiva per il controllo delle risorse che permette di identificare i sistemi non conformi agli standard o alle procedure consigliate dell'organizzazione. Il Centro sicurezza di Azure offre Baseline di sicurezza e la protezione avanzata dalle minacce per carichi di lavoro cloud ibridi. Grazie al Centro sicurezza di Azure è possibile applicare criteri di sicurezza ai flussi di lavoro, limitare l'esposizione alle minacce, rilevare e rispondere agli attacchi, tra cui:

- Visualizzazione unificata della sicurezza in tutti i carichi di lavoro locali e cloud con il Centro sicurezza di Azure.
- Monitoraggio continuo e valutazioni della sicurezza per garantire la conformità e correggere eventuali vulnerabilità.
- Strumenti interattivi e Intelligence per le minacce contestuali per un'analisi semplificata.
- Registrazione completa e integrazione con le informazioni di sicurezza esistenti.

### <a name="extending-cloud-native-policies"></a>Estensione di criteri nativi del cloud

L'uso del cloud potrebbe ridurre alcuni problemi legati alla protezione. Microsoft garantisce la sicurezza fisica dei data center di Azure e aiuta a proteggere la piattaforma cloud da minacce infrastrutturali, ad esempio un attacco DDoS. Dato che Microsoft dispone di migliaia di specialisti Cybersecurity che lavorano quotidianamente sulla sicurezza, le risorse per rilevare, prevenire o attenuare attacchi cibernetici sono considerevoli. In realtà, mentre le organizzazioni erano preoccupati per la sicurezza del cloud, la maggior parte del tempo è consapevole del fatto che il livello di investimento in persone e infrastrutture specializzate da fornitori come Microsoft rende il cloud più sicuro della maggior parte delle sedi locali Datacenter.

Anche con questo investimento in una linea di base di sicurezza nativa del cloud, è consigliabile che tutti i criteri di base di sicurezza estendano i criteri nativi cloud predefiniti. Di seguito sono riportati alcuni esempi di criteri estesi che devono essere presi in considerazione, anche in un ambiente cloud nativo:

- **Proteggere le macchine virtuali.** La sicurezza deve essere una delle principali priorità di ogni organizzazione e per eseguirla in modo efficace sono necessarie diverse operazioni. Bisogna valutare lo stato della sicurezza, della protezione contro potenziali minacce, oltre a rilevare e rispondere rapidamente alle minacce che si verificano.
- **Proteggere il contenuto della VM.** Configurare backup automatici a intervalli regolari è fondamentale per proteggere le macchine dagli errori dell'utente. Tuttavia questo non basta: è anche necessario assicurarsi che i backup siano protetti dagli attacchi informatici e siano disponibili al momento opportuno.
- **Monitorare le macchine virtuali e le applicazioni.** Questo modello include numerose attività, tra cui ottenere informazioni sull'integrità delle macchine virtuali, comprendere in che modo interagiscono e definire i modi per monitorare le applicazioni in esecuzione su queste macchine virtuali. Tutte queste attività sono fondamentali per mantenere le applicazioni in esecuzione anche di notte.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver esaminato i criteri di base della sicurezza di esempio per le soluzioni native del cloud, tornare alla [Guida alla revisione dei criteri](../policy-compliance/cloud-policy-review.md) per iniziare a compilare questo esempio per creare criteri personalizzati per l'adozione del cloud.

> [!div class="nextstepaction"]
> [Creare criteri personalizzati usando la guida alla revisione dei criteri](../policy-compliance/cloud-policy-review.md)
