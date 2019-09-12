---
title: 'Software Defined Networking: Reti perimetrali nel cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Questa architettura di rete consente un accesso limitato tra le reti locali e basate sul cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 6dfee69d20afac27c735f2ff77abbadc2816ca26
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828344"
---
# <a name="software-defined-networking-cloud-dmz"></a>Software Defined Networking: Reti perimetrali nel cloud

L'architettura di rete perimetrale nel cloud consente un accesso limitato fra la rete locale e quella basata sul cloud, usando una rete privata virtuale (VPN) per connettere le reti. Anche se un modello di rete perimetrale viene comunemente usato quando si vuole proteggere l'accesso esterno a una rete, l'architettura della rete perimetrale cloud descritta qui è progettata in modo specifico per proteggere l'accesso alla rete locale dalle risorse basate sul cloud e viceversa.

![Architettura di rete ibrida sicura](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/images/dmz-private.png)

Questa architettura è progettata per supportare scenari in cui l'organizzazione vuole iniziare a integrare carichi di lavoro basati sul cloud con carichi di lavoro locali, ma potrebbe non aver ancora maturato completamente i criteri di sicurezza nel cloud o acquisito una connessione WAN dedicata sicura fra i due ambienti. Di conseguenza le reti cloud devono essere trattate come una rete perimetrale per garantire la sicurezza dei servizi locali.

La rete perimetrale distribuisce appliance virtuali di rete per implementare funzionalità di sicurezza quali firewall e ispezione dei pacchetti. Il traffico che passa tra le applicazioni o i servizi locali e quelli basati sul cloud deve passare attraverso la rete perimetrale, dove può essere controllato. Le connessioni VPN e le regole che determinano il traffico consentito attraverso la rete perimetrale sono rigidamente controllate dai team di sicurezza IT.

## <a name="cloud-dmz-assumptions"></a>Presupposti relativi alle reti perimetrali nel cloud

La distribuzione di una rete perimetrale Cloud include i presupposti seguenti:

- I team di sicurezza non hanno allineato completamente i requisiti e i criteri di sicurezza locali e basati sul cloud.
- I carichi di lavoro basati sul cloud richiedono l'accesso a un subset limitato di servizi ospitati nelle reti locali o di terze parti oppure gli utenti o le applicazioni nell'ambiente locale necessitano di un accesso limitato alle risorse ospitate nel cloud.
- L'implementazione di una connessione VPN tra le reti locali e un provider di servizi cloud non è impedita da criteri aziendali, requisiti normativi o problemi di compatibilità tecnica.
- I carichi di lavoro non richiedono più sottoscrizioni per ignorare i limiti delle risorse di sottoscrizione oppure comportano più sottoscrizioni, ma non richiedono la gestione centrale della connettività o dei servizi condivisi usati dalle risorse distribuite in più sottoscrizioni.

I team di adozione del cloud devono prendere in considerazione i seguenti problemi quando si esamina l'implementazione di un'architettura di rete virtuale DMZ cloud:

- La connessione di reti locali a reti cloud aumenta la complessità dei requisiti di sicurezza. Anche se le connessioni tra le reti cloud e l'ambiente locale sono protette, è comunque necessario assicurarsi che le risorse cloud siano protette. Tutti gli indirizzi IP pubblici creati per accedere ai carichi di lavoro basati sul cloud devono essere protetti correttamente usando una rete perimetrale [pubblica](/azure/architecture/reference-architectures/dmz/secure-vnet-dmz) o un [firewall di Azure](/azure/firewall).
- L'architettura di rete perimetrale nel cloud viene generalmente usata come tappa in attesa che la connettività venga ulteriormente protetta e i criteri di sicurezza tra le reti locale e cloud vengano allineati, consentendo una più ampia adozione di un'architettura di rete ibrida completa. Tuttavia, può anche essere applicato a distribuzioni isolate con esigenze di sicurezza, identità e connettività specifiche che l'approccio alla rete perimetrale cloud soddisfa.

## <a name="learn-more"></a>Altre informazioni

Per ulteriori informazioni sull'implementazione di una rete perimetrale cloud in Azure, vedere:

- [Implementare una rete perimetrale tra Azure e il data center locale](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid). Questo articolo illustra come implementare un'architettura di rete ibrida sicura in Azure.
