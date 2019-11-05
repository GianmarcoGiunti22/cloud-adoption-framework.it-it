---
title: Eseguire l'onboarding in servizi di gestione server di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Eseguire l'onboarding in servizi di gestione server di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: c0b1a3ec7f748f9a9217dde45226ae778a2c78d9
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565342"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Fase 2: onboarding dei servizi di gestione del server di Azure

Dopo aver acquisito familiarità con gli [strumenti](./tools-services.md) e la [pianificazione](./prerequisites.md) necessari per i servizi di gestione di Azure, si è pronti per la seconda fase. La fase 2 fornisce istruzioni dettagliate per l'onboarding di questi servizi da usare con le risorse di Azure. Per iniziare, è necessario valutare questo processo di onboarding prima di adottarlo nel proprio ambiente.

> [!NOTE]
> Gli approcci di automazione descritti nelle sezioni successive di questa guida sono destinati alle distribuzioni che non dispongono già di server distribuiti nel cloud. Per creare tutte le risorse e i criteri necessari, è necessario avere il ruolo proprietario in una sottoscrizione. Se sono già state create aree di lavoro Log Analytics e account di automazione, è consigliabile passare queste risorse nei parametri appropriati quando si avviano gli script di automazione di esempio.

## <a name="onboarding-processes"></a>Processi di onboarding

Questa sezione del materiale sussidiario illustra i seguenti processi di onboarding per le macchine virtuali di Azure e i server locali:

- **Abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione tramite il portale**. Usare questo processo per acquisire familiarità con i servizi di gestione del server di Azure.
- **Configurare i servizi di gestione per una sottoscrizione usando il portale**. Questo processo consente di configurare l'ambiente di Azure in modo che tutte le nuove macchine virtuali di cui viene eseguito il provisioning usino automaticamente i servizi di gestione. Utilizzare questo approccio se si preferisce l'esperienza portale di Azure per gli script e le righe di comando.
- **Configurare i servizi di gestione per una sottoscrizione usando automazione di Azure**. Questo processo è completamente automatizzato. È sufficiente creare una sottoscrizione e gli script configureranno l'ambiente in modo da usare i servizi di gestione per qualsiasi nuova VM sottoposta a provisioning. Usare questo approccio se si ha familiarità con gli script di PowerShell e i modelli di Azure Resource Manager o se si vuole imparare a usarli.

Le procedure per ognuno di questi approcci sono diverse.

> [!NOTE]
> Quando si usa il portale di Azure, la sequenza di passaggi di caricamento differisce dalla procedura automatica di onboarding. Il portale offre un'esperienza di onboarding più semplice.

Il diagramma seguente illustra il modello di distribuzione consigliato per i servizi di gestione:

![Diagramma del modello di distribuzione consigliato](./media/recommended-deployment.png)

Come illustrato nel diagramma precedente, l'agente di Log Analytics dispone di una configurazione di *registrazione automatica* e *consenso esplicito* per i server locali:

- **Registrazione automatica:** Quando l'agente di Log Analytics viene installato in un server e configurato per la connessione a un'area di lavoro, le soluzioni abilitate in tale area di lavoro vengono applicate automaticamente al server.
- **Consenso esplicito:** Anche se l'agente è installato e connesso all'area di lavoro, la soluzione non viene applicata a meno che non venga aggiunta alla configurazione dell'ambito del server nell'area di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come caricare una singola macchina virtuale usando il portale per valutare il processo di onboarding.

> [!div class="nextstepaction"]
> [Onboarding di una singola macchina virtuale di Azure per la valutazione](./onboard-single-vm.md)
