---
title: Pianificazione dei prerequisiti per i servizi di gestione del server di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti e pianificazione dei prerequisiti per i servizi di gestione del server di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ac4ece6c5daec788d116e67c79429572722fc618
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548234"
---
# <a name="phase-1-prerequisite-planning-for-azure-server-management-services"></a>Fase 1: pianificazione dei prerequisiti per i servizi di gestione del server di Azure

In questa fase si acquisirà familiarità con la suite di servizi di gestione del server di Azure e si pianifica come distribuire le risorse necessarie per implementare queste soluzioni di gestione.

## <a name="understand-the-tools-and-services"></a>Informazioni sugli strumenti e sui servizi

Esaminare gli [strumenti e i servizi di gestione del server di Azure](./tools-services.md) per una panoramica dettagliata delle aree di gestione che coinvolgono le operazioni di Azure in corso e i servizi e gli strumenti di Azure che contribuiscono a supportare l'utente in queste aree. Soddisfare i requisiti di gestione comporterà l'uso combinato di diversi servizi. Questi strumenti vengono spesso usati come riferimento in questa guida.

Le sezioni seguenti illustrano la pianificazione e la preparazione necessarie per usare questi strumenti e servizi.

## <a name="log-analytics-workspace-and-automation-account-planning"></a>Area di lavoro Log Analytics e pianificazione degli account di automazione

Molti dei servizi che si utilizzeranno per caricare i servizi di gestione di Azure richiedono un'area di lavoro Log Analytics e un account di automazione di Azure collegato.

Un' [area di lavoro log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) è un ambiente univoco per l'archiviazione dei dati di log di monitoraggio di Azure. Ogni area di lavoro dispone di un repository di dati e di una configurazione propri. Le origini dati e le soluzioni sono configurate per archiviare i dati in aree di lavoro particolari. Per le soluzioni di monitoraggio di Azure è necessario che tutti i server siano connessi a un'area di lavoro, in modo che sia possibile archiviare e accedere ai dati di log.

Alcuni dei servizi di gestione richiedono un account di [automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) . Usando questo account e le funzionalità di automazione di Azure, è possibile integrare i servizi di Azure e altri sistemi pubblici per distribuire, configurare e gestire i processi di gestione del server.

I servizi di gestione del server di Azure seguenti richiedono un'area di lavoro Log Analytics collegata e un account di automazione per funzionare:

- [Gestione aggiornamenti di Azure](https://docs.microsoft.com/azure/automation/automation-update-management)
- [Rilevamento modifiche e inventario](https://docs.microsoft.com/azure/automation/change-tracking)
- [Hybrid Runbook Worker](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)
- [Configurazione dello stato desiderato](https://docs.microsoft.com/azure/virtual-machines/extensions/dsc-overview)

La seconda fase di questa guida è incentrata sulla distribuzione di servizi e script di automazione. Viene illustrato come creare un'area di lavoro Log Analytics e un account di automazione. Questa guida illustra anche come usare i criteri di Azure per assicurarsi che le nuove VM siano connesse all'area di lavoro corretta.

Gli esempi illustrati in questa guida presuppongono una distribuzione che non dispone già di server distribuiti nel cloud. Per altre informazioni sui principi e sulle considerazioni relative alla pianificazione delle aree di lavoro, vedere [gestire i dati di log e le aree di lavoro in monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).

## <a name="planning-considerations"></a>Considerazioni sulla pianificazione

Quando si preparano le aree di lavoro e gli account creati per i servizi di gestione di onboarding, consultare le seguenti discussioni sui problemi:

- **Aree geografiche di Azure e conformità alle normative**. Le aree di Azure sono organizzate in aree *geografiche*. Una [geografia di Azure](https://azure.microsoft.com/global-infrastructure/geographies) garantisce che i requisiti di residenza dei dati, sovranità, conformità e resilienza siano rispettati entro i limiti geografici. Se i carichi di lavoro sono soggetti alla sovranità dei dati o ad altri requisiti di conformità, gli account di area di lavoro e di automazione devono essere distribuiti nelle aree all'interno della stessa area geografica di Azure delle risorse del carico di lavoro
- **Numero di aree di lavoro**. Come principio di guida, creare il numero minimo di aree di lavoro necessarie per ogni area geografica di Azure. Si consiglia almeno un'area di lavoro per ogni area geografica di Azure in cui si trovano le risorse di calcolo o di archiviazione. Questo allineamento iniziale aiuta a evitare futuri problemi di regolamentazione durante la migrazione dei dati in aree geografiche diverse.
- **Conservazione e limitazione dei dati**. Per la creazione di aree di lavoro o di account di automazione, potrebbe essere necessario prendere in considerazione i criteri di conservazione dei dati o i requisiti di riduzione dei dati. Per ulteriori informazioni su questi principi e considerazioni aggiuntive quando si pianificano le aree di lavoro, vedere [gestire i dati di log e le aree di lavoro in monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).
- **Mapping dell'area**. Il collegamento di un'area di lavoro Log Analytics e di un account di automazione di Azure è supportato solo tra determinate aree di Azure. Se ad esempio l'area di lavoro Log Analytics è ospitata nell'area *eastus* , è necessario creare l'account di automazione collegato nell'area *EastUS2* per poter essere utilizzato con i servizi di gestione. Se si dispone di un account di automazione creato in un'altra area, non sarà in grado di collegarsi a un'area di lavoro di *eastus*. La scelta dell'area di distribuzione può influire significativamente sui requisiti della geografia di Azure. Consultare la [tabella mapping regione](https://docs.microsoft.com/azure/automation/how-to/region-mappings) per decidere quale area deve ospitare le aree di lavoro e gli account di automazione.
- **Multihoming dell'area di lavoro**. Log Analytics Agent supporta multihoming in alcuni scenari, ma l'agente affronta diverse limitazioni e problemi durante l'esecuzione in questa configurazione. A meno che Microsoft non abbia consigliato di usare multihoming per lo scenario in uso, non è consigliabile configurare multihoming nell'agente di Log Analytics.

## <a name="resource-placement-examples"></a>Esempi di posizionamento delle risorse

Esistono diversi modelli per scegliere la sottoscrizione in cui inserire l'area di lavoro Log Analytics e l'account di automazione. In breve, è necessario inserire l'area di lavoro e gli account di automazione in una sottoscrizione di proprietà del team responsabile dell'implementazione di Gestione aggiornamenti e Rilevamento modifiche e servizi di inventario.

Gli esempi seguenti illustrano alcuni modi in cui è possibile distribuire le aree di lavoro e gli account di automazione.

### <a name="placement-by-geography"></a>Selezione host per geografia

Per gli ambienti piccoli e medi con una singola sottoscrizione e diverse centinaia di risorse che si estendono su più aree geografiche di Azure, creare un'area di lavoro Log Analytics e un account di automazione di Azure in ogni area geografica.

È possibile creare un'area di lavoro e un account di automazione di Azure, una coppia, in ogni gruppo di risorse e distribuire la coppia nella geografia corrispondente alle macchine virtuali. In alternativa, se i criteri di conformità dei dati non stabiliscono che le risorse risiedono in aree specifiche, è possibile creare una coppia per gestire tutte le macchine virtuali. Si consiglia inoltre di inserire le coppie dell'area di lavoro e dell'account di automazione in gruppi di risorse separati per offrire un controllo degli accessi in base al ruolo più granulare.

Nell'esempio del diagramma seguente è presente una sottoscrizione con due gruppi di risorse, ognuno dei quali si trova in un'area geografica diversa.

![Modello di area di lavoro per ambienti da piccoli a medi](./media/workspace-model-small.png)

### <a name="placement-in-a-management-subscription"></a>Selezione host in una sottoscrizione di gestione

Per ambienti più grandi che si estendono su più sottoscrizioni e un reparto IT centrale che possiede il monitoraggio e la conformità, è possibile creare coppie di aree di lavoro e account di automazione in una sottoscrizione di gestione IT. In questo modello, le risorse delle macchine virtuali in una geografia archiviano i dati nell'area di lavoro geography corrispondente nella sottoscrizione di gestione IT. I team di applicazioni che devono eseguire attività di automazione, ma che non richiedono l'area di lavoro collegata e gli account di automazione, possono creare account di automazione distinti nelle proprie sottoscrizioni dell'applicazione.

![Modello di area di lavoro per ambienti di grandi dimensioni](./media/workspace-model-large.png)

### <a name="decentralized-placement"></a>Selezione host decentralizzata

In un modello alternativo per ambienti di grandi dimensioni, la responsabilità per l'applicazione di patch e la gestione può risiedere con il team di sviluppo di applicazioni. In questo caso, è necessario inserire le coppie area di lavoro e account di automazione nelle sottoscrizioni del team dell'applicazione insieme alle altre risorse.

  ![Modello di account area di lavoro per ambienti decentralizzati](./media/workspace-model-decentralized.png)

## <a name="create-a-workspace-and-automation-account"></a>Creare un'area di lavoro e un account di automazione

Dopo aver deciso come posizionare e organizzare le coppie di aree di lavoro e account, è necessario assicurarsi di aver creato queste risorse prima di avviare il processo di onboarding. Gli esempi di automazione inclusi più avanti in questa guida creano automaticamente un'area di lavoro e una coppia di account di automazione. Tuttavia, se non si dispone di un'area di lavoro esistente e di una coppia di account di automazione, è necessario crearne una se si vuole eseguire l'onboarding usando il portale.

Per creare un'area di lavoro Log Analytics tramite il portale di Azure, vedere [creare un'area di lavoro](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace#create-a-workspace). Successivamente, creare un account di automazione corrispondente per ogni area di lavoro seguendo i passaggi descritti in [creare un account di automazione di Azure](https://docs.microsoft.com/azure/automation/automation-quickstart-create-account).

> [!NOTE]
> Quando si crea un account di automazione tramite la portale di Azure, il comportamento predefinito tenta di creare account RunAs per le risorse di Azure Resource Manager e del modello di distribuzione classica. Se non sono presenti VM classiche nell'ambiente e non si è il coamministratore della sottoscrizione, il portale creerà un account RunAs per Gestione risorse, ma genererà un errore durante la distribuzione dell'account RunAs classico. Se non si intende supportare le risorse classiche, è possibile ignorare questo errore.
>
> È anche possibile creare account RunAs usando [PowerShell](https://docs.microsoft.com/azure/automation/manage-runas-account#create-run-as-account-using-powershell).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come caricare [i server nei](./onboarding-overview.md) servizi di gestione di Azure.

> [!div class="nextstepaction"]
> [Eseguire l'onboarding in servizi di gestione server di Azure](./onboarding-overview.md)
