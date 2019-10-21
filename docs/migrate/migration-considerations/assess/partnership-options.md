---
title: Informazioni sulle opzioni di collaborazione e supporto
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descrive le opzioni e gli approcci per supportare le attività di migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5eabc654c174ac3eff895e6b2ff94700789f5de5
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549168"
---
# <a name="understand-partnership-options"></a>Informazioni sulle opzioni di partnership

Durante la migrazione, il team di adozione del cloud esegue la migrazione effettiva dei carichi di lavoro al cloud. Diversamente dalle attività collaborative e di risoluzione dei problemi quando si definisce il [digital estate](../../../digital-estate/index.md) o si crea l'infrastruttura cloud di base, la migrazione tende a essere una serie di attività di esecuzione ripetitiva. Oltre agli aspetti ripetitivi, è probabile che si verifichino sforzi di test e ottimizzazione che richiedono una conoscenza approfondita del provider di servizi cloud scelto. La natura ripetitiva di questo processo può essere a volte risolta in modo ottimale da un partner, riducendo il carico del personale a tempo pieno. Inoltre, i partner potrebbero essere in grado di allineare meglio le competenze tecniche approfondite quando i processi ripetitivi riscontrano anomalie di esecuzione.

I partner tendono a essere strettamente allineati a un singolo fornitore di cloud o a un numero ridotto di fornitori di cloud. Per illustrare meglio le opzioni di collaborazione, nella parte restante di questo articolo si presuppone che Microsoft Azure sia il provider di servizi cloud scelto.

Durante la fase di pianificazione, creazione o migrazione, una società dispone in genere di quattro opzioni di collaborazione di esecuzione:

- **Self-service guidato.** Il team tecnico esistente esegue la migrazione, con l'aiuto di Microsoft.
- **FastTrack for Azure.** Usare il programma Microsoft FastTrack for Azure per accelerare la migrazione.
- **Partner di soluzioni.** È possibile connettersi ai partner di soluzioni di Azure o ai partner Cloud Solutions (CSP) per accelerare la migrazione.
- **Self-service supportato.** L'esecuzione viene completata dal personale tecnico esistente con il supporto di Microsoft.

## <a name="guided-self-service"></a>Self-service guidato

Se un'organizzazione sta pianificando una migrazione di Azure in modo autonomo, Microsoft è sempre disponibile a supportarla durante tutto il suo percorso. Per semplificare la migrazione ad Azure, Microsoft e i suoi partner hanno sviluppato un ampio set di architetture, guide, strumenti e servizi per ridurre i rischi e velocizzare la migrazione di macchine virtuali, applicazioni e database. Questi strumenti e servizi supportano un'ampia gamma di sistemi operativi, linguaggi di programmazione, framework e database.

- **Strumenti di valutazione e migrazione.** Azure offre un'ampia gamma di strumenti da usare in fasi diverse per la trasformazione cloud, inclusa la valutazione dell'infrastruttura esistente. Per altre informazioni, vedere la sezione "Valutazione" del capitolo "Migrazione" riportata di seguito.
- **[Framework di adozione del cloud di Microsoft](../../index.md).** Questo framework presenta un approccio strutturato all'adozione e alla migrazione del cloud. Si basa sulle procedure consigliate per molti impegni dei clienti supportati da Microsoft ed è organizzato come una serie di passaggi, dall'architettura e dalla progettazione all'implementazione. Per ogni passaggio è disponibile materiale sussidiario utile per la progettazione dell'architettura dell'applicazione.
- **[Modelli di progettazione cloud](https://docs.microsoft.com/azure/architecture/patterns).** Azure fornisce alcuni schemi progettuali cloud utili per la creazione di carichi di lavoro affidabili, scalabili e sicuri nel cloud. Ogni schema descrive il problema che risolve, le considerazioni per l'applicazione dello schema e un esempio basato su Azure. La maggior parte degli schemi include esempi o frammenti di codice che illustrano come implementare lo schema in Azure. Tuttavia, questi sono pertinenti a qualsiasi sistema distribuito, sia in hosting su Azure sia su altre piattaforme cloud.
- **[Concetti fondamentali sul cloud](https://docs.microsoft.com/azure/architecture/guide).** I concetti fondamentali consentono di insegnare gli approcci di base per l'implementazione di concetti di base. Questa guida consente ai tecnici di considerare le soluzioni che vanno oltre un singolo servizio di Azure.
- **[Scenari di esempio](https://docs.microsoft.com/azure/architecture/example-scenario).** La guida fornisce riferimenti derivati da implementazioni reali dei clienti, che descrivono gli strumenti, gli approcci e i processi che i clienti precedenti hanno seguito per raggiungere obiettivi aziendali specifici.
- **[Architetture di riferimento](https://docs.microsoft.com/azure/architecture/reference-architectures).** Le architetture di riferimento sono disposte per scenario, con le architetture correlate raggruppate insieme. Ogni architettura include procedure consigliate, oltre a considerazioni per la scalabilità, la disponibilità, la gestibilità e la sicurezza. Molte includono anche una soluzione distribuibile.

## <a name="fasttrack-for-azure"></a>FastTrack for Azure

[FastTrack for Azure](https://azure.microsoft.com/roadmap/fasttrack-for-azure) offre assistenza diretta da parte dei tecnici di Azure che collaborano con i partner per aiutare i clienti a creare soluzioni di Azure in modo rapido e sicuro. FastTrack fornisce le procedure consigliate e gli strumenti che provengono da esperienze dei clienti reali per guidare i clienti dalla fase di installazione, configurazione e sviluppo alla produzione di soluzioni di Azure, tra cui:

- Migrazione dei data center
- Windows Server in Azure
- Linux su Azure
- SAP in Azure
- Continuità aziendale e ripristino di emergenza (BCDR)
- HPC (High-Performance Computing)*
- App native del cloud
- DevOps
- Modernizzazione di app
- Analisi cloud**
- App intelligenti
- Agenti intelligenti**
- Modernizzazione dei dati in Azure
- Sicurezza e gestione
- Dati distribuiti a livello globale
- IoT***

*Anteprima limitata in Stati Uniti, Canada, Regno Unito ed Europa occidentale

**Anteprima limitata nel Regno Unito e in Europa occidentale

***Disponibile nella seconda metà del 2019

Durante un tipico caso di assistenza di FastTrack for Azure, Microsoft consente di definire la visione aziendale per pianificare e sviluppare soluzioni di Azure con successo. Il team valuta le esigenze dell'architettura e fornisce indicazioni, principi di progettazione, strumenti e risorse per facilitare la creazione, la distribuzione e la gestione di soluzioni di Azure. Il team associa i partner qualificati per i servizi di distribuzione su richiesta e periodicamente esegue controlli per assicurarsi che la distribuzione avanzi secondo quanto pianificato e per aiutare nella rimozione di blocchi.

Ecco le fasi principali di un impegno tipico di FastTrack for Azure:

- **Individuazione.** Identificare gli stakeholder principali, comprendere l'obiettivo o la visione per i problemi da risolvere e valutare le esigenze a livello di architettura.
- **Abilitazione della soluzione.** Apprendere i principi di progettazione per la creazione di applicazioni, verificare l'architettura delle applicazioni e delle soluzioni e indicazioni e strumenti utili per la distribuzione dai modelli di verifica alla produzione.
- **Collaborazione continua.** I tecnici di Azure e i responsabili del programma eseguono controlli a intervalli regolari per garantire che la distribuzione avanzi secondo quanto pianificato e per aiutare nella rimozione di blocchi.

## <a name="microsoft-services-offerings-aligned-to-cloud-adoption-framework-approaches"></a>Offerte di servizi Microsoft allineate agli approcci del framework di adozione del cloud

![Approccio al framework di adozione del cloud dei servizi Microsoft](../../../_images/migrate/mcs-program-approach.jpg)

**Valuta:** I servizi Microsoft usano un [approccio unificato basato su dati e strumenti](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) costituito da workshop di architettura, informazioni in tempo reale di Azure, modelli di minacce per sicurezza e identità e vari strumenti per fornire informazioni approfondite su problemi, rischi, consigli e i problemi relativi a un ambiente Azure esistente con un risultato chiave, ad esempio la roadmap per la [modernizzazione di alto livello](https://download.microsoft.com/download/F/7/2/F72FAD7E-8BBD-4E04-8C7B-9AC4FE04A150/Cloud_Adoption_Discovery_and_Roadmap_Datasheet.pdf).

**Adottare:** Grazie ad [Azure cloud Foundation](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf), i servizi Microsoft definiscono le progettazioni, i modelli e l'architettura di governance di base di Azure, eseguendo il mapping dei requisiti all'architettura di riferimento più appropriata e pianificando, progettando e distribuendo l'infrastruttura. gestione, sicurezza e identità necessari per i carichi di lavoro.

**Esegui migrazione/ottimizzazione:** La soluzione di [modernizzazione cloud](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) dei servizi Microsoft offre un approccio completo per spostare le applicazioni e l'infrastruttura in Azure, nonché per ottimizzare e modernizzare una volta nel cloud grazie alla migrazione semplificata.

**Innovazione:** La [soluzione CCoE (cloud Center of Excellence)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) dei servizi Microsoft offre un impegno di coaching DevOps e usa i principi DevOps combinati con controlli di sicurezza e gestione dei servizi nativi del cloud prescrittivi per favorire l'innovazione aziendale, aumenta l'agilità e Riduci il tempo per il valore entro una funzionalità sicura, prevedibile e flessibile per la gestione delle operazioni e della distribuzione dei servizi.

## <a name="azure-support"></a>Supporto tecnico di Azure

In caso di domande o per assistenza, [creare una richiesta di supporto](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest). Se per la richiesta di supporto sono necessarie informazioni tecniche dettagliate, visitare la pagina dei [piani di supporto di Azure](https://azure.microsoft.com/support/plans) per allinearsi al piano più adatto alle proprie esigenze.

## <a name="azure-solutions-partner"></a>Partner per le soluzioni di Azure

I provider di soluzioni certificate Microsoft sono specializzati nella fornitura di soluzioni aggiornate per i clienti basate su tecnologia Microsoft in tutto il mondo. È così possibile ottimizzare la propria attività commerciale nel cloud con l'aiuto di un partner esperto.

Ricevere aiuto dai partner che hanno realizzato soluzioni di Azure pronte all'uso o personalizzate e da coloro che possono contribuire alla distribuzione e alla gestione di tali soluzioni per l'azienda:

- **[Trovare un partner di soluzioni cloud](https://www.microsoft.com/solution-providers/home).** Un CSP certificato può aiutare a sfruttare al meglio il cloud valutando gli obiettivi aziendali per l'adozione del cloud, identificando la soluzione cloud ottimale che soddisfa le esigenze aziendali e consentendo all'azienda di diventare più agile ed efficiente.
- **[Trovare un partner del servizio gestito](https://www.microsoft.com/solution-providers/search?cacheId=16a3b49b-fef2-449d-bdf0-628008114cca).** Un partner del servizio gestito di Azure (MSP) consente una transizione aziendale ad Azure, fornendo assistenza in tutti gli aspetti del percorso cloud. Dalla consulenza alle migrazioni e alla gestione delle operazioni, i partner del servizio gestito cloud mostrano ai clienti tutti i vantaggi offerti dall'adozione del cloud. Fungono anche da punto di accesso al normale servizio di assistenza, al provisioning e all'esperienza di fatturazione, il tutto con un modello di business con pagamento in base al consumo (PAYG) flessibile.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver selezionato un partner e una strategia di supporto, è possibile aggiornare i [backlog di rilascio e iterazione](./release-iteration-backlog.md) per riflettere le attività e le assegnazioni pianificate.

> [!div class="nextstepaction"]
> [Gestire le modifiche usando i backlog di rilascio e iterazione](./release-iteration-backlog.md)
