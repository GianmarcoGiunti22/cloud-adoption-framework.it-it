---
title: 'Accelerazione della distribuzione: metriche, indicatori e tolleranza ai rischi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Accelerazione della distribuzione: metriche, indicatori e tolleranza ai rischi'
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5049b41abc03c5f59d0d750373b48a39b0638084
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029616"
---
# <a name="deployment-acceleration-metrics-indicators-and-risk-tolerance"></a>Accelerazione della distribuzione: metriche, indicatori e tolleranza ai rischi

Questo articolo è stato progettato per aiutare a quantificare la tolleranza ai rischi aziendali in relazione all'accelerazione della distribuzione. La definizione di metriche e indicatori consente di creare un business case per effettuare un investimento riguardo alla disciplina Accelerazione della distribuzione.

## <a name="metrics"></a>metrics

La disciplina di accelerazione della distribuzione è incentrata sui rischi correlati alla configurazione, distribuzione, aggiornamento e manutenzione delle risorse cloud. Quando si adotta questa disciplina di governance del cloud sono utili le informazioni seguenti:

- **Errori di distribuzione:** Percentuale di distribuzioni che hanno esito negativo o che comportano la configurazione di risorse.
- **Tempo per la distribuzione:** La quantità di tempo necessaria per distribuire gli aggiornamenti in un sistema esistente.
- **Asset non conformi:** Il numero o la percentuale delle risorse che non sono conformi ai criteri definiti.

## <a name="risk-tolerance-indicators"></a>Indicatori sulla tolleranza ai rischi

I rischi dell'accelerazione della distribuzione sono in gran parte correlati al numero e alla complessità dei sistemi basati sul cloud distribuiti per l'azienda. Di pari passo con la crescita dell'ambiente cloud, si assiste a un aumento del numero di sistemi distribuiti e della frequenza di aggiornamento delle risorse cloud. Le dipendenze tra le risorse rendono ancora più importante la corretta configurazione delle risorse e della progettazione dei sistemi per la resilienza, in caso di tempi di inattività imprevisti di una o più risorse.

<!-- "en-us" location is required for the URL below. -->

Valutare l'opportunità di adottare una cultura organizzativa basata su DevOps o [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) sin dalle prime fasi del percorso di adozione del cloud. Le organizzazioni IT aziendali tradizionali hanno spesso operazioni silo, sicurezza e team di sviluppo che spesso non collaborano bene o sono addirittura conflittuali o ostili. Se si identificano questi problemi in anticipo e si favorisce l'integrazione degli stakeholder principali di ogni team, sarà più facile assicurare un'adozione del cloud più agile mantenendo al tempo stesso un ambiente sicuro e gestito in modo efficiente.

Collaborare con il team di DevSecOps e con gli stakeholder aziendali per identificare i [rischi aziendali](./business-risks.md) correlati alla configurazione e definire quindi una baseline accettabile per la tolleranza ai rischi di configurazione. Questa sezione delle linee guida per l'adozione del cloud fornisce esempi, ma i rischi e le basi di riferimento dettagliati per la società o le distribuzioni saranno probabilmente diversi.

Dopo aver creato una baseline, è necessario stabilire i benchmark minimi che rappresentano un aumento inaccettabile dei rischi identificati. Questi benchmark fungono da trigger per quando è necessario intervenire per correggere questi rischi. Di seguito sono riportati alcuni esempi del modo in cui le metriche correlate alla configurazione, come quelle descritte in precedenza, possono giustificare un maggiore investimento nella disciplina Accelerazione della distribuzione.

- **Trigger della deviazione della configurazione:** Se un'azienda riscontra cambiamenti imprevisti nella configurazione dei componenti di sistema principali, oppure errori nella distribuzione o negli aggiornamenti dei sistemi, dovrebbe investire nella disciplina Accelerazione della distribuzione per identificare le cause principali e le operazioni correttive da intraprendere.
- **Trigger non conformi:** Se il numero di risorse non conformi supera una soglia definita (come numero totale di risorse o come percentuale del totale), un'azienda dovrebbe investire per migliorare la disciplina Accelerazione della distribuzione in modo da assicurare che la configurazione di ogni risorsa rimanga conforme per tutto il suo ciclo di vita.
- **Trigger pianificazione progetto:** Se il tempo necessario per distribuire le risorse e le applicazioni dell'azienda supera spesso una soglia definita, un'azienda dovrebbe investire nei processi di distribuzione dell'accelerazione per introdurre o migliorare distribuzioni automatizzate in modo da garantire coerenza e prevedibilità. I tempi di distribuzione espressi in giorni o addirittura settimane indicano in genere una strategia di distribuzione dell'accelerazione non ottimale.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare le metriche e gli indicatori di tolleranza in linea con il piano di adozione del cloud attuale.

Esaminare i criteri di accelerazione della distribuzione di esempio come punto di partenza per sviluppare criteri che risolvono i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

> [!div class="nextstepaction"]
> [Esaminare i criteri di esempio](./policy-statements.md)
