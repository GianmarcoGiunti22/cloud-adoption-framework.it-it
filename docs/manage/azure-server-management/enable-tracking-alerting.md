---
title: Abilita rilevamento e avvisi per le modifiche critiche
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Abilita rilevamento e avvisi per le modifiche critiche
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: f3faa122039097dd6f0f4df1d6f5071b77816545
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656633"
---
# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Abilita rilevamento e avvisi per le modifiche critiche

Azure Rilevamento modifiche e l'inventario forniscono avvisi sullo stato di configurazione dell'ambiente ibrido e sulle modifiche apportate a tale ambiente. Può segnalare modifiche critiche a file, servizi, software e registro di sistema che potrebbero influire sui server distribuiti.

Per impostazione predefinita, il servizio inventario di automazione di Azure non monitora i file o le impostazioni del registro di sistema. La soluzione fornisce un elenco di chiavi del registro di sistema consigliate per il monitoraggio. Per visualizzare questo elenco, passare all'account di automazione nella portale di Azure e selezionare **inventory** > **Edit Settings**.

![Screenshot della visualizzazione inventario di automazione di Azure nella portale di Azure](./media/change-tracking1.png)

Per ulteriori informazioni su ogni chiave del registro di sistema, vedere [rilevamento delle modifiche della chiave del registro di sistema](https://docs.microsoft.com/azure/automation/automation-change-tracking#registry-key-change-tracking). Selezionare un tasto qualsiasi per valutare e quindi abilitarlo. L'impostazione viene applicata a tutte le macchine virtuali abilitate nell'area di lavoro corrente.

È anche possibile usare il servizio per tenere traccia delle modifiche dei file critiche. Ad esempio, si potrebbe voler tenere traccia del file C:\windows\system32\drivers\etc\hosts perché il sistema operativo lo usa per eseguire il mapping dei nomi host agli indirizzi IP. Le modifiche a questo file possono causare problemi di connettività o reindirizzare il traffico a siti Web pericolosi.

Per abilitare il rilevamento del contenuto di file per il file degli host, seguire i passaggi in [abilitare il rilevamento del contenuto del file](https://docs.microsoft.com/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

È anche possibile aggiungere un avviso per le modifiche ai file di cui si sta eseguendo il monitoraggio. Si immagini, ad esempio, di voler impostare un avviso per le modifiche apportate al file degli host. Selezionare **log Analytics** sulla barra dei comandi o cercare log per l'area di lavoro log Analytics collegata. In Log Analytics utilizzare la query seguente per cercare le modifiche apportate al file hosts:

```kusto
ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
```

![Screenshot dell'editor di query di Log Analytics nell'portale di Azure](./media/change-tracking2.png)

Questa query cerca le modifiche apportate al contenuto dei file con un percorso che contiene la parola "hosts". È anche possibile cercare un file specifico modificando il parametro path. ad esempio `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`.
  
Dopo che la query ha restituito i risultati, selezionare **nuova regola di avviso** per aprire l'Editor regole di avviso. È anche possibile ottenere questo editor tramite monitoraggio di Azure nel portale di Azure.

Nell'editor delle regole di avviso esaminare la query e modificare la logica di avviso, se necessario. In questo caso, si desidera che l'avviso venga generato se vengono rilevate modifiche in qualsiasi computer nell'ambiente.

![Screenshot dell'editor delle regole di avviso Log Analytics nella portale di Azure](./media/change-tracking3.png)

Dopo aver impostato la logica della condizione, è possibile assegnare gruppi di azioni per eseguire azioni in risposta all'avviso. In questo esempio, quando viene generato l'avviso, vengono inviati messaggi di posta elettronica e viene creato un ticket ITSM. È possibile eseguire molte altre azioni utili, ad esempio l'attivazione di una funzione di Azure, un Runbook di automazione di Azure, un webhook o un'app per la logica.

![Screenshot del riepilogo della regola di avviso di esempio nell'portale di Azure](./media/change-tracking4.png)

Dopo aver impostato tutti i parametri e la logica, applicare l'avviso all'ambiente.

## <a name="tracking-and-alerting-examples"></a>Esempi di rilevamento e avviso

In questa sezione vengono illustrati altri scenari comuni per il rilevamento e l'invio di avvisi che è possibile utilizzare.

### <a name="driver-file-changed"></a>File del driver modificato

Utilizzare la query seguente per rilevare se i file del driver vengono modificati, aggiunti o rimossi. È utile per tenere traccia delle modifiche apportate ai file di sistema critici.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Servizio specifico arrestato

Utilizzare la query seguente per tenere traccia delle modifiche apportate ai servizi critici del sistema.

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Nuovo software installato

Usare la query seguente per gli ambienti che devono bloccare le configurazioni software.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>La versione software specifica è o non è installata in un computer

Utilizzare la query seguente per valutare la sicurezza. Questa query fa riferimento `ConfigurationData`, che contiene i log per l'inventario e fornisce l'ultimo stato di configurazione segnalato, non le modifiche.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-the-registry"></a>DLL nota modificata nel registro di sistema

Utilizzare la query seguente per rilevare le modifiche apportate alle chiavi del registro di sistema note.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come usare automazione di Azure per [creare pianificazioni](./update-schedules.md) degli aggiornamenti per gestire gli aggiornamenti ai server.

> [!div class="nextstepaction"]
> [Creare pianificazioni degli aggiornamenti](./update-schedules.md)
