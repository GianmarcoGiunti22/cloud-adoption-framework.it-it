---
title: Guida alle decisioni relative alla gestione delle identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla gestione delle identità come servizio di base nelle migrazioni di Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: ceb9fb6ff6be481f665a0bb70e3afcc2eddb6e92
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71023886"
---
# <a name="identity-decision-guide"></a>Guida alle decisioni relative alla gestione delle identità

In qualsiasi ambiente, che sia locale, ibrido o cloud, l'IT deve avere il controllo su quali amministratori, utenti e gruppi hanno accesso alle risorse. I servizi di gestione delle identità e degli accessi (IAM) consentono di gestire il controllo di accesso nel cloud.

![Grafico delle opzioni relative alla gestione delle identità, dalla meno complessa alla più complessa, allineato con i collegamenti sotto](../../_images/decision-guides/decision-guide-identity.png)

Passare a: [Determinare i requisiti di integrazione della soluzione di gestione delle identità](#determine-identity-integration-requirements) | [Baseline del cloud](#cloud-baseline) | [Sincronizzazione della directory](#directory-synchronization) | [Servizi di dominio ospitati nel cloud](#cloud-hosted-domain-services) | [Active Directory Federation Services](#active-directory-federation-services) | [Altre informazioni](#learn-more)

Sono disponibili diverse opzioni per la gestione delle identità in un ambiente cloud. Queste opzioni variano in termini di costi e complessità. Un fattore chiave nella strutturazione dei servizi di gestione delle identità basati sul cloud è il livello di integrazione necessario con l'infrastruttura di gestione delle identità locale esistente.

In Azure, Azure Active Directory (Azure AD) fornisce un livello di base per il controllo di accesso e la gestione delle identità per le risorse cloud. Se però l'infrastruttura di Active Directory locale dell'organizzazione ha una struttura di foresta complessa o unità organizzative personalizzate, i carichi di lavoro basati sul cloud potrebbero richiedere la sincronizzazione della directory con Azure AD per ottenere un set coerente di identità, gruppi e ruoli tra l'ambiente locale e l'ambiente cloud. Inoltre, per supportare le applicazioni che dipendono da meccanismi di autenticazione legacy potrebbe essere necessario distribuire Active Directory Domain Services (AD DS) nel cloud.

La gestione delle identità basata sul cloud è un processo iterativo. È consigliabile iniziare con una soluzione nativa del cloud con un piccolo gruppo di utenti e di ruoli corrispondenti per una distribuzione iniziale. Con il progressivo perfezionamento della migrazione, potrebbe diventare necessario integrare la soluzione di gestione delle identità con la sincronizzazione della directory o aggiungere servizi di dominio come parte delle distribuzioni del cloud. Rivedere la propria strategia di gestione delle identità in ogni iterazione del processo di migrazione.

## <a name="determine-identity-integration-requirements"></a>Determinare i requisiti di integrazione della soluzione di gestione delle identità

| Domanda | Infrastruttura nativa del cloud | Sincronizzazione delle directory | Servizi di dominio ospitati nel cloud | Active Directory Federation Services |
|------|------|------|------|------|
| Attualmente manca un servizio directory locale? | Sì | No | No | No |
| I carichi di lavoro devono usare un set comune di utenti e gruppi nell'ambiente cloud e in quello locale? | No | Sì | No | No |
| I carichi di lavoro dipendono da meccanismi di autenticazione legacy, come Kerberos o NTLM? | No | No | Sì | Sì |
| È necessario il Single Sign-On tra più provider di identità? | No | No | No | Sì |

Nell'ambito della pianificazione della migrazione ad Azure, è necessario determinare il modo migliore per integrare i servizi di gestione delle identità esistenti con i servizi cloud. Di seguito sono descritti alcuni scenari di integrazione comuni.

### <a name="cloud-baseline"></a>Infrastruttura nativa del cloud

Azure AD è il sistema di gestione delle identità e degli accessi nativo per la concessione a utenti e gruppi dell'accesso alle funzionalità di gestione nella piattaforma Azure. Se l'organizzazione non dispone di una soluzione di gestione delle identità locale rilevante e si prevede di eseguire la migrazione dei carichi di lavoro in modo che siano compatibili con i meccanismi di autenticazione basati sul cloud, è consigliabile iniziare a sviluppare l'infrastruttura di gestione delle identità usando Azure AD come base.

**Presupposti relativi alla baseline del cloud:** L'uso di un'infrastruttura di gestione delle identità completamente nativa del cloud presuppone le condizioni seguenti:

- Le risorse basate sul cloud non hanno dipendenze dai servizi directory locali o da server Active Directory oppure è possibile modificare i carichi di lavoro per rimuovere queste dipendenze.
- I carichi di lavoro di applicazioni o servizi di cui eseguire la migrazione supportano meccanismi di autenticazione compatibili con Azure AD o possono essere facilmente modificati per supportarli. Azure AD si affida a meccanismi di autenticazione basati su Internet come SAML, OAuth e OpenID Connect. I carichi di lavoro esistenti che dipendono da metodi di autenticazione legacy che usano protocolli come Kerberos o NTLM potrebbero dover essere sottoposti a refactoring prima della migrazione al cloud usando il modello di baseline del cloud.

> [!TIP]
> La migrazione completa dei servizi di gestione delle identità in Azure AD elimina la necessità di mantenere l'infrastruttura di gestione delle identità locale, semplificando notevolmente la gestione IT.
>
> Tuttavia, Azure AD non rappresenta un sostituto completo per un'infrastruttura di Active Directory locale tradizionale. Le funzionalità di directory, come i metodi di autenticazione legacy, la gestione dei computer o i criteri di gruppo potrebbero non essere disponibili se non si distribuiscono strumenti o servizi aggiuntivi nel cloud.
>
> Per gli scenari in cui è necessaria l'integrazione delle identità o dei servizi di dominio locali con le distribuzioni nel cloud, vedere i modelli con sincronizzazione della directory e servizi di dominio ospitati nel cloud presentati in precedenza.

### <a name="directory-synchronization"></a>Sincronizzazione delle directory

Per le organizzazioni che hanno già un'infrastruttura di Active Directory locale, la sincronizzazione della directory è spesso la soluzione migliore per mantenere la gestione esistente di utenti e accessi e fornire al contempo le funzionalità IAM necessarie per gestire le risorse cloud. Questo processo replica continuamente le informazioni della directory tra Azure AD e i servizi directory locali, supportando credenziali comuni per gli utenti e un sistema di gestione di identità, ruoli e autorizzazioni coerente nell'intera organizzazione.

Note: le organizzazioni che hanno adottato Office 365 potrebbero avere già implementato la [sincronizzazione della directory](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization) fra la propria infrastruttura Active Directory locale e Azure Active Directory.

**Presupposti relativi alla sincronizzazione della directory:** L'uso di una soluzione di gestione delle identità sincronizzata presuppone le condizioni seguenti:

- È necessario mantenere un set comune di account utente e di gruppi nell'infrastruttura cloud e in quella locale.
- I servizi di gestione delle identità locali supportano la replica con Azure AD.

> [!TIP]
> Qualsiasi carico di lavoro basato sul cloud che dipende da meccanismi di autenticazione legacy forniti da server Active Directory locali e non supportati da Azure AD avrà ancora bisogno di connettività ai servizi di dominio locali o ai server virtuali nell'ambiente cloud che forniscono questi servizi. L'uso di servizi di gestione delle identità locali introduce anche dipendenze a livello di connettività tra la rete cloud e la rete locale.

### <a name="cloud-hosted-domain-services"></a>Servizi di dominio ospitati nel cloud

In presenza di carichi di lavoro che dipendono da un meccanismo di autenticazione basata sulle attestazioni che usa protocolli legacy come Kerberos o NTLM, e che non possono essere sottoposti a refactoring per accettare protocolli di autenticazione moderni come SAML o OAuth e OpenID Connect, potrebbe essere necessario eseguire la migrazione di alcuni servizi di dominio al cloud nell'ambito della distribuzione cloud.

Questo modello implica la distribuzione di macchine virtuali che eseguono Active Directory nelle reti virtuali aziendali basate sul cloud al fine di rendere disponibile Active Directory Domain Services (AD DS) per le risorse nel cloud. Le applicazioni e i servizi esistenti trasferiti nella rete cloud dovrebbero poter usare questi server di directory ospitati nel cloud con modifiche minime.

Probabilmente le directory e i servizi di dominio esistenti continueranno a essere usati nell'ambiente locale. In questo scenario è consigliabile usare anche la sincronizzazione della directory per fornire un set comune di utenti e ruoli sia nell'ambiente cloud che in quello locale.

**Presupposti relativi ai servizi di dominio ospitati nel cloud:** L'esecuzione di una migrazione di directory presuppone le condizioni seguenti:

- I carichi di lavoro dipendono da un meccanismo di autenticazione basata sulle attestazioni che usa protocolli come Kerberos o NTLM.
- Le macchine virtuali dei carichi di lavoro devono essere aggiunte a un dominio ai fini della gestione o dell'applicazione di criteri di gruppo di Active Directory.

> [!TIP]
> Benché la migrazione della directory associata a servizi di dominio ospitati nel cloud assicuri un'ottima flessibilità per la migrazione dei carichi di lavoro esistenti, l'hosting di macchine virtuali nella rete virtuale cloud per fornire questi servizi aumenta la complessità delle attività di gestione IT. Man mano che la propria esperienza di migrazione nel cloud matura, esaminare i requisiti di manutenzione a lungo termine per l'hosting di questi server. Stabilire se il refactoring dei carichi di lavoro esistenti per la compatibilità con provider di identità cloud come Azure Active Directory può ridurre la necessità di questi server ospitati nel cloud.

### <a name="active-directory-federation-services"></a>Active Directory Federation Services

La federazione delle identità stabilisce relazioni di trust fra più sistemi di gestione delle identità per abilitare funzionalità comuni di autenticazione e autorizzazione. È quindi possibile supportare funzionalità di Single Sign-On in più domini all'interno dell'organizzazione oppure sistemi di gestione delle identità gestiti da clienti o partner commerciali.

Azure AD supporta la federazione di domini Active Directory locali tramite [Active Directory Federation Services](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-whatis) (AD FS). Vedere l'architettura di riferimento [Estendere Active Directory Federation Services in Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs) per informazioni su come implementarla in Azure.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni sui servizi di gestione delle identità in Azure, vedere:

- [Azure AD](https://azure.microsoft.com/services/active-directory). Azure AD fornisce servizi di gestione delle identità basati sul cloud. Consente di gestire l'accesso alle risorse di Azure e di controllare la gestione delle identità, la registrazione dei dispositivi, il provisioning degli utenti, il controllo di accesso alle applicazioni e la protezione dei dati.
- [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity). Lo strumento Azure AD Connect consente di connettere istanze di Azure AD alle soluzioni di gestione delle identità esistenti, permettendo la sincronizzazione della directory esistente nel cloud.
- [Controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/overview). Azure AD offre funzionalità di controllo degli accessi in base al ruolo che consentono di gestire in modo efficiente e sicuro l'accesso alle risorse nel piano di gestione. I processi e le responsabilità sono organizzati in ruoli e gli utenti sono assegnati a questi ruoli. Il controllo degli accessi in base al ruolo consente di controllare chi ha accesso a una risorsa e quali azioni possono essere eseguite dall'utente su quella risorsa.
- [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure) (PIM). PIM riduce il tempo di esposizione dei privilegi di accesso alle risorse e aumenta la visibilità sul loro utilizzo tramite report e avvisi. Consente agli utenti di assumere i loro privilegi soltanto "just in time" (JIT) oppure li assegna loro per una durata più breve, dopo la quale i privilegi vengono revocati automaticamente.
- [Integrare i domini Active Directory locali con Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad). Questa architettura di riferimento fornisce un esempio di sincronizzazione della directory tra domini Active Directory locali e Azure AD.
- [Estendere Active Directory Domain Services in Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain). Questa architettura di riferimento fornisce un esempio di distribuzione di server AD DS per estendere i servizi di dominio alle risorse basate sul cloud.
- [Estendere Active Directory Federation Services in Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs). Questa architettura di riferimento configura Active Directory Federation Services (AD FS) per l'esecuzione dell'autenticazione federata e dell'autorizzazione con la directory Azure AD.

## <a name="next-steps"></a>Passaggi successivi

L'identità è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
