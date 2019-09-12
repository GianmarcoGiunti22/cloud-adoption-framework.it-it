<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="policy-statements"></a>Policy statements

Le seguenti istruzioni dei criteri stabiliscono i requisiti necessari per correggere i rischi definiti. Questi criteri definiscono i requisiti funzionali per il prodotto minimo funzionante (MVP, Minimum Viable Product) per la governance. Ognuno sarà rappresentato nell'implementazione dell'MVP per la governance.

Gestione costi:

- per motivi di rilevamento, tutti gli asset devono essere assegnati a un proprietario dell'applicazione all'interno di una delle funzioni aziendali principali.
- Quando si verificano problemi relativi ai costi, verranno stabiliti altri requisiti di governance per il team finanziario.

Baseline di sicurezza:

- qualsiasi asset distribuito nel cloud deve avere una classificazione dei dati approvata.
- Nessun asset identificato con un livello di dati protetto può essere distribuito nel cloud, finché non possono essere approvati e implementati i requisiti minimi per la sicurezza e la governance.
- Fino a quando non è possibile convalidare e governare i requisiti minimi di sicurezza della rete, gli ambienti cloud vengono considerati come una zona demilitarizzata e devono soddisfare requisiti di connessione simili ad altri Data Center o reti interne.

Coerenza delle risorse:

- poiché in questa fase non vengono distribuiti carichi di lavoro di importanza strategica, non sussistono requisiti da disciplinare relativi a Contratti di servizio, prestazioni o continuità aziendale e ripristino di emergenza.
- Quando vengono distribuiti carichi di lavoro cruciali, verranno stabiliti ulteriori requisiti di governance con il reparto IT.

Baseline di identità:

- tutti gli asset distribuiti nel cloud devono essere controllati tramite identità e ruoli approvati da criteri di governance correnti.
- tutti i gruppi con privilegi elevati nell'infrastruttura di Active Directory Domain Services locale dovrebbero essere associati a un ruolo di controllo approvato degli accessi in base al ruolo.

Accelerazione della distribuzione:

- tutte le risorse devono essere raggruppate e contrassegnate in base a strategie definite di raggruppamento e assegnazione dei tag.
- Tutti gli asset devono usare un modello di distribuzione approvato.
- Una volta stabilita una base di governance per un provider di servizi cloud, eventuali strumenti di distribuzione devono essere compatibili con quelli definiti dal team di governance.

## <a name="processes"></a>Processi

Non è stato allocato alcun budget per il monitoraggio e l'applicazione continui di questi criteri di governance. Per questo motivo, il team di governance del cloud ha alcuni modi ad hoc per monitorare l'aderenza alle istruzioni dei criteri.

- **Istruzione** Il team di governance del cloud sta investendo tempo per istruire i team di adozione del cloud sulle guide di governance che supportano questi criteri.
- **Revisioni della distribuzione:** Prima di distribuire qualsiasi asset, il team di governance del Cloud esamina la guida alla governance con i team di adozione del cloud.
