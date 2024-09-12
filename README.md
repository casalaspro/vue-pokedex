# BoolDex!

### *The Pokedex Web App that uses [PokéApi](https://pokeapi.co/)! The Pokemon API Database!*

## Consegna:

📚 Vogliamo sviluppare il nostro Pokedex per poter riconoscere e catturare tutti i Pokemon presenti sul web!

Creiamo quindi una web app con Vue 3 che ci permetta di cercare Pokemon attraverso le API di PokeAPI e visualizzare i dettagli del Pokemon trovato. Quando troviamo un Pokemon che ci ispira particolarmente, possiamo catturarlo e salvarlo nel nostro Pokedex.

*Dobbiamo fare in modo che non scappino al refresh del browser!* 

Per rendere il nostro Pokedex completo quindi gestiamo i Pokemon dando la possibilità di salvarli o liberarli.

## Milestones

**Milestone 1**

Creiamo un componente per la ricerca: avremo bisogno di un campo di input in cui scrivere il nome del Pokemon e un pulsante per chiamare l’API. Inizialmente proviamo a vedere se i risultati sono corretti tramite un console.log (o nella tab Rete degli strumenti di chrome).

**Milestone 2**

Una volta che abbiamo i dati del nostro Pokemon, creiamo il componente per visualizzare i dettagli che arrivano tramite l’API. È sufficiente mostrare i dati principali, ad una visualizzazione più complessa ci penseremo più avanti.

**Milestone 3**

Aggiungere la possibilità tramite un pulsante di salvare il Pokemon trovato nel nostro Pokedex, mostrando la lista dei Pokemon salvati.

**Milestone 4**

Diamo la possibilità di cancellare dalla lista i Pokemon salvati e di poterne visualizzare il dettaglio nel componente dedicato cliccandoci sopra.

**Milestone 5**

Per completare il nostro pokedex, gestiamo la persistenza dei Pokemon salvati attraverso il local storage, da manipolare sia in fase di aggiunta che in fase di cancellazione di un Pokemon dalla lista.

**Milestone 6**

Dall’API ci arriveranno le varie statistiche del Pokemon, proviamo a far visualizzare i valori delle varie skill sotto forma di progress bar.

➕ **Bonus 1**

Nel nostro componente di ricerca potremmo aver implementato un emit e una props in ingresso. Sfruttare la documentazione di Vue per simulare il v-model su un componente custom (del tipo `<SearchCustom v-model=”search” >`)

➕ **Bonus 2**

L’API ci restituisce diverse immagini del Pokemon (fronte e retro). Proviamo a sfruttarle entrambe nel componente di dettaglio del Pokemon, magari implementando un’animazione per alternarle.

## Approccio progettuale

1. **Analisi del funzionamento dell'app e suddivisione in componenti**

2. **Schematizzazione dell'interazione dei componenti tra di loro**

3. **Approfondimento delle tecnologie necessarie allo sviluppo**

    *Dettagli da approfondire:*

  - V-model
  - Component v-model
  - Axios
  - LocalStorage
  - LocalStorage JSON in Vue
  - Props / Emit
  - Promise
  - JSON parse / stringify
  - Documentazione [PokéApi](https://pokeapi.co/)
  

