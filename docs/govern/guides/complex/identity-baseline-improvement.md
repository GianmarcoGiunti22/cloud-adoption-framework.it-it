---
title: 'Guida governance per le aziende complesse: migliorare la disciplina della linea di base di identità'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida governance per le aziende complesse: migliorare la disciplina della linea di base di identità'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/06/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8c64507c03a99ef771f7885dc8fbde960c570e4d
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566318"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-identity-baseline-discipline"></a>Guida governance per le aziende complesse: migliorare la disciplina della linea di base di identità

Questo articolo fa avanzare il racconto aggiungendo i controlli di base di identità all'MVP governance.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

La motivazione aziendale per la migrazione al cloud dei due data center è stata approvata dal CFO. Durante lo studio di fattibilità tecnica sono stati individuati diversi ostacoli:

- I dati protetti e le applicazioni cruciali rappresentano 25% dei carichi di lavoro nei due data center. Nessuno dei due può essere eliminato fino a quando non sono stati modernizzati i criteri di governance correnti relativi ai dati personali sensibili e alle applicazioni di importanza critica.
- Il 7% degli asset in quei data center non è compatibile con il cloud. Verranno spostati in un data center alternativo prima della risoluzione del contratto del data center.
- Il 15% degli asset nel data center (750 macchine virtuali) ha una dipendenza da sistemi di autenticazione legacy o di autenticazione a più fattori di terze parti.
- La connessione VPN tra Azure e i data center esistenti non offre velocità di trasmissione dei dati o latenza sufficiente per eseguire la migrazione dell'intero volume degli asset entro i due anni previsti per il ritiro del data center.

I primi due blocchi stradali vengono gestiti in parallelo. Questo articolo illustra la risoluzione del terzo e del quarto ostacolo.

### <a name="expand-the-cloud-governance-team"></a>Espandi il team di governance del cloud

Il team di governance del cloud è in espansione. Data la necessità di ulteriore supporto in merito alla gestione delle identità, un amministratore di sistemi del team addetto alla baseline di identità ora partecipa a una riunione settimanale per mantenere i membri del team al corrente dei cambiamenti.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

Il team IT ha ricevuto l'approvazione a procedere con i piani del CIO e del CFO per il ritiro di due data center. Tuttavia, la preoccupazione dell'IT è che il 750 (il 15%) degli asset in tali data center dovrà essere spostato in una posizione diversa dal cloud.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

I nuovi piani per lo stato futuro richiedono una soluzione più solida per la baseline di identità, per eseguire la migrazione delle 750 macchine virtuali con requisiti di autenticazione legacy. Oltre a questi due Data Center, è previsto che questa sfida influisca su percentuali simili di asset in altri Data Center.

Lo stato futuro richiede ora anche una connessione dal provider di servizi cloud alla soluzione MPLS/lease-line della società.

I cambiamenti che riguardano lo stato attuale e quello futuro creano nuovi rischi che richiederanno nuove definizioni di criteri.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Interruzione aziendale durante la migrazione.** La migrazione al cloud crea un rischio controllato e limitato nel tempo, che può essere gestito. Lo spostamento dell'hardware obsolescente in un'altra parte del mondo comporta rischi molto maggiori. È necessaria una strategia di mitigazione dei rischi per evitare interruzioni delle operazioni aziendali.

**Dipendenze di identità esistenti.** Le dipendenze da servizi di autenticazione e gestione delle identità esistenti possono ritardare o impedire la migrazione di alcuni carichi di lavoro al cloud. La mancata restituzione dei due data center nei tempi previsti comporterà spese nell'ordine dei milioni di dollari in canoni di lease.

Questo rischio aziendale può tradursi in alcuni rischi tecnici:

- L'autenticazione legacy potrebbe non essere disponibile nel cloud, limitando la distribuzione di alcune applicazioni.
- La soluzione di autenticazione a più fattori di terze parti corrente potrebbe non essere disponibile nel cloud, limitando la distribuzione di alcune applicazioni.
- Il ristrumento o lo stato di trasferimento può creare interruzioni o aggiungere costi.
- La velocità e la stabilità della rete VPN potrebbero impedire la migrazione.
- Il traffico in ingresso nel cloud può causare problemi di sicurezza in altre parti della rete globale.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida.

- Il provider di servizi cloud scelto deve offrire un mezzo per l'autenticazione tramite i metodi legacy.
- Il provider di servizi cloud scelto deve offrire un mezzo di autenticazione con la soluzione di autenticazione a più fattori di terze parti corrente.
- È necessario stabilire una connessione privata ad alta velocità tra il provider di servizi cloud e il provider Telco della società, connettendo il provider di servizi cloud alla rete globale di Data Center.
- Finché non vengono stabiliti requisiti di sicurezza sufficienti, nessun tipo di traffico pubblico in ingresso può accedere agli asset aziendali ospitati nel cloud. Tutte le porte vengono bloccate per qualsiasi origine all'esterno della WAN globale.

## <a name="incremental-improvement-of-the-best-practices"></a>Miglioramento incrementale delle procedure consigliate

Il progetto di governance MVP cambia per includere nuovi criteri di Azure e un'implementazione di Active Directory in una macchina virtuale. Insieme, queste due modifiche di progettazione soddisfano le nuove definizioni dei criteri aziendali.

Ecco le nuove procedure consigliate:

- **Progetto VNet ibrido sicuro:** Il lato locale della rete ibrida deve essere configurato per consentire la comunicazione tra la soluzione seguente e i server Active Directory locali. La procedura consigliata richiede una rete perimetrale per abilitare Active Directory Domain Services attraverso i limiti di rete.
- **Modelli di Azure Resource Manager:**
    1. Definire un NSG per bloccare il traffico esterno e consentire il traffico interno.
    2. Distribuire due macchine virtuali Active Directory in una coppia con carico bilanciato in base a un'immagine dorata. Al primo avvio, l'immagine esegue uno script di PowerShell per eseguire l'aggiunta al dominio e la registrazione con i servizi di dominio. Per altre informazioni, vedere [Estendere Active Directory Domain Services in Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain).
- Criteri di Azure: applicare NSG a tutte le risorse.
- Azure Blueprints:
    1. Creare un progetto denominato `active-directory-virtual-machines`.
    2. Aggiungere tutti i modelli e i criteri di Active Directory al progetto.
    3. Pubblicare il progetto in qualsiasi gruppo di gestione applicabile.
    4. Applicare il progetto a qualsiasi sottoscrizione che richiede l'autenticazione a più fattori legacy o di terze parti.
    5. È ora possibile usare l'istanza di Active Directory in esecuzione in Azure come estensione della soluzione Active Directory locale, in modo da consentire l'integrazione con lo strumento di autenticazione a più fattori esistente e fornire l'autenticazione basata sulle attestazioni, tramite funzionalità di Active Directory esistente.

## <a name="conclusion"></a>Conclusione

L'aggiunta di queste modifiche all'MVP di governance consente di correggere molti dei rischi in questo articolo, consentendo a ogni team di adozione del cloud di spostarsi rapidamente oltre questo ostacolo.

## <a name="next-steps"></a>Passaggi successivi

Quando l'adozione del cloud continua e offre un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambieranno. Di seguito sono riportate alcune modifiche che possono verificarsi. Per questa società fittizia, il prossimo trigger è l'inclusione di dati protetti nel piano di adozione del cloud. Questa modifica richiede controlli di sicurezza aggiuntivi.

> [!div class="nextstepaction"]
> [Migliorare la disciplina della linea di base di sicurezza](./security-baseline-improvement.md)
