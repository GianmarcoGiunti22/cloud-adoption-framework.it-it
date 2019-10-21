---
title: Creare coerenza del cloud ibrido
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definizione dell'approccio per la creazione della coerenza del cloud ibrido.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5b2de64af3d7e48a38fd1f125fc5f8b37b190dd2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547188"
---
# <a name="create-hybrid-cloud-consistency"></a>Creare coerenza del cloud ibrido

Questo articolo illustra gli approcci di alto livello per la creazione della coerenza del cloud ibrido.

I modelli di distribuzione ibrida durante la migrazione possono ridurre il rischio e contribuire a una transizione fluida dell'infrastruttura. Le piattaforme cloud offrono il massimo livello di flessibilità per i processi aziendali. Molte organizzazioni sono riluttanti a eseguire il passaggio al cloud. Ma preferiscono avere il controllo completo sui dati più sensibili. Sfortunatamente, i server locali non consentono lo stesso tasso di innovazione del cloud. Una soluzione cloud ibrida offre la velocità di innovazione nel cloud e il controllo della gestione locale.

## <a name="integrate-hybrid-cloud-consistency"></a>Integrare la coerenza del cloud ibrido

L'uso di una soluzione cloud ibrida consente alle organizzazioni di ridimensionare le risorse di calcolo. Elimina inoltre la necessità di sostenere ingenti spese in conto capitale per gestire picchi nella domanda a breve termine. Le modifiche apportate all'azienda possono favorire la necessità di liberare risorse locali per dati o applicazioni più sensibili. Il deprovisioning delle risorse cloud è più semplice, veloce e meno costoso. Si pagano solo le risorse usate temporaneamente dall'organizzazione, senza dover acquistare e gestire risorse aggiuntive. Questo approccio riduce la quantità di apparecchiature che potrebbero rimanere inattive per lunghi periodi di tempo. Cloud computing ibrido offre tutti i vantaggi di cloud computing flessibilità, la scalabilità e l'efficienza dei costi con il minor rischio possibile di esposizione dei dati.

![Creating la coerenza del cloud ibrido tra identità, gestione, sicurezza, dati, sviluppo e DevOps ](../../_images/hybrid-consistency.png)
*Figura 1-creazione della coerenza del cloud ibrido tra identità, gestione, sicurezza, dati, sviluppo e DevOps.*

Una vera soluzione cloud ibrida deve fornire quattro componenti, ognuno dei quali offre vantaggi significativi:

- **Identità comune per le applicazioni locali e cloud:** Questo componente consente di migliorare la produttività degli utenti offrendo agli utenti Single Sign-On (SSO) a tutte le applicazioni. Garantisce inoltre la coerenza tra le applicazioni e gli utenti oltre i limiti di rete o cloud.
- **Gestione e sicurezza integrate nel cloud ibrido:** Questo componente offre un modo coerente per monitorare, gestire e proteggere l'ambiente, consentendo una maggiore visibilità e controllo.
- **Una piattaforma di dati coerente per il Data Center e il cloud:** Questo componente crea la portabilità dei dati, combinata con l'accesso facile ai servizi dati locali e cloud per ottenere informazioni approfondite su tutte le origini dati.
- **Sviluppo unificato e DevOps nel cloud e nei data center locali:** Questo componente consente di spostare le applicazioni tra i due ambienti in base alle esigenze. La produttività degli sviluppatori migliora perché entrambe le posizioni hanno ora lo stesso ambiente di sviluppo.

Di seguito sono riportati alcuni esempi di questi componenti dal punto di vista di Azure:

- Azure Active Directory (Azure AD) funziona con Active Directory locale per fornire un'identità comune a tutti gli utenti. SSO in locale e tramite il cloud per consentire agli utenti di accedere in modo semplice e sicuro alle applicazioni e agli asset di cui hanno bisogno. Gli amministratori possono gestire i controlli di sicurezza e governance, nonché la flessibilità necessaria per regolare le autorizzazioni senza influire sull'esperienza utente.
- Azure offre servizi di gestione e sicurezza integrati per l'infrastruttura cloud e locale. Questi servizi includono un set integrato di strumenti usati per monitorare, configurare e proteggere i cloud ibridi. Questo approccio end-to-end per la gestione riguarda in modo specifico le questioni reali che fanno fronte alle organizzazioni che considerano una soluzione cloud ibrida.
- Il cloud ibrido di Azure offre strumenti comuni che garantiscono l'accesso sicuro a tutti i dati, in modo fluido ed efficiente. I servizi dati di Azure collaborano con Microsoft SQL Server per creare una piattaforma dati coerente. Un modello di cloud ibrido coerente consente agli utenti di lavorare con dati operativi e analitici. Gli stessi servizi vengono forniti in locale e nel cloud per il data warehousing, l'analisi dei dati e la visualizzazione dei dati.
- I servizi cloud di Azure, combinati con Azure Stack in locale, offrono sviluppo unificato e DevOps. La coerenza nel cloud e in locale significa che il team di DevOps può creare applicazioni che vengono eseguite in entrambi gli ambienti e che possono essere facilmente distribuite nella posizione corretta. È anche possibile riutilizzare i modelli nella soluzione ibrida, che consente di semplificare ulteriormente i processi di DevOps.

## <a name="azure-stack-in-a-hybrid-cloud-environment"></a>Azure Stack è un ambiente cloud ibrido

Azure Stack è una soluzione cloud ibrida che consente alle organizzazioni di eseguire servizi coerenti con Azure nel proprio Data Center. Offre un'esperienza semplificata per lo sviluppo, la gestione e la sicurezza, coerente con i servizi cloud pubblici di Azure. Azure Stack è un'estensione di Azure. È possibile usarlo per eseguire i servizi di Azure dagli ambienti locali e quindi passare al cloud di Azure se e quando necessario.

Con Azure Stack, è possibile distribuire e usare IaaS e PaaS usando gli stessi strumenti e offrendo la stessa esperienza del cloud pubblico di Azure. La gestione di Azure Stack, indipendentemente dal fatto che si scelga il portale dell'interfaccia utente Web o PowerShell, ha un aspetto coerente con Azure per gli amministratori IT e gli utenti finali.

Azure e Azure Stack aprono nuovi casi di utilizzo ibrido per le applicazioni line-of-business rivolte ai clienti e interne:

- **Soluzioni perimetrali e disconnesse.** Per soddisfare i requisiti di latenza e connettività, i clienti possono elaborare i dati localmente in Azure Stack e quindi aggregarli in Azure per un'ulteriore analisi. Possono usare la logica dell'applicazione comune in entrambi. Molti clienti sono interessati a questo scenario perimetrale in diversi contesti, ad esempio le fabbriche, le navi da crociera e gli alberi.
- **Applicazioni cloud che soddisfano diverse normative.** I clienti possono sviluppare e distribuire applicazioni in Azure, con la massima flessibilità per la distribuzione in locale su Azure Stack per soddisfare i requisiti normativi o relativi ai criteri. Non sono necessarie modifiche al codice. Gli esempi di applicazioni includono il controllo globale, la creazione di report finanziari, il commercio estero, il gioco online e la segnalazione delle spese. I clienti a volte possono cercare di distribuire istanze diverse della stessa applicazione in Azure o Azure Stack, in base ai requisiti aziendali e tecnici. Mentre Azure soddisfa la maggior parte dei requisiti, Azure Stack integra l'approccio di distribuzione quando necessario.
- **Modello di applicazione cloud in locale.** I clienti possono usare servizi Web di Azure, contenitori, architetture serverless e architetture di microservizi per aggiornare ed estendere le applicazioni esistenti o crearne di nuove. È possibile usare processi coerenti per DevOps in Azure nel cloud e in Azure Stack in locale. La modernizzazione delle applicazioni ha un interesse crescente anche per le applicazioni cruciali di base.

Azure Stack è disponibile tramite due opzioni di distribuzione:

- **Azure stack sistemi integrati:** Azure Stack sistemi integrati sono offerti tramite partner Microsoft e hardware per creare una soluzione in grado di offrire un'innovazione basata sul cloud bilanciata con una gestione semplice. Poiché Azure Stack viene offerto come sistema integrato di hardware e software, è possibile ottenere flessibilità e controllo pur continuando ad adottare l'innovazione dal cloud. Azure Stack i sistemi integrati hanno una dimensione compresa tra 4 e 12 nodi. Sono supportati congiuntamente dal partner hardware e da Microsoft. Usare i sistemi integrati Azure Stack per rendere possibili nuovi scenari per i carichi di lavoro di produzione.
- **Azure stack Development Kit:** Il Microsoft Azure Stack Development Kit è una distribuzione a nodo singolo di Azure Stack. È possibile usarlo per valutare e ottenere informazioni sulle Azure Stack. È anche possibile usare il kit come ambiente di sviluppo, in cui è possibile sviluppare usando le API e gli strumenti coerenti con Azure. Il Azure Stack Development Kit non è destinato all'uso come ambiente di produzione.

## <a name="azure-stack-one-cloud-ecosystem"></a>Ecosistema Azure Stack un cloud

È possibile velocizzare le iniziative Azure Stack usando l'ecosistema completo di Azure:

- Azure garantisce che la maggior parte delle applicazioni e dei servizi certificati per Azure funzioneranno in Azure Stack. Diversi ISV estendono le proprie soluzioni ai Azure Stack. Questi ISV includono BitNami, Docker, Kemp Technologies, pivotal Cloud Foundry, Red Hat Enterprise Linux e SUSE Linux.
- È possibile scegliere di usare e gestire Azure Stack come servizio completamente gestito. Molti partner avranno offerte di servizi gestiti in Azure e Azure Stack a breve. Questi partner includono Tieto, Yourhosting, revera, Pulse e NTT. Questi partner forniscono servizi gestiti per Azure tramite il programma Cloud Solution Provider (CSP). Stanno estendendo le loro offerte per includere soluzioni ibride.
- Come esempio di una soluzione cloud ibrida completamente gestita e completamente gestita, Avanade offre un'offerta all-in-One. Include servizi di trasformazione cloud, software, infrastruttura, installazione e configurazione e servizi gestiti in corso. In questo modo i clienti possono utilizzare Azure Stack proprio come fanno oggi con Azure.
- I provider consentono di accelerare le iniziative di modernizzazione delle applicazioni creando soluzioni di Azure end-to-end per i clienti. Offrono set di competenze di Azure, conoscenza di dominio e settore e competenze di processo, ad esempio DevOps. Ogni Azure Stack cloud è un'opportunità per un provider di progettare la soluzione e condurre e influenzare la distribuzione del sistema. Possono anche personalizzare le funzionalità incluse e fornire le attività operative. Esempi di provider sono Avanade, DXC, Dell EMC Services, Infront Consulting Group, HPE Pointnext e PwC (in precedenza PricewaterhouseCoopers).
