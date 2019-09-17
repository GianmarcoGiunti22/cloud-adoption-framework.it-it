---
title: Guida all'idoneità del CISO per il cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Come può un CISO prepararsi per il cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/03/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 935012e6b2de78e4698a7d484da25cf888d00071
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029801"
---
# <a name="ciso-cloud-readiness-guide"></a>Guida all'idoneità del CISO per il cloud

Microsoft Guidance come il Framework di adozione del cloud non è posizionato in modo da determinare o guidare i vincoli di sicurezza univoci delle migliaia di aziende supportate da questa documentazione. Quando si passa al cloud, il ruolo di Chief Information Security Officer o Chief Information Security Office (CISO) non viene soppiantato dalle tecnologie cloud. Al contrario, il CISO e il relativo reparto diventano più integrati. Questa guida presuppone che il lettore abbia familiarità con i processi CISO e stia cercando di modernizzare tali processi per abilitare la trasformazione cloud.

L'adozione del cloud assicura servizi che non vengono presi spesso in considerazione negli ambienti IT tradizionali. Le distribuzioni self-service o automatizzate vengono in genere eseguite dallo sviluppo di applicazioni o da altri team IT non allineati tradizionalmente alla distribuzione di produzione. In alcune organizzazioni i componenti aziendali dispongono in modo analogo di funzionalità self-service. Ciò può comportare nuovi requisiti di sicurezza che non erano richiesti in precedenza nell'ambiente locale. La sicurezza centralizzata è più complessa e la protezione diventa spesso una responsabilità condivisa tra l'azienda e la cultura IT. Questo articolo può aiutare un CISO a prepararsi per tale approccio e ad avvicinarsi alla governance incrementale.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-a-ciso-prepare-for-the-cloud"></a>Come può un CISO prepararsi per il cloud?

Come la maggior parte dei criteri, i criteri di sicurezza e governance all'interno di un'organizzazione tendono a crescere in modo organico. Quando si verificano problemi di sicurezza, vengono plasmati nuovi criteri per informare gli utenti e ridurre la probabilità che si ripetano. Per quanto naturale, questo approccio comporta un aumento spropositato dei criteri oltre a dipendenze tecniche. I percorsi di trasformazione cloud creano un'opportunità univoca di modernizzare e reimpostare i criteri. Mentre si prepara per un qualsiasi percorso di trasformazione, il CISO può realizzare un valore immediato e significativo fungendo da stakeholder principale nell'ambito di una [revisione dei criteri](./cloud-policy-review.md).

In questo tipo di revisione il ruolo del CISO è quello di creare un equilibrio sicuro tra i vincoli dei criteri/requisiti di conformità esistenti e il comportamento di sicurezza migliorato dei provider di servizi cloud. La valutazione di questi progressi può assumere molte forme; spesso vengono misurati in base al numero di criteri di sicurezza che possono essere trasferiti in modo sicuro al provider di servizi cloud.

**Trasferimento dei rischi per la sicurezza:** man mano che i servizi vengono spostati in modelli di hosting dell'infrastruttura distribuita come servizio (IaaS), l'azienda si assume meno rischi diretti riguardanti il provisioning dell'hardware. I rischi non vengono meno, ma sono trasferiti al fornitore di servizi cloud. Se l'approccio di un fornitore di cloud al provisioning dell'hardware offre lo stesso livello di mitigazione dei rischi, in un processo ripetibile sicuro, il rischio di esecuzione del provisioning dell'hardware viene rimosso dall'area di responsabilità aziendale e trasferito al cloud provider. In questo modo si riduce il rischio di sicurezza globale aziendale che è responsabile della gestione di, anche se il rischio stesso deve essere ancora rilevato e rivisto periodicamente.

Poiché le soluzioni si spostano ulteriormente nello stack per incorporare i modelli PaaS (Platform as a Service, piattaforma distribuita come servizio) o Software as a Service (SaaS), è possibile evitare o trasferire rischi aggiuntivi. Quando il rischio viene trasferito in modo sicuro a un provider di servizi cloud, anche il costo di esecuzione, monitoraggio e applicazione dei criteri di sicurezza o di altri criteri di conformità può essere ridotto in modo sicuro.

**Mentalità di crescita:** La modifica può essere spaventosa per gli implementatori aziendali e tecnici. Quando il CISO introduce un cambiamento di mentalità orientata alla crescita in un'organizzazione, a questi timori naturali si sostituisce un interesse sempre maggiore per la sicurezza e la conformità ai criteri. Avvicinarsi a una [revisione di criteri](./cloud-policy-review.md), un percorso di trasformazione o semplici revisioni di implementazione con una mentalità di crescita, consente al team di spostarsi rapidamente, ma non a scapito di un profilo di rischio equo e gestibile.

## <a name="resources-for-the-chief-information-security-officer"></a>Risorse per il Chief Information Security Officer

La conoscenza del cloud è fondamentale per l'approccio a una [revisione dei criteri](./cloud-policy-review.md) con una mentalità orientata alla crescita. Le risorse seguenti possono aiutare il CISO a comprendere meglio il comportamento di sicurezza della piattaforma Microsoft Azure.

Risorse della piattaforma di sicurezza:

- [Ciclo di vita dello sviluppo della sicurezza, controlli interni](https://www.microsoft.com/sdl)
- [Formazione sulla sicurezza obbligatoria, controlli in background](https://downloads.cloudsecurityalliance.org/star/self-assessment/StandardResponsetoRequestforInformationWindowsAzureSecurityPrivacy.docx)
- [Test di penetrazione, rilevamento delle intrusioni, DDoS, controlli e registrazione](https://www.microsoft.com/trustcenter/Security/AuditingAndLogging)
- [Data center all'avanguardia](https://www.microsoft.com/cloud-platform/global-datacenters), sicurezza fisica, [rete protetta](https://docs.microsoft.com/azure/security/security-network-overview)
- [Microsoft Azure Security Response in the Cloud (PDF)](https://aka.ms/SecurityResponsePaper) (Risposta della sicurezza di Microsoft Azure nel cloud)

Privacy e controlli:

- [Gestione costante dei propri dati](https://www.microsoft.com/trustcenter/Privacy/You-own-your-data)
- [Controllo sulla posizione dei dati](https://www.microsoft.com/trustcenter/Privacy/Where-your-data-is-located)
- [Accesso ai dati in base ai propri termini](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Risposta alle richieste delle forze dell'ordine](https://www.microsoft.com/trustcenter/Privacy/Responding-to-govt-agency-requests-for-customer-data)
- [Standard di privacy rigorosi](https://www.microsoft.com/TrustCenter/Privacy/We-set-and-adhere-to-stringent-standards)

Conformità:

- [Centro protezione Microsoft](https://www.microsoft.com/trustcenter/default.aspx)
- [Hub controlli comuni](https://www.microsoft.com/trustcenter/Common-Controls-Hub)
- [Elenco di controllo dei servizi cloud per diligenza](https://www.microsoft.com/trustcenter/Compliance/Due-Diligence-Checklist)
- [Conformità in base al servizio, alla località e al settore](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

Trasparenza:

- [Come vengono protetti da Microsoft i dati dei clienti nei servizi di Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Come viene gestita da Microsoft la posizione dei dati nei servizi di Azure](https://azuredatacentermap.azurewebsites.net)
- [Personale Microsoft che ha accesso ai dati e in quali termini](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Come vengono protetti da Microsoft i dati dei clienti nei servizi di Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Certificazione di verifica per i servizi di Azure, hub per la trasparenza](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

## <a name="next-steps"></a>Passaggi successivi

Il primo passo per mettere in atto una strategia di governance è una [revisione dei criteri](./cloud-policy-review.md). I [criteri e la conformità](./index.md) possono essere una guida utile durante la revisione dei criteri.

> [!div class="nextstepaction"]
> [Prepararsi alla revisione dei criteri](./cloud-policy-review.md)
