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
ms.openlocfilehash: 22fa26bdf4665584224551015cd4b3277d4755a3
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223768"
---
# <a name="identity-baseline-policy-compliance-processes"></a>Processi per la conformità ai criteri della Baseline di identità

Questo articolo illustra un approccio ai processi per la conformità ai criteri che regolano la [Baseline di identità](./index.md). Una governance efficace dell'identità inizia con processi manuali ricorrenti che guidano l'adozione di criteri di identità e le revisioni. Questo richiede il coinvolgimento regolare del team di governance del cloud e delle aziende interessate e degli stakeholder IT per rivedere e aggiornare i criteri e garantire la conformità ai criteri. Inoltre, molti processi di applicazione e di monitoraggio continuo possono essere automatizzati o eseguiti con strumenti per ridurre il sovraccarico di governance e consentire una risposta più rapida alla deviazione dai criteri.

## <a name="planning-review-and-reporting-processes"></a>Processi di pianificazione, verifica e creazione di report

Gli strumenti di gestione delle identità offrono caratteristiche e funzionalità che semplificano notevolmente il controllo di accesso e la gestione dell'utente all'interno di una distribuzione cloud. Tuttavia, richiedono anche processi e criteri ben congegnati per supportare gli obiettivi dell'organizzazione. Il set seguente contiene esempi di processi comunemente coinvolti nella disciplina Baseline di identità. Usare questi esempi come punto di partenza per la pianificazione di processi che consentono di continuare ad aggiornare i criteri di identità in base alle modifiche dell'azienda e ai feedback da parte del team IT incaricato di concretizzare le indicazioni sulla governance.

**Valutazione e pianificazione iniziali del rischio:** Come parte dell'adozione iniziale della disciplina Baseline di identità, identificare i principali rischi aziendali e le tolleranze correlate alla gestione delle identità nel cloud. Usare queste informazioni per discutere di rischi tecnici specifici con i membri del reparto IT e del team per la gestione delle identità, in modo da poter sviluppare un set di base relativo ai criteri di sicurezza per attenuare tali rischi e per stabilire la strategia di governance iniziale.

**Pianificazione della distribuzione:** Prima di qualsiasi distribuzione, esaminare le esigenze di accesso per tutti i carichi di lavoro e sviluppare una strategia di controllo di accesso che sia allineata ai criteri di identità aziendali stabiliti. Documentare eventuali gap tra esigenze e criteri correnti per determinare se sia necessario aggiornare i criteri e modificarli se necessario.

**Test di distribuzione:** Come parte della distribuzione, il team di governance del cloud, in collaborazione con i team IT responsabili dei servizi di identità, sarà responsabile della revisione della distribuzione per convalidare la conformità dei criteri di identità.

**Pianificazione annuale:** Su base annuale, eseguire una verifica generale della strategia di gestione delle identità. Esplorare le modifiche pianificate per l'ambiente dei servizi di identità e le strategie aggiornate di adozione del cloud per identificare il potenziale aumento del rischio o se sia necessario modificare i modelli di infrastruttura delle identità correnti. È consigliabile usare questo momento anche per esaminare le più recenti procedure consigliate riguardo la Gestione delle identità, per integrarle ai criteri e ai processi di revisione.

**Pianificazione trimestrale**: Ogni trimestre esegue una revisione generale dei dati di controllo delle identità e degli accessi e soddisfa i team di adozione del cloud per identificare eventuali nuovi rischi o requisiti operativi che richiederebbero aggiornamenti ai criteri di identità o alle modifiche nel controllo di accesso strategia.

Questo processo di pianificazione è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud per i gap della conoscenza correlati a criteri nuovi o mutevoli e a rischi correlati all'identità. Invitare il personale IT pertinente a partecipare alle attività di verifica e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

**Formazione e formazione:** Con cadenza semestrale, è possibile offrire sessioni di formazione per assicurarsi che il personale IT e gli sviluppatori siano aggiornati sui requisiti di criteri di identità più recenti. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione, le linee guida o altre risorse di training per assicurarsi che siano in linea con le definizioni dei criteri aziendali più recenti.

**Verifiche mensili per il controllo e la creazione di report:** Su base mensile, eseguire un controllo su tutte le distribuzioni cloud per garantire il costante allineamento con i criteri delle identità. Usare questa verifica per controllare l'accesso degli utenti in confronto alle modifiche dell'azienda per assicurarsi che gli utenti possano accedere correttamente alle risorse cloud e garantire che vengano seguite le strategie di accesso, ad esempio il controllo degli accessi in base al ruolo, in modo coerente. Identificare gli account con privilegi e documentarne lo scopo. Questo processo di revisione genera un report per il team di strategia cloud e ogni team di adozione del cloud che illustra in dettaglio la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

## <a name="ongoing-monitoring-processes"></a>Processi di monitoraggio continuo

La determinazione del buon esito della strategia di governance delle identità dipende dalla visibilità dello stato attuale e passato del sistema delle identità. Senza la possibilità di analizzare le metriche rilevanti per la distribuzione su cloud e i dati pertinenti, non è possibile identificare cambiamenti nei rischi o rilevare violazioni delle tolleranze ai rischi. I processi di governance in corso illustrati in precedenza richiedono dati di qualità per garantire che i criteri possano essere modificati per supportare le mutevoli esigenze dell'azienda.

Verificare che i team IT abbiano implementato sistemi di monitoraggio automatizzati per i servizi delle identità che consentono di acquisire i dati di log e controllo rilevanti necessari per valutare i rischi. Essere proattivi nel monitoraggio di questi sistemi garantisce la rapida individuazione e mitigazione di potenziali violazioni di criteri e assicura che le eventuali modifiche alla propria infrastruttura delle identità si rifletta sulla strategia di monitoraggio.

## <a name="violation-triggers-and-enforcement-actions"></a>Violazione di trigger e azioni di applicazione

Le violazioni dei criteri di identità possono comportare l'accesso non autorizzato ai dati sensibili e causare gravi interruzioni di servizi e applicazioni di importanza cruciale. Quando vengono rilevate violazioni, si devono intraprendere azioni in modo da riallineare i criteri il prima possibile. Il team IT può automatizzare la maggior parte delle violazioni di trigger usando gli strumenti descritti in [Identity Baseline toolchain for Azure](./toolchain.md) (Toolchain di Baseline di identità per Azure).

I trigger seguenti e le azioni di applicazione forniscono esempi a cui è possibile fare riferimento quando si pianifica l'uso dei dati di monitoraggio per risolvere le violazioni dei criteri:

- **È stata rilevata un'attività sospetta:** Gli accessi utente rilevati dalle informazioni degli indirizzi IP proxy anonimi, le posizioni non note o successivi accessi da località geografiche troppo distanti possono indicare una potenziale violazione della sicurezza dell'account o il tentativo di un accesso non autorizzato. L'accesso verrà bloccato fino a quando non sarà possibile verificare l'identità dell'utente e la password sarà reimpostata.
- **Credenziali utente perse:** Un account il cui nome utente e la password sono andati persi in internet verrà disabilitato fino a quando non sarà possibile verificare l'identità dell'utente e la password sarà reimpostata.
- **Sono stati rilevati controlli di accesso insufficienti:** Tutti gli asset protetti in cui le restrizioni all'accesso non soddisfano i requisiti di sicurezza saranno bloccati fino a quando la risorsa non risulta conforme.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per istruzioni sull'esecuzione dei criteri di gestione del cloud in linea con i piani di adozione, vedere l'articolo sul miglioramento della disciplina.

> [!div class="nextstepaction"]
> [Miglioramento della disciplina Baseline di identità](./discipline-improvement.md)
