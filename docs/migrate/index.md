---
title: Migrazione al cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migrazione al cloud in Cloud Adoption Framework
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: migrate
layout: LandingPage
ms.openlocfilehash: c112c1d340de944502ac16159977ffa12b5b095d
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378270"
---
# <a name="cloud-migration-in-the-cloud-adoption-framework"></a>Migrazione al cloud in Cloud Adoption Framework

Qualsiasi [piano di adozione del cloud](../plan/index.md) a livello aziendale includerà carichi di lavoro che non implicano investimenti significativi per la creazione della nuova logica di business. Per il trasferimento di questi carichi di lavoro è possibile adottare diversi approcci, ovvero lift-and-shift, lift-and-optimize oppure modernizzazione, ognuno dei quali è considerato una migrazione. Gli esercizi seguenti consentiranno di definire i processi iterativi per valutare, ottimizzare, proteggere e gestire i carichi di lavoro, nonché eseguirne la migrazione.

## <a name="getting-started"></a>Introduzione

Per la preparazione a questa fase del ciclo di vita di adozione del cloud, il framework suggerisce i cinque esercizi seguenti:

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/prerequisites.md?tabs=Checklist">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Prerequisito per la migrazione</h3>
Verificare che un'area di destinazione sia stata distribuita e sia pronta a ospitare i primi carichi di lavoro di cui verrà eseguita la migrazione ad Azure. Se non sono stati creati una strategia e un piano di adozione del cloud, verificare che entrambe le attività siano in corso.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Eseguire la migrazione del primo carico di lavoro</h3>
Usare la Guida alla migrazione ad Azure per completare la migrazione del primo carico di lavoro. In questo modo si acquisirà familiarità con gli strumenti e gli approcci necessari per adeguare le attività previste per l'adozione.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./expanded-scope/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Scenari di migrazione espansi</h3>
Usare l'elenco di controllo per la definizione dell'ambito di espansione per identificare gli scenari per i quali sarà necessario apportare modifiche all'architettura ufficiale futura, ai processi di migrazione, alle configurazioni delle aree di destinazione o alle decisioni relative agli strumenti per la migrazione.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-best-practices/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Procedure consigliate</h3>
Convalidare le modifiche in base alle sezione delle procedure consigliate per garantire una corretta implementazione dell'ambito di espansione o di approcci di migrazione specifici del carico di lavoro e/o dell'architettura.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./migration-considerations/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/5.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Miglioramenti dei processi</h3>
La migrazione è un'attività che implica un notevole carico dal punto di vista dei processi. In caso di ridimensionamento delle attività di migrazione, consultare la sezione relativa alle considerazioni sulla migrazione per valutare e perfezionare vari aspetti dei processi.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="iterative-migration-process"></a>Processo di migrazione iterativo

In sostanza, la migrazione al cloud si articola in quattro semplici fasi: valutazione, migrazione, ottimizzazione e sicurezza e gestione. Questa sezione di Cloud Adoption Framework spiega come massimizzare il valore restituito da ogni fase del processo e allineare tali fasi al piano di adozione del cloud. L'immagine seguente illustra queste fasi in un approccio iterativo:

![Modello di migrazione di Cloud Adoption Framework](../_images/operational-transformation-migrate.png)

## <a name="creating-a-balanced-cloud-portfolio"></a>Creazione di un portfolio cloud bilanciato

Qualsiasi portfolio tecnologico bilanciato include una combinazione mista di asset in vari stati. Alcune applicazioni sono pianificate per il ritiro e hanno un supporto minimo. Altre applicazioni o altri asset sono supportati in uno stato di manutenzione, ma le funzionalità di tali soluzioni sono stabili. Per i processi aziendali più recenti, è probabile che le condizioni di mercato in evoluzione promuovano interventi continuativi di miglioramento delle funzionalità o modernizzazione. Quando emergono opportunità per promuovere nuovi flussi di ricavi, nell'ambiente vengono introdotti nuove applicazioni o nuovi asset. In ogni fase del ciclo di vita di un asset, l'impatto di qualsiasi investimento su ricavi e profitti sarà variabile. Man mano che si avanza nel ciclo di vita diminuiscono le probabilità che una nuova funzionalità o un nuovo progetto di modernizzazione produca un ritorno sugli investimenti interessante.

Il cloud offre vari meccanismi di adozione, ognuno con livelli simili di investimento e rendimento. La creazione di applicazioni native del cloud può ridurre notevolmente le spese operative. Dopo il rilascio di un'applicazione nativa del cloud, lo sviluppo di nuove funzionalità e soluzioni può essere gestito con iterazioni più veloci. La modernizzazione di un'applicazione può offrire vantaggi simili grazie alla rimozione dei vincoli tradizionali associati ai modelli di sviluppo locale. Sfortunatamente, questi due approcci richiedono molta manodopera e dipendono da dimensioni, competenze ed esperienza del team di sviluppo software. Spesso, la manodopera disponibile non è allineata, ovvero i professionisti con le competenze e il talento adeguati per modernizzare le applicazioni preferiscono creare nuove applicazioni. In un mercato che dipende dalla manodopera, i progetti di modernizzazione su larga scala possono essere inficiati da problemi di soddisfazione e uso del talento dei dipendenti. In un portfolio bilanciato, questo approccio deve essere riservato alle applicazioni che potrebbero ottenere miglioramenti delle funzionalità significativi se rimanessero in locale.

## <a name="envision-an-end-state"></a>Prevedere uno stato finale

Qualsiasi viaggio deve avere una destinazione. Occorre avere una visione approssimativa dello stato finale prima di partire. Questa infografica illustra un punto di partenza costituito dalle applicazioni, i dati e l'infrastruttura esistenti, che definiscono il digital estate. Durante il processo di migrazione, ogni asset viene trasferito tramite una delle opzioni sulla destra.

## <a name="migration-implementation"></a>Implementazione della migrazione

Questi articoli descrivono due percorsi, ognuno con un obiettivo simile, ovvero la migrazione di un'alta percentuale degli asset esistenti in Azure. Tuttavia, i risultati aziendali e lo stato corrente influiranno in modo significativo sui processi necessari per raggiungere la destinazione. Queste leggere deviazioni danno vita a due approcci radicalmente diversi per raggiungere uno stato finale simile.

![Modello di migrazione di Cloud Adoption Framework](../_images/operational-transformation-migrate.png)

Per guidare l'esecuzione incrementale durante la transizione verso lo stato finale, questo modello separa la migrazione in due aree di interesse.

**Preparazione alla migrazione:** stabilire un backlog di migrazione approssimativo basato in larga misura sullo stato corrente e i risultati desiderati.

- **Risultati aziendali:** i principali obiettivi aziendali della migrazione.
- **Stima del digital estate:** una stima approssimativa del numero e delle condizioni dei carichi di lavoro di cui deve essere eseguita la migrazione.
- **Ruoli e responsabilità:** una definizione chiara di struttura del team, separazione delle responsabilità e requisiti di accesso.
- **Requisiti di gestione delle modifiche:** la tempistica, i processi e la documentazione necessari per verificare e approvare le modifiche.

Questi dati di input iniziali danno forma al backlog di migrazione. L'output del backlog di migrazione è un elenco in ordine di priorità delle applicazioni di cui eseguire la migrazione al cloud. Tale elenco definisce l'esecuzione del processo di migrazione al cloud. Nel corso del tempo si estenderà fino a includere gran parte della documentazione necessaria per gestire le modifiche.

**Processo di migrazione:** ogni attività di migrazione al cloud è inclusa in uno dei processi seguenti, in relazione al backlog di migrazione.

- **Valutazione:** valutare un asset esistente e definire un piano per la migrazione dell'asset.
- **Migrazione:** replicare le funzionalità di un asset nel cloud.
- **Ottimizzazione:** bilanciare prestazioni, costi, accesso e capacità operativa di un asset cloud.
- **Protezione e gestione:** assicurarsi che un asset cloud sia pronto per le attività operative continuative.

Le informazioni raccolte durante lo sviluppo di un backlog di migrazione determinano la complessità e il livello di impegno necessario all'interno del processo di migrazione al cloud durante ogni iterazione e per ogni versione della funzionalità.

## <a name="transition-to-the-end-state"></a>Transizione verso lo stato finale

L'obiettivo è una migrazione senza problemi e in parte automatizzata al cloud. Il processo di migrazione usa gli strumenti forniti da un fornitore di cloud per gestire velocemente la replica e la gestione temporanea degli asset nel cloud. Al termine della verifica, una semplice modifica della rete reindirizza gli utenti alla soluzione cloud. Per molti casi d'uso, la tecnologia per raggiungere questo obiettivo è ampiamente disponibile. Esistono casi di esempio che dimostrano la velocità con cui è possibile replicare 10.000 macchine virtuali in Azure.

È comunque necessario un approccio alla migrazione incrementale. Nella maggior parte degli ambienti, il lungo elenco di macchine virtuali da sottoporre a migrazione deve essere suddiviso in unità di lavoro più piccole perché una migrazione abbia esito positivo. Esistono molti fattori che limitano il numero di macchine virtuali di cui è possibile eseguire la migrazione in un determinato periodo. La velocità di rete in uscita è uno dei pochi limiti tecnici. La maggior parte dei limiti è correlato alla capacità dell'azienda di convalidare le modifiche richieste e adattarsi ai cambiamenti.

L'approccio di migrazione incrementale di Cloud Adoption Framework consente di creare un piano incrementale che rispecchia e documenta le limitazioni tecniche e culturali. L'obiettivo di questo modello è ottimizzare la velocità di migrazione riducendo al tempo stesso al minimo il sovraccarico sia per il team IT che per l'azienda. Di seguito sono riportati due esempi di esecuzione di una migrazione incrementale basata sul backlog di migrazione.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./azure-migration-guide/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida alla migrazione ad Azure</h3>
                        <p><b>Riepilogo descrittivo:</b> questo cliente sta eseguendo la migrazione di meno di 1.000 macchine virtuali. Meno di dieci applicazioni supportate sono di proprietà di un utente non incluso nell'organizzazione IT. Le applicazioni rimanenti, le macchine virtuali e i dati associati sono di proprietà e supportati dai membri del team di adozione del cloud. I membri del team di adozione del cloud hanno accesso amministrativo agli ambienti di produzione nel data center esistente.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./expanded-scope/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guida a uno scenario complesso</h3>
                        <p><b>Riepilogo descrittivo:</b> la migrazione di questo cliente presenta aspetti complessi a livello di azienda, cultura e tecnologia. Questa guida include più problematiche specifiche per tali complessità e i modi per affrontarle.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

Questi due percorsi rappresentano i due estremi dell'esperienza per i clienti che investono nella migrazione al cloud. Per la maggior parte delle aziende sarà applicabile una combinazione dei due scenari precedenti. Dopo aver esaminato i percorsi, usare il modello di migrazione di Cloud Adoption Framework per avviare la conversazione sulla migrazione e modificare i percorsi delle baseline per adattarli al meglio alle esigenze specifiche.

## <a name="next-steps"></a>Passaggi successivi

Scegliere uno di questi percorsi:

> [!div class="nextstepaction"]
> [Guida alla migrazione ad Azure](./azure-migration-guide/index.md)
>
> [Guida per l'ambito esteso](./expanded-scope/index.md)
