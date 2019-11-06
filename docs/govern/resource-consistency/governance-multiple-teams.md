---
title: progettazione della governance per più team
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Linee guida per la configurazione dei controlli di governance di Azure per più team, più carichi di lavoro e più ambienti.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: caa9d3ced70ce15eacf37b4bcbb653efae9da1ef
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656697"
---
# <a name="governance-design-for-multiple-teams"></a>Progettazione di governance per più team

L'obiettivo di questa guida è illustrare il processo di progettazione di un modello di governance delle risorse in Azure per supportare più team, più carichi di lavoro e più ambienti. Per prima cosa verranno esaminati alcuni ipotetici requisiti di governance, quindi verranno illustrate diverse implementazioni di esempio che soddisfano tali requisiti.

I requisiti sono:

- L'azienda prevede di passare i nuovi ruoli cloud e le nuove responsabilità a un insieme di utenti e pertanto richiede la gestione delle identità per più team con diverse esigenze di accesso alle risorse in Azure. Il sistema di gestione delle identità è necessario per memorizzare l'identità degli utenti seguenti:
  - L'utente dell'organizzazione responsabile della proprietà delle **sottoscrizioni**.
  - L'utente dell'organizzazione responsabile delle **risorse dell'infrastruttura condivisa** usate per connettere la rete locale a una rete virtuale di Azure.
  - Due utenti dell'organizzazione responsabili della gestione di un **carico di lavoro**.
- Supporto di più **ambienti**. Un ambiente è un raggruppamento logico di risorse, ad esempio macchine virtuali, reti virtuali e servizi di routing del traffico di rete. Questi gruppi di risorse hanno requisiti di sicurezza e gestione simili e vengono in genere usati per uno scopo specifico, ad esempio test o produzione. In questo esempio il requisito è per quattro ambienti:
  - Un **ambiente di infrastruttura condivisa** che include risorse condivise dai carichi di lavoro in altri ambienti. Ad esempio, una rete virtuale con una subnet gateway che fornisce connettività all'ambiente locale.
  - Un **ambiente di produzione** con i criteri di sicurezza più restrittivi. Può includere carichi di lavoro interni o rivolti all'esterno.
  - **Ambiente di pre-produzione** per il lavoro di sviluppo e test. Questo ambiente ha criteri di sicurezza, conformità e costi diversi da quelli dell'ambiente di produzione. In Azure il formato di una sottoscrizione Sviluppo/test Enterprise.
  - **Ambiente sandbox** a scopo di prova e istruzione. Questo ambiente viene in genere assegnato a ogni dipendente che partecipa alle attività di sviluppo e dispone di controlli di sicurezza operativi e procedurali rigorosi per impedire l'atterraggio dei dati aziendali. In Azure, le sottoscrizioni di Visual Studio sono di tipo. Queste sottoscrizioni _non_ devono inoltre essere associate all'Azure Active Directory aziendale.
- Un **modello di autorizzazione con privilegi minimi** in cui gli utenti non hanno autorizzazioni predefinite. Il modello deve supportare quanto segue:
  - Un singolo utente attendibile (trattato come un account del servizio) nell'ambito della sottoscrizione con l'autorizzazione per assegnare i diritti di accesso alle risorse.
  - Per impostazione predefinita, a ogni proprietario del carico di lavoro viene negato l'accesso alle risorse. I diritti di accesso alle risorse vengono concessi in modo esplicito dal singolo utente attendibile nell'ambito del gruppo di risorse.
  - Accesso di gestione per le risorse dell'infrastruttura condivisa limitate ai proprietari dell'infrastruttura condivisa.
  - Accesso di gestione per ogni carico di lavoro limitato al proprietario del carico di lavoro (in produzione) e livelli di controllo crescenti, perché lo sviluppo aumenta da sviluppo a test fino alla fase di produzione.
  - L'azienda non vuole avere la necessità di gestire i ruoli in modo indipendente in ognuno dei tre ambienti principali e pertanto richiede l'uso dei soli [ruoli predefiniti](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles) disponibili nel controllo degli accessi in base al ruolo (RBAC) di Azure. Se l'azienda richiede assolutamente ruoli RBAC personalizzati, saranno necessari processi aggiuntivi per sincronizzare i ruoli personalizzati nei tre ambienti.
- Monitoraggio dei costi in base al nome del proprietario del carico di lavoro, all'ambiente o a entrambi.

## <a name="identity-management"></a>Gestione delle identità

Prima di poter progettare la gestione delle identità per il modello di governance, è importante comprendere le quattro aree principali che lo compongono:

- **Amministrazione:** Processi e strumenti per la creazione, la modifica e l'eliminazione dell'identità utente.
- **Autenticazione:** Verifica dell'identità dell'utente tramite la convalida delle credenziali, ad esempio un nome utente e una password.
- **Autorizzazione:** Determinare le risorse a cui un utente autenticato può accedere o le operazioni di cui dispone dell'autorizzazione per l'esecuzione.
- **Controllo:** Esaminare periodicamente i log e altre informazioni per individuare i problemi di sicurezza correlati all'identità utente. Include l'analisi di modelli di utilizzo sospetti, l'esame periodico delle autorizzazioni dell'utente per verificare che siano corrette e altre funzioni.

Azure ritiene attendibile un solo servizio per l'identità, ovvero Azure Active Directory (Azure AD). Verranno aggiunti utenti ad Azure AD e questo servizio verrà usato per tutte le funzioni elencate in precedenza. Prima di esaminare come verrà configurato Azure AD, è importante comprendere gli account con privilegi che vengono usati per gestire l'accesso a questi servizi.

Quando l'organizzazione si è iscritta a un account Azure, è stato assegnato almeno un **proprietario dell'account** Azure. È stato creato anche un **tenant** di Azure AD, a meno che un tenant esistente non fosse già stato associato all'uso dell'organizzazione di altri servizi Microsoft come Office 365. Un **amministratore globale**  con autorizzazioni complete per il tenant di Azure AD è stato associato al momento della creazione.

Le identità dell'utente sia per il proprietario dell'account Azure che per l'amministratore globale di Azure AD sono archiviate in un sistema di identità altamente sicuro gestito da Microsoft. Il proprietario dell'account Azure è autorizzato a creare, aggiornare ed eliminare sottoscrizioni. L'amministratore globale di Azure AD è autorizzato a eseguire molte azioni in Azure AD, ma questa guida alla progettazione si concentrerà sulla creazione e sull'eliminazione dell'identità utente.

> [!NOTE]
> È possibile che l'organizzazione disponga già di un tenant di Azure AD esistente se è presente una licenza di Office 365, Intune o Dynamics associata all'account.

Il proprietario dell'account Azure è autorizzato a creare, aggiornare ed eliminare sottoscrizioni:

![account Azure con gestione account di Azure e Azure AD amministratore globale](../../_images/govern/design/governance-3-0.png)
*Figura 1: un account Azure con un account manager e Azure ad amministratore globale.*

L'amministratore globale di **Azure AD** è autorizzato a creare account utente:

![account Azure con gestione account di Azure e Azure AD amministratore globale](../../_images/govern/design/governance-3-0a.png)
*Figura 2: l'amministratore globale Azure ad crea gli account utente necessari nel tenant.*

I primi due account, **Proprietario del carico di lavoro per App1** e **Proprietario del carico di lavoro per App2**, sono associati ognuno a un utente dell'organizzazione responsabile della gestione di un carico di lavoro. L'account **Network Operations** è di proprietà dell'utente responsabile delle risorse dell'infrastruttura condivisa. Infine, l'account **Subscription Owner** è associato al responsabile della proprietà delle sottoscrizioni.

## <a name="resource-access-permissions-model-of-least-privilege"></a>Modello di autorizzazioni di accesso alle risorse con privilegi minimi

Ora che sono disponibili il sistema di gestione delle identità e gli account utente, è necessario decidere come applicare i ruoli di controllo degli accessi in base al ruolo a ogni account per supportare un modello di autorizzazioni con privilegi minimi.

Un altro requisito prevede che le risorse associate a ogni carico di lavoro siano isolate l'una dall'altra in modo che nessun proprietario di un carico di lavoro abbia accesso di gestione ad altri carichi di lavoro di cui non è proprietario. È anche necessario implementare questo modello usando solo i ruoli predefiniti per il controllo degli accessi in base al ruolo di Azure.

Ogni ruolo di Controllo degli accessi in base al ruolo viene applicato a uno di tre ambiti in Azure: **sottoscrizione**, **gruppo di risorse** e singola **risorsa**. I ruoli vengono ereditati negli ambiti inferiori. Ad esempio, se a un utente viene assegnato il [ruolo proprietario predefinito](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) a livello di sottoscrizione, tale ruolo viene assegnato anche a tale utente a livello di gruppo di risorse e a livello di risorsa singolo a meno che non venga sottoposto a override.

Pertanto, per creare un modello di accesso con privilegi minimi è necessario decidere le azioni che un determinato tipo di utente può eseguire in ognuno di questi tre ambiti. Ad esempio, il requisito prevede che il proprietario di un carico di lavoro sia autorizzato a gestire l'accesso solo alle risorse associate al proprio carico di lavoro e non ad altre. Se si assegna il ruolo proprietario predefinito nell'ambito della sottoscrizione, ogni proprietario del carico di lavoro avrà accesso di gestione a tutti i carichi di lavoro.

Di seguito sono riportati due modelli di autorizzazioni di esempio per comprendere meglio questo concetto. Nel primo esempio il modello considera attendibile solo l'amministratore per creare i gruppi di risorse. Nel secondo esempio il modello assegna il ruolo di proprietario predefinito a ogni proprietario del carico di lavoro nell'ambito della sottoscrizione.

In entrambi gli esempi, è disponibile un amministratore del servizio di sottoscrizione a cui viene assegnato il ruolo proprietario predefinito nell'ambito della sottoscrizione. Tenere presente che il ruolo proprietario predefinito concede tutte le autorizzazioni, inclusa la gestione dell'accesso alle risorse.
![amministratore del servizio di sottoscrizione con ruolo proprietario](../../_images/govern/design/governance-2-1.png)
*Figura 3-A una sottoscrizione con un amministratore del servizio è stato assegnato il ruolo proprietario predefinito.*

1. Nel primo esempio è presente il **proprietario del carico di lavoro A** senza autorizzazioni a livello della sottoscrizione, per impostazione predefinita senza diritti di gestione dell'accesso alle risorse. Questo utente vuole distribuire e gestire le risorse per il proprio carico di lavoro. Deve contattare l'**amministratore del servizio** per richiedere la creazione di un gruppo di risorse.
    ![il proprietario del carico di lavoro richiede la creazione del gruppo di risorse A](../../_images/govern/design/governance-2-2.png)
2. L' **amministratore del servizio** esamina la richiesta e crea il **gruppo di risorse A**. A questo punto, **il proprietario del carico di lavoro a** non è ancora autorizzato a eseguire alcuna operazione.
    ![l'amministratore del servizio crea il gruppo di risorse A](../../_images/govern/design/governance-2-3.png)
3. L'**amministratore del servizio** aggiunge il **proprietario del carico di lavoro A** al **gruppo di risorse A** e assegna il [ruolo di collaboratore predefinito](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor). Il ruolo di collaboratore concede tutte le autorizzazioni per il **gruppo di risorse A**, tranne la gestione delle autorizzazioni di accesso.
    ![l'amministratore del servizio aggiunge il proprietario del carico di lavoro al gruppo di risorse A](../../_images/govern/design/governance-2-4.png)
4. Si supponga che il **proprietario del carico di lavoro A** debba consentire a un paio di componenti del team di visualizzare i dati di monitoraggio della CPU e del traffico di rete nell'ambito della pianificazione delle capacità del carico di lavoro. Poiché il **proprietario del carico di lavoro a** è assegnato al ruolo Collaboratore, non dispone dell'autorizzazione per aggiungere un utente al **gruppo di risorse a**. È necessario che invii questa richiesta all' **amministratore del servizio**.
    ![il proprietario del carico di lavoro richiede l'aggiunta dei collaboratori del carico di lavoro al gruppo di risorse](../../_images/govern/design/governance-2-5.png)
5. L' **amministratore del servizio** esamina la richiesta e aggiunge i due utenti **collaboratore del carico di lavoro** al gruppo di **risorse a**. Nessuno di questi due utenti richiede l'autorizzazione per la gestione delle risorse, pertanto viene assegnato il [ruolo predefinito Reader](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor).
    ![l'amministratore del servizio aggiunge i collaboratori del carico di lavoro al gruppo di risorse A](../../_images/govern/design/governance-2-6.png)
6. Successivamente, anche il **proprietario del carico di lavoro B** richiede che un gruppo di risorse contenga le risorse per il proprio carico di lavoro. Come il **proprietario del carico di lavoro A**, il **proprietario del carico di lavoro B** non è inizialmente autorizzato a eseguire azioni a livello di sottoscrizione, quindi deve inviare una richiesta all'**amministratore del servizio**.
    ![il proprietario del carico di lavoro B richiede la creazione del gruppo di risorse B](../../_images/govern/design/governance-2-7.png)
7. L' **amministratore del servizio** esamina la richiesta e crea il **gruppo di risorse B**.  ![amministratore del servizio crea il gruppo di risorse B](../../_images/govern/design/governance-2-8.png)
8. L' **amministratore del servizio** aggiunge quindi il **proprietario del carico di lavoro b** al **gruppo di risorse b** e assegna il ruolo Collaboratore predefinito.
    ![l'amministratore del servizio aggiunge il proprietario del carico di lavoro B al gruppo di risorse B](../../_images/govern/design/governance-2-9.png)

A questo punto, ogni proprietario del carico di lavoro è isolato nel proprio gruppo di risorse. I proprietari del carico di lavoro o i componenti dei loro team non hanno accesso alle risorse di altri gruppi di risorse.

![sottoscrizione con i gruppi di risorse A e B](../../_images/govern/design/governance-2-10.png)
*Figura 4-una sottoscrizione con due proprietari del carico di lavoro isolati con il proprio gruppo di risorse.*

Questo modello è un modello con privilegi minimi&mdash;a ogni utente viene assegnata l'autorizzazione corretta nell'ambito di gestione delle risorse corretto.

Si consideri tuttavia che ogni attività in questo esempio è stata eseguita dall'**amministratore del servizio**. Anche se in un esempio semplice come questo può non sembrare un problema perché ci sono solo due proprietari del carico di lavoro, è facile immaginare i problemi che ne deriverebbero per una grande organizzazione. Ad esempio, l'**amministratore del servizio** può andare incontro a un collo di bottiglia con un gran numero di richieste arretrate che causano ritardi.

Di seguito è riportato un secondo esempio che riduce il numero di attività eseguite dall'**amministratore del servizio**.

1. In questo modello, al **proprietario del carico di lavoro a** viene assegnato il ruolo proprietario predefinito nell'ambito della sottoscrizione, consentendo loro di creare il proprio gruppo di risorse: **gruppo di risorse a**.  ![amministratore del servizio aggiunge il proprietario del carico di lavoro a alla sottoscrizione](../../_images/govern/design/governance-2-11.png)
2. Quando viene creato il **gruppo di risorse a** , il **proprietario del carico di lavoro a** viene aggiunto per impostazione predefinita ed eredita il ruolo predefinito del proprietario dall'ambito della sottoscrizione.
    ![Il proprietario del carico di lavoro A crea il gruppo di risorse A](../../_images/govern/design/governance-2-12.png)
3. Il ruolo proprietario predefinito concede al **proprietario del carico di lavoro un'** autorizzazione per gestire l'accesso al gruppo di risorse. Il **proprietario del carico di lavoro a** aggiunge due **collaboratori del carico di lavoro** e assegna il ruolo di lettore predefinito a ognuno di essi.
    ![Il proprietario del carico di lavoro A aggiunge i collaboratori del carico di lavoro](../../_images/govern/design/governance-2-13.png)
4. **L'amministratore del servizio** aggiunge ora il **proprietario del carico di lavoro B** alla sottoscrizione con il ruolo di proprietario predefinito.
    ![L'amministratore del servizio aggiunge i proprietari dei carichi di lavoro A e B alla sottoscrizione](../../_images/govern/design/governance-2-14.png)
5. **Il proprietario del carico di lavoro B** crea il  **gruppo di risorse B** e viene aggiunto per impostazione predefinita. Anche in questo caso, il **proprietario del carico di lavoro B** eredita il ruolo di proprietario predefinito dall'ambito della sottoscrizione.
    ![Il proprietario del carico di lavoro B crea il gruppo di risorse B](../../_images/govern/design/governance-2-15.png)

Si noti che in questo modello l'**amministratore del servizio** ha eseguito meno azioni rispetto al primo esempio, avendo delegato l'accesso di gestione a ognuno dei proprietari dei carichi di lavoro.

![sottoscrizione con i gruppi di risorse A e B](../../_images/govern/design/governance-2-16.png)
*Figura 5: una sottoscrizione con un amministratore del servizio e due proprietari del carico di lavoro, tutti assegnati al ruolo proprietario predefinito.*

Dato che tuttavia sia il **proprietario del carico di lavoro A** che il  **proprietario del carico di lavoro B** hanno il ruolo di proprietario predefinito nell'ambito della sottoscrizione, ognuno di essi ha ereditato il ruolo di proprietario predefinito per il gruppo di risorse dell'altro. Ciò significa che non solo hanno pieno accesso alle risorse dell'altro, ma possono anche delegare l'accesso di gestione al gruppo di risorse dell'altro. Ad esempio, il **proprietario del carico di lavoro B** è autorizzato ad aggiungere qualsiasi altro utente al **gruppo di risorse A** e può assegnare agli utenti qualsiasi ruolo, incluso il ruolo di proprietario predefinito.

Se si confronta ogni esempio con i requisiti definiti, entrambi gli esempi supportano un singolo utente attendibile nell'ambito della sottoscrizione, autorizzato a concedere diritti di accesso alle risorse ai due proprietari dei carichi di lavoro. Nessuno dei due proprietari dei carichi di lavoro aveva accesso alla gestione delle risorse per impostazione predefinita e doveva richiedere all'**amministratore del servizio** di assegnare esplicitamente le autorizzazioni. Solo il primo esempio supporta tuttavia il requisito secondo il quale le risorse associate a ciascun carico di lavoro debbano essere isolate l'una dall'altra, in modo tale che nessun proprietario del carico di lavoro abbia accesso alle risorse degli altri carichi di lavoro.

## <a name="resource-management-model"></a>Modello di gestione delle risorse

Ora che è stato progettato un modello di autorizzazioni con privilegi minimi, verranno esaminate alcune applicazioni pratiche di questi modelli di governance. Secondo i requisiti definiti, è necessario supportare i tre ambienti seguenti:

1. **Ambiente infrastruttura condivisa:** Gruppo di risorse condivise da tutti i carichi di lavoro. Si tratta di risorse quali gateway di rete, firewall e servizi di sicurezza.
2. **Ambiente di produzione:** Più gruppi di risorse che rappresentano più carichi di lavoro di produzione. Queste risorse vengono usate per ospitare elementi privati e pubblici delle applicazioni. Queste risorse hanno in genere i modelli di governance e sicurezza più rigorosi per proteggere le risorse, il codice delle applicazioni e i dati da accessi non autorizzati.
3. **Ambiente di preproduzione:** Più gruppi di risorse che rappresentano più carichi di lavoro pronti per la produzione. Queste risorse vengono usate per lo sviluppo e il test di queste risorse possono avere un modello di governance più rilassato per consentire una maggiore agilità degli sviluppatori. La sicurezza all'interno di questi gruppi dovrebbe aumentare il più vicino alla "produzione" per ottenere un processo di sviluppo di applicazioni.

Per ognuno di questi tre ambienti è necessario tenere traccia dei dati sui costi per **proprietario del carico di lavoro**, **ambiente** o entrambi. In altre termini, sarà necessario ottenere informazioni sui costi in corso dell' **infrastruttura condivisa**, i costi sostenuti da singoli utenti negli ambienti di **pre** -produzione e di **produzione** e infine il costo **complessivo della preproduzione e**ambienti di produzione.

Si è già appreso che le risorse sono suddivise in due livelli: **sottoscrizione** e **gruppo di risorse**. La prima decisione da prendere è quindi come organizzare gli ambienti per **sottoscrizione**. Sono disponibili solo due opzioni: una singola sottoscrizione o più sottoscrizioni.

Prima di esaminare gli esempi di ognuno di questi modelli, verrà esaminata la struttura di gestione per le sottoscrizioni in Azure.

Secondo i requisiti definiti, un utente dell'organizzazione è responsabile delle sottoscrizioni e ha l'account **proprietario della sottoscrizione** nel tenant di Azure AD. Questo account non è tuttavia autorizzato a creare sottoscrizioni. Solo il **proprietario dell'account Azure** ha tale autorizzazione:

![un proprietario dell'account Azure crea una sottoscrizione](../../_images/govern/design/governance-3-0b.png)
*Figura 6: un proprietario dell'account Azure crea una sottoscrizione.*

Una volta creata la sottoscrizione, il **proprietario dell'account Azure** può aggiungere l'account **proprietario della sottoscrizione** alla sottoscrizione con il ruolo **proprietario**:

![il proprietario dell'account Azure aggiunge l'account utente del proprietario della sottoscrizione alla sottoscrizione con il ruolo proprietario.](../../_images/govern/design/governance-3-0c.png)
*Figura 7: il proprietario dell'account Azure aggiunge l'account utente del **proprietario della sottoscrizione** alla sottoscrizione con il ruolo **proprietario** .*

Il **proprietario della sottoscrizione** può ora creare **gruppi di risorse** e delegare la gestione dell'accesso alle risorse.

Verrà ora esaminato un esempio di modello di gestione delle risorse che usa una sottoscrizione singola. La prima decisione da prendere è come allineare i gruppi di risorse ai tre ambienti. Sono disponibili due opzioni:

1. Allineare ogni ambiente a un singolo gruppo di risorse. Tutte le risorse dell'infrastruttura condivisa vengono distribuite in un singolo gruppo di risorse dell'**infrastruttura condivisa**. Tutte le risorse associate ai carichi di lavoro di sviluppo vengono distribuite in un singolo gruppo di risorse di **sviluppo**. Tutte le risorse associate ai carichi di lavoro di produzione vengono distribuite in un singolo gruppo di risorse di **produzione**  per l'ambiente di **produzione**.
2. Creare un gruppo di risorse separato per ciascun carico di lavoro, usando una convenzione di denominazione e tag per allineare i gruppi di risorse a ognuno dei tre ambienti.

Verrà ora valutata la prima opzione. Si userà il modello di autorizzazioni illustrato nella sezione precedente, con un solo amministratore del servizio della sottoscrizione che crea i gruppi di risorse e aggiunge gli utenti ai gruppi con il ruolo di **collaboratore** o **lettore** predefiniti.

1. Il primo gruppo di risorse distribuito rappresenta l'ambiente dell'**infrastruttura condivisa**. Il **proprietario della sottoscrizione** crea un gruppo di risorse per le risorse dell'infrastruttura condivisa denominato `netops-shared-rg`.
    ![la creazione di un gruppo di risorse](../../_images/govern/design/governance-3-0d.png)
2. Il **proprietario della sottoscrizione** aggiunge l'account **utente delle operazioni di rete** al gruppo risorse e assegna il ruolo di **collaboratore**.
    ![l'aggiunta di un utente di operazioni di rete](../../_images/govern/design/governance-3-0e.png)
3. L'**utente delle operazioni di rete** crea un [gateway VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) e lo configura per la connessione all'appliance VPN locale. L'**utente delle operazioni di rete** applica anche una coppia di [tag](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) a ognuna delle risorse: *environment:shared* e *managedBy:netOps*. Quando l'**amministratore del servizio della sottoscrizione** esporta un report sui costi, i costi verranno allineati a ognuno di questi tag. L'**amministratore del servizio della sottoscrizione** può così organizzare i costi usando i tag *environment* e *managedBy*. Si noti il contatore dei **limiti delle risorse** in alto a destra nella figura. Ogni sottoscrizione di Azure ha [limiti del servizio](https://docs.microsoft.com/azure/azure-subscription-service-limits). Per comprendere l'effetto di questi limiti si seguirà il limite della rete virtuale per ogni sottoscrizione. Esiste un limite di 1000 reti virtuali per ogni sottoscrizione e dopo la distribuzione della prima rete virtuale restano disponibili 999 reti.
    ![la creazione di un gateway VPN](../../_images/govern/design/governance-3-1.png)
4. Vengono distribuiti altri due gruppi di risorse. Il primo è denominato `prod-rg`. Questo gruppo di risorse è allineato all'ambiente di produzione. Il secondo è denominato `dev-rg` ed è allineato all'ambiente di sviluppo. Tutte le risorse associate ai carichi di lavoro di produzione sono distribuite nell'ambiente di produzione e tutte le risorse associate ai carichi di lavoro di sviluppo sono distribuite nell'ambiente di sviluppo. In questo esempio verranno distribuiti solo due carichi di lavoro in ognuno di questi due ambienti, quindi non si incontrerà alcun limite di servizio della sottoscrizione di Azure. È tuttavia importante considerare che ogni gruppo di risorse ha un limite di 800 risorse per gruppo di risorse. Se si continua ad aggiungere carichi di lavoro a ogni gruppo di risorse, alla fine il limite verrà raggiunto.
    ![la creazione di gruppi di risorse](../../_images/govern/design/governance-3-2.png)
5. Il primo **proprietario del carico di lavoro** invia una richiesta all'**amministratore del servizio della sottoscrizione** e viene aggiunto a ognuno dei gruppi di risorse dell'ambiente di sviluppo e di produzione con il ruolo di **collaboratore**. Come si è appreso in precedenza, il ruolo di **collaboratore** consente all'utente di eseguire qualsiasi operazione, tranne l'assegnazione di un ruolo a un altro utente. Il primo **proprietario del carico di lavoro** può ora creare le risorse associate al proprio carico di lavoro.
    ![aggiunta di collaboratori](../../_images/govern/design/governance-3-3.png)
6. Il primo **proprietario del carico di lavoro** crea una rete virtuale in ognuno dei due gruppi di risorse con una coppia di macchine virtuali in ciascuno. Il primo **proprietario del carico di lavoro** applica i tag *environment* e *managedBy* a tutte le risorse. Si noti che il contatore dei limiti del servizio di Azure indica ora 997 reti virtuali rimanenti.
    ![la creazione di reti virtuali](../../_images/govern/design/governance-3-4.png)
7. Nessuna delle reti virtuali ha connettività con l'ambiente locale al momento della creazione. In questo tipo di architettura, è necessario eseguire il peering di ogni rete virtuale con *hub-vnet* nell'ambiente dell'**infrastruttura condivisa**. Il peering di rete virtuale crea una connessione tra due reti virtuali separate e consente al traffico di rete di passare da una rete all'altra. Si noti che il peering di rete virtuale non è intrinsecamente transitivo. È necessario specificare un peering in ognuna delle due reti virtuali connesse. Se solo una delle reti virtuali specifica un peering, la connessione è incompleta. Per illustrare l'effetto, il primo **proprietario del carico di lavoro** specifica un peering tra **prod-vnet** e **hub-vnet**. Il primo peering è stato creato, ma il traffico non viene trasmesso perché il peering complementare da **hub-vnet**  a **prod-vnet** non è stato ancora specificato. Il primo **proprietario del carico di lavoro** contatta l'utente delle **operazioni di rete** e richiede questa connessione di peering complementare.
    ![la creazione di una connessione di peering](../../_images/govern/design/governance-3-5.png)
8. L'utente delle **operazioni di rete** esamina la richiesta, la approva e quindi specifica il peering nelle impostazioni di **hub-vnet**. La connessione peering è ora completa e il traffico di rete viene trasmesso tra le due reti virtuali.
    ![la creazione di una connessione di peering](../../_images/govern/design/governance-3-6.png)
9. Un secondo **proprietario del carico di lavoro**  invia ora una richiesta all'**all'amministratore del servizio della sottoscrizione** e viene aggiunto ai gruppi di risorse degli ambienti di **produzione** e **sviluppo** esistenti con il ruolo di **collaboratore**. Il secondo **proprietario del carico di lavoro** ha per tutte le risorse le stesse autorizzazioni del primo **proprietario del carico di lavoro** in ogni gruppo di risorse.
    ![aggiunta di collaboratori](../../_images/govern/design/governance-3-7.png)
10. Il secondo **proprietario del carico di lavoro** crea una subnet nella rete virtuale **prod-vnet**, quindi aggiunge due macchine virtuali. Il secondo **proprietario del carico di lavoro** applica i tag *environment* e *managedBy* a ogni risorsa.
    ![la creazione di subnet](../../_images/govern/design/governance-3-8.png)

Questo modello di esempio per la gestione delle risorse consente di gestire le risorse nei tre ambienti richiesti. Le risorse dell'infrastruttura condivisa sono protette perché nella sottoscrizione è presente un solo utente autorizzato ad accedere a tali risorse. Ognuno dei proprietari del carico di lavoro può usare le risorse dell'infrastruttura condivisa senza avere autorizzazioni sulle risorse condivise in sé. Questo modello di gestione, tuttavia, non soddisfa il requisito di isolamento del carico di lavoro: ognuno dei due **proprietari del carico di lavoro** può accedere alle risorse del carico di lavoro dell'altro.

Un'altra considerazione importante per questo modello potrebbe non essere così ovvia. Nell'esempio è stato il **proprietario del carico di lavoro per app1** a richiedere la connessione di peering di rete con **hub-vnet** per ottenere la connettività con l'ambiente locale. L'utente delle **operazioni di rete** ha valutato la richiesta in base alle risorse distribuite con tale carico di lavoro. Quando il **proprietario della sottoscrizione** ha aggiunto **app2 workload owner** con il ruolo di **collaboratore**, quell'utente aveva i diritti di accesso di gestione per tutte le risorse nel gruppo di risorse **prod-rg**.

![Diagramma che illustra i diritti di accesso alla gestione](../../_images/govern/design/governance-3-10.png)

Ciò significa che **app2 workload owner** è autorizzato a distribuire la propria subnet con macchine virtuali nella rete virtuale **prod-vnet**. Per impostazione predefinita, tali macchine virtuali hanno ora accesso alla rete locale. L'utente delle **operazioni di rete** non è a conoscenza di tali macchine e non ne ha approvato la connettività con l'ambiente locale.

Si esaminerà ora una sottoscrizione singola con più gruppi di risorse per ambienti e carichi di lavoro diversi. Si noti che nell'esempio precedente le risorse per ogni ambiente erano facilmente identificabili perché facevano parte dello stesso gruppo di risorse. Ora che quel raggruppamento non è più disponibile, sarà necessario fare affidamento su una convenzione di denominazione dei gruppi di risorse per ottenere tale funzionalità.

1. Le risorse dell'**infrastruttura condivisa** avranno ancora un gruppo di risorse separato in questo modello, che quindi non cambia. Ogni carico di lavoro richiede due gruppi di risorse, uno per ognuno degli ambienti di **sviluppo** e **produzione**. Per il primo carico di lavoro, il **proprietario della sottoscrizione** crea due gruppi di risorse. Il primo è denominato **App1-prod-RG** e il secondo è denominato **App1-dev-RG**. Come illustrato in precedenza, questa convenzione di denominazione identifica le risorse come associate al primo carico di lavoro, **app1**, e all'ambiente **dev** o **prod**. Anche in questo caso, il proprietario della *sottoscrizione* aggiunge il **proprietario del carico di lavoro App1** al gruppo di risorse con il ruolo **collaboratore** .
    ![aggiunta di collaboratori](../../_images/govern/design/governance-3-12.png)
2. In modo simile al primo esempio, **app1 workload owner** distribuisce una rete virtuale denominata **app1-prod-vnet** nell'ambiente di **produzione** e un'altra denominata **app1-dev-vnet**  nell'ambiente di **sviluppo**. Anche in questo caso, **app1 workload owner** invia una richiesta all'utente delle **operazioni di rete** per la creazione di una connessione di peering. Si noti che **app1 workload owner** aggiunge gli stessi tag del primo esempio e il contatore dei limiti indica 997 reti virtuali rimanenti nella sottoscrizione.
    ![la creazione di una connessione di peering](../../_images/govern/design/governance-3-13.png)
3. Il proprietario della **sottoscrizione** crea ora due gruppi di risorse per **app2 workload owner**. Seguendo le stesse convenzioni valide per **app1 workload owner**, i gruppi di risorse vengono denominati **app2-prod-rg** e **app2-dev-rg**. Il **proprietario della sottoscrizione** aggiunge **app2 workload owner** a ognuno dei gruppi di risorse con il ruolo **collaboratore**.
    ![aggiunta di collaboratori](../../_images/govern/design/governance-3-14.png)
4. *App2 workload owner* distribuisce le reti e le macchine virtuali nei gruppi di risorse con le stesse convenzioni di denominazione. Vengono aggiunti i tag e il contatore dei limiti scende a 995 reti virtuali rimanenti nella *sottoscrizione*.
    ![la distribuzione di reti virtuali e VM](../../_images/govern/design/governance-3-15.png)
5. *App2 workload owner* invia una richiesta all'utente delle *operazioni di rete* per eseguire il peering di *app2-prod-vnet* con *hub-vnet*. L'utente delle *operazioni di rete*  crea la connessione di peering.
    ![la creazione di una connessione di peering](../../_images/govern/design/governance-3-16.png)

Il modello di gestione ottenuto è simile al primo esempio, con numerose differenze fondamentali:

- Ognuno dei due carichi di lavoro è isolato per carico di lavoro e ambiente.
- Questo modello richiedeva due reti virtuali in più rispetto al primo modello di esempio. Pur non trattandosi di una distinzione importante con due soli carichi di lavoro, il limite teorico del numero di carichi di lavoro per questo modello è 24.
- Le risorse non sono più raggruppate in un unico gruppo di risorse per ogni ambiente. Il raggruppamento delle risorse richiede la comprensione delle convenzioni di denominazione usate per ogni ambiente.
- Ognuna delle connessioni di rete virtuali con peering è stata esaminata e approvata dall'utente delle *operazioni di rete*.

Si esaminerà ora un modello di gestione delle risorse con più sottoscrizioni. In questo modello, ognuno dei tre ambienti verrà allineato a una sottoscrizione distinta: una sottoscrizione di **servizi condivisi**, una sottoscrizione di **produzione** e, infine, una sottoscrizione di **sviluppo**. Le considerazioni per questo modello sono simili a quelle di un modello che usa una sottoscrizione singola, perché è necessario decidere come allineare i gruppi di risorse ai carichi di lavoro. È già stato stabilito che la creazione di un gruppo di risorse per ogni carico di lavoro soddisfa i requisiti di isolamento del carico di lavoro, quindi si seguirà questo modello in questo esempio.

1. In questo modello sono disponibili tre *sottoscrizioni*: *infrastruttura condivisa*, *produzione* e *sviluppo*. Ognuna di queste tre sottoscrizioni richiede un *proprietario della sottoscrizione* e in questo esempio semplice si userà lo stesso account utente per tutte e tre. Le risorse dell'*infrastruttura condivisa* sono gestite in modo simile ai primi due esempi precedenti e il primo carico di lavoro è associato ad *app1-rg* nell'ambiente di *produzione* e al gruppo di risorse con lo stesso nome nell'ambiente di *sviluppo*. *App1 workload owner* viene aggiunto a ogni gruppo di risorse con il ruolo di *collaboratore*.
    ![aggiunta di collaboratori](../../_images/govern/design/governance-3-17.png)
2. Come per gli esempi precedenti, *app1 workload owner* crea le risorse e richiede la connessione di peering con la rete virtuale dell'*infrastruttura condivisa*. *App1 workload owner* aggiunge solo il tag *managedBy* perché il tag *environment* non è più necessario. In altre parole, le risorse per ogni ambiente sono ora raggruppate nella stessa *sottoscrizione* e il tag *environment* è ridondante. Il contatore dei limiti scende a 999 reti virtuali rimanenti.
    ![la creazione di una connessione di peering](../../_images/govern/design/governance-3-18.png)
3. Il *proprietario della sottoscrizione* ripete infine il processo per il secondo carico di lavoro, aggiungendo i gruppi di risorse con *app2 workload owner* nel ruolo di *collaboratore. Il contatore dei limiti per ogni sottoscrizione dell'ambiente scende a 998 reti virtuali rimanenti.

Questo modello di gestione ha i vantaggi del secondo esempio illustrato in precedenza. La differenza principale è tuttavia che i limiti non rappresentano un problema reale perché sono distribuiti in due *sottoscrizioni*. Lo svantaggio è che i dati sui costi rilevati dai tag devono essere aggregati per tutte e tre le *sottoscrizioni*.

È quindi possibile selezionare uno di questi due esempi di modelli di gestione delle risorse a seconda della priorità dei propri requisiti. Se si prevede che l'organizzazione non raggiungerà i limiti del servizio per una sottoscrizione singola, è possibile usare una sottoscrizione singola con più gruppi di risorse. Se invece l'organizzazione prevede molti carichi di lavoro, può essere meglio usare più sottoscrizioni per ogni ambiente.

## <a name="implement-the-resource-management-model"></a>Implementare il modello di gestione delle risorse

Sono stati appresi diversi modelli per la gestione dell'accesso alle risorse di Azure. Ora verranno esaminati i passaggi necessari per implementare il modello di gestione delle risorse con una sottoscrizione per ognuno degli ambienti, di **infrastruttura condivisa**, **produzione** e **sviluppo**, illustrati nella guida alla progettazione. Sarà presente un **proprietario della sottoscrizione** per tutti e tre gli ambienti. Ogni carico di lavoro sarà isolato in un **gruppo di risorse** con un **proprietario del carico di lavoro** aggiunto con il ruolo di **collaboratore**.

> [!NOTE]
> Vedere [informazioni sull'accesso alle risorse in Azure](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles) per altre informazioni sulla relazione tra gli account e le sottoscrizioni di Azure.

Seguire questa procedura:

1. Creare un [account di Azure](https://docs.microsoft.com/azure/active-directory/sign-up-organization), se l'organizzazione non ne ha già uno. La persona che effettua l'iscrizione per l'account di Azure diventa l'amministratore account di Azure e i leader dell'organizzazione devono scegliere una persona che assuma questo ruolo. Questo utente sarà responsabile di:
    - Creazione di sottoscrizioni.
    - Creazione e amministrazione di tenant di [Azure Active Directory (Azure ad)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) che archiviano l'identità utente per tali sottoscrizioni.
2. Il team di leader dell'organizzazione decide quali utenti sono responsabili di:
    - Gestione dell'identità utente. Per impostazione predefinita, viene creato un [tenant di Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant) quando viene creato l'account di Azure dell'organizzazione e l'amministratore account viene aggiunto come [amministratore globale di Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). L'organizzazione può scegliere un altro utente per gestire l'identità utente [assegnando il ruolo di amministratore globale di Azure AD a tale utente](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal).
    - Sottoscrizioni, che richiedono che tali utenti:
        - Gestire i costi associati all'utilizzo delle risorse nella sottoscrizione.
        - Implementare e gestire il modello di autorizzazione minima per l'accesso alle risorse.
        - Tengano traccia dei limiti dei servizi.
    - Servizi di infrastruttura condivisi (se l'organizzazione decide di usare questo modello), che richiedono che l'utente sia responsabile di:
        - Connettività di rete da sito locale ad Azure.
        - Proprietà della connettività di rete all'interno di Azure tramite il peering reti virtuali.
    - Proprietari dei carichi di lavoro.
3. L'amministratore globale di Azure AD [crea i nuovi account utente](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory) per:
    - La persona che sarà il **proprietario della sottoscrizione** per ogni sottoscrizione associata a ogni ambiente. Si noti che questo è necessario solo se l'**amministratore del servizio** di sottoscrizione non ha il compito di gestire l'accesso alle risorse per ogni sottoscrizione/ambiente.
    - Persona che sarà l'utente delle **operazioni di rete**.
    - Le persone che sono i **proprietari dei carichi di lavoro**.
4. L'amministratore account di Azure crea le tre sottoscrizioni seguenti usando il [portale degli account di Azure](https://account.azure.com):
    - Sottoscrizione per l'ambiente di **infrastruttura condivisa** .
    - Sottoscrizione per l'ambiente di **produzione** .
    - Una sottoscrizione per l'ambiente di **sviluppo**.
5. L'amministratore account di Azure [aggiunge il proprietario del servizio di sottoscrizione a ogni sottoscrizione](https://docs.microsoft.com/azure/billing/billing-add-change-azure-subscription-administrator#to-assign-a-user-as-an-administrator).
6. Creare un processo di approvazione per i **proprietari dei carichi di lavoro** per richiedere la creazione dei gruppi di risorse. Il processo di approvazione può essere implementato in molti modi, ad esempio tramite posta elettronica oppure usando uno strumento di gestione dei processi come i [flussi di lavoro di SharePoint](https://support.office.com/article/introduction-to-sharepoint-workflow-07982276-54e8-4e17-8699-5056eff4d9e3). Il processo di approvazione può seguire questi passaggi:
    - Il **proprietario del carico di lavoro** prepara una distinta base per le risorse di Azure necessarie nell'ambiente di **sviluppo**, di **produzione** o in entrambi e la invia al **proprietario della sottoscrizione**.
    - Il **proprietario della sottoscrizione** esamina la distinta base e convalida le risorse richieste per garantire che siano appropriate per l'uso previsto, ad esempio verificando che le [dimensioni delle macchine virtuali](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) richieste siano corrette.
    - Se la richiesta non viene approvata, viene inviata una notifica al **proprietario del carico di lavoro**. Se la richiesta viene approvata, il **proprietario della sottoscrizione** [crea il gruppo di risorse richiesto](https://docs.microsoft.com/azure/azure-resource-manager/manage-resource-groups-portal#create-resource-groups) seguendo le [convenzioni di denominazione](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) dell'organizzazione, [aggiunge il **proprietario del carico di lavoro**](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal#add-a-role-assignment) con il [**ruolo di collaboratore** ](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor)e invia una notifica al **proprietario del carico di lavoro** per comunicare che il gruppo di risorse è stato creato.
7. Creare un processo di approvazione per i proprietari del carico di lavoro per richiedere una connessione peering reti virtuali dal proprietario dell'infrastruttura condivisa. Come con il passaggio precedente, questo processo di approvazione può essere implementato tramite posta elettronica o tramite uno strumento di gestione dei processi.

Ora che il modello di governance è stato implementato, è possibile distribuire i servizi di infrastruttura condivisa.

## <a name="related-resources"></a>Risorse correlate

[Ruoli predefiniti per le risorse di Azure](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Altre informazioni sulla distribuzione di un'infrastruttura di base](../../infrastructure/virtual-machines/basic-workload.md)
