---
title: Introduzione alla conformità alle normative
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione alla conformità alle normative
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a3cd1f6e817c47360b3146c962a02088aea6a692
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70826927"
---
# <a name="introduction-to-regulatory-compliance"></a>Introduzione alla conformità alle normative

Si tratta di un articolo introduttivo sulla conformità alle normative, di conseguenza non è destinato all'implementazione di una strategia di conformità. Lo scopo è quello di offrire una consapevolezza generale. Informazioni più dettagliate sulle [offerte di conformità di Azure](https://aka.ms/allcompliance) sono disponibili nel [Centro protezione Microsoft](https://www.microsoft.com/trustcenter/default.aspx). Inoltre, tutte le documentazioni scaricabili sono disponibili per determinati clienti di Azure dal [portale di attendibilità dei servizi Microsoft](https://servicetrust.microsoft.com).

La conformità alle normative si riferisce alla disciplina e al processo di garantire che un'azienda segua le leggi applicate da enti che disciplinano la loro geografia o le regole richieste dagli standard di settore adottati volontariamente. Per quanto riguarda la conformità alle normative IT, le persone e i processi monitorano i sistemi aziendali nel tentativo di rilevare e prevenire le violazioni di criteri e procedure stabilite da tali leggi, normative e standard. Si applica a sua volta a un'ampia gamma di processi di monitoraggio e applicazione. A seconda del settore e della geografia, questi processi possono diventare lunghi e complessi.

La conformità è impegnativa per le organizzazioni multinazionali, soprattutto in settori altamente regolamentati, come servizi finanziari e sanitari. Gli standard e le normative si abbondano e, in alcuni casi, possono cambiare di frequente, rendendo difficile per le aziende rimanere al passo con la modifica delle leggi internazionali sulla gestione dei dati.

Come con i controlli di sicurezza, le organizzazioni devono comprendere la separazione delle responsabilità relative alla conformità alle normative nel cloud. I provider di servizi cloud si impegnano a garantire la conformità di servizi e piattaforme. Tuttavia, le organizzazioni devono anche confermare che le applicazioni, l'infrastruttura da cui dipendono le applicazioni e i servizi forniti da terze parti siano certificati come conformi.

Nelle descrizioni seguenti si riporta la conformità alle normative in vari settori e aree geografiche:

## <a name="hipaa"></a>HIPAA

Un'applicazione di servizi sanitari che elabora informazioni sanitarie protette (PHI) è soggetta sia alla normativa sulla privacy sia al regolamento di sicurezza inclusi all'interno dell'Health Information Portability and Accountability Act (HIPAA). Come minimo, HIPAA potrebbe richiedere che un'azienda sanitaria debba ricevere garanzie scritte dal provider di servizi cloud che proteggerà qualsiasi PHI ricevuto o creato.

## <a name="pci"></a>PCI

Payment Card Industry Data Security Standard (PCI DSS) è uno standard di sicurezza delle informazioni proprietarie per le organizzazioni che gestiscono carte di credito dei principali circuiti, tra cui Visa, MasterCard, American Express, Discover e JCB. Lo standard PCI è obbligatorio per i marchi di carte di credito ed è stato istituito dal Payment Card Industry Security Standards Council. Lo standard è stato creato per aumentare i controlli sui dati dei titolari di carte di credito per ridurre il rischio di frodi. La convalida della conformità viene eseguita una volta all'anno da un Qualified Security Assessor (QSA) esterno o da un Internal Security Assessor (ISA) dell'azienda, che crea un rapporto di conformità (ROC) per le organizzazioni che gestiscono volumi elevati di transazioni o sottopone un questionario di autovalutazione (SAQ) alle aziende.

## <a name="personal-data"></a>Dati personali

I dati personali sono informazioni che possono essere usate per identificare un utente, un dipendente, un partner o qualsiasi altra persona vivente o legale. Molte leggi emergenti, in particolare quelle riguardanti la privacy e i dati personali, richiedono che le aziende siano conformi e segnalino la conformità e le eventuali violazioni che potrebbero verificarsi.

## <a name="gdpr"></a>GDPR

Uno degli sviluppi più importanti in questo ambito è la recente promulgazione del Regolamento generale sulla protezione dei dati (GDPR) della Commissione europea, progettato per rafforzare la protezione dei dati degli utenti nell'Unione Europea. GDPR richiede che i dati relativi a singoli utenti (ad esempio "un nome, un indirizzo di casa, una foto, un indirizzo di posta elettronica, dettagli della banca, post su siti Web di social networking, informazioni mediche o un indirizzo IP del computer") vengano mantenuti nei server all'interno dell'Unione europea e non trasferiti di esso. Inoltre, richiede che le aziende inviino notifiche a singoli utenti di eventuali violazioni dei dati e che le aziende dispongano di un responsabile della protezione dei dati (DPO). Gli altri paesi hanno già (o stanno sviluppando) normative analoghe.

## <a name="compliant-foundation-in-azure"></a>Conformità in Azure

Per consentire ai clienti di soddisfare i propri obblighi di conformità nei settori regolamentati e nei mercati in tutto il mondo,&mdash;Azure mantiene il più ampio portfolio di conformità nel settore (numero totale di offerte), oltre a una profondità (numero di Servizi rivolte ai clienti nell'ambito della valutazione). Le offerte di conformità di Azure sono raggruppate in quattro segmenti: applicabili a livello globale, enti pubblici degli Stati Uniti, specifiche del settore e specifiche dell'area o del paese.

Le offerte di conformità di Azure si basano su vari tipi di garanzie, tra cui certificazioni formali, attestazioni, convalide, autorizzazioni e valutazioni generate da società di revisione indipendenti di terze parti, nonché modifiche contrattuali, autovalutazioni e documenti sussidiari per i clienti prodotti da Microsoft. La descrizione di ogni offerta in questo documento presenta una dichiarazione aggiornata dell'ambito di applicazione che indica quali servizi di Azure rivolti ai clienti rientrino nell'ambito della valutazione e offre collegamenti a risorse scaricabili per facilitare ai clienti l'adempimento dei propri obblighi in termini di conformità.

Informazioni più dettagliate sulle offerte di conformità di Azure sono disponibili su [Microsoft Trust Center](https://www.microsoft.com/trustcenter/compliance/complianceofferings). Inoltre, tutte le documentazioni scaricabili sono disponibili per determinati clienti di Azure dal [portale di attendibilità del servizio](https://servicetrust.microsoft.com) nelle seguenti sezioni:

- **Report di controllo:** Include le sezioni per i report FedRAMP, GRC Assessment, ISO, PCI DSS e SOC.
- **Risorse di protezione dati:** Include guide alla conformità, domande frequenti e white paper, nonché sezioni relative a test di penna e valutazione della sicurezza.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sulla preparazione per la sicurezza nel cloud.

> [!div class="nextstepaction"]
> [Preparazione alla sicurezza del cloud](./how-can-a-ciso-prepare-for-the-cloud.md)
