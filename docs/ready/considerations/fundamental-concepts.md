---
title: Concetti fondamentali di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sui termini e i concetti fondamentali usati in Azure e su come sono correlati.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 47148153d63137e6281b37bcb2be28e63bc6586c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025162"
---
# <a name="azure-fundamental-concepts"></a>Concetti fondamentali di Azure

Vengono fornite informazioni sui termini e i concetti fondamentali usati in Azure e su come sono correlati.

## <a name="azure-terminology"></a>Terminologia di Azure

È utile conoscere le definizioni seguenti quando si inizia il lavoro di adozione del cloud di Azure:

- **Resource** (Risorsa): entità gestita da Azure, ad esempio macchine virtuali, reti virtuali e account di archiviazione di Azure.
- **Sottoscrizione** Contenitore logico per le risorse. Ogni risorsa di Azure è associata a una sola sottoscrizione. La creazione di una sottoscrizione è il primo passaggio per l'adozione di Azure.
- **Account Azure**: l'indirizzo di posta elettronica fornito quando si crea una sottoscrizione di Azure è l'account Azure per la sottoscrizione. L'entità associata all'account di posta elettronica è responsabile dei costi mensili sostenuti dalle risorse nella sottoscrizione. Quando si crea un account Azure, si forniscono le informazioni di contatto e i dettagli di fatturazione, ad esempio una carta di credito. È possibile usare lo stesso account Azure (indirizzo di posta elettronica) per più sottoscrizioni. Ogni sottoscrizione è associata a un solo account Azure.
- **Amministratore account**: entità associata all'indirizzo di posta elettronica usato per creare una sottoscrizione di Azure. L'amministratore account è responsabile del pagamento di tutti i costi sostenuti dalle risorse della sottoscrizione.
- **Azure Active Directory** (Azure AD): servizio Microsoft basato sul cloud per la gestione delle identità e degli accessi. Azure AD consente ai dipendenti di accedere alle risorse.
- **Tenant di Azure AD**: istanza dedicata e attendibile di Azure AD. Un tenant di Azure AD viene creato automaticamente quando un'organizzazione effettua per la prima volta l'iscrizione per una sottoscrizione di un servizio cloud Microsoft, ad esempio Microsoft Azure, Microsoft Intune oppure Office 365. Un tenant di Azure rappresenta una singola organizzazione.
- **Directory di Azure AD**: ogni tenant di Azure AD ha una singola directory dedicata e attendibile. La directory include gli utenti, i gruppi e le app del tenant. Viene usata per eseguire le funzioni di gestione di identità e accessi per le risorse del tenant. Una directory può essere associata a più sottoscrizioni, ma ogni sottoscrizione è associata a una sola directory.
- **Gruppi di risorse**: contenitori logici usati per raggruppare le risorse correlate in una sottoscrizione. Ogni risorsa può appartenere a un solo gruppo di risorse.
- **Gruppi di gestione**: contenitori logici usati per una o più sottoscrizioni. È possibile definire una gerarchia di gruppi di gestione, sottoscrizioni, gruppi di risorse e risorse per gestire in modo efficiente l'accesso, i criteri e la conformità tramite l'ereditarietà.
- **Area**: set di data center di Azure distribuiti all'interno di un perimetro definito dalla latenza. I data center sono connessi tramite una rete a livello di area, dedicata e a bassa latenza. La maggior parte delle risorse di Azure viene eseguita in un'area di Azure specifica.

## <a name="azure-subscription-purposes"></a>Scopi di una sottoscrizione di Azure

Una sottoscrizione di Azure ha diversi scopi, come descritto di seguito:

- **Contratto legale**. Ogni sottoscrizione è associata a un'[offerta di Azure](https://azure.microsoft.com/support/legal/offer-details), ad esempio una versione di valutazione gratuita o con pagamento in base al consumo. Ogni offerta ha un piano tariffario specifico, vantaggi e termini e condizioni associati. L'offerta di Azure viene scelta al momento della creazione di una sottoscrizione.
- **Contratto di pagamento**. Quando si crea una sottoscrizione, si forniscono informazioni di pagamento per tale sottoscrizione, ad esempio un numero di carta di credito. Ogni mese, i costi sostenuti dalle risorse distribuite nella sottoscrizione vengono calcolati e fatturati tramite il metodo di pagamento.
- **Limite di ridimensionamento**. Per una sottoscrizione sono definiti limiti di ridimensionamento. Le risorse della sottoscrizione non possono superare i limiti di ridimensionamento impostati. Ad esempio, esiste un limite per il numero di macchine virtuali che è possibile creare in una singola sottoscrizione.
- **Limite amministrativo**. Una sottoscrizione può fungere da limite per l'amministrazione, la sicurezza e i criteri. Azure fornisce anche altri meccanismi per soddisfare queste esigenze, ad esempio gruppi di gestione, gruppi di risorse e controllo degli accessi in base al ruolo.

## <a name="azure-subscription-considerations"></a>Considerazioni sulle sottoscrizioni di Azure

Quando si crea una sottoscrizione di Azure, sono disponibili diverse opzioni chiave relative alla sottoscrizione:

- **Chi è responsabile del pagamento della sottoscrizione?** Per impostazione predefinita, l'entità associata all'indirizzo di posta elettronica fornito quando si crea una sottoscrizione è l'amministratore account della sottoscrizione. L'entità associata a questo indirizzo di posta elettronica è responsabile del pagamento di tutti i costi sostenuti dalle risorse della sottoscrizione.
- **A quale offerta di Azure si è interessati?** Ogni sottoscrizione è associata a un'[offerta di Azure](https://azure.microsoft.com/support/legal/offer-details) specifica. È possibile scegliere l'offerta di Azure che meglio soddisfa le proprie esigenze. Se ad esempio si intende usare una sottoscrizione per eseguire carichi di lavoro non di produzione, è possibile scegliere l'offerta Sviluppo/test con pagamento in base al consumo o l'offerta Sviluppo/test Enterprise.

> [!NOTE]
> Quando si esegue l'iscrizione ad Azure, è possibile che venga visualizzata la frase *creare un account Azure*. Un account Azure viene creato quando si crea una sottoscrizione di Azure e si associa la sottoscrizione a un account di posta elettronica.

## <a name="azure-administrative-roles"></a>Ruoli amministrativi di Azure

Azure definisce tre tipi di ruoli per l'amministrazione di sottoscrizioni, identità e risorse:

- Ruoli di amministratore della sottoscrizione classica
- Ruoli di controllo degli accessi in base al ruolo di Azure
- Ruoli di amministratore di Azure Active Directory (Azure AD)

Il ruolo di amministratore account per una sottoscrizione di Azure viene assegnato all'account di posta elettronica usato per creare la sottoscrizione di Azure. L'amministratore account è il proprietario della fatturazione della sottoscrizione. Può gestire i dettagli della sottoscrizione nel [Centro account di Azure](https://account.azure.com/Subscriptions).

Per impostazione predefinita, anche il ruolo di amministratore dei servizi per una sottoscrizione viene assegnato all'account di posta elettronica usato per creare la sottoscrizione di Azure. L'amministratore dei servizi dispone di autorizzazioni per la sottoscrizione equivalenti al ruolo proprietario basato su Controllo degli accessi in base al ruolo. L'amministratore dei servizi ha accesso completo al portale di Azure. L'amministratore account può cambiare l'amministratore dei servizi con un altro account di posta elettronica.

Quando si crea una sottoscrizione di Azure, è possibile associarla a un tenant di Azure AD esistente. In caso contrario, viene creato un nuovo tenant di Azure AD con una directory associata. Il ruolo di amministratore globale nella directory di Azure AD viene assegnato all'account di posta elettronica usato per creare la sottoscrizione di Azure AD.

Un account di posta elettronica può essere associato a più sottoscrizioni di Azure. L'amministratore account può trasferire una sottoscrizione a un altro account.

Per una descrizione dettagliata dei ruoli definiti in Azure, vedere [Ruoli di amministratore della sottoscrizione classica, ruoli Controllo degli accessi in base al ruolo di Azure e ruoli di amministratore di Azure AD](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles).

## <a name="subscriptions-and-regions"></a>Sottoscrizioni e aree

Ogni risorsa di Azure è associata in modo logico a una sola sottoscrizione. Quando si crea una risorsa, si sceglie la sottoscrizione di Azure in cui distribuire la risorsa. È possibile spostare una risorsa in un'altra sottoscrizione in un secondo momento.

Una sottoscrizione non è associata a una specifica area di Azure. Tuttavia, ogni risorsa di Azure viene distribuita in una sola area. È possibile disporre di risorse in più aree associate alla stessa sottoscrizione.

> [!NOTE]
> La maggior parte delle risorse di Azure viene distribuita in un'area specifica. Tuttavia, alcuni tipi di risorse sono considerati risorse globali, ad esempio i criteri impostati usando i servizi Criteri di Azure.

## <a name="related-resources"></a>Risorse correlate

Le risorse seguenti forniscono informazioni dettagliate sui concetti illustrati in questo articolo:

- [Funzionamento di Azure](../../getting-started/what-is-azure.md)
- [Gestione dell'accesso alle risorse in Azure](../../govern/resource-consistency/resource-access-management.md)
- [Panoramica di Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)
- [Controllo degli accessi in base al ruolo per le risorse di Azure](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [Informazioni su Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)
- [Associare o aggiungere una sottoscrizione di Azure al tenant di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)
- [Topologie per Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies)
- [Sottoscrizioni, licenze, account e tenant per le offerte cloud di Microsoft](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings)

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono i concetti fondamentali di Azure, è possibile ottenere informazioni su come implementare il [ridimensionamento con più sottoscrizioni di Azure](./scaling-subscriptions.md).

> [!div class="nextstepaction"]
> [Ridimensionamento con più sottoscrizioni di Azure](./scaling-subscriptions.md)
