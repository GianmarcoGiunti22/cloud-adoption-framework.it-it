---
title: 'Pronto: convenzioni di denominazione e assegnazione di tag consigliate'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Questo articolo fornisce raccomandazioni dettagliate per l'assegnazione di nomi e tag mirate specificamente a supportare le attività aziendali di adozione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness
ms.openlocfilehash: 9caeca52ba0ab3a909b0f42ac6f016d44033a4ee
ms.sourcegitcommit: 617c3f12a3657a8a1393fd08d261dd98eb81b65c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74086792"
---
# <a name="ready-recommended-naming-and-tagging-conventions"></a>Pronto: convenzioni di denominazione e assegnazione di tag consigliate

Organizzare asset basati sul cloud in modo da facilitare la gestione operativa e supportare i requisiti di contabilità è una sfida comune che richiede un grande impegno nell'ambito delle attività di adozione del cloud. Applicando alle risorse ospitate nel cloud convenzioni ben definite di assegnazione di tag ai metadati e di denominazione, il personale IT può trovare e gestire rapidamente le risorse. Nomi e tag ben definiti contribuiscono anche a uniformare i costi di utilizzo del cloud ai team aziendali tramite meccanismi contabili di chargeback e showback.

Le regole di [denominazione e le restrizioni per le risorse di Azure di](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) centro architetture di Azure forniscono indicazioni generali e limitazioni della piattaforma. La discussione seguente estende queste indicazioni generiche con raccomandazioni più dettagliate destinate specificamente a supportare le attività di adozione del cloud nelle aziende.

I nomi delle risorse possono essere difficili da modificare. Deve essere quindi una priorità dei team di adozione del cloud definire una convenzione di denominazione completa prima di iniziare una vasta distribuzione nel cloud.

> [!NOTE]
> Ogni azienda ha requisiti di gestione e organizzazione diversi. Le raccomandazioni fornite in questo articolo sono un punto di partenza per le discussioni nei team di adozione del cloud.
>
> Man mano che queste discussioni progrediscono, usare il modello seguente per registrare le decisioni relative all'assegnazione di tag e alla denominazione che vengono definite quando si uniformano queste raccomandazioni con esigenze aziendali specifiche.
>
> Scaricare il [modello di registrazione delle convenzioni di assegnazione di tag e di denominazione](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Denominazione delle risorse e applicazione di tag

La strategia di applicazione di tag e di denominazione include dettagli aziendali e operativi come componenti di nomi delle risorse e di tag di metadati:

- L'aspetto di questa strategia relativo all'azienda deve garantire che i tag e i nomi delle risorse includano le informazioni aziendali necessarie per identificare i team. Usare una risorsa assieme ai proprietari aziendali responsabili dei costi delle risorse.
- L'aspetto operativo garantisce che i nomi e i tag includano le informazioni usate dai team IT per identificare il carico di lavoro, l'applicazione, l'ambiente, la criticità e altre informazioni utili per la gestione delle risorse.

### <a name="resource-naming"></a>Denominazione delle risorse

Una convenzione di denominazione efficace assembla i nomi delle risorse usando informazioni importanti delle risorse come parti del nome di una risorsa. Ad esempio, usando le convenzioni di denominazione consigliate descritte [più avanti in questo articolo](#sample-naming-convention), una risorsa IP pubblica per un carico di lavoro di SharePoint di produzione può essere denominata `pip-sharepoint-prod-westus-001`.

Dal nome è possibile identificare rapidamente il tipo di risorsa, il carico di lavoro associato, l'ambiente di distribuzione e l'area di Azure in cui è ospitata.

#### <a name="naming-scope"></a>Ambito della denominazione

Tutti i tipi di risorse di Azure hanno un ambito che definisce il livello in cui i nomi delle risorse devono essere univoci. Una risorsa deve avere un nome univoco all'interno dell'ambito.

Ad esempio, una rete virtuale ha un ambito di gruppo di risorse, il che significa che può essere presente una sola rete denominata `vnet-prod-westus-001` in un dato gruppo di risorse. Altri gruppi di risorse possono avere una propria rete virtuale denominata `vnet-prod-westus-001`. Le subnet, per fornire un altro esempio, hanno come ambito le reti virtuali, il che significa che ogni subnet all'interno di una rete virtuale deve essere denominata in modo univoco.

Alcuni nomi di risorse, ad esempio i servizi PaaS con endpoint pubblici o etichette DNS di macchine virtuali, hanno ambiti globali, il che significa che devono essere univoci nell'intera piattaforma Azure.

I nomi delle risorse hanno limiti di lunghezza. Quando si sviluppano le convenzioni di denominazione, è importante trovare un punto di equilibrio tra il contesto incorporato in un nome e i relativi ambito e lunghezza. Per altre informazioni sulle regole di denominazione relative ai caratteri consentiti, agli ambiti e alle lunghezze dei nomi per i tipi di risorse, vedere [Convenzioni di denominazione per le risorse di Azure](/azure/architecture/best-practices/resource-naming).

#### <a name="recommended-naming-components"></a>Componenti di denominazione consigliati

Quando si definisce la convenzione di denominazione, identificare le informazioni chiave che devono riflettersi in un nome di risorsa. Le informazioni importanti variano a seconda dei tipi di risorse. L'elenco seguente fornisce esempi di informazioni utili per la creazione di nomi di risorse.

Fare in modo che i componenti di denominazione siano brevi per evitare di superare i limiti di lunghezza dei nomi delle risorse.

| Componente di denominazione | DESCRIZIONE | esempi |
| --- | --- | --- |
| Business unit | Divisione di livello principale della società che possiede la sottoscrizione o carico di lavoro a cui appartiene la risorsa. Nelle organizzazioni più piccole questo componente potrebbe rappresentare un singolo elemento organizzativo di livello principale dell'azienda. | *fin*, *mktg*, *product*, *it*, *corp* |
| Tipo di sottoscrizione | Descrizione riepilogativa dello scopo della sottoscrizione che contiene la risorsa. Spesso suddivisa in base al tipo di ambiente di distribuzione o a carichi di lavoro specifici. | *prod,* s*hared, client* |
| Nome di applicazione o di servizio | Nome dell'applicazione, del carico di lavoro o del servizio di cui fa parte la risorsa. | *navigator*, *emissions*, *sharepoint*, *hadoop* |
| Ambiente di distribuzione | Fase del ciclo di vita di sviluppo per il carico di lavoro supportato dalla risorsa. | *prod, dev, qa, stage, test* |
| Area | Area di Azure in cui è distribuita la risorsa. | *westus, eastus2, westeurope, usgovia* |

#### <a name="recommended-resource-type-prefixes"></a>Prefissi di tipo di risorsa consigliati

Ogni carico di lavoro può essere costituito da più risorse e servizi singoli. Incorporando i prefissi dei tipi di risorse nei nomi delle risorse, è più semplice identificare visivamente i componenti dell'applicazione o del servizio.

L'elenco seguente fornisce i prefissi dei tipi di risorse di Azure consigliati da usare quando si definiscono le convenzioni di denominazione.

| Tipo di risorsa                       | Prefisso nome risorsa |
| ----------------------------------- | -------------------- |
| Resource group                      | rg-                  |
| Rete virtuale di Azure               | vnet-                |
| Gateway di rete virtuale             | vnet-gw-             |
| Connessione gateway                  | cn-                  |
| Subnet                              | snet-                |
| Gruppo di sicurezza di rete              | nsg-                 |
| Tabella di route                         | Route               |
| Macchine virtuali di Azure              | vm-                  |
| Account di archiviazione di macchine virtuali                  | stvm                 |
| IP pubblico                           | pip-                 |
| Servizio di bilanciamento del carico di Azure                 | lb-                  |
| NIC                                 | nic-                 |
| Azure Key Vault                     | KV                  |
| Servizio Azure Kubernetes            | AKS                 |
| Bus di servizio di Azure                   | sb-                  |
| Code del bus di servizio di Azure            | sbq-                 |
| App del Servizio app di Azure              | azapp-               |
| App di Funzioni di Azure                | azfun-               |
| Servizi cloud di Azure                | azcs-                |
| database SQL di Azure                  | sqldb-               |
| Azure Cosmos DB (noto precedentemente come Azure DocumentDB) | cosdb-               |
| Cache Redis di Azure               | redis-               |
| Database di Azure per MySQL            | mysql-               |
| Azure SQL Data Warehouse            | sqldw-               |
| SQL Server Stretch Database         | sqlstrdb-            |
| Archiviazione di Azure                       | stor                 |
| Azure StorSimple                    | ssimp                |
| Ricerca di Azure                        | srch-                |
| Servizi cognitivi di Azure            | cs-                  |
| Area di lavoro di Azure Machine Learning    | aml-                 |
| Archiviazione di Azure Data Lake             | dls                  |
| Azure Data Lake Analytics.           | dla                  |
| Azure HDInsight - Spark             | hdis-                |
| Azure HDInsight - Hadoop            | hdihd-               |
| Azure HDInsight - R Server          | hdir-                |
| Azure HDInsight - HBase             | hdihb-               |
| Power BI Embedded                   | pbiemb               |
| Azure Stream Analytics              | asa-                 |
| Data factory di Azure                  | df-                  |
| Hub eventi di Azure                    | evh-                 |
| Hub IoT Azure                       | aih-                 |
| Hub di notifica di Azure             | anh-                 |
| Spazio dei nomi di Hub di notifica di Azure   | anhns-               |

### <a name="metadata-tags"></a>Tag dei metadati

Quando si applicano tag di metadati alle risorse cloud, è possibile includere informazioni su tali asset che non è stato possibile includere nel nome della risorsa. È possibile usare tali informazioni per eseguire operazioni più sofisticate di filtraggio e creazione di report per le risorse. I tag devono includere il contesto dell'applicazione o del carico di lavoro associato, i requisiti operativi e le informazioni sulla proprietà della risorsa. Queste informazioni possono essere usate dai team IT o aziendali per individuare le risorse o generare report sull'uso delle risorse e sulla fatturazione.

La scelta dei tag da applicare alle risorse e dei tag obbligatori o facoltativi varia tra le organizzazioni. L'elenco seguente riporta alcuni esempi di tag comuni che includono contesto e informazioni importanti su una risorsa. Usare questo elenco come punto di partenza per definire le proprie convenzioni di assegnazione dei tag.

| Nome del tag                  | DESCRIZIONE                                                                                                                                                                                                    | Chiave               | Valore di esempio                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------|
| Nome dell'applicazione          | Nome dell'applicazione, del servizio o del carico di lavoro a cui è associata la risorsa.                                                                                                                                 | *ApplicationName* | *{app name}*                                    |
| Nome del responsabile approvazione             | Persona responsabile dell'approvazione dei costi correlati a questa risorsa.                                                                                                                                               | *Approver*        | *{email}*                                       |
| Budget richiesto/approvato  | Denaro allocato per l'applicazione, il servizio o il carico di lavoro.                                                                                                                                                    | *BudgetAmount*    | *{\$}*                                          |
| Business unit             | Divisione di livello principale della società che possiede la sottoscrizione o carico di lavoro a cui appartiene la risorsa. Nelle organizzazioni più piccole questo tag potrebbe rappresentare un elemento organizzativo di livello principale condiviso o di una singola azienda. | *BusinessUnit*    | *FINANCE, MARKETING,{Product Name}, CORP, SHARED* |
| Centro di costo               | Centro di costo di contabilità associato a questa risorsa.                                                                                                                                                          | *CostCenter*      | *Number*{3}                                      |
| Ripristino di emergenza         | Criticità aziendale dell'applicazione, del carico di lavoro o del servizio.                                                                                                                                                | *DR*              | *Mission-critical, Critical, Essential*         |
| Data di fine del progetto   | Data in cui l'applicazione, il carico di lavoro o il servizio è pianificato per il ritiro.                                                                                                                                  | *EndDate*         | *{date}*                                        |
| Environment               | Ambiente di distribuzione dell'applicazione, del carico di lavoro o del servizio.                                                                                                                                              | *Env*             | *Prod, Dev, QA, Stage, Test*                    |
| Nome proprietario                | Proprietario dell'applicazione, del carico di lavoro o del servizio.                                                                                                                                                                | *Proprietario*           | *{email}*                                       |
| Nome richiedente            | Utente che ha richiesto la creazione dell'applicazione.                                                                                                                                                          | *Requestor*       | *{email}*                                       |
| Classe servizio             | Livello di contratto di servizio dell'applicazione, del carico di lavoro o del servizio.                                                                                                                                       | *ServiceClass*    | *Dev, Bronze, Silver, Gold*                     |
| Data di inizio del progetto | Data in cui l'applicazione, il carico di lavoro o il servizio è pianificato per la prima distribuzione.                                                                                                                                           | *StartDate*       | *{date}*                                        |

## <a name="sample-naming-convention"></a>Convenzione di denominazione di esempio

La sezione seguente fornisce esempi di schemi di denominazione per tipi di risorse di Azure comuni distribuiti durante una distribuzione cloud aziendale.

<!-- markdownlint-disable MD033 -->

### <a name="subscriptions"></a>Sottoscrizioni

| Tipo di asset   | Ambito                        | Format                                             | esempi                                     |
|--------------|------------------------------|----------------------------------------------------|----------------------------------------------|
| Sottoscrizione | Contratto Enterprise/account | \<Business unit\>-\<Tipo di sottoscrizione\>-\<\#\#\#\> | <ul><li>mktg-prod-001 </li><li>corp-shared-001 </li><li>fin-client-001</li></ul> |

### <a name="resource-groups"></a>Gruppi di risorse

| Tipo di asset     | Ambito        | Format                                                     | esempi                                                                            |
|----------------|--------------|------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Resource group | Sottoscrizione | RG-\<app o nome servizio\>-\<tipo di sottoscrizione\>-\<\#\#\#\> | <ul><li>rg-mktgsharepoint-prod-001 </li><li>rg-acctlookupsvc-share-001 </li><li>rg-ad-dir-services-shared-001</li></ul> |

### <a name="virtual-networking"></a>Reti virtuali

| Tipo di asset               | Ambito           | Format                                                                | esempi                                                                                              |
|--------------------------|-----------------|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Rete virtuale di Azure          | Resource group  | vnet-\<Tipo di sottoscrizione\>-\<Area\>-\<\#\#\#\>                      | <ul><li>vnet-shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-client-eastus2-001</li></ul>                                  |
| Gateway virtuale di rete virtuale     | rete virtuale | vnet-gw-v-\<Tipo di sottoscrizione\>-\<Area\>-\<\#\#\#\>                 | <ul><li>vnet-gw-v-shared-eastus2-001 </li><li>vnet-gw-v-prod-westus-001 </li><li>vnet-gw-v-client-eastus2-001</li></ul>                   |
| Gateway locale di rete virtuale       | Gateway virtuale | vnet-gw-l-\<Tipo di sottoscrizione\>-\<Area\>-\<\#\#\#\>                 | <ul><li>vnet-gw-l-shared-eastus2-001 </li><li>vnet-gw-l-prod-westus-001 </li><li>vnet-gw-l-client-eastus2-001</li></ul>                   |
| Connessioni da sito a sito | Resource group  | cn-\<nome gateway locale\>-to-\<nome gateway virtuale\>                 | <ul><li>cn-l-gw-shared-eastus2-001-to-v-gw-shared-eastus2-001 </li><li>cn-l-gw-shared-eastus2-001-to-shared-westus-001</li></ul> |
| Connessioni di rete virtuale         | Resource group  | cn-\<sottoscrizione1\>\<area1\>-to-\<sottoscrizione2\>\<area2\>-      | <ul><li>cn-shared-eastus2-to-shared-westus </li><li>cn-prod-eastus2-to-prod-westus</li></ul>                                     |
| Subnet                   | rete virtuale | snet-\<sottoscrizione\>-\<area secondaria\>-\<\#\#\#\>                       | <ul><li>snet-shared-eastus2-001 </li><li>snet-prod-westus-001 </li><li>snet-client-eastus2-001</li></ul>                                  |
| Gruppo di sicurezza di rete   | Subnet o scheda di interfaccia di rete   | nsg-\<nome criterio o nome app\>-\<\#\#\#\>                             | <ul><li>nsg-weballow-001 </li><li>nsg-rdpallow-001 </li><li>nsg-sqlallow-001 </li><li>nsg-dnsbloked-001</li></ul>                                  |
| IP pubblico                | Resource group  | pip-\<nome macchina virtuale o nome app\>-\<Ambiente\>-\<area secondaria\>-\<\#\#\#\> | <ul><li>pip-dc1-shared-eastus2-001 </li><li>pip-hadoop-prod-westus-001</li></ul>                                                 |

### <a name="azure-virtual-machines"></a>Macchine virtuali di Azure

| Tipo di asset         | Ambito          | Format                                                              | esempi                                                                             |
|--------------------|----------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Macchine virtuali di Azure    | Resource group | vm\<nome criterio o nome app\>\<\#\#\#\>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Account di archiviazione di macchine virtuali | Globale         | stvm\<tipo di prestazioni\>\<nome app o nome prodotto\>\<area\>\<\#\#\#\> | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Etichetta DNS          | Globale         | \<Un record di macchina virtuale\>.[\<area\>.cloudapp.azure.com]                  | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                        |
| Servizio di bilanciamento del carico di Azure      | Resource group | lb-\<nome o ruolo app\>\<Ambiente\>\<\#\#\#\>                    | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                          |
| NIC                | Resource group | nic-\<\#\#\>-\<nome macchina virtuale\>-\<sottoscrizione\>\<\#\#\#\>                  | <ul><li>nic-01-dc1-shared-001 </li><li>nic-02-vmhadoop1-prod-001 </li><li>nic-02-vmtest1-client-001</li></ul>            |

### <a name="paas-services"></a>Servizi PaaS

| Tipo di asset     | Ambito  | Format                                                              | esempi                                                                                 |
|----------------|--------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| servizio app di Azure    | Globale | azapp-\<Nome app\>-\<Ambiente\>-\<\#\#\#\>.[{azurewebsites.net}] | <ul><li>azapp-navigator-prod-001.azurewebsites.net </li><li>azapp-accountlookup-dev-001.azurewebsites.net</li></ul> |
| App Funzioni di Azure   | Globale | azfun-\<Nome app\>-\<Ambiente\>-\<\#\#\#\>.[{azurewebsites.net}] | <ul><li>azfun-navigator-prod-001.azurewebsites.net </li><li>azfun-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Servizi cloud di Azure | Globale | azcs-\<Nome app\>-\<Ambiente\>-\<\#\#\#\>.[{cloudapp.net}]       | <ul><li>azcs-navigator-prod-001.azurewebsites.net </li><li>azcs-accountlookup-dev-001.azurewebsites.net</li></ul>   |

### <a name="azure-service-bus"></a>Bus di servizio di Azure

| Tipo di asset         | Ambito       | Format                                                     | esempi                           |
|--------------------|-------------|------------------------------------------------------------|------------------------------------|
| Bus di servizio di Azure        | Globale      | sb-\<Nome app\>-\<Ambiente\>.[{servicebus.windows.net}] | <ul><li>sb-navigator-prod </li><li>sb-emissions-dev</li></ul> |
| Code del bus di servizio di Azure | BUS DI SERVIZIO | sbq-\<descrittore query\>                                   | <ul><li>sbq-messagequery</li></ul>                   |

### <a name="databases"></a>Database

| Tipo di asset                          | Ambito              | Format                                | esempi                                       |
|-------------------------------------|--------------------|---------------------------------------|------------------------------------------------|
| database SQL di Azure                  | Globale             | sqldb-\<Nome app\>-\<Ambiente\>    | <ul><li>sqldb-navigator-prod </li><li>sqldb-emissions-dev</li></ul>       |
| Azure Cosmos DB (noto precedentemente come DocumentDB) | Globale             | cosdb-\<Nome app\>-\<Ambiente\>    | <ul><li>cosdb-navigator-prod </li><li>cosdb-emissions-dev</li></ul>       |
| Cache Redis di Azure               | Globale             | redis-\<Nome app\>-\<Ambiente\>    | <ul><li>redis-navigator-prod </li><li>redis-emissions-dev</li></ul>       |
| Database di Azure per MySQL            | Globale             | mysql-\<Nome app\>-\<Ambiente\>    | <ul><li>mysql-navigator-prod </li><li>mysql-emissions-dev</li></ul>       |
| Azure SQL Data Warehouse                  | Globale             | sqldw-\<Nome app\>-\<Ambiente\>    | <ul><li>sqldw-navigator-prod </li><li>sqldw-emissions-dev</li></ul>       |
| SQL Server Stretch Database         | database SQL di Azure | sqlstrdb-\<Nome app\>-\<Ambiente\> | <ul><li>sqlstrdb-navigator-prod </li><li>sqlstrdb-emissions-dev</li></ul> |

### <a name="storage"></a>Archiviazione

| Tipo di asset                              | Ambito  | Format                                                                        | esempi                                   |
|-----------------------------------------|--------|-------------------------------------------------------------------------------|--------------------------------------------|
| Account di archiviazione di Azure - Uso generale     | Globale | st\<nome spazio di archiviazione\>\<\#\#\#\>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Account di archiviazione di Azure - Log di diagnostica. | Globale | stdiag\<prime 2 lettere del nome di sottoscrizione e numero\>\<area\>\<\#\#\#\> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                              | Globale | ssimp\<Nome app\>\<Ambiente\>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="ai--machine-learning"></a>Intelligenza artificiale e Machine Learning

| Tipo di asset                       | Ambito          | Format                            | esempi                               |
|----------------------------------|----------------|-----------------------------------|----------------------------------------|
| Ricerca di Azure                     | Globale         | srch-\<Nome app\>-\<Ambiente\> | <ul><li>srch-navigator-prod </li><li>srch-emissions-dev</li></ul> |
| Servizi cognitivi di Azure               | Resource group | cs-\<Nome app\>-\<Ambiente\>   | <ul><li>cs-navigator-prod </li><li>cs-emissions-dev</li></ul>     |
| Area di lavoro di Azure Machine Learning | Resource group | aml-\<Nome app\>-\<Ambiente\>  | <ul><li>aml-navigator-prod </li><li>aml-emissions-dev</li></ul>   |

### <a name="analytics"></a>Analisi

| Tipo di asset                | Ambito  | Format                             | esempi                                 |
|---------------------------|--------|------------------------------------|------------------------------------------|
| Data factory di Azure        | Globale | df-\<Nome app\>\<Ambiente\>     | <ul><li>df-navigator-prod </li><li>df-emissions-dev</li></ul>       |
| Archiviazione di Azure Data Lake   | Globale | dls\<Nome app\>\<Ambiente\>     | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>         |
| Azure Data Lake Analytics. | Globale | dla\<Nome app\>\<Ambiente\>     | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>         |
| Azure HDInsight - Spark         | Globale | hdis-\<Nome app\>-\<Ambiente\>  | <ul><li>hdis-navigator-prod </li><li>hdis-emissions-dev </li></ul>  |
| Azure HDInsight - Hadoop        | Globale | hdihd-\<Nome app\>-\<Ambiente\> | <ul><li>hdihd-hadoop-prod </li><li>hdihd-emissions-dev</li></ul>    |
| Azure HDInsight - R Server      | Globale | hdir-\<Nome app\>-\<Ambiente\>  | <ul><li>hdir-navigator-prod </li><li>hdir-emissions-dev</li></ul>   |
| Azure HDInsight - HBase         | Globale | hdihb-\<Nome app\>-\<Ambiente\> | <ul><li>hdihb-navigator-prod </li><li>hdihb-emissions-dev</li></ul> |
| Power BI Embedded         | Globale | pbiemb\<Nome app\>\<Ambiente\>  | <ul><li>pbiem-navigator-prod </li><li>pbiem-emissions-dev</li></ul> |

### <a name="internet-of-things-iot"></a>Internet delle cose

| Tipo di asset                         | Ambito          | Format                             | esempi                                 |
|------------------------------------|----------------|------------------------------------|------------------------------------------|
| Analisi di flusso di Azure in IoT Edge | Resource group | asa-\<Nome app\>-\<Ambiente\>   | <ul><li>asa-navigator-prod </li><li>asa-emissions-dev</li></ul>     |
| Hub IoT Azure                      | Globale         | aih-\<Nome app\>-\<Ambiente\>   | <ul><li>aih-navigator-prod </li><li>aih-emissions-dev</li></ul>     |
| Hub eventi di Azure                          | Globale         | evh-\<Nome app\>-\<Ambiente\>   | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>     |
| Hub di notifica di Azure                   | Resource group | anh-\<Nome app\>-\<Ambiente\>   | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>     |
| Spazio dei nomi di Hub di notifica di Azure         | Globale         | anhns-\<Nome app\>-\<Ambiente\> | <ul><li>anhns-navigator-prod </li><li>anhns-emissions-dev</li></ul> |
