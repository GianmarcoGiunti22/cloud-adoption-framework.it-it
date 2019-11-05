<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="dependent-decisions"></a>Decisioni dipendenti

Le decisioni seguenti provengono da team esterni al team di governance del cloud. che si occuperanno anche della loro implementazione. Tuttavia, il team di governance del cloud è responsabile dell'implementazione di una soluzione per verificare che tali implementazioni vengano applicate in modo coerente.

### <a name="identity-baseline"></a>Baseline di identità

La baseline di identità è un requisito iniziale indispensabile per tutte le azioni di governance. Prima di tentare di applicare la governance, è infatti necessario definire l'identità. La strategia di identità definita verrà quindi applicata dalle soluzioni di governance.
In questa guida alla governance, il team di gestione delle identità implementa il modello di **[sincronizzazione della directory](~/decision-guides/identity/index.md#directory-synchronization)** :

- Il controllo degli accessi in base al ruolo verrà fornito da Azure Active Directory (Azure AD), usando la sincronizzazione della directory o "lo stesso accesso" implementato durante la migrazione dell'azienda a Office 365. Per altre informazioni sull'implementazione, vedere [Architettura di riferimento per l'integrazione di Azure AD](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
- Il tenant di Azure AD controllerà anche l'autenticazione e l'accesso degli asset distribuiti in Azure.

Nell'MVP della governance, il team di governance imporrà l'applicazione del tenant replicato tramite gli strumenti di governance delle sottoscrizioni, descritti più avanti in questo articolo. Nelle iterazioni future il team di governance potrebbe inoltre applicare strumenti avanzati in Azure AD per estendere questa funzionalità.

### <a name="security-baseline-networking"></a>Baseline di sicurezza: rete

La rete definita dal software è un aspetto iniziale importante della baseline di sicurezza. La definizione dell'MVP di governance dipende dalle decisioni iniziali del team di gestione della sicurezza, che stabilisce le modalità di configurazione sicura delle reti.

Data la mancanza di requisiti, la protezione IT è sicura e richiede un modello di rete perimetrale **[cloud](~/decision-guides/software-defined-network/cloud-dmz.md)** . La governance delle distribuzioni Azure risulterà quindi poco intensa.

- Le sottoscrizioni di Azure possono connettersi a un data center esistente tramite VPN, ma devono seguire tutti i criteri di governance IT locali esistenti relativi alla connessione di una zona demilitarizzata a risorse protette. Per altre informazioni sull'implementazione relative alla connettività VPN, vedere [Architettura di riferimento di una rete VPN](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn).
- Le decisioni relative alla subnet, al firewall e al routing vengono affidate al responsabile di ogni applicazione/carico di lavoro.
- È necessario eseguire ulteriori analisi prima del rilascio di eventuali dati protetti o carichi di lavoro cruciali.

In questo modello le reti cloud possono connettersi solo a risorse locali tramite una VPN esistente compatibile con Azure. Il traffico della connessione verrà considerato come qualsiasi altro tipo di traffico proveniente da una rete perimetrale. Per gestire in sicurezza il traffico proveniente da Azure è possibile che siano necessarie considerazioni aggiuntive sul dispositivo perimetrale locale.

Il team di governance del cloud ha invitato in modo proattivo i membri dei team di rete e della sicurezza IT a riunioni regolari, al fine di mantenere le richieste di rete e i rischi.

### <a name="security-baseline-encryption"></a>Baseline di sicurezza: crittografia

La crittografia è un'altra decisione fondamentale relativa alla disciplina sulla baseline di sicurezza. Considerando che l'azienda non archivia ancora dati protetti nel cloud, il team di sicurezza ha optato per un modello di crittografia meno aggressivo.
A questo punto, un **[modello nativo del cloud per la crittografia](~/decision-guides/encryption/index.md#key-management)** è consigliato ma non obbligatorio per alcun team di sviluppo.

- In merito all'uso della crittografia, non sono stati definiti requisiti di governance perché i criteri aziendali correnti non consentono l'archiviazione nel cloud di dati protetti o cruciali.
- Prima di rilasciare i dati protetti o i carichi di lavoro cruciali, sarà necessaria un'ulteriore analisi.

## <a name="policy-enforcement"></a>Imposizione dei criteri

La prima decisione da prendere in merito all'accelerazione della distribuzione riguarda il modello di applicazione. In questa descrizione, il team di governance ha deciso di implementare il modello di **[imposizione automatizzato](~/decision-guides/policy-enforcement/index.md#automated-enforcement)** .

- I team di sicurezza e identità potranno usufruire del Centro sicurezza di Azure per monitorare i rischi di sicurezza. Entrambi i team possono anche usare il Centro sicurezza per identificare nuovi rischi e migliorare i criteri aziendali.
- In tutte le sottoscrizioni è obbligatorio il controllo degli accessi in base al ruolo per controllare l'applicazione dell'autenticazione.
- In ogni gruppo verrà inoltre pubblicato Criteri di Azure, che verrà applicato a tutte le sottoscrizioni. Il livello dei criteri applicati sarà tuttavia limitato in questo MVP per la governance iniziale.
- Anche se vengono usati gruppi di gestione di Azure, è prevista una gerarchia relativamente semplice.
- Verranno usati progetti Azure Blueprints per distribuire e aggiornare le sottoscrizioni tramite l'applicazione di requisiti di controllo degli accessi in base al ruolo, modelli di Resource Manager e Criteri di Azure nei vari gruppi di gestione.

## <a name="apply-the-dependent-patterns"></a>Applicare i modelli dipendenti

Le decisioni seguenti rappresentano i modelli da applicare tramite la strategia di applicazione dei criteri sopra descritta:

**Linea di base identità.** I progetti Azure Blueprints definiranno i requisiti di controllo degli accessi in base al ruolo a livello di sottoscrizione per garantire che in tutte le sottoscrizioni sia configurata un'identità coerente.

**Baseline di sicurezza: rete.** Il team di governance del cloud gestisce un modello di Gestione risorse per stabilire un gateway VPN tra Azure e il dispositivo VPN locale. Quando un team di applicazioni richiede una connessione VPN, il team di governance del cloud applicherà il modello di Gestione risorse gateway tramite i progetti di Azure.

**Baseline di sicurezza: crittografia.** A questo punto, in quest'area non è necessaria l'applicazione dei criteri. Questa operazione verrà rivisitata durante le iterazioni successive.
