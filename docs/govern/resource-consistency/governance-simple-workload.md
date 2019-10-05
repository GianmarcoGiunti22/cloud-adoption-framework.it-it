---
title: progettazione della governance per un carico di lavoro semplice
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Indicazioni per la configurazione dei controlli di governance di Azure per consentire a un utente di distribuire un carico di lavoro semplice.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9a64a069dcebb12cf550f697561b76903e6d01bf
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967352"
---
# <a name="governance-design-for-a-simple-workload"></a>progettazione della governance per un carico di lavoro semplice

L'obiettivo di questa guida è illustrare il processo di progettazione di un modello di governance delle risorse in Azure per supportare un solo team e un carico di lavoro semplice. Verranno esaminati alcuni ipotetici requisiti di governance, quindi verranno illustrate diverse implementazioni di esempio che soddisfano tali requisiti.

Nella fase di adozione iniziale, l'obiettivo è distribuire un carico di lavoro semplice in Azure. Ne derivano i requisiti seguenti:

- Gestione delle identità per un singolo **proprietario del carico di lavoro** responsabile della distribuzione e della gestione del carico di lavoro semplice. Il proprietario del carico di lavoro necessita di autorizzazioni per creare, leggere, aggiornare ed eliminare risorse, nonché dell'autorizzazione a delegare questi diritti ad altri utenti nel sistema di gestione delle identità.
- Gestire tutte le risorse per il carico di lavoro semplice come un'unica unità di gestione.

## <a name="licensing-azure"></a>Licenze di Azure

Prima di iniziare a progettare il modello di governance, è importante capire come avviene la concessione in licenza di Azure, Questo perché gli account amministrativi associati alla licenza di Azure hanno il massimo livello di accesso alle risorse di Azure. Questi account amministrativi costituiscono la base del modello di governance.

> [!NOTE]
> Se l'organizzazione ha già un [Contratto Enterprise Microsoft](https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx) che non include Azure, è possibile aggiungere Azure assumendo un impegno monetario iniziale. Per altre informazioni, vedere [Licenze di Azure per l'azienda](https://azure.microsoft.com/pricing/enterprise-agreement).

Quando Azure è stato aggiunto al Contratto Enterprise dell'organizzazione, a questa è stato chiesto di creare un **account Azure**. Durante il processo di creazione dell'account, sono stati creati un **proprietario dell'account Azure** e un tenant di Azure Active Directory (Azure AD) con un account di **amministratore globale**. Un tenant di Azure AD è un costrutto logico che rappresenta un'istanza sicura e dedicata di Azure AD.

account ![Azure con Azure account manager e Azure AD amministratore globale @ no__t-1*Figura 1-un account Azure con un account manager e Azure ad amministratore globale.*

## <a name="identity-management"></a>Gestione delle identità

Azure considera attendibile solo [Azure AD](https://docs.microsoft.com/azure/active-directory) per autenticare gli utenti e autorizzare l'accesso degli utenti alle risorse, quindi Azure AD è il sistema di gestione delle identità. L'amministratore globale di Azure AD ha il livello massimo di autorizzazioni e può eseguire tutte le azioni relative all'identità, incluse la creazione di utenti e l'assegnazione di autorizzazioni.

Il requisito è la gestione delle identità per un singolo **proprietario del carico di lavoro** responsabile della distribuzione e della gestione del carico di lavoro semplice. Il proprietario del carico di lavoro necessita di autorizzazioni per creare, leggere, aggiornare ed eliminare risorse, nonché dell'autorizzazione a delegare questi diritti ad altri utenti nel sistema di gestione delle identità.

L'amministratore globale di Azure AD creerà l'account del **proprietario del carico di lavoro** per il proprietario del carico di lavoro:

![The Azure AD amministratore globale crea l'account proprietario del carico di lavoro @ no__t-1*Figura 2-l'amministratore di Azure ad globale crea l'account utente del proprietario del carico di lavoro.*

Non è possibile assegnare autorizzazioni di accesso alle risorse fino a quando questo utente non viene aggiunto a una **sottoscrizione**, quindi questa operazione verrà eseguita nelle prossime due sezioni.

## <a name="resource-management-scope"></a>Ambito di gestione delle risorse

Con l'aumento del numero di risorse distribuite dall'organizzazione, cresce anche la complessità della governance di tali risorse. Azure implementa una gerarchia di contenitori logica per consentire all'organizzazione di gestire le risorse in gruppi a vari livelli di granularità, noti anche come **ambito**.

Il livello massimo dell'ambito di gestione delle risorse è il livello **sottoscrizione**. La sottoscrizione viene creata dal **proprietario dell'account** Azure, che stabilisce l'impegno finanziario ed è responsabile del pagamento di tutte le risorse di Azure associate alla sottoscrizione:

Il proprietario dell'account di Azure ![The crea una sottoscrizione @ no__t-1*Figura 3: il proprietario dell'account Azure crea una sottoscrizione.*

Quando viene creata la sottoscrizione, il **proprietario dell'account Azure** associa alla sottoscrizione un tenant di Azure AD che viene usato per l'autenticazione e l'autorizzazione degli utenti:

il proprietario dell'account di Azure ![The associa il tenant Azure AD alla sottoscrizione @ no__t-1*Figura 4: il proprietario dell'account Azure associa il tenant Azure ad alla sottoscrizione.*

Si sarà notato che attualmente non c'è alcun utente associato alla sottoscrizione; ciò significa che nessuno è autorizzato a gestire le risorse. In realtà, il **proprietario dell'account** è il proprietario della sottoscrizione ed è autorizzato a eseguire qualsiasi azione su una risorsa della sottoscrizione. In termini pratici, il **proprietario dell'account** sarà tuttavia molto probabilmente un responsabile della divisione finanziaria dell'organizzazione e non si occuperà delle operazioni di creazione, lettura, aggiornamento ed eliminazione delle risorse; tali attività saranno svolte dal **proprietario del carico di lavoro**. È quindi necessario aggiungere il **proprietario del carico di lavoro** alla sottoscrizione e assegnare le autorizzazioni.

Essendo l'unico utente attualmente autorizzato ad aggiungere il **proprietario del carico di lavoro** alla sottoscrizione, il **proprietario dell'account** aggiungerà il **proprietario del carico di lavoro** alla sottoscrizione:

il proprietario dell'account di Azure ![The aggiunge il * * proprietario del carico di lavoro * * alla sottoscrizione @ no__t-1*Figura 5: il proprietario dell'account Azure aggiunge il proprietario del carico di lavoro alla sottoscrizione.*

Il **proprietario dell'account** Azure concede le autorizzazioni al **proprietario del carico di lavoro** assegnando un [ruolo di controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control). Il ruolo di controllo degli accessi in base al ruolo specifica un insieme di autorizzazioni assegnate al **proprietario del carico di lavoro** per un singolo tipo di risorsa o un insieme di tipi di risorsa.

Si noti che in questo esempio il **proprietario dell'account** ha assegnato il ruolo di [proprietario **predefinito**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner):

![The * * proprietario del carico di lavoro * * è stato assegnato il ruolo proprietario predefinito @ no__t-1*Figura 6-al proprietario del carico di lavoro è stato assegnato il ruolo proprietario predefinito.*

Il ruolo di **proprietario** predefinito concede tutte le autorizzazioni al **proprietario del carico di lavoro** nell'ambito della sottoscrizione.

> [!IMPORTANT]
> Il **proprietario dell'account** Azure è responsabile dell'impegno finanziario associato alla sottoscrizione, ma il proprietario del **carico di lavoro** ha le stesse autorizzazioni. Il **proprietario dell'account** deve considerare il **proprietario del carico di lavoro** affidabile per la distribuzione delle risorse che rientrano nel budget della sottoscrizione.

Il livello successivo dell'ambito di gestione è il livello **risorsa di gruppo**. Un gruppo di risorse è un contenitore logico per le risorse. Le operazioni a livello di gruppo di risorse si applicano a tutte le risorse di un gruppo. È anche importante notare che le autorizzazioni per ogni utente vengono ereditate dal livello superiore successivo, a meno che non vengano esplicitamente modificate in quell'ambito.

Per spiegare questo concetto, di seguito è illustrato cosa accade quando il **proprietario del carico di lavoro** crea un gruppo di risorse:

![The * * proprietario del carico di lavoro * * crea un gruppo di risorse @ no__t-1*Figura 7-il proprietario del carico di lavoro crea un gruppo di risorse ed eredita il ruolo proprietario predefinito nell'ambito del gruppo di risorse.*

Il ruolo di **proprietario** predefinito concede tutte le autorizzazioni al **proprietario del carico di lavoro** nell'ambito del gruppo di risorse. Come accennato in precedenza, questo ruolo viene ereditato dal livello di sottoscrizione. Se a questo utente è assegnato un ruolo diverso in questo ambito, questo ruolo sarà applicabile solo a questo ambito.

Il livello più basso dell'ambito di gestione è il livello **risorsa**. Le operazioni a livello di risorsa si applicano solo alla risorsa stessa. Le autorizzazioni a livello di risorsa vengono ereditate dall'ambito del gruppo di risorse. Se ad esempio il **proprietario del carico di lavoro** distribuisce una [rete virtuale](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) nel gruppo di risorse:

![The * * proprietario del carico di lavoro * * crea una risorsa @ no__t-1*Figura 8-il proprietario del carico di lavoro crea una risorsa ed eredita il ruolo proprietario incorporato nell'ambito della risorsa.*

Il **proprietario del carico di lavoro** eredita il ruolo di proprietario nell'ambito della risorsa, ovvero ha tutte le autorizzazioni per la rete virtuale.

## <a name="implementing-the-basic-resource-access-management-model"></a>Implementazione di un modello di base per la gestione dell'accesso alle risorse

A questo punto viene illustrato come implementare il modello di governance progettato in precedenza.

Per iniziare, l'organizzazione richiede un account Azure. Se l'organizzazione ha già un [Contratto Enterprise Microsoft](https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx) che non include Azure, è possibile aggiungere Azure assumendo un impegno monetario iniziale. Per altre informazioni, vedere [Licenze di Azure per l'azienda](https://azure.microsoft.com/pricing/enterprise-agreement).

Quando viene creato l'account Azure, è necessario specificare una persona dell'organizzazione che sarà il **proprietario dell'account Azure**. Per impostazione predefinita, viene quindi creato un tenant Azure Active Directory (Azure AD). Il **proprietario dell'account** Azure deve creare l'[account utente](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory) per la persona dell'organizzazione che sarà il **proprietario del carico di lavoro**.

Il **proprietario dell'account** Azure deve quindi [creare una sottoscrizione](https://docs.microsoft.com/partner-center/create-a-new-subscription) alla quale dovrà essere [associato il tenant Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).

Dopo aver creato la sottoscrizione e aver associato il tenant Azure AD, è possibile [aggiungere il **proprietario del carico di lavoro** alla sottoscrizione con il ruolo di **proprietario** predefinito](https://docs.microsoft.com/azure/billing/billing-add-change-azure-subscription-administrator#to-assign-a-user-as-an-administrator).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire un carico di lavoro di base in Azure](../../infrastructure/virtual-machines/basic-workload.md)
> [!div class="nextstepaction"]
> [Informazioni sull'accesso alle risorse per più team](./governance-multiple-teams.md)
