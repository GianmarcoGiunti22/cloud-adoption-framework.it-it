---
title: Processi per la conformità ai criteri della Baseline di identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processi per la conformità ai criteri della Baseline di identità
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6b92072ed182eefc596ab446638a87b4fd560080
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566207"
---
# <a name="identity-baseline-policy-compliance-processes"></a>Processi per la conformità ai criteri della Baseline di identità

Questo articolo illustra un approccio ai processi per la conformità ai criteri che regolano la [Baseline di identità](./index.md). Una governance efficace dell'identità inizia con processi manuali ricorrenti che guidano l'adozione di criteri di identità e le revisioni. Questo richiede il coinvolgimento regolare del team di governance del cloud e delle aziende interessate e degli stakeholder IT per rivedere e aggiornare i criteri e garantire la conformità ai criteri. Inoltre, molti processi di applicazione e di monitoraggio continuo possono essere automatizzati o eseguiti con strumenti per ridurre il sovraccarico di governance e consentire una risposta più rapida alla deviazione dai criteri.

## <a name="planning-review-and-reporting-processes"></a>Pianificazione, revisione e creazione di report per i processi

Gli strumenti di gestione delle identità offrono caratteristiche e funzionalità che semplificano notevolmente il controllo di accesso e la gestione dell'utente all'interno di una distribuzione cloud. Tuttavia, richiedono anche processi e criteri ben congegnati per supportare gli obiettivi dell'organizzazione. Il set seguente contiene esempi di processi comunemente coinvolti nella disciplina Baseline di identità. Usare questi esempi come punto di partenza per la pianificazione di processi che consentono di continuare ad aggiornare i criteri di identità in base alle modifiche dell'azienda e ai feedback da parte del team IT incaricato di concretizzare le indicazioni sulla governance.

**Valutazione e pianificazione iniziali del rischio:** Nell'ambito dell'adozione iniziale della disciplina di base di identità, identificare i rischi e le tolleranze aziendali principali correlati alla gestione delle identità cloud. Usare queste informazioni per discutere di rischi tecnici specifici con i membri del reparto IT e del team per la gestione delle identità, in modo da poter sviluppare un set di base relativo ai criteri di sicurezza per attenuare tali rischi e per stabilire la strategia di governance iniziale.

**Pianificazione della distribuzione:** Prima di qualsiasi distribuzione, esaminare le esigenze di accesso per tutti i carichi di lavoro e sviluppare una strategia di controllo di accesso che sia allineata ai criteri di identità aziendali stabiliti. Documentare eventuali gap tra esigenze e criteri correnti per determinare se sia necessario aggiornare i criteri e modificarli se necessario.

**Test di distribuzione:** Come parte della distribuzione, il team di governance del cloud, in collaborazione con i team IT responsabili dei servizi di identità, sarà responsabile della revisione della distribuzione per convalidare la conformità dei criteri di identità.

**Pianificazione annuale:** Su base annuale, eseguire una revisione di alto livello della strategia di gestione delle identità. Esplorare le modifiche pianificate per l'ambiente dei servizi di identità e le strategie aggiornate di adozione del cloud per identificare il potenziale aumento del rischio o se sia necessario modificare i modelli di infrastruttura delle identità correnti. È consigliabile usare questo momento anche per esaminare le più recenti procedure consigliate riguardo la Gestione delle identità, per integrarle ai criteri e ai processi di revisione.

**Pianificazione trimestrale:** Ogni trimestre esegue una revisione generale dei dati di controllo delle identità e degli accessi e soddisfa i team di adozione del cloud per identificare eventuali nuovi rischi o requisiti operativi che richiederebbero aggiornamenti ai criteri di identità o alle modifiche nel controllo di accesso strategia.

Questo processo di pianificazione è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud per i gap della conoscenza correlati a criteri nuovi o mutevoli e a rischi correlati all'identità. Invitare il personale IT pertinente a partecipare alle attività di verifica e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

Formazione **e formazione:** Con cadenza semestrale, è possibile offrire sessioni di formazione per assicurarsi che il personale IT e gli sviluppatori siano aggiornati sui requisiti di criteri di identità più recenti. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione, materiale sussidiario o altre risorse di training per assicurarsi che siano in linea con le istruzioni dei criteri aziendali più recenti.

**Verifiche mensili per il controllo e la creazione di report:** Su base mensile, eseguire un controllo su tutte le distribuzioni cloud per assicurare l'allineamento continuo con i criteri di identità. Usare questa verifica per controllare l'accesso degli utenti in confronto alle modifiche dell'azienda per assicurarsi che gli utenti possano accedere correttamente alle risorse cloud e garantire che vengano seguite le strategie di accesso, ad esempio il controllo degli accessi in base al ruolo, in modo coerente. Identificare gli account con privilegi e documentarne lo scopo. Questo processo di revisione genera un report per il team di strategia cloud e ogni team di adozione del cloud che illustra in dettaglio la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

## <a name="processes-for-ongoing-monitoring"></a>Processi per il monitoraggio continuo

La determinazione del buon esito della strategia di governance delle identità dipende dalla visibilità dello stato attuale e passato del sistema delle identità. Senza la possibilità di analizzare le metriche rilevanti per la distribuzione su cloud e i dati pertinenti, non è possibile identificare cambiamenti nei rischi o rilevare violazioni delle tolleranze ai rischi. I processi di governance in corso illustrati in precedenza richiedono dati di qualità per garantire che i criteri possano essere modificati per supportare le mutevoli esigenze dell'azienda.

Verificare che i team IT abbiano implementato sistemi di monitoraggio automatizzati per i servizi delle identità che consentono di acquisire i dati di log e controllo rilevanti necessari per valutare i rischi. Essere proattivi nel monitoraggio di questi sistemi garantisce la rapida individuazione e mitigazione di potenziali violazioni di criteri e assicura che le eventuali modifiche alla propria infrastruttura delle identità si rifletta sulla strategia di monitoraggio.

## <a name="violation-triggers-and-enforcement-actions"></a>Trigger per le violazioni e azioni di imposizione

Le violazioni dei criteri di identità possono comportare l'accesso non autorizzato ai dati sensibili e causare gravi interruzioni di servizi e applicazioni di importanza cruciale. Quando vengono rilevate violazioni, si devono intraprendere azioni per riallinearsi il prima possibile ai criteri. Il team IT può automatizzare la maggior parte delle violazioni di trigger usando gli strumenti descritti in [Identity Baseline toolchain for Azure](./toolchain.md) (Toolchain di Baseline di identità per Azure).

I trigger seguenti e le azioni di applicazione forniscono esempi a cui è possibile fare riferimento quando si pianifica l'uso dei dati di monitoraggio per risolvere le violazioni dei criteri:

- È stata **rilevata un'attività sospetta:** Gli account di accesso utente rilevati da indirizzi IP proxy anonimi, posizioni non note o accessi successivi da posizioni geografiche impossibili potrebbero indicare una potenziale violazione dell'account o un tentativo di accesso dannoso. L'accesso verrà bloccato fino a quando non sarà possibile verificare l'identità dell'utente e la password sarà reimpostata.
- **Credenziali utente perse:** Gli account con nome utente e password persi in Internet verranno disabilitati fino a quando non sarà possibile verificare l'identità dell'utente e la reimpostazione della password.
- Sono stati **rilevati controlli di accesso insufficienti:** Eventuali asset protetti in cui le restrizioni di accesso non soddisfano i requisiti di sicurezza avranno accesso bloccato fino a quando la risorsa non viene messa in conformità.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per istruzioni sull'esecuzione di criteri di gestione cloud in allineamento con i piani di adozione, consultare l'articolo sul miglioramento della disciplina.

> [!div class="nextstepaction"]
> [Miglioramento della disciplina Baseline di identità](./discipline-improvement.md)
