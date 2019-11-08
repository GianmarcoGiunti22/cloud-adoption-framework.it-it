---
title: Pianificazione dei prerequisiti per i servizi di gestione del server di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti e pianificazione dei prerequisiti per i servizi di gestione del server di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 20a4168f5a7650b20357de2ec2628a0edb093993
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751650"
---
# <a name="phase-1-prerequisite-planning-for-azure-server-management-services"></a>Fase 1: pianificazione dei prerequisiti per i servizi di gestione del server di Azure

In questa fase si acquisirà familiarità con la suite di servizi di gestione del server di Azure e si pianifica come distribuire le risorse necessarie per implementare queste soluzioni di gestione.

## <a name="understand-the-tools-and-services"></a>Informazioni sugli strumenti e sui servizi

Esaminare [gli strumenti e i servizi di gestione del server di Azure](./tools-services.md) per una panoramica dettagliata di:

- Le aree di gestione utilizzate per le operazioni di Azure in corso.
- I servizi e gli strumenti di Azure che aiutano a supportare l'utente in queste aree.

Questi servizi verranno usati insieme per soddisfare i requisiti di gestione. Questi strumenti vengono spesso usati come riferimento in questa guida.

Le sezioni seguenti illustrano la pianificazione e la preparazione necessarie per usare questi strumenti e servizi.

## <a name="log-analytics-workspace-and-automation-account-planning"></a>Area di lavoro Log Analytics e pianificazione degli account di automazione

Molti dei servizi da usare per l'onboarding dei servizi di gestione di Azure richiedono un'area di lavoro Log Analytics e un account di automazione di Azure collegato.

Un'[area di lavoro Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) è un ambiente univoco per l'archiviazione dei dati dei log di Monitoraggio di Azure. Ogni area di lavoro include un proprio repository di dati e una configurazione specifica. Le origini dati e le soluzioni sono configurate per archiviare i dati in determinate aree di lavoro. Per le soluzioni di monitoraggio di Azure è necessario che tutti i server siano connessi a un'area di lavoro, in modo che sia possibile archiviare e accedere ai dati dei relativi log.

Alcuni dei servizi di gestione richiedono un account di [automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) . Questo account viene usato e le funzionalità di automazione di Azure per integrare i servizi di Azure e altri sistemi pubblici per distribuire, configurare e gestire i processi di gestione del server.

I servizi di gestione del server di Azure seguenti richiedono un'area di lavoro Log Analytics collegata e un account di automazione:

- [Gestione aggiornamenti di Azure](https://docs.microsoft.com/azure/automation/automation-update-management)
- [Rilevamento modifiche e inventario](https://docs.microsoft.com/azure/automation/change-tracking)
- [Hybrid Runbook Worker](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)
- [Configurazione dello stato desiderato](https://docs.microsoft.com/azure/virtual-machines/extensions/dsc-overview)

La seconda fase di questa guida è incentrata sulla distribuzione di servizi e script di automazione. Viene illustrato come creare un'area di lavoro Log Analytics e un account di automazione. Questa guida illustra anche come usare i criteri di Azure per assicurarsi che le nuove macchine virtuali siano connesse all'area di lavoro corretta.

Gli esempi in questa guida presuppongono una distribuzione che non dispone già di server distribuiti nel cloud. Per altre informazioni sui principi e sulle considerazioni relative alla pianificazione delle aree di lavoro, vedere [gestire i dati di log e le aree di lavoro in monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).

## <a name="planning-considerations"></a>Considerazioni sulla pianificazione

Quando si preparano le aree di lavoro e gli account necessari per l'onboarding dei servizi di gestione, considerare i problemi seguenti:

- **Aree geografiche di Azure e conformità alle normative:** Le aree di Azure sono organizzate in aree *geografiche*. Una [geografia di Azure](https://azure.microsoft.com/global-infrastructure/geographies) garantisce che i requisiti di residenza dei dati, sovranità, conformità e resilienza siano rispettati entro i limiti geografici. Se i carichi di lavoro sono soggetti alla sovranità dei dati o ad altri requisiti di conformità, gli account di area di lavoro e di automazione devono essere distribuiti nelle aree all'interno della stessa area geografica di Azure delle risorse del carico di lavoro supportate
- **Numero di aree di lavoro:** Come principio di guida, creare il numero minimo di aree di lavoro necessarie per ogni area geografica di Azure. Si consiglia almeno un'area di lavoro per ogni area geografica di Azure in cui si trovano le risorse di calcolo o di archiviazione. Questo allineamento iniziale aiuta a evitare futuri problemi di regolamentazione quando si esegue la migrazione dei dati in aree geografiche diverse.
- **Conservazione e limitazione dei dati:** Per la creazione di aree di lavoro o di account di automazione, potrebbe essere necessario prendere in considerazione i criteri di conservazione dei dati o i requisiti di riduzione dei dati. Per altre informazioni su questi principi e per altre considerazioni sulla pianificazione delle aree di lavoro, vedere [gestire i dati di log e le aree di lavoro in monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).
- **Mapping area:** Il collegamento di un'area di lavoro Log Analytics e di un account di automazione di Azure è supportato solo tra determinate aree di Azure. Se, ad esempio, l'area di lavoro Log Analytics è ospitata nell'area *eastus* , è necessario creare l'account di automazione collegato nell'area *EastUS2* da usare con i servizi di gestione. Se si dispone di un account di automazione creato in un'altra area, non è possibile collegarsi a un'area di lavoro di *eastus*. La scelta dell'area di distribuzione può influire significativamente sui requisiti della geografia di Azure. Consultare la [tabella mapping regione](https://docs.microsoft.com/azure/automation/how-to/region-mappings) per decidere quale area deve ospitare le aree di lavoro e gli account di automazione.
- **Multihoming area di lavoro:** L'agente di Log Analytics di Azure supporta multihoming in alcuni scenari, ma l'agente affronta diverse limitazioni e problemi durante l'esecuzione in questa configurazione. A meno che non sia stato consigliato da Microsoft per uno scenario specifico, non è consigliabile configurare multihoming nell'agente Log Analytics.

## <a name="resource-placement-examples"></a>Esempi di posizionamento delle risorse

Esistono diversi modelli per scegliere la sottoscrizione in cui inserire l'area di lavoro Log Analytics e l'account di automazione. In breve, inserire l'area di lavoro e gli account di automazione in una sottoscrizione di proprietà del team responsabile dell'implementazione del servizio Gestione aggiornamenti e del Rilevamento modifiche e del servizio di inventario.

Di seguito sono riportati esempi di alcuni modi per distribuire le aree di lavoro e gli account di automazione.

### <a name="placement-by-geography"></a>Selezione host per geografia

Gli ambienti piccoli e medi hanno una singola sottoscrizione e diverse centinaia di risorse che si estendono su più aree geografiche di Azure. Per questi ambienti, creare un'area di lavoro Log Analytics e un account di automazione di Azure in ogni area geografica.

È possibile creare un'area di lavoro e un account di automazione di Azure, come una coppia, in ogni gruppo di risorse. Distribuire quindi la coppia nella geografia corrispondente alle macchine virtuali.

In alternativa, se i criteri di conformità dei dati non stabiliscono che le risorse risiedono in aree specifiche, è possibile creare una coppia per gestire tutte le macchine virtuali. Si consiglia inoltre di inserire le coppie dell'area di lavoro e dell'account di automazione in gruppi di risorse separati per offrire un controllo degli accessi in base al ruolo più granulare.

Nell'esempio riportato nel diagramma seguente è presente una sottoscrizione con due gruppi di risorse, ognuno dei quali si trova in un'area geografica diversa:

![Modello di area di lavoro per ambienti da piccoli a medi](./media/workspace-model-small.png)

### <a name="placement-in-a-management-subscription"></a>Selezione host in una sottoscrizione di gestione

Gli ambienti più grandi si estendono su più sottoscrizioni e hanno un reparto IT centrale che possiede il monitoraggio e la conformità. Per questi ambienti, creare coppie di aree di lavoro e account di automazione in una sottoscrizione di gestione IT. In questo modello, le risorse della macchina virtuale in un'area geografica archiviano i dati nell'area di lavoro geography corrispondente nella sottoscrizione di gestione IT. Se i team di applicazioni devono eseguire attività di automazione, ma non richiedono l'area di lavoro collegata e gli account di automazione, possono creare account di automazione distinti nelle proprie sottoscrizioni dell'applicazione.

![Modello di area di lavoro per ambienti di grandi dimensioni](./media/workspace-model-large.png)

### <a name="decentralized-placement"></a>Selezione host decentralizzata

In un modello alternativo per ambienti di grandi dimensioni, il team di sviluppo di applicazioni può essere responsabile dell'applicazione di patch e della gestione. In questo caso, inserire le coppie dell'area di lavoro e dell'account di automazione nelle sottoscrizioni del team dell'applicazione insieme alle altre risorse.

  ![Modello di account area di lavoro per ambienti decentralizzati](./media/workspace-model-decentralized.png)

## <a name="create-a-workspace-and-automation-account"></a>Creare un'area di lavoro e un account di automazione

Dopo aver scelto il modo migliore per inserire e organizzare le coppie di aree di lavoro e account, assicurarsi di aver creato queste risorse prima di avviare il processo di caricamento. Gli esempi di automazione più avanti in questa guida creano automaticamente un'area di lavoro e una coppia di account di automazione. Tuttavia, se si vuole eseguire l'onboarding usando il portale di Azure e non si dispone di un'area di lavoro esistente e di una coppia di account di automazione, è necessario crearne una.

Per creare un'area di lavoro Log Analytics usando il portale di Azure, vedere [creare un'area di lavoro](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace#create-a-workspace). Successivamente, creare un account di automazione corrispondente per ogni area di lavoro seguendo i passaggi descritti in [creare un account di automazione di Azure](https://docs.microsoft.com/azure/automation/automation-quickstart-create-account).

> [!NOTE]
> Quando si crea un account di automazione usando il portale di Azure, il portale tenta per impostazione predefinita di creare account RunAs per Azure Resource Manager e per le risorse del modello di distribuzione classica. Se non si dispone di macchine virtuali classiche nell'ambiente e non si è il coamministratore della sottoscrizione, il portale crea un account RunAs per Gestione risorse, ma genera un errore durante la distribuzione dell'account RunAs classico. Se non si intende supportare le risorse classiche, è possibile ignorare questo errore.
>
> È anche possibile creare account RunAs usando [PowerShell](https://docs.microsoft.com/azure/automation/manage-runas-account#create-run-as-account-using-powershell).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come caricare [i server](./onboarding-overview.md) in servizi di gestione del server di Azure.

> [!div class="nextstepaction"]
> [Eseguire l'onboarding in servizi di gestione server di Azure](./onboarding-overview.md)
