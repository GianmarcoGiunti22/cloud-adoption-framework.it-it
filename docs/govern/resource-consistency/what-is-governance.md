---
title: Informazioni sulla governance delle risorse cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla governance delle risorse cloud in Azure
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 083b18c0c8c5edc0dc21a198df32e8934929299c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030321"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-cloud-resource-governance"></a>Informazioni sulla governance delle risorse cloud

In che [modo funziona Azure?](../../getting-started/what-is-azure.md)si è appreso che Azure è una raccolta di server e hardware di rete che esegue hardware e software virtualizzato per conto degli utenti. Azure consente agli sviluppatori e ai reparti IT dell'organizzazione di essere agile, semplificando la creazione, la lettura, l'aggiornamento e l'eliminazione delle risorse in base alle esigenze.

Tuttavia, sebbene le risorse non limitate possano rendere gli sviluppatori più agile, possono anche causare costi imprevisti. Un team di sviluppo, ad esempio, potrebbe avere l'approvazione per distribuire un set di risorse per i test, ma potrebbe dimenticarsi di eliminare tali risorse al termine della fase di test. Queste risorse continueranno a accumulare costi anche se non sono più approvate o necessarie.

La soluzione è governance di accesso alle risorse. **Governance** è il processo continuo di gestione, monitoraggio e controllo dell'uso delle risorse di Azure per soddisfare gli obiettivi e i requisiti dell'organizzazione.

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ii94]

<!-- markdownlint-enable MD034 -->

Questi requisiti sono univoci per ogni organizzazione, quindi un approccio per la governance con una dimensione adatta alla governance non è utile. Al contrario, spetta a ogni organizzazione progettare il modello di governance usando due strumenti di governance primari di Azure: il **controllo degli accessi in base al ruolo**e i **criteri delle risorse**.

RBAC definisce i ruoli e i ruoli definiscono le operazioni consentite per ogni utente assegnato a tale ruolo. Il ruolo **proprietario** consente, ad esempio, a tutte le operazioni (creazione, lettura, aggiornamento ed eliminazione) su una risorsa, mentre il ruolo **lettore** consente solo operazioni di lettura. I ruoli possono essere definiti in modo estensivo e applicati a molti tipi di risorse oppure definiti più restrittivi e applicati solo a pochi tipi di risorse.

I criteri delle risorse definiscono le regole per la creazione delle risorse. Un criterio di risorsa, ad esempio, può limitare lo SKU di una macchina virtuale a una determinata dimensione preapprovata. Un altro criterio di risorse potrebbe imporre l'applicazione di un tag per un centro di costo assegnato quando viene effettuata la richiesta per creare la risorsa.

Quando si configurano questi strumenti, è importante bilanciare la governance e l'agilità organizzativa. Quanto più restrittivo è il criterio di governance, minore sarà l'agilità degli sviluppatori e dei ruoli di lavoro IT. Un criterio di governance restrittivo può richiedere più passaggi manuali, ad esempio richiedere a uno sviluppatore di compilare un modulo o inviare un messaggio di posta elettronica a un membro del team di governance per creare manualmente una risorsa. Il team di governance ha una capacità limitata e può diventare un collo di bottiglia, in modo che i team di sviluppo attendano in modo non produttivo le risorse da creare o le risorse non necessarie accumulano costi prima che vengano eliminate.

## <a name="next-steps"></a>Passaggi successivi

Ora che si è compreso il concetto di governance delle risorse cloud, è possibile ottenere altre informazioni sulla gestione dell'accesso alle risorse in Azure.

> [!div class="nextstepaction"]
> [Informazioni sull'accesso alle risorse in Azure](./resource-access-management.md)
