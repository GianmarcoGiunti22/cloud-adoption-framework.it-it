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
ms.openlocfilehash: 9613e4be1173687e5f40409c34799c26480b0702
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829449"
---
# <a name="software-defined-networking-paas-only"></a>Software Defined Networking: solo PaaS

Quando si implementa una risorsa piattaforma distribuita come servizio (PaaS), il processo di distribuzione crea automaticamente una rete sottostante presunta con un numero limitato di controlli su tale rete, inclusi bilanciamento del carico, blocco delle porte e connessioni ad altri servizi PaaS.

In Azure diversi tipi di risorsa PaaS possono essere [distribuiti](/azure/virtual-network/virtual-network-for-azure-services) o [connessi a](/azure/virtual-network/virtual-network-service-endpoints-overview) una rete virtuale, consentendo a queste risorse di integrarsi con l'infrastruttura di rete virtuale esistente. Altri servizi, ad esempio gli [ambienti del servizio app](/azure/app-service/environment/intro), i [Servizi Kubernetes di Azure](/azure/aks/intro-kubernetes)e [Service Fabric](/azure/service-fabric/service-fabric-overview) devono essere distribuiti all'interno della rete virtuale. Tuttavia, in molti casi un'architettura di rete solo PaaS, che si basa solo sulle funzionalità di rete nativa predefinite fornite dalle risorse PaaS, è sufficiente per soddisfare i requisiti di connettività e gestione del traffico del carico di lavoro.

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
