---
title: 'Innovazione nel cloud: interagire con i dispositivi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione nel cloud-interagire con i dispositivi
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 4a1b96a5f29ebac9fd228ab1603d12e08b38ba63
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752078"
---
# <a name="ambient-experiences-interact-with-devices"></a>Esperienze di ambiente: interagire con i dispositivi

In [Build con l'empatia del cliente](./build.md)abbiamo discusso i tre test di vera innovazione: risolvere le esigenze dei clienti, far tornare il cliente e ridimensionare le coorti dei clienti. Ogni test dell'ipotesi richiede sforzi e iterazioni sull'approccio all'adozione. In questo articolo vengono fornite informazioni dettagliate su alcuni approcci avanzati per ridurre tale impegno attraverso *esperienze ambientali*. Interagendo con i dispositivi, anziché un'applicazione, è probabile che il cliente ritorni prima alla soluzione.

## <a name="ambient-experiences"></a>Esperienze di ambiente

Un'esperienza di ambiente è un'esperienza digitale che si riferisce all'ambiente immediato. Una soluzione che offre esperienze di ambiente si impegna a soddisfare il cliente nel momento in cui è necessario. Quando possibile, la soluzione soddisfa la necessità del cliente senza uscire dal flusso di attività che lo ha attivato.

La vita nell'economia digitale è piena di distrazioni. Siamo tutti colpiti da messaggi di posta elettronica, Web, visivi e verbali, ciascuno dei quali è un rischio di distrazione. Questo rischio aumenta con ogni secondo che trascorre tra il punto di bisogno del cliente e il momento in cui si verifica una soluzione. Innumerevoli clienti si perdono nel breve intervallo di tempo. Per favorire un aumento dell'adozione della ripetizione, è necessario ridurre il numero di distrazioni riducendo il tempo per la soluzione (TTS).

## <a name="interacting-with-devices"></a>Interazione con i dispositivi

Un'esperienza Web standard è la tecnica di sviluppo delle applicazioni più comune utilizzata per soddisfare le esigenze del cliente. Questo approccio presuppone che il cliente si trovi davanti al computer. Se il cliente soddisfa in modo coerente il proprio punto di necessità quando si è davanti al computer portatile, creare un'app Web. Tale app Web fornirà un'esperienza di ambiente per il cliente in questo scenario. Tuttavia, sappiamo che questo scenario è meno e meno probabile nell'era corrente.

![Esperienze di ambiente](../../_images/innovate/ambient-experiences.png)

Le esperienze di ambiente in genere richiedono più di un'app Web in questi giorni. Attraverso la [misurazione](./measure.md) e l' [apprendimento con il cliente](./learn.md) , il comportamento che attiva la necessità del cliente può essere osservato, rilevato e utilizzato per creare un'esperienza più ambientale. Nell'elenco seguente sono riepilogati alcuni approcci per l'integrazione delle soluzioni di ambiente nelle proprie ipotesi, con ulteriori dettagli su ognuno dei paragrafi seguenti.

- **[Esperienza mobile](#mobile-experience):** Come per i portatili, le app per dispositivi mobili sono onnipresenti negli ambienti dei clienti. In alcune situazioni, questo potrebbe fornire un livello sufficiente di interattività per rendere un ambiente della soluzione.
- **[Realtà mista](#mixed-reality):** Talvolta è necessario modificare gli ambienti tipici di un cliente per creare un ambiente di interazione. Questo fattore crea qualcosa di una falsa realtà in cui il cliente interagisce con la soluzione e ha una necessità soddisfatta. In questo caso, la soluzione è di ambiente all'interno della realtà falsa.
- **[Realtà integrata](#integrated-reality):** Avvicinandosi al vero ambiente, le soluzioni di realtà integrate si concentrano sull'uso di un dispositivo presente nella realtà del cliente per integrare la soluzione nei loro comportamenti naturali. Un assistente virtuale è un ottimo esempio di integrazione della realtà nell'ambiente circostante. Un'opzione meno nota riguarda Internet delle cose tecnologie, che integrano i dispositivi già esistenti negli ambienti del cliente.
- **[Realtà regolata](#adjusted-reality):** Quando una di queste soluzioni di ambiente USA l'analisi predittiva nel cloud per definire e fornire un'interazione con il cliente attraverso l'ambiente naturale, la soluzione ha regolato la realtà.

Comprendere le esigenze dei clienti e misurare l'effetto del cliente sia per determinare se è necessaria un'interazione del dispositivo o un'esperienza di ambiente per convalidare l'ipotesi. Con ognuno di questi punti dati, le sezioni seguenti consentiranno di trovare la soluzione migliore.

## <a name="mobile-experience"></a>Esperienza mobile

Nella prima fase dell'esperienza di ambiente, l'utente si allontana dal computer. I clienti attuali e i professionisti aziendali si spostano fluidamente tra dispositivi mobili e PC. Ogni piattaforma o dispositivo usato dal cliente crea una nuova esperienza potenziale. L'aggiunta di un'esperienza mobile che estende la soluzione principale è il modo più rapido per migliorare l'integrazione nelle immediate vicinanze del cliente. Mentre un dispositivo mobile è lontano dall'ambiente, potrebbe essere più vicino al punto di necessità del cliente.

Quando i clienti sono dispositivi mobili e cambiano di frequente, questo potrebbe rappresentare la forma di ambiente più pertinente per una particolare soluzione. Nel corso dell'ultimo decennio, l'innovazione è stata spesso attivata dall'integrazione delle soluzioni esistenti con un'esperienza mobile.

App Azure Services è un ottimo esempio di questo approccio. Durante le prime iterazioni, la [funzionalità app Web di app Azure Services](https://docs.microsoft.com/azure/app-service/overview) può essere usata per testare l'ipotesi. Poiché le ipotesi diventano più complesse, la [funzionalità app per dispositivi mobili di app Azure Services](https://docs.microsoft.com/azure/app-service-mobile) può estendere l'app Web per l'esecuzione in un'ampia gamma di piattaforme per dispositivi mobili.

## <a name="mixed-reality"></a>Realtà mista

Le soluzioni di realtà mista rappresentano il livello successivo di maturità per le esperienze ambientali. Questo approccio aumenta o replica gli ambienti del cliente; consente di creare un'estensione della realtà per il funzionamento del cliente all'interno di.

> [!IMPORTANT]
> Se è necessario un dispositivo di realtà virtuale (VR) e *non fa già parte dei comportamenti immediati o naturali di un cliente*, la realtà aumentata o virtuale è più un'esperienza alternativa e meno un'esperienza di ambiente.

Le esperienze di realtà miste sono sempre più comuni tra i dipendenti remoti. Il loro utilizzo cresce ancora più rapidamente nei settori che richiedono collaborazione o competenze speciali che non sono immediatamente disponibili nel mercato locale. Situazioni che richiedono il supporto centralizzato per l'implementazione di un prodotto complesso per una forza lavoro remota sono particolarmente fertili per la realtà aumentata. In questi scenari, il team di supporto centrale e i dipendenti remoti possono utilizzare la realtà aumentata per lavorare, risolvere i problemi e installare il prodotto.

Si consideri, ad esempio, il caso di ancoraggi spaziali. Gli ancoraggi spaziali consentono di creare esperienze di realtà miste con oggetti che rendono permanente le rispettive posizioni tra i dispositivi nel tempo. Tramite gli ancoraggi spaziali, è possibile acquisire, registrare e salvare in modo permanente un comportamento specifico, offrendo così un'esperienza di ambiente al successivo funzionamento dell'utente all'interno di tale ambiente. Gli [ancoraggi spaziali di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview) sono un servizio che sposta questa logica nel cloud, consentendo l'esperienza di condivisione tra dispositivi e anche tra soluzioni.

## <a name="integrated-reality"></a>Realtà integrata

Al di là della realtà mobile o anche della realtà mista si trova la realtà integrata. La realtà integrata mira a rimuovere completamente l'esperienza digitale. Ci sono dispositivi con funzionalità di calcolo e connettività. Questi dispositivi possono essere usati per raccogliere i dati dalle immediate vicinanze senza che il cliente debba mai toccare un telefono, un portatile o un dispositivo VR.

Questa esperienza è ideale quando una forma di dispositivo è coerente negli stessi ambienti in cui si verifica la necessità del cliente. Gli scenari comuni includono pavimenti, ascensori e persino la tua auto. Questi tipi di dispositivi di grandi dimensioni contengono già la potenza di calcolo. È anche possibile usare i dati del dispositivo stesso per rilevare i comportamenti dei clienti e inviare tali comportamenti al cloud. Questa acquisizione automatica dei dati sul comportamento dei clienti riduce drasticamente la necessità di un cliente di immettere i dati. Inoltre, l'esperienza Web, per dispositivi mobili o VR può fungere da ciclo di commenti e suggerimenti per condividere ciò che è stato appreso dalla soluzione di realtà integrata.

Esempi di realtà integrata in Azure possono includere:

- [Soluzioni azure Internet delle cose (Internet)](https://docs.microsoft.com/azure/iot-fundamentals), una raccolta di servizi in Azure che consentono di gestire i dispositivi e il flusso di dati da tali dispositivi nel cloud ed eseguire il back-up agli utenti finali.
- [Azure Sphere](https://docs.microsoft.com/azure-sphere), una combinazione di hardware e software. Azure Sphere è un modo sicuro per consentire a un dispositivo esistente di trasmettere in modo sicuro i dati tra il dispositivo e le soluzioni Azure.
- [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk), sensori di intelligenza artificiale con modelli avanzati di visione artificiale e riconoscimento vocale. Questi sensori possono raccogliere dati visivi e audio dalle immediate vicinanze e inserire tali input nella soluzione.

È possibile utilizzare tutti e tre questi strumenti per raccogliere dati dall'ambiente naturale e al punto di necessità del cliente. A questo punto, la soluzione può rispondere a tali input di dati per risolvere la necessità, a volte prima che il cliente sappia anche che si è verificato un trigger per la necessità.

## <a name="adjusted-reality"></a>Realtà modificata

La forma più elevata dell'esperienza ambiente è la realtà adattata, spesso definita *Intelligence di ambiente*. La realtà adattata è un approccio all'uso delle informazioni della soluzione per modificare la realtà del cliente senza che sia necessario interagire direttamente con un'applicazione. Con questo approccio, l'applicazione creata inizialmente per dimostrare l'ipotesi potrebbe non essere più pertinente. I dispositivi nell'ambiente contribuiscono invece a modulare gli input e gli output per soddisfare le esigenze dei clienti.

Assistenti virtuali e Smart speaker offrono ottimi esempi di realtà adattata. Da solo, uno smart Speaker è un esempio di realtà integrata semplice. Ma è possibile aggiungere un sensore di luce e movimento a una soluzione di Smart speaker ed è facile creare una soluzione di base che accenda le luci quando si immette una chat room.

Le fabbriche in tutto il mondo forniscono esempi aggiuntivi di realtà adattata. Durante le fasi iniziali della realtà integrata, i sensori sui dispositivi hanno rilevato condizioni come il surriscaldamento e quindi hanno avvertito un uomo attraverso un'applicazione. In realtà adattata, il cliente potrebbe essere ancora impegnato, ma il ciclo di commenti è più rigoroso. In una fabbrica di realtà regolata, è possibile che un dispositivo rilevi il surriscaldamento in un computer vitale in un punto lungo la linea di assembly. Altrove, un secondo dispositivo rallenta leggermente la produzione per consentire al computer di raffreddarsi e quindi riprendere la velocità completa quando la condizione viene risolta. In questa situazione, il cliente è un partecipante di seconda mano. Il cliente usa l'applicazione per impostare le regole e comprendere il modo in cui tali regole hanno influenzato la produzione, ma non sono necessarie per il ciclo di feedback.

I servizi di Azure descritti in [soluzioni azure Internet delle cose](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](https://docs.microsoft.com/azure-sphere)e [Azure Kinect Developer Kit](https://docs.microsoft.com/azure/Kinect-dk) possono essere componenti di una soluzione di realtà adattata. L'applicazione e la logica di business originali fungeranno quindi da intermediario tra l'input ambientale e la modifica che deve essere apportata nell'ambiente fisico.

Un dispositivo gemello digitale è un altro esempio di realtà adattata. Questo termine si riferisce a una rappresentazione digitale di un dispositivo fisico, presentata tramite computer, dispositivi mobili o formati di realtà mista. A differenza dei modelli 3D meno sofisticati, un dispositivo gemello digitale riflette i dati raccolti da un dispositivo reale nell'ambiente fisico. Questa soluzione consente all'utente di interagire con la rappresentazione digitale in modi che non possono mai essere eseguiti nel mondo reale. Con questo approccio, i dispositivi fisici regolano un ambiente di realtà mista. Tuttavia, la soluzione raccoglie comunque i dati da una soluzione di realtà integrata e usa tali dati per definire la realtà degli ambienti attuali del cliente.

In Azure i dispositivi gemelli digitali vengono creati e accessibili tramite un servizio denominato dispositivi [gemelli digitali di Azure](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di una conoscenza più approfondita delle interazioni dei dispositivi e dell'esperienza di ambiente più adatta alla propria soluzione, si è pronti per esplorare la disciplina finale dell'innovazione, la [stima e l'influenza](./predict.md).

> [!div class="nextstepaction"]
> [Stimare e influenzare](./predict.md)
