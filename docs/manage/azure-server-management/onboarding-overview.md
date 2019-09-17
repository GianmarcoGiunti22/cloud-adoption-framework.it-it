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
ms.openlocfilehash: 330e297b4fb63eaa376e8b6dac0ccf77c2a16ef4
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028777"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Fase 2: Onboarding di servizi di gestione del server di Azure

Quando si ha familiarità con gli [strumenti](./tools-services.md) e la [pianificazione](./prerequisites.md) necessari per i servizi di gestione di Azure, si è pronti per la seconda fase, che fornisce istruzioni dettagliate per l'onboarding di questi servizi da usare con le risorse di Azure. Per iniziare, è necessario valutare questo processo di onboarding prima di adottarlo nel proprio ambiente.

> [!NOTE]
> Gli approcci di automazione descritti nelle sezioni successive di questa guida sono destinati alle distribuzioni che non dispongono già di server distribuiti nel cloud. Per creare tutte le risorse e i criteri necessari, è necessario avere il ruolo proprietario in una sottoscrizione. Se sono già state create Log Analytics area di lavoro e le risorse dell'account di automazione, è consigliabile passare queste risorse nei parametri appropriati quando si avviano gli script di automazione di esempio.

## <a name="onboarding-processes"></a>Processi di onboarding

Questa sezione del materiale sussidiario illustra i seguenti processi di onboarding per le macchine virtuali di Azure e i server locali:

- **Abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione tramite il portale**. Usare questo processo per acquisire familiarità con i servizi di gestione del server di Azure.
- **Configurare i servizi di gestione per una sottoscrizione usando il portale**. Questo processo consente di configurare l'ambiente di Azure in modo che tutte le nuove macchine virtuali di cui viene eseguito il provisioning usino automaticamente i servizi di gestione. Utilizzare questo approccio se si preferisce l'esperienza portale di Azure per gli script e le righe di comando.
- **Configurare i servizi di gestione per una sottoscrizione usando automazione di Azure**. Questo processo è completamente automatizzato. È sufficiente creare una sottoscrizione e gli script configureranno l'ambiente in modo da usare i servizi di gestione per qualsiasi nuova VM sottoposta a provisioning. Usare questo approccio se si ha familiarità con gli script di PowerShell e i modelli di Azure Resource Manager o se si vuole imparare a usarli.

Le procedure per ognuno di questi approcci sono diverse.

> [!NOTE]
> La sequenza di passaggi di onboarding quando si usa la portale di Azure differisce dalla procedura di onboarding automatizzata, perché il portale offre un'esperienza di onboarding più semplice.

Il diagramma seguente illustra il modello di distribuzione consigliato per i servizi di gestione. 

![Diagramma del modello di distribuzione consigliato](./media/recommended-deployment.png)

> [!NOTE]
> Come illustrato nel diagramma precedente, l'agente di Log Analytics dispone di una configurazione di *registrazione automatica* e *consenso esplicito* per i server locali. La *registrazione automatica* indica che quando l'agente di log Analytics è installato in un server e configurato per la connessione a un'area di lavoro, le soluzioni abilitate nell'area di lavoro verranno applicate automaticamente al server. Il *consenso esplicito* significa che anche se l'agente è installato e connesso all'area di lavoro, la soluzione non verrà applicata a meno che non venga aggiunta alla configurazione dell'ambito del server nell'area di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come caricare una singola macchina virtuale usando il portale per valutare il processo di onboarding.

> [!div class="nextstepaction"]
> [Onboarding di una singola macchina virtuale di Azure per la valutazione](./onboard-single-vm.md)
