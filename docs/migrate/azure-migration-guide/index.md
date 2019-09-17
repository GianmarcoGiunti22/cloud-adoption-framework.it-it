---
title: Introduzione alla guida alla migrazione ad Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come eseguire in modo efficace la migrazione dei servizi dell'organizzazione in Azure con istruzioni dettagliate.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 9b77b8fbbe6479b716d9b9f91d6e0154db8c0db7
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022821"
---
::: zone target="chromeless"

# <a name="before-you-start"></a>Prima di iniziare

::: zone-end

::: zone target="docs"

# <a name="introduction-to-the-azure-migration-guide"></a>Introduzione alla guida alla migrazione ad Azure

::: zone-end

Prima di eseguire la migrazione delle risorse ad Azure, è necessario scegliere il metodo di migrazione e le funzionalità che verranno usate per la governance e la sicurezza dell'ambiente. Questa guida presenta in modo dettagliato questo processo decisionale.

::: zone target="docs"

> [!TIP]
> Per un'esperienza interattiva, visualizzare questa guida nel portale di Azure. Passare al [Centro di avvio rapido di Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) nel portale di Azure e selezionare **Migrate your environment to Azure** (Eseguire la migrazione dell'ambiente in Azure).

::: zone-end

# <a name="overviewtaboverview"></a>[Overview](#tab/Overview)

Questa guida illustra le nozioni di base della migrazione di applicazioni e risorse dall'ambiente locale ad Azure. È progettata per ambiti di migrazione di complessità minima. Per stabilire se questa guida è appropriata per la migrazione, vedere la scheda **Quando usare questa guida**.

Quando si esegue la migrazione ad Azure, è possibile eseguire la migrazione delle applicazioni così come sono con soluzioni con macchine virtuali basate su IaaS (operazione nota come "rehosting" o migrazione "lift and shift") oppure è possibile scegliere di modernizzare le applicazioni sfruttando la flessibilità offerta dall'uso di servizi gestiti e altre funzionalità native del cloud. Vedere la scheda **Opzioni di migrazione** per altre informazioni su queste opzioni. Durante lo sviluppo della strategia di migrazione è opportuno considerare gli aspetti seguenti:

- Le applicazioni incluse nella migrazione funzioneranno nel cloud?
- Qual è la strategia migliore (per quanto riguarda tecnologia, strumenti e migrazioni) per l'applicazione? Per altre informazioni, vedere la [guida alle decisioni relative agli strumenti di migrazione](../../decision-guides/migrate-decision-guide/index.md) di Microsoft Cloud Adoption Framework.
- Come si possono ridurre al minimo i tempi di inattività durante la migrazione?
- Come controllare i costi?
- Come si può tenere traccia dei costi delle risorse e fatturarli in modo accurato?
- Come si può garantire che l'organizzazione rimanga conforme e rispetti le normative?
- Come soddisfare i requisiti legali per la sovranità dei dati in determinati paesi?

Questa guida aiuta a rispondere a queste domande. Sono inclusi suggerimenti per le attività e le funzionalità da prendere in considerazione durante i preparativi per la distribuzione delle risorse in Azure, tra cui:

> [!div class="checklist"]
>
> - **Configurare i prerequisiti.** Pianificare la migrazione e occuparsi dei preparativi.
> - **Valutare l'idoneità tecnica.** Convalidare la conformità e l'idoneità tecniche per la migrazione.
> - **Gestire i costi e la fatturazione.** Esaminare i costi delle risorse.
> - **Eseguire la migrazione dei servizi.** Eseguire la migrazione effettiva.
> - **Organizzare le risorse.** Bloccare le risorse critiche per il sistema e assegnare tag alle risorse per tenerne traccia.
> - **Ottimizzare e trasformare.** Usare l'opportunità di post-migrazione per verificare le risorse.
> - **Proteggere e gestire.** Assicurarsi che l'ambiente sia sicuro e monitorato in modo corretto.
> - **Ottenere assistenza.** Ottenere assistenza e supporto tecnico durante le attività di migrazione o di post-migrazione.

::: zone target="docs"

Per altre informazioni su come organizzare e strutturare le sottoscrizioni, gestire le risorse distribuite e rispettare i requisiti dei criteri aziendali, vedere [Governance in Azure](https://docs.microsoft.com/azure/security/governance-in-azure).

::: zone-end

# <a name="when-to-use-this-guidetabwhentousethisguide"></a>[Quando usare questa guida](#tab/WhenToUseThisGuide)

Anche se gli strumenti presentati in questa guida supportano un'ampia gamma di scenari di migrazione, questa guida è incentrata su progetti di ambito limitato di _complessità minima_. Per determinare se questa guida alla migrazione è adatta a uno specifico progetto, valutare se le condizioni seguenti sono applicabili:

- Si esegue la migrazione di un ambiente omogeneo.
- Solo alcune unità aziendali devono essere allineate per completare la migrazione.
- Non si prevede di automatizzare l'intera migrazione.
- Si esegue la migrazione di un numero ridotto di server.
- Il mapping delle dipendenze dei componenti di cui eseguire la migrazione è semplice da definire.
- Il settore di appartenenza prevede requisiti normativi minimi rilevanti per questo tipo di migrazione.

Se una di queste condizioni _non_ è applicabile alla situazione specifica, è consigliabile valutare invece la [guida per l'ambito esteso](../expanded-scope/index.md). Si consiglia anche di richiedere assistenza a uno dei team o dei partner Microsoft per eseguire migrazioni che richiedono la guida per l'ambito esteso. I clienti che collaborano con Microsoft o partner certificati hanno maggiori probabilità di successo in questi scenari. Altre informazioni su come richiedere assistenza sono disponibili in questa guida.

<!-- markdownlint-enable MD033 -->

::: zone target="docs"

Per altre informazioni, vedere:

- [Guida per l'ambito esteso](../expanded-scope/index.md)

::: zone-end

# <a name="migration-optionstabmigrationoptions"></a>[Opzioni di migrazione](#tab/MigrationOptions)

È possibile eseguire una migrazione al cloud in diversi modi. Alcuni sono più adatti a scenari diversi rispetto ad altri. Mentre si determina come eseguire la migrazione dell'ambiente, considerare le opzioni seguenti per decidere una strategia di migrazione:

- **Rehosting:** nota anche come "lift and shift", un'attività di rehosting consente di spostare lo stato corrente in Azure, con modifiche minime all'architettura complessiva.
- **Refactoring:** le opzioni di piattaforma distribuita come servizio (PaaS) possono ridurre i costi operativi associati a molte applicazioni. Può essere prudente effettuare un leggero refactoring di un'applicazione per adattare un modello PaaS. Questo fa riferimento anche al refactoring del codice nel processo di sviluppo dell'applicazione per consentire a quest'ultima di restare al passo per nuove opportunità commerciali.
- **Riprogettazione:** Alcune applicazioni obsolete non sono compatibili con i provider di servizi cloud a causa delle decisioni di progettazione prese quando sono state compilate. In questi casi, l'applicazione potrebbe dover essere riprogettata come parte della migrazione.
- **Ricostruzione:** in alcuni scenari, le modifiche necessarie per eseguire la migrazione di un'applicazione possono risultare troppo estese per giustificare un'ulteriore investimento e la soluzione deve essere ricostruita.
- **Sostituzione:** Le soluzioni vengono in genere implementate usando la tecnologia e le tecniche migliori disponibili al momento. In alcuni casi, le applicazioni moderne in forma di software come servizio (SaaS) possono offrire tutte le funzionalità fornite dall'applicazione ospitata. In questi scenari, si potrebbe pianificare la sostituzione futura di un carico di lavoro, escludendolo così dalla pianificazione per la migrazione.

::: zone target="chromeless"

Questi metodi non si escludono a vicenda. Ad esempio, anche se la migrazione iniziale potrebbe usare un modello di **rehosting**, è possibile scegliere di implementare il **refactoring** o la **riprogettazione** nell'ambito della fase di ottimizzazione di post-migrazione. Questi scenari sono presentati nella sezione **Ottimizzare e trasformare** di questa guida.

::: zone-end

::: zone target="docs"

Questi metodi non si escludono a vicenda. Ad esempio, anche se la migrazione iniziale potrebbe usare un modello di **rehosting**, è possibile scegliere di implementare il **refactoring** o la **riprogettazione** nell'ambito della fase di ottimizzazione di post-migrazione. Questi scenari sono presentati nella sezione [Ottimizzare e trasformare](./optimize-and-transform.md) di questa guida.

::: zone-end

![Infografica delle opzioni di migrazione](../../_images/migrate/migration-options.png)
