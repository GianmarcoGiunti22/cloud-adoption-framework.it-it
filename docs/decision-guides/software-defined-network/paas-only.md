---
title: 'Software Defined Networking: solo PaaS'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Discussione del modello solo PaaS per Software Defined Networking nel cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: ca73050c2ca6a753727b7b972a3c1febe4ec9515
ms.sourcegitcommit: e0a783dac15bc4c41a2f4ae48e1e89bc2dc272b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73058740"
---
# <a name="software-defined-networking-paas-only"></a>Software Defined Networking: solo PaaS

Quando si implementa una risorsa piattaforma distribuita come servizio (PaaS), il processo di distribuzione crea automaticamente una rete sottostante presunta con un numero limitato di controlli su tale rete, inclusi bilanciamento del carico, blocco delle porte e connessioni ad altri servizi PaaS.

In Azure diversi tipi di risorsa PaaS possono essere [distribuiti](https://docs.microsoft.com/azure/virtual-network/virtual-network-for-azure-services) o [connessi a](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) una rete virtuale, consentendo a queste risorse di integrarsi con l'infrastruttura di rete virtuale esistente. Altri servizi, ad esempio gli [ambienti del servizio app](https://docs.microsoft.com/azure/app-service/environment/intro), [Azure KUBERNETES Service (AKS)](https://docs.microsoft.com/azure/aks/intro-kubernetes)e [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) devono essere distribuiti all'interno della rete virtuale. Tuttavia, in molti casi un'architettura di rete solo PaaS, che si basa solo sulle funzionalità di rete nativa predefinite fornite dalle risorse PaaS, è sufficiente per soddisfare i requisiti di connettività e gestione del traffico del carico di lavoro.

Se si sta valutando un'architettura di rete solo PaaS, verificare che i presupposti obbligatori siano allineati ai requisiti.

## <a name="paas-only-assumptions"></a>Presupposti solo PaaS

La distribuzione di un'architettura di rete solo PaaS presuppone quanto segue:

- L'applicazione distribuita è un'applicazione autonoma o dipende solo da altre risorse PaaS che non richiedono una rete virtuale.
- I team responsabili delle operazioni IT possono aggiornare gli strumenti, il training e i processi per supportare la gestione, la configurazione e la distribuzione delle applicazioni PaaS autonome.
- L'applicazione PaaS non fa parte di un più ampio processo di migrazione cloud che includerà risorse IaaS.

Questi presupposti sono qualificatori minimi allineati alla distribuzione di una rete solo PaaS. Sebbene questo approccio possa essere allineato ai requisiti di una singola distribuzione di applicazione, ogni team di adozione del cloud deve prendere in considerazione queste domande a lungo termine:

- L'ambito o le dimensioni di questa distribuzione si espanderanno rendendo necessario l'accesso ad altre risorse non PaaS?
- Sono pianificate altre distribuzioni PaaS oltre alla soluzione corrente?
- L'organizzazione ha in programma altre migrazioni cloud in futuro?

Le risposte a queste domande non precludono a un team la scelta di un'opzione solo PaaS, ma è opportuno valutarle prima di prendere una decisione finale.
