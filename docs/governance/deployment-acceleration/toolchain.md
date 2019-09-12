---
title: Strumenti di Accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti di Accelerazione della distribuzione
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 62058d6a7d8d05b046e29a03650ca0f095a3789d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828968"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Strumenti di Accelerazione della distribuzione

[Accelerazione della distribuzione](index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina è incentrata sulle modalità di definizione dei criteri per definire la configurazione o la distribuzione di risorse. All'interno delle cinque discipline della governance del cloud, la disciplina di accelerazione della distribuzione prevede l'allineamento della distribuzione e della configurazione. tramite attività manuali o tramite attività DevOps completamente automatizzate. In entrambi i casi, i criteri che interessano rimarranno in gran parte uguali.

È molto probabile che responsabili, sorveglianti e progettisti del cloud con un interesse per la governance, investano molto tempo nella disciplina di Accelerazione della distribuzione, che consente di codificare criteri e requisiti tra le attività di adozione di più cloud. Gli strumenti di questa attrezzatura sono importanti per il team di governance del cloud e devono avere una priorità alta sul percorso di apprendimento per il team.

Di seguito è riportato un elenco di strumenti di Azure che possono consentire di sviluppare i criteri e i processi che supportano la disciplina di governance.

|  | [Criteri di Azure](/azure/governance/policy/overview) | [Gruppi di gestione di Azure](/azure/governance/management-groups) | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) | [Azure Blueprint](/azure/governance/blueprints/overview) | [Grafico delle risorse di Azure](/azure/governance/resource-graph/overview) | [Gestione costi di Azure](/azure/cost-management) |
|---------|---------|---------|---------|---------|---------|---------|
|Implementare i criteri aziendali     |Sì |No  |No  |No | No |No |
|Applicare criteri tra sottoscrizioni     |Obbligatoria |Sì  |No  |No | No |No |
|Distribuire le risorse definite     |No |No  |Sì  |No | No |No |
|Creare ambienti completamente conformi      |Obbligatoria |Obbligatoria  |Obbligatoria  |Sì | No |No |
|Criteri di controllo      |Sì |No  |No  |No | No |No |
|Eseguire query sulle risorse di Azure      |No |No  |No  |No |Sì |No |
|Report sui costi delle risorse      |No |No  |No  |No |No |Sì |

Gli strumenti aggiuntivi seguenti potrebbero essere necessari per realizzare obiettivi specifici di Accelerazione della distribuzione. Spesso questi strumenti vengono usati al di fuori del team di governance, ma sono comunque considerati un aspetto della disciplina di Accelerazione della distribuzione.

|  | [Portale di Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)  | [Criteri di Azure](/azure/governance/policy/overview) | [Azure DevOps](/azure/devops/index) | [Backup di Azure](/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|
|Distribuzione manuale (asset singolo)     | Sì | Sì  | No  | Non efficiente | No | Yes |
|Distribuzione manuale (ambiente completo)     | Non efficiente | Sì | No  | Non efficiente | No | Sì |
|Distribuzione automatizzata (ambiente completo)     | No  | Sì  | No  | Sì  | No | Sì |
|Aggiornare configurazione di un asset singolo     | Sì | Yes | Non efficiente | Non efficiente | No | Sì: durante la replica |
|Aggiornare la configurazione di un ambiente completo     | Non efficiente | Sì | Sì | Sì  | No | Sì: durante la replica |
|Gestire una deviazione di configurazione     | Non efficiente | Non efficiente | Sì  | Sì  | No | Sì: durante la replica |
|Creare una pipeline automatizzata per distribuire il codice e configurare gli asset (DevOps)     | No | No | No | Sì | No | No |

A parte gli strumenti Azure nativi indicati in precedenza, è comune per i clienti usare gli strumenti di terze parti per semplificare le distribuzioni di Accelerazione della distribuzione e DevOps.
