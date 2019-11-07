---
title: Guida alle decisioni per le reti definite dal software
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle reti definite dal software come servizio di base nelle migrazioni Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 46d01d6685b4cac55db7ed313b70891b4f9c029f
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564778"
---
# <a name="software-defined-networking-decision-guide"></a>Guida alle decisioni per le reti definite dal software

La rete definita dal software (SDN, Software Defined Networking) è un'architettura di rete progettata per consentire funzionalità di rete virtualizzata che possono essere gestite, configurate e modificate in modo centralizzato tramite software. Le reti definite dal software consentono di creare reti basate sul cloud usando gli equivalenti virtualizzati di router fisici, firewall e altri dispositivi di rete usati nelle reti locali. Una rete definita dal software è fondamentale per la creazione di reti virtuali protette in piattaforme cloud pubbliche come Azure.

## <a name="networking-decision-guide"></a>Guida decisionale di rete

![Grafico delle opzioni di rete dalla meno alla più complessa, allineato con i collegamenti sotto](../../_images/decision-guides/decision-guide-software-defined-network.png)

Passare a: [Solo PaaS](./paas-only.md) | [Reti cloud native](./cloud-native.md) | [Reti perimetrali nel cloud](./cloud-dmz.md) [Ambiente ibrido](./hybrid.md) | [Modello hub-spoke](./hub-spoke.md) | [Altre informazioni](#learn-more)

LSDN offre diverse opzioni con vari livelli di prezzo e complessità. La guida di individuazione sopra riportata rappresenta un riferimento per personalizzare rapidamente queste opzioni per allinearsi al meglio con le specifiche strategie aziendali e tecnologiche.

Il punto critico in questa guida dipende da diverse decisioni chiave prese dal team di strategia del cloud prima di prenderne altre sull'architettura di rete. Le più importanti tra queste sono le decisioni riguardanti la [definizione del digital estate](../../digital-estate/index.md) e la [progettazione delle sottoscrizioni](../subscriptions/index.md) (per cui possono essere necessari anche input da decisioni prese correlate all'accounting del cloud e alle strategie dei mercati globali).

Le distribuzioni in aree singole con piccole dimensioni di meno di 1.000 macchine virtuali hanno meno probabilità di essere influenzate in modo significativo da questo punto di flesso. Al contrario, il grande lavoro di adozione richiesto con più di 1.000 macchine virtuali, più business unit o più mercati geo-politici può essere influenzato notevolmente dalla scelta della SDN e da questo punto di flesso cruciale.

## <a name="choose-the-right-virtual-networking-architectures"></a>Scegliere le architetture di rete virtuale appropriate

Questa sezione sviluppa la guida decisionale per aiutare a scegliere le architetture di rete virtuale appropriate.

Esistono diversi modi per implementare le tecnologie SDN per creare reti virtuali basate su cloud. Il modo in cui le reti virtuali usate nella migrazione si strutturano e interagiscono con l'infrastruttura IT esistente dipende da una combinazione dei requisiti del carico di lavoro e della governance.

Quando si pianifica quale architettura di rete virtuale o combinazione di architetture considerare durante la pianificazione della migrazione cloud, bisogna considerare le domande seguenti per determinare quale sia quella più appropriata per l'azienda:

| Domanda | solo PaaS | Gestione nativa del cloud | Reti perimetrali nel cloud | Ibrido | Hub e spoke |
|-----|-----|-----|-----|-----|-----|
| Il carico di lavoro usa solo i servizi PaaS e non richiede funzionalità di rete oltre a quelle fornite dagli stessi servizi? | Sì | No | No | No | No |
| Il carico di lavoro richiede l'integrazione con applicazioni locali? | No | No | Sì | Sì | Sì |
| Sono stati stabiliti criteri di sicurezza avanzati e connettività sicura tra le reti locali e cloud? | No | No | No | Sì | Sì |
| Il carico di lavoro richiede servizi di autenticazione non supportati tramite i servizi di identità cloud oppure serve un accesso diretto ai controller di dominio locali? | No | No | No | Sì | Sì |
| È necessario distribuire e gestire un numero elevato di macchine virtuali e di carichi di lavoro? | No | No | No | No | Sì |
| È necessario fornire gestione centralizzata e connettività locale in fase di delega controllo sulle risorse ai singoli team del carico di lavoro? | No | No | No | No | Sì |

## <a name="virtual-networking-architectures"></a>Architetture di rete virtuale

Altre informazioni sulle architetture di rete primarie definite dal software:

- **[Solo PaaS](./paas-only.md):** la maggior parte dei prodotti PaaS (piattaforma distribuita come servizio) supporta un set limitato di funzionalità di rete predefinite e può non essere necessaria una rete definita dal software definita in modo esplicito per supportare i requisiti del carico di lavoro.
- **[Nativa del cloud](./cloud-native.md):** un'architettura cloud nativa supporta i carichi di lavoro basati sul cloud tramite reti virtuali realizzate sulla base delle funzionalità di rete definita dal software predefinite della piattaforma cloud, senza dipendenze da risorse locali o altre risorse esterne.
- **[Reti perimetrali nel cloud](./cloud-dmz.md):** supportano connettività limitata tra la rete locale e quella cloud protetta tramite l'implementazione di una zona demilitarizzata con stretto controllo del traffico tra i due ambienti.
- **[Ibrido](./hybrid.md)** : l'architettura di rete del cloud ibrida consente alle reti virtuali in ambienti cloud attendibili di accedere alle risorse in locale e viceversa.
- **[Hub-spoke](./hub-spoke.md):** l'architettura hub-spoke consente di gestire la connettività esterna e i servizi condivisi, di isolare singoli carichi di lavoro e di superare i limiti potenziali della sottoscrizione in modo centralizzato.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni sulle reti definite dal software in Azure, vedere:

- [Rete virtuale di Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). In Azure la funzionalità chiave di SDN viene fornita dalla rete virtuale di Azure che agisce come un cloud analogo alle reti locali fisiche. Le reti virtuali fungono anche da limite di isolamento predefinito tra le risorse della piattaforma.
- [Procedure consigliate di Azure per la sicurezza di rete](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices). Indicazioni del team di sicurezza di Azure su come configurare le reti virtuali per ridurre al minimo le vulnerabilità di sicurezza.

## <a name="next-steps"></a>Passaggi successivi

Le reti definite dal software sono solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
