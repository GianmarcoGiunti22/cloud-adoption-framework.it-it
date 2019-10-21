---
title: Distribuire il piano di adozione del cloud in Azure DevOps
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Distribuire il modello per il piano di adozione del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 9988141c1f0133a0a18c11c46e09d7285d988e5e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549178"
---
# <a name="cloud-adoption-plan-and-azure-devops"></a>Piano di adozione del cloud e Azure DevOps

Azure DevOps è il set di strumenti basati sul cloud per i clienti di Azure che gestiscono progetti iterativi. Sono inclusi anche gli strumenti per la gestione delle pipeline di distribuzione e altri aspetti importanti di DevOps. 

Questo articolo illustra come distribuire rapidamente un backlog in Azure DevOps usando un modello di piano di adozione del cloud. Questo modello allinea le attività di adozione del cloud a un processo standardizzato, in base alle linee guida nel Framework di adozione del cloud.

## <a name="create-your-cloud-adoption-plan"></a>Creare il piano di adozione del cloud

Per distribuire il piano di adozione del cloud, aprire il [Generatore di demo di Azure DevOps](https://aka.ms/adopt/plan/generator). Questo strumento consente di distribuire il modello nel tenant di Azure DevOps. Per usare lo strumento, è necessario eseguire i passaggi seguenti:

1. Verificare che il campo **modello selezionato** sia impostato su **piano di adozione cloud**. In caso contrario, selezionare **Scegli modello** per scegliere il modello corretto.
2. Selezionare l'organizzazione DevOps di Azure dall'elenco a discesa **Seleziona organizzazione** .
3. Immettere un nome per il nuovo progetto. Il piano di adozione del cloud avrà questo nome quando viene distribuito nel tenant di Azure DevOps.
4. Selezionare **Crea progetto** per creare un nuovo progetto nel tenant, in base al modello di piano. Un indicatore di stato Mostra lo stato di avanzamento verso la distribuzione del progetto.
5. Al termine della distribuzione selezionare **passa a progetto** per visualizzare il nuovo progetto.

Dopo aver creato il progetto, continuare con questa serie di articoli per vedere come è possibile modificare il modello per allinearlo al piano di adozione del cloud.

Per ulteriori informazioni sul supporto e su questo strumento, vedere [Azure DevOps Services Generatore di demo](https://docs.microsoft.com/azure/devops/demo-gen/?toc=%2Fazure%2Fdevops%2Fdemo-gen%2Ftoc.json&bc=%2Fazure%2Fdevops%2Fdemo-gen%2Fbreadcrumb%2Ftoc.json&view=azure-devops).

## <a name="bulk-edit-the-cloud-adoption-plan"></a>Modificare in blocco il piano di adozione del cloud

Quando il progetto del piano è stato distribuito, è possibile utilizzare Microsoft Excel per modificarlo. È molto più semplice creare nuovi carichi di lavoro o asset nel piano usando Excel rispetto all'esperienza del browser Azure DevOps.

Per preparare la workstation per la modifica bulk, vedere [aggiungere o modificare in blocco elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="use-the-cloud-adoption-plan"></a>Usare il piano di adozione del cloud

Il piano di adozione del cloud organizza le attività in base al tipo di attività:

- **EPICS**: un' *epopea* rappresenta una fase complessiva del ciclo di vita dell'adozione del cloud.
- **Funzionalità**: le funzionalità vengono usate per organizzare obiettivi specifici all'interno di ogni fase. Ad esempio, la migrazione di un carico di lavoro specifico è una funzionalità.
- **Storie utente**: il gruppo storie utente lavora in raccolte logiche di attività in base a un obiettivo specifico.
- **Attività**: le attività sono le operazioni effettive da eseguire.

A ogni livello, le attività vengono sequenziate in base alle dipendenze. Le attività sono collegate agli articoli nel Framework di adozione del cloud per chiarire l'obiettivo o l'attività.

La visualizzazione più chiara del piano di adozione del cloud deriva dalla visualizzazione del backlog **Epic** . Per informazioni sul passaggio alla visualizzazione del backlog **Epic** , vedere l'articolo sulla [visualizzazione di un backlog](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops#view-a-backlog-or-portfolio-backlog). Da questa visualizzazione è facile pianificare e gestire il lavoro necessario per completare la fase corrente del ciclo di vita dell'adozione.

> [!NOTE]
> Lo stato corrente del piano di adozione del cloud è incentrato principalmente sulle attività di migrazione. Le attività correlate a governance, innovazione o operazioni devono essere popolate manualmente.

## <a name="align-the-cloud-adoption-plan"></a>Allinea il piano di adozione del cloud

Le pagine di panoramica per la strategia e le fasi di pianificazione del ciclo di vita dell'adozione del cloud fanno riferimento al [modello di pianificazione e strategia del Framework di adozione del cloud](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx). Questo modello organizza le decisioni e i punti dati che allineano il modello per il piano di adozione del cloud con i piani specifici per l'adozione. Se non è già stato fatto, potrebbe essere necessario completare gli esercizi correlati alla [strategia](../strategy/index.md) e alla [pianificazione](../plan/index.md) prima di allineare il nuovo progetto.

Gli articoli seguenti supportano l'allineamento del piano di adozione del cloud:

- [Carichi di lavoro](./workloads.md): allineare le funzionalità all'interno del migrazione cloud Epic per acquisire ogni carico di lavoro da migrare o modernizzare. È possibile aggiungere e modificare tali funzionalità per acquisire il lavoro necessario per eseguire la migrazione dei primi 10 carichi di lavoro.
- [Asset](./assets.md): ogni asset (macchina virtuale, applicazione o dati) è rappresentato dalle storie utente in ogni carico di lavoro. È possibile aggiungere e modificare tali storie utente per allinearle alla propria azienda digitale.
- [Razionalizzazione](./review-rationalization.md): quando viene definito ogni carico di lavoro, è possibile che vengano contestate le ipotesi iniziali relative al carico di lavoro. Questo può comportare modifiche alle attività in ogni asset.
- [Creare i piani di rilascio](./iteration-paths.md): i percorsi di iterazione stabiliscono i piani di rilascio allineando le attività con diverse versioni e iterazioni.
- [Stabiliscono sequenze temporali](./timelines.md): la definizione di date di inizio e di fine per ogni iterazione crea una sequenza temporale per gestire il progetto globale.

Questi cinque articoli sono utili per ogni attività di allineamento necessaria per iniziare a gestire le attività di adozione. Il passaggio successivo consente di iniziare l'esercizio di allineamento.

## <a name="next-steps"></a>Passaggi successivi

Avviare l'allineamento del progetto del piano [definendo e assegnando priorità ai carichi di lavoro](./workloads.md).

> [!div class="nextstepaction"]
> [Definire e assegnare priorità ai carichi di lavoro](./workloads.md)
