---
title: Ridimensionamento con più sottoscrizioni di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come eseguire il ridimensionamento con più sottoscrizioni di Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: be35763ea3beeec5977073dab8ef98c2e441b537
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548784"
---
# <a name="scaling-with-multiple-azure-subscriptions"></a>Ridimensionamento con più sottoscrizioni di Azure

Le organizzazioni spesso necessitano di più di una sottoscrizione di Azure in seguito ai limiti delle risorse e ad altre considerazioni sulla governance. È quindi importante avere una strategia per il ridimensionamento delle sottoscrizioni.

## <a name="production-and-nonproduction-workloads"></a>Carichi di lavoro di produzione e non di produzione

Quando si distribuisce il primo carico di lavoro di produzione in Azure, è consigliabile iniziare con due sottoscrizioni: una per l'ambiente di produzione e l'altra per l'ambiente di non produzione (sviluppo/test).

![Un modello di sottoscrizione di base che mostra le chiavi accanto alle caselle con etichetta "produzione" e "non produzione"](../../_images/ready/basic-subscription-model.png)

Questo approccio è consigliato per diversi motivi:

- Azure dispone di offerte di sottoscrizione specifiche per i carichi di lavoro di sviluppo/test. Queste offerte offrono tariffe scontate per i servizi e le licenze di Azure.
- Gli ambienti di produzione e non di produzione avranno probabilmente diversi set di criteri di Azure. L'uso di sottoscrizioni separate semplifica l'applicazione di ogni singolo set di criteri a livello di sottoscrizione.
- Per i test è possibile che alcuni tipi di risorse di Azure siano in una sottoscrizione di sviluppo/test. Con una sottoscrizione separata, è possibile usare questi tipi di risorse senza renderli disponibili nell'ambiente di produzione.
- È possibile usare sottoscrizioni di sviluppo/test come ambienti sandbox isolati. Tali sandbox consentono agli amministratori e agli sviluppatori di creare ed eliminare rapidamente interi set di risorse di Azure. Questo isolamento può anche essere utile ai fini della protezione e della sicurezza dei dati.
- Le soglie di costo accettabili probabilmente variano tra le sottoscrizioni di produzione e quelle di sviluppo/test.

## <a name="other-reasons-for-multiple-subscriptions"></a>Altri motivi per cui usare più sottoscrizioni

Altre situazioni possono richiedere l'uso di sottoscrizioni aggiuntive. Quando si espande l'ambiente cloud, tenere presente quanto segue.

- Le sottoscrizioni hanno limiti diversi per i diversi tipi di risorse. Il numero di reti virtuali in una sottoscrizione, ad esempio, è limitato. Quando una sottoscrizione si avvicina a uno qualsiasi dei relativi limiti, è necessario creare un'altra sottoscrizione e inserire nuove risorse.

  Per altre informazioni, vedere [Sottoscrizione di Azure e limiti, quote e vincoli dei servizi](https://docs.microsoft.com/azure/azure-subscription-service-limits).

- Ogni sottoscrizione può implementare criteri propri per i tipi di risorse distribuibili e le aree supportate.

- Le sottoscrizioni nelle aree del cloud pubblico e nelle aree del cloud sovrane o governative hanno limitazioni diverse. Queste sono spesso basate su livelli diversi di classificazione dei dati tra gli ambienti.

- Se si separano completamente set diversi di utenti per motivi di sicurezza o di conformità, potrebbero essere necessarie sottoscrizioni distinte. Ad esempio, è possibile che le organizzazioni governative nazionali debbano limitare l'accesso ai soli cittadini di una sottoscrizione.

- Sottoscrizioni diverse possono avere tipi diversi di offerte, ognuno con i propri termini e vantaggi.

- Possono esistere problemi di attendibilità tra i proprietari di una sottoscrizione e il proprietario delle risorse da distribuire. L'uso di un'altra sottoscrizione con una proprietà diversa può attenuare questi problemi, tuttavia è necessario considerare anche i problemi di rete e protezione dei dati che si verificano in questa distribuzione.

- Controlli finanziari o geopolitici rigidi possono richiedere accordi finanziari distinti per sottoscrizioni specifiche. Queste preoccupazioni possono includere considerazioni sulla sovranità dei dati, aziende con più filiali o contabilità e fatturazione separate per le business unit in paesi diversi e valute diverse.

- Le risorse di Azure create con il modello di distribuzione classica devono essere isolate nella relativa sottoscrizione. La sicurezza per le risorse classiche è diversa da quella delle risorse distribuite tramite Azure Resource Manager. I criteri di Azure non possono essere applicati alle risorse classiche.

- Gli amministratori del servizio che usano le risorse classiche hanno le stesse autorizzazioni dei proprietari con controllo degli accessi in base al ruolo di una sottoscrizione. È difficile limitare sufficientemente l'accesso di tali amministratori dei servizi in una sottoscrizione che combina risorse classiche e risorse di Resource Manager.

È anche possibile scegliere di creare sottoscrizioni aggiuntive per altri motivi aziendali o tecnici specifici dell'organizzazione. Si potrebbe incorrere in costi aggiuntivi per i dati in ingresso e in uscita tra le sottoscrizioni,

È possibile spostare molti tipi di risorse da una sottoscrizione a un'altra o usare distribuzioni automatizzate per eseguire la migrazione delle risorse a un'altra sottoscrizione. Per altre informazioni, vedere [Spostare le risorse di Azure in un altro gruppo di risorse o in un'altra sottoscrizione](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="managing-multiple-subscriptions"></a>Gestione di più sottoscrizioni

Se si dispone solo di poche sottoscrizioni, è relativamente semplice gestirle in modo indipendente. Ma se si dispone di numerose sottoscrizioni, è consigliabile considerare la possibilità di creare una gerarchia di gruppi di gestione per semplificare la gestione delle sottoscrizioni e delle risorse.

I gruppi di gestione consentono di gestire in modo efficiente l'accesso, i criteri e la conformità per le sottoscrizioni di un'organizzazione. Ogni gruppo di gestione è un contenitore per una o più sottoscrizioni.

I gruppi di gestione sono disposti in un'unica gerarchia. Si definisce questa gerarchia nel tenant di Azure Active Directory (Azure AD) per allinearsi alla struttura e alle esigenze dell'organizzazione. Il primo livello è denominato *gruppo di gestione radice*. È possibile definire fino a sei livelli di gruppi di gestione nella gerarchia. Ogni sottoscrizione è contenuta in un solo gruppo di gestione.

Azure offre quattro livelli relativi all'ambito di gestione: gruppi di gestione, sottoscrizioni, gruppi di risorse e risorse. Tutti gli accessi o i criteri applicati a un livello della gerarchia vengono ereditati dai livelli sottostanti. Il proprietario di una risorsa o di una sottoscrizione non può modificare un criterio ereditato. Questa limitazione contribuisce a migliorare la governance.

> [!NOTE]
> Si noti che l'ereditarietà tag non è attualmente disponibile, ma diventerà disponibile a breve.

Basandosi su questo modello di ereditarietà, è possibile disporre le sottoscrizioni nella gerarchia in modo che ogni sottoscrizione segua i criteri e i controlli di sicurezza appropriati.

![I quattro livelli di ambito per organizzare le risorse di Azure](../../ready/azure-setup-guide/media/organize-resources/scope-levels.png)

Qualsiasi assegnazione di accesso o criteri nel gruppo di gestione radice viene applicata a tutte le risorse all'interno della directory. Valutare attentamente gli elementi definiti in questo ambito. Includere solo le assegnazioni che è necessario avere.

Quando si definisce inizialmente la gerarchia di gruppi di gestione, è necessario innanzitutto creare il gruppo di gestione radice. È quindi possibile spostare tutte le sottoscrizioni esistenti nella directory nel gruppo di gestione radice. Le nuove sottoscrizioni vengono sempre create nel gruppo di gestione radice. In seguito sarà possibile spostarle in un altro gruppo di gestione.

Quando si sposta una sottoscrizione in un gruppo di gestione esistente, i criteri e le assegnazioni di ruoli vengono ereditati dalla gerarchia di gruppi di gestione soprastante. Dopo aver stabilito più sottoscrizioni per i carichi di lavoro di Azure, è necessario creare sottoscrizioni aggiuntive per contenere i servizi di Azure condivisi da altre sottoscrizioni.

![Esempio di gerarchia di gruppi di gestione](../../_images/ready/management-group-hierarchy.png)

Per altre informazioni, vedere [Organizzare le risorse con i gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups).

## <a name="tips-for-creating-new-subscriptions"></a>Suggerimenti per la creazione di nuove sottoscrizioni

- Identificare chi sarà responsabile della creazione di nuove sottoscrizioni.
- Decidere quali risorse saranno disponibili per impostazione predefinita in una sottoscrizione.
- Decidere quali devono essere tutte le sottoscrizioni standard. Tra gli elementi da considerare sono inclusi l'accesso basato sul controllo degli accessi in base al ruolo, i criteri, i tag e le risorse dell'infrastruttura.
- Se possibile, [usare un'entità servizio](https://docs.microsoft.com/azure/azure-resource-manager/grant-access-to-create-subscription) per creare nuove sottoscrizioni. Definire un gruppo di sicurezza in grado di richiedere nuove sottoscrizioni tramite un flusso di lavoro automatizzato.
- Se si è un cliente Enterprise Agreement (EA), chiedere al supporto tecnico di Azure di bloccare la creazione di sottoscrizioni non EA per l'organizzazione.

## <a name="related-resources"></a>Risorse correlate

- [Concetti fondamentali di Azure](./fundamental-concepts.md).
- [Organizzare le risorse con i gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups).
- [Elevare i privilegi di accesso per gestire tutte le sottoscrizioni e i gruppi di gestione di Azure](https://docs.microsoft.com/azure/role-based-access-control/elevate-access-global-admin).
- [Spostare le risorse di Azure in un altro gruppo di risorse o in un'altra sottoscrizione](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="next-steps"></a>Passaggi successivi

Esaminare le [convenzioni di denominazione e assegnazione di tag consigliate](./naming-and-tagging.md) da seguire durante la distribuzione delle risorse di Azure.

> [!div class="nextstepaction"]
> [Convenzioni di denominazione e assegnazione di tag consigliate](./naming-and-tagging.md)
