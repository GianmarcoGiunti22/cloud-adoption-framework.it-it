---
title: Valutare e ridimensionare gli asset nel cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Valutare e ridimensionare gli asset nel cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 13a18db6a074f73b962d29f4d5963571a49869d4
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022656"
---
# <a name="benchmark-and-resize-cloud-assets"></a>Valutare e ridimensionare gli asset nel cloud

Il monitoraggio dell'utilizzo e dei costi ha un'importanza critica per le infrastrutture cloud. Le organizzazioni pagano per le risorse che utilizzano nel corso del tempo. Quando l'utilizzo supera le soglie di contratto, possono essere registrate rapidamente eccedenze dei costi impreviste. I report di Gestione costi consentono di monitorare le spese in modo da analizzare e tenere traccia dell'utilizzo del cloud, dei costi e dell'andamento. Tramite l'uso di report relativi a un determinato periodo di tempo, è possibile rilevare le anomalie che differiscono dall'andamento normale. Le inefficienze nella distribuzione del cloud sono visibili nei report sull'ottimizzazione. È possibile notare inefficienze nei report di analisi dei costi.

Nei tradizionali modelli locali del settore IT, la richiesta di sistemi IT è costosa e richiede molto tempo. I processi spesso comportano lunghi cicli di revisione della spesa di capitale e possono addirittura richiedere un processo di pianificazione annuale. È quindi prassi comune acquistare più asset del necessario. È altrettanto frequente che gli amministratori IT eseguano l'overprovisioning degli asset in previsione di possibili richieste future.

Nel cloud, i modelli di accounting e provisioning consentono di eliminare i ritardi che determinano l'acquisto di asset in eccesso. Quando un asset necessita di risorse aggiuntive, può essere ridimensionato in modo quasi immediato. Ciò significa che le dimensioni degli asset possono essere ridotte in modo sicuro per limitare al minimo i costi e l'utilizzo di risorse. Durante le fasi di valutazione e l'ottimizzazione, il team di adozione del cloud cerca di trovare il giusto equilibrio tra prestazioni e costi, effettuando il provisioning degli asset in modo che non siano più grandi o più piccoli del necessario per soddisfare le esigenze di produzione.

<!-- markdownlint-disable MD026 -->

## <a name="should-assets-be-optimized-during-or-after-the-migration"></a>Gli asset devono essere ottimizzati durante o dopo la migrazione?

Quando è necessario ottimizzare un asset? Durante o dopo la migrazione? La risposta semplice è *in entrambi i casi*, ma non è del tutto esatta. Per una spiegazione, è possibile esaminare due scenari di base per ottimizzare il ridimensionamento delle risorse:

- **Ridimensionamento pianificato.** Spesso un asset è chiaramente sovradimensionato e sottoutilizzato e deve essere ridimensionato durante la distribuzione. Per determinare se un asset è stato ridimensionato in modo corretto, in questo caso è necessario eseguire test di accettabilità da parte degli utenti dopo la migrazione. Se un utente esperto non riscontra perdite di prestazioni o di funzionalità durante i test, è possibile dedurre che l'asset è stato ridimensionato in modo corretto.
- **Ottimizzazione.** Nei casi in cui la necessità di ottimizzazione non è evidente, i team IT devono usare un approccio basato sui dati per gestire le dimensioni delle risorse. Usando i benchmark delle prestazioni dell'asset, un team IT può prendere decisioni consapevoli sulle dimensioni, la portata, l'architettura e i servizi più adatti a una soluzione. Può quindi ridimensionare e testare le teorie delle prestazioni dopo la migrazione.

Durante la migrazione, formulare ipotesi ragionate e sperimentare varie soluzioni di ridimensionamento. Per una vera ottimizzazione delle risorse, tuttavia, sono necessari dati basati sulle prestazioni effettive in un ambiente cloud. A tale scopo, il team IT deve prima implementare approcci per il monitoraggio delle prestazioni e dell'utilizzo di risorse.

## <a name="benchmark-and-optimize-with-azure-cost-management"></a>Valutare e ottimizzare con Gestione costi di Azure

Il servizio [Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/overview), concesso in licenza da Cloudyn, una società affiliata di Microsoft, consente di gestire la spesa per il cloud in modo preciso e trasparente. Questo servizio esegue il monitoraggio, la valutazione, l'allocazione e l'ottimizzazione dei costi del cloud.

I dati cronologici possono aiutare a gestire i costi analizzando l'utilizzo e i costi nel tempo in modo da identificare le tendenze, che vengono quindi usate per prevedere la spesa futura. La gestione dei costi comprende anche utili report sui costi previsti. L'allocazione dei costi consente di gestire i costi analizzandoli in base a criteri di assegnazione di tag. L'allocazione dei costi può essere usata per lo showback/chargeback in modo da visualizzare l'uso delle risorse e i costi associati allo scopo di influenzare i comportamenti di consumo o addebitare i costi ai clienti tenant. Il controllo di accesso consente di gestire i costi assicurando che gli utenti e i team accedano unicamente ai dati di Gestione costi necessari. Gli avvisi consentono di gestire i costi tramite l'invio di una notifica automatica nel caso di spese insolite o eccessive. Gli avvisi possono inviare una notifica automaticamente anche ad altre parti interessate per le anomalie di spesa e i rischi di spesa eccessiva. Vari report supportano gli avvisi basati su soglie di budget e di costi.

## <a name="improve-efficiency"></a>Migliorare l'efficienza

Con Gestione costi è possibile determinare l'uso ottimale delle macchine virtuali e identificare le macchine virtuali inattive o rimuovere tali macchine virtuali e i dischi non collegati. Usando le informazioni contenute nei report sull'ottimizzazione e sull'inefficienza del ridimensionamento, è possibile creare un piano per ridimensionare o rimuovere le macchine virtuali inattive.

## <a name="next-steps"></a>Passaggi successivi

Dopo il test e l'ottimizzazione di un carico di lavoro, è il momento di [preparare il carico di lavoro per la promozione](./ready.md).

> [!div class="nextstepaction"]
> [Preparazione di un carico di lavoro per la promozione in produzione](./ready.md)
