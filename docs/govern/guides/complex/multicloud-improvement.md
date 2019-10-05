---
title: 'Guida alla governance per le aziende complesse: Miglioramento del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: Miglioramento del cloud'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: aaafd0d4fa3c94d1ccf0b5bc3ee3f30377a2b08e
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967661"
---
# <a name="governance-guide-for-complex-enterprises-multicloud-improvement"></a>Guida alla governance per le aziende complesse: Miglioramento del cloud

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

Microsoft riconosce che i clienti possono adottare più cloud per scopi specifici. La società fittizia in questa guida non è un'eccezione. In parallelo con il percorso di adozione di Azure, il successo aziendale ha portato all'acquisizione di una piccola ma complementare. La nuova azienda gestisce tutte le operazioni IT con un provider di servizi cloud diverso.

Questo articolo descrive i cambiamenti introdotti dall'integrazione della nuova organizzazione. Ai fini della descrizione, si presuppone che questa società abbia completato ogni iterazione di governance descritta in questa guida alla governance.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Nella fase precedente della presente descrizione, la società ha iniziato a implementare i controlli dei costi e il monitoraggio dei costi, in quanto la spesa cloud diventa parte delle normali spese operative dell'azienda.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- Il controllo delle identità avviene tramite un'istanza locale di Active Directory. La gestione delle identità ibride è facilitata tramite la replica in Azure Active Directory.
- Operazioni IT o operazioni cloud sono gestite principalmente da monitoraggio di Azure e dalle funzionalità di automazione correlate.
- Il ripristino di emergenza e la continuità aziendale (DRBC) sono controllati dalle istanze di Azure Vault.
- Per monitorare le violazioni della sicurezza e gli attacchi viene usato Centro sicurezza di Azure.
- Centro sicurezza di Azure e Monitoraggio di Azure vengono usati entrambi per monitorare la governance del cloud.
- Per automatizzare la conformità ai criteri vengono usati Azure Blueprints, Criteri di Azure e i gruppi di gestione.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

L'obiettivo è integrare l'azienda acquisita nelle procedure operative esistenti ove possibile.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Costo di acquisizione aziendale:** L'acquisizione della nuova azienda è stimata come redditizia in circa cinque anni. Considerato il ritorno lento dell'investimento, il consiglio vuole mantenere sotto controlli i costi di acquisizione quanto più possibile. C'è il rischio di un conflitto tra controllo dei costi e integrazione tecnica.

Questo rischio aziendale può comportare alcuni rischi tecnici:

- C'è un rischio di migrazione cloud che produce costi di acquisizione aggiuntivi.
- Esiste anche il rischio che la governance del nuovo ambiente non sia appropriata oppure che si verifichino violazioni dei criteri.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida.

- Tutti gli asset in un cloud secondario devono essere monitorati tramite gli strumenti esistenti per la gestione operativa e il monitoraggio della sicurezza.
- Tutte le unità organizzative devono essere integrate nel provider di identità esistente.
- Il provider di identità primario deve gestire l'autenticazione per gli asset nel cloud secondario.

## <a name="incremental-improvement-of-the-best-practices"></a>Miglioramento incrementale delle procedure consigliate

Questa sezione dell'articolo migliora la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

1. Connettere le reti. Eseguita da rete e sicurezza IT, supportata dalla governance.
    1. L'aggiunta di una connessione dal provider MPLS o a linea in lease al nuovo Cloud integrerà le reti. L'aggiunta di tabelle di routing e di configurazioni del firewall consentirà di controllare l'accesso e il traffico tra gli ambienti.
2. Consolidare i provider di identità. A seconda dei carichi di lavoro ospitati nel cloud secondario, esistono diverse opzioni per il consolidamento dei provider di identità. Di seguito sono riportati alcuni esempi:
    1. Per le applicazioni che eseguono l'autenticazione tramite OAuth 2, gli utenti in Active Directory nel cloud secondario possono essere semplicemente replicati nel tenant di Azure AD esistente.
    2. Nel caso opposto, la federazione tra i due provider di identità in locale consentirebbe la replica degli utenti dai nuovi domini di Active Directory in Azure.
3. Aggiungere asset ad Azure Site Recovery.
    1. Azure Site Recovery è stato creato come strumento ibrido e multicloud sin dall'inizio.
    2. Potrebbe essere possibile proteggere le macchine virtuali nel cloud secondario con gli stessi processi di Azure Site Recovery usati per proteggere gli asset locali.
4. Aggiungere asset a gestione costi di Azure.
    1. Gestione costi di Azure è stato creato come strumento multicloud sin dall'inizio.
    2. Le macchine virtuali nel cloud secondario potrebbero essere compatibili con Gestione costi di Azure per alcuni provider di servizi cloud. Si potrebbe incorrere in costi aggiuntivi.
5. Aggiungere asset a Monitoraggio di Azure.
    1. Monitoraggio di Azure è stato concepito sin dall'inizio come strumento cloud ibrido.
    2. Le macchine virtuali nel cloud secondario potrebbero essere compatibili con gli agenti di Monitoraggio di Azure, permettendo così di includerle in Monitoraggio di Azure per il monitoraggio operativo.
6. Strumenti di applicazione della governance.
    1. L'applicazione della governance è specifica del cloud,
    2. I criteri aziendali stabiliti nella Guida alla governance non sono specifici del cloud. Anche se l'implementazione può variare da cloud a cloud, le definizioni dei criteri possono essere applicate al provider secondario.

L'adozione di più cloud deve essere contenuta nel punto in cui è necessario in base alle esigenze tecniche o ai requisiti aziendali specifici. Man mano che l'adozione di più cloud aumenta, comporta rischi di complessità e sicurezza.

## <a name="next-steps"></a>Passaggi successivi

In molte grandi aziende, le cinque discipline della governance del cloud possono essere blocchi da adottare. Nell'articolo successivo sono riportate alcune considerazioni aggiuntive sulla governance di un team per contribuire a garantire un successo a lungo termine nel cloud.

> [!div class="nextstepaction"]
> [Più livelli di governance](./multiple-layers-of-governance.md)
