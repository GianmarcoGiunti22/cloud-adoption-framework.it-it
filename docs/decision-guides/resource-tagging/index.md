---
title: Guida alle decisioni per la denominazione delle risorse e l'assegnazione di tag
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sull'organizzazione e sui tag delle risorse come servizio di base nelle migrazioni di Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: ef226d55d6b16c69b35c57734de25efec6abaa00
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378022"
---
# <a name="resource-naming-and-tagging-decision-guide"></a>Guida alle decisioni per la denominazione delle risorse e l'assegnazione di tag

L'organizzazione delle risorse basate sul cloud è una delle attività più importanti per l'IT, a meno che non siano disponibili solo distribuzioni semplici. L'organizzazione delle risorse ha tre scopi principali:

- **Gestione delle risorse:** I team IT dovranno trovare rapidamente le risorse associate a specifici carichi di lavoro, ambienti, gruppi di proprietà o altre importanti informazioni. L'organizzazione delle risorse è critica per l'assegnazione di ruoli aziendali e di autorizzazioni di accesso per la gestione delle risorse.
- **Automazione:** Oltre a rendere più semplice per l'IT la gestione delle risorse, uno schema organizzativo appropriato consente di sfruttare i vantaggi dell'automazione come parte della creazione di risorse, del monitoraggio operativo e della creazione di processi DevOps.
- **Accounting:** Per fare in modo che i gruppi aziendali siano a conoscenza dell'utilizzo delle risorse cloud, è necessario che l'IT sappia quali sono le risorse usate dai carichi di lavoro e dai team. Per supportare approcci come l'accounting chargeback e showback, è necessario organizzare le risorse cloud in modo che rispecchino la proprietà e l'utilizzo.

## <a name="tagging-decision-guide"></a>Guida relativa alle decisioni sui tag

![Grafico delle opzioni relative ai tag, dalla meno complessa alla più complessa, allineato con i collegamenti sotto](../../_images/decision-guides/decision-guide-resource-tagging.png)

Passare a: [Convenzioni di denominazione di base](#baseline-naming-conventions) | [Modelli di assegnazione di tag alle risorse](#resource-tagging-patterns) | [Altre informazioni](#learn-more)

L'approccio ai tag può essere semplice o complesso, con particolare attenzione ad attività che vanno dal supporto dei team IT che gestiscono i carichi di lavoro cloud all'integrazione delle informazioni relative a tutti gli aspetti dell'azienda.

L'assegnazione di tag allineata alle funzioni IT, ad esempio in base a carico di lavoro, funzione o ambiente, consentirà di ridurre la complessità di monitoraggio degli asset e faciliterà notevolmente il processo decisionale di gestione in base ai requisiti operativi.

Gli schemi di assegnazione di tag con focus sugli aspetti aziendali, come accounting, dirigenza o criticità aziendali potrebbero richiedere molto più tempo per creare standard di assegnazione di tag che rispecchino gli interessi aziendali e per mantenere tali standard nel corso del tempo. Tuttavia, il risultato di questo processo è un sistema di assegnazione di tag che offre maggiori possibilità di tenere conto dei costi e del valore degli asset IT per l'intera azienda. Questa associazione tra il valore aziendale di un asset e il costo operativo è uno dei primi passi da fare per modificare la percezione dell'IT come centro di costo all'interno dell'intera organizzazione.

## <a name="baseline-naming-conventions"></a>Convenzioni di denominazione di base

Una convenzione di denominazione standard è il punto di partenza per organizzare le risorse ospitate nel cloud. Un sistema di denominazione strutturato correttamente consente di identificare rapidamente le risorse a fini di gestione e di accounting. Se in altre parti dell'organizzazione esistono convenzioni di denominazione IT, valutare se le convenzioni di denominazione per il cloud devono essere allineate con queste convenzioni o se è meglio stabilire standard separati basati sul cloud.

Tenere anche presente che i [requisiti di denominazione](../../ready/considerations/naming-and-tagging.md) sono diversi a seconda dei tipi di risorsa di Azure. Le convenzioni di denominazione devono essere compatibili con questi requisiti di denominazione.

## <a name="resource-tagging-patterns"></a>Modelli di tag delle risorse

Per un'organizzazione più sofisticata di quella che può garantire una convenzione di denominazione coerente, le piattaforme cloud consentono di applicare tag alle risorse.

I *tag* sono elementi dei metadati collegati alle risorse. I tag sono costituiti da coppie di stringhe chiave/valore. I valori inclusi in queste coppie vengono decisi dall'utente, ma l'applicazione di un set coerente di tag globali, nell'ambito dei criteri di denominazione e applicazione di tag completi, è una parte essenziale dei criteri di governance generali.

Come parte del processo di pianificazione, usare le domande seguenti per determinare il tipo di informazioni che devono supportare i tag delle risorse:

- Qual è il modo migliore per integrare i criteri di denominazione e assegnazione di tag con i criteri di denominazione e aziendali esistenti nell'organizzazione?
- Si implementerà un sistema di accounting chargeback o showback? Sarà necessario associare le risorse alle informazioni di accounting per reparti, gruppi aziendali e team in modo più dettagliato rispetto a una semplice suddivisione a livello di sottoscrizione?
- I tag devono rappresentare i dettagli come i requisiti di conformità alle normative per una risorsa? Quali sono i dettagli operativi, ad esempio i requisiti in termini di tempo di attività, le pianificazioni per l'applicazione di patch o i requisiti di sicurezza?
- Quali tag saranno obbligatori per tutte le risorse in base ai criteri IT centrali? Quali tag saranno facoltativi? I singoli team possono implementare schemi di tag personalizzati?

I modelli di assegnazione di tag comuni elencati di seguito offrono alcuni esempi di come si possono usare i tag per organizzare gli asset cloud. Questi modelli non sono concepiti per essere esclusivi e possono essere usati in parallelo, rendendo disponibili più modalità di organizzazione degli asset in base alle esigenze dell'azienda.

<!-- markdownlint-disable MD033 -->

| Tipo di tag | Esempi | DESCRIZIONE |
|-----|-----|-----|
| Funzionale            | app = catalogsearch1 <br/>tier = web <br/>webserver = apache<br/>env = prod <br/>env = staging <br/>env = dev                 | Classifica le risorse in relazione al loro scopo in un carico di lavoro, all'ambiente in cui sono state distribuite o ad altre funzionalità e dettagli operativi.                                 |
| classificazione        | confidentiality=private<br/>sla = 24hours                                 | Classifica una risorsa in base a come viene usata e ai criteri applicati                               |
| Contabilità            | department = finance <br/>project = catalogsearch <br/>region = northamerica | Consente di associare le risorse a determinati gruppi di un'organizzazione per la fatturazione |
| Collaborazione           | owner = jsmith <br/>contactalias = catsearchowners<br/>stakeholders = user1;user2;user3<br/>                       | Fornisce informazioni sulle persone (al di fuori di IT) correlate o altrimenti interessate dalla risorsa                      |
| Scopo               | businessprocess=support<br/>businessimpact=moderate<br/>revenueimpact=high   | Allinea le risorse alle funzioni aziendali per supportare meglio le decisioni relative agli investimenti  |

<!-- markdownlint-enable MD033 -->

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni sulla denominazione e l'applicazione di tag in Azure, vedere:

- [Convenzioni di denominazione per le risorse di Azure](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions). Fare riferimento a queste linee guida per le convenzioni di denominazione consigliate per le risorse di Azure.
- [Usare tag per organizzare le risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags?toc=/azure/billing/TOC.json). È possibile applicare i tag in Azure sia a livello di singole risorse che di gruppo di risorse, ottenendo la flessibilità necessaria in termini di granularità per qualsiasi report di accounting in base ai tag applicati.

## <a name="next-steps"></a>Passaggi successivi

L'assegnazione di tag alle risorse è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
