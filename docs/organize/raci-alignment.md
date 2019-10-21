---
title: Allineamento delle responsabilità tra i team
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scopri come allineare le responsabilità tra i team.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 40ccd0c17a55a87c84d40abd749bf8e61f891e6c
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549085"
---
# <a name="align-responsibilities-across-teams"></a>Allinea le responsabilità tra i team

Scopri come allineare le responsabilità tra i team sviluppando una matrice tra team che identifichi *le parti responsabili, contabili, consultate e informate* (RACI). Questo articolo fornisce un esempio di matrice RACI per le strutture organizzative descritte in [definire le strutture del team](./organization-structures.md):

- [Solo team di adozione cloud](#cloud-adoption-team-only)
- [Procedura consigliata per MVP](#best-practice-minimum-viable-product-mvp)
- [IT centrale](#central-it)
- [Allineamento strategico](#strategic-alignment)
- [Allineamento operativo](#operational-alignment)
- [Centro cloud di eccellenza (CCoE)](#cloud-center-of-excellence-ccoe)

Per tenere traccia delle decisioni relative alla struttura organizzativa nel tempo, scaricare e modificare il [modello del foglio di calcolo Raci](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx).

Gli esempi in questo articolo specificano questi costrutti RACI:

- Un team che è *responsabile* per una funzione.
- I team *responsabili* dei risultati.
- I team che devono essere *consultati* durante la pianificazione.
- I team che devono essere *informati* quando il lavoro viene completato.

L'ultima riga di ogni tabella, ad eccezione della prima, contiene un collegamento alla funzionalità cloud più allineata per ulteriori informazioni.

## <a name="cloud-adoption-team-only"></a>Solo team di adozione cloud

|  |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di adozione del cloud |Responsabili|Responsabili|Responsabili|Responsabili|Responsabili|Responsabili|Responsabili|Responsabili|

## <a name="best-practice-minimum-viable-product-mvp"></a>Procedura consigliata: prodotto minimo valido (MVP)

|  |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di adozione del cloud|Responsabili|Responsabili|Responsabili|Responsabili|Consultato|Consultato|Consultato|Informate|
|Team di governance del cloud|Consultato|Informate|Informate|Informate|Responsabili|Responsabili|Responsabili|Responsabili|
||||||||||
|Funzionalità cloud allineata|[Adozione del cloud](./cloud-adoption.md)|[Strategia cloud](./cloud-strategy.md)|[Strategia cloud](./cloud-strategy.md)|[Operazioni cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[automazione del cloud](./cloud-automation.md)|

## <a name="central-it"></a>IT centrale

| |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di adozione del cloud  |Responsabili|Responsabili|Responsabile    |Responsabile|Informate   |Informate   |Informate   |Informate   |
|Team di governance del cloud|Consultato  |Informate   |Informate   |Informate   |Responsabili|Consultato  |Responsabile|Informate   |
|IT centrale           |Consultato  |Informate   |Responsabili   |Responsabili   |Responsabile  |Responsabili|Responsabili|Responsabili|
||||||||||
|Funzionalità cloud allineata|[Adozione del cloud](./cloud-adoption.md)|[Strategia cloud](./cloud-strategy.md)|[Strategia cloud](./cloud-strategy.md)|[Operazioni cloud](./cloud-operations.md)|[Governance cloud](./cloud-governance.md)|[IT centrale](./central-it.md)|[IT centrale](./central-it.md)|[IT centrale](./central-it.md)|

## <a name="strategic-alignment"></a>Allineamento strategico

|  |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di strategia cloud  |Consultato  |Responsabili|Responsabili|Consultato  |Consultato  |Informate   |Informate   |Informate   |
|Team di adozione del cloud  |Responsabili|Consultato  |Responsabile|Responsabili|Informate   |Informate   |Informate   |Informate   |
|Modello CCoE RACI      |Consultato  |Informate   |Informate   |Informate   |Responsabili|Responsabili|Responsabili|Responsabili|
||||||||||
|Funzionalità cloud allineata|[Adozione del cloud](./cloud-adoption.md)|[Strategia cloud](./cloud-strategy.md)|[Strategia cloud](./cloud-strategy.md)|[Operazioni cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[automazione del cloud](./cloud-automation.md)|

## <a name="operational-alignment"></a>Allineamento operativo

|  |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di strategia cloud  |Consultato  |Responsabili|Responsabili|Consultato  |Consultato  |Informate   |Informate   |Informate   |
|Team di adozione del cloud  |Responsabili|Consultato  |Responsabile|Consultato  |Informate   |Informate   |Informate   |Informate   |
|Team operativo cloud|Consultato  |Consultato  |Responsabile|Responsabili|Consultato  |Informate   |Responsabili|Consultato  |
|Modello CCoE RACI      |Consultato  |Informate   |Informate   |Informate   |Responsabili|Responsabili|Responsabile|Responsabili|
||||||||||
|Funzionalità cloud allineata|[Adozione del cloud](./cloud-adoption.md)|[Strategia cloud](./cloud-strategy.md)|[Strategia cloud](./cloud-strategy.md)|[Operazioni cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[automazione del cloud](./cloud-automation.md)|

## <a name="cloud-center-of-excellence-ccoe"></a>Centro cloud di eccellenza (CCoE)

|  |Recapito della soluzione  |Allineamento aziendale  |Gestione delle modifiche  |Operazioni della soluzione  |Governance |Maturità della piattaforma  |Operazioni della piattaforma  |Automazione della piattaforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Team di strategia cloud  |Consultato  |Responsabili|Responsabili|Consultato  |Consultato  |Informate   |Informate   |Informate   |
|Team di adozione del cloud  |Responsabili|Consultato  |Responsabile|Consultato  |Informate   |Informate   |Informate   |Informate   |
|Team operativo cloud|Consultato  |Consultato  |Responsabile|Responsabili|Consultato  |Informate   |Responsabili|Consultato  |
|Team di governance del cloud|Consultato  |Informate   |Informate   |Consultato  |Responsabili|Consultato  |Responsabile|Informate   |
|Team della piattaforma cloud  |Consultato  |Informate   |Informate   |Consultato  |Consultato  |Responsabili|Responsabile|Responsabile|
|Team di automazione del cloud|Consultato  |Informate   |Informate   |Informate   |Consultato  |Responsabile|Responsabile|Responsabili|
||||||||||
|Funzionalità cloud allineata|[Adozione del cloud](./cloud-adoption.md)|[Strategia cloud](./cloud-strategy.md)|[Strategia cloud](./cloud-strategy.md)|[Operazioni cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[piattaforma cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md) -[automazione del cloud](./cloud-automation.md)|

## <a name="next-steps"></a>Passaggi successivi

Per tenere traccia delle decisioni sulla struttura dell'organizzazione nel tempo, scaricare e modificare il [modello del foglio di calcolo Raci](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx). Copiare e modificare il campione più allineato dalle matrici RACI in questo articolo.

> [!div class="nextstepaction"]
> [Scaricare il modello del foglio di calcolo relativo alle assegnazioni delle responsabilità](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx)
