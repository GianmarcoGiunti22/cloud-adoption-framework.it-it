---
title: Guida decisionale di imposizione dei criteri
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle sottoscrizioni di imposizione dei criteri come priorità di progettazione principale nelle migrazioni di Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 7e3df166c41658b248bc7fb61067b27362a8070c
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753147"
---
# <a name="policy-enforcement-decision-guide"></a>Guida decisionale di imposizione dei criteri

La definizione di criteri dell'organizzazione non è efficace a meno che possa essere applicata all'interno dell'organizzazione. Un aspetto fondamentale della pianificazione di qualsiasi migrazione cloud consiste nel determinare il modo migliore di combinare gli strumenti implementati dalla piattaforma cloud con i processi IT esistenti, per ottimizzare la conformità ai criteri dell'intero gruppo di cloud.

![Grafico delle opzioni di imposizione dei criteri dalla meno alla più complessa, allineato con i collegamenti sotto](../../_images/decision-guides/decision-guide-policy-enforcement.png)

Passare a: [Procedure consigliate di base](#baseline-best-practices) | [Monitoraggio della conformità ai criteri](#policy-compliance-monitoring) | [Applicazione dei criteri](#policy-enforcement) | [Criteri tra organizzazioni](#cross-organization-policy) | [Applicazione automatizzata](#automated-enforcement)

Con l'espansione del cloud risulterà necessario mantenere e applicare criteri per una più ampia gamma di risorse e sottoscrizioni. L'espansione dell'ambiente e l'aumento dei requisiti dei criteri dell'organizzazione renderanno necessario estendere l'ambito dei processi di applicazione dei criteri per garantire che vengano rispettati con coerenza e il rilevamento veloce di eventuali violazioni.

I meccanismi di applicazione dei criteri forniti dalla piattaforma a livello di risorse o di sottoscrizione sono in genere sufficienti per gli ambienti cloud più piccoli. Per le distribuzioni più grandi è giustificato un ambito di applicazione più esteso e potrebbe essere necessario sfruttare i vantaggi di meccanismi di applicazione più sofisticati che coinvolgono gli standard di distribuzione, il raggruppamento e l'organizzazione delle risorse, nonché l'integrazione dell'applicazione dei criteri con i sistemi esistenti di registrazione e creazione di report.

I fattori principali per determinare l'ambito dei processi di applicazione dei criteri sono i [requisiti di governance del cloud](../../govern/index.md) dell'organizzazione, le dimensioni e la natura dell'ambiente cloud e il modo in cui l'organizzazione è rispecchiata nella [progettazione delle sottoscrizioni](../subscriptions/index.md). Un aumento delle dimensioni dell'ambiente o la maggiore esigenza di gestire centralmente l'applicazione dei criteri possono entrambi giustificare l'estensione dell'ambito di applicazione.

## <a name="baseline-best-practices"></a>Procedure consigliate di base

Per le distribuzioni cloud semplici e le sottoscrizioni singole, è possibile applicare molti criteri aziendali usando funzionalità native per le risorse e le sottoscrizioni in Azure. L'uso coerente dei modelli illustrati in tutte le [guide alle decisioni](../index.md) di Cloud Adoption Framework contribuisce a stabilire un livello di conformità ai criteri di base senza investimenti specifici per l'applicazione dei criteri. Queste funzionalità includono:

- [I modelli di distribuzione](../resource-consistency/index.md) possono effettuare il provisioning delle risorse con struttura e configurazione standardizzate.
- [L'assegnazione di tag e standard di denominazione](../resource-tagging/index.md) consente di organizzare le operazioni e supportare i requisiti di business e dell'account.
- Le restrizioni di rete e la gestione del traffico possono essere implementate tramite [reti definite dal software](../software-defined-network/index.md).
- Il [controllo degli accessi in base al ruolo](../identity/index.md) consente di proteggere e isolare le risorse cloud.

La pianificazione dell'imposizione dei criteri del cloud si avvia esaminando come l'applicazione dei modelli standard descritti nel corso di queste guide consenta di soddisfare i requisiti dell'organizzazione.

## <a name="policy-compliance-monitoring"></a>Monitoraggio della conformità ai criteri

Un primo passaggio, oltre al semplice basarsi sui meccanismi di applicazione dei criteri forniti dalla piattaforma Azure, consiste nel garantire la possibilità di verificare che le applicazioni e i servizi basati sul cloud siano conformi ai criteri dell'organizzazione. Ciò include l'implementazione di funzionalità di notifica per avvisare i responsabili se una risorsa diventa non conforme. La [creazione di log e report](../logging-and-reporting/index.md) efficaci sullo stato di conformità dei carichi di lavoro nel cloud è una parte essenziale della strategia di imposizione dei criteri aziendali.

Se un gruppo di cloud aumenta, strumenti aggiuntivi, ad esempio il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center), garantiscono la sicurezza integrata e il rilevamento delle minacce e consentono di applicare la gestione centralizzata dei criteri e degli avvisi per entrambe le risorse locali e cloud.

## <a name="policy-enforcement"></a>Imposizione dei criteri

In Azure è possibile applicare le impostazioni di configurazione e le regole per la creazione di risorse a livello di gruppo di gestione, sottoscrizione o gruppo di risorse per assicurare l'allineamento dei criteri.

[Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) è un servizio di Azure per la creazione, l'assegnazione e la gestione dei criteri. Questi criteri applicano regole ed effetti diversi alle risorse, in modo che le risorse rimangano conformi ai contratti di servizio e agli standard dell'azienda. Criteri di Azure valuta le risorse per la mancata conformità con i criteri assegnati. Ad esempio, è possibile limitare le dimensioni SKU di macchine virtuali nell'ambiente in uso. Dopo aver implementato i criteri corrispondenti, le risorse nuove ed esistenti vengono valutate per la conformità. Con i criteri corretti, le risorse esistenti possono essere rese conformi.

## <a name="cross-organization-policy"></a>Criteri tra organizzazioni

Se l'ambiente cloud aumenta estendendosi a più sottoscrizioni che richiedono l'applicazione dei criteri, sarà necessario concentrarsi su una strategia per l'applicazione estesa all'intero ambiente cloud per garantire coerenza.

Per la [progettazione di una sottoscrizione](../subscriptions/index.md) è necessario tenere conto dei criteri in relazione alla struttura organizzativa. Oltre ad aiutare a supportare un'organizzazione complessa all'interno della progettazione di una sottoscrizione, i [gruppi di gestione di Azure](../../ready/azure-best-practices/scaling-subscriptions.md#manage-multiple-subscriptions) possono essere usati per assegnare le regole dei criteri di Azure tra più sottoscrizioni.

## <a name="automated-enforcement"></a>Imposizione automatizzata

Anche se i modelli di distribuzione sono validi in scala ridotta, [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) consente di effettuare il provisioning e l'orchestrazione della distribuzione su larga scala e in maniera standard delle soluzioni di Azure. I carichi di lavoro tra più sottoscrizioni possono essere distribuiti con impostazioni dei criteri coerenti per tutte le risorse create.

Per gli ambienti IT che integrano risorse cloud e locali, potrebbe essere necessario usare sistemi di log e di report per offrire funzionalità di monitoraggio ibrido. I sistemi di monitoraggio operativi di terze parti o personalizzati possono offrire funzionalità aggiuntive di imposizione dei criteri. Per gli ambienti cloud più estesi e maturi, prendere in considerazione il modo migliore per integrare questi sistemi con gli asset cloud.

## <a name="next-steps"></a>Passaggi successivi

L'applicazione dei criteri è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
