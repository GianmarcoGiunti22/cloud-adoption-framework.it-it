---
title: 'Software Defined Networking: Rete ibrida'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descrizione del modo in cui le reti ibride consentono alle reti virtuali cloud di connettersi alle risorse locali.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 94e285f59442b6632209e1cd6a76c39cfccd337b
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829488"
---
# <a name="software-defined-networking-hybrid-network"></a>Software Defined Networking: Rete ibrida

L'architettura di rete del cloud ibrido consente alle reti virtuali di accedere a risorse locali e servizi e vice versa usando una connessione WAN dedicata, ad esempio ExpressRoute o un altro metodo di connessione per connettersi direttamente alle reti.

![Rete ibrida](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/images/expressroute.png)

Basandosi sull'architettura di rete virtuale nativa del cloud, una rete virtuale ibrida è isolata all'inizio della creazione. L'aggiunta della connettività all'ambiente locale concede l'accesso da e verso la rete locale, anche se è necessario consentire in modo esplicito tutte le altre risorse di destinazione di traffico in ingresso nella rete virtuale. È possibile proteggere la connessione tramite i dispositivi virtuali firewall e le regole di gestione per limitare l'accesso oppure specificare esattamente quali servizi possono essere accessibili tra le due reti, usando le funzionalità di routing nativo del cloud o la distribuzione di appliance virtuali di rete (NVA) per la gestione del traffico.

Sebbene l'architettura di rete ibrida supporti le connessioni VPN, è preferibile disporre di connessioni WAN dedicate come ExpressRoute a causa di prestazioni migliori e maggiore sicurezza.

## <a name="hybrid-assumptions"></a>Presupposti della connessione ibrida

La distribuzione di una rete virtuale ibrida include i presupposti seguenti:

- I team della sicurezza IT si sono allineati ai criteri di sicurezza di rete locale e basata su cloud, per garantire che le reti virtuali basate su cloud possano essere considerate attendibili per comunicare direttamente con i sistemi locali.
- I carichi di lavoro basati su cloud richiedono l'accesso alle risorse di archiviazione, alle applicazioni e ai servizi ospitati sulle reti locali o di terze parti, oppure agli utenti e alle applicazioni in locale che devono accedere alle risorse ospitate nel cloud.
- È necessario eseguire la migrazione delle applicazioni e dei servizi esistenti che dipendono da risorse locali, ma non si vogliono impiegare le risorse in un nuovo sviluppo per rimuovere tali dipendenze.
- La connessione delle reti locali a risorse cloud tramite VPN o WAN dedicata non è impedita dai criteri aziendali, dai requisiti di sovranità dei dati o da altri problemi di conformità alle normative.
- I carichi di lavoro non richiedono più sottoscrizioni per ignorare i limiti delle risorse di sottoscrizione o i carichi di lavoro coinvolgono più sottoscrizioni, ma non richiedono la gestione centralizzata della connettività o dei servizi condivisi usati dalle risorse distribuite tra più sottoscrizioni.

I team di adozione del cloud devono prendere in considerazione i seguenti problemi quando si esamina l'implementazione di un'architettura di rete virtuale ibrida:

- La connessione di reti locali a reti cloud aumenta la complessità dei requisiti di sicurezza. Entrambe le reti devono essere protette da vulnerabilità esterne e da accessi non autorizzati da entrambi i lati dell'ambiente ibrido.
- Il ridimensionamento del numero e delle dimensioni di carichi di lavoro all'interno di un ambiente cloud ibrido può implicare una complessità significativa nella gestione di routing e traffico.
- Sarà necessario sviluppare criteri di controllo di accesso e di gestione compatibili per mantenere la governance coerente in tutta l'organizzazione.

## <a name="learn-more"></a>Altre informazioni

Per ulteriori informazioni sulle reti ibride in Azure, vedere:

- [Architetture di riferimento della rete ibrida di Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/expressroute). Le reti virtuali ibride di Azure usano un circuito ExpressRoute o una VPN di Azure per connettere la rete virtuale con le risorse IT esistenti dell'organizzazione non ospitate in Azure. Questo articolo illustra le opzioni per la creazione di una rete ibrida in Azure.
