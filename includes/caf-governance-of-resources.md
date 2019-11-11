<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->
> [!NOTE]
>In caso di modifiche dei requisiti aziendali, i gruppi di gestione di Azure consentono di riorganizzare facilmente la gerarchia di gestione e le assegnazioni dei gruppi di sottoscrizioni. Tenere presente, tuttavia, che le assegnazioni di criteri e ruoli applicate a un gruppo di gestione vengono ereditate da tutte le sottoscrizioni al di sotto di tale gruppo nella gerarchia. Se si prevede di riassegnare le sottoscrizioni tra i gruppi di gestione, assicurarsi di essere a conoscenza di eventuali modifiche di assegnazione dei criteri e dei ruoli che potrebbero derivarne. Per altre informazioni, vedere la [documentazione dei gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups).

### <a name="governance-of-resources"></a>Governance delle risorse

Un set di criteri e ruoli di controllo degli accessi in base al ruolo globali fornirà un livello di base per l'imposizione della governance. Per soddisfare i requisiti dei criteri del team di governance del cloud, l'implementazione di una soluzione MVP per la governance richiede il completamento delle attività seguenti:

1. Identificare le definizioni personalizzate di Criteri di Azure necessarie per imporre i requisiti aziendali. Tale attività può includere l'uso di definizioni predefinite e la creazione di nuove definizioni personalizzate.
2. Creare una definizione di progetto usando questi criteri predefiniti e personalizzati nonché le assegnazioni di ruolo personalizzate richiede dall'MVP per la governance.
3. Applicare criteri e configurazione a livello globale assegnando la definizione del progetto a tutte le sottoscrizioni.

#### <a name="identify-policy-definitions"></a>Identificare le definizioni dei criteri

Azure offre vari criteri e definizioni di ruolo predefiniti che è possibile assegnare a qualsiasi gruppo di gestione, sottoscrizione o gruppo di risorse. È possibile gestire molti requisiti di governance comuni con le definizioni predefinite. Tuttavia, è probabile che sarà anche necessario creare definizioni di criteri personalizzate per gestire esigenze specifiche.

Le definizioni di criteri personalizzate vengono salvate in un gruppo di gestione o in una sottoscrizione e vengono ereditate tramite la gerarchia dei gruppi di gestione. Se la posizione di salvataggio di una definizione di criteri è un gruppo di gestione, tale definizione è disponibile per l'assegnazione a qualsiasi gruppo di gestione o sottoscrizione figlio di tale gruppo.

Dal momento che i criteri richiesti per supportare l'MVP per la governance sono progettati per l'applicazione a tutte le sottoscrizioni correnti, i requisiti aziendali seguenti verranno implementati usando una combinazione di definizioni predefinite e definizioni personalizzate create nel gruppo di gestione radice:

1. Limitare l'elenco delle assegnazioni di ruolo disponibili a un set di ruoli predefiniti di Azure autorizzato dal team di governance del cloud. A questo scopo, è necessaria una [definizione di criteri personalizzata](https://github.com/Azure/azure-policy/tree/master/samples/Authorization/allowed-role-definitions).
2. Richiedere i tag seguenti per tutte le risorse: *reparto/unità di fatturazione*, *area geografica*, *classificazione dei dati*, *criticità*, *contratto di servizio*, *ambiente*, *archetipo di applicazione*, *applicazione* e *proprietario dell'applicazione*. Per gestire questa situazione, è possibile usare la definizione predefinita `Require specified tag`.
3. È necessario che il tag `Application` per le risorse abbia un nome corrispondente a quello del gruppo di risorse pertinente. Per gestire questa situazione, è possibile usare la definizione predefinita "Richiedi tag e relativo valore".

Per informazioni sulla definizione di criteri personalizzati, vedere la [documentazione di Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/tutorials/create-custom-policy-definition). Per istruzioni ed esempi di criteri personalizzati, vedere il [sito degli esempi di criteri di Azure](https://docs.microsoft.com/azure/governance/policy/samples) e il [repository di GitHub](https://github.com/Azure/azure-policy) associato.

#### <a name="assign-azure-policy-and-rbac-roles-using-azure-blueprints"></a>Assegnare criteri di Azure e ruoli di controllo degli accessi in base al ruolo tramite Azure Blueprints

È possibile assegnare i criteri di Azure a livello di gruppo di risorse, sottoscrizione e gruppo di gestione e includerli nelle definizioni di [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview). Anche se i requisiti dei criteri definiti in questo MVP per la governance si applicano a tutte le sottoscrizioni correnti, è molto probabile che le distribuzioni future richiedano eccezioni o criteri alternativi. Di conseguenza, l'assegnazione di criteri tramite i gruppi di gestione, con tutte le sottoscrizioni figlio che ereditano queste assegnazioni, potrebbe non essere sufficientemente flessibile per supportare questi scenari.

I progetti Azure Blueprints consentono l'assegnazione coerente di criteri e ruoli, l'applicazione di modelli di Resource Manager e la distribuzione di gruppi di risorse tra più sottoscrizioni. Come per le definizioni dei criteri, le definizioni di progetto vengono salvate nei gruppi di gestione o nelle sottoscrizioni e sono disponibili tramite ereditarietà per qualsiasi elemento figlio nella gerarchia dei gruppi di gestione.

Il team di governance del cloud ha deciso che l'applicazione delle assegnazioni di criteri di Azure e di controllo degli accessi in base al ruolo necessarie tra le sottoscrizioni verrà implementata tramite Azure Blueprints e gli artefatti associati:

1. Nel gruppo di gestione radice creare una definizione di progetto denominata `governance-baseline`.
2. Aggiungere gli artefatti del progetto seguenti alla definizione di progetto:
    1. Assegnazioni dei criteri per le definizioni di criteri di Azure personalizzate definite a livello della radice del gruppo di gestione.
    2. Definizioni dei gruppi di risorse per tutti i gruppi necessari nelle sottoscrizioni creati o gestiti dall'MVP per la governance.
    3. Assegnazioni di ruolo standard necessarie nelle sottoscrizioni create o gestite dall'MVP per la governance.
3. Pubblicare la definizione del progetto.
4. Assegnare la definizione del progetto `governance-baseline` a tutte le sottoscrizioni.

Vedere le [documentazione di Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) per altre informazioni sulla creazione e l'uso delle definizioni di progetto.

### <a name="secure-hybrid-vnet"></a>Rete virtuale ibrida protetta

Accade spesso che specifiche sottoscrizioni richiedano un certo livello di accesso alle risorse locali. Questo è comune negli scenari di migrazione o sviluppo in cui risorse dipendenti risiedono nel data center locale.

Fino a quando non viene stabilita l'attendibilità completa nell'ambiente cloud, è importante controllare e monitorare con grande attenzione qualsiasi comunicazione tra l'ambiente locale e i carichi di lavoro nel cloud e assicurarsi che la rete locale sia protetta da possibili accessi non autorizzati da risorse basate sul cloud. Per supportare questi scenari, l'MVP per la governance aggiunge le procedure consigliate seguenti:

1. Creare una rete virtuale ibrida protetta cloud.
    1. L'[architettura di riferimento di una VPN nel cloud](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn) definisce un modello di distribuzione per la creazione di un gateway VPN in Azure.
    2. Verificare che i meccanismi di gestione della sicurezza e del traffico locali considerino le reti cloud connesse come non attendibili. Le risorse e i servizi ospitati nel cloud devono avere accesso solo a servizi locali autorizzati.
    3. Verificare che il dispositivo perimetrale locale nel data center locale sia compatibile con i [requisiti del gateway VPN di Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices) e sia configurato per l'accesso a Internet pubblico.
    4. Si noti che i tunnel VPN non devono essere considerati circuiti pronti per la produzione per tutto tranne i carichi di lavoro più semplici. Per qualsiasi esigenza che vada oltre alcuni semplici carichi di lavoro con connettività locale, è consigliabile usare Azure ExpressRoute.
1. Nel gruppo di gestione radice creare una seconda definizione di progetto denominata `secure-hybrid-vnet`.
    1. Aggiungere il modello di Resource Manager per Gateway VPN come artefatto della definizione del progetto.
    2. Aggiungere il modello di Resource Manager per la rete virtuale come artefatto della definizione del progetto.
    3. Pubblicare la definizione del progetto.
1. Assegnare la definizione del progetto `secure-hybrid-vnet` a tutte le sottoscrizioni che richiedono la connettività locale. Questa definizione deve essere assegnata in aggiunta alla definizione del progetto `governance-baseline`.

Una delle principali preoccupazioni espresse dai team di sicurezza IT e di governance tradizionale è il rischio che nella fase iniziale di adozione del cloud vengano compromessi asset esistenti. L'approccio sopra descritto consente ai team di adozione del cloud di creare ed eseguire la migrazione di soluzioni ibride, con meno rischi per gli asset locali. Evoluzioni successive dell'ambiente cloud che ne migliorano l'attendibilità possono consentire la rimozione di questa soluzione temporanea.

> [!NOTE]
> Questo approccio costituisce un punto di partenza per creare rapidamente un MVP per la governance della baseline, ma è solo l'inizio del percorso di governance. Sarà infatti necessaria un'evoluzione successiva man mano che l'azienda prosegue il processo di adozione del cloud e aumentano i rischi nelle aree seguenti:
>
> - Carichi di lavoro cruciali
> - Dati protetti
> - Gestione dei costi
> - Scenari multi-cloud
>
> I dettagli specifici di questo MVP sono basati inoltre sul percorso di esempio di una società fittizia descritto negli articoli seguenti. Prima di implementare questa procedura consigliata è opportuno acquisire familiarità con gli altri articoli di questa serie.
