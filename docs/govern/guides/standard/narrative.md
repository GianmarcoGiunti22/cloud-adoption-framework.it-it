---
title: 'Guida alla governance aziendale standard: descrizione alla base della strategia di governance'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Questa descrizione stabilisce un caso d'uso per la governance durante un percorso di adozione cloud aziendale standard.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8bf9b65c71defd57c319f46a83b5d4540967b012
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547432"
---
# <a name="standard-enterprise-governance-guide-the-narrative-behind-the-governance-strategy"></a>Guida alla governance aziendale standard: descrizione alla base della strategia di governance

La descrizione seguente descrive il caso d'uso per la governance durante un [percorso di adozione del cloud aziendale standard](./index.md). Prima di implementare il percorso, è importante comprendere i presupposti e la logica che si riflettono in questa descrizione. Sarà quindi possibile allineare più facilmente la strategia di governance al percorso specifico per la propria organizzazione.

## <a name="back-story"></a>Scenario

Il consiglio di amministrazione ha avviato l'anno con piani per dare nuova energia alle attività aziendali in diversi modi, invitando la dirigenza a migliorare le esperienze dei clienti per conquistare nuove quote di mercato. Il consiglio spinge anche verso la realizzazione di nuovi prodotti e servizi per garantire all'azienda una posizione leader riconosciuta nel settore. Sono state anche avviate iniziative parallele per ridurre gli sprechi e tagliare i costi non necessari. Anche se possono intimorire, le azioni del consiglio di amministrazione e della dirigenza dimostrano che gli investimenti sono incentrati al massimo sulla crescita futura.

In passato, CIO aziendale è stato escluso da queste conversazioni strategiche. Tuttavia, dato che la visione futura è intrinsecamente collegata allo sviluppo tecnico, il reparto IT partecipa alla discussione per contribuire alla definizione di questi piani di notevole portata. Ci si aspetta ora che il reparto IT contribuisca in modi nuovi. Il team non è preparato per queste modifiche ed è probabile che abbia difficoltà con la curva di apprendimento.

## <a name="business-characteristics"></a>Caratteristiche dell'azienda

Il profilo di business della società è il seguente:

- Tutte le attività di vendita e operative sono concentrate in un singolo paese, con una bassa percentuale di clienti globali.
- L'azienda opera come una singola business unit, con budget allineato alle funzioni, tra cui Vendite, Marketing, Operazioni e IT.
- Per l'azienda, la maggior parte delle attività IT è considerata come un deflusso di capitali o un centro di costo.

## <a name="current-state"></a>Stato corrente

Questo è lo stato corrente delle attività IT e cloud della società:

- Il reparto IT gestisce operativamente due ambienti di infrastruttura ospitati. Un ambiente contiene gli asset di produzione. Il secondo ambiente contiene gli asset per il ripristino di emergenza e alcuni asset per sviluppo e test. Questi ambienti sono ospitati da due diversi provider. Il reparto IT fa riferimento a questi due data center rispettivamente come Prod e DR.
- L'accesso al cloud è avvenuto tramite la migrazione di tutti gli account di posta elettronica degli utenti finali a Office 365. Questa migrazione è stata completata sei mesi fa. Pochi altri asset IT sono stati distribuiti nel cloud.
- I team di sviluppo di applicazioni lavorano in una capacità di sviluppo/test per ottenere informazioni sulle funzionalità native del cloud.
- Il team di business intelligence (BI) sta sperimentando implementazioni di Big Data nel cloud e la gestione dei dati in nuove piattaforme.
- La società ha un criterio definito in modo generico che informa che i dati personali dei clienti e i dati finanziari non possono essere ospitati nel cloud, che limita le applicazioni cruciali nelle distribuzioni correnti.
- Gli investimenti IT sono controllati in gran parte dalle spese di capitale. e sono pianificati di anno in anno. Nel corso degli ultimi anni, gli investimenti sono stati limitati a poco più dei requisiti di manutenzione di base.

## <a name="future-state"></a>Stato futuro

Sono previste le modifiche seguenti per gli anni successivi:

- Il CIO sta esaminando i criteri sui dati personali e sui dati finanziari per consentire gli obiettivi di stato futuri.
- I team di sviluppo delle applicazioni e di business intelligence intendono rilasciare soluzioni basate sul cloud in produzione nel corso dei 24 mesi successivi, in linea con la visione aziendale per l'engagement dei clienti e i nuovi prodotti.
- Nel corso dell'anno, il team IT terminerà il ritiro dei carichi di lavoro di ripristino di emergenza del data center DR con la migrazione di 2.000 macchine virtuali nel cloud. È previsto che questa misura consenta risparmi sui costi stimati per 25 milioni di dollari USA nel corso dei prossimi cinque anni.
    costi ![On locali rispetto ai costi di Azure che dimostrano un ritorno di $25M USD nei prossimi cinque anni ](../../../_images/govern/calculator-small-to-medium-enterprise.png)
- La società intende modificare il modo in cui rende gli investimenti IT riposizionando le spese di capitale vincolate come una spesa operativa al suo interno. Questa modifica consentirà un maggiore controllo dei costi e permetterà al reparto IT di accelerare altri progetti pianificati.

## <a name="next-steps"></a>Passaggi successivi

La società ha elaborato criteri aziendali per strutturare l'implementazione della governance. Tali criteri aziendali guidano molte delle decisioni tecniche.

> [!div class="nextstepaction"]
> [Esaminare i criteri aziendali iniziali](./initial-corporate-policy.md)
