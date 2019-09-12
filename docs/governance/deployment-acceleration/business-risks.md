---
title: Motivazioni e rischi aziendali che determinano l'accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla disciplina Accelerazione della distribuzione come parte di una strategia di governance del cloud.
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: feaf5a7f0f2622c2b2289fe81315ea9ccf2ada4e
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828071"
---
# <a name="deployment-acceleration-motivations-and-business-risks"></a>Motivazioni e rischi aziendali di Accelerazione della distribuzione

Questo articolo illustra i motivi per cui i clienti in genere adottano la disciplina Accelerazione della distribuzione all'interno di una strategia di governance del cloud. Offre inoltre alcuni esempi di rischi aziendali che determinano le definizioni sui criteri.

<!-- markdownlint-disable MD026 -->

## <a name="is-deployment-acceleration-relevant"></a>È rilevante l'accelerazione della distribuzione?

I sistemi locali spesso sono distribuiti usando immagini di base o script di installazione. Di solito è necessaria una configurazione aggiuntiva, che può comportare più fasi o l'intervento dell'utente. Questi processi manuali sono soggetti a errori e spesso generano una "deviazione della configurazione", che richiede attività di correzione e risoluzione dei problemi dispendiose in termini di tempo.

La maggior parte delle risorse di Azure può essere distribuita e configurata manualmente tramite il portale di Azure. Questo approccio potrebbe essere sufficiente per le proprie esigenze se si hanno poche risorse da gestire. Tuttavia, man mano che il cloud si espande, l'organizzazione deve iniziare a integrare l'automazione nei processi di distribuzione per garantire che le risorse cloud evitino la configurazione o altri problemi introdotti dai processi manuali. L'adozione di un approccio DevOps o [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) è spesso il modo migliore per gestire le distribuzioni Man mano che le attività di adozione del cloud maturano.

<!-- "en-us" location is required for the URL above. -->

Un piano di Accelerazione della distribuzione affidabile assicura che le risorse del cloud vengano distribuite, aggiornate, configurate in modo corretto e coerente e rimangano tali. Il livello di maturità della strategia di Accelerazione della distribuzione può costituire inoltre un fattore significativo nella [Cost Management strategy (strategia di Gestione costi)](../cost-management/index.md). La configurazione e il provisioning automatizzato delle risorse cloud consentono di ridurre o deallocare le risorse quando la richiesta è scarsa o limitata nel tempo, in modo da pagare per le risorse solo quando servono.

## <a name="business-risk"></a>Rischio aziendale

La disciplina Accelerazione della distribuzione cerca di risolvere i rischi aziendali seguenti. Durante l'adozione del cloud, monitorare la pertinenza di ognuno degli aspetti seguenti:

- **Interrompi servizio:** La mancanza di processi di distribuzione ripetibili e prevedibili o modifiche non gestite alle configurazioni di sistema possono compromettere il normale funzionamento e causare una perdita di produttività o una perdita economica.
- **Sovraccarichi dei costi:** Le modifiche impreviste nella configurazione delle risorse di sistema possono rendere più difficoltosa l'identificazione della causa radice dei problemi, aumentando i costi di sviluppo, operazioni e manutenzione.
- **Inefficienze organizzative:** Le barriere tra team di sviluppo, operazioni e sicurezza possono causare numerose sfide all'adozione efficace delle tecnologie cloud e allo sviluppo di un modello di governance del cloud unificato.

## <a name="next-steps"></a>Passaggi successivi

Usando il [modello di gestione cloud](./template.md), documentare i rischi aziendali che probabilmente verranno introdotti dal piano di adozione del Cloud corrente.

Dopo aver stabilito in modo realistico i rischi aziendali, il passaggio successivo consiste nel documentare le metriche e gli indicatori principali della tolleranza ai rischi dell'azienda allo scopo di monitorare tale tolleranza.

> [!div class="nextstepaction"]
> [Metriche, indicatori e tolleranza ai rischi](./metrics-tolerance.md)
