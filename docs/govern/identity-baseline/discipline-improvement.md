---
title: Miglioramento della disciplina Baseline di identità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Miglioramento della disciplina Baseline di identità
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 265365d2064349f53d61b10af4af053c418c871a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547458"
---
# <a name="identity-baseline-discipline-improvement"></a>Miglioramento della disciplina Baseline di identità

La disciplina Baseline di identità è incentrata sulle modalità di definizione dei criteri che garantiscono la coerenza e la continuità delle identità utente, indipendentemente dal provider di servizi cloud che ospita l'applicazione o il flusso di lavoro. All'interno delle cinque discipline di Governance Cloud, la Baseline di identità include le decisioni relative a [Hybrid Identity Strategy (Strategia di identità ibrida)](../../decision-guides/identity/index.md), valutazione ed estensione dei repository di identità, implementazione di Single Sign-On (same sign-on), controllo e monitoraggio per usi non autorizzati o attori malintenzionati. In alcuni casi, potrebbe inoltre comportare decisioni per modernizzare, consolidare o integrare più provider di identità.

Questo articolo delinea alcune attività potenziali che l'azienda può svolgere al fine di sviluppare ed evolvere al meglio la disciplina Baseline di identità. Queste attività possono essere suddivise nelle fasi di pianificazione, costruzione, adozione e funzionamento dell'implementazione di una soluzione cloud, che vengono poi ripetute per consentire lo sviluppo di un [incremental approach to cloud governance (approccio incrementale alla governance del cloud)](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quattro fasi di adozione](../../_images/govern/adoption-phases.png)

*Figura 1-fasi di adozione dell'approccio incrementale alla governance del cloud.*

È impossibile tener conto per qualsiasi documento dei requisiti di tutte le aziende. Di conseguenza, questo articolo delinea le attività di esempio minime e potenziali suggerite per ogni fase del processo di maturazione della governance. L'obiettivo iniziale di queste attività è quello di semplificare la creazione di un [criterio MVP](../guides/index.md#an-incremental-approach-to-cloud-governance) e stabilire un Framework per migliorare i criteri incrementali. Il team di governance del cloud dovrà decidere quanto investire in queste attività per migliorare le funzionalità di governance della linea di base di identità.

> [!CAUTION]
> Né le attività minime o potenziali descritte in questo articolo sono allineate a criteri aziendali specifici o a requisiti di conformità di terze parti. Queste linee guida sono state progettate per facilitare le conversazioni che porteranno all'allineamento di entrambi i requisiti con un modello di governance del cloud.

## <a name="planning-and-readiness"></a>Pianificazione e preparazione

Questa fase di maturità della governance colma il divario tra i risultati aziendali e le strategie attuabili. Durante questo processo, il team di leadership definisce metriche specifiche, associa tali metriche al patrimonio digitale e inizia a pianificare l'impegno complessivo richiesto per la migrazione.

**Attività minime suggerite:**

- Valutare la [Identity toolchain (Toolchain di identità)](./toolchain.md) e implementare una strategia ibrida adatta alla propria organizzazione.
- Sviluppare una bozza di documento relativo alle linee guida sull'architettura e distribuirla ai principali stakeholder.
- Formare e coinvolgere le persone e i team interessati allo sviluppo delle linee guida sull'architettura.

**Attività potenziali:**

- Definire i ruoli e le assegnazioni che regolano l'identità e la gestione dell'accesso nel cloud.
- Definire i gruppi in locale ed associarli ai ruoli corrispondenti basati sul cloud.
- Provider di identità di inventario (incluse le identità basate su database usate da applicazioni personalizzate).
- Consolidare e integrare i provider di identità laddove esiste la duplicazione, per semplificare la soluzione di identità complessiva e ridurre i rischi.
- Valutare la compatibilità ibrida di provider di identità esistenti.
- Per i provider di identità che non sono ibrido compatibili, valutare le opzioni di sostituzione o di consolidamento.

## <a name="build-and-predeployment"></a>Compilazione e pre-distribuzione

Per eseguire correttamente la migrazione di un ambiente, sono necessari diversi prerequisiti tecnici e non tecnici. Questo processo riguarda principalmente le decisioni, la conformità e l'infrastruttura di base preliminari a una migrazione.

**Attività minime suggerite:**

- Prendere in considerazione un test pilota prima di implementare la [Identity toolchain (Toolchain di identità)](./toolchain.md), assicurandosi che semplifichi l'esperienza utente il più possibile.
- Applicare il feedback dei test pilota nella pre-distribuzione. Ripetere fino a quando i risultati sono accettabili.
- Aggiornare il documento sulle linee guida dell'architettura per includere piani di distribuzione e adozione da parte degli utenti e per distribuirlo ai principali stakeholder.
- Prendere in considerazione la definizione di un programma early adopter e distribuire un numero limitato di utenti.
- Continuare a formare le persone e i team più interessati alle linee guida dell'architettura.

**Attività potenziali:**

- Valutare l'architettura logica e fisica e determinare una [Hybrid Identity Strategy (Strategia di identità ibrida)](../../decision-guides/identity/index.md).
- Eseguire l'associazione dei criteri di gestione di accesso alle identità, ad esempio le assegnazioni di ID di accesso, quindi scegliere il metodo di autenticazione appropriato per Azure AD.
  - Se federati, abilitare restrizioni dei tenant per gli account amministrativi.
- Integrare le directory locali e il cloud.
- È consigliabile usare i modelli di accesso seguenti:
  - Modello [di accesso con privilegi minimi](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) .
  - Modello di accesso di [base di identità con privilegi](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure) .
- Finalizzare tutti i dettagli di preintegrazione ed esaminare le [procedure consigliate](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices)per l'identità.
  - Abilitare identità singola, Single Sign-On (SSO) o seamless SSO.
  - Configurare la funzionalità di autenticazione a più fattori per gli amministratori.
  - Consolidare o integrare i provider di identità, se necessario.
  - Implementare gli strumenti necessari per centralizzare la gestione delle identità.
  - Abilitare l'accesso just-in-time (JIT) e gli avvisi di modifica del ruolo.
  - Eseguire un'analisi dei rischi delle attività amministrative chiave per l'assegnazione ai ruoli predefiniti.
  - Si consideri un'implementazione aggiornata di un'autenticazione più avanzata per tutti gli utenti.
  - Abilitare Privileged Identity Baseline (PIM) per JIT (usando l'attivazione limitata al tempo) per altri ruoli amministrativi.
  - Separare gli account utente dagli account di amministratore globale (per assicurarsi che gli amministratori non aprano inavvertitamente i messaggi di posta elettronica o eseguano programmi associati agli account di amministratore globale).

## <a name="adopt-and-migrate"></a>Adottare ed eseguire la migrazione

La migrazione è un processo incrementale incentrato sullo spostamento, il testing e l'adozione di applicazioni o carichi di lavoro in un patrimonio digitale esistente.

**Attività minime suggerite:**

- Eseguire la migrazione della [Identity toolchain (Toolchain di identità)](./toolchain.md) dallo sviluppo alla produzione.
- Aggiornare il documento relativo alle linee guida sull'architettura e distribuirlo ai principali stakeholder.
- Sviluppare materiali didattici e documentazione, comunicazioni di sensibilizzazione, incentivi e altri programmi per guidare l'adozione da parte degli utenti.

**Attività potenziali:**

- Verificare che le procedure consigliate definite durante le fasi di pre-distribuzione della compilazione siano eseguite correttamente.
- Convalidare e perfezionare la [strategia di identità ibrida](../../decision-guides/identity/index.md).
- Assicurarsi che ogni applicazione o carico di lavoro continui l'allineamento alla strategia di identità prima del rilascio.
- Verificare che Single Sign-On (SSO) e l'accesso SSO facile funzionino come previsto dalle applicazioni.
- Ridurre o eliminare il numero di archivi di identità alternativi.
- Esaminare la necessità per ogni archivio identità nell'app o nel database. Le identità che si trovano all'esterno di un provider di identità appropriato (proprio o di terze parti) possono rappresentare rischi per l'applicazione e gli utenti.
- Abilitare l'accesso condizionale per le [Applicazioni federate locali](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup).
- Distribuire identità tra le aree globali in più hub con sincronizzazione tra le aree.
- Stabilire la federazione di controllo centrale degli accessi in base al ruolo (RBAC).

## <a name="operate-and-post-implementation"></a>Operazioni e post-implementazione

Al termine della trasformazione, la governance e le operazioni devono continuare a funzionare per il ciclo di vita naturale di un'applicazione o di un carico di lavoro. Questa fase di maturità della governance si basa principalmente sulle attività che vengono svolte in genere dopo che la soluzione è stata implementata e il ciclo di trasformazione ha iniziato a stabilizzarsi.

**Attività minime suggerite:**

- Personalizzare la [linea di base di riferimento](./toolchain.md) per le identità in base alle modifiche apportate alle esigenze di identità mutevoli dell'organizzazione.
- Automatizzare le notifiche e i report in modo che possano avvisare su potenziali minacce.
- Monitorare e creare report sullo stato di uso del sistema e di adozione da parte dell'utente.
- Creare report sulle metriche di post-distribuzione e distribuirle agli stakeholder.
- Perfezionare le linee guida sull'architettura per guidare i processi di adozione futura.
- Comunicare e dedicarsi periodicamente alla formazione continua dei team interessati per garantire il rispetto costante delle linee guida sull'architettura.

**Attività potenziali:**

- Eseguire controlli periodici dei criteri di identità e delle prassi di conformità.
- Assicurarsi che gli account utente sensibili (CEO, CFO, VP e così via) siano sempre abilitati per l'autenticazione a più fattori e il rilevamento anomalo degli accessi.
- Analizzare regolarmente gli attori malintenzionati e le violazioni dei dati, in particolare quelli correlati a furti di identità, ad esempio potenziali acquisizioni di account amministratore.
- Configurare uno strumento di monitoraggio e creazione di report.
- Prendere in considerazione minuziosamente l'integrazione con sistemi di prevenzione delle frodi e sicurezza.
- Esaminare regolarmente i diritti di accesso per utenti con privilegi o ruoli elevati.
  - Identificare tutti gli utenti idonei per attivare i privilegi di amministratore.
- Esaminare l'onboarding, l'offboarding e i processi di aggiornamento della credenziali.
- Verificare i livelli crescenti di automazione e la comunicazione tra i moduli di gestione delle identità e degli accessi (IAM).
- Prendere in considerazione di implementare un approccio di sviluppo delle operazioni di sicurezza (DevSecOps).
- Eseguire un'analisi di impatto per misurare i risultati su costi, sicurezza e adozione utente.
- Presentare periodicamente un report di impatto che mostri le modifiche delle metriche create dal sistema e stimare l'impatto aziendale della [Hybrid Identity Strategy (Strategia di identità ibrida)](../../decision-guides/identity/index.md).
- Stabilire un monitoraggio integrato consigliato dal [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-intro).

## <a name="next-steps"></a>Passaggi successivi

Una volta compreso il concetto di governance dell'identità del cloud, esaminare il [toolchain della Baseline di identità](./toolchain.md) per identificare gli strumenti e le funzionalità di Azure di cui si avrà bisogno per sviluppare la disciplina di governance della Baseline di identità sulla piattaforma Azure.

> [!div class="nextstepaction"]
> [Toolchain della Baseline di identità per Azure](./toolchain.md)
