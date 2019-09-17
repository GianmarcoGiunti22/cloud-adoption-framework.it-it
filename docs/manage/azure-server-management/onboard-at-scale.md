---
title: Configurare i servizi di gestione di Azure per una sottoscrizione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurare i servizi di gestione di Azure per una sottoscrizione
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 56a989e975625c9d8f0f3db80dab9043dca3a479
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028202"
---
# <a name="configure-azure-management-services-at-scale"></a>Configurare i servizi di gestione di Azure su larga scala

Il caricamento dei servizi di gestione di Azure nei server implica due attività: la distribuzione degli agenti del servizio nei server e l'abilitazione delle soluzioni di gestione. In questo articolo vengono illustrati i processi seguenti che consentono di completare queste attività:

- [Distribuzione degli agenti necessari nelle macchine virtuali di Azure con criteri di Azure](#deploy-extensions-to-azure-vms-using-azure-policy)
- [Distribuzione degli agenti richiesti nei server locali](#install-required-agents-on-on-premises-servers)
- [Abilitare e configurare le soluzioni](#enable-and-configure-solutions)

> [!NOTE]
> Creare l' [area di lavoro log Analytics richiesta e l'account di automazione di Azure](./prerequisites.md#create-a-workspace-and-automation-account) prima di caricare le macchine virtuali in servizi di gestione di Azure.

## <a name="deploy-extensions-to-azure-vms-using-azure-policy"></a>Distribuire estensioni in macchine virtuali di Azure con criteri di Azure

Tutte le soluzioni di gestione illustrate in [strumenti e servizi di gestione di Azure](./tools-services.md) richiedono l'installazione dell'agente di log Analytics in macchine virtuali di Azure e server locali. È possibile caricare le macchine virtuali di Azure su larga scala usando criteri di Azure. Assegnare i criteri per assicurarsi che l'agente sia installato in tutte le macchine virtuali di Azure e connesso all'area di lavoro Log Analytics corretta.

Criteri di Azure prevede un'iniziativa di [criteri](https://docs.microsoft.com/azure/governance/policy/index.md#initiative-definition) incorporata che include l'agente di log Analytics e [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-onboard#the-microsoft-dependency-agent), necessario per monitoraggio di Azure per le macchine virtuali.

<!-- TODO: Add these when available.
- [Preview]: Enable Azure Monitor for virtual machine scale sets.
- [Preview]: Enable Azure Monitor for VMs.
 -->

> [!NOTE]
> Per altre informazioni sui vari agenti per il monitoraggio di Azure, vedere [Panoramica degli agenti di monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agents-overview).

### <a name="assign-policies"></a>Assegnare criteri

Per assegnare i criteri elencati nella sezione precedente:

1. Nella portale di Azure passare ad **Azure Policy** > **assegnations** > **assign Initiative**.

    ![Screenshot dell'interfaccia dei criteri del portale](./media/onboarding-at-scale1.png)

2. Nella pagina **assegnazione criteri** selezionare l' **ambito** facendo clic sui puntini di sospensione (...) e quindi selezionare un gruppo di gestione o una sottoscrizione. Facoltativamente, selezionare un gruppo di risorse. Un ambito determina le risorse o il gruppo di risorse a cui sono assegnati i criteri. Quindi scegliere **Seleziona** nella parte inferiore della pagina **ambito** .

3. Selezionare i puntini di sospensione (...) accanto a **definizione criteri** per aprire l'elenco delle definizioni disponibili. È possibile filtrare la definizione di iniziativa immettendo **monitoraggio di Azure** nella casella di **ricerca** :

    ![Screenshot dell'interfaccia dei criteri del portale](./media/onboarding-at-scale2.png)

4. Il **nome dell'assegnazione** viene popolato automaticamente con il nome del criterio selezionato, ma è possibile modificarlo. È anche possibile aggiungere una descrizione facoltativa per fornire ulteriori informazioni su questa assegnazione dei criteri. Il campo **assegnato da** viene compilato automaticamente in base all'utente che ha eseguito l'accesso. Questo campo è facoltativo e è possibile immettere valori personalizzati.

5. Per questo criterio, selezionare **log Analytics area di lavoro** per l'agente di log Analytics da associare.

    ![Screenshot dell'interfaccia dei criteri del portale](./media/onboarding-at-scale3.png)

6. Controllare il **percorso di identità gestito**. Se questi criteri sono di tipo [DeployIfNotExists](https://docs.microsoft.com/azure/governance/policy/concepts/effects#deployifnotexists), sarà necessaria un'identità gestita per distribuire il criterio. Nel portale, l'account verrà creato come indicato con la selezione della casella di controllo.

7. Selezionare **Assegna**.

Al termine della procedura guidata, l'assegnazione dei criteri verrà distribuita nell'ambiente. Possono essere necessari fino a 30 minuti affinché i criteri abbiano effetto. È possibile testarlo creando nuove macchine virtuali dopo 30 minuti, quindi controllando che la Microsoft Monitoring Agent (MMA) sia abilitata per impostazione predefinita nella macchina virtuale.

## <a name="install-required-agents-on-on-premises-servers"></a>Installare gli agenti richiesti nei server locali

> [!NOTE]
> Creare l' [area di lavoro log Analytics richiesta e l'account di automazione di Azure](./prerequisites.md#create-a-workspace-and-automation-account) prima di caricare i server nei servizi di gestione di Azure.

Per i server locali, è necessario scaricare e installare manualmente l'agente di [log Analytics e Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud) e configurarli per connettersi all'area di lavoro corretta. A tale scopo, specificare l'ID dell'area di lavoro e le informazioni sulla chiave, che è possibile trovare accedendo all'area di lavoro log Analytics nel portale di Azure e selezionando **Impostazioni** > **Impostazioni avanzate**.

![Screenshot delle impostazioni avanzate dell'area di lavoro Log Analytics nel portale di Azure](./media/onboarding-on-premises.png)

## <a name="enable-and-configure-solutions"></a>Abilitare e configurare le soluzioni

Per abilitare le soluzioni, è necessario configurare l'area di lavoro Log Analytics. Le macchine virtuali di Azure e i server locali caricati otterranno le soluzioni dalle aree di lavoro Log Analytics a cui sono connesse.

In questa sezione sono descritte le soluzioni seguenti:

- [Gestione degli aggiornamenti](#update-management)
- [Rilevamento modifiche e inventario](#change-tracking-and-inventory-solutions)
- [Log attività di Azure](#azure-activity-log)
- [Integrità agente Log Analytics di Azure](#azure-log-analytics-agent-health)
- [Antimalware Assessment](#antimalware-assessment)
- [Monitoraggio di Azure per le macchine virtuali](#azure-monitor-for-vms)
- [Centro sicurezza di Azure](#azure-security-center)

### <a name="update-management"></a>Gestione degli aggiornamenti

Gestione aggiornamenti, Rilevamento modifiche e le soluzioni di inventario richiedono sia un'area di lavoro Log Analytics che un account di automazione. Per assicurarsi che queste risorse siano configurate correttamente, è consigliabile eseguire l'onboarding tramite l'account di automazione. Per altre informazioni, vedere [onboarding gestione aggiornamenti, rilevamento modifiche e Inventory Solutions](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

Si consiglia di abilitare la soluzione Gestione aggiornamenti per tutti i server. Gestione aggiornamenti è gratuita per le macchine virtuali di Azure e i server locali. Se si Abilita Gestione aggiornamenti tramite l'account di automazione, viene creata una [configurazione dell'ambito](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account#scope-configuration) nell'area di lavoro. È necessario aggiornare manualmente l'ambito per includere i computer coperti dal servizio di aggiornamento.

Per coprire tutti i server esistenti, nonché i server futuri, è necessario rimuovere la configurazione dell'ambito. A tale scopo, visualizzare l'account di automazione nella portale di Azure e selezionare **Gestione aggiornamenti** > Gestisci Abilita**computer** > **in tutti i computer disponibili e futuri**. L'abilitazione di questa impostazione consente a tutte le macchine virtuali di Azure connesse all'area di lavoro di usare Gestione aggiornamenti.

![Screenshot del Gestione aggiornamenti nel portale di Azure](./media/onboarding-configuration1.png)

### <a name="change-tracking-and-inventory-solutions"></a>Soluzioni di Rilevamento modifiche e inventario

Per eseguire l'onboarding delle soluzioni di Rilevamento modifiche e inventario, seguire la stessa procedura illustrata Gestione aggiornamenti. Per ulteriori informazioni sull'onboarding di queste soluzioni dall'account di automazione, vedere onboarding [Gestione aggiornamenti, rilevamento modifiche e Inventory Solutions](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

La soluzione Rilevamento modifiche è gratuita per le macchine virtuali di Azure e costa $6 per nodo al mese per i server locali. Questo costo copre Rilevamento modifiche, l'inventario e la configurazione dello stato desiderato. Se si desidera registrare solo server locali specifici, è possibile optare per questi server. Si consiglia di eseguire l'onboarding di tutti i server di produzione.

#### <a name="opt-in-via-the-azure-portal"></a>Acconsentire esplicitamente tramite il portale di Azure

1. Passare all'account di automazione in cui è abilitato Rilevamento modifiche e l'inventario.
2. Selezionare **rilevamento modifiche**.
3. Selezionare **Gestisci computer** nel riquadro superiore destro.
4. Selezionare **Abilita nei computer selezionati**e selezionare i computer da attivare facendo clic su **Aggiungi** accanto al nome del computer.
5. Selezionare **Abilita** per abilitare la soluzione per tali computer.

![Screenshot del Rilevamento modifiche nel portale di Azure](./media/onboarding-configuration2.png)

#### <a name="opt-in-by-using-saved-searches"></a>Acconsentire esplicitamente all'uso di ricerche salvate

In alternativa, è possibile configurare la configurazione dell'ambito per acconsentire esplicitamente ai server locali. La configurazione dell'ambito usa le ricerche salvate.

Per creare o modificare la ricerca salvata, attenersi alla procedura seguente:

1. Passare all'area di lavoro Log Analytics collegata all'account di automazione configurato nei passaggi precedenti.

2. In **Generale** selezionare **Ricerche salvate**.

3. Nella casella **filtro** immettere **rilevamento modifiche** per filtrare l'elenco di ricerche salvate. Nei risultati selezionare **MicrosoftDefaultComputerGroup**.

4. Immettere il nome del computer o il VMUUID per includere i computer per i quali si desidera acconsentire esplicitamente Rilevamento modifiche.

    ```kusto
    Heartbeat
    | where AzureEnvironment=~"Azure" or Computer in~ ("list of the on-premises server names", "server1")
    | distinct Computer
    ```

    > [!NOTE]
    > Il nome del server deve corrispondere esattamente al valore incluso nell'espressione e non deve contenere un suffisso del nome di dominio.

5. Selezionare **Salva**.

6. Per impostazione predefinita, la configurazione dell'ambito è collegata alla ricerca salvata di **MicrosoftDefaultComputerGroup** e verrà aggiornata automaticamente.

### <a name="azure-activity-log"></a>Azure Activity Log

Il [log attività di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) fa anche parte di monitoraggio di Azure. Fornisce informazioni approfondite sugli eventi a livello di sottoscrizione che si verificano in Azure.

Per aggiungere la soluzione:

1. Nella portale di Azure aprire **tutti i servizi** e selezionare **gestione +**  > **soluzioni**di governance.
2. Nella visualizzazione **soluzioni** selezionare **Aggiungi**.
3. Cercare **analisi log attività** e selezionarlo.
4. Selezionare **Create**.

È necessario specificare il nome dell' **area** di lavoro creata nella sezione precedente in cui la soluzione è abilitata.

### <a name="azure-log-analytics-agent-health"></a>Integrità agente di Azure Log Analytics

La soluzione Azure Log Analytics Integrità agente offre informazioni dettagliate sull'integrità, sulle prestazioni e sulla disponibilità dei server Windows e Linux.

Per aggiungere la soluzione:

1. Nella portale di Azure aprire **tutti i servizi** e selezionare **gestione +**  > **soluzioni**di governance.
2. Nella visualizzazione **soluzioni** selezionare **Aggiungi**.
3. Cercare **Azure log Analytics Health Agent** e selezionarlo.
4. Selezionare **Create**.

È necessario specificare il nome dell' **area** di lavoro creata nella sezione precedente in cui la soluzione è abilitata.

Al termine della creazione, l'istanza della risorsa dell'area di lavoro Visualizza **AgentHealthAssessment** quando si seleziona **Visualizza** > **soluzioni**.

### <a name="antimalware-assessment"></a>Antimalware Assessment

La soluzione Valutazione antimalware consente di identificare i server che sono infetti o a rischio maggiore di infezioni da parte di malware.

Per aggiungere la soluzione:

1. Nella portale di Azure aprire **tutti i servizi** e selezionare **gestione +**  > **soluzioni**di governance.
2. Nella visualizzazione **soluzioni** selezionare **Aggiungi**.
3. Cercare **valutazione antimalware** e selezionarlo.
4. Selezionare **Create**.

È necessario specificare il nome dell' **area** di lavoro creata nella sezione precedente in cui la soluzione è abilitata.

Al termine della creazione, l'istanza della risorsa dell' area di lavoro Visualizza antimalware quando si seleziona **Visualizza** > **soluzioni**.

### <a name="azure-monitor-for-vms"></a>Monitoraggio di Azure per le macchine virtuali

È possibile abilitare [monitoraggio di Azure per le macchine virtuali](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) tramite la pagina Visualizza per l'istanza di macchina virtuale, come descritto nell'articolo precedente, [abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione](./onboard-single-vm.md). Non è consigliabile abilitare le soluzioni direttamente dalla pagina **soluzioni** come per le altre soluzioni descritte in questo articolo. Per le distribuzioni su larga scala, potrebbe essere più semplice usare l' [automazione](./onboarding-automation.md) per abilitare le soluzioni corrette nell'area di lavoro.

### <a name="azure-security-center"></a>Centro sicurezza di Azure

In queste linee guida è consigliabile caricare tutti i server nel livello *gratuito* del Centro sicurezza di Azure per impostazione predefinita. Questa opzione offre un livello di base di valutazioni della sicurezza e raccomandazioni per la sicurezza praticabile per l'ambiente in uso. L'aggiornamento al livello *standard* del Centro sicurezza offre vantaggi aggiuntivi, descritti in dettaglio nella pagina dei [prezzi del Centro sicurezza](https://docs.microsoft.com/azure/security-center/security-center-pricing).

Per abilitare il livello gratuito del Centro sicurezza di Azure, seguire questa procedura:

1. Passare alla pagina del portale del **Centro sicurezza** .
2. Selezionare **criteri di sicurezza** in **criteri & conformità**.
3. Trovare la risorsa dell'area di lavoro Log Analytics creata nel riquadro più a destra.
4. Selezionare **Modifica impostazioni >** per l'area di lavoro.
5. Selezionare **Piano tariffario**.
6. Scegliere l'opzione **gratuito** .
7. Selezionare **Salva**.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come usare l'automazione per l'onboarding di server e la creazione di avvisi.

> [!div class="nextstepaction"]
> [Automatizzare l'onboarding e la configurazione degli avvisi](./onboarding-automation.md)
