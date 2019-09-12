---
title: 'Guida aziendale standard: Miglioramento del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida aziendale standard: Miglioramento del cloud'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d1953e190e2581d96db443be00aad74a6b94d5f9
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908774"
---
# <a name="small-to-medium-enterprise-guide-multicloud-improvement"></a>Guida per le aziende di piccole e medie dimensioni: Miglioramento del cloud

In questo articolo viene avanzata la descrizione tramite l'aggiunta di controlli per l'adozione di più cloud.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

Microsoft è consapevole che i clienti stanno adottando più cloud per scopi specifici. Il cliente fittizio in questa guida non è un'eccezione. Parallelamente al percorso di adozione di Azure, il successo aziendale ha portato all'acquisizione di un'altra azienda, di piccole dimensioni ma complementare. La nuova azienda gestisce tutte le operazioni IT con un provider di servizi cloud diverso.

Questo articolo descrive i cambiamenti introdotti dall'integrazione della nuova organizzazione. Ai fini della descrizione, si presuppone che questa società abbia completato ogni iterazione di governance descritta in questa guida alla governance.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Nella fase precedente di questo scenario, la società aveva iniziato a eseguire attivamente il push di applicazioni di produzione nel cloud tramite le pipeline CI/CD.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- Il controllo delle identità avviene tramite un'istanza locale di Active Directory. La gestione delle identità ibride è facilitata tramite la replica in Azure Active Directory.
- Le operazioni IT o le operazioni nel cloud sono in gran parte gestite da Monitoraggio di Azure e automazioni correlate.
- Il ripristino di emergenza e la continuità aziendale sono controllati tramite istanze di Azure Key Vault.
- Per monitorare le violazioni della sicurezza e gli attacchi viene usato Centro sicurezza di Azure.
- Centro sicurezza di Azure e Monitoraggio di Azure vengono usati entrambi per monitorare la governance del cloud.
- Per automatizzare la conformità ai criteri vengono usati Azure Blueprints, Criteri di Azure e i gruppi di gestione.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

L'obiettivo è integrare l'azienda acquisita nelle procedure operative esistenti ove possibile.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Costo di acquisizione aziendale:** L'acquisizione della nuova azienda è stimata come redditizia in circa cinque anni. Considerato il ritorno lento dell'investimento, il consiglio vuole mantenere sotto controlli i costi di acquisizione quanto più possibile. C'è il rischio di un conflitto tra controllo dei costi e integrazione tecnica.

Questo rischio aziendale può comportare alcuni rischi tecnici:

- La migrazione cloud potrebbe produrre costi di acquisizione aggiuntivi.
- Il nuovo ambiente potrebbe non essere governato correttamente, che potrebbe causare violazioni dei criteri.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di correggere i nuovi rischi e l'implementazione della guida:

- Tutti gli asset in un cloud secondario devono essere monitorati tramite gli strumenti esistenti per la gestione operativa e il monitoraggio della sicurezza.
- Tutte le unità organizzative devono essere integrate nel provider di identità esistente.
- Il provider di identità primario deve gestire l'autenticazione per gli asset nel cloud secondario.

## <a name="incremental-improvement-of-governance-practices"></a>Miglioramento incrementale delle procedure di governance

In questa sezione dell'articolo verrà modificata la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste modifiche di progettazione soddisferanno le nuove istruzioni dei criteri aziendali.

1. Connettere le reti. Questo passaggio viene eseguito dai team di rete e della sicurezza IT e supportato dal team di governance del cloud. L'aggiunta di una connessione dal provider MPLS/linea dedicata al nuovo cloud consentirà di integrare le reti. L'aggiunta di tabelle di routing e di configurazioni del firewall consentirà di controllare l'accesso e il traffico tra gli ambienti.
1. Consolidare i provider di identità. A seconda dei carichi di lavoro ospitati nel cloud secondario, esistono diverse opzioni per il consolidamento dei provider di identità. Di seguito sono riportati alcuni esempi:
    1. Per le applicazioni che eseguono l'autenticazione tramite OAuth 2, gli utenti in Active Directory nel cloud secondario possono essere semplicemente replicati nel tenant di Azure AD esistente. Questo assicura che tutti gli utenti possano essere autenticati nel tenant.
    1. Da altra parte, la federazione consente alle unità organizzative di confluire in Active Directory locale, quindi nell'istanza di Azure AD.
1. Aggiungere asset ad Azure Site Recovery.
    1. Azure Site Recovery è stato progettato dall'inizio come strumento ibrido o multicloud.
    1. Potrebbe essere possibile proteggere le macchine virtuali nel cloud secondario con gli stessi processi di Azure Site Recovery usati per proteggere gli asset locali.
1. Aggiungere asset a gestione costi di Azure.
    1. Gestione costi di Azure è stato progettato dall'inizio come uno strumento per più cloud.
    1. Le macchine virtuali nel cloud secondario possono essere compatibili con Gestione costi di Azure per alcuni provider di servizi cloud. Si potrebbe incorrere in costi aggiuntivi.
1. Aggiungere asset a Monitoraggio di Azure.
    1. Monitoraggio di Azure è stato progettato sin dall'inizio come strumento cloud ibrido.
    1. Le macchine virtuali nel cloud secondario potrebbero essere compatibili con gli agenti di Monitoraggio di Azure, permettendo così di includerle in Monitoraggio di Azure per il monitoraggio operativo.
1. Adottare gli strumenti di applicazione della governance.
    1. L'applicazione della governance è specifica del cloud,
    1. I criteri aziendali stabiliti nella Guida alla governance non sono specifici del cloud. Anche se l'implementazione può variare da cloud a cloud, i criteri possono essere applicati al provider secondario.

Man mano che l'adozione di più cloud aumenta, le modifiche alla progettazione precedenti continueranno a maturare.

## <a name="conclusion"></a>Conclusione

Questa serie di articoli descrive lo sviluppo incrementale delle procedure consigliate di governance, allineate con le esperienze di questa società fittizia. Iniziando gradualmente, ma sulle giuste basi, la società è stata in grado di muoversi rapidamente, applicando comunque la giusta quantità di governance al momento giusto. L'MVP di per sé non ha protetto il cliente. Al contrario, ha creato le fondamenta per gestire i rischi e aggiungere protezioni. A questo punto, sono stati applicati livelli di governance per correggere i rischi tangibili. Il percorso presentato in questo articolo non sarà perfettamente allineato con le esperienze di tutti i lettori. È infatti da intendere come modello per la governance incrementale. È consigliabile adattare queste procedure consigliate in base ai propri specifici vincoli e requisiti di governance.
