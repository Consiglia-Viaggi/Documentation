# Consiglia Viaggi

Il CV’19 (ConsigliaViaggi) è un Sistema Informativo complesso e distribuito finalizzato ad offrire una moderna piattaforma di supporto ai contenuti relativi a viaggi, multicanale. Il sistema distribuito presenta una parte di Back-Office per la gestione delle strutture ricettive e delle recensioni da parte degli amministratori, un Front-End per la ricerca di strutture e la visualizzazione di relative recensioni da parte di un utente finale, ed un client su dispositivo mobile,  utilizzato anche  per  funzionalità  di localizzazione  in  mobilità  (es:  visualizza  tutti  i ristoranti in un raggio di 500m dalla mia posizione attuale).
I principali servizi offerti dal sistema sono 7:

1. Visualizzazione di strutture recettive, individuate attraverso filtri  avanzati  per  la ricerca.
2. Visualizzazione di recensioni per la struttura individuata, con vari filtri (numero stelle, etc).
3. Aggiunta di una nuova Recensione
4. Gestione delle Strutture
5. Gestione Recensioni
6. Gestione dei Visitatori
7. Generazione Statistiche

Il sistema offre un sito web in cui sono disponibili recensioni relative ad alberghi, ristoranti ed attrazioni. Il sito deve offrire molteplici funzionalità di ricerca delle strutture (es: Nome, Città, Range di Prezzo, etc.). Le strutture vanno visualizzate su una mappa. E’ gradita ma non necessaria la possibilità di effettuare anche ricerche sulla mappa.Ciascun visitatore del sito può leggere i commenti degli altri utenti su alberghi, ristoranti, e attrazioni turistiche.  
È tuttavia necessario essere iscritti al sito per scrivere una recensione. I recensori di CV’19, pur registrandosi al sito con il proprio nome e cognome, possono scegliere se essere visualizzati, dagli utenti del sito, con nome e cognome oppure un nickname. Un visitatore può anche inserire una propria recensione relativa ad una struttura, specificando un rating da 1 a 5 e una descrizione testuale.Lato  Back-Office, un  gestore  del  sistema ha possibilità di effettuare le tipiche  operazioni CRUD sulla base di dati, specificando tutte   le informazioni per gestire una nuova struttura/attrazione. Inoltre,ha  facoltà  di ricercare tutte le  strutture  già caricate, con la possibilità di visualizzare informazioni statistiche sotto forma di tabelle e grafici (rating migliore, maggior numero di visitatori, etc...), e modificarne i dati salienti.  

Il Back-End offre anche una funzionalità di moderazione delle valutazioni: il sistema raccoglie le  valutazioni  scritte dagli utenti utilizzatori delle strutture; ogni recensione viene valutata dallo  staff  che  giudica  se è coerente alle linee guida del sito; in caso contrario non viene pubblicata.  
Infine, l’amministratore ha possibilità di visionare i dati dei visitatori, ancora a fini statistici (numero di recensioni, media valutazioni, etc...).Le funzionalità 1 -3devono essere disponibili sia in forma di Sito Web che di App sul client mobile.Si richiede che Sito e App condividano lo stesso back-end. La versione Mobile deve sfruttare la posizione del dispositivo per facilitare le ricerche.

### Servizi da implementare
Sviluppati tramite applicativo mobile su piattaforma Android:
- Visualizzazione di strutture recettive, individuate attraverso filtri  avanzati  per  la ricerca.
- Visualizzazione di recensioni per la struttura individuata, con vari filtri (numero stelle, etc).
- Aggiunta di una nuova Recensione.

Sviluppati tramite interfaccia web accessibile da browser:
- Gestione Recensioni
- Generazione Statistiche

# Modello funzionale
### Use case: Applicativo Android
![UseCaseAndroid](https://user-images.githubusercontent.com/22590804/105637061-afddea80-5e6b-11eb-8883-70fffbffbfe3.jpg)

### Use case: Sito web
![UseCaseSitoWeb](https://user-images.githubusercontent.com/22590804/105637087-d56af400-5e6b-11eb-9234-8761b6957704.jpg)

# Tabelle di Cockburn: Android
## Accesso senza email
**Use case 1**: accesso senza email.  
**Goal in context**: permettere all’utente di saltare la fase di accesso senza inserire alcuna credenziale.  
**Precondition**: l’utente deve essere nella schermata d’accesso "Primo Avvio".  
**Success End Condition**: apre interfaccia "Attiva posizione".  
**Failed End Condition**: l’utente non preme il pulsante "Salta per ora".  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che puòaccedere senza l’email.  
**Trigger**: viene premuto il pulsante "Salta per ora".  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Salta per ora"  |   |
| 2  |   | Apre interfaccia "Attiva posizione"l  |

## Attivare posizione
**Use case 2**: attivare posizione.  
**Goal in context**: permette all'utente di attivare la posizione.  
**Precondition**: l'utente deve attivare il posizionamento Global Positioning System.   
**Success End Condition**: pre interfaccia "Main Posizione On".  
**Failed End Condition**: l'utente non preme sul pulsante "Attiva posizione".   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può acconsentire di essere localizzato.   
**Trigger**: viene premuto il pulsante "Consenti".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Consenti"  |   |
| 2  |   |  Apre interfaccia "Main Posizione On" |
| 3  | Procede a localizzare l'utente  |   |
| 4  |   |  Apre interfaccia "Main Posizione On" |



## Non attivare posizione
**Use case 3**: non attivare posizione.  
**Goal in context**: usufruire dell'applicazione senza la geo localizzazione.   
**Precondition**: l'utente sceglie di non attivare la posizione.  
**Success End Condition**: apre interfaccia "Main Posizione Off".  
**Failed End Condition**: l'utente non preme il pulsante "Consenti" nell'interfaccia "Attiva Posizione".    
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può rifiutare di essere localizzato.  
**Trigger**: viene premuto il pulsante "Non adesso".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Non adesso"  |   |
| 2  |   |  Apre interfaccia "Main Posizione Off"  |


## Ricerca struttura
**Use case 4**: ricerca struttura.   
**Goal in context**: ricerca di una o più strutture.  
**Precondition**: l'utente si trova nella schermata "Ricerca".  
**Success End Condition**: apre la schermata "Risultati ricerca".  
**Failed End Condition**: subvariation 1: campo di ricerca vuoto. Subvariation 2: utente ricerca una struttura non presente. L'utente non preme il pulsante "Vai".   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può effettuare ricerche di strutture.  
**Trigger**: viene premuto il pulsante "Vai".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Compila il campo "Cerca" con un testo  |   |
| 2  |  Clicca il pulsante "Vai" |   |
| 3  |   | Apre interfaccia "Risultati Ricerca"    |

### Subvariation 1: campo cerca vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 2.1  |  Non compila il campo "Cerca"  |   |
| 3.1  |  Preme il pulsante "Vai" |   |
| 4.1  |   | Mostra messaggio "Inserisci qualcosa da cercare" |

### Subvariation 2: l'utente cerca una struttura non presente
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 2.2  |  Compila il campo "Cerca" con un nome struttura non presente  |   |
| 3.2  |  Preme il pulsante "Vai" |   |
| 4.2  |   |Mostra "Risultati ricerca" vuoto avvisando l'utente |

## Ricerca avanzata
**Use case 5**: ricerca avanzata.   
**Goal in context**: ricerca avanzata tramite filtri.   
**Precondition**: l'utente si trova nella schermata "Ricerca".   
**Success End Condition**: apre l'interfaccia "Ricerca Avanzata".   
**Failed End Condition**: l'utente non preme il pulsante "Ricerca Avanzata".   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può effettuare la propria ricerca con filtri avanzati.  
**Trigger**: viene premuto il pulsante "Ricerca Avanzata".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Ricerca Avanzata"  |   |
| 2  |   | Apre interfaccia "Ricerca Avanzata"   |

## Scegli migliore/peggiore
**Use case 6**: scegli migliore peggiore.  
**Goal in context**: ricerca una struttura ordinando per migliore/peggiore.   
**Precondition**: l'utente si trova nella schermata "Ricerca avanzata".   
**Success End Condition**: ritorna all'interfaccia "Ricerca".  
**Failed End Condition**: l'utente non preme il pulsante "Salva" per applicare il nuovo filtro migliore/peggiore.  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può specificare una ricerca avanzata sul filtro della struttura: migliore/peggiore.   
**Trigger**: viene premuto il pulsante "Salva".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Muove lo slide verso destra o sinistra per scegliere se ordinare per migliore o per peggiore. |   |
| 2  |  Preme il pulsante "Salva" |   |
| 3  |   | Ritorna all'interfaccia "Ricerca"   |


## Scegli il più caro/meno caro
**Use case 7**: ricerca avanzata.   
**Goal in context**: ricerca una struttura ordinando per meno caro/più caro.    
**Precondition**: l'utente si trova nella schermata "Ricerca avanzata".    
**Success End Condition**: ritorna all'interfaccia "Ricerca".    
**Failed End Condition**: l'utente non preme il pulsante "Salva" per applicare il nuovo filtro più caro/meno caro.   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può specificare una ricerca avanzata sul filtro della struttura: più caro/meno caro.    
**Trigger**: viene premuto il pulsante "Salva".    
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Muove lo slide verso destra o sinistra per scegliere se ordinare per più caro o meno caro  |   |
| 2  | Preme il pulsante "Salva"  |   |
| 3  |   |  Ritorna all'interfaccia "Ricerca"   |


## Scegli il più vicino/più lontano
**Use case 8**: scegli il più vicino/più lontano.  
**Goal in context**: ricerca una struttura ordinando per più vicino/più lontano.   
**Precondition**: l'utente si trova nella schermata "Ricerca avanzata".   
**Success End Condition**: ritorna all'interfaccia "Ricerca".   
**Failed End Condition**: l'utente non preme il pulsante "Salva" per applicare il nuovo filtro più vicino/più lontano.  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può specificare una ricerca avanzata sul filtro della struttura: più vicino/più lontano.    
**Trigger**: viene premuto il pulsante "Salva".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Muove lo slide verso destra o sinistra per scegliere se ordinare per più vicino o più lontano |   |
| 2  | Preme il pulsante "Salva" |   |
| 3  |   | Ritorna all'interfaccia "Ricerca" |


## Scegli servizi specifici
**Use case 9**: scegli servizi specifici.   
**Goal in context**: ricerca una struttura selezionando i servizi offerti.   
**Precondition**: l'utente si trova nella schermata "Ricerca avanzata".   
**Success End Condition**: ritorna all'interfaccia "Ricerca".   
**Failed End Condition**: l'utente non preme il pulsante "Salva" per applicare i nuovi servizi selezionati.  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può specificare una ricerca avanzata sul filtro di specifici servizi.   
**Trigger**: viene premuto il pulsante "Salva".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Seleziona uno o più servizi |   |
| 2  |  Preme il pulsante "Salva" |   |
| 3  |   |  Ritorna all'interfaccia "Ricerca" |


## Lista strutture ricercate
**Use case 10**: risultati ricerca.   
**Goal in context**: l'utente ha cercato una struttura.   
**Precondition**: apre la schermata "Risultati Ricerca".  
**Success End Condition**: apre la schermata "Risultati Ricerca".  
**Failed End Condition**: subvariation 1: l'utente ricerca una struttura non presente.   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può selezionare una struttura di quelle proposte nella lista.   
**Trigger**: l'utente clicca su una struttura.  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Viene mostrata una lista di strutture  |   |
| 2  |  Viene cliccata una struttura tra quellepresenti |   |
| 3  |   | Apre "Pagina Struttura" |



### Subvariation 1: struttura non presente
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1  |   |  Mostra "Non sono presenti strutture"  |


## Mostra struttura ricercata
**Use case 11**: mostra struttura ricercata.  
**Goal in context**: mostra all'utente l'insieme di informazioni in merito ad una struttura scelta.   
**Precondition**: l'utente si trova nella schermata "Risultati Ricerca".  
**Success End Condition**: mostra l'interfaccia "Pagina Struttura".   
**Failed End Condition**: subvariation 1: La ricerca in "Risultati Ricerca" non elenca alcuna struttura presente.   
L'utente non seleziona una struttura in "Risultati Ricerca".   
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può visualizzare l'insieme generale di informazioni di una struttura scelta.   
**Trigger**: viene selezionata una struttura in "Risultati Ricerca".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Seleziona una struttura  |   |
| 2  |   |  Apre l'interfaccia "Risultati Ricerca"  |

### Subvariation 1: la ricerca non elenca alcuna struttura presente
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1  |   |  Mostra "Risultati Ricerca" vuoto  |


## Mostra recensioni
**Use case 12**: mostra recensioni utente.  
**Goal in context**: mostra la lista di tutte le recensioni pubblicate dall'utente.  
**Precondition**: l'utente si trova nella schermata "Profilo" ed è un utente registrato.   
**Success End Condition**: apre la schermata "Le Mie Recensioni".   
**Failed End Condition**: l'utente non seleziona "Le Mie Recensioni".  
**Primary Actor**: utente. Si definisce un utente già registrato che può visualizzare le proprie recensioni.    
**Trigger**: l'utente seleziona la cella "Le mie recensioni".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Selezionare "Le mie recensioni"  |   |
| 2  |   | Apre l'interfaccia "Le Mie Recensioni"  |


## Mostra galleria
**Use case 13**: mostra galleria.  
**Goal in context**: mostra all'utente un insieme di immagini di una struttura selezionata.   
**Precondition**: l'utente si trova nella schermata "Pagina Struttura".  
**Success End Condition**: apre la schermata "Pagina Struttura - Foto".  
**Failed End Condition**: l'utente non preme il pulsante "Foto".  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può visualizzare l'insieme di immagini di una struttura.  
**Trigger**: viene premuto il pulsante "Foto".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Preme il pulsante "Foto" |   |
| 2  |   |  Mostra l'interfaccia contenente tutte le foto della struttura |


## Aggiungi recensione
**Use case 14**: aggiungi recensione.  
**Goal in context**: aggiungi una recensione per una determinata struttura.   
**Precondition**: l'utente si trova nella schermata "Struttura", nel tab "Recensioni" ed è un utente registrato.   
**Success End Condition**:  l'utente pubblica una recensione.   
**Failed End Condition**:Subvariation 1: l'utente non inserisce nessun titolo. Subvariation 2: l'utente non inserisce nessuna descrizione. Subvariation 3: l'utente preme il pulsante "Annulla". L'utente non preme il pulsante "Invia" per pubblicare la recensione o preme il pulsante "Annulla".  
**Primary Actor**:utente. Si definisce un utente già registrato che può aggiungere una recensione ad una struttura.      
**Trigger**:  viene premuto il pulsante "Invia".    
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Premere il pulsante "Scrivi Recensioni"  |   |
| 2  |   |  Mostra l'interfaccia "Recensione"  |
| 3  |  Toccare una stella per valutare la struttura  |   |
| 4  | Modifica il numero di stelle della recensione  |   |
| 5  | Inserire un titolo per la recensione  |   |
| 6  |  Modifica il titolo della recensione  |   |
| 7  |  Inserire una descrizione della recensione  |   |
| 8  | Modifica la descrizione della recensione  |   |
| 9  |  Premere il pulsante "Invia"  |   |
| 10  |   | Salva la recensione per l'approvazione e la pubblicazione  |

### Subvariation 1: l'utente non inserisce nessun titolo
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 5.1  |  Non inserisce il titolo della recensione   | |
| 6.1  |   Preme il pulsante "Invia" |   |
| 7.1  |   | Mostra messaggio "Compila i campi richiesti" |

### Subvariation 2:  l'utente non inserisce nessuna descrizione
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 7.2  |  Non inserisce la descrizione della recensione  |   |
| 8.2  | Preme il pulsante "Invia"  |  |
| 9.2  |   | Mostra messaggio "Compila i campi richiesti" |


### Subvariation 3: l'utente preme il pulsante annulla
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 7.3  | Preme il pulsante annulla  |    |
| 8.3  |   | Non salva alcuna informazione scritta dall'utente     |

## Mostra foto
**Use case 15**: mostra foto.  
**Goal in context**: mostra una foto tra quelle pubblicate per una determinata struttura.    
**Precondition**: l'utente si trova nella schermata "Galleria", per una qualsiasi struttura scelta.  
**Success End Condition**: apre la schermata "Foto".   
**Failed End Condition**: l'utente non seleziona nessuna foto.  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può visualizzare una foto specifica di una struttura.    
**Trigger**: viene selezionata una foto.   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Seleziona una foto dalla lista  |   |
| 2  |   | Mostra l'interfaccia "Foto", che presenta la foto ingrandita.   |


## Accesso con email
**Use case 16**: accesso con email.  
**Goal in context**: permettere all'utente di accedere al suo account.  
**Precondition**: l'utente deve disporre di un account registrato.  
**Success End Condition**: apre interfaccia "Attiva posizione".   
**Failed End Condition**: Subvaration 1: credenziali non valide. Subvaration 2: account inserito non registrato. Subvaration 3: campo email vuoto. Subvaration 4: campo password vuoto. Subvaration 5: campo email e password vuoto. L'utente non preme il pulsante "accedi".  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può accedere con l'email.  
**Trigger**: viene premuto il pulsante "Accedi".  
**Description**:   

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Compila il campo "Indirizzo e-mail"  |   |
| 2  |  Compila il campo "Password"  |   |
| 3  |  Preme il pulsante "Accedi" |   |
| 4  |   | Apre interfaccia "Attiva posizione"   |

### Subvariation 1:  credenziali non valide
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 4.1  |  Compila i campi "Indirizzo email" e/o "Password" con credenziali errate  |   |
| 4.1  | Preme il pulsante "Accedi"|  |
| 5.1  |   | Mostra messaggio "Credenziali non valide" |

### Subvariation 2: account non registrato
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.2  | Compila i campi "Indirizzo email" e/o "Password"  |   |
| 4.2  |Preme il pulsante "Accedi"  |  |
| 5.2  |   |   Mostra messaggio "Credenziali non valide"|

### Subvariation 3: campo email vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.3  | Compila il campo "Password" e non "Indirizzo email"   |   |
| 4.3  | Preme il pulsante "Accedi"  |  |
| 5.3  |   | Mostra messaggio "Inserisci la tua email" |

### Subvariation 4: campo password vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.4  | Compila il campo "Indirizzo email" e non "Password"   |   |
| 4.4  | Preme il pulsante "Accedi" |  |
| 5.4  |   |  Mostra messaggio "Inserisci la tua password" |

### Subvariation 5: campo email e password vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.5  |  Lascia vuoti i campi "Indirizzo email" e "Password"  |   |
| 4.5  |Preme il pulsante "Accedi"  |  |
| 5.5  |   | Mostra messaggio "Compila i campi richiesti" |

## Mostra profilo
**Use case 17**: mostra profilo.  
**Goal in context**: mostrare il profilo dell'utente.  
**Precondition**: l'utente deve essere registrato ed aver effettuato l'accesso.   
**Success End Condition**: apre la schermata "Profilo Utente Registrato".   
**Failed End Condition**: Subvariation 1: l'utente non è registrato. L'utente non preme il pulsante "Profilo".   
**Primary Actor**:utente. Si definisce un utente già registrato che può visualizzare il proprio profilo.    
**Trigger**: viene premuto il pulsante "Profilo".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Preme il pulsante "Profilo"  |   |
| 2  |   | Utente registrato: apre interfaccia "Profilo Utente Registrato"   |

### Subvariation 1: utente non registrato
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |  Preme il pulsante "Profilo"  |   |
| 2.1  |  | Utente non registrato: apre interfaccia "Registrazione Accedi" |


## Modifica l'email utente
**Use case 18**: modifica l'email utente.  
**Goal in context**: email utente modificata.   
**Precondition**: l'utente si trova nella schermata "Modifica account", per cui deve essere un utente registrato.   
**Success End Condition**: mostra il popup "Informazioni aggiornate".   
**Failed End Condition**: Subvariation 1: campo "Nuova email" vuoto. Subvariation 2: campo "Conferma nuova email" vuoto. Subvariation 3: le email non corrispondono. Subvariation 4: l'email inserita è la stessa già usata.  
**Primary Actor**: utente. Si definisce un utente già registrato che può modificare la propria email.  
**Trigger**: viene premuto il pulsante "Aggiorna".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Compila il campo "Nuova email"  |   |
| 2  |  Compila il campo "Conferma nuova email"   |   |
| 3  |  Compila il campo "Password attuale" |   |
| 4  |   Preme il pulsante "Aggiorna" |   |
| 5  |   | Controlla se la password attuale coincide con quella salvata nel sistema  |
| 6  |   | Controlla se le due email coincidono  |
| 7  |   | Mostra un pop-up "Informazioni aggiornate"  |

### Subvariation 1: campo "Nuova email" vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |  Lascia vuoto il campo "Nuova email"  |   |
| 2.1  | Preme il pulsante "Aggiorna" |  |
| 3.1  |  | Mostra messaggio "Compila i campi richiesti" |


### Subvariation 2: campo "Conferma nuova email" vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.2 |   Lascia vuoto il campo "Conferma nuova email" |   |
| 2.2  | Preme il pulsante "Aggiorna"  |  |
| 3.2  |  |  Mostra messaggio "Compila i campi richiesti" |


### Subvariation 3: le email non corrispondono
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.3 |  Compila il campo "Nuova email"   |   |
| 4.3  |  Compia il campo "Conferma nuova email" con una email errata |  |
| 5.3  |  Preme il pulsante "Aggiorna" |  |
| 6.3  |  | Mostra messaggio "Le email non corrispondono" |

### Subvariation 4: l'email inserita è la stessa già usata
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.4 |  Inserisci la stessa email con cui si ha effettuato l'accesso  |   |
| 4.4  | Preme il pulsante "Aggiorna" |  |
| 5.4  |  | Mostra messaggio "L'email deve essere diversa da quella in uso" |


## Modifica la password utente
**Use case 19**: modifica la password utente.   
**Goal in context**: modificare la password dell'utente.  
**Precondition**: l'utente si trova nella schermata "Modifica account", per cui deve essere un utente registrato.  
**Success End Condition**: mostra il popup "nformazioni aggiornate".   
**Failed End Condition**:Subvariation 1: l'utente lascia il campo "Password attuale" vuoto. Subvariation 2: l'utente lascia il campo "Nuova password" vuoto.     Subvariation 3: L'utente lascia il campo "Conferma nuova password" vuoto. Subvariation 4: la password attuale è errata. Subvariation 5: Le password non corrispondono. L'utente non preme il pulsante "Aggiorna" per applicare i cambiamenti.  
**Primary Actor**: utente. Si definisce un utente già registrato che può modificare la propria password.  
**Trigger**: viene premuto il pulsante "Aggiorna".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Inserisci la password attuale |   |
| 2  | Inserisci la nuova password   |   |
| 3  | Conferma la nuova password  |   |
| 4  |   Preme il pulsante "Aggiorna" |   |
| 5  |   | Controlla se la password attuale coincide con quella salvata nel sistema  |
| 6  |   |  Controlla se le due password coincidono  |
| 7  |   |  Mostra il popup "Informazioni aggiornate"  |

### Subvariation 1: campo "Password attuale" vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 4.1 |  Lascia vuoto il campo "Password attuale"  |   |
| 5.1  | Preme il pulsante "Aggiorna" |  |
| 6.1  |  | Mostra messaggio "Compila i campi richiesti" |

### Subvariation 2: campo "Nuova password" vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.2 |  Lascia vuoto il campo "Nuova password"  |   |
| 2.2  |  Preme il pulsante "Aggiorna" |  |
| 3.2 |  | Mostra messaggio "Compila i campi richiesti" |

### Subvariation 3: campo "Conferma nuova password" vuoto
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.3 |  Lascia vuoto il campo "Conferma nuova password"  |   |
| 2.3  | Preme il pulsante "Aggiorna"  |  |
| 3.3  |  | Mostra messaggio "Compila i campi richiesti" |

### Subvariation 4: la password attuale è errata.
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.4 |  Inserisci una password attuale errata   |   |
| 4.4  |  Preme il pulsante "Aggiorna"|  |
| 5.4  |  | Mostra messaggio "La password attuale è errata" |


### Subvariation 5: le password non corrispondono.
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 3.5 |  Inserisci una nuova password   |   |
| 4.5  | Conferma la nuova password immettendone una errata  |  |
| 5.5  | Preme il pulsante "Aggiorna" |  |
| 5.5  |  | Mostra messaggio "Le password non corrispondono." |

## Mostra recensioni utente 
**Use case 20**: mostra recensioni.   
**Goal in context**: mostra tutte le recensioni pubblicate per una determinata struttura.   
**Precondition**: l'utente si trova nella schermata "Pagina struttura", per una qualsiasi struttura scelta.  
**Success End Condition**: apre la schermata "Recensioni".   
**Failed End Condition**: l'utente non preme il pulsante "Recensioni" per mostrare tutte le recensioni.  
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può visualizzare le recensioni di una deternimata struttura.     
**Trigger**: viene premuto il pulsante "Recensioni".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Recensioni"  |   |
| 2  |   | Mostra l'interfaccia "Recensioni", connessa al pulsante "Recensioni".   |


## Mostra termini e condizioni
**Use case 21**: mostra termini e condizioni.  
**Goal in context**: mostra i termini e le condizioni d'uso dell'applicazione, aprendo una pagina web.   
**Precondition**: l'utente si trova nella schermata "Profilo" ed è un utente registrato.    
**Success End Condition**: apre il collegamento ad internet che reindirizza alla pagina web "Termini  condizioni".    
**Failed End Condition**: l'utente non seleziona la cella "Termini e condizioni".    
**Primary Actor**: utente. Si definisce un utente non registrato o un utente già registrato che può leggere i termini e condizione dell'applicativo.    
**Trigger**: l'utente seleziona la cella "Termini  condizioni".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Seleziona la cella "Recensioni utente"  |   |
| 2  |   | Apre il collegamento ad internet, reindirizzando alla pagina "Termini  Condizioni"   |

# Tabelle di Cockburn: Sito Web
## Accesso con email
**Use case 1**: accesso con email.   
**Goal in context**: viene effettuato l'accesso con l'email.   
**Precondition**: vengono inserite le giuste credenziali d'accesso.   
**Success End Condition**: viene aperta la schermata "Home".   
**Failed End Condition**: subvariation 1: credenziali non valide.   
**Primary Actor**: l'utente non preme il pulsante accedi.    
**Trigger**: amministratore. Si definisce un amministratore del sito web che può accedere usando la propria email.  
**Description**: viene premuto il pulsante "Accedi".  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Compila il campo "Indirizzo e-mail"  |   |
| 2  | Compila il campo "Password"  |   |
| 3  |  Preme il pulsante "Accedi" |   |
| 4  |    |  Apre interfaccia "Home"  |

### Subvariation 1: la password attuale è errata.
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |  Compila il campo "Indirizzo e-mail" e/o "Password" con credenziali sbagliate   |   |
| 2.1  |  Preme il pulsante "Accedi" |  |
| 3.1  |  | Mostra messaggio "Credenziali non valide" |

## Home
**Use case 2**: home.  
**Goal in context**:  viene visualizzata la pagina "Home".   
**Precondition**: viene effettuato l'accesso con e-mail e password.   
**Success End Condition**: viene mostrata la schermata principale di amministrazione nell'interfaccia "Home".    
**Failed End Condition**: non viene mostrata la schermata principale di amministrazione sull'interfaccia "Home".  
**Primary Actor**: amministratore.  Si definisce un amministratore del sito web che può accedere alle informazioni specifiche del suo account.  
**Trigger**: viene premuto il pulsante "Accedi".   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Home" sulla barra in alto del sito  |   |
| 2  |   |  Mostra interfaccia "Home" |

## Modifica email
**Use case 3**: modifica email.  
**Goal in context**: viene modificata l'email dell'amministratore.   
**Precondition**: viene fatto l'accesso con le giuste credenziali e ci si trova nell'interfaccia "Home".      
**Success End Condition**: cambio di email.  
**Failed End Condition**: Subvariation 1: viene inserita la stessa email. Subvariation 2: viene inserita una password di conferma errata. Non viene premuto il pulsante "Conferma".  
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può modificare la propria email.     
**Trigger**: viene premuto il pulsante "Conferma".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Viene premuto il pulsante "Modifica indirizzo email"  |   |
| 2  |   | Apre l'interfaccia "Modifica email"  |
| 3  | |  Compila il campo "Nuovo indirizzo email" |
| 4  |  Compila il campo "Conferma la tua password"  |   |
| 5  |   | Ritorna all'interfaccia "Home" |

### Subvariation 1: viene inserita la stessa mail
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |  Viene premuto il pulsante "Modifica indirizzo rmail"    |   |
| 2.1  |   |  Apre interfaccia "Modifica email" |
| 3.1  |  Compila il campo "Nuovo indirizzo email" con la stessa email |  |
| 4.1  |  Compila il campo "Conferma la tua password" |  |
| 5.1  |  | Mostra messaggio di errore "Hai utilizzato la stessa email" |


### Subvariation 2: viene inserita una password di conferma errata
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.2 |  Viene premuto il pulsante "Modifica indirizzo email"   |   |
| 2.2  |   | Apre interfaccia "Modifica email" |
| 3.2  |  Compila il campo "Nuovo indirizzo email" con la stessa email |  |
| 4.2  | Compila il campo "Conferma la tua password" con una password errata |  |
| 5.2  |  | Mostra messaggio di errore "La password inserita è errata" |

## Modifica password
**Use case 4**: modifica password.  
**Goal in context**: apre l'interfaccia "Modifica Password".   
**Precondition**: l'amministratore deve aver effettuato l'accesso al sito e trovarsi nell'interfaccia "Home".  
**Success End Condition**: la password viene modificata.   
**Failed End Condition**: Subvariation 1: la password nuova e quella di conferma non coincidono. Non viene premuto il pulsante "Conferma".   
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può modificare la propria password.   
**Trigger**: l'amministratore preme il pulsante "Modifica Password".     
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Modifica password"  |   |
| 2  |   | Mostra l'interfaccia "Modifica password"  |
| 3  |Compila il campo "Nuova Password" |   |
| 4  |  Compila il campo "Conferma"  |   |
| 5  |   | Ritorna all'interfaccia "Home" |

### Subvariation 1: la password nuova e quella di conferma non coincidono
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |   | Mostra l'interfaccia "Modifica password"  |
| 2.1  | Compila il campo "Nuova Password"   |  |
| 3.1  | Compila il campo "Conferma nuova password" con una password errata |  |
| 4.1  | | Mostra messaggio di errore "Le due password non corrispondono" |


## Recensioni
**Use case 5**: recensioni.   
**Goal in context**: mostra l'insieme di recensioni da dover approvare.   
**Precondition**: l'amministratore si trova in una qualsiasi interfaccia del sito.    
**Success End Condition**: viene mostrata l'interfaccia "Recensioni".   
**Failed End Condition**: l'amministratore non preme il pulsante "Recensioni" nella barra in alto del sito. L'amministratore non seleziona alcuna recensione.      
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può accedere a informazini generali sulle recensioni degli utenti.  
**Trigger**: l'amministratore preme il pulsante "Recensioni" nella barra in alto del sito.   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme il pulsante "Recensioni"  |   |
| 2  |   | Mostra l'interfaccia "Recensioni"  |


## Mostra dettagli recensione
**Use case 6**: mostra recensione.  
**Goal in context**: mostra la recensione di un utente che può essere approvata o eliminata.   
**Precondition**: l'amministratore ha selezionato una recensione di un utente nell'interfaccia "Recensioni".  
**Success End Condition**: viene mostrata l'interfaccia "Mostra dettagli recensione" dell'utente scelto.   
**Failed End Condition**: l'amministratore non preme né il pulsante "Approva" né il pulsante "Elimina".   
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può visualizzare una specifica recensione di un utente.        
**Trigger**: l'amministratore seleziona una recensione presente nella lista delle recensioni.   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Seleziona una recensione   |   |
| 2  |   | Mostra l'interfaccia "Mostra dettagli recensione" |


## Approva
**Use case 7**: approva.   
**Goal in context**: approva la recensione scelta dall'amministratore.   
**Precondition**: l'amministratore ha selezionato una recensione di un utente nell'interfaccia "Recensioni".   
**Success End Condition**: viene approvata la recensione scelta dall'amministratore.   
**Failed End Condition**: l'amministratore non preme pulsanti.  
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può approvare una specifica recensione utente.     
**Trigger**: l'amministratore preme il pulsante "Approva".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Approva la recensione scelta   |   |
| 2  |   | Mostra l'interfaccia "Recensioni"  |


## Elimina
**Use case 8**: elimina.  
**Goal in context**: elimina la recensione scelta dall'amministratore.  
**Precondition**: l'amministratore ha selezionato una recensione di un utente nell'interfaccia "Recensioni".  
**Success End Condition**: viene eliminata la recensione scelta dall'amministratore.   
**Failed End Condition**: l'amministratore non seleziona alcuna recensione.  
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può eliminare una specifica recensione utente.    
**Trigger**: l'amministratore seleziona una recensione presente nella lista delle recensioni.   
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Elimina la recensione scelta |   |
| 2  |   |  Mostra l'interfaccia "Recensioni" |


## Statistiche
**Use case 9**: statistiche.  
**Goal in context**: mostra un insieme generico di statistiche.   
**Precondition**: l'amministratore si trova in una qualsiasi interfaccia del sito.    
**Success End Condition**: viene mostrata l'interfaccia "Statistiche".    
**Failed End Condition**: l'amministratore non preme il pulsante "Statistiche" nella barra in alto del sito.  
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può visualizzare un insieme di statistiche generiche.    
**Trigger**: l'amministratore preme il pulsante "Statistiche" nella barra in alto del sito.  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme "Statistiche"   |   |
| 2  |   | Mostra l'interfaccia "Statistiche"  |


## Lista statistiche utente
**Use case 10**: lista statistiche utente.   
**Goal in context**: mostra l'elenco di tutti gli utenti che hanno fatto una recensione.  
**Precondition**: l'amministratore si trova nell'interfaccia "Statistiche".  
**Success End Condition**: viene mostrata l'interfaccia "Lista statistiche per utente".    
**Failed End Condition**: Subvariation 1: nessun utente ha effettuato una recensione. L'amministratore non seleziona "Statistiche per utente".   
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può visualizzare tutte le statistiche.       
**Trigger**: l'amministratore preme il pulsante "Statistiche per utente".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  |  Preme il pulsante "Statistiche per utente" |   |
| 2  |   | Mostra l'interfaccia "Lista statistiche per utente"  |

### Subvariation 1:  nessun utente ha effettuato una recensione
| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1.1 |   | Mostra l'interfaccia "Modifica password"  |


## Statistiche generali
**Use case 11**: statistiche generali.   
**Goal in context**: mostra le statistiche generali.    
**Precondition**: l'amministratore si trova nell'interfaccia "Statistiche".  
**Success End Condition**: viene mostrata l'interfaccia "Statistiche generali".  
**Failed End Condition**: l'amministratore non seleziona "Statistiche generali".   
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può visualizzare tutte le statistiche dell'applicativo filtrate in maniera generale.       
**Trigger**: l'amministratore preme il pulsante "Statistiche generali".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme "Statistiche generali"   |   |
| 2  |   | Mostra l'interfaccia "Statistiche generali"  |

## Statistiche per utente
**Use case 12**: statistiche per utente.   
**Goal in context**: mostra la lista di tutti gli utenti.    
**Precondition**: l'amministratore si trova nell'interfaccia "Statistiche".    
**Success End Condition**: viene mostrata l'interfaccia "Statistiche per utente".    
**Failed End Condition**: l'amministratore non seleziona "Statistiche per utente".    
**Primary Actor**: amministratore. Si definisce un amministratore del sito web che può visualizzare tutte le statistiche dell'applicativo filtrate in maniera specifica per utente.     
**Trigger**: l'amministratore preme il pulsante "Statistiche per utente".  
**Description**:  

| Step n°        | Utente | Sistema | 
| ------------- | ------------- | ------------- |
| 1  | Preme "Statistiche per utente"   |   |
| 2  |   | Mostra l'interfaccia "Statistiche per utente"  |

# Mock-up
### Applicativo Android

![1-primoavvio](https://user-images.githubusercontent.com/22590804/106390498-11143980-63e9-11eb-88b9-9c533b45f5c9.png)      <br /> <br /> <br /> <br />
![2-registrazioneaccedi](https://user-images.githubusercontent.com/22590804/106390499-12456680-63e9-11eb-8e59-7741ccb4bfa6.png)      <br /> <br /> <br /> <br />
![3-registrazione](https://user-images.githubusercontent.com/22590804/106390500-12ddfd00-63e9-11eb-9a53-08e3ff99efb9.png) <br /> <br /> <br /> <br />
![4-mainposizioneon](https://user-images.githubusercontent.com/22590804/106390501-12ddfd00-63e9-11eb-9cbe-a4ff5b1d8c99.png) <br /> <br /> <br /> <br />
![5-mainposizioneoff](https://user-images.githubusercontent.com/22590804/106390503-13769380-63e9-11eb-8284-9119b8637d15.png) <br /> <br /> <br /> <br />
![6-ricerca](https://user-images.githubusercontent.com/22590804/106390504-13769380-63e9-11eb-972f-5806d91fbd3a.png) <br /> <br /> <br /> <br />
![7-ricercaavanzata](https://user-images.githubusercontent.com/22590804/106390505-140f2a00-63e9-11eb-9639-822a3a00c754.png) <br /> <br /> <br /> <br />
![8-servizi](https://user-images.githubusercontent.com/22590804/106390507-140f2a00-63e9-11eb-8f91-c44bce1663a2.png) <br /> <br /> <br /> <br />
![9-risultatiricerca](https://user-images.githubusercontent.com/22590804/106390508-14a7c080-63e9-11eb-9dd8-69ded7b71eef.png) <br /> <br /> <br /> <br />
![10-paginastruttura](https://user-images.githubusercontent.com/22590804/106390509-14a7c080-63e9-11eb-91f7-a88d3d9f0b3a.png) <br /> <br /> <br /> <br />

![11scrivirecensioni](https://user-images.githubusercontent.com/22590804/106390514-15d8ed80-63e9-11eb-8925-9184e3bccd12.png) <br /> <br /> <br /> <br />
![12-profiloutenteregistrato](https://user-images.githubusercontent.com/22590804/106390516-16718400-63e9-11eb-8e09-83dbca1a4dd7.png) <br /> <br /> <br /> <br />
![13-lemierecensioni](https://user-images.githubusercontent.com/22590804/106390518-16718400-63e9-11eb-8dea-be6230089ec1.png) <br /> <br /> <br /> <br />
![14-modificaindirizzoemail](https://user-images.githubusercontent.com/22590804/106390519-16718400-63e9-11eb-8492-0ce30552cefe.png) <br /> <br /> <br /> <br />
![15-modificapassword](https://user-images.githubusercontent.com/22590804/106390520-170a1a80-63e9-11eb-9473-413112c8a1a4.png) <br /> <br /> <br /> <br />
![16-eliminaaccount](https://user-images.githubusercontent.com/22590804/106390522-170a1a80-63e9-11eb-8692-3ec75dec74c5.png) <br /> <br /> <br /> <br />
![17-terminicondizioni](https://user-images.githubusercontent.com/22590804/106390523-170a1a80-63e9-11eb-8184-8b0062951e13.png) <br /> <br /> <br /> <br />


### Sito Web
![accessoconemail](https://user-images.githubusercontent.com/22590804/106390821-95b38780-63ea-11eb-975a-57848c83831e.png) <br /> <br /> <br /> <br />
![approvaeliminarecensione](https://user-images.githubusercontent.com/22590804/106390824-964c1e00-63ea-11eb-809e-b642e545a6b7.png) <br /> <br /> <br /> <br />
![home](https://user-images.githubusercontent.com/22590804/106390825-96e4b480-63ea-11eb-9c1a-0cd18764ecfd.png) <br /> <br /> <br /> <br />
![listastatisticheperutente](https://user-images.githubusercontent.com/22590804/106390827-977d4b00-63ea-11eb-8606-f7bc136cc4b8.png) <br /> <br /> <br /> <br />
![modificaemail](https://user-images.githubusercontent.com/22590804/106390828-977d4b00-63ea-11eb-9c55-cc7e9a1bd447.png) <br /> <br /> <br /> <br />
![modificapassword](https://user-images.githubusercontent.com/22590804/106390829-9815e180-63ea-11eb-915a-ef43c9118c67.png) <br /> <br /> <br /> <br />
![mostradettaglirecensione](https://user-images.githubusercontent.com/22590804/106390830-9815e180-63ea-11eb-9d65-18713c00bf9b.png) <br /> <br /> <br /> <br />
![recensioni](https://user-images.githubusercontent.com/22590804/106390831-98ae7800-63ea-11eb-8bc4-f720af36b282.png) <br /> <br /> <br /> <br />
![statistiche](https://user-images.githubusercontent.com/22590804/106390833-98ae7800-63ea-11eb-91a4-d45172f4a756.png) <br /> <br /> <br /> <br />
![statistichegenerali](https://user-images.githubusercontent.com/22590804/106390834-99470e80-63ea-11eb-849f-5124c989ff1e.png) <br /> <br /> <br /> <br />
![statisticheperutente](https://user-images.githubusercontent.com/22590804/106390835-99470e80-63ea-11eb-8628-0bde24ff7517.png) <br /> <br /> <br /> <br />

## Glossario
### Account
Funzionalità e attributi riservati a chi ha associato un nome utente ed una password.

### Affordance
Qualità fisica di un oggetto che suggerisce a un essere umano le azioni appropriate per manipolarlo.

### Amministratore
Amministratore identifica un utilizzatore dell'interfaccia web con pieni privilegi di approvazione o eliminazione di recensioni di utenti registrati.

### Campo vuoto
Identifica un campo che richiede una specifica e/o insieme specifico di informazioni necessarie per proseguire nel flusso dell'applicativo che viene lasciato vuoto, ovvero privo delle informazioni richieste.

### Evento
Condizione che si verifica dopo l'esecuzione di un'istruzione o,nel nostro caso, di un trigger.

### Filtro
Filtro evidenzia una serie di possibili scelte che possono essere effettuate da un utente o utente registrato. Con scelte si intendono un sottoinsieme di criteri per specificare una determinata ricerca su una struttura.

### Galleria
Insieme di immagini di una specifica struttura. Tale insieme può essere visualizzato da un utente registrato e non.

### Geo localizzazione 
Localizzazione di un ricevitore mediante lo scambio di informazioni radio tra esso ed un insieme di satelliti. La geo localizzazione viene utilizzata per trovare la posizione di un utente o un utente registrato. Ciò avviene attraverso il dispositivo utilizzato (smartphone).

### Home
Home identifica la schermata principale dove l'utente viene riportato nell'apertura dell'applicazione o dopo lo sviluppo di un evento.

### Interfaccia
Elemento intermediario tra l'utente che deve usufruire del sistema e il sistema stesso. L'interfaccia permette all'utente di interagire con il sistema in maniera semplice ed elegante.

### Popup
Finestre a comparsa che appaiono automaticamente nell'applicazione dopo aver premuto un pulsante.

### Posizione
Posizione di un utente sulla base della geo localizzazione.

### Profilo
Profilo identifica un'insieme di informazioni che costituiscono un utente registrato. Con informazioni si intende ad esempio l'email, recensione effettuate ed altri dettagli.

### Pulsante
Pulsante definite un' elemento grafico delle tipologia degli affordance utili per l'interazione con l'utente.

### Servizio
Servizio specifica un tipo di bene che viene offerto a: utente, utente registrato e amministratore.

### Statistiche
Dati relativi ad utenti o all'applicativo stesso. Sono informazioni accessibili soltanto all'amministratore.

### Subvariation
Permette la gestione di situazione di errore negli use case. In un certo passo può succedere qualcosa di diverso dal flusso classico dell'use case e il sistema dovrà reagire in maniera diversa.

### Trigger
Azione svolta da: utente, utente registrato o amministratore per dare vita ad uno specifico evento.

### Use Case
Tradotto in italiano "caso d'uso", è un diagramma usato nell'informatica (più in particolar modo nell'ingegneria del software) che ha la finalità di comunicare col cliente tutte le funzionalità software che vengono offerte. 

### Utente
Utente identifica un qualsiasi utilizzatore dell'applicativo.

### Utente registrato
Utente registrato identifica un utente che si è già registrato al servizio o che procede alla sua registrazione dall'applicativo.

# Modello di dominio
## Class Diagram: Applicativo Android 
![Class%20Diagram%20Di%20Dominio](https://user-images.githubusercontent.com/22590804/106391201-774e8b80-63ec-11eb-91a7-d7da194dc02c.png)

## Class Diagram: Sito Web 
![Class%20diagram%20Website%20-%20Dominio](https://user-images.githubusercontent.com/22590804/106391204-787fb880-63ec-11eb-97a0-221417008583.png)

## Class Diagram: Databse
![Database](https://user-images.githubusercontent.com/22590804/106391205-79184f00-63ec-11eb-8c6e-57b470426664.png)

## CRC Cards: Applicativo Android
|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Utente |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |    salvare le informazioni dell’utente               |
| Collaborators |  Recensioni, Ricerca                 |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Ricerca | 
| Superclass |        -          |
| Subclass |           Ricerca avanzata        |
| Responsabilities |     permette la ricerca di una struttura          |
| Collaborators |    Struttura           |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Ricerca avanzata |
| Superclass |       Ricerca          |
| Subclass |           -         |
| Responsabilities |  permette l'utilizzo di filtri nella ricerca              |
| Collaborators |        -       |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Struttura |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |    mostra i dettagli della struttura & Ricerca             |
| Collaborators |    Utente, Struttura          |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Recensione |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |    permette di visualizzare le recensioni di una struttura, permette di scrivere una recensione            |
| Collaborators |   Utente, Struttura           |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Galleria |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |   permette la visualizzazione della galleria delle foto              |
| Collaborators |      Foto, Struttura         |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Foto |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |    permette la visualizzazione di una foto specifica              |
| Collaborators |     Struttura, Galleria         |

## CRC Cards: Sito Web
|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Amministratore |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |    Gestisce le recensioni, Visualizza le statistiche             |
| Collaborators |     Recensioni, Statistiche    |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Recensioni  |
| Superclass |        -          |
| Subclass |           -         |
| Responsabilities |   Visualizza una recensione             |
| Collaborators |     Statistiche    |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Statistiche |
| Superclass |        -          |
| Subclass |           Statistiche generali,  Statistiche utente        |
| Responsabilities |    Visualizza le informazioni di statistiche generali             |
| Collaborators |    Amministratore     |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Statistiche generali |
| Superclass |  Statistiche |
| Subclass |           -         |
| Responsabilities |     Visualizza specifiche delle statistiche generali             |
| Collaborators |     -   |

|  CRC Cards       |               |  
| ------------- | ------------- | 
| Class name | Statistiche utente |
| Superclass |       Statistiche utente         |
| Subclass |        Statistiche        |
| Responsabilities |    Visualizza specifiche delle statistiche utente             |
| Collaborators |    -    |
