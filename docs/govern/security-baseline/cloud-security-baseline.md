---
title: Informazioni sulla baseline per la sicurezza del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla baseline per la sicurezza del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: dfb7969d19017c003ef961c18e87b8cb110ccd4e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029223"
---
# <a name="understand-the-cloud-security-baseline"></a>Informazioni sulla baseline per la sicurezza del cloud

Questo è un articolo introduttivo sull'argomento generale di una linea di base di sicurezza cloud che si basa sulle [cinque discipline della governance del cloud](../governance-disciplines.md) per definire un Framework di governance. Informazioni più dettagliate sulla sicurezza del cloud sono disponibili nel [cloud attendibile di Azure](https://azure.microsoft.com/overview/trusted-cloud). Gli approcci consigliati per migliorare le condizioni di sicurezza delle organizzazioni sono disponibili nel [catalogo dei servizi di sicurezza del cloud](https://www.microsoft.com/security/information-protection)

> [!NOTE]
> Le informazioni in questo articolo non sono progettate per offrire un contesto sufficiente per consentire al lettore di implementare una strategia di sicurezza, ma sono pensate solo per offrire conoscenze generali.

## <a name="cloud-security"></a>Sicurezza del cloud

La sicurezza del cloud è un'estensione delle procedure di protezione delle informazioni tradizionali. La sicurezza IT tradizionale include criteri e controlli per la governance della sicurezza dei computer e della rete, della protezione dei dati, dell'utilizzo delle informazioni e così via. Gli stessi criteri e controlli sono necessari nel cloud. Durante qualsiasi trasformazione cloud, è fondamentale che i CISO siano coinvolti attivamente e conoscano il panorama Cloud, per garantire che i criteri IT legacy siano mappati ai livelli di controllo appropriati nel cloud.

Come minimo, qualsiasi strategia di sicurezza del cloud deve tenere conto degli aspetti seguenti:

- **Classificare i dati.** classificazione appropriata dei dati per essere a conoscenza delle origini dati che sono private, protette o con riservatezza elevata. Ciò consentirà di gestire i rischi durante la pianificazione.
- **Pianificare uno scenario di cloud ibrido.** Comprendere in che modo le reti locali legacy si connetteranno al cloud aiuteranno i CISO a identificare e correggere i rischi.
- **Pianificare attacchi ed errori.** nei primi mesi di una trasformazione verranno commessi errori durante la fase di apprendimento del team. Iniziare con distribuzioni a basso rischio e con molte restrizioni per imparare in modo sicuro.
- **Priorità della privacy.** per qualsiasi trasformazione, l'intero team deve tenere sempre presente la privacy di clienti e dipendenti. I dati sono sicuri nel cloud, ma il team deve essere consapevole di questo aspetto e prestare estrema attenzione per la gestione dei dati sensibili.

## <a name="protecting-data-and-privacy"></a>Protezione dei dati e privacy

Per le organizzazioni in tutto&mdash;il mondo, i governi, i no profit&mdash;o le aziende cloud computing sono diventati una parte essenziale della strategia it continuativa. I servizi cloud di offrono alle organizzazioni di tutte le dimensioni l'accesso a risorse di archiviazione dei dati virtualmente illimitate, liberandole dalla necessità di acquistare, gestire e aggiornare reti e sistemi di computer locali. Microsoft e altri provider di servizi cloud offrono l'infrastruttura IT, la piattaforma e il software come un servizio (SaaS), consentendo ai clienti di incrementare o ridurre rapidamente le risorse necessarie, pagando solo per la potenza di calcolo e le risorse di archiviazione usate.

Tuttavia, man mano che le organizzazioni continuano a sfruttare i vantaggi dei servizi cloud, come maggiore scelta, agilità e flessibilità affiancate allo stesso tempo dalla possibilità di aumentare l'efficienza e ridurre i costi IT, devono tenere conto degli effetti su privacy, sicurezza e conformità dell'introduzione dei servizi cloud. Microsoft si è impegnata per rendere le proprie offerte cloud non solo scalabili, affidabili e gestibili, ma anche per assicurarsi che i dati dei clienti siano protetti e vengano usati in modo trasparente.

La sicurezza è un componente essenziale delle misure di protezione dei dati avanzate in tutti gli ambienti di elaborazione online. Ma la sicurezza da sola non è sufficiente. La scelta di un particolare prodotto di cloud computing da parte di utenti e aziende dipende anche dalla possibilità di considerare attendibile la protezione della privacy delle informazioni personali e l'uso dei dati esclusivamente in modo coerente con le aspettative dei clienti. Scoprire di più sull'approccio di Microsoft alla [protezione dei dati e della privacy nel cloud](https://go.microsoft.com/fwlink/?LinkId=808242&clcid=0x409).

## <a name="risk-mitigation"></a>Mitigazione dei rischi

I due i maggiori rischi per qualsiasi data center possono essere ricondotti a due origini: Sistemi obsoleti ed errore umano. La protezione da questi due rischi è il minimo quando si definisce una strategia di protezione IT. Lo stesso vale nel cloud. Di seguito sono riportati alcuni esempi di controlli che possono essere messi a punto per correggere i rischi e rafforzare la strategia di sicurezza del cloud.

- **Sistemi legacy:** molti componenti nelle soluzioni di data center locali sono costituiti da software, hardware e processi antecedenti ai rischi di sicurezza attuali. Quando possibile, correggere, sostituire o ritirare questi sistemi durante una trasformazione cloud. Naturalmente, ciò non sempre è fattibile. Se i sistemi legacy rimarranno in produzione in una soluzione ibrida, è importante che tali sistemi siano stati inventariati e compresi durante la progettazione del data center virtuale. In questo modo, il team di progettazione ha la possibilità di eliminare o controllare l'accesso a questi sistemi dal cloud.
- **Processi e controlli di sicurezza IT:** Come minimo, i team di progettazione del cloud devono essere aggiornati sui processi e sui controlli di sicurezza IT esistenti per poterli trasferire nel cloud. In uno scenario ideale, un membro del team di sicurezza IT dovrebbe ricevere un'adeguata formazione sulla sicurezza informatica e diventare un membro dedicato dei team di progettazione e implementazione.
- **Monitoraggio e controllo:** per la progettazione dei processi e degli strumenti di governance, assicurarsi che le soluzioni di monitoraggio e controllo includano i rischi o le violazioni della sicurezza.

> [!NOTE]
> **Divulgazione del debito tecnico:** Per questo argomento non sono disponibili azioni implementabili. Nel corso del tempo verranno pubblicati articoli aggiuntivi in merito. Informazioni più dettagliate sulla sicurezza del cloud sono disponibili nel sito dedicato al [cloud attendibile di Azure](https://azure.microsoft.com/overview/trusted-cloud). Gli approcci consigliati per migliorare le condizioni di sicurezza delle organizzazioni sono disponibili nel [catalogo dei servizi di sicurezza del cloud](https://www.microsoft.com/security/information-protection)
