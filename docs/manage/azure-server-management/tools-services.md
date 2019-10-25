---
title: Strumenti e servizi di gestione del server di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti e servizi di gestione del server di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: e365cca30b5fe98e0737beb3005a13544844dc41
ms.sourcegitcommit: 15898374495761bfb76cee719e0f9189856884e6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888879"
---
# <a name="azure-server-management-tools-and-services"></a>Strumenti e servizi di gestione del server di Azure

Come illustrato nella [Panoramica](./index.md) di questa sezione, Azure Server Management Services Suite copre le aree seguenti:

- [Migrazione](#migrate)
- [Proteggere](#secure)
- [Proteggere](#protect)
- [Monitorare](#monitor)
- [Configurare](#configure)
- [Governare](#govern)

Le sezioni seguenti descrivono brevemente queste aree di gestione e forniscono collegamenti a contenuti dettagliati sui principali servizi di Azure che li supportano.

## <a name="migrate"></a>Migrazione

I servizi di migrazione consentono di eseguire la migrazione dei carichi di lavoro in Azure. Per fornire le linee guida ottimali, il servizio Azure Migrate inizia con la misurazione delle prestazioni del server locale e la valutazione dell'idoneità per la migrazione. Al termine della valutazione, è possibile usare [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) e il [servizio migrazione del database di Azure](https://docs.microsoft.com/azure/dms/dms-overview) per eseguire la migrazione dei computer locali in Azure. Azure migrate

## <a name="secure"></a>Sicurezza

Il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) è un'applicazione completa per la gestione della sicurezza. Eseguendo l'onboarding nel centro sicurezza, è possibile ottenere rapidamente una valutazione dello stato di conformità delle normative e della sicurezza dell'ambiente. Per istruzioni sull'onboarding dei server nel centro sicurezza di Azure, vedere [configurare i servizi di gestione di Azure per una sottoscrizione](./onboard-at-scale.md#azure-security-center).

## <a name="protect"></a>Protezione

Per proteggere i dati, è necessario pianificare il backup, la disponibilità elevata, la crittografia, l'autorizzazione e i problemi operativi correlati. Questi argomenti sono trattati in modo estensivo, quindi in questo articolo si concentrerà sulla creazione di un piano di ripristino di emergenza per la continuità aziendale (BCDR). Verranno inclusi riferimenti alla documentazione che descrive in dettaglio come implementare e distribuire questo tipo di piano.

Quando si compilano strategie di protezione dei dati, è consigliabile prendere in considerazione la suddivisione delle applicazioni del carico di lavoro nei livelli diversi, perché ogni livello richiede in genere un piano di protezione univoco. Per altre informazioni sulla progettazione di applicazioni resilienti, vedere [progettazione di applicazioni resilienti per Azure](https://docs.microsoft.com/azure/architecture/resiliency).

La protezione dei dati più semplice è backup. Per velocizzare il processo di ripristino in caso di perdita del server, è consigliabile eseguire il backup non solo dei dati, ma anche delle configurazioni del server. Il backup è un meccanismo efficace per gestire l'eliminazione accidentale dei dati e gli attacchi ransomware. [Backup di Azure](https://docs.microsoft.com/azure/backup) consente di proteggere i dati in Azure e nei server locali che eseguono Windows o Linux. Per informazioni dettagliate sulle funzionalità e le guide alle procedure di questo servizio, vedere la [documentazione di backup di Azure](https://docs.microsoft.com/azure/backup/backup-overview).

Il ripristino tramite backup può richiedere molto tempo. Lo standard di settore è in genere un giorno. Se un carico di lavoro richiede la continuità aziendale per errori hardware o interruzioni del Data Center, è consigliabile usare la replica dei dati. [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) fornisce la replica continua delle macchine virtuali, una soluzione che fornisce una perdita di dati minima. Site Recovery supporta anche diversi scenari di replica, ad esempio la replica di VM di Azure tra due aree di Azure, tra server locali e tra l'ambiente locale e Azure. Per ulteriori informazioni, vedere la [matrice di replica complete Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview#what-can-i-replicate).

Per i dati file server, un altro servizio da considerare è [sincronizzazione file di Azure](https://docs.microsoft.com/azure/storage/files/storage-sync-files-planning). Questo servizio consente di centralizzare le condivisioni file dell'organizzazione in File di Azure preservando al tempo stesso la flessibilità, le prestazioni e la compatibilità di un file server locale. Per usare questo servizio, seguire le istruzioni per la distribuzione di Sincronizzazione file di Azure.

## <a name="monitor"></a>Monitorare

[Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) offre una visualizzazione delle varie risorse, ad esempio applicazioni, contenitori e macchine virtuali. Raccoglie anche dati da diverse origini.

- Monitoraggio di Azure per le macchine virtuali ([Insights](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview)) fornisce una visualizzazione approfondita dell'integrità delle macchine virtuali, delle tendenze delle prestazioni e delle dipendenze. Il servizio esegue il monitoraggio dello stato dei sistemi operativi delle macchine virtuali di Azure, dei set di scalabilità di macchine virtuali e dei computer nell'ambiente locale.
- Log Analytics ([log](https://docs.microsoft.com/azure/azure-monitor/platform/data-collection#logs)) è una funzionalità di monitoraggio di Azure. Il suo ruolo è fondamentale per la storia di gestione complessiva di Azure. Funge da archivio dati per l'analisi dei log e per molti altri servizi di Azure. Offre un linguaggio di query avanzato e un motore di analisi che fornisce informazioni dettagliate sul funzionamento delle applicazioni e delle risorse.
- [Log attività di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) è anche una funzionalità di monitoraggio di Azure. Fornisce informazioni approfondite sugli eventi a livello di sottoscrizione che si verificano in Azure.

## <a name="configure"></a>Configurazione

Diversi servizi rientrano in questa categoria. Consentono di automatizzare le attività operative, gestire le configurazioni dei server, misurare la conformità degli aggiornamenti, pianificare gli aggiornamenti e rilevare le modifiche apportate ai server. Questi servizi sono fondamentali per supportare le operazioni in corso.

- [Gestione aggiornamenti](https://docs.microsoft.com/azure/automation/automation-update-management#view-update-assessments) automatizza la distribuzione delle patch nell'ambiente, inclusa la distribuzione in istanze del sistema operativo in esecuzione all'esterno di Azure. Supporta i sistemi operativi Windows e Linux e tiene traccia delle principali vulnerabilità del sistema operativo e della non conformità causata da patch mancanti.
- [Rilevamento modifiche e l'inventario](https://docs.microsoft.com/azure/automation/change-tracking) forniscono informazioni approfondite sul software in esecuzione nell'ambiente in uso e le eventuali modifiche apportate.
- [Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) consente di eseguire script Python e PowerShell o manuali operativi per automatizzare le attività nell'ambiente. Quando si usa il ruolo di [lavoro ibrido per Runbook](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker), è possibile estendere il manuali operativi anche alle risorse locali.
- La [configurazione dello stato di automazione di Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) consente di effettuare il push delle configurazioni DSC (Desired state Configuration) di PowerShell direttamente da Azure. A sua volta, DSC consente di monitorare e mantenere le configurazioni del sistema operativo guest e del carico di lavoro.

## <a name="govern"></a>Governance

L'adozione e il passaggio al cloud creano nuove problematiche di gestione e richiedono un approccio diverso per il passaggio da un carico di gestione operativo al monitoraggio e alla governance. Il Framework di adozione del cloud per Azure inizia con la [governance](../../govern/index.md). Viene illustrato come eseguire la migrazione al cloud, l'aspetto del percorso e chi dovrebbe essere in funzione.

Il progetto di governance per le organizzazioni standard è spesso diverso dalla progettazione della governance per le aziende complesse. Per ulteriori informazioni sulle procedure consigliate per la governance per un'organizzazione standard, vedere [Guida alla governance standard](../../govern/guides/standard/index.md). Per altre informazioni sulle procedure consigliate per la governance per un'azienda complessa, vedere [Guida alla governance per le aziende complesse](../../govern/guides/complex/index.md).

## <a name="billing-information"></a>Informazioni di fatturazione

Per informazioni sui prezzi per i servizi di gestione di Azure, vedere le pagine seguenti:

- [Azure Site Recovery](https://azure.microsoft.com/pricing/details/site-recovery)

- [Backup di Azure](https://azure.microsoft.com/pricing/details/backup)

- [Monitoraggio di Azure](https://azure.microsoft.com/pricing/details/monitor)

- [Centro sicurezza di Azure](https://azure.microsoft.com/pricing/details/security-center)

- [Servizio Gestione aggiornamenti di Azure](https://azure.microsoft.com/pricing/details/automation)

- [Azure Rilevamento modifiche e servizi di inventario](https://azure.microsoft.com/pricing/details/automation)

- [Configurazione dello stato desiderato](https://azure.microsoft.com/pricing/details/automation)

- [Servizio di automazione di Azure](https://azure.microsoft.com/pricing/details/automation)

- [Criteri di Azure](https://azure.microsoft.com/pricing/details/azure-policy)

- [Servizio Sincronizzazione file di Azure](https://azure.microsoft.com/pricing/details/storage/blobs)

> [!NOTE]
> La soluzione Azure Gestione aggiornamenti è gratuita, ma c'è un piccolo costo correlato all'inserimento di dati. Come regola generale, i primi 5 GB al mese di inserimento dei dati sono gratuiti. Si osserva generalmente che ogni computer utilizza circa 25 MB al mese. Circa 200 computer al mese sono coperti gratuitamente. Per ogni server aggiuntivo, moltiplicare il numero di server aggiuntivi di 25 MB al mese. Moltiplicare questo per il costo di archiviazione per la quantità totale di spazio di archiviazione necessario. [I costi di archiviazione sono disponibili qui](https://azure.microsoft.com/pricing/details/storage). Ogni server aggiuntivo deve avere un impatto nominale sul costo.
