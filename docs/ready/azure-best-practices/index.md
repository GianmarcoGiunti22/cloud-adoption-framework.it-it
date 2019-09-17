---
title: Procedure consigliate per l'idoneità per Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione alle procedure consigliate per l'idoneità per Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 275342d452c3f9c47c004014d6e2831c88aa91df
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022245"
---
# <a name="best-practices-for-azure-readiness"></a>Procedure consigliate per l'idoneità per Azure

Gran parte della preparazione al cloud consiste nel dotare il personale delle competenze tecniche necessarie per avviare l'adozione del cloud e preparare l'ambiente di destinazione della migrazione per gli asset e i carichi di lavoro che verranno spostati nel cloud. Gli argomenti seguenti includono le procedure consigliate e altre indicazioni per consentire al team di definire e preparare l'ambiente di Azure.

## <a name="azure-fundamentals"></a>Concetti fondamentali di Azure

Per l'organizzazione e la distribuzione degli asset nell'ambiente di Azure, usare le indicazioni seguenti:

- [Concetti fondamentali di Azure](../considerations/fundamental-concepts.md). Informazioni sui termini e i concetti fondamentali usati in Azure e sulla correlazione tra questi concetti.
- [Convenzioni consigliate per l'assegnazione di nomi e tag](../considerations/naming-and-tagging.md). Esaminare le raccomandazioni dettagliate per l'assegnazione di nomi e tag alle risorse. Queste raccomandazioni sono state appositamente studiate per supportare le attività di adozione del cloud in ambito aziendale.
- [Ridimensionamento con più sottoscrizioni di Azure](../considerations/scaling-subscriptions.md). Informazioni sulle strategie per il ridimensionamento con più sottoscrizioni di Azure.
- [Organizzare le risorse con i gruppi di gestione di Azure](https://docs.microsoft.com/azure/governance/management-groups/?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come i gruppi di gestione di Azure consentono di gestire risorse, ruoli, criteri, nonché la distribuzione tra più sottoscrizioni.
- [Creare coerenza del cloud ibrido](../../infrastructure/misc/hybrid-consistency.md). Creare soluzioni cloud ibride che offrono i vantaggi dell'innovazione cloud, pur mantenendo molte delle caratteristiche della gestione locale.

## <a name="networking"></a>Rete

Per preparare l'infrastruttura di rete cloud per i carichi di lavoro, usare le indicazioni seguenti:

- [Decisioni relative alla rete](../considerations/network-decisions.md). Scegliere i servizi di rete, gli strumenti e le architetture che supportano i requisiti di connettività, governance e carico di lavoro dell'organizzazione.
- [Pianificazione della rete virtuale](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulla pianificazione di reti virtuali in base ai requisiti di isolamento, connettività e località.
- [Procedure consigliate per la sicurezza di rete](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulle procedure consigliate per risolvere problemi comuni di sicurezza della rete usando le funzionalità predefinite di Azure.
- [Reti perimetrali](./perimeter-networks.md). Le reti perimetrali consentono la connettività sicura tra le reti cloud e le reti dei data center locali o fisici, oltre alla connettività da e verso Internet.
- [Topologia di rete hub-spoke](./hub-spoke-network-topology.md). Hub-spoke è un modello di rete per la gestione efficiente dei comuni requisiti di comunicazione o sicurezza per carichi di lavoro complessi. Questo modello è in grado di gestire anche le potenziali limitazioni delle sottoscrizioni di Azure.

## <a name="identity-and-access-control"></a>Identità e controllo di accesso

Per la progettazione dell'infrastruttura di identità e controllo di accesso, in modo da migliorare l'efficienza dei carichi di lavoro in termini di sicurezza e gestione, usare le indicazioni seguenti:

- [Procedure consigliate per la sicurezza con il controllo di accesso e la gestione delle identità di Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulle procedure consigliate per il controllo di accesso e la gestione delle identità con le funzionalità integrate di Azure.
- [Procedure consigliate per il controllo degli accessi in base al ruolo](./roles.md). Il controllo degli accessi in base al ruolo (RBAC) di Azure consente una gestione degli accessi specifica basata su gruppi per risorse organizzate in base ai ruoli utente.
- [Protezione dell'accesso con privilegi per le distribuzioni ibride e cloud in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Azure Active Directory è utile per verificare la sicurezza degli account amministratore e dell'accesso amministrativo dell'organizzazione nell'ambiente cloud e locale.

## <a name="storage"></a>Archiviazione

- [Indicazioni per Archiviazione di Azure](../considerations/storage-guidance.md). Selezionare la soluzione di archiviazione di Azure più adatta per supportare gli scenari di utilizzo.
- [Guida alla sicurezza di Archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulle funzionalità di sicurezza di Archiviazione di Azure.

## <a name="databases"></a>Database

- [Scegliere l'opzione SQL Server più adatta in Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Scegliere la soluzione PaaS o IaaS che supporta meglio i carichi di lavoro di SQL Server.
- [Procedure consigliate per la sicurezza del database](https://docs.microsoft.com/azure/security/azure-database-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni sulle procedure consigliate per la sicurezza del database nella piattaforma Azure.
- [Scegliere l'archivio dati appropriato](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview). La selezione dell'archivio dati corretto per le proprie esigenze è una decisione di progettazione fondamentale. Esistono centinaia di implementazioni tra cui scegliere nei database SQL e NoSQL. Gli archivi dati vengono spesso classificati in base a come strutturano i dati e ai tipi di operazioni supportate. Questo articolo descrive molti dei modelli di archiviazione più comuni.

## <a name="cost-management"></a>Gestione dei costi

- [Tenere traccia dei costi tra business unit, ambienti e progetti](./track-costs.md). Informazioni sulle procedure consigliate per la creazione di meccanismi appropriati di verifica dei costi.
- [Come ottimizzare gli investimenti per il cloud con Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Implementare una strategia per la gestione dei costi e ottenere informazioni sugli strumenti disponibili per la risoluzione di problemi correlati ai costi.
- [Creare e gestire i budget](https://docs.microsoft.com/azure/cost-management/tutorial-acm-create-budgets?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come creare e gestire i budget usando Gestione costi di Azure.
- [Esportare i dati relativi ai costi](https://docs.microsoft.com/azure/cost-management/tutorial-export-acm-data?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come creare e gestire i dati esportati in Gestione costi di Azure.
- [Ottimizzare i costi in base alle raccomandazioni](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come identificare le risorse sottoutilizzate e intervenire per ridurre i costi con Gestione costi di Azure e Azure Advisor.
- [Usare gli avvisi per i costi per monitorare l'uso e le spese](https://docs.microsoft.com/azure/cost-management/cost-mgt-alerts-monitor-usage-spending?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Informazioni su come usare gli avvisi di Gestione costi per il monitoraggio dell'uso e delle spese di Azure.
