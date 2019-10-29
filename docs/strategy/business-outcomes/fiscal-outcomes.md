---
title: Esempi di esiti fiscali
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esempi di esiti fiscali
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 350b13e993d2130dc72482cbe7cafb3823b6a4d8
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048362"
---
# <a name="examples-of-fiscal-outcomes"></a>Esempi di esiti fiscali

A livello superiore, le conversazioni sui temi finanziari sono basate su tre concetti fondamentali:

- **Ricavi:** La maggior parte del denaro entrerà nell'azienda a seguito della vendita di beni o servizi.
- **Costo:** Meno denaro verrà speso per la creazione, il marketing, le vendite o il recapito di beni o servizi.
- **Profitto:** Sebbene siano rari, alcune trasformazioni possono aumentare i ricavi e ridurre i costi. Si tratta di un risultato redditizio.

Nella parte restante di questo articolo vengono illustrati questi risultati fiscali nel contesto di una trasformazione cloud.

> [!NOTE]
> Gli esempi seguenti sono ipotetici e non devono essere considerati una garanzia di restituzione quando si adotta una strategia cloud.

## <a name="revenue-outcomes"></a>Risultati in termini di ricavi

### <a name="new-revenue-streams"></a>Nuovi flussi di ricavi

Il cloud consente di creare nuove opportunità per offrire nuovi prodotti ai clienti o fornire prodotti esistenti in modo nuovo. I nuovi flussi di ricavi sono innovativi, imprenditorialità ed entusiasmanti per molte persone nel mondo del business. Anche i nuovi flussi di ricavi sono soggetti a errori e sono considerati da molte aziende a rischio elevato. Quando vengono proposti i risultati relativi ai ricavi, è probabile che si verifichi una resistenza. Per aggiungere credibilità a questi risultati, partner con un leader aziendale che è un innovativo collaudato. La convalida del flusso dei ricavi all'inizio del processo contribuisce a evitare i blocchi stradali dall'azienda.

- **Esempio:** Una società ha venduto libri per più di un centinaio di anni. Un dipendente della società si rende conto che il contenuto può essere recapitato in modo elettronico. Il dipendente crea un dispositivo che può essere venduto nella libreria, che consente di scaricare direttamente gli stessi libri, guidando $X nelle vendite di nuovi libri.

### <a name="revenue-increases"></a>Aumento dei profitti

Grazie alla scalabilità globale e alla portata digitale, il cloud può aiutare le aziende ad aumentare i ricavi da flussi di ricavi esistenti. Spesso questo tipo di risultato deriva da un allineamento con le vendite o la leadership di marketing.

- **Esempio:** Una società che vende widget potrebbe vendere un numero maggiore di widget, se i venditori potevano accedere in modo sicuro al catalogo digitale della società e ai livelli di scorte. Sfortunatamente, i dati sono solo nel sistema ERP aziendale, a cui è possibile accedere solo tramite un dispositivo connesso alla rete. La creazione di una facciata del servizio per l'interfaccia con il ERP e l'esposizione dell'elenco di cataloghi e dei livelli di scorte non sensibili a un'applicazione nel cloud consentirebbe ai venditori di accedere ai dati necessari mentre sono in sede con un cliente. Estendendo Active Directory locali utilizzando Azure Active Directory (Azure AD) e integrando l'accesso basato sui ruoli nell'applicazione, l'azienda può garantire che i dati rimangano protetti. Questo progetto semplice potrebbe influire sui ricavi di una linea di prodotti esistente per _x%_ .

### <a name="profit-increases"></a>Aumento dei profitti

Raramente una singola attività riesce simultaneamente ad aumentare i ricavi e a ridurre i costi. Tuttavia, in questo caso, allineare le istruzioni di risultato da uno o più risultati dei ricavi con uno o più risultati dei costi per comunicare il risultato desiderato.

## <a name="cost-outcomes"></a>Risultati dei costi

### <a name="cost-reduction"></a>Riduzione dei costi

Il cloud computing può ridurre le spese di capitale per l'hardware e il software, configurare i Data Center, eseguire Data Center in sede e così via. I costi per i rack di server, l'energia elettrica rotonda per l'alimentazione e il raffreddamento e gli esperti IT per la gestione dell'infrastruttura si aggiungono rapidamente. L'arresto di un Data Center può ridurre gli impegni delle spese di capitale. Questa operazione viene in genere definita "come uscire dall'azienda del Data Center". La riduzione dei costi viene in genere misurata in dollari nel budget corrente, che può estendersi da uno a cinque anni a seconda del modo in cui il CFO gestisce le finanze.

- **#1 di esempio:** Il Data Center di un'azienda usa un'alta percentuale del budget IT annuale. SI sceglie di eseguire una migrazione cloud e di passare le risorse nel data center alle soluzioni di infrastruttura distribuita come servizio (IaaS), creando una riduzione dei costi di tre anni.
- **#2 di esempio:** Una società Holding ha recentemente acquisito una nuova azienda. Nell'acquisizione, i termini stabiliscono che la nuova entità deve essere rimossa dai data center correnti entro sei mesi. La mancata esecuzione di questa operazione comporterà una multa di 1 milione USD al mese per la società in possesso. Lo spostamento delle risorse digitali nel cloud in una migrazione cloud potrebbe consentire una rimozione rapida delle risorse precedenti.
- **#3 di esempio:** Una società di imposte sui redditi che soddisfi le esperienze dei clienti del 70% dei ricavi annuali durante i primi tre mesi dell'anno. Il resto dell'anno, il suo investimento IT di grandi dimensioni si trova relativamente inattivo. Una migrazione cloud potrebbe consentire la distribuzione della capacità di calcolo/hosting necessaria per questi tre mesi. Durante i restanti nove mesi, i costi IaaS potrebbero essere significativamente ridotti riducendo il footprint di calcolo.

### <a name="example-coverdell"></a>Esempio: Coverdell

Coverdell modernizza la propria infrastruttura per ottenere risparmi sui costi dei record con Azure. La decisione di Coverdell di investire in Azure e di unire la propria rete di siti Web, applicazioni, dati e infrastruttura all'interno di questo ambiente, ha comportato una riduzione dei costi superiore a quella prevista per l'azienda. La migrazione verso un ambiente solo con Azure ha eliminato 54.000 dollari in costi mensili per i servizi di colocation. Con la nuova infrastruttura unificata dell'azienda, Coverdell prevede di risparmiare un importo stimato di 1 milione USD nei prossimi due o tre anni.

> "L'accesso allo stack di tecnologie di Azure apre la porta per alcune soluzioni scalabili, di facile implementazione e a disponibilità elevata che sono convenienti. In questo modo i nostri architetti possono essere molto più creativi con le soluzioni che forniscono. "  
> Ryan Sorensen  
> Director dello sviluppo di applicazioni e dell'architettura aziendale  
> Coverdell

### <a name="cost-avoidance"></a>Costi evitati

L'interruzione di un Data Center può anche garantire un costo evitabile, impedendo cicli di aggiornamento futuri. Un ciclo di aggiornamento è il processo di acquisto di nuovo hardware e software per sostituire i sistemi locali obsoleti. In Azure, l'hardware e il sistema operativo sono sottoposti a regolare manutenzione, con patch e aggiornamenti gratuiti per i clienti. Questo consente a un CFO di rimuovere la spesa futura pianificata dalle previsioni finanziarie a lungo termine. L'elusione dei costi viene misurata in dollari. Si differenzia dalla riduzione dei costi, che in genere si concentra su un budget futuro che non è ancora stato completamente approvato.

- **Esempio:** Il Data Center di un'azienda è attivo per un rinnovo del lease in sei mesi. Il Data Center è stato in servizio per otto anni. Quattro anni fa, tutti i server sono stati aggiornati e virtualizzati, con un costo pari a milioni di dollari della società. Il prossimo anno, la società intende aggiornare di nuovo l'hardware e il software. La migrazione degli asset in quel Data Center come parte di una migrazione cloud consente di evitare i costi rimuovendo l'aggiornamento pianificato dal budget previsto per l'anno successivo. Potrebbe anche produrre una riduzione dei costi diminuendo o eliminando i costi di locazione immobiliare.

### <a name="capital-expenses-vs-operating-expenses"></a>Spese di capitale e spese operative

Prima di discutere i risultati dei costi, è importante comprendere le due opzioni di costo principale: spese di capitale e spese operative.

I termini seguenti consentono di comprendere le differenze tra le spese di capitale e le spese operative durante le discussioni aziendali su un percorso di trasformazione.

- **Capital** è il denaro e le risorse di proprietà di un'azienda per contribuire a uno scopo specifico, ad esempio l'aumento della capacità del server o la creazione di un'applicazione.
- Le **spese di capitale** generano vantaggi per un lungo periodo. Queste spese sono in genere non ricorrenti e comportano l'acquisizione di asset permanenti. La creazione di un'applicazione può essere considerata come una spesa in conto capitale.
- Le **spese operative** sono costi continui per le attività aziendali. Usare i servizi cloud in un modello con pagamento in base al consumo può essere considerato come una spesa operativa.
- Gli **Asset** sono risorse economiche che possono essere di proprietà o controllate per produrre valore. Server, data Lake e applicazioni possono essere considerati asset.
- L' **ammortamento** è una riduzione del valore di un asset nel tempo. Più rilevante per le spese di capitale e la conversazione delle spese operative, l'ammortamento è il modo in cui vengono allocati i costi di un asset nei periodi in cui vengono usati. Ad esempio, se si compila un'applicazione in quest'anno ma si prevede una durata media di cinque anni (come la maggior parte delle app commerciali), il costo del team di sviluppo e gli strumenti necessari per creare e distribuire la codebase verrebbero ammortizzati uniformemente oltre cinque anni.
- La **valutazione** è il processo di stima del valore di un'azienda. Nella maggior parte dei settori, la valutazione è basata sulla capacità dell'azienda di generare ricavi e profitti, rispettando al tempo stesso i costi operativi necessari per creare i beni che forniscono tali ricavi. In alcuni settori, ad esempio la vendita al dettaglio o in alcuni tipi di transazioni, ad esempio l'equità privata, le risorse e l'ammortamento possono svolgere una parte importante della valutazione della società.

Spesso è una scommessa sicura che vari dirigenti, tra cui Chief Investment Officer (CIO), discutono il migliore uso della capitale per espandere l'azienda nella direzione desiderata. Fornire al CIO un mezzo per la conversione di conversazioni di spese di capitale contenzioso in una chiara responsabilità per le spese operative potrebbe essere un risultato interessante. In molti settori, i direttori finanziari (CFO) sono attivamente alla ricerca di modi per associare meglio l'affidabilità finanziaria al costo dei beni venduti.

Tuttavia, prima di associare un percorso di trasformazione a questo tipo di conversione di capitale e di spese operative, è consigliabile incontrare i membri dei team CFO o CIO per individuare la struttura di costo preferita dall'azienda. In alcune organizzazioni la riduzione delle spese di capitale a favore delle spese operative è un risultato estremamente *indesiderato* . Come indicato in precedenza, questo approccio è talvolta riscontrato in aziende di vendita al dettaglio, holding e private equity che hanno un valore superiore sui modelli di contabilità degli asset tradizionali, che inseriscono un valore minimo sull'IP. Si tratta anche di organizzazioni in cui si è verificata un'esperienza negativa quando il personale IT è stato esternalizzato o altre funzioni nel passato.

Se è auspicabile un modello di spesa operativa, l'esempio seguente potrebbe essere un risultato aziendale valido:

- **Esempio:** Il Data Center dell'azienda è attualmente svalutazione a _x USD_ all'anno per i prossimi tre anni. È prevista la necessità di un ulteriore _USD_ per aggiornare l'hardware prossimo anno. È possibile convertire le spese di capitale in un modello di spesa operativa a una velocità pari pari a _z USD_ al mese, consentendo una migliore gestione e responsabilità per i costi operativi della tecnologia.

## <a name="next-steps"></a>Passaggi successivi

Scopri di più sui [Risultati della flessibilità](./agility-outcomes.md).

> [!div class="nextstepaction"]
> [Risultati agilità](./agility-outcomes.md)
