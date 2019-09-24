---
title: Motivazioni e rischi aziendali della Baseline di identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivazioni e rischi aziendali della Baseline di identità
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: e4203944d6ab5de891f637034d60381290a31c46
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222183"
---
# <a name="identity-baseline-motivations-and-business-risks"></a>Motivazioni e rischi aziendali della Baseline di identità

Questo articolo illustra i motivi per cui i clienti in genere adottano la disciplina Baseline di identità all'interno di una strategia di governance del cloud. Offre anche alcuni esempi di rischi aziendali che determinano le informative sui criteri.

<!-- markdownlint-disable MD026 -->

## <a name="identity-baseline-relevancy"></a>Pertinenza della linea di base di identità

Le directory locali tradizionali sono progettate per consentire alle aziende di controllare accuratamente le autorizzazioni e i criteri per gli utenti, i gruppi e i ruoli all'interno delle reti interne e dei datacenter. Questo avviene per supportare le implementazioni di singoli tenant, con servizi applicabili solo all'interno dell'ambiente locale.

I servizi di gestione delle identità cloud espandono le funzionalità di autenticazione e controllo di accesso di un'organizzazione su Internet. Supportano il multitenant e possono essere usati per gestire gli utenti e i criteri di accesso tra le applicazioni e le distribuzioni cloud. Le piattaforme cloud pubbliche includono servizi di identità nativi del cloud che supportano attività di gestione e distribuzione e sono in grado di [variare i livelli di integrazione](../../decision-guides/identity/index.md) con le soluzioni di identità locali esistenti. Tutte queste caratteristiche possono rendere i criteri di identità cloud più complicati di quanto richiesto dalle tradizionali soluzioni locali.

L'importanza della disciplina Baseline di identità per la distribuzione cloud, dipenderà dalle dimensioni del team e dalla necessità di integrare la soluzione di gestione delle identità basata su cloud con un servizio di gestione delle identità locale esistente. Le distribuzione dei test iniziali possono non richiedere molto in termini di organizzazione utente o di gestione, ma con la maturazione della struttura cloud, è probabile che sia necessario supportare un'integrazione organizzativa più complessa e una gestione centralizzata.

## <a name="business-risk"></a>Rischio aziendale

La disciplina Baseline di identità cerca di affrontare i rischi aziendali principali relativi ai servizi di gestione delle identità e al controllo di accesso. Collaborare con l'azienda per identificare questi rischi e monitorarne la rilevanza durante la pianificazione e l'implementazione delle distribuzioni cloud.

I rischi si differenziano per l'organizzazione, ma i seguenti sono i rischi comuni correlati all'identità che è possibile usare come punto di partenza per le discussioni all'interno del team di governance del cloud:

- **Accesso non autorizzato.** Dati e risorse sensibili a cui possono accedere utenti non autorizzati possono portare a fughe di dati o interruzioni del servizio, violando il perimetro di sicurezza della vostra organizzazione e rischiando di incorrere in responsabilità commerciali o legali.
- **Inefficienza a causa di più soluzioni Identity.** Le organizzazioni con più tenant di servizi di gestione delle identità possono richiedere più account per gli utenti. Ciò può portare a inefficienze per gli utenti, che devono ricordare più set di credenziali e per l'IT nella gestione degli account su più sistemi. Se le assegnazioni di accesso degli utenti non vengono aggiornate tra le soluzioni di gestione delle identità se il personale, i team e gli obiettivi aziendali cambiano, le risorse cloud possono risultare vulnerabili all'accesso non autorizzato o rendere impossibile agli utenti accedere alle risorse richieste.
- **Impossibilità di condividere risorse con partner esterni.** La difficoltà di aggiungere partner commerciali esterni alle soluzioni di gestione delle identità esistenti può impedire un'efficiente condivisione delle risorse e comunicazione aziendale.
- **Dipendenze di identità locali.** I meccanismi di autenticazione legacy o l'autenticazione a più fattori di terze parti potrebbero non essere disponibili nel cloud, richiedendo la migrazione dei carichi di lavoro da riattrezzare o l'implementazione di servizi di gestione delle identità aggiuntivi nel cloud. Entrambi i requisiti potrebbero ritardare o impedire la migrazione e aumentare i costi.

## <a name="next-steps"></a>Passaggi successivi

Usando il [modello di gestione cloud](./template.md), documentare i rischi aziendali che probabilmente verranno introdotti dal piano di adozione del Cloud corrente.

Dopo aver stabilito in modo realistico i rischi aziendali, il passaggio successivo consiste nel documentare le metriche e gli indicatori principali della tolleranza ai rischi dell'azienda allo scopo di monitorare tale tolleranza.

> [!div class="nextstepaction"]
> [Indicatori, metriche e tolleranza ai rischi](./metrics-tolerance.md)
