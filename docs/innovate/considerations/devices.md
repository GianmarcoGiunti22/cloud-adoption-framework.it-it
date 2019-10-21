---
title: 'Innovazione nel cloud: interagire con i dispositivi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione nel cloud-interagire con i dispositivi
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/24/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 8c170b543344394396660ee299589a94365cff8f
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557726"
---
# <a name="ambient-experiences-interact-with-devices"></a>Esperienze di ambiente: interagire con i dispositivi

Nell'ambito della [creazione con empatia](./build.md), abbiamo discusso i tre test di vera innovazione: risolvere le esigenze dei clienti, far tornare il cliente, ridimensionare in base alle coorti dei clienti. Ogni test dell'ipotesi richiederà sforzi e iterazioni sull'approccio all'adozione. In questo articolo vengono fornite informazioni dettagliate su alcuni approcci avanzati per ridurre tale impegno attraverso **esperienze ambientali**. Interagendo con i dispositivi, anziché un'applicazione, è più probabile che il cliente torni alla soluzione prima di soddisfare le proprie esigenze.

## <a name="ambient-experiences"></a>Esperienze di ambiente

Un'esperienza di ambiente è un'esperienza digitale che si riferisce all'ambiente immediato. Una soluzione che offre esperienze di ambiente si impegna a soddisfare il cliente nel momento in cui è necessario. Quando possibile, la soluzione soddisfa le esigenze del cliente senza uscire dal flusso naturale delle attività svolte.

La vita nell'economia digitale è piena di distrazioni. Siamo tutti colpiti da messaggi di posta elettronica, Web, visivi e verbali, ciascuno dei quali è un rischio di distrazione. Il rischio di distrazione aumenta con ogni secondo tra il punto di necessità del cliente e un'interazione con la soluzione. Innumerevoli clienti si perdono nel breve intervallo di tempo. Per promuovere gli aumenti nell'adozione ripetuta, ridurre il numero di distrazioni riducendo il tempo per la soluzione (TTS).

## <a name="interacting-with-devices"></a>Interazione con i dispositivi

Un'esperienza Web standard è la tecnica di sviluppo delle applicazioni più comune utilizzata per soddisfare le esigenze del cliente. Il presupposto di questo approccio è che il cliente si troverà davanti al computer. Se il cliente soddisfa in modo coerente il proprio punto di necessità quando si è davanti al computer portatile, creare un'app Web. Questa app Web fornirà un'"esperienza di ambiente" per il cliente, in questo scenario. Tuttavia, sappiamo che questo scenario è sempre meno probabile nella società moderna.

![Esperienze di ambiente](../../_images/innovate/ambient-experiences.png)

Le esperienze di ambiente, come illustrato in precedenza, richiedono in genere più di un'app Web. Grazie alla [misurazione](./measure.md) e all' [apprendimento con il cliente](./learn.md) , il comportamento che conduce al trigger di richiesta del cliente può essere osservato, rilevato e utilizzato per creare un'esperienza più ambientale. Di seguito sono riepilogati alcuni approcci per l'integrazione delle soluzioni di ambiente nelle proprie ipotesi, più dettagli su ognuno nei paragrafi seguenti.

- **[Esperienza mobile](#mobile-experience)** : molto simile a un portatile, le app per dispositivi mobili fanno in genere parte dell'ambiente dei clienti. In alcuni scenari, questo può fornire un livello sufficiente di interattività per rendere un ambiente della soluzione.
- **[Realtà mista](#mixed-reality):** Talvolta è necessario modificare l'ambiente naturale di un cliente per creare un ambiente di interazione. In questo modo si crea un po' di una falsa realtà in cui il cliente può interagire con la soluzione e avere una necessità soddisfatta. In questo caso, la soluzione è di ambiente all'interno della realtà falsa.
- **[Realtà integrata](#integrated-reality):** Avvicinandosi al vero ambiente, le soluzioni di realtà integrate si concentrano sull'uso di un dispositivo presente nella realtà del cliente per integrare la soluzione in comportamenti naturali. Un assistente virtuale è un ottimo esempio di integrazione della realtà nell'ambiente circostante. Un'opzione meno nota è quella di usare le tecnologie Internet delle cose (Internet delle cose) per integrare i dispositivi già esistenti negli ambienti del cliente.
- **[Realtà regolata](#adjusted-reality):** Quando una delle soluzioni di ambiente precedenti usa l'analisi predittiva nel cloud per definire e fornire un'interazione con il cliente attraverso l'ambiente naturale, la soluzione ha regolato la realtà.

Comprendere le esigenze dei clienti e misurare l'effetto del cliente contribuirà a determinare se sarà necessaria un'interazione del dispositivo o un'esperienza di ambiente per convalidare l'ipotesi. Con ognuno di questi punti dati, le sezioni seguenti aiuteranno a trovare la soluzione migliore.

## <a name="mobile-experience"></a>Esperienza per dispositivi mobili

La prima fase dell'esperienza ambientale consiste nell'allontanarsi dal computer. I clienti attuali e i professionisti aziendali si spostano fluidamente tra dispositivi mobili e PC. Ogni piattaforma o dispositivo usato dal cliente crea una nuova esperienza potenziale per il cliente. L'aggiunta di un'esperienza mobile che estende la soluzione principale è il modo più rapido per migliorare l'integrazione nelle immediate vicinanze del cliente. Mentre un dispositivo mobile è lontano dall'ambiente, potrebbe essere più vicino al punto di necessità del cliente.

Quando i clienti sono dispositivi mobili e cambiano di frequente, questo può essere il formato più pertinente per l'esperienza di ambiente per una determinata soluzione. Una fonte comune di innovazione nell'ultimo decennio è stata l'espansione delle soluzioni esistenti per l'integrazione di un'esperienza per dispositivi mobili.

Esempi di questo approccio sono disponibili in app Azure Services. Durante le prime iterazioni, la [funzionalità app Web di app Azure servizio](/azure/app-service/overview) può essere usata per testare l'ipotesi. Poiché le ipotesi diventano più complesse, la [funzionalità app per dispositivi mobili di app Azure Services](/azure/app-service-mobile/) può estendere l'app Web per l'esecuzione in un'ampia gamma di piattaforme per dispositivi mobili.

## <a name="mixed-reality"></a>Realtà mista

Il livello successivo di maturità per le esperienze ambientali è l'aumento o la replica degli ambienti del cliente attraverso soluzioni di realtà mista. In questo approccio, la soluzione diventa più ambiente creando un'estensione della realtà per il funzionamento del cliente all'interno di.

> [!IMPORTANT]
> Se è necessario un dispositivo di realtà virtuale (VR) e *non fa già parte dei comportamenti immediati o naturali*, la realtà aumentata/virtuale è più un'esperienza alternativa e meno un'esperienza di ambiente.

Questa forma di esperienza è sempre più comune per i dipendenti remoti. L'uso di queste esperienze è sempre più veloce in settori che richiedono collaborazione o competenze speciali che non sono immediatamente disponibili nel mercato locale. Uno scenario comune che richiede la realtà aumentata come parte di un comportamento naturale è il supporto centralizzato per l'implementazione di un prodotto complesso per una forza lavoro remota. In questi scenari, il team di supporto centrale e il dipendente remoto possono sfruttare la realtà aumentata per risolvere i problemi o installare il prodotto.

Per lo scenario precedente o altri scenari simili, un esempio di esperienza di ambiente è l'uso di ancoraggi spaziali. Gli ancoraggi spaziali consentono di creare esperienze di realtà miste con oggetti che rendono permanente la loro posizione tra i dispositivi nel tempo. Tramite gli ancoraggi spaziali, un comportamento specifico può essere acquisito, registrato e reso permanente in modo da garantire un'esperienza di ambiente, la volta successiva che l'utente sta operando all'interno di quell'ambiente potenziato. Gli [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview) sono un servizio che sposta questa logica nel cloud, consentendo l'esperienza di condivisione tra dispositivi e anche tra soluzioni.

## <a name="integrated-reality"></a>Realtà integrata

Al di là della realtà mobile o anche della realtà mista è l'uso della realtà integrata. Con questo approccio, l'obiettivo è rimuovere completamente l'esperienza digitale. Ci sono dispositivi con funzionalità di calcolo e connettività. Questi dispositivi possono essere usati per raccogliere i dati dalle immediate vicinanze senza che il cliente debba mai toccare un telefono, un portatile o un dispositivo VR.

Questa forma di esperienza è ideale quando una forma di dispositivo è coerente negli stessi ambienti in cui si verifica la necessità del cliente. Gli scenari comuni includono pavimenti, ascensori o persino la tua auto. Questi tipi di dispositivi di grandi dimensioni contengono già la potenza di calcolo. È anche possibile usare i dati del dispositivo stesso per rilevare i comportamenti dei clienti e inviare tali comportamenti nel cloud. Questa acquisizione automatica dei dati sul comportamento dei clienti riduce drasticamente la necessità di un cliente di immettere i dati. Inoltre, l'esperienza Web, per dispositivi mobili o VR può essere usata come ciclo di feedback per condividere ciò che è stato appreso dalla soluzione di realtà integrata.

Esempi di realtà integrata in Azure possono includere:

- [Soluzioni azure Internet delle cose (Internet)](https://docs.microsoft.com/azure/iot-fundamentals), una raccolta di servizi in Azure, che consentono di gestire i dispositivi e il flusso di dati da tali dispositivi nel cloud ed eseguire il back-up agli utenti finali.
- [Azure Sphere](/azure-sphere), una combinazione di hardware e software, Azure Sphere è un modo sicuro per consentire a un dispositivo esistente di trasmettere in modo sicuro i dati tra il dispositivo e le soluzioni di Azure.
- [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk), sensori di intelligenza artificiale con modelli avanzati di visione artificiale e riconoscimento vocale, che possono raccogliere dati visivi e audio da un ambiente immediato e inserire tali input nella soluzione.

Tutti e tre possono essere utilizzati per raccogliere i dati all'interno dell'ambiente naturale, al momento della necessità del cliente. A questo punto, la soluzione può rispondere a tali input di dati per risolvere la necessità, a volte prima che il cliente sappia anche che si è verificato un trigger per la necessità.

## <a name="adjusted-reality"></a>Realtà regolata

La forma più elevata dell'esperienza ambiente è la realtà adattata, spesso definita Intelligence di ambiente. La realtà adattata è un approccio all'uso delle informazioni della soluzione per modificare la realtà del cliente, senza la necessità di interagire direttamente con un'applicazione. Con questo approccio, l'applicazione creata inizialmente per dimostrare l'ipotesi potrebbe non essere più pertinente. Al contrario, i dispositivi nell'ambiente faciliterebbe gli input e gli output per soddisfare le esigenze dei clienti.

Assistenti virtuali e Smart Speaker possono fornire un ottimo esempio di realtà adattata. Da solo, uno smart Speaker è un esempio di realtà integrata semplice. È possibile aggiungere una Smart Light e un senso di movimento a una soluzione di relatore intelligente ed è facile creare una soluzione di base con accende le luci quando si immette una chat room.

Le fabbriche in tutto il mondo forniscono altri scenari di realtà adattate. Durante le fasi iniziali della realtà integrata, i sensori sui dispositivi rilevavano le condizioni, ad esempio il surriscaldamento, e segnalavano la necessità di una modifica a un uomo attraverso un'applicazione. In realtà adattata, il cliente potrebbe essere ancora impegnato. Il ciclo di commenti è tuttavia più rigoroso. In una fabbrica di realtà regolata, un dispositivo rileverebbe il surriscaldamento in un computer vitale in un punto qualsiasi all'interno della linea di assembly. Altrove, un secondo dispositivo rallenta leggermente la produzione per consentire al computer di raffreddarsi e riprendere la velocità quando la condizione è stata risolta. In questo scenario, il cliente è una seconda parte. Il cliente usa l'applicazione per impostare le regole e comprendere il modo in cui tali regole hanno influenzato la produzione, ma non è una parte obbligatoria del ciclo di feedback.

I servizi di Azure nella sezione precedente, le [soluzioni azure Internet delle cose](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](/azure-sphere)e il kit per [sviluppatori di Azure Kinect](https://docs.microsoft.com/azure/Kinect-dk) possono essere componenti di una soluzione di realtà adattata. La logica di business e l'applicazione originale fungerebbe da intermediario tra l'input ambientale e la modifica da apportare all'ambiente fisico.

Un altro esempio di realtà regolata è la creazione di un dispositivo gemello digitale, ovvero una rappresentazione digitale di un dispositivo fisico, presentato tramite computer, dispositivi mobili o formati di realtà mista. A differenza dei modelli 3D meno sofisticati, un dispositivo gemello digitale riflette i dati raccolti da un dispositivo reale nell'ambiente fisico. Ciò consente all'utente di interagire con la rappresentazione digitale in modi che non possono mai essere eseguiti nel mondo reale. In questo approccio i dispositivi fisici regolano un ambiente di realtà mista. Tuttavia, la soluzione sta ancora raccogliendo i dati da una soluzione di realtà integrata e usando tale soluzione per definire la realtà degli ambienti attuali del cliente.

In Azure i dispositivi gemelli digitali vengono creati e accessibili tramite un servizio denominato dispositivi [gemelli digitali di Azure](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza più approfondita delle interazioni dei dispositivi e dell'esperienza di ambiente più adatta alla soluzione, si è ora pronti per esplorare la disciplina finale dell'innovazione, la [stima e l'influenza](./predict.md).

> [!div class="nextstepaction"]
> [Stimare e influenzare](./predict.md)
