---
title: Elenco di controllo per l'ambito esteso della migrazione al cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Elenco di controllo per l'ambito esteso della migrazione al cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4daf4b01a2fde83de1040f224b8096475a24fe60
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224363"
---
# <a name="expanded-scope-for-cloud-migration"></a>Ambito esteso per la migrazione al cloud

La [guida alla migrazione ad Azure](../azure-migration-guide/index.md) in Cloud Adoption Framework è il punto di partenza consigliato per i lettori interessati a una migrazione con rehosting ad Azure, nota anche come migrazione "lift and shift". Tale guida presenta una serie di prerequisiti, strumenti e approcci per la migrazione di macchine virtuali al cloud.

Anche se questa guida è un punto di partenza efficace per acquisire familiarità con questo tipo di migrazione, si basa su svariati presupposti. Questi presupposti fanno sì che la guida sia utile per un'alta percentuale dei lettori di Cloud Adoption Framework, proponendo un approccio semplificato alle migrazioni. In questa sezione di Cloud Adoption Framework vengono presentati alcuni scenari di migrazione con ambito esteso e si tratta di informazioni utili per orientare i progetti a cui non si applicano tali presupposti.

## <a name="cloud-migration-expanded-scope-checklist"></a>Elenco di controllo per l'ambito esteso della migrazione al cloud

L'elenco di controllo seguente presenta alcune aree comuni di complessità che potrebbero richiedere l'estensione dell'ambito della migrazione oltre a quanto previsto dalla [guida alla migrazione ad Azure](../azure-migration-guide/index.md).

- **Modifiche di ambito dettate da necessità aziendali:**
  - [Bilanciamento del portfolio](./balance-the-portfolio.md)
  - [Supporto dei mercati globali](../../decision-guides/regions/index.md)
  - Consapevolezza dei costi durante una migrazione *(disponibile nel terzo trimestre del 2019)*
- **Modifiche di ambito determinate da esigenze culturali:**
  - Processi di gestione delle modifiche e di approvazione *(disponibile nel terzo trimestre del 2019)*
  - Disponibilità della dirigenza *(disponibile nel terzo trimestre del 2019)*
  - [Idoneità a livello di competenze](./suggested-skills.md)
  - Allineamento del supporto (partner, servizi e supporto) *(disponibile nel terzo trimestre del 2019)*
- **Modifiche di ambito determinate da strategie tecniche:**
  - Vincoli dei data center esistenti *(disponibile nel terzo trimestre del 2019)*
  - Migrazione su larga scala - Volumi elevati o velocità delle migrazioni *(disponibile nel terzo trimestre del 2019)*
  - [Più data center](./multiple-datacenters.md)
  - [Requisiti dei dati superiori alla capacità di rete](./network-capacity-exceeded.md)
  - Gestione delle modifiche e documentazione della soluzione *(disponibile nel terzo trimestre del 2019)*
  - [Strategia di governance o di conformità](./governance-or-compliance.md)
- **Modifiche di ambito specifiche dei carichi di lavoro:**
  - Progettare i carichi di lavoro per la resilienza *(disponibile nel terzo trimestre del 2019)*
  - Allineare la migrazione ai modelli di applicazione *(disponibile nel terzo trimestre del 2019)*

Se uno qualsiasi di questi aspetti più complessi rispecchia lo scenario di interesse, è probabile che questa sezione di Cloud Adoption Framework possa offrire il tipo di indicazioni necessarie per un corretto allineamento dell'ambito nei processi di migrazione.

Ognuno di questi scenari è presentato nei vari articoli in questa sezione di Cloud Adoption Framework.

## <a name="scope-options-explained"></a>Spiegazione delle opzioni disponibili per l'ambito

Per agevolare la comprensione di ogni scenario di estensione dell'ambito, l'elenco seguente riepilogherà brevemente i titoli usati nell'elenco di controllo precedente.

### <a name="business-driven-scope-changes"></a>Modifiche di ambito dettate da necessità aziendali

- **Bilanciamento del portfolio di adozione del cloud:** il team di strategia del cloud è interessato a destinare investimenti maggiori alla migrazione (rehosting di carichi di lavoro e applicazioni esistenti con modifiche minime) o all'innovazione (refactoring o ricostruzione di carichi di lavoro e applicazioni con tecnologie cloud moderne). Spesso, la chiave del successo è trovare un equilibrio tra queste due priorità. In questa guida, il bilanciamento del portfolio di adozione del cloud è un argomento comune e viene affrontato per ognuno dei processi di migrazione.
- **Supporto dei mercati globali:** l'azienda opera in più aree geografiche con requisiti di sovranità dei dati diversi. Per soddisfare tali requisiti, occorre tenere conto di considerazioni aggiuntive nella verifica dei prerequisiti e per la distribuzione degli asset durante la migrazione.

### <a name="culture-driven-scope-changes"></a>Modifiche di ambito determinate da esigenze culturali

- **Processi di gestione delle modifiche e di approvazione:** quando la cultura dell'organizzazione è complessa, basata su una struttura fortemente a matrice o isolata, i processi correlati alla gestione delle modifiche e all'approvazione diventano complessi. Indicazioni su come gestire questa complessità sono reperibili nei processi di valutazione, migrazione e ottimizzazione.
- **Disponibilità della dirigenza:** un livello appropriato di supporto esecutivo e leadership è fondamentale per il successo di un progetto di migrazione. Se il team dirigente non è pronto a impegnarsi, è improbabile che il supporto segua. Questa complessità viene affrontata durante i processi di definizione dei prerequisiti e di valutazione.
- **Idoneità a livello di competenze:** se il team di adozione del cloud o altri team di supporto non sono pronti per l'esecuzione, possono rapidamente subentrare complicazioni durante l'intero progetto di migrazione. Questo aspetto viene affrontato durante ognuno dei processi di migrazione in una pagina specifica per l'idoneità a livello di competenze.
- **Allineamento del supporto (partner, servizi e supporto):** all'interno di ognuno dei processi descritti, esistono modi in cui un partner, i servizi del fornitore del cloud e il supporto dal fornitore di cloud possono essere d'aiuto per l'esecuzione. In ognuna delle sezioni dedicate ai processi, le opzioni verranno illustrate in maggiore dettaglio in una pagina sull'allineamento del supporto.

### <a name="technical-strategy-driven-scope-changes"></a>Modifiche di ambito determinate da strategie tecniche

- **Vincoli dei data center esistenti:** le aziende spesso scelgono di eseguire la migrazione al cloud perché la capacità, la velocità e la stabilità di un data center esistente non sono più soddisfacenti. Sfortunatamente, questi stessi vincoli implicano complicazioni per il processo di migrazione e richiedono una pianificazione aggiuntiva durante i processi di valutazione e migrazione.
- **Migrazione su larga scala:** è probabile che le migrazioni che superano i 2.000 asset siano soggette a vincoli che richiedono un'ulteriore pianificazione e un approccio disciplinato per l'esecuzione. I processi di valutazione e migrazione vengono adattati per tenere conto della complessità di scala.
- **Più data center:** la migrazione di più data center aggiunge una grande complessità. Durante i processi di valutazione, migrazione, ottimizzazione e gestione vengono discusse ulteriori considerazioni.
- **Gestione delle modifiche e documentazione della soluzione:** i grandi inventari di digital estate, le architetture di soluzioni complesse, i debiti tecnici di lunga data e le interdipendenze possono creare complicazioni che devono essere affrontate durante i processi di valutazione, migrazione e ottimizzazione.
- **Strategia di governance o di conformità:** quando la governance e la conformità sono vitali per il successo di una migrazione, è necessario un ulteriore allineamento tra i team di governance IT e il team di adozione del cloud.

### <a name="workload-specific-scope-changes"></a>Modifiche di ambito specifiche dei carichi di lavoro

- **Progettare i carichi di lavoro per la resilienza:** I principi comuni di progettazione del cloud possono aiutare a preparare i carichi di lavoro cruciali per una migliore resilienza. In questo articolo verrà spiegato l'impatto su un processo di migrazione quando la resilienza è un requisito del carico di lavoro. Vengono anche condivisi alcuni principi comuni da includere nella configurazione generale dell'ambiente per migliorare la resilienza per l'ambiente.
- **Allineare la migrazione ai modelli di applicazione:** il modello di migrazione di un carico di lavoro può influire sul percorso di migrazione scelto. Questo articolo delinea alcune modifiche di ambito che verrebbero integrate nel livello elemento di lavoro di un backlog di migrazione per riflettere i diversi approcci alla migrazione per ogni carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Esplorare il sommario a sinistra per leggere informazioni su esigenze o modifiche di ambito specifiche. In alternativa, la prima estensione dell'ambito nell'elenco [Bilanciamento del portfolio](./balance-the-portfolio.md) è un buon punto di partenza per iniziare a esaminare questi scenari.

> [!div class="nextstepaction"]
> [Bilanciamento del portfolio](./balance-the-portfolio.md)
