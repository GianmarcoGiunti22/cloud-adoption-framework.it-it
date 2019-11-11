---
title: Guida alle decisioni relative alla crittografia
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulla crittografia come servizio di base nelle migrazioni di Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: ed394c0bd1748a6e3382835cec816b552217bd01
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753362"
---
# <a name="encryption-decision-guide"></a>Guida alle decisioni relative alla crittografia

La crittografia protegge i dati dall'accesso non autorizzato. Criteri di crittografia correttamente implementati forniscono ulteriori livelli di sicurezza per i carichi di lavoro basati sul cloud e li proteggono dalle azioni di utenti malintenzionati e altri utenti non autorizzati sia all'interno che all'esterno dell'organizzazione e delle reti.

Passare a: [Gestione delle chiavi](#key-management) | [Crittografia dei dati](#data-encryption) | [Altre informazioni](#learn-more)

La strategia di crittografia per il cloud è incentrata sui criteri aziendali e sui requisiti di conformità. La crittografia delle risorse è consigliabile e molti servizi di Azure, ad esempio Archiviazione di Azure e Database SQL di Azure abilitano la crittografia per impostazione predefinita. Tuttavia, la crittografia ha costi che possono aumentare la latenza e l'utilizzo complessivo delle risorse.

Per i carichi di lavoro complessi, trovare il giusto equilibrio fra crittografia e prestazioni è essenziale, così come determinare le modalità di crittografia dei dati e del traffico. I meccanismi di crittografia possono variare a livello di costi e complessità e sia i requisiti tecnici che per i criteri possono influire sulle decisioni per la modalità di applicazione della crittografia e di archiviazione e gestione dei secreti e delle chiavi cruciali.

I criteri aziendali e la conformità di terze parti sono fattori decisivi nella pianificazione di una strategia di crittografia. Azure offre diversi meccanismi standard che possono soddisfare requisiti comuni per la crittografia dei dati, sia inattivi che in transito. Tuttavia, per i criteri e i requisiti di conformità che richiedono controlli più rigorosi, come i segreti standardizzati e la gestione delle chiavi, la crittografia dei dati in uso o la crittografia specifica dei dati, sarà probabilmente necessario sviluppare una strategia di crittografia più elaborata per il supporto di questi requisiti.

## <a name="key-management"></a>Gestione della chiave

La crittografia dei dati nel cloud dipende dall'archiviazione, dalla gestione e dall'uso operativo in sicurezza delle chiavi di crittografia. Un sistema di gestione delle chiavi è fondamentale per la capacità dell'organizzazione di creare, archiviare e gestire le chiavi di crittografia, nonché password importanti, stringhe di connessione e altre informazioni IT riservate.

I sistemi di gestione delle chiavi moderni, ad esempio Azure Key Vault, supportano l'archiviazione e la gestione di chiavi protette tramite software per l'utilizzo in attività di sviluppo e test e chiavi protette tramite moduli di protezione hardware per ottenere la massima protezione dei carichi di lavoro di produzione o dei dati sensibili.

Nell'ambito della pianificazione di una migrazione al cloud, la tabella seguente può essere utile per decidere come archiviare e gestire le chiavi, i certificati e i segreti di crittografia, che hanno un'importanza fondamentale per la creazione di distribuzioni cloud sicure e gestibili:

| Domanda | Gestione nativa del cloud | BYOK (Bring Your Own Key) | HYOK (Hold Your Own Key) |
|---------------------------------------------------------------------------------------------------------------------------------------|--------------|--------|-------------|
| Nell'organizzazione manca una soluzione di gestione centralizzata di chiavi e segreti?                                                                    | Sì          | No     | No          |
| Sarà necessario limitare la creazione di chiavi e segreti nei dispositivi all'hardware locale, quando si usano queste chiavi nel cloud? | No           | Sì    | No          |
| Nell'organizzazione sono in vigore regole o criteri che impediscono di archiviare le chiavi fuori sede?                | No           | No     | Sì         |

### <a name="cloud-native"></a>Gestione nativa del cloud

Con la gestione delle chiavi nativa del cloud, tutte le chiavi e i segreti vengono generati, gestiti e archiviati in un insieme di credenziali basato sul cloud come Azure Key Vault. Questo approccio semplifica molte attività IT correlate alla gestione delle chiavi, ad esempio backup, archiviazione e rinnovo delle chiavi.

L'uso di un sistema di gestione delle chiavi nativo del cloud presuppone le condizioni seguenti:

- Si considera attendibile la soluzione cloud di gestione delle chiavi con la creazione, la gestione e l'hosting di chiavi e segreti dell'organizzazione.
- Si abilitano tutte le applicazioni e i servizi locali che si basano sull'accesso a servizi di crittografia o segreti ad accedere al sistema di gestione delle chiavi nel cloud.

### <a name="bring-your-own-key"></a>BYOK (Bring Your Own Key)

L'approccio BYOK consiste nel generare chiavi nell'hardware HSM dedicato nell'ambiente locale, per poi trasferirle in modo sicuro in un sistema di gestione basato sul cloud come Azure Key Vault per usarle con le risorse ospitate nel cloud.

**Presupposti per BYOK (Bring Your Own Key):** la generazione di chiavi in locale e il relativo uso con un sistema di gestione delle chiavi basato sul cloud presuppongono le condizioni seguenti:

- Si considera attendibile l'infrastruttura sottostante della piattaforma cloud a livello di sicurezza e controllo di accesso per l'hosting e l'uso di chiavi e segreti.
- Le applicazioni o i servizi ospitati nel cloud sono in grado di accedere alle chiavi e ai segreti e di usarli in modo affidabile e sicuro.
- I criteri normativi o organizzativi richiedono di mantenere nell'ambiente locale la creazione e la gestione dei segreti e delle chiavi dell'organizzazione.

### <a name="on-premises-hold-your-own-key"></a>Gestione locale (HYOK, Hold Your Own Key)

In alcuni scenari potrebbero esistere normative, criteri o motivi tecnici che impediscono di archiviare le chiavi in un sistema di gestione delle chiavi basato sul cloud. In questi casi è necessario generare le chiavi tramite hardware locale, archiviarle e gestirle tramite un sistema di gestione delle chiavi locale e fornire un meccanismo che consenta alle risorse basate sul cloud di accedere a queste chiavi ai fini della crittografia. Tenere presente che un approccio HYOK potrebbe non essere compatibile con tutti i servizi basati su Azure.

**Presupposti relativi alla gestione delle chiavi locale:** l'uso di un sistema di gestione delle chiavi locale presuppone le condizioni seguenti:

- I criteri normativi o organizzativi richiedono di mantenere nell'ambiente locale la creazione, la gestione e l'hosting dei segreti e delle chiavi dell'organizzazione.
- Tutte le applicazioni o i servizi basati sul cloud che si basano sull'accesso a servizi di crittografia o segreti possono accedere al sistema di gestione delle chiavi locale.

## <a name="data-encryption"></a>Crittografia dei dati

Quando si pianificano i criteri di crittografia, considerare i numerosi stati diversi dei dati con esigenze di crittografia diverse:

| Stato dei dati | Dati |
|-----|-----|
| Dati in transito | Traffico di rete interno, connessioni Internet, connessioni fra data center o reti virtuali |
| Dati inattivi    | Database, file, unità virtuali, archivio PaaS |
| Dati in uso     | Dati caricati nella RAM o in cache della CPU |

### <a name="data-in-transit"></a>Dati in transito

I dati in transito sono dati che si spostano tra le risorse nella rete interna, tra i data center, in reti esterne o su Internet.

La crittografia dei dati in transito avviene in genere richiedendo i protocolli SSL/TLS per il traffico di rete. È necessario crittografare sempre il traffico tra le risorse ospitate nel cloud e le reti esterne o la rete Internet pubblica. Le risorse PaaS applicano in genere la crittografia SSL/TLS per impostazione predefinita. I team di adozione del cloud e i proprietari dei carichi di lavoro dovranno valutare se applicare la crittografia per il traffico che intercorre tra risorse IaaS ospitate all'interno delle reti virtuali.

**Presupposti relativi alla crittografia dei dati in transito:** L'implementazione dei criteri di crittografia corretti per i dati in transito presuppone le condizioni seguenti:

- Tutti gli endpoint accessibili pubblicamente nell'ambiente cloud comunicheranno con la rete Internet pubblica tramite i protocolli SSL/TLS.
- Per stabilire la connessione tra una rete cloud e la rete locale o un'altra rete esterna attraverso la rete Internet pubblica, si usano i protocolli VPN crittografati.
- Per stabilire la connessione tra una rete cloud e la rete locale o un'altra rete esterna attraverso una connessione WAN dedicata come ExpressRoute, si userà una VPN o un'altra appliance di crittografia locale associata a una VPN o un'altra appliance di crittografia virtuale corrispondente distribuita nella rete cloud.
- In presenza di dati sensibili che non devono essere inclusi nei log sul traffico o in altri report di diagnostica visibili al personale IT, si crittograferà tutto il traffico tra le risorse nella rete virtuale.

### <a name="data-at-rest"></a>Dati inattivi

I dati inattivi sono i dati che non vengono spostati o elaborati attivamente e includono file, database, unità di macchine virtuali, account di archiviazione PaaS o risorse simili. La crittografia dei dati archiviati protegge i dispositivi virtuali o i file dall'accesso non autorizzato che può avvenire tramite penetrazione da una rete esterna, rilasci accidentali o utenti interni malintenzionati.

Per le risorse di database e archiviazione PaaS generalmente la crittografia è applicata per impostazione predefinita. È possibile proteggere le risorse IaaS crittografando i dati a livello di disco virtuale o crittografando l'intero account di archiviazione che ospita le unità virtuali. Tutti questi asset possono usare chiavi gestite da Microsoft o gestite dal cliente archiviate in Azure Key Vault.

La crittografia dei dati inattivi comprende anche tecniche di crittografia dei database più avanzate, come la crittografia a livello di colonna e di riga, che offre un controllo notevolmente superiore sui dati esatti da proteggere.

I criteri e i requisiti di conformità complessivi, il livello di riservatezza dei dati archiviati e i requisiti di prestazioni dei carichi di lavoro dovrebbero determinare quali risorse debbano essere crittografate.

### <a name="assumptions-about-encrypting-data-at-rest"></a>Presupposti relativi alla crittografia dei dati inattivi

La crittografia dei dati inattivi presuppone le condizioni seguenti:

- Si archiviano i dati che non sono destinati all'utilizzo pubblico.
- I carichi di lavoro possono accettare i costi di latenza aggiuntivi per la crittografia dei dischi.

### <a name="data-in-use"></a>Dati in uso

La crittografia dei dati in uso implica la protezione dei dati in una risorsa di archiviazione non permanente, come la RAM o la cache della CPU, oltre all'uso di tecnologie come la crittografia della memoria completa o di tecnologie enclave come Secure Guard Extensions (SGX) di Intel. Sono incluse anche tecniche di crittografia come la crittografia omomorfica, che può essere usata per creare ambienti di esecuzione sicuri e affidabili.

**Presupposti relativi alla crittografia dei dati in uso:** La crittografia dei dati in uso presuppone le condizioni seguenti:

- La proprietà dei dati deve essere sempre mantenuta separata dalla piattaforma cloud sottostante, anche a livello di RAM e CPU.

## <a name="learn-more"></a>Altre informazioni

Per altre informazioni sulla crittografia e sulla gestione delle chiavi in Azure, vedere:

- [Panoramica della crittografia di Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview). Descrizione dettagliata del modo in cui Azure usa la crittografia per proteggere i dati inattivi e i dati in transito.
- [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-overview). Key Vault è il principale sistema di gestione delle chiavi per l'archiviazione e la gestione di chiavi, segreti e certificati di crittografia in Azure.
- [Procedure consigliate per la sicurezza dei dati e la crittografia in Azure](https://docs.microsoft.com/azure/security/azure-security-data-encryption-best-practices). Presentazione delle procedure consigliate per la sicurezza dei dati e la crittografia in Azure.
- [Confidential computing in Azure](https://azure.microsoft.com/solutions/confidential-compute). L'iniziativa Confidential computing di Azure offre strumenti e tecnologie per creare ambienti di esecuzione affidabili o altri meccanismi di crittografia per la protezione dei dati in uso.

## <a name="next-steps"></a>Passaggi successivi

La crittografia è solo uno dei componenti principali dell'infrastruttura che richiedono decisioni a livello di architettura durante un processo di adozione del cloud. Vedere la [panoramica sulle guide alle decisioni](../index.md) per informazioni sui modelli alternativi o i modelli usati per prendere decisioni di progettazione per altri tipi di infrastruttura.

> [!div class="nextstepaction"]
> [Guide alle decisioni per l'architettura](../index.md)
