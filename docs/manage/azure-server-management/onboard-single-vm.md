---
title: Abilitare Server Management Services in una singola macchina virtuale per la valutazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Abilitare Server Management Services in una singola macchina virtuale per la valutazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7ee8cab09fc5ad875240a10d7fe6f632d91432c9
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751645"
---
# <a name="enable-server-management-services-on-a-single-vm-for-evaluation"></a>Abilitare Server Management Services in una singola macchina virtuale per la valutazione

Informazioni su come abilitare i servizi di gestione server in una singola macchina virtuale per la valutazione.

> [!NOTE]
> Creare l' [area di lavoro log Analytics richiesta e l'account di automazione di Azure](./prerequisites.md#create-a-workspace-and-automation-account) prima di implementare i servizi di gestione di Azure in una macchina virtuale.

L'onboarding dei servizi di gestione del server di Azure a singole macchine virtuali nell'portale di Azure è semplice. Prima di eseguire l'onboarding, è possibile acquisire familiarità con questi servizi. Quando si seleziona un'istanza di macchina virtuale, tutte le soluzioni nell'elenco di [strumenti e servizi di gestione](./tools-services.md) vengono visualizzate nel menu **operazioni** o **monitoraggio** . Si seleziona una soluzione e si segue la procedura guidata per l'onboarding.

![Screenshot delle impostazioni della macchina virtuale nella portale di Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Risorse correlate

Per ulteriori informazioni su come eseguire l'onboarding di queste soluzioni in singole macchine virtuali, vedere:

- [Caricare le soluzioni di Gestione aggiornamenti, Rilevamento modifiche e inventario dalla macchina virtuale di Azure](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-vm)
- [Caricare il monitoraggio di Azure per le macchine virtuali](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come usare i criteri di Azure per caricare le macchine virtuali di Azure su larga scala.

> [!div class="nextstepaction"]
> [Configurare i servizi di gestione di Azure per una sottoscrizione](./onboard-at-scale.md)
