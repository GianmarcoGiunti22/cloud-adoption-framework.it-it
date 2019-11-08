---
title: Istruzioni dei criteri di esempio della Baseline di identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Istruzioni dei criteri di esempio della Baseline di identità
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 118a111ae787e58d1f50704216e921a4df43501e
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753025"
---
# <a name="identity-baseline-sample-policy-statements"></a>Istruzioni dei criteri di esempio della Baseline di identità

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà indirizzato da questo criterio.
- **Istruzione per i criteri:** Una chiara spiegazione di riepilogo dei requisiti dei criteri.
- **Opzioni di progettazione:** Raccomandazioni di utilità pratica, specifiche o altre istruzioni che i team IT e gli sviluppatori possono usare per l'implementazione dei criteri.

Le istruzioni dei criteri di esempio seguenti riguardano i rischi aziendali comuni correlati all'identità. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="lack-of-access-controls"></a>Mancanza di controlli di accesso

**Rischio tecnico:** Le impostazioni di controllo degli accessi insufficienti o ad hoc possono causare il rischio di accesso non autorizzato a risorse sensibili o cruciali.

**Istruzione per i criteri:** Tutti gli asset distribuiti nel cloud devono essere controllati usando identità e ruoli approvati dai criteri di governance correnti.

**Opzioni di progettazione potenziali:** [Azure Active Directory l'accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) è il meccanismo di controllo di accesso predefinito in Azure.

## <a name="overprovisioned-access"></a>Accesso con provisioning eccessivo

**Rischio tecnico:** Gli utenti e i gruppi che controllano le risorse che esulano dalla loro area di responsabilità possono causare modifiche non autorizzate che portano a interruzioni o vulnerabilità della sicurezza.

**Istruzione per i criteri:** Verranno implementati i criteri seguenti:

- Un modello di accesso con privilegi minimi verrà applicato a tutte le risorse necessarie per le applicazioni di importanza strategica o i dati protetti.
- Le autorizzazioni elevate devono essere un'eccezione e tali eccezioni devono essere registrate con il team di governance del cloud. Le eccezioni verranno controllate regolarmente.

**Possibili opzioni di progettazione:** Consultare le [procedure consigliate](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices) per la gestione delle identità di Azure per implementare una strategia di controllo degli accessi in base al ruolo che limita l'accesso in base ai principi di sicurezza che [devono](https://wikipedia.org/wiki/Need_to_know) essere appreso e con [privilegi minimi](https://wikipedia.org/wiki/Principle_of_least_privilege) .

## <a name="lack-of-shared-management-accounts-between-on-premises-and-the-cloud"></a>Mancanza di account di gestione condivisi tra locali e cloud

**Rischio tecnico:** La gestione IT o il personale amministrativo con account in locale Active Directory potrebbe non avere accesso sufficiente alle risorse cloud potrebbe non essere in grado di risolvere in modo efficiente i problemi operativi o di sicurezza.

**Istruzione per i criteri:** Tutti i gruppi nell'infrastruttura Active Directory locale con privilegi elevati devono essere mappati a un ruolo approvato controllo degli accessi in base al ruolo.

**Possibili opzioni di progettazione:** Implementare una soluzione di gestione delle identità ibrida tra la Azure Active Directory basata sul cloud e l'Active Directory locale e aggiungere i gruppi locali necessari ai ruoli RBAC necessari per svolgere il proprio lavoro.

## <a name="weak-authentication-mechanisms"></a>Meccanismi di autenticazione debole

**Rischio tecnico:** I sistemi di gestione delle identità con metodi di autenticazione utente con protezione insufficiente, ad esempio combinazioni di utente/password di base, possono causare password compromesse o violate, con un rischio di accesso non autorizzato ai sistemi cloud protetti.

**Istruzione per i criteri:** Tutti gli account sono necessari per accedere alle risorse protette usando un metodo di autenticazione a più fattori.

**Possibili opzioni di progettazione:** Per Azure Active Directory, implementare [Azure multi-factor authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) come parte del processo di autorizzazione dell'utente.

## <a name="isolated-identity-providers"></a>Provider di identità isolata

**Rischio tecnico:** I provider di identità incompatibili possono determinare l'impossibilità di condividere risorse o servizi con clienti o altri partner commerciali.

**Istruzione per i criteri:** La distribuzione di qualsiasi applicazione che richiede l'autenticazione del cliente deve usare un provider di identità approvato compatibile con il provider di identità primario per gli utenti interni.

**Possibili opzioni di progettazione:** Implementare la [Federazione con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed) tra i provider di identità interni e dei clienti oppure usare [Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

## <a name="identity-reviews"></a>Revisione di identità

**Rischio tecnico:** Con il passare del tempo, l'aggiunta di nuove distribuzioni cloud o altri problemi di sicurezza può comportare un aumento dei rischi di accesso non autorizzato alle risorse protette.

**Istruzione per i criteri:** I processi di governance del cloud devono includere la revisione trimestrale con i team di gestione delle identità per identificare gli attori dannosi o i modelli di utilizzo che devono essere evitati dalla configurazione degli asset

**Possibili opzioni di progettazione:** Stabilire una riunione trimestrale di revisione della sicurezza che includa i membri del team di governance e il personale IT responsabile della gestione dei servizi di identità. Esaminare i dati e le metriche di sicurezza esistenti per stabilire i gap nei criteri e negli strumenti di gestione delle identità correnti e aggiornare i criteri per correggere eventuali nuovi rischi.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi indicati in questo articolo come punto di partenza per lo sviluppo di criteri per risolvere i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

Per iniziare a sviluppare le proprie istruzioni di criteri personalizzate correlate alla Baseline di identità, scaricare il [modello Baseline di identità](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Baseline di identità.

> [!div class="nextstepaction"]
> [Stabilire i processi di conformità ai criteri](./compliance-processes.md)
