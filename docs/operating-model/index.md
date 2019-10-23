---
title: Introduzione al modello operativo
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sul modello operativo di Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: operating-model
ms.openlocfilehash: 77e3ded1f76b096655a7831bc1950bf28bd4c86b
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683821"
---
# <a name="establish-an-operating-model-for-the-cloud"></a>Definire un modello operativo per il cloud

L'adozione del cloud è uno sforzo iterativo incentrato sulle attività che si possono svolgere. La strategia per il cloud definisce la trasformazione digitale per guidare i programmi aziendali, con vari team che attuano i progetti di adozione. Le fasi di pianificazione e preparazione assicurano il successo di ognuno di questi importanti elementi. Tutte le fasi di adozione del cloud equivalgono a progetti tangibili con obiettivi, tempistiche e budget gestibili.

Queste iniziative di adozione sono relativamente facili da monitorare e misurare, anche quando comportano più iterazioni e versioni dei progetti. Ogni fase del ciclo di vita di adozione è importante. Ogni fase è soggetta a potenziali ostacoli tra vincoli aziendali, culturali e tecnologici. Ma ogni fase dipende pesantemente dal modello operativo sottostante.

**Se l'adozione descrive quello che si fa, il modello operativo definisce il chi e il come che rendono possibile l'adozione dietro le quinte.**

Secondo Satya Nadella, **"La cultura aziendale ha sempre la meglio sulla strategia"** . Il modello operativo è la personificazione della cultura IT, acquisita in numerosi processi misurabili. Se il cloud è basato su un modello operativo stabile, la cultura genererà la strategia, accelerando l'adozione e la realizzazione del valore di business. Al contrario, quando l'adozione ha successo ma non c'è un modello operativo, i risultati possono essere straordinari ma di brevissima durata. Per il successo a lungo termine, è fondamentale che l'adozione e i modelli operativi procedano in parallelo.

## <a name="establish-your-operating-model"></a>Definire il modello operativo

Gli attuali modelli operativi possono essere ridimensionati per supportare l'adozione del cloud. Un modello operativo moderno può aiutare a risolvere i problemi non tecnici che si presentano durante l'adozione del cloud.

Questa sezione di Cloud Adoption Framework offre un modello operativo attuabile, da usare come riferimento per prendere decisioni non tecniche. Questo modello operativo è costituito da tre metodologie che possono risultare utili nella creazione di un modello operativo cloud personalizzato:

- [Governance](../govern/index.md): assicurare la coerenza tra le attività di adozione. Allinearsi ai requisiti di governance o conformità per mantenere un ambiente tra cloud gestito in modo adeguato.
- [Gestione](../manage/index.md): allineare i processi in corso per la gestione operativa della tecnologia per massimizzare il valore aggiunto ottenuto e ridurre al minimo le interruzioni.
- [Organizzazione](../organize/index.md): Con la maturazione del modello operativo, si evolvono anche i vari team e le funzionalità che lo supportano.

## <a name="aligning-operating-models"></a>Allineamento dei modelli operativi

Il cloud e l'economia digitale hanno messo in luce l'esigenza di più modelli operativi. Questa esigenza è a volte dettata dal requisito di supportare più cloud pubblici. Più in generale, dipende dalla transizione dall'ambiente locale al cloud. In ogni caso, è importante allineare i modelli operativi per garantire prestazioni massime e ridondanza minima.

Gli analisti prevedono un'ampia e diffusa adozione del multi-cloud. Molti clienti iniziano a confermare questa previsione. Purtroppo, la gestione di più cloud presenta sfide significative, secondo quanto segnalato dai clienti. La duplicazione di risorse, processi, competenze e tecnologie genera un aumento dei costi e non il risparmio previsto per il cloud. Per evitare l'affermarsi di questa tendenza, è consigliabile adottare un modello operativo specializzato. Con l'allineamento dovrà esserci sempre un unico **modello operativo generale**. Per supportare le deviazioni dal modello standard in specifici scenari, si potranno sfruttare **modelli operativi specializzati**.

- **Modello operativo generale:** il modello operativo generale si basa su una singola piattaforma di cloud pubblico o privato. Le operazioni di tale piattaforma definiscono standard, criteri e processi operativi. Il modello operativo dovrà essere il principale strumento per delineare la futura strategia per il cloud. In questo modello l'obiettivo è affidarsi al principale provider di servizi cloud per la maggior parte delle attività di adozione del cloud.

- **Modello operativo specializzato:** per realizzare specifici risultati aziendali, può essere preferibile rivolgersi a un provider di servizi cloud alternativo. In presenza di casi d'uso aziendali convincenti, gli standard, i criteri e i processi del modello operativo generale vengono applicati al nuovo provider di servizi cloud, ma vengono poi modificati in base al caso d'uso specifico.

Se la principale piattaforma di scelta è Azure, le guide e le procedure consigliate riportate in ogni sezione del modello operativo descritte sopra risulteranno particolarmente utili per la creazione di un modello operativo personalizzato. Ma partendo dal presupposto che non tutti i clienti che consultano questo framework hanno scelto Azure come piattaforma principale, il contenuto teorico di ogni sezione può essere applicato a modelli operativi del cloud pubblico o privato con risultati simili.

## <a name="next-steps"></a>Passaggi successivi

La governance rappresenta il primo passo da compiere per definire un modello operativo per il cloud.

> [!div class="nextstepaction"]
> [Informazioni sulla governance del cloud](../govern/index.md)
