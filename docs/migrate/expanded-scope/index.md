---
title: Elenco di controllo per l'ambito esteso della migrazione al cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Elenco di controllo per l'ambito esteso della migrazione al cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ee164f75b4f3748fce027d0c6c98db5200dcdd71
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548508"
---
# <a name="expanded-scope-for-cloud-migration"></a>Ambito esteso per la migrazione al cloud

La [guida alla migrazione ad Azure](../azure-migration-guide/index.md) in Cloud Adoption Framework è il punto di partenza consigliato per i lettori interessati a una migrazione con rehosting ad Azure, nota anche come migrazione "lift and shift". Tale guida presenta una serie di prerequisiti, strumenti e approcci per la migrazione di macchine virtuali al cloud.

Anche se questa guida è un punto di partenza efficace per acquisire familiarità con questo tipo di migrazione, si basa su svariati presupposti. Questi presupposti si basano sulle esigenze di molti utenti di Cloud Adoption Framework, proponendo un approccio semplificato alle migrazioni. In questa sezione di Cloud Adoption Framework vengono presentati alcuni scenari di migrazione con ambito esteso e si tratta di informazioni utili per orientare i progetti a cui non si applicano tali presupposti.

## <a name="cloud-migration-expanded-scope-checklist"></a>Elenco di controllo per l'ambito esteso della migrazione al cloud

L'elenco di controllo seguente presenta alcune aree comuni di complessità che potrebbero richiedere l'estensione dell'ambito della migrazione oltre a quanto previsto dalla [guida alla migrazione ad Azure](../azure-migration-guide/index.md).

### <a name="business-driven-scope-expansion"></a>Espansione dell'ambito in base al business

- **[Bilanciare il portfolio](./balance-the-portfolio.md):** il team di strategia del cloud è interessato a destinare investimenti maggiori alla migrazione (rehosting di carichi di lavoro e applicazioni esistenti con modifiche minime) o all'innovazione (refactoring o ricostruzione di carichi di lavoro e applicazioni con tecnologie cloud moderne). Spesso, la chiave del successo è trovare un equilibrio tra queste due priorità. In questa guida, il bilanciamento del portfolio di adozione del cloud è un argomento comune e viene affrontato per ognuno dei processi di migrazione.
- **[Supporto dei mercati globali](../../decision-guides/regions/index.md):** l'azienda opera in più aree geografiche con requisiti di sovranità dei dati diversi. Per soddisfare tali requisiti, occorre tenere conto di considerazioni aggiuntive nella verifica dei prerequisiti e per la distribuzione degli asset durante la migrazione.

### <a name="technology-driven-scope-expansion"></a>Espansione dell'ambito in base alla tecnologia

- **[Migrazione di VMware](./vmware-host.md):** la migrazione degli host VMware può accelerare il processo complessivo di migrazione. Ogni host VMware trasferito implica lo spostamento di più carichi di lavoro nel cloud con un approccio lift-and-shift. Dopo la migrazione, le VM e i carichi di lavoro possono rimanere in VMware o essere trasferiti in funzionalità cloud moderne.
- **[Migrazione di SQL Server](./sql-migration.md):** la migrazione di istanze di SQL Server può accelerare il processo complessivo di migrazione. Ogni istanza di SQL Server trasferita implica lo spostamento di più database e servizi, accelerando potenzialmente più carichi di lavoro.
- **[Più data center](./multiple-datacenters.md):** la migrazione di più data center aggiunge una notevole complessità. Durante i processi di valutazione, migrazione, ottimizzazione e gestione vengono discusse ulteriori considerazioni per la preparazione di ambienti più complessi.
- **[Requisiti dei dati superiori alla capacità di rete](./network-capacity-exceeded.md):** le aziende spesso scelgono di eseguire la migrazione al cloud perché la capacità, la velocità e la stabilità di un data center esistente non sono più soddisfacenti. Sfortunatamente, questi stessi vincoli implicano complicazioni per il processo di migrazione e richiedono una pianificazione aggiuntiva durante i processi di valutazione e migrazione.
- **[Strategia di governance o di conformità](./governance-or-compliance.md):** quando la governance e la conformità sono vitali per il successo di una migrazione, è necessario un ulteriore allineamento tra i team di governance IT e il team di adozione del cloud.

Se uno qualsiasi di questi aspetti più complessi rispecchia lo scenario di interesse, è probabile che questa sezione di Cloud Adoption Framework possa offrire il tipo di linee guida necessarie per un corretto allineamento dell'ambito nei processi di migrazione.

Ognuno di questi scenari è presentato nei vari articoli in questa sezione di Cloud Adoption Framework.

## <a name="next-steps"></a>Passaggi successivi

Esplorare il sommario a sinistra per leggere informazioni su esigenze o modifiche di ambito specifiche. In alternativa, la prima estensione dell'ambito nell'elenco [Bilanciare il portfolio](./balance-the-portfolio.md) è un buon punto di partenza per iniziare a esaminare questi scenari.

> [!div class="nextstepaction"]
> [Bilanciare il portfolio](./balance-the-portfolio.md)
