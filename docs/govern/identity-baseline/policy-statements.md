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
ms.openlocfilehash: 39742436ab6c4a176e40ce8188c13cca55f23521
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222125"
---
# <a name="identity-baseline-sample-policy-statements"></a>Istruzioni dei criteri di esempio della Baseline di identità

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio tecnico:** Riepilogo del rischio che verrà risolto da questi criteri.
- **Definizione dei criteri**: Una spiegazione chiara e riepilogativa dei requisiti dei criteri.
- **Opzioni di progettazione**: Suggerimenti pratici, specifiche o altre linee guida che i team IT e gli sviluppatori possono usare quando implementano i criteri.

Le istruzioni dei criteri di esempio seguenti riguardano i rischi aziendali comuni correlati all'identità. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="lack-of-access-controls"></a>Mancanza di controlli di accesso

**Rischio tecnico:** le impostazioni di controllo di accesso insufficienti o ad hoc possono introdurre rischi di accesso non autorizzato alle risorse sensibili o di importanza cruciale.

**Definizione dei criteri**: tutti gli asset distribuiti nel cloud devono essere controllati tramite identità e ruoli approvati da criteri di governance correnti.

**Possibili opzioni di progettazione:** [Accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) è il meccanismo di controllo di accesso predefinito di Azure.

## <a name="overprovisioned-access"></a>Accesso con provisioning eccessivo

**Rischio tecnico:** utenti e gruppi con il controllo delle risorse oltre l'area di responsabilità possono comportare modifiche non autorizzate, vulnerabilità della sicurezza o interruzioni.

**Definizione dei criteri**: verranno implementati i criteri seguenti:

- Un modello di accesso con privilegi minimi verrà applicato a tutte le risorse necessarie per le applicazioni di importanza strategica o i dati protetti.
- Le autorizzazioni elevate devono essere un'eccezione e tali eccezioni devono essere registrate con il team di governance del cloud. Le eccezioni verranno controllate regolarmente.

**Possibili opzioni di progettazione:** Consultare le [procedure consigliate](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices) per la gestione delle identità di Azure per implementare una strategia di controllo degli accessi in base al ruolo che limita l'accesso in base ai principi di sicurezza che [devono](https://wikipedia.org/wiki/Need_to_know) essere appreso e con [privilegi minimi](https://wikipedia.org/wiki/Principle_of_least_privilege) .

## <a name="lack-of-shared-management-accounts-between-on-premises-and-the-cloud"></a>Mancanza di account di gestione condivisi tra locali e cloud

**Rischio tecnico:** la gestione IT o il personale amministrativo con gli account in Active Directory Domain Services locale potrebbero non disporre dei diritti di accesso sufficienti alle risorse del cloud che potrebbero non essere in grado di risolvere efficacemente i problemi operativi e di sicurezza.

**Definizione dei criteri**: tutti i gruppi con privilegi elevati nell'infrastruttura di Active Directory Domain Services locale dovrebbero essere associati a un ruolo di controllo approvato degli accessi in base al ruolo.

**Possibili opzioni di progettazione:** Implementare una soluzione di gestione delle identità ibrida tra la Azure Active Directory basata sul cloud e l'Active Directory locale e aggiungere i gruppi locali necessari ai ruoli RBAC necessari per svolgere il proprio lavoro.

## <a name="weak-authentication-mechanisms"></a>Meccanismi di autenticazione debole

**Rischio tecnico:** sistemi di gestione delle identità con i metodi di autenticazione utente non sufficientemente sicura, ad esempio le combinazioni di base utente/password, possono portare a password compromesse o violate, costituendo un grave rischio di accesso non autorizzato ai sistemi cloud protetti.

**Definizione dei criteri**: Tutti gli account sono necessari per accedere alle risorse protette usando un metodo di autenticazione a più fattori.

**Possibili opzioni di progettazione:** Per Azure Active Directory, implementare [autenticazione a più fattori di Azure](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) come parte del processo di autorizzazione utente.

## <a name="isolated-identity-providers"></a>Provider di identità isolata

**Rischio tecnico:** provider di identità incompatibili possono causare l'impossibilità di condividere risorse o servizi con i clienti e altri partner aziendali.

**Definizione dei criteri**: per la distribuzione di applicazioni che richiedono l'autenticazione del cliente è necessario usare un provider di identità approvato compatibile con il provider di identità primario per gli utenti interni.

**Possibili opzioni di progettazione:** Implementare la [Federazione con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed) tra i provider di identità interni e dei clienti o sfruttare [Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

## <a name="identity-reviews"></a>Revisione di identità

**Rischio tecnico:** Con il passare del tempo, l'aggiunta di nuove distribuzioni cloud o altri problemi di sicurezza può comportare un aumento dei rischi di accesso non autorizzato alle risorse protette.

**Definizione dei criteri**: i processi di Governance cloud devono includere un esame trimestrale condotto con i team che si occupano della gestione dell'identità, al fine di identificare gli attori dannosi o i modelli di uso da evitare nella configurazione degli asset del cloud.

**Possibili opzioni di progettazione:** stabilire una riunione di revisione trimestrale per la sicurezza che includa sia i membri del team di governance e sia il personale IT responsabile dei servizi di gestione delle identità. Esaminare i dati e le metriche di sicurezza esistenti per stabilire i gap nei criteri e negli strumenti di gestione delle identità correnti e aggiornare i criteri per correggere eventuali nuovi rischi.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi indicati in questo articolo come punto di partenza per lo sviluppo di criteri per risolvere i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

Per iniziare a sviluppare le proprie istruzioni di criteri personalizzate correlate alla Baseline di identità, scaricare il [modello Baseline di identità](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Baseline di identità.

> [!div class="nextstepaction"]
> [Establish policy compliance processes](./compliance-processes.md) (Stabilire i processi di conformità ai criteri)
