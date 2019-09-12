---
title: Linee guida per lo sviluppo di un piano di modifiche aziendali
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione nel cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 44296faa9b5be56988babe9e0a847564d51148c3
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833401"
---
# <a name="business-change-plan"></a>Piano di modifiche aziendali

Tradizionalmente, il rilascio di nuovi carichi di lavoro viene affidato al reparto IT. Durante una trasformazione di notevole entità, ad esempio una migrazione del data center o una migrazione al cloud, è possibile che venga applicato un modello simile di gestione IT. Adottando l'approccio tradizionale, tuttavia, si rischia di perdere l'opportunità di realizzare valore aziendale aggiuntivo. Per questo motivo, prima di promuovere in produzione un carico di lavoro di cui è stata eseguita la migrazione, è consigliabile implementare un approccio più ampio all'adozione da parte degli utenti. Questo articolo illustra i vantaggi aggiuntivi offerti da un piano di modifiche aziendali rispetto a un piano standard di adozione da parte degli utenti.

## <a name="traditional-user-adoption-approach"></a>Approccio tradizionale all'adozione da parte degli utenti

I piani di adozione di questo tipo si concentrano sul modo in cui gli utenti adotteranno una nuova tecnologia o una modifica a una determinata tecnologia. Questo approccio viene testato in base al tempo necessario per consentire agli utenti di acquisire familiarità con i nuovi strumenti. In un tipico piano di adozione da parte degli utenti, il personale IT si concentra sull'installazione, la configurazione, la manutenzione e la formazione associate alle modifiche tecniche introdotte nell'ambiente aziendale.

Anche se gli approcci possano variare, quasi tutti i piani di adozione da parte degli utenti hanno temi generali in comune. Questi temi si basano in genere su un approccio al controllo del rischio e alla facilitazione, in linea con il miglioramento incrementale. La matrice di Eason, illustrata nella figura seguente, rappresenta i fattori chiave associati a questi temi per una serie di tipi di adozione.

![Matrice di Eason per l'adozione da parte degli utenti](../../../_images/eason-matrix.jpg)

*Matrice Eason dei tipi di adozione da parte degli utenti.*

Questi temi sono spesso basati sul presupposto che l'introduzione di nuove soluzioni per gli utenti debba concentrarsi principalmente sul controllo del rischio e sulla facilitazione del cambiamento. Inoltre, il personale IT si è sempre concentrato principalmente sul rischio derivante dal cambiamento tecnologico e dalla facilitazione di tale cambiamento.

## <a name="creating-business-change-plans"></a>Creazione di piani di modifiche aziendali

Un piano di modifiche aziendali va ben oltre il semplice concetto di modifica tecnica e presuppone che ogni rilascio nell'ambito di un processo di migrazione comporti un certo livello di cambiamento dei processi aziendali. L'attenzione viene rivolta in direzione upstream e downstream rispetto all'implementazione delle modifiche tecniche. Le domande seguenti sono utili per riflettere sull'adozione da parte degli utenti in una prospettiva di cambiamento aziendale per ottenere il massimo impatto aziendale:

**Domande upstream.** Le domande upstream esaminano gli effetti o le modifiche prima dell'adozione da parte degli utenti:

- I [risultati aziendali](../../../business-strategy/business-outcomes/index.md) previsti sono stati quantificati?
- L'impatto aziendale è coerente con le [metriche di apprendimento](../../../business-strategy/learning-metrics.md) definite?
- Quali processi e team aziendali usufruiscono di questa soluzione tecnologica?
- Quale persona in azienda può organizzare al meglio gli utenti esperti per il test e il feedback?
- I responsabili aziendali interessati sono stati coinvolti nella definizione delle priorità e nella pianificazione della migrazione?
- In azienda sono previsti eventi o date critiche su cui può avere impatto questo cambiamento?
- Il piano di modifiche aziendali aumenta l'impatto ma riduce al minimo le interruzioni delle attività aziendali?
- È previsto un tempo di inattività? L'intervallo di tempo di inattività è stato comunicato agli utenti finali?

**Domande downstream.** Al termine del processo di adozione ha inizio la fase di trasformazione aziendale. Purtroppo, è questo il punto in cui si concludono molti piani di adozione da parte degli utenti. Le domande downstream consentono al team di strategia del cloud di concentrarsi sulla trasformazione dopo che le modifiche tecniche sono state completate:

- Gli utenti aziendali reagiscono correttamente alle modifiche?
- Ora che le modifiche tecniche sono state adottate, la previsione delle prestazioni risulta corretta?
- I processi aziendali o le esperienze dei clienti stanno cambiando come previsto?
- Sono necessarie altre modifiche per realizzare le metriche di apprendimento?
- Le modifiche sono state allineate ai risultati aziendali prefissati? Se la risposta è negativa, per quale motivo?
- È necessario introdurre altre modifiche per contribuire ai risultati aziendali?
- Sono stati osservati effetti negativi in seguito a questo cambiamento?

Il piano di modifiche aziendali varia a seconda dell'azienda. L'obiettivo di queste domande è di semplificare l'integrazione dell'azienda con il cambiamento associato a ogni rilascio. Se si interpreta ogni rilascio non come semplice cambiamento tecnologico da adottare ma come piano di modifiche aziendali, i risultati aziendali possono risultare più facili da raggiungere.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver documentato e pianificato la trasformazione aziendale, è possibile passare alla [fase di test](./business-test.md).

> [!div class="nextstepaction"]
> [Informazioni aggiuntive per il test aziendale (test di accettazione utente) durante la migrazione](./business-test.md)

## <a name="references"></a>Riferimenti

- Eason, K. (1988) _Information technology and organizational change_, New York: Taylor and Francis.
