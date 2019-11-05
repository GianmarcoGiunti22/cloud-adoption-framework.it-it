---
title: gestione dell'accesso alle risorse in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: "Spiegazione dei costrutti di gestione dell'accesso alle risorse in Azure: Azure Resource Manager, sottoscrizioni, gruppi di risorse e risorse"
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a429aa445a7188a98593ec27892fb6ded8f9eb45
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565983"
---
# <a name="resource-access-management-in-azure"></a>gestione dell'accesso alle risorse in Azure

[Governance cloud](../index.md) delinea le cinque discipline della governance del cloud, che include la gestione delle risorse. [Informazioni sulla governance dell'accesso alle risorse](./index.md) illustra in modo più dettagliato in che modo la gestione dell'accesso alle risorse si integra con la disciplina di gestione delle risorse. Prima di esaminare come si progetta un modello di governance, è importante comprendere i controlli di gestione dell'accesso alle risorse in Azure. La configurazione di questi controlli di gestione dell'accesso alle risorse costituisce la base del modello di governance.

Verrà ora esaminata la distribuzione delle risorse in Azure.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-an-azure-resource"></a>Informazioni sulla risorsa in Azure

In Azure il termine _risorsa_ si riferisce a un'entità gestita da Azure. Ad esempio, le macchine virtuali, le reti virtuali e gli account di archiviazione sono tutte risorse di Azure.

![diagramma di una risorsa](../../_images/govern/design/governance-1-9.png)
*Figura 1-una risorsa.*

## <a name="what-is-an-azure-resource-group"></a>Informazioni sul gruppo di risorse di Azure

Ogni risorsa in Azure deve appartenere a un [gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups). Un gruppo di risorse è semplicemente un costrutto logico che raggruppa più risorse in modo che possano essere gestite come una singola entità _in base al ciclo di vita e alla sicurezza_. Ad esempio, le risorse che condividono un ciclo di vita simile, come le risorse per un'[applicazione a più livelli](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier), possono essere create o eliminate come gruppo. Un altro modo: tutto ciò che è nato insieme, viene gestito insieme e deprecato insieme, viene riunito in un gruppo di risorse.

![diagramma di un gruppo di risorse contenente una risorsa](../../_images/govern/design/governance-1-10.png)
*Figura 2-un gruppo di risorse contiene una risorsa.*

I gruppi di risorse e le risorse in essi contenute sono associati a una **sottoscrizione** di Azure.

## <a name="what-is-an-azure-subscription"></a>Informazioni sulla sottoscrizione di Azure

Una sottoscrizione di Azure è simile a un gruppo di risorse, in quanto si tratta di un costrutto logico che raggruppa i gruppi di risorse e le loro risorse. Una sottoscrizione di Azure è tuttavia anche associata ai controlli usati da Azure Resource Manager. Esaminare Azure Resource Manager per comprendere la sua relazione con una sottoscrizione di Azure.

![diagramma di una sottoscrizione di Azure](../../_images/govern/design/governance-1-11.png)
*Figura 3: una sottoscrizione di Azure.*

## <a name="what-is-azure-resource-manager"></a>Informazioni su Azure Resource Manager

In [Funzionamento di Azure](../../getting-started/what-is-azure.md) si è appreso che Azure include un "front-end" con molti servizi che orchestrano tutte le funzioni di Azure. Uno di questi servizi è [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager), che ospita l'API RESTful usata dai client per gestire le risorse.

![diagramma di Azure Resource Manager](../../_images/govern/design/governance-1-12.png)
*Figura 4-Azure Resource Manager.*

La figura seguente illustra tre client: [PowerShell](https://docs.microsoft.com/powershell/azure/overview), il [portale di Azure](https://portal.azure.com)e l'interfaccia della riga di comando di [Azure](https://docs.microsoft.com/cli/azure):

![diagramma dei client di Azure che si connettono all'API Azure Resource Manager](../../_images/govern/design/governance-1-13.png)
*Figura 5: i client di Azure si connettono all'API restful Azure Resource Manager.*

Anche se questi client si connettono ad Azure Resource Manager usando l'API RESTful, Azure Resource Manager non include funzionalità per gestire direttamente le risorse. La maggior parte dei tipi di risorse in Azure ha invece un proprio [**provider di risorse**](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#terminology).

![i provider di risorse *di azure](../../_images/govern/design/governance-1-14.png)
figura 6-provider di risorse di Azure.*

Quando un client invia una richiesta per gestire una risorsa specifica, Azure Resource Manager si connette al provider di risorse per quel tipo di risorsa per completare la richiesta. Se, ad esempio, un client invia una richiesta per gestire una risorsa macchina virtuale, Azure Resource Manager si connette al provider di risorse **Microsoft.Compute**.

![Azure Resource Manager la connessione al provider di risorse Microsoft. Compute](../../_images/govern/design/governance-1-15.png)
*Figura 7-Azure Resource Manager si connette al provider di risorse **Microsoft. Compute** per gestire la risorsa specificata nella richiesta client.*

Azure Resource Manager richiede al client di specificare un identificatore sia per la sottoscrizione che per il gruppo di risorse per gestire la risorsa macchina virtuale.

Ora che si è appreso come funziona Resource Manager, tornare alla trattazione del modo in cui una sottoscrizione di Azure è associata ai controlli usati da Azure Resource Manager. Prima che qualsiasi richiesta di gestione delle risorse possa essere eseguita da Azure Resource Manager, vengono effettuati alcuni controlli.

Il primo controllo è che una richiesta venga eseguita da un utente convalidato e che Azure Resource Manager abbia una relazione di trust con [Azure Active Directory](https://docs.microsoft.com/azure/active-directory) (Azure AD) perché possa rendere disponibile la funzionalità di identità utente.

![Azure Active Directory](../../_images/govern/design/governance-1-16.png)
*Figura 8-Azure Active Directory.*

Gli utenti di Azure AD sono segmentati in **tenant**. Un tenant è un costrutto logico che rappresenta un'istanza sicura e dedicata di Azure AD, generalmente associata a un'organizzazione. Ogni sottoscrizione è associata a un tenant di Azure AD.

![un tenant di Azure AD associato a una sottoscrizione](../../_images/govern/design/governance-1-17.png)
*Figura 9: un tenant Azure ad associato a una sottoscrizione.*

Per ogni richiesta del client di gestire una risorsa in una specifica sottoscrizione è necessario che l'utente abbia un account nel tenant di Azure AD associato.

Il controllo successivo consiste nel verificare che l'utente abbia autorizzazioni sufficienti per effettuare la richiesta. Le autorizzazioni vengono assegnate agli utenti tramite il [controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control).

![utenti assegnati ai ruoli RBAC](../../_images/govern/design/governance-1-18.png)
*Figura 10. A ogni utente nel tenant vengono assegnati uno o più ruoli RBAC.*

Un ruolo di controllo degli accessi in base al ruolo specifica un insieme di autorizzazioni che un utente può avere per una risorsa specifica. Quando il ruolo viene assegnato all'utente, tali autorizzazioni vengono applicate. Ad esempio, il ruolo di [proprietariopredefinito](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) consente all'utente di eseguire qualsiasi azione su una risorsa.

Il controllo successivo verifica che la richiesta sia consentita nelle impostazioni specificate per i [criteri delle risorse di Azure](https://docs.microsoft.com/azure/governance/policy). I criteri delle risorse di Azure specificano le operazioni consentite per una determinata risorsa. Ad esempio, un criterio delle risorse di Azure può specificare che agli utenti sia consentito distribuire solo un tipo specifico di macchina virtuale.

![criteri delle risorse di Azure](../../_images/govern/design/governance-1-19.png)
*Figura 11. Criteri delle risorse di Azure.*

Il controllo successivo consiste nel verificare che la richiesta non superi un [limite della sottoscrizione di Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits). Ad esempio, ogni sottoscrizione ha un limite di 980 gruppi di risorse. Se viene ricevuta una richiesta di distribuzione di un gruppo di risorse aggiuntivo al raggiungimento del limite, questo viene negato.

![limiti delle risorse di Azure](../../_images/govern/design/governance-1-20.png)
*Figura 12. Limiti delle risorse di Azure.*

Il controllo finale verifica che la richiesta rientri nell'impegno finanziario associato alla sottoscrizione. Se, ad esempio, la richiesta riguarda la distribuzione di una macchina virtuale, Azure Resource Manager verifica che la sottoscrizione contenga informazioni di pagamento sufficienti.

![un impegno finanziario associato a una sottoscrizione](../../_images/govern/design/governance-1-21.png)
*Figura 13. Un impegno finanziario è associato a una sottoscrizione.*

## <a name="summary"></a>Riepilogo

In questo articolo si è appreso come viene gestito l'accesso alle risorse in Azure con Azure Resource Manager.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver compreso come gestire l'accesso alle risorse in Azure, è necessario apprendere come progettare un modello di governance [per un carico di lavoro semplice](./governance-simple-workload.md) o per [più team](./governance-multiple-teams.md) usando questi servizi.

> [!div class="nextstepaction"]
> [Panoramica della governance](../index.md)
