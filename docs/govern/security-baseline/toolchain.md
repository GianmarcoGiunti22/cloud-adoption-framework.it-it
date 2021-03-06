---
title: Strumenti per la baseline di sicurezza in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione degli strumenti che consentono di migliorare la linea di base di sicurezza in Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 7f4062c08ef1c9fec72e515453e8acc8cedfc513
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565906"
---
# <a name="security-baseline-tools-in-azure"></a>Strumenti per la baseline di sicurezza in Azure

La [baseline di sicurezza](./index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina è incentrata sulle modalità di definizione dei criteri che proteggono la rete, gli asset e, soprattutto, i dati che risiedono nella soluzione di un provider di servizi cloud. All'interno delle cinque discipline della governance del cloud, la disciplina di base della sicurezza prevede la classificazione dei dati e delle proprietà digitali. Comporta inoltre la documentazione dei rischi, della tolleranza aziendale e delle strategie di mitigazione associate alla sicurezza di dati, asset e reti. Dal punto di vista tecnico, questa disciplina include anche il coinvolgimento delle decisioni riguardanti la [crittografia](../../decision-guides/encryption/index.md), i [requisiti di rete](../../decision-guides/software-defined-network/index.md), le [strategie di identità ibride](../../decision-guides/identity/index.md)e gli strumenti per [automatizzare l'applicazione](../../decision-guides/policy-enforcement/index.md) dei criteri di sicurezza tra i [gruppi di risorse](../../decision-guides/resource-consistency/index.md).

Il seguente elenco di strumenti di Azure può aiutare a maturare i criteri e i processi che supportano la linea di base di sicurezza.

| Strumento | [Portale di Azure](https://azure.microsoft.com/features/azure-portal) e [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Insieme di credenziali delle chiavi di Azure](https://docs.microsoft.com/azure/key-vault)  | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) | [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) | [Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) |
|------------------------------------------------------------|---------------------------------|-----------------|----------|--------------|-----------------------|---------------|
| Applicazione di controlli di accesso alle risorse e alla creazione di risorse   | Sì                             | No              | Sì      | No           | No                    | No            |
| Protezione delle reti virtuali                                    | Sì                             | No              | No       | Sì          | No                    | No            |
| Crittografia delle unità virtuali                                     | No                              | Sì             | No       | No           | No                    | No            |
| Crittografia delle risorse di archiviazione e dei database PaaS                         | No                              | Sì             | No       | No           | No                    | No            |
| Gestione dei servizi di gestione delle identità ibrida                            | No                              | No              | Sì      | No           | No                    | No            |
| Limitazione dei tipi di risorsa consentiti                         | No                              | No              | No       | Sì          | No                    | No            |
| Applicazione di restrizioni a livello di area geografica                          | No                              | No              | No       | Sì          | No                    | No            |
| Monitoraggio dell'integrità della sicurezza di reti e risorse          | No                              | No              | No       | No           | Sì                   | Sì           |
| Rilevamento di attività dannose                                  | No                              | No              | No       | No           | Sì                   | Sì           |
| Rilevamento preventivo delle vulnerabilità                        | No                              | No              | No       | No           | Sì                   | No            |
| Configurazione del backup e del ripristino di emergenza                     | Sì                             | No              | No       | No           | No                    | No            |

Per un elenco completo di strumenti e servizi per la sicurezza di Azure, vedere [Servizi e tecnologie per la sicurezza disponibili in Azure](https://docs.microsoft.com/azure/security/azure-security-services-technologies).

È anche comune per i clienti usare strumenti di terze parti per facilitare le attività di base di sicurezza. Per altre informazioni, vedere l'articolo [Integrare soluzioni di sicurezza nel Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-partner-integration).

Oltre a strumenti di sicurezza, [Microsoft Trust Center](https://www.microsoft.com/trustcenter/guidance/risk-assessment) contiene ampio materiale sussidiario, report e documentazione correlata con cui è possibile eseguire valutazioni dei rischi nell'ambito del processo di pianificazione della migrazione.
