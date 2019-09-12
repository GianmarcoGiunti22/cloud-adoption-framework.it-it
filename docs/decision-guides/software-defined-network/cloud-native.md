---
title: 'Software Defined Networking: Gestione nativa del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Discussione dei servizi di rete virtuale nativi del cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 1c30e57761b12d00617296fb3f9d5a87b8b6cce7
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828331"
---
# <a name="software-defined-networking-cloud-native"></a>Software Defined Networking: Gestione nativa del cloud

Una rete virtuale nativa del cloud è obbligatoria quando si distribuiscono risorse IaaS, ad esempio macchine virtuali, in una piattaforma cloud. Per l'accesso alle reti virtuali da origini esterne, come il Web, è necessario eseguire esplicitamente il provisioning. Questi tipi di reti virtuali supportano la creazione di subnet, regole di gestione, firewall virtuali e dispositivi per la gestione del traffico.

Una rete virtuale nativa del cloud non ha dipendenze dalle risorse locali o altre risorse non cloud dell'organizzazione per supportare i carichi di lavoro ospitati nel cloud. A tutte le risorse necessarie viene effettuato il provisioning nella stessa rete virtuale o tramite le offerte PaaS gestite.

## <a name="cloud-native-assumptions"></a>Presupposti nativi del cloud

Per la distribuzione di una rete virtuale nativa del cloud si presuppone quanto segue:

- I carichi di lavoro distribuiti nella rete virtuale non hanno dipendenze su applicazioni o servizi che sono accessibili solo dall'interno della rete locale. A meno che non forniscano endpoint accessibili attraverso la rete Internet pubblica, le applicazioni e i servizi ospitati internamente in locale non sono utilizzabili dalle risorse ospitate in una piattaforma cloud.
- La gestione dell'identità e il controllo di accesso e del carico di lavoro dipende dai servizi di gestione delle identità della piattaforma cloud o da server IaaS ospitati nell'ambiente cloud. Non è necessario connettersi direttamente a servizi di gestione delle identità ospitati in locale o ad altre posizioni esterne.
- Non è necessario che i servizi di gestione delle identità supportino Single Sign-On (SSO) con le directory locali.

Le reti virtuali native del cloud non hanno dipendenze esterne. Questo le rende facili da distribuire e configurare; di conseguenza questa architettura è spesso la scelta migliore per esperimenti o altre distribuzioni più piccole autosufficienti o di rapida iterazione.

I problemi aggiuntivi che i team di adozione del cloud devono prendere in considerazione quando si discute di un'architettura di rete virtuale nativa del cloud includono:

- I carichi di lavoro esistenti progettati per l'esecuzione in un data center locale possono richiedere ampie modifiche per sfruttare le funzionalità basate su cloud, come i servizi di archiviazione o di autenticazione.
- Le reti native del cloud sono gestite esclusivamente tramite gli strumenti di gestione della piattaforma cloud e pertanto possono causare divergenze di gestione e criteri rispetto agli standard IT esistenti.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulle reti virtuali native del cloud in Azure, vedere:

- [Rete virtuale di Azure: guide alle procedure](/azure/virtual-network/virtual-network-vnet-plan-design-arm). Le reti virtuali di Azure appena create sono cloud native per impostazione predefinita. Usare queste guide per facilitare la pianificazione della progettazione e la distribuzione di reti virtuali.
- [Limiti delle sottoscrizioni: Rete](/azure/azure-subscription-service-limits?toc=%2fazure%2fvirtual-network%2ftoc.json#networking-limits). Qualsiasi rete virtuale singola e le risorse connesse possono esistere soltanto all'interno di una singola sottoscrizione e operare con i limiti della stessa.
