---
title: Funzionamento di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del funzionamento interno di Azure
author: alexbuckgit
ms.author: abuck
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: governance
ms.openlocfilehash: 1f627dcba8db040ea212f151f216428b724c90d0
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048458"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-does-azure-work"></a>Funzionamento di Azure

Azure è una piattaforma cloud pubblica di Microsoft. Azure offre una vasta gamma di servizi, tra cui piattaforma distribuita come servizio (PaaS), infrastruttura distribuita come servizio (IaaS) e funzionalità del servizio di database gestito. Ma che cos'è esattamente Azure e come funziona?

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ixGo]

Come altre piattaforme cloud, Azure si basa su una tecnologia nota come _virtualizzazione_. Quasi tutto l'hardware di computer può essere emulato in software perché è costituito semplicemente da un set di istruzioni codificate in silicone in modo permanente o semipermanente. Usando un livello di emulazione che associa le istruzioni del software a quelle dell'hardware, un componente hardware virtualizzato può essere eseguito nel software come un componente fisico realmente esistente.

In pratica, il cloud è costituito da un set di server fisici in uno o più data center che eseguono hardware virtualizzato per conto dei clienti. In che modo il cloud riesce a creare, avviare, arrestare ed eliminare milioni di istanze di hardware virtualizzato per milioni di clienti allo stesso tempo?

Per comprendere questo concetto, si esaminerà l'architettura dell'hardware nel data center. All'interno di ogni data center è presente una raccolta di server che si siedono nei rack server. Ogni rack di server contiene numerosi **blade** con un commutatore per la connettività di rete e un'unità PDU (Power Distribution Unit) per l'alimentazione. I rack sono talvolta raggruppati in unità più grandi, dette _cluster_.

All'interno di ogni rack o cluster, la maggior parte dei server ha il compito di eseguire le istanze di hardware virtualizzato per conto degli utenti. Tuttavia, alcuni server eseguono il software di gestione cloud noto come controller di infrastruttura. Il _controller di infrastruttura_ è un'applicazione distribuita a cui sono affidati numerosi compiti, tra cui l'allocazione dei servizi, il monitoraggio dell'integrità dei server e dei servizi in esecuzione su di essi e la correzione di eventuali errori dei server.

Ogni istanza del controller di infrastruttura è connessa a un altro set di server che eseguono il software di orchestrazione del cloud, in genere denominato _front-end_. Il front-end ospita i servizi Web, le API RESTful e i database interni di Azure usati per tutte le funzioni eseguite dal cloud.

Ad esempio, il front-end ospita i servizi che gestiscono le richieste dei clienti per allocare risorse di Azure, ad esempio [macchine virtuali](https://docs.microsoft.com/azure/virtual-machines), e servizi come [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction). Per prima cosa, il front-end convalida l'utente e verifica che sia autorizzato ad allocare le risorse richieste. In tal caso, il front-end controlla un database per individuare un rack server con capacità sufficiente e quindi indica al controller di infrastruttura su tale rack di allocare la risorsa.

Fondamentalmente, Azure è una vasta raccolta di server e componenti hardware di rete che eseguono un set complesso di applicazioni distribuite per orchestrare la configurazione e il funzionamento dell'hardware e del software virtualizzati su tali server. Si tratta di un'orchestrazione che rende Azure così potente&mdash;gli utenti non sono più responsabili della gestione e dell'aggiornamento dell'hardware, in quanto Azure esegue questa operazione dietro le quinte.

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono gli elementi interni di Azure, vedere informazioni sulla governance delle risorse cloud.

> [!div class="nextstepaction"]
> [Informazioni sulla governance delle risorse](../govern/resource-consistency/what-is-governance.md)
