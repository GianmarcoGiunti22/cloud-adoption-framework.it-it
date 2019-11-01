---
title: Controllo degli accessi in base al ruolo consigliato
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Controllo degli accessi in base al ruolo consigliato
author: rotycenh
ms.author: brblanch
ms.date: 11/28/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: BrianBlanchard
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 6aa17f3ffb16afae0b27bcccbee84ddf9ad2c5f0
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73243136"
---
# <a name="role-based-access-control"></a>Controllo degli accessi basato sul ruolo

La definizione di privilegi e diritti di accesso basati su gruppo è una procedura consigliata. La definizione di gruppi, anziché di singoli utenti, consente di gestire più facilmente i criteri di accesso, mantenere la coerenza degli accessi tra i team e ridurre gli errori di configurazione. L'assegnazione e la rimozione di utenti nei gruppi appropriati sono inoltre utili per mantenere aggiornati i privilegi di utenti specifici. Il [controllo degli accessi in base al ruolo (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/overview) di Azure consente una gestione degli accessi con granularità fine per le risorse organizzate in base ai ruoli utente.

Per una panoramica delle procedure di controllo degli accessi in base al ruolo consigliate come parte di una strategia di sicurezza e gestione delle identità, vedere [Procedure consigliate per la sicurezza con il controllo di accesso e la gestione delle identità di Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices#use-role-based-access-control).

## <a name="overview-of-role-based-access-control"></a>Panoramica del controllo degli accessi in base al ruolo

Usando il [controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/overview), è possibile separare i compiti all'interno del team e concedere a utenti, gruppi, entità servizio o identità gestite specifiche di Azure Active Directory (Azure AD) solo l'accesso sufficiente per eseguire le loro attività. Invece di concedere a tutti l'accesso senza restrizioni alla sottoscrizione o alle risorse di Azure, è possibile limitare le autorizzazioni per ogni set di risorse.

Le [definizioni di ruolo Controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/role-definitions) elencano le operazioni consentite o non consentite agli utenti o ai gruppi assegnati a un determinato ruolo. L'[ambito](https://docs.microsoft.com/azure/role-based-access-control/overview#scope) di un ruolo specifica le risorse a cui si applicano queste autorizzazioni definite. Gli ambiti possono essere definiti a più livelli: gruppo di gestione, sottoscrizione, gruppo di risorse o risorsa. Gli ambiti sono strutturati in una relazione di tipo padre/figlio.

![Gerarchia degli ambiti del controllo degli accessi in base al ruolo](../../_images/azure-best-practices/rbac-scope.png)

Per istruzioni dettagliate per l'assegnazione di utenti e gruppi a ruoli specifici e l'assegnazione di ruoli ad ambiti, vedere [Gestire l'accesso alle risorse di Azure usando il controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal).

Quando si pianifica una strategia di controllo di accesso, usare un modello di accesso con privilegi minimi che conceda agli utenti solo le autorizzazioni necessarie per eseguire le loro attività. Il diagramma seguente mostra uno schema consigliato per l'uso del controllo degli accessi in base al ruolo in base a questo approccio.

![Modello consigliato per l'uso del controllo degli accessi in base al ruolo](../../_images/azure-best-practices/rbac-least-privilege.png)

> [!NOTE]
> Quanto più specifiche o dettagliate sono le autorizzazioni definite dall'utente, tanto più probabile è che i controlli di accesso diventino complessi e difficili da gestire. Questo è particolarmente vero man mano che aumentano le dimensioni dell'ambiente cloud. Evitare di definire autorizzazioni specifiche per le risorse. In alternativa, [usare gruppi di gestione](https://docs.microsoft.com/azure/governance/management-groups) per il controllo di accesso a livello aziendale e [gruppi di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) per il controllo di accesso nell'ambito di sottoscrizioni. Evitare anche di definire autorizzazioni specifiche per gli utenti. In alternativa, assegnare l'accesso a [gruppi in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups).

## <a name="using-built-in-rbac-roles"></a>Uso dei ruoli predefiniti del controllo degli accessi in base al ruolo

In Azure sono disponibili molte definizioni di ruolo predefinite, con tre ruoli principali per concedere l'accesso:

- Il ruolo [Proprietario](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) può gestire qualsiasi cosa, incluso l'accesso alle risorse.
- Il ruolo [Collaboratore](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) può gestire qualsiasi cosa, tranne l'accesso alle risorse.
- Il ruolo [Lettore](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader) può visualizzare qualsiasi cosa, ma senza apportare modifiche.

A partire da questi livelli di accesso di base, i ruoli predefiniti aggiuntivi forniscono controlli più dettagliati per accedere a specifici tipi di risorse o funzionalità di Azure. È ad esempio possibile gestire l'accesso alle macchine virtuali usando i ruoli predefiniti seguenti:

- Il ruolo [Accesso amministratore alle macchine virtuali](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-administrator-login) può visualizzare le macchine virtuali nel portale e accedere come _amministratore_.
- Il ruolo [Collaboratore Macchina virtuale](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) può gestire le macchine virtuali, ma non può accedere né a tali macchine né alla rete virtuale o all'account di archiviazione a cui sono connesse.
- Il ruolo [Accesso utente alle macchine virtuali](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-user-login) può visualizzare le macchine virtuali nel portale e accedere come normale utente.

Per un altro esempio d'uso dei ruoli predefiniti per gestire l'accesso a particolari funzionalità, vedere le informazioni relative al controllo dell'accesso alle funzionalità di rilevamento dei costi in [Tenere traccia dei costi tra business unit, ambienti o progetti](../azure-best-practices/track-costs.md#provide-the-right-level-of-cost-access).

Per un elenco completo dei ruoli predefiniti disponibili, vedere [Ruoli predefiniti per le risorse di Azure](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles).

## <a name="using-custom-roles"></a>Uso dei ruoli personalizzati

Anche se i ruoli predefiniti di Azure supportano un'ampia gamma di scenari di controllo di accesso, possono non soddisfare tutte le esigenze dell'organizzazione o del team. Se, ad esempio, un gruppo di utenti è responsabile della gestione delle macchine virtuali e delle risorse del database SQL di Azure, può essere necessario creare un ruolo personalizzato per ottimizzare la gestione dei controlli di accesso necessari.

La documentazione relativa al controllo degli accessi in base al ruolo di Azure contiene istruzioni sulla [creazione di ruoli personalizzati](https://docs.microsoft.com/azure/role-based-access-control/custom-roles) oltre a informazioni dettagliate sul [funzionamento delle definizioni di ruolo](https://docs.microsoft.com/azure/role-based-access-control/role-definitions).

## <a name="separation-of-responsibilities-and-roles-for-large-organizations"></a>Separazione di responsabilità e ruoli per le organizzazioni di grandi dimensioni

Il controllo degli accessi in base al ruolo consente alle organizzazioni di assegnare team diversi a varie attività di gestione nell'ambito di vasti ambienti cloud. I team IT centrali possono infatti controllare le principali funzionalità di sicurezza e di accesso e, allo stesso tempo, gli sviluppatori di software e altri team possono disporre di un'ampia capacità di controllo su carichi di lavoro o gruppi di risorse specifici.

La maggior parte degli ambienti cloud può inoltre trarre vantaggio da una strategia di controllo di accesso basata su più ruoli in cui è accentuata la separazione delle responsabilità tra i ruoli. Questo approccio richiede che il completamento di qualsiasi modifica significativa alle risorse o all'infrastruttura coinvolga più ruoli. In questo modo si ha la certezza che una modifica venga rivista e approvata da più persone. Questa separazione delle responsabilità limita la capacità di un singolo utente di accedere a dati sensibili o introdurre vulnerabilità senza conoscere gli altri membri del team.

La tabella seguente illustra un modello comune per suddividere le responsabilità IT in ruoli personalizzati distinti:

<!-- markdownlint-disable MD033 -->

| Group | Nome del ruolo comune | Responsabilità |
| --- | --- | --- |
| Operazioni per la sicurezza | SecOps | Esegue una supervisione generale della sicurezza.<br/><br/> Stabilisce e applica i criteri di sicurezza, ad esempio la crittografia dei file inattivi.<br/><br/> Gestisce le chiavi di crittografia.<br/><br/> Gestisce le regole del firewall. |
| Operazioni per la rete | NetOps | Gestisce la configurazione e le operazioni nell'ambito delle reti virtuali, ad esempio le route e i peering. |
| Operazioni per i sistemi | SysOps | Specifica le opzioni dell'infrastruttura di calcolo e archiviazione e gestisce le risorse che sono state distribuite. |
| Sviluppo, test e operazioni | DevOps | Compila e distribuisce le funzionalità e le applicazioni per i carichi di lavoro.<br/><br/> Gestisce le funzionalità e le applicazioni per soddisfare i contratti di servizio e altri standard di qualità. |

<!-- markdownlint-enable MD033 -->

La suddivisione delle azioni e delle autorizzazioni in questi ruoli standard è spesso la stessa nelle applicazioni, nelle sottoscrizioni o nell'intero ambiente cloud, anche se questi ruoli vengono eseguiti da persone diverse a livelli diversi. Di conseguenza, è possibile creare un set comune di definizioni di ruolo Controllo degli accessi in base al ruolo da applicare in diversi ambiti all'interno del proprio ambiente. Gli utenti e i gruppi possono quindi essere assegnati a un ruolo comune, ma solo per l'ambito di risorse, gruppi di risorse, sottoscrizioni o gruppi di gestione di cui sono responsabili.

Ad esempio, in una [topologia di rete hub-spoke](../azure-best-practices/hub-spoke-network-topology.md) con più sottoscrizioni, è possibile disporre di un set comune di definizioni di ruolo per l'hub e per tutti i spoke del carico di lavoro. Il ruolo NetOps di una sottoscrizione di hub può essere assegnato ai membri del personale IT centrale dell'organizzazione che sono responsabili della gestione della rete per i servizi condivisi usati da tutti i carichi di lavoro. Il ruolo NetOps di una sottoscrizione di spoke di carico di lavoro può quindi essere assegnato ai membri del team specifico del carico di lavoro, consentendo loro di configurare la rete all'interno di tale sottoscrizione in modo da supportare al meglio i requisiti del carico di lavoro. La stessa definizione di ruolo viene usata per entrambi, ma le assegnazioni basate su ambito garantiscono che gli utenti abbiano accesso solo alle risorse necessarie per svolgere le proprie attività.
