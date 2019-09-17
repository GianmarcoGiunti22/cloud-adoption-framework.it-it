---
title: Abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: e9d5e17e87d79d8d1fdf7239298a973959103a37
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028191"
---
# <a name="enable-management-services-on-a-single-vm-for-evaluation"></a>Abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione

Informazioni su come abilitare i servizi di gestione in un'unica macchina virtuale per la valutazione.

> [!NOTE]
> Creare l' [area di lavoro log Analytics richiesta e l'account di automazione di Azure](./prerequisites.md#create-a-workspace-and-automation-account) prima di caricare le macchine virtuali in servizi di gestione di Azure.

Il caricamento di singole macchine virtuali (VM) nei servizi di gestione del server di Azure è semplice nella portale di Azure. Il portale consente di acquisire familiarità con questi servizi prima di caricarli nelle VM. Quando si seleziona un'istanza di macchina virtuale, tutte le soluzioni descritte nell'elenco degli [strumenti e dei servizi di gestione](./tools-services.md) vengono visualizzate nel menu **operazioni** o nel menu **monitoraggio** . È possibile selezionare ogni soluzione e seguire la procedura guidata per l'onboarding.

![Screenshot delle impostazioni della macchina virtuale nella portale di Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Risorse correlate

Per ulteriori informazioni sull'onboarding di singole macchine virtuali in ogni soluzione, vedere:

- [Caricare le soluzioni di Gestione aggiornamenti, Rilevamento modifiche e inventario dalla macchina virtuale di Azure](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-vm)
- [Caricare il monitoraggio di Azure per la macchina virtuale](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come usare i criteri di Azure per caricare le macchine virtuali di Azure su larga scala.

> [!div class="nextstepaction"]
> [Configurare i servizi di gestione di Azure per una sottoscrizione](./onboard-at-scale.md)
